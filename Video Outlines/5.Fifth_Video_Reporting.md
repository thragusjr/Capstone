---
title: '5. Fifth Video: Reporting'
updated: 2023-04-23 04:13:33Z
created: 2023-04-22 20:57:21Z
---

## **Considerations When Writing a Report**
- **Technical Writing**
	- Write in 3rd Person
- **Explain on a Level a Client Can Understand**
	- The individuals reviewing this document may not have extensive cybersecurity expertise. This is not an ELI5, but its should not be overly complex either.

## **Points to Cover in a Report:**
- **CVE: Vulnerability Name & Categorization**
	- [Exploit-DB / Exploits + Shellcode + GHDB · GitLab](https://gitlab.com/exploit-database/exploitdb)
	- [Overview | CVE](https://www.cve.org/About/Overview)
	- [Exploit Database Search](https://www.exploit-db.com/search)
	- [CVE Security Vulnerability Database](https://www.cvedetails.com/)
	- Date, Version(s) of Associated Services
- **CVSS Score: Severity**
	- [CVSS v3.1 User Guide](https://www.first.org/cvss/v3.1/user-guide)
	- [CVSS v3.1 Examples](https://www.first.org/cvss/v3.1/examples)
	- [National Vulnerability Database - Home](https://nvd.nist.gov/)
- **Impact to the business if not remediated.**
	- What could happen to the business if this vulnerability is left unfixed?
- **Remediation Guidance**
	- How do you recommend patching, blacking or otherwise fixing this vulnerability
- **Vulnerability/Finding Details** 
	- This section is for documenting how the vulnerability was found/exploited.
- **Look at Publicly Available Pentest Reports For Reference**
	- [A list of public penetration test reports published by several consulting firms and academic security groups.](https://github.com/juliocesarfort/public-pentesting-reports)

## **Faraday**
- **Start Faraday in CLI**
	- faraday-cli
- **Authentication Info**
	- faraday-cli auth
- **Other Useful Faraday Commands**
	- -f/--faraday-url FARADAY_URL	url of your faraday server
	- -i/--ignore-ssl	Ignore SSL certificate validation
	- -i/--ignore-ssl	Ignore SSL certificate validation
	- -u/--user USER	Faraday user
	- -p/--password PASSWORD	Faraday password
- **List Current Workplace(s)**
	- faraday-cli workspace list -p
- **Delete a workspace**
	- faraday-cli workspace delete test
- **Import Report From Tool**
	- faraday-cli tool report $HOME/Downloads/openvas-report.xml

## **Resources:**
https://docs.faraday-cli.faradaysec.com/
https://github.com/infobyte/faraday_plugins
