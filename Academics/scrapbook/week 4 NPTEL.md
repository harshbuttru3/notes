## Host 
host <domain_url> will show ip address and  mailservers
host -t ns <domain_url> will show name servers of that domains
host -l <domain_url> <name_server> will show is it zone transferable or not and show 

## DIG
dig <domain_url>  will show ip addresses,etc
dig <domain_url> +short
dig <domain_url> -t ns will show name server.
dig <domani_url> -t mx will show mail server.
dig axfr <domain_url> @<name_server> will show zone transfer data.

## dnsenum 
dnsenum <doman_url> will enumerate automatically all the possible data and bruteforce 

## dnsrecon 
nhi padhaya to sayd nhi puchhega
