# 🔤 Data Encoding: Character Sets & Text Representation

---

## 📌 1. Introduction to Character Encoding

Computers process and store all data as binary digits (**0** and **1**). To display text, letters, punctuation, and emojis on screens, systems rely on **Encodings**—agreed-upon standards that map numeric values (code points) to specific characters.

```
┌─────────────────┐       Encoding Rule       ┌─────────────────┐
│ Character: "A"  │ ────────────────────────► │ Binary: 01000001│
└─────────────────┘  (e.g., ASCII Code 65)    └─────────────────┘
```
When a sender and a recipient use different encoding standards to read the same file, the software misinterprets the underlying numbers, resulting in unreadable text known as **garbled text / gibberish**.

---

## 🔠 2. The Evolution of Character Sets

### 1. ASCII (American Standard Code for Information Interchange)
Introduced in 1963, ASCII was designed as a small "bilingual dictionary" between English text and numeric codes.

* **Size:** 7 bits per character ($2^7 = 128$ total characters, ranging from 0 to 127).
* **Coverage:** English uppercase/lowercase letters, digits (`0-9`), basic punctuation marks, and control characters (e.g., Newline `\n`).

#### ASCII Sample Reference Table

| Decimal | Hexadecimal | Binary | Symbol | Description |
| :---: | :---: | :---: | :---: | :--- |
| `48` | `30` | `00110000` | `0` | Digit Zero |
| `57` | `39` | `00111001` | `9` | Digit Nine |
| `65` | `41` | `01000001` | `A` | Uppercase A |
| `88` | `58` | `01011000` | `X` | Uppercase X |
| `89` | `59` | `01011001` | `Y` | Uppercase Y |
| `90` | `5A` | `01011010` | `Z` | Uppercase Z |
| `91` | `5B` | `01011011` | `[` | Opening bracket |
| `92` | `5C` | `01011100` | `\` | Backslash |
| `93` | `5D` | `01011101` | `]` | Closing bracket |

#### Practical Example: Encoding "TryHackMe"
Saving the string `TryHackMe\n` to a file yields the following representations on disk:

* **Binary Stream:**  
  `01010100 01110010 01111001 01001000 01100001 01100011 01101011 01001101 01100101 00001010`
* **Hexadecimal Stream:**  
  `54 72 79 48 61 63 6b 4d 65 0a`
* **Decimal Sequence:**  
  `124 162 171 110 141 143 153 115 145 012`

---

### 2. Extended ASCII & Regional European Standards (ISO/IEC 8859)
ASCII's 7-bit limitation could not accommodate non-English regional characters (e.g., `ñ`, `ß`, `ł`, `č`, `ş`). By expanding to **8 bits (1 Byte)**, 128 additional character slots were created (totaling 256 states). 

Because 256 slots were still insufficient for all global scripts, regional standards were established:
* **ISO-8859-1 (Latin-1):** Designed for Western European languages (German `ß`, French `é`, Spanish `ñ`).
* **ISO-8859-2 (Latin-2):** Designed for Central and Eastern European languages (Polish `ł`, Czech `č`, Hungarian `ő`).

> **The Issue:** If a document is saved using ISO-8859-1 and later opened with an ISO-8859-2 viewer, identical byte values map to entirely different letters, breaking text integrity.

---

### 3. Unicode: The Universal Standard
To solve global fragmentation, **Unicode** was created as a single universal standard. It assigns a unique code point (format: `U+XXXX`) to every character across all modern, historical, and symbolic writing systems.

#### Character Count Escalation
* **English:** 26 letters (52 uppercase/lowercase).
* **Arabic:** Over 250 characters (including ligatures and diacritics).
* **Japanese (JIS X 0208):** 6,879 characters (Kanji logographs).
* **Chinese (GB 18030-2022):** Over 87,887 Hanzi characters.
* **Unicode 17.0:** Contains close to **157,000 characters**, including almost **4,000 emoji sequences**.

#### Code Point Examples
* `U+0041` = Latin "A"
* `U+03A9` = Greek "Ω"
* `U+3042` = Japanese Hiragana "あ"
* `U+9F8D` = Chinese Hanzi "龍" (Dragon)
* `U+1F60A` = Emoji "😊"

---

## ⚙️ 3. Unicode Transformation Formats: UTF-8, UTF-16 & UTF-32

While Unicode defines *which number* represents *which character*, **UTF standards** define *how those numbers are stored in bytes*.

```
┌──────────┬──────────────────────┬─────────────────────────────────────────────────────────────┐
│ Encoding │ Byte Length          │ Operational Mechanics & Efficiency                          │
├──────────┼──────────────────────┼─────────────────────────────────────────────────────────────┤
│ UTF-8    │ Variable (1–4 Bytes) │ Uses 1 byte for ASCII (0x00–0x7F). Highly efficient & fully │
│          │                      │ backward-compatible with ASCII. Dominates the web.          │
├──────────┼──────────────────────┼─────────────────────────────────────────────────────────────┤
│ UTF-16   │ Variable (2 or 4 B)  │ Uses 2 bytes for common Latin/Asian characters. Uses pairs  │
│          │                      │ (4 bytes total) for emojis and rare historical scripts.     │
├──────────┼──────────────────────┼─────────────────────────────────────────────────────────────┤
│ UTF-32   │ Fixed (4 Bytes)      │ Every character takes exactly 4 bytes (32 bits). Simple to  │
│          │                      │ index in memory, but wastes storage space for Latin text.   │
└──────────┴──────────────────────┴─────────────────────────────────────────────────────────────┘
```
### Encoding Comparison Examples

* **Letter `A` (`U+0041`):**
  * **UTF-8:** `41` (1 byte)
  * **UTF-16:** `0041` (2 bytes)
  * **UTF-32:** `00000041` (4 bytes)

* **Emoji `🔥` (`U+1F525`):**
  * **UTF-8:** Requires 4 bytes
  * **UTF-16:** Requires a surrogate pair (`U+D83D U+DD25`, 4 bytes total)
  * **UTF-32:** `0001F525` (4 bytes)

* **Smiley Face `😊` (`U+1F60A`):**
  * **UTF-32 Binary:** `00000000 00000001 11110110 00001010`

---
## 🛡️ 4. Security Perspective

In cybersecurity and digital forensics, understanding character encoding—how letters, numbers, and symbols are converted into bits and bytes—is critical when analyzing files, system logs, and network traffic.

### 🔍 Practical Security Insights

* **Decoding Gibberish in Forensic Investigations:**  
  When analyzing raw memory dumps, network packets, or suspicious text files, security tools often encounter "gibberish" characters. This non-readable text happens when a system attempts to read data using the wrong encoding standard (for example, reading a UTF-8 or ISO-8859 file as basic 7-bit ASCII). Security analysts must identify the original encoding to correctly reconstruct the evidence.

* **Binary and Hexadecimal Inspection in Malware Analysis:**  
  Human analysts cannot easily read continuous streams of binary digits (`01010100...`). Because of this, forensic tools present binary text data in Hexadecimal format (`54 72 79...`). Recognizing how text string characters map to their Hex ASCII values (such as `41` for `A` or `0A` for a newline `\n`) allows security teams to manually spot hidden messages or embedded commands inside unknown files.

* **Unicode and Multi-Byte Character Risks:**  
  While traditional ASCII uses just 1 byte per character, Unicode standards like UTF-8, UTF-16, and UTF-32 allow characters—including foreign scripts, symbols, and emojis—to take up to 4 bytes. In security, attackers sometimes exploit the difference between fixed 1-byte systems and variable 1-to-4 byte systems. If a security program expects 1-byte ASCII input but receives multi-byte Unicode input (like complex Chinese Hanzi characters or emojis), it may miscalculate file sizes, truncate text, or drop parts of important security logs.

* **Regional Encoding Differences (ISO-8859):**  
  Different region-specific standards (such as ISO-8859-1 for Western Europe versus ISO-8859-2 for Central Europe) map the exact same byte values to entirely different letters. In international security monitoring, failing to account for regional character sets can cause log management systems to misinterpret usernames, file paths, or domain names during incident response.
