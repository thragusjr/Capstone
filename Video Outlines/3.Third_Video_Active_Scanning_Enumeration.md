---
Title: '3. Third Video: Active Scanning & Enumeration'
updated: 2023-04-23 00:15:16Z
created: 2023-04-22 20:54:50Z
---

- Enumeration is when dig into the items we found in information gathering to see if we can find anything of value.
	- We research on potential weak points. 
- For example, if we find a workstation that is running on Windows 7, we're going to go out and research vulnerabilties on Win7

# **Active Scanning & Enumeration**

## **Nikto**
- **Default scan**
			- nikto -h "IP address", nikto --url "domain"
		- **Scan a host-specify ports**
			- nikto -host [host IP/name] -port [port number 1], [port number 2], [port number 3]
		- **Scan and output infor**
			- nikto -host [host IP/name] -output [output_file]

## **dnsrecon**
- dnsrecon - d
- dnsrecon -d DOMAIN -D /usr/share/wordlists/dnsmap.txt -t std --xml dnsrecon.xml
- Lookup domain using a wordlist using standard type of enumeration (-t std), output to xml called dnsrecon.xml (--xml or -x) with 
	- dnsrecon -d DOMAIN.com -D /usr/share/wordlists/dnsmap.txt -t std --xml dnsrecon.xml --name_server 8.8.8.8
- Brute Force discovery of domains and hosts using wordlist
	- - dnsrecon -d www.acme.com -D /path/to/dict.txt -t brt
- Reverse Lookup
	- dnsrecon -r 208.67.222.200-208.67.222.255 -d microsoft.com

## **Dirb:** 
- dirb "domain"
- dirb "URL" usr/share/dirb/wordlist -o dirbOutput.txt

## **wFuzz**
- Look at payloads
	- wfuzz -e payloads
- Subdomain Fuzzing With Wordlist
	- wfuzz -c -Z -w subdomains.txt http://FUZZ.vulnweb.com
- Directory Fuzzing With Wordlist:
	- wfuzz -w wordlist/general/common.txt http://testphp.vulnweb.com/FUZZ

## **Wpscan**:
**Basic Use**
- wpscan --url %3Cdomain%3E
- wpscan --url <domain> --enumerate ap at (All Plugins, All Themes)
- wpscan --url <domain> --enumerate u (Usernames)
- wpscan --url <domain> --enumerate v
- wpscan --url "target" --enumerate vp,u,vt,tt --follow-redirection --verbose --log target.log

**Enumerate vulnerable plugins, users, vulnerable themes, timthumbs**
wpscan --url "target" --enumerate vp,u,vt,tt --follow-redirection --verbose --log target.log>)
