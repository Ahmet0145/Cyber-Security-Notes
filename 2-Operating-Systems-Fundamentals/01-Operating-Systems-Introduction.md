# Operating System (OS) Basics

## 🎯 What is an Operating System?
An **Operating System (OS)** is the core software layer that coordinates and manages all software and hardware components on a computer. It sits directly between the user, applications, and physical hardware, functioning as the central manager that unifies the system.
```
+-------------------------------------------------------------+
|                            USER                             |
+-------------------------------------------------------------+
|                        APPLICATIONS                         |
+-------------------------------------------------------------+
|                      OPERATING SYSTEM                       |
+-------------------------------------------------------------+
|                          HARDWARE                           |
+-------------------------------------------------------------+
```
---

## 🏗️ OS Architecture & Privilege Separation

Modern operating systems enforce strict system privilege layers to maintain stability and manage control:

* **Kernel Space:** The highly privileged core of the OS with unrestricted direct access to hardware (CPU, Memory, Storage).
* **User Space:** The isolated layer where standard applications run. Applications are prevented from accessing hardware directly. When an app needs to save a file or play sound, it must issue a **System Call** requesting the Kernel to execute the task on its behalf.

### ✈️ The Airport Analogy (How it Works)
To visualize how an OS operates, imagine a busy international airport:
* **Hardware (CPU, RAM, Storage):** The physical infrastructure—runways, airplanes, fuel systems, and radar equipment.
* **Applications (Web Browsers, Games):** The various airlines and passengers attempting to take off, land, and request services.
* **Operating System (Kernel & User Space):** Air Traffic Control (ATC). Kernel Space is the secured Control Tower where only authorized personnel work, while User Space represents the terminal and passengers requesting service via System Calls.

---

## 🛠️ Core Duties of an Operating System

| OS Responsibility | What the OS Does | Real-World Example |
| :--- | :--- | :--- |
| **Process Management** | Creates, schedules, prioritizes, and terminates running programs; manages CPU usage. | Running a browser, music player, and IDE simultaneously without freezing. |
| **Memory Management** | Allocates and reclaims RAM for active processes; uses Virtual Memory when RAM runs low. | Keeps open applications isolated so a crash in one doesn't bring down others. |
| **File System Management** | Organizes files into directories, manages file paths, permissions, and metadata. | Saving a file, setting permissions to "read-only", or searching directory trees. |
| **User Management** | Handles user accounts, authentication, and access control boundaries. | Enforcing password logins and keeping user profile folders private. |
| **Device Management** | Loads hardware drivers to provide a Hardware Abstraction Layer (HAL). | Plugging in a USB mouse or printer and having it work immediately. |

---

## 🌍 Operating System Types & Interfaces

Different hardware requirements and environments require specialized OS designs:

### 1. OS Interfaces (GUI vs. CLI)
* **Graphical User Interface (GUI):** A visual interface using windows, icons, menus, and mouse pointers. Designed for intuitive use.
* **Command-Line Interface (CLI):** A text-based interface where users type precise commands (e.g., `ls` or `dir`). Provides speed, automation, and full administrative control.

### 2. OS Classifications
* **Desktop:** Feature-rich GUIs, multitasking-focused (Windows 11, macOS, Ubuntu Desktop).
* **Server:** Headless (GUI-less), maximum uptime, multi-user, optimized for remote management (Linux Server, Windows Server).
* **Mobile:** Touch-optimized, battery-efficient, app sandboxing (Android, iOS).
* **Embedded / IoT:** Minimal footprint, runs dedicated functions on limited hardware (Real-Time OS, Embedded Linux).
* **Cloud / Virtual:** Lightweight, container-optimized, rapidly scalable (Alpine Linux, Bottlerocket).

---

## 🧪 Hands-on Lab Simulation (System Inspection)
In the practical exercise, we investigate an unknown/gifted machine to gather system specs and identify the installed OS:
* **Identifying OS Version:** Interacting with system utilities (`About This Computer` or CLI commands like `uname -a`) reveals the system is running **Ubuntu Linux**.
* **FileSystem Inspection:** Navigating through the `/home` directory via both GUI file manager and CLI commands (`ls /home`) to inspect file hierarchies and user configurations.

---

## 🛡️ Security Perspective: OS as a Security Foundation

Before any antivirus or external firewall is installed, the OS acts as the primary defense boundary:

* **Authentication:** Verifies user identity via credentials, tokens, or biometrics before granting environment access.
* **Access Control & Permissions:** Enforces strict boundaries on who can read, write, or execute sensitive system files.
* **Process Isolation:** Keeps memory spaces strictly separated so malicious processes cannot inspect or tamper with adjacent execution streams.
* **System Integrity Protection:** Safeguards critical system files and settings from unauthorized user-space modifications.
