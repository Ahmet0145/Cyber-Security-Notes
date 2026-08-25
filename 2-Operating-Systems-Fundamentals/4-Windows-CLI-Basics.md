# 🕵️‍♂️ Module 0x01: Command Line Interface (CLI) Fundamentals & Reconnaissance

## 📜 Operational Scenario: Onboarding under Fire

Welcome to your first shift with the **Cyber Security Operations Team**. Today was scheduled as an orientation day to familiarize you with internal tools and operating procedures. However, security operations rarely adhere to a quiet schedule.

Your team lead was abruptly called away to respond to a active security incident. Attached to your workstation monitor, you find a handwritten note:

> **[TEAM LEAD NOTICE]**  
> *Welcome to the unit! I had to step away unexpectedly to support an ongoing intrusion response.*  
> *Our daily analytical and administrative workflows rely entirely on the **Linux Command Line Interface**. I've staged a series of core tasks on this machine to help you get acquainted with the environment.*  
> *Launch your terminal, explore the local filesystem, and locate the `mission_brief.txt` file to receive your primary objectives.*  
> *Good luck!*

---

## 🖥️ System Access: Why We Rely on the Terminal

Before launching commands, it is essential to understand why security professionals prioritize text-based **Command Line Interfaces (CLI)** over Graphical User Interfaces (GUI):

* **Execution Velocity:** Performing repetitive administrative, log analysis, and system navigation tasks is significantly faster via text commands.
* **Granular System Access:** Provides direct, unabstracted interaction with the underlying operating system kernel and restricted directories.
* **Security Tooling Standard:** The vast majority of offensive, defensive, and digital forensics utilities are designed natively for command-line execution.

To launch your workspace, double-click the **Terminal** application shortcut located on your desktop environment.

---

## 🎯 Primary Objective 1: Navigation & Filesystem Exploration

### Step 1: Confirm Current Working Location (`pwd`)
When starting a terminal session, you must establish your current position within the system hierarchy. Use the **Print Working Directory** (`pwd`) command:

```bash
ubuntu@soc-workstation:~$ pwd
/home/ubuntu
```
Purpose: Outputs the absolute path of your active working directory.
---
### Step 2: Inspect Directory Contents (ls and ls -la)
To review the files and folders located in your current path, execute the List (ls) command:
```
ubuntu@soc-workstation:~$ ls
Desktop  Downloads  Documents  logs  projects
```
To display detailed metadata—such as file permissions, user ownership, file sizes, creation timestamps, and hidden items (files or folders starting with a dot .)—append the -la flags:
```
ubuntu@soc-workstation:~$ ls -la
total 144
drwxr-xr-x 24 ubuntu ubuntu 4096 Feb 10 10:48 .
drwxr-xr-x  3 root   root   4096 Feb 10 10:36 ..
-rw-------  1 ubuntu ubuntu  439 Feb 10 06:47 .bash_history
-rw-r--r--  1 ubuntu ubuntu  111 Oct  3  2024 .secret_config
drwxr-xr-x  2 ubuntu ubuntu 4096 Feb 27  2022 Desktop
drwxr-xr-x  6 ubuntu ubuntu 4096 Dec 11 12:45 Documents
```
---
### Step 3: Traverse the Filesystem (cd)
To move into a specific directory, use the Change Directory (cd) command. To step back up into the parent directory, use cd ..:
```
# Move into the targeted directory:
ubuntu@soc-workstation:~$ cd Documents/
ubuntu@soc-workstation/Documents$ pwd
/home/ubuntu/Documents

# Return to the parent directory:
ubuntu@soc-workstation/Documents$ cd ..
ubuntu@soc-workstation:~$ pwd
/home/ubuntu
```
---
### Step 4: Locate Staged Artifacts (find)
Your operational briefing mentioned a target file named mission_brief.txt hidden within your home environment. Use the Find utility to discover its exact location:
```
ubuntu@soc-workstation:~$ find ~ -name mission_brief.txt
/home/ubuntu/projects/secret/mission_brief.txt
```
Note: The ~ symbol represents the active user's home directory (/home/ubuntu).

Once identified, navigate directly to the target folder and confirm its presence:

```
ubuntu@soc-workstation:~$ cd /home/ubuntu/projects/secret/
ubuntu@soc-workstation/projects/secret$ ls
mission_brief.txt
```
---
### Step 5: Read Target File Contents (cat)
To inspect the text content of the target file without launching a full editor, use the Concatenate (cat) command:
```
ubuntu@soc-workstation/projects/secret$ cat mission_brief.txt

==================================================
 OPERATIONAL BRIEFING ACKNOWLEDGED
 Outstanding work navigating the filesystem!
 
 Your next assignment is to perform a baseline system audit:
 1. Active User Identity   -> (whoami)
 2. Operating System Kernel -> (uname -a)
 3. Disk Space Allocation   -> (df -h)
 4. OS Release Version      -> (cat /etc/os-release)
==================================================
```
---
## 📊 Primary Objective 2: Baseline System Audit & Information Gathering
Executing a rapid diagnostic assessment helps analysts identify the target operating environment, available resources, and system limits.

Step 1: Identify Active User Session
Determine the privileges and identity of your current session using whoami:
```
ubuntu@soc-workstation:~$ whoami
ubuntu
```
---
### Step 2: Inspect Kernel & Hardware Architecture
Retrieve core system details, kernel builds, and hardware architecture type using uname -a:
```
ubuntu@soc-workstation:~$ uname -a
Linux soc-workstation 6.8.0-31-generic #31-Ubuntu SMP Mon May 13 15:58:18 UTC 2024 x86_64 GNU/Linux
```
Linux: Operating system kernel family.

soc-workstation: Local host network name.

6.8.0-31-generic: Specific active kernel release.

x86_64: 64-bit hardware architecture platform.
---
### Step 3: Analyze Storage Utilization
Review mounted partitions, total capacity, and available storage using df -h (the -h flag formats values into human-readable MB/GB units):
```
ubuntu@soc-workstation:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/root        20G   12G  8.0G  60% /
tmpfs           1.9G     0  1.9G   0% /dev/shm
/dev/sda1       511M  6.0M  505M   2% /boot/efi
```
### Step 4: Extract OS Distribution Metadata
Inspect core system release configurations stored inside the /etc/os-release system file:
```
ubuntu@soc-workstation:~$ cat /etc/os-release
NAME="Ubuntu"
VERSION="24.04 LTS (Noble Numbat)"
ID=ubuntu
ID_LIKE=debian
PRETTY_NAME="Ubuntu 24.04 LTS"
```
# 📑 Technical Command Reference Summary

| Assessment Target | Command | Functional Purpose |
| :--- | :--- | :--- |
| **Current Path** | `pwd` | Outputs current absolute directory path. |
| **List Directory** | `ls -la` | Displays all files (including hidden `.file` items) with permissions and sizes. |
| **Directory Shift** | `cd <path>` | Changes active workspace directory (`..` moves up one level). |
| **Artifact Search** | `find ~ -name <file>` | Scans directory tree for matching filename patterns. |
| **Display File** | `cat <file>` | Prints plain text file contents to terminal stdout. |
| **User Context** | `whoami` | Identifies active execution user context. |
| **System Info** | `uname -a` | Displays kernel version, hostname, and CPU architecture. |
| **Storage Audit** | `df -h` | Summarizes mounted disk usage in human-readable notation (GB/MB). |
| **Distribution Info** | `cat /etc/os-release` | Reads system build specifications and OS distribution name. |

