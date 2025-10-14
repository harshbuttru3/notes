**`nslookup`** (short for "name server lookup") is a command-line tool for querying the Domain Name System (DNS) to get information about a domain name, including its IP address. It's a fundamental utility for network administrators and developers, and is included with all major operating systems, including Windows, macOS, and Linux. 

Think of DNS as the internet's phonebook, translating easy-to-remember domain names (like `google.com`) into numerical IP addresses (like `142.250.190.142`) that computers use to communicate. The `nslookup` command is your tool for looking up those translations. 

### When to use `nslookup`

- **Troubleshooting:** If a website is down, `nslookup` can confirm if the domain name is resolving to the correct IP address or if there's a DNS-related problem.
- **Verification:** You can check that a domain's DNS records, such as for email servers, are correctly configured.
- **Security:** Performing a reverse lookup (finding a domain from an IP address) can help investigate suspicious network activity.
- **Testing:** Querying a specific DNS server can help diagnose issues with your local DNS resolver. 

### Basic usage

`nslookup` can be used in two modes: 

#### 1. Non-interactive mode (for single queries)

You type the command and the query all on one line.

- **Look up a domain's IP address (A record):**
```sh
    nslookup example.com
    ```

This shows the default DNS server being used and the IPv4 (A) and IPv6 (AAAA) addresses for the domain.


- **Perform a reverse lookup:**
- ```sh
    nslookup 142.250.190.142
    ```
This command returns the domain name associated with that specific ip address.

- **Query a specific DNS server:**
```sh
    nslookup example.com 8.8.8.8
    ```

This sends the query for `example.com` to Google's public DNS server (`8.8.8.8`) instead of your system's default. 

#### 2. Interactive mode (for multiple queries)

You enter a session and can perform multiple queries and change settings. 

To start, just type `nslookup` and press **Enter**. Your command prompt will change to `>`. 

```sh
nslookup
>
```
To exit the interactive session, type **`exit`** and press **Enter**. 

**Finding specific DNS record types**

One of the most powerful features of `nslookup` is searching for specific DNS record types.

- **To set the record type** in interactive mode, use `set type=<record_type>`.
- **For a single query** in non-interactive mode, you can often use `nslookup -type=<record_type> <domain>`. 

Here are some of the most common record types:

- **A**: An IPv4 address record.
- **AAAA**: An IPv6 address record.
- **MX**: The Mail Exchange record for email servers.
- **NS**: The Name Server records, which list authoritative DNS servers.
- **CNAME**: A Canonical Name or alias record.
- **TXT**: A Text record used for verification services (like SPF or DKIM).
- **ANY**: Returns all available records for the domain. 

**Example:** Find the mail servers for `example.com`.

sh

```
nslookup
> set type=mx
> example.com
> exit
```
**Interpreting the output**

When you run an `nslookup` command, you will see two main sections in the output:

- **Server:** This shows the DNS server that handled your request. By default, this is your computer's configured DNS server.
- **Answer:** This contains the result of your query. 

You may sometimes see the message "**Non-authoritative answer**" in the output. This means the information was returned from a local cache rather than the domain's authoritative name server, but this is normal and not an error.