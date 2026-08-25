# 🔢 Data Representation: Binary, Hexadecimal & Color Encoding in Security

---

## 📌 1. Number Systems & Memory Representation

Computers use physical states (low/high voltage range, magnetic polarity, light presence in fiber optics) to read and write data as binary digits: **0** and **1**.

### Base Systems Overview

| System | Base | Available Digits | Grouping / Bit Equivalency | Primary Use Case |
| :--- | :--- | :--- | :--- | :--- |
| **Decimal** | Base-10 | `0 - 9` | N/A | Human everyday tasks (counting, prices, time). |
| **Binary** | Base-2 | `0` and `1` | 1 bit = 1 binary digit | Low-level machine processing & hardware logic gates. |
| **Hexadecimal** | Base-16 | `0 - 9` and `A - F` | 1 hex digit = 4 bits (1 nibble) | Compact representation of memory addresses & binary data. |
| **Octal** | Base-8 | `0 - 7` | 1 octal digit = 3 bits | File permission masks (e.g., Linux `chmod 755`). |

---

## 🔣 2. Conversions & Mathematical Mechanics

Understanding base conversions is essential for analyzing memory dumps, raw packet captures, and executable binaries.

### Positional Notation Formula
To convert a base-$N$ number with digits $d_k d_{k-1} \dots d_1 d_0$ to decimal:
$$\text{Decimal Value} = \sum_{i=0}^{k} (d_i \times N^i)$$

### 4-Bit Binary to Hexadecimal Mapping

| Decimal | Hexadecimal | 4-Bit Binary | Decimal | Hexadecimal | 4-Bit Binary |
| :---: | :---: | :---: | :---: | :---: | :---: |
| `0` | `0` | `0000` | `8` | `8` | `1000` |
| `1` | `1` | `0001` | `9` | `9` | `1001` |
| `2` | `2` | `0010` | `10` | `A` | `1010` |
| `3` | `3` | `0011` | `11` | `B` | `1011` |
| `4` | `4` | `0100` | `12` | `C` | `1100` |
| `5` | `5` | `0101` | `13` | `D` | `1101` |
| `6` | `6` | `0110` | `14` | `E` | `1110` |
| `7` | `7` | `0111` | `15` | `F` | `1111` |

---

## 🎨 3. Color Encoding: From 8 Colors to 16 Million Colors

Computers construct display colors by mixing primary light components: **Red (R)**, **Green (G)**, and **Blue (B)**.

### Basic 3-Bit Palette (8 Colors)
When each primary color component is strictly `ON` (1) or `OFF` (0), the system yields $2^3 = 8$ total color states:

```
R (Bit 2) ──┐
G (Bit 1) ──┼──► 3 Bits ──► 2 × 2 × 2 = 8 Combinations
B (Bit 0) ──┘
```
* `000` — All off — **Black**
* `001` — Blue on — **Blue**
* `010` — Green on — **Green**
* `100` — Red on — **Red**
* `011` — Green & Blue on — **Cyan**
* `101` — Red & Blue on — **Magenta**
* `110` — Red & Green on — **Yellow**
* `111` — All on — **White**

### True Color Palette (24-Bit / 16 Million Colors)
Expanding each color component from 1 bit to **8 bits (1 Byte / 1 Octet)** allows 256 intensity levels per channel ($2^8 = 256$):

$$\text{Total Color Space} = 256 \times 256 \times 256 = 16,777,216 \text{ colors}$$

A 24-bit color string (e.g., `10100011 11101010 00101010`) is inconvenient to read, so it is formatted into a 6-digit Hex code: `#A3EA2A`.
```
HEX COLOR CODE: # A3 EA 2A
                  │  │  │
┌─────────────────┘  │  └─────────────────┐
▼                    ▼                    ▼
[ Red Byte ]      [ Green Byte ]       [ Blue Byte ]
Hex: A3           Hex: EA              Hex: 2A
Dec: 163          Dec: 234             Dec: 42
Bin: 10100011     Bin: 11101010        Bin: 00101010
```
---

## 🛡️ 4. Security Perspective

Understanding number systems (Binary, Hexadecimal, Octal) and how data is stored in memory forms the foundation of cybersecurity and digital forensics.

### 🔍 Why Does It Matter?

* **Binary System & Weak Passwords:**  
  Computers only understand `0`s and `1`s. Passwords and data are stored in memory as these bits. Attackers use automated tools to guess weak or predictable passwords (like sequential keyboard patterns such as `1q2w3e4r5t`) using this binary logic.

* **Hexadecimal (Hex) & Malware Analysis:**  
  Reading long streams of `0`s and `1`s is difficult, so data is grouped into 4-bit chunks and represented as Hexadecimal (`0-9` and `A-F`). When inspecting malware, suspicious files, or raw network traffic, complex code appears in `Hex` format.

* **Octal & File Permissions:**  
  In Linux/Unix systems, file access permissions (who can read, write, or execute) are configured using the `Octal` (0-7) number system. Misconfigured permissions can allow unauthorized users to escalate their privileges to administrator.

* **Colors & Hidden Data (Steganography):**  
  On-screen colors are stored as 24-bit (3 Bytes) RGB values. Attackers sometimes hide secret messages or malicious code inside image files by subtly tweaking the smallest bits of these color codes without noticeably changing the image's appearance.
