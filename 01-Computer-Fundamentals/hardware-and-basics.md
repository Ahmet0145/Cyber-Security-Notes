# 💻 Hardware Architecture & System Fundamentals for Cybersecurity

Welcome to my hardware documentation repository. As a First-Year Computer Engineering student specializing in Cybersecurity, I created this project to document my learning journey, technical research, and practical insights.

This documentation serves as a practical knowledge base covering essential hardware components, their interconnections, and their relevance to system performance and security operations.

---

## 📌 Table of Contents
1. [Overview & System Architecture](#overview--system-architecture)
2. [Core Hardware Components](#core-hardware-components)
   - [Motherboard)](#1-motherboard)
   - [CPU (Central Processing Unit)](#2-cpu-central-processing-unit)
   - [RAM (Random Access Memory)](#3-ram-random-access-memory)
   - [Storage (SSD / HDD)](#4-storage-ssd--hdd)
   - [GPU (Graphics Processing Unit)](#5-gpu-graphics-processing-unit)
   - [PSU & Cooling Systems](#6-psu--cooling-systems)
3. [Security & Forensics Perspective](#security--forensics-perspective)

---

# 💻 Computer Hardware & Security Fundamentals

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

<img width="1264" height="842" alt="Gemini_Generated_Image_iqfj8piqfj8piqfj" src="https://github.com/user-attachments/assets/672a2ac8-d809-4774-a6c6-1a7cc61108db" />


### 📌 Overview & System Role
RAM functions like a computer's short-term memory. It temporarily stores the data and programs that the CPU actively uses while the system is running. Because RAM is volatile, all data stored in it is instantly erased when the computer is turned off. Modern desktop systems use high-speed standards such as DDR4 or DDR5 to process tasks quickly.

🛡️ **Security & Practical Perspective**
* **Temporary Data Exposure:** Sensitive information, such as passwords or unencrypted text, is temporarily stored in RAM while in use. If a system is compromised while running, an attacker could potentially access this active memory data.
* **Malware Execution:** Malicious software needs system memory to run its code. Monitoring active RAM processes helps security tools detect and block suspicious activity before it causes harm.
