# 💻 Hardware Architecture & System Fundamentals for Cybersecurity

Welcome to my hardware documentation repository. As a First-Year Computer Engineering student specializing in Cybersecurity, I created this project to document my learning journey, technical research, and practical insights.

This documentation serves as a practical knowledge base covering essential hardware components, their interconnections, and their relevance to system performance and security operations.

---

## 📌 Table of Contents

A- [Overview & System Architecture](#overview--system-architecture)<br>
B- [Core Hardware Components](#core-hardware-components)
  * [Motherboard](#1-motherboard)
  * [CPU (Central Processing Unit)](#2-cpu-central-processing-unit)
  * [RAM (Random Access Memory)](#3-ram-random-access-memory)
  * [Storage (SSD / HDD)](#4-storage-ssd--hdd)
  * [GPU (Graphics Processing Unit)](#5-gpu-graphics-processing-unit)
  * [PSU](#6-psu)
  * [Network Adapter (NIC / Wi-Fi)](#7-network-adapter-nic--wi-fi)
  * [Input/Output (I/O) Devices](#8-inputoutput-io-devices)

C- [Boot Process (What Happens When You Press Start?)](#boot-process-what-happens-when-you-press-start)<br>
D- [Security & Forensics Perspective](#security--forensics-perspective)

---

# A-💻 Computer Hardware & Security Fundamentals

<img width="1024" height="682" alt="image" src="https://github.com/user-attachments/assets/56d41eb5-6b65-49ec-a7df-8130841f1e2d" />

## 📌 Introduction
Computer hardware consists of the physical, tangible components that make up a computer system. Understanding these core components, how they interact, and how data moves between them is essential for both system architecture and cybersecurity fundamentals.

Above is an overview of the key internal hardware components that form a modern PC system. Let's examine each of these components one by one!
-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

## 🖥️ 1. Motherboard

<img width="1407" height="768" alt="Gemini_Generated_Image_g60v8jg60v8jg60v" src="https://github.com/user-attachments/assets/1d6b49e0-be5f-4dbf-a903-27a1a5c8426d" />


### 📌 Overview & System Role
The motherboard is the primary printed circuit board (PCB) inside a computer system. Often described as the "backbone" or "nervous system" of a PC, its main function is to physically hold and electrically connect all hardware components. It contains various buses (data pathways), sockets, and slots that allow the CPU, RAM, storage drives, and expansion cards (like GPUs) to communicate with each other seamlessly. Without the motherboard, these components would remain isolated and unable to exchange data.

#### 🛡️ Security & Practical Perspective
* **First Line of Control (BIOS/UEFI):** The motherboard contains the BIOS/UEFI software, which powers on the system before the Operating System loads. Setting a strong BIOS password prevents unauthorized users from changing boot settings.
* **Physical Security:** Because the motherboard holds all vital components, physical security is critical. If an attacker gets direct physical access to the motherboard, they can manipulate hardware or steal storage devices.
-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

## ⚙️ 2. CPU (Central Processing Unit)

<img width="1407" height="768" alt="Gemini_Generated_Image_jixao1jixao1jixa" src="https://github.com/user-attachments/assets/a2b7aecd-5401-4b24-b273-2110c2daf5e8" />


### 📌 Overview & System Role
The Central Processing Unit (CPU) is often considered the "brain" of the computer. Its primary role is to fetch, decode, and execute instructions provided by software and the operating system. It performs all fundamental arithmetic, logical, and input/output operations required to run applications.

#### 🛡️ Security & Practical Perspective
* **Code Execution & Malware Analysis:** Since all software runs directly on the CPU, understanding processor execution helps in reverse engineering and analyzing how malicious code operates.
* **Hardware Virtualization:** Modern CPUs provide hardware-assisted virtualization (e.g., Intel VT-x, AMD-V), which is essential for running isolated Virtual Machines (Sandboxes) to safely analyze untrusted files.
 ---

## 🖥️ 3. RAM (Random Access Memory)

<img width="1264" height="842" alt="Gemini_Generated_Image_" src="https://github.com/user-attachments/assets/1a6395b1-f6e3-4957-94ef-c74005742a40" />


### 📌 Overview & System Role
RAM functions like a computer's short-term memory. It temporarily stores the data and programs that the CPU actively uses while the system is running. Because RAM is volatile, all data stored in it is instantly erased when the computer is turned off. Modern desktop systems use high-speed standards such as DDR4 or DDR5 to process tasks quickly.

🛡️ **Security & Practical Perspective**
* **Temporary Data Exposure:** Sensitive information, such as passwords or unencrypted text, is temporarily stored in RAM while in use. If a system is compromised while running, an attacker could potentially access this active memory data.
* **Malware Execution:** Malicious software needs system memory to run its code. Monitoring active RAM processes helps security tools detect and block suspicious activity before it causes harm.
---

## 💾 4. Storage (SSD / HDD)

<img width="1408" height="768" alt="Gemini_Generated_Image_lqn4bilqn4bilqn4" src="https://github.com/user-attachments/assets/d85e570c-e59e-43cf-bf5c-42da6ef298c6" />


### 📌 Overview & System Role
Storage devices are used to save data permanently, even when the computer is powered off. They are comparable to human long-term memory. 

* **HDDs (Hard Disk Drives):** Use older technology with moving mechanical parts, which limits their performance. However, they remain popular for providing large storage capacity at a lower cost.
* **SSDs (Solid State Drives):** Have no moving parts and use memory chips, allowing for significantly faster read and write speeds.
* **Connectivity:** Storage devices connect to the motherboard via **SATA cables** or direct **PCI Express / M.2 slots**.

#### 🛡️ Security & Practical Perspective
* **First Line of Control (BIOS/UEFI):** Setting a strong BIOS password prevents unauthorized users from changing boot settings and accessing storage options.
* **Physical Security:** Because storage devices hold all permanent data, physical security is critical. If an attacker gains direct physical access, they can manipulate or steal the storage drive.
* **Full-Disk Encryption:** Encrypting the drive (e.g., BitLocker) protects sensitive files from being accessed if the physical drive or device is lost or stolen.
* **Data Recovery & Digital Forensics:** Deleting a file from a storage drive does not immediately erase its raw data. Cybersecurity experts analyze storage drives to recover deleted evidence and track system activity.

---

## 🎮 5. GPU (Graphics Processing Unit)

<img width="1408" height="768" alt="Gemini_Generated_Image_y30t1ey30t1ey30t" src="https://github.com/user-attachments/assets/a4f56f15-8a2e-49a4-8dcb-b1f45d523ebf" />


### 📌 Overview & System Role
The graphics card (GPU) is comparable to the visual cortex of our brain. While our eyes pick up visual information and the brain processes it into images, the graphics card receives data from the operating system and applications, then processes and outputs visual information to displays. 

Graphics cards connect directly to the **PCI Express (PCIe) slots** on the motherboard.

#### 🛡️ Security & Practical Perspective
* **Physical Security:** Because high-performance GPUs are valuable physical components connected via PCIe, physical security is critical to prevent hardware theft or direct physical manipulation.
* **GPU-Accelerated Password Cracking:** Attackers use the massive parallel processing power of GPUs for high-speed brute-force attacks and hash cracking (e.g., Hashcat).
* **Malicious Mining (Cryptojacking):** Malware often targets high-performance GPUs to illegally mine cryptocurrency in the background, consuming system resources and causing hardware overheating.

---

## ⚡ 6. Power Supply Unit (PSU)

<img width="1024" height="559" alt="image" src="https://github.com/user-attachments/assets/b646f4ef-70ea-4358-bd11-f4ac6b17cc03" />


### 📌 Overview & System Role
Every system needs power. Just as our heart pumps blood to our organs, a PSU supplies energy to all system components. The PSU takes power from a wall outlet and converts high-voltage AC into regulated low-voltage DC power. It distributes this energy via various connectors like the main motherboard connector, PCIe, and Molex connectors.

If components require more power than the PSU can provide, the system will fail or abruptly shut down.

#### 🛡️ Security & Practical Perspective
* **Physical Security:** Direct physical access to the PSU or its external power switch allows attackers to abruptly cut off system power, completely bypassing operating system-level shutdown protocols.
* **System Stability & Data Integrity:** Subpar or failing power units cause sudden voltage drops and unexpected shutdowns, which can corrupt data currently being written to storage or corrupt memory states.
* **Power Tampering & Availability Threats:** Disrupting or manipulating clean power delivery can lead to physical hardware damage or act as a physical Denial-of-Service (DoS) attack on crucial server infrastructure.

---

## 🌐 7. Network Adapter (NIC / Wi-Fi)

<img width="1408" height="768" alt="Gemini_Generated_Image_1gutie1gutie1gut" src="https://github.com/user-attachments/assets/0922b25a-bb34-4d83-8b99-814c0269215b" />


### 📌 Overview & System Role
Just as we use our vocal cords to communicate with our environment, a network adapter lets computers communicate with other systems and networks. Network adapters come in wireless (Wi-Fi) and wired (Ethernet) variants. Often they are embedded directly into the motherboard, but they can also be added as dedicated expansion cards connecting via **PCI Express (PCIe) ports**.

#### 🛡️ Security & Practical Perspective
* **Physical Security:** Physical access to network ports allows attackers to attach rogue hardware devices, network taps, or malicious USB-to-Ethernet dongles to intercept or bypass network monitoring.
* **MAC Address Spoofing:** Every network adapter has a physical hardware address (MAC address). Attackers can spoof MAC addresses to bypass network access control (NAC) policies and filters.
* **Eavesdropping & Packet Sniffing:** Network adapters receive data frames from the network. In promiscuous mode, an adapter captures all passing network traffic, allowing attackers to perform packet sniffing and eavesdrop on unencrypted data.

---

## ⌨️ 8. Input / Output (I/O) Devices

<img width="1408" height="768" alt="Gemini_Generated_Image_fnbo2bfnbo2bfnbo" src="https://github.com/user-attachments/assets/a430ee8c-59da-454a-a6bd-10e72fdfce23" />


### 📌 Overview & System Role
Just as we have senses to obtain information for our brains to process and then act on, computers have input and output devices. Input devices (such as keyboards, mice, microphones, and scanners) send data to the computer, while output devices (such as monitors, printers, and speakers) receive data from the computer to display or present results.

Common connection interfaces for these peripherals include **USB**, **HDMI**, and **DisplayPort**.

#### 🛡️ Security & Practical Perspective
* **Physical Security:** Direct physical access to I/O ports allows attackers to attach hardware keyloggers to record keystrokes or connect malicious USB Rubber Ducky devices to execute automated command injection scripts.
* **Malicious Peripherals (BadUSB):** USB devices can be programmed to spoof other device types (such as pretending to be a keyboard), allowing them to bypass traditional software security checks and deliver payloads.
* **Display & Peripheral Eavesdropping:** External monitors and audio devices can be targeted for unauthorized screen capture, shoulder surfing, or audio interception to gather sensitive credentials and data.

---

## 🚀 C-Boot Process (What Happens When You Press Start?)

Now that the core components are installed in the computer system, it is time to boot up the system. We can compare this to how we wake up in the morning and do a quick check to see if everything is working. Only when everything is OK, do we get up and start our day. The diagram below shows the steps a computer system goes through before it shows you a working interface in the form of an Operating System.

```mermaid
graph LR
    A[Press Power Button] --> B[Firmware Starts]
    B --> C[POST]
    C --> D[Select Boot Device]
    D --> E[Start Bootloader]
```

Step 1: Press the Power Button: Pressing the power button sends an electrical signal to the Power Supply Unit (PSU) to initiate power flow throughout the system. Think of this as our body receiving oxygen upon waking up, allowing the heart to start pumping blood.

Step 2: Firmware Starts: Once power reaches the components, system firmware initializes to bring hardware to life. The central system managing this is the UEFI (Unified Extensible Firmware Interface). Note: While the legacy term BIOS is still commonly used, modern systems have almost entirely replaced BIOS with UEFI.

Step 3: Power-On Self Test (POST): Before handing over control, the UEFI runs the Power-On Self Test (POST). This routine verifies that all required hardware (CPU, RAM, Storage, etc.) is physically present, correctly configured, and operating without errors.

Step 4: Select Boot Device: After POST succeeds, the system determines where to load the operating system from. The UEFI checks a prioritized list of boot devices (such as an NVMe SSD, HDD, or external USB drive) to locate the OS installation.

Step 5: Initiate Bootloader: Once the boot device is selected, the UEFI initializes the device's Bootloader. The bootloader transfers the Operating System files into Random Access Memory (RAM) and officially hands full hardware control over to the OS.

---

## 🛡️ D-Security & Forensics Perspective

Understanding core hardware components is essential for both defensive cybersecurity operations and digital forensics investigations. Physical components directly dictate how data is stored, processed, and preserved during an incident response.

### 🔍 Key Cyber Security & Forensic Takeaways

* **Volatile Memory Analysis (RAM Forensics):**  
  RAM contains active execution states, unencrypted passwords, network sockets, and running malware in real time[cite: 1]. Because RAM loses all data when power is lost (volatility), forensic acquisition of memory must be performed *live* before shutting down a suspect system during incident response[cite: 1].

* **Non-Volatile Data Retention (Storage Persistence):**  
  Storage devices (SSDs, HDDs) hold persistent evidence, operational logs, and deleted files[cite: 1]. Forensic examiners create bit-stream physical copies (forensic images) of these drives to analyze artifacts without altering the original evidence[cite: 1].

* **Firmware & Bootkit Threats:**  
  Malicious code targeting the UEFI/BIOS level (known as bootkits) operates below the operating system[cite: 1]. These persistent threats survive OS reinstallations and bypass traditional software-level antivirus protection[cite: 1].

* **Hardware Interception & Physical Attack Vectors:**  
  Direct physical access allows attackers to deploy rogue hardware keyloggers, network taps, or malicious USB peripherals (BadUSB) to completely bypass OS-level controls and authentication[cite: 1].
