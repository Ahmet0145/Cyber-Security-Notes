# 🕵️‍♂️ Mission 0x01: Linux Terminal Navigation & System Reconnaissance

## 📜 Operational Briefing: First Day on the SOC Team

You just joined the Cyber Operations Support Team (SOC) as a Junior Analyst. Today was supposed to be your onboarding day with a guided tour of the tools and systems. However, cyber operations rarely go according to plan.

Your team leader had to leave abruptly to handle an ongoing high-severity incident. Before running out the door, they left a yellow sticky note on your monitor:

> **[TEAM LEADER NOTE]**
> *Welcome aboard! I had to step away abruptly to support an active threat response, so I couldn't brief you in person.*
> *Our day-to-day security operations rely heavily on the **Linux Command Line**. I've placed a few initial tasks on your system to help you hit the ground running.*
> *Fire up your terminal, navigate through the filesystem, and locate the `mission_brief.txt` file to get started.*
> *Best of luck!*

---

## 🖥️ Understanding the Interface: Why the Command Line?

Why do security professionals prefer a text-based **Command-Line Interface (CLI)** over a graphical user interface (GUI)?

* **Speed & Efficiency:** Complex system tasks, log searching, and batch file manipulations happen in milliseconds.
* **Granular Control:** Direct interaction with the operating system kernel without GUI limitations.
* **Tool Compatibility:** The vast majority of professional security assessment tools only run inside terminal environments.

---

## 🎯 Step-by-Step Reconnaissance & Navigation Guide

### Step 1: "Where Am I?" (`pwd`)
When opening a terminal session, you must establish your current working environment. The **Print Working Directory** (`pwd`) command displays your current location in the filesystem.

```bash
ubuntu@soc-workstation:~$ pwd
/home/ubuntu
```
Step 2: "What Is Around Me?" (ls and ls -la)
To inspect files and directories residing in your current location, use the List (ls) command:
```
ubuntu@soc-workstation:~$ ls
Desktop  Downloads  Documents  logs  projects
```
To reveal hidden files (files prefixed with a dot .) along with file permissions, ownership, and creation dates, append the -la flag:

```
ubuntu@soc-workstation:~$ ls -la
drwxr-xr-x 24 ubuntu ubuntu 4096 Feb 10 10:48 .
drwxr-xr-x  3 root   root   4096 Feb 10 10:36 ..
-rw-------  1 ubuntu ubuntu  439 Feb 10 06:47 .bash_history
-rw-r--r--  1 ubuntu ubuntu  111 Oct  3  2024 .secret_config
```
Step 3: Traversing the Filesystem (cd)
To navigate into a target directory, use the Change Directory (cd) command. To move back up one level in the directory hierarchy, use cd ...
```
# Navigate into the Documents directory:
ubuntu@soc-workstation:~$ cd Documents/

# Return to the previous parent directory:
ubuntu@soc-workstation/Documents$ cd ..
```
Step 4: Locating Target Artifacts (find)
Your supervisor left a file named mission_brief.txt somewhere inside the user directory. Use the Find utility to discover its exact path:

```
ubuntu@soc-workstation:~$ find ~ -name mission_brief.txt
/home/ubuntu/projects/secret/mission_brief.txt
```
Step 5: Reading File Contents (cat)
Once the complete file path is identified, display its contents to the screen using the Concatenate (cat) command:
```
ubuntu@soc-workstation:~$ cat /home/ubuntu/projects/secret/mission_brief.txt

==================================================
 MISSION BRIEFING ACKNOWLEDGED.
 Excellent job navigating to the file.
 Your next assignment is to generate a basic system status report:
 1. Who are you currently logged in as? (whoami)
 2. What kernel version is running? (uname -a)
 3. What is the total disk usage? (df -h)
 4. What are the specific Linux distribution details? (cat /etc/os-release)
==================================================
```

| Investigation Step | Command | Operational Purpose |
| :--- | :--- | :--- |
| **User Identity** | `whoami` | Identifies the active user session name. |
| **Kernel & OS Specs** | `uname -a` | Displays system architecture (x86_64), hostname, and kernel release. |
| **Storage Utilization** | `df -h` | Summarizes mounted disk space in human-readable formats (GB/MB). |
| **Distribution Details** | `cat /etc/os-release` | Reads system release configuration files for OS details (Ubuntu/Debian). |
