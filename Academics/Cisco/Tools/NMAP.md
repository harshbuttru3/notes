### 📌 What is Nmap?

**Nmap** (Network Mapper) is a **free and open-source tool** for:

- Network discovery
    
- Security auditing
    
- Port scanning
    
- OS detection
    
- Vulnerability scanning
    

---

### 🎯 Use Cases

|Use Case|Description|
|---|---|
|Host Discovery|Find live systems in a network|
|Port Scanning|Discover open/closed/filtered ports|
|Service Version Detection|Identify software and version on ports|
|OS Fingerprinting|Guess the OS and device type|
|Vulnerability Detection|With `nmap` scripts (NSE)|

---

### ⚙️ Basic Syntax

bash

CopyEdit

`nmap [options] [target]`

Example:

bash

CopyEdit

`nmap 192.168.1.1`

---

## 🧪 Common Nmap Commands

### 🟢 1. Ping Scan (Find live hosts)

bash

CopyEdit

`nmap -sn 192.168.1.0/24`

- `-sn`: No port scan, just ping
    
- Useful for discovering live hosts
    

---

### 🟡 2. Port Scan (Default 1000 ports)

bash

CopyEdit

`nmap 192.168.1.1`

---

### 🔵 3. Service Version Detection

bash

CopyEdit

`nmap -sV 192.168.1.1`

- `-sV`: Detect services and versions
    

---

### 🟣 4. OS Detection

bash

CopyEdit

`nmap -O 192.168.1.1`

- `-O`: Try to guess the OS (root required)
    

---

### 🔴 5. Full Scan (Intense)

bash

CopyEdit

`nmap -A 192.168.1.1`

- Enables:
    
    - OS detection
        
    - Version detection
        
    - Script scanning
        
    - Traceroute
        

---

### 🔍 6. Specific Port Scan

bash

CopyEdit

`nmap -p 21,22,80,443 192.168.1.1`

- `-p`: Specify ports to scan
    

---

### ⚡ 7. Fast Scan (100 ports only)

bash

CopyEdit

`nmap -F 192.168.1.1`

---

### 🌐 8. Scan a Website

bash

CopyEdit

`nmap example.com`

---

## 📜 Nmap Scan Types

|Option|Description|
|---|---|
|`-sS`|SYN scan (Stealth scan)|
|`-sT`|TCP Connect scan (no root needed)|
|`-sU`|UDP scan|
|`-sA`|ACK scan|
|`-sN`|Null scan (no flags)|

---

## 🧠 Nmap Cheat Sheet (Quick Table)

|Task|Command|
|---|---|
|Ping sweep|`nmap -sn 10.0.0.0/24`|
|Fast scan|`nmap -F target`|
|All ports|`nmap -p- target`|
|Scan with OS + version|`nmap -A target`|
|TCP connect scan|`nmap -sT target`|
|Stealth scan|`nmap -sS target`|
|UDP scan|`nmap -sU target`|
|Scan multiple targets|`nmap target1 target2` or `-iL list.txt`|
|Save output|`-oN`, `-oX`, `-oG`|
## 🛡️ NSE (Nmap Scripting Engine)

Nmap has powerful built-in scripts for:

- Vulnerability scanning
    
- Malware detection
    
- Brute-forcing
    
- Enumeration
    

### 🔧 Use NSE Scripts

bash

CopyEdit

`nmap --script=vuln 192.168.1.1`

### 🧠 Useful NSE Script Categories:

| Category    | Examples                     |
| ----------- | ---------------------------- |
| `auth`      | Login bypass, brute-force    |
| `vuln`      | Check for CVEs               |
| `discovery` | List shares, services, users |
| `malware`   | Detect infected hosts        |