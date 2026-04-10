[[CCNA]]


---

# Module 5 – Number Systems

**Course:** Introduction to Networks (ITN v7.0)
**Module Objective:** Calculate numbers between **decimal**, **binary**, and **hexadecimal** numbering systems.

---

## 🔢 Why Number Systems Matter in Networking

* Humans work in **decimal**
* Computers, routers, and switches work in **binary**
* Networking uses **hexadecimal** to make long binary values easier to read
* IP addresses, MAC addresses, and IPv6 rely on these conversions

---

## 5.1 Binary Number System

### Binary vs Decimal

| System  | Base | Digits |
| ------- | ---- | ------ |
| Decimal | 10   | 0–9    |
| Binary  | 2    | 0, 1   |

* Binary digits are called **bits**
* **8 bits = 1 byte**
* IPv4 addresses:

  * 32 bits total
  * Divided into **4 octets**
  * Written in **dotted decimal** for humans

---

### Binary Positional Notation

Each bit position represents a power of 2:

| Bit Position  | 2⁷  | 2⁶ | 2⁵ | 2⁴ | 2³ | 2² | 2¹ | 2⁰ |
| ------------- | --- | -- | -- | -- | -- | -- | -- | -- |
| Decimal Value | 128 | 64 | 32 | 16 | 8  | 4  | 2  | 1  |

---

### Binary → Decimal Conversion

**Steps**

1. Write positional values (128 → 1)
2. Multiply each bit by its position value
3. Add the results

**Example**

```
11000000 = 128 + 64 = 192
```

**IPv4 Example**

```
11000000.10101000.00001011.00001010
= 192.168.11.10
```

---

### Decimal → Binary Conversion

**Steps**

1. Start at 128 (MSB)
2. If the decimal value ≥ position value → write **1**, subtract
3. If not → write **0**
4. Continue down to 1

**Example: Convert 168**

```
128 → yes (1), remainder 40
64  → no  (0)
32  → yes (1), remainder 8
16  → no  (0)
8   → yes (1), remainder 0
4,2,1 → 0
```

**Result**

```
168 = 10101000
```

---

### Key Binary Takeaways

* Devices only understand **binary**
* IPv4 addresses are binary internally
* Decimal is just a human-friendly representation

---

## 5.2 Hexadecimal Number System

### What is Hexadecimal?

* **Base 16**
* Digits: `0–9` and `A–F`

| Hex | Decimal |
| --- | ------- |
| A   | 10      |
| B   | 11      |
| C   | 12      |
| D   | 13      |
| E   | 14      |
| F   | 15      |

---

### Why Hex is Used

* Easier to read than long binary strings
* **1 hex digit = 4 binary bits**
* Used for:

  * **IPv6 addresses**
  * **MAC addresses**

---

### IPv6 and Hexadecimal

* IPv6 = **128 bits**
* Every **4 bits = 1 hex digit**
* Total = **32 hex digits**
* Grouped into **hextets** (4 hex digits per group)

---

### Decimal → Hexadecimal Conversion

**Steps**

1. Convert decimal → binary (8 bits)
2. Split binary into **groups of 4**
3. Convert each group to hex

**Example: 168**

```
168 → 10101000
1010 1000
A    8
```

✅ **168 = A8**

---

### Hexadecimal → Decimal Conversion

**Steps**

1. Convert hex → 4-bit binary
2. Combine into 8-bit binary
3. Convert binary → decimal

**Example: D2**

```
D → 1101
2 → 0010
11010010 → 210
```

✅ **D2 = 210**

---

## 🧠 Module 5 Key Takeaways

* Binary is base 2 and used by all network devices
* Decimal is base 10 and used by humans
* IPv4 uses **binary internally**, decimal externally
* Hexadecimal is base 16 and simplifies binary representation
* IPv6 and MAC addresses rely heavily on hex
* Hex ↔ decimal conversions always pass through **binary**

---

## 🔖 Tags (Obsidian)


#cisco #itn #ccna
#number-systems
#binary #decimal #hexadecimal
#ipv4 #ipv6 #mac-address
#networking-basics


