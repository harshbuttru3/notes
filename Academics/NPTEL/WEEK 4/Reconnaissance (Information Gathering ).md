- It is the process of collecting as much information as possible about a target network. 
### Objectives of Reconnaissance : 
- Collect network information : 
	- Domain name, IP addresses, internal domain name, services running (TCP, UDP)
- Collect system information : 
	- User names, routing tables, system names, system architecture, password, etc. 
- Collect organisation information : 
	- Employee details, organisation names, location, contact information, security policies, etc. 
- Two types of reconnaissance : 
		1. Passive reconnaissance. 
		2. Active reconnaissance. 

## Passive Reconnaissance : 
- In this type of information gathering we collect information about the target indirectly. 
	- Without direct communication with the target system. 
	- Collection of the data that are publically available for webpage/application.
	- We can collect information using [archive.org](https://archive.org), [WHOis](https://whois.com), [Netcraft](https://netcraft.com), [Harvester](https://www.kali.org/tools/theharvester/) tools.
	-  We can also use search engine and search operator available with search engine. 
### 1. Archive.org : 
- In archive.org website, we can get complete history of any website like when it was last updated. 
- We can go back to the particular date and observe the webpage. 
- We can mirror the website which will load all the files locally, such as HTML codes, Images, etc. That can be used to observe the directories used. 
### 2. Whois : 
- Whois database lookup allows us to access many useful information about target such as : 
	- Registration details
	- IP address
	- contact number and Email ID
	- Domain owner
	- Name server 
	- Regional internet Registries. 
### 3. Netcraft : 
- Netcraft is an internet service company.
- Through Netcraft we can find the list of subdomains and operating system of corresponding server. 
- This can be useful while exploiting the system. 
### 4. Search Engine and Search Operator (Google Dorking ) : 
- Using search engine we can extract information such as platform used by organisation, employee details, login pages. 
	- Use various filters to restrict the search. 
- We can also extract some information from search engine cache and internet archives. 

### Useful Search Operators. 
- Site: finds results on a specific website or domain.
- Inurl: searches for a keyword within a URL. 
- Intitle: Finds a keyword within a webpage's title. 
- Filetype: Locates specific file types like PDF or XLS. 
- Link: Finds web pages linking to a specific URL. 
- Intext: Searches for keywords within the body text of a webpage. 
- Allintitle: Finds pages with multiple keywords in the title. 
- Cache: Shows the cached version of a webpage. 
- Related: Displays pages related to a specific URL. 
- Info: provides details about a website, including cache and similar pages.
- Ext: Finds a specific file extension.
- Define: Displays the definition of a word or phrase.
- Phonebook: search for phone numbers and contact information for a person or business. 
- Map: Shows a map of a location or address.
- Allinurl: Finds pages with multiple keywords in the URL. 
- Before: Finds content indexed before a specific date. 
- After: Finds content indexed after a specific date. 
- Numrange: Searches for nmbers within a specified range.
- AROUND(X): Finds pages where two terms are within a specified nmber of words from each other. 
- Inanchor: Searches for keywords within the anchor text of links on a webpage. 

- @: if we want the search to be restricted to only social media, then we use @ before the search key. 
- Quotes (""): Will help to get exact match result. 
- Many more search operators are available. 
	- We can also combine search operators to get more specific information. 
	- Can be helpful for, targeted search, exclude/include specific terms/sites, site index information, etc. 
### Other ways of Reconnaissance : 
- We can register and opt for alerts to know all updates about a company/organisation. 
- If we are analysing social media accounts then we can follow the targeted person/organisation to get all new updates. 
- We can even look into groups, forums, and blogs. 
- Simple browsing of the website can identify the software, database used, etc. 
- 