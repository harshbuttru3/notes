Date: 2025-07-26
Tags: [[OSINT]]  [[1. Performing Passive Reconnaissance]] [[Reconnaissance]] 
#recon #passive_recon #tools #footprinting

---
## Spiderfoot - OSINT Automation Tool
SpiderFoot is an open-source OSINT tool used for automated reconnaissance. It collects intelligence on IP addresses, domain names, emails, usernames, DNS records, etc., from over 200+ public data sources, 
Useful for:
- Ethical hacking & penetration testing
- Footprinting & reconnaissance phase
- Threat intelligence gathering
### Features : 
- GUI (web based ) and CLI mode
- over 200 OSINT modules (shodan, haveibeenpwned, virus total, etc)
- Detects:  
	- Vulnerabilities
	- passive DNS data
	- Leaked credentials
	- WHOIS, ASN, SSL certs, etc.
 - Supports Tor and proxy routing 
 - exportable reports (HTML, CSV, JSON, etc)
### Starting SpiderFoot : 
we can start spiderfoot with the command : 
> spiderfoot -l 127.0.0.1:5001

and then in gui mode, we can create new scans and view reports of it.

some of the modules in spiderfoot requires api key, for that we have to make account on that service website and get the api key and insert it in that module's setting. 
