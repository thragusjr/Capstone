---
title: '2. Second Video: Passive Scanning & Information Gathering'
updated: 2023-04-23 00:02:25Z
created: 2023-04-22 22:43:05Z
---

# **Initial Reconnaissance**
- ### **Useful Commands**
	- host *URL*
	- nslookup *URL*
	- traceroute *URL*
		- **-p** _port_
	- dig -t ns twitter.com

- ### **Online Resources**
	- [Internet Archive: Wayback Machine](https://archive.org/web/)
	- [Shodan Search Engine](https://www.shodan.io/)
	- [OSINT Framework](https://osintframework.com/)


# **Scanning and Enumeration**
## **Nmap:**
- nmap -sn 10.21.10.0/24

## **NetDiscover (ARP Scanning):**
- netdiscover -i eth0
- netdiscover -r 10.21.10.0/24

## **Nmap**
- **Important flags**
	- sS - SYN scan
	- sC - default script
	- sV - version information
	- A - All/aggressive
	- O - operating system information
- **Scan**
	- **Standard Scan example**
		- nmap -sn 10.21.10.0/24
	- **Scan for Nmap --tailored script --interrogate for service version info --interrogate for OS info --output to XML**
		- nmap -sC -sV -O -oX
	- **Nmap port 80 - IP - Pipe to Nikto for scan** 
		- nmap -p80 10.0.1.0/24 -oG - | nikto.pl -h -

## **DnsRecon**
- **Help**
	- dnsrecon -h
- **Scan Domain**
	- dnsrecon - d * domain *

## **theHarvester**
- theHarvester --help
- **Scan** on Microsoft, limit 200 results, source:duckduckgo
	- theHarvester -d microsoft.com -l 200 -b duckduckgo

## **Owasp AMASS**
- Enumeration: Passive
	- amass enum -passive -d <URL> -src
	- Indentify domains by using -whois option (Passive)
		- amass intel -d <url> -whois
