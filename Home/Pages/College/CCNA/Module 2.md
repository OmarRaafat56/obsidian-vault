[[CCNA]]


---

# Module 2 – Basic Switch and End Device Configuration

**Course:** Introduction to Networks (ITN v7.0)
**Module Objective:** Implement initial settings including passwords, IP addressing, and default gateway parameters on network switches and end devices.

---

## Cisco IOS Access

### Operating System Components

* **Hardware:** Physical components of the device
* **Kernel:** Manages hardware resources for software
* **Shell:** User interface (CLI or GUI)

### GUI vs CLI

* **GUI:** User-friendly, icon-based (e.g., Windows, macOS)
* **CLI:** Text-based, more reliable for network devices
  → Preferred for configuring network equipment

### Access Methods

* **Console:** Local physical access (initial setup, recovery)
* **SSH:** Secure remote CLI access (**recommended**)
* **Telnet:** Insecure remote access (plaintext credentials)

### Terminal Emulation Software

* Used to access devices via console or network
* Examples: PuTTY, Tera Term, SecureCRT

---

## IOS Navigation

### Primary Command Modes

* **User EXEC (`>`):**

  * Limited monitoring commands
* **Privileged EXEC (`#`):**

  * Full access to commands and features

### Configuration Modes

* **Global Configuration (`(config)#`):** Device-wide settings
* **Line Configuration (`(config-line)#`):** Console, VTY, AUX
* **Interface Configuration (`(config-if)#`):** Ports and interfaces

### Navigating IOS Modes

* `enable` → User EXEC → Privileged EXEC
* `configure terminal` → Global Config
* `exit` → One level up
* `end` or `Ctrl+Z` → Privileged EXEC

---

## IOS Command Structure

### Command Components

* **Keyword:** Predefined IOS command
* **Argument:** User-supplied value

### Syntax Conventions

* **Bold text:** Enter exactly as shown
* *Italic text:* User-defined values
* `[ ]` Optional element
* `{ }` Required element
* `{x | y}` Required choice

### Help Features

* **Context-sensitive help (`?`):**

  * Shows available commands, keywords, and arguments
* **Command syntax checker:**

  * Identifies errors and incomplete commands

### Hot Keys & Shortcuts

* `Tab` → Auto-complete commands
* `↑ / Ctrl+P` → Command history
* `Ctrl+C` → Abort command
* `Ctrl+Z` → Exit configuration mode
* `Ctrl+Shift+6` → Stop pings/traceroutes

---

## Basic Device Configuration

### Device Naming

* Set a unique **hostname**
* Rules:

  * Start with a letter
  * No spaces
  * Letters, digits, dashes only
  * ≤ 64 characters

### Password Configuration

* Secure:

  * User EXEC (console)
  * Privileged EXEC
  * VTY (Telnet/SSH)

**Password Best Practices**

* ≥ 8 characters
* Mix upper/lowercase, numbers, symbols
* Avoid reused or common passwords

### Encrypt Passwords

* `service password-encryption`
* Prevents plaintext passwords in configs

### Banner Message

* Warns unauthorized users
* Command:

  ```
  banner motd # Unauthorized access prohibited #
  ```

---

## Save Configurations

### Configuration Files

* **running-config**

  * Stored in RAM
  * Active configuration
  * Lost on reboot
* **startup-config**

  * Stored in NVRAM
  * Loaded at boot

### Save Configuration

```
copy running-config startup-config
```

### Restore or Remove Changes

* Remove commands manually
* `reload` → Discards unsaved changes
* `erase startup-config` → Factory reset (followed by reload)

### Backup to Text File

* Capture configs via terminal logging
* Useful for documentation and recovery

---

## Ports and Addresses

### IP Addressing

* **IPv4:** 32-bit, dotted decimal
* **Subnet Mask:** Identifies network vs host
* **Default Gateway:** Router to reach remote networks
* **IPv6:** 128-bit, hexadecimal, colon-separated

### Interfaces and Media

* Communication depends on:

  * Device interfaces
  * Network ports
  * Media type (copper, fiber, wireless)
* Media choice depends on:

  * Distance
  * Environment
  * Speed
  * Cost

---

## Configure IP Addressing

### End Devices

* **Manual configuration:** Static IP, subnet mask, gateway
* **Automatic configuration:** DHCP (default)
* IPv6 uses **DHCPv6** or **SLAAC**

### Switch Virtual Interface (SVI)

* Required for **remote switch management**
* Steps:

  ```
  interface vlan 1
  ip address <ip> <subnet-mask>
  no shutdown
  ```

---

## Verify Connectivity

### Verification Tools

* `ping` → Test reachability
* Check interface status (`no shutdown`)
* Confirm IP settings on hosts and switches

---

## Module Takeaways

* Cisco IOS uses structured command modes
* Secure access with passwords and encryption
* Always save configurations
* IP addressing is required for communication
* Use `ping` to verify end-to-end connectivity

---

## Tags


#cisco #itn #networking
#ios #cli #switch-configuration
#ip-addressing #dhcp #svi
#network-security #ccna
#packet-tracer


