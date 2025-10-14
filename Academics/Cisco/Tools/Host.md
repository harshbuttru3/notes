The **host** command is a simple DNS lookup utility used to **map domain names to IP addresses (and vice versa)**. 
It's commonly used in the **reconnaissance phase** of ethical hacking to gather information about : 
- IP addresses
- DNS records 
- Mail servers (MX)
- Name server (NS) 
- and more...

#### 1. Find IP address of a Domain : 
```sh
host example.com
```
The above command will show the IPv4 address associated with the domain. 

#### 2. Find IPv6 address (AAAA record) : 
```sh
host -t AAAA example.com
```
#### 3. Find Mail servers (MX records) : 
Helps identify mail server infrastructure - useful for phishing simulation or social engineering.  
```sh
host -t MX example.com
```
#### 4. Find Name Server (NS records) : 
useful to discover the authoritative name servers. 
```sh
host -t NS example.com
```
#### 5. Zone Transferable :
helps in finding whether the data are transferable (sync) 
```sh
host -l example.com <name_server> 
```
#### 6. Find All DNS records : 
This is similar to a DNS zone transfer, but only gives what the server allows publicly.
```sh
host -a example.com
```
#### 7. Reverse DNS lookup (Find Domain from IP) : 
Used to identify domains hosted on an IP address.
```sh
host 92.184.216.34
```
#### 8. Check TXT Records : 
Useful for discovering email security configurations. 
```sh
host -t TXT example.com
```
## ⚡ Useful Options

|Option|Description|
|---|---|
|`-t <type>`|Specify record type (A, MX, NS, TXT, AAAA, SOA, etc.)|
|`-a`|Query all available records|
|`-C`|Check zone transfer (AXFR)|
|`-l`|List all hosts in a domain (if allowed)|
|`-v`|Verbose mode|
|`-4` or `-6`|Force IPv4 or IPv6 lookup|