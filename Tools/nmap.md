---
title: Nmap
updated: 2023-04-23 02:48:41Z
created: 2023-04-15 02:34:34Z
---

# **Nmap**

| Command | Description |
| --- | --- |
| `nmap -sV -sC -oA nmap 0.0.0.0` | Output all formats |
| `nmap -v -sS -A -T4 target` | Nmap verbose scan, runs syn stealth, T4 timing (should be ok on LAN), OS and service version info, traceroute and scripts against services |
| `nmap -v -sS -p- -A -T4 target` | As above but scans all TCP ports (takes a lot longer) |
| `nmap -v -sU -sS -p- -A -T4 target` | As above but scans all TCP ports and UDP scan (takes even longer) |
| `ls /usr/share/nmap/scripts/* | grep ftp` | Search nmap scripts for keywords |
| `nmap -v -p 445 --script=smb-check-vulns --script-args=unsafe=1 target` | Nmap script to scan for vulnerable SMB servers - WARNING: unsafe=1 may cause knockover |
| `nmap --script ftp-anon,ftp-bounce,ftp-libopie,ftp-proftpd-backdoor,ftp-vsftpd-backdoor,ftp-vuln-cve2010-4221,tftp-enum -p 21 target` | Port 21 - FTP |
| `nmap --script=smtp-commands,smtp-enum-users,smtp-vuln-cve2010-4344,smtp-vuln-cve2011-1720,smtp-vuln-cve2011-1764 -p 25 target` | Port 25 - SMTP |
| `smtp-user-enum -M VRFY -U /root/sectools/SecLists/Usernames/Names/names.txt -t target` | SMTP user enumeration |
| `nmap -p69 --script=tftp-enum.nse 10.11.1.111` | Port 69 - UDP - TFTP |
| `nmap -p 88 --script=krb5-enum-users --script-args="krb5-enum-users.realm='DOMAIN.LOCAL'" Target` | Port 88 - Kerberos |
| `nmap target --script=msrpc-enum` | Port 135 - MSRPC |
| `nmap --script=smb-enum* --script-args=unsafe=1 -T5 target` | Port 139/445 - SMB |
| `nmap --script smb-enum-shares -p139,445 -T4 -Pn targer` | Port 139/445 - SMB |
| `nmap --script smb-vuln* -p139,445 -T4 -Pn target` | Port 139/445 - SMB |
| `nmap -p445 --script smb-brute --script-args userdb=userfilehere,passdb=/usr/share/seclists/Passwords/Common-Credentials/10-million-password-list-top-1000000.txt target -vvvv` | Port 139/445 - SMB |
| `nmap –script smb-brute target` | Port 139/445 - SMB |
| `nmap -vv -sV -sU -Pn -p 161,162 --script=snmp-netstat,snmp-processes target` | Port 161/162 UDP - SNMP |
| `nmap -sV --script=ssl-heartbleed target` | Port 443 - HTTPS |
| `nmap -sV --script=ssl-heartbleed target` | Port 443 - HTTPS |
| `nmap -p 1433 -sU --script=ms-sql-info.nse target` | Port 1433 - MSSQL |
| `nmap -p 1521 -A target` | Port 1521 - Oracle |
| `nmap -p 1521 --script=oracle-tns-version,oracle-sid-brute,oracle-brute target` | Port 1521 - Oracle |
| `nmap --script=mysql-databases.nse,mysql-empty-password.nse,mysql-enum.nse,mysql-info.nse,mysql-variables.nse,mysql-vuln-cve2012-2122.nse target -p 3306` | Port 3306 - MySQL |
| `nmap -p 3389 --script=rdp-vuln-ms12-020.nse target` | Port 3389 - RDP |
| `nmap --script=vnc-info,vnc-brute,vnc-title -p 5900 target` | Port 5900 - VNC |

# Additional Flags & Scan Types

| Flag | Description | Example |
|------|-------------|---------|
| `-sS` | SYN scan - This is the default scan technique used by Nmap. It sends a SYN packet to the target port and waits for a response. If the port is open, the target sends a SYN-ACK packet back, indicating that the port is open. | `nmap -sS 192.168.1.1` |
| `-sT` | TCP connect scan - This technique attempts to establish a full TCP connection with the target port. If the connection is successful, the port is considered open. | `nmap -sT 192.168.1.1` |
| `-sU` | UDP scan - This technique sends UDP packets to the target port and waits for a response. If the port is open, the target will send a response. | `nmap -sU 192.168.1.1` |
| `-sA` | ACK scan - This technique sends an ACK packet to the target port and waits for a response. If the port is closed, the target will send an RST packet back. If the port is filtered, no response will be received. | `nmap -sA 192.168.1.1` |
| `-sN` | NULL scan - This technique sends a NULL packet to the target port and waits for a response. If the port is closed, the target will send an RST packet back. If the port is open or filtered, no response will be received. | `nmap -sN 192.168.1.1` |
| `-sF` | FIN scan - This technique sends a FIN packet to the target port and waits for a response. If the port is closed, the target will send an RST packet back. If the port is open or filtered, no response will be received. | `nmap -sF 192.168.1.1` |
| `-sX` | XMAS scan - This technique sends a packet with the FIN, URG, and PUSH flags set to the target port and waits for a response. If the port is closed, the target will send an RST packet back. If the port is open or filtered, no response will be received. | `nmap -sX 192.168.1.1` |
| `-O` | Operating system detection - This flag enables Nmap to attempt to determine the operating system running on the target host. | `nmap -O 192.168.1.1` |
| `-sV` | Service and version detection - This flag enables Nmap to attempt to determine the service and version running on the target port. | `nmap -sV 192.168.1.1` |
| `-A` | Aggressive scanning - This flag enables several other flags such as OS detection, version detection, and traceroute. It is a comprehensive scan and may cause network disruption. | `nmap -A 192.168.1.1` |
| `-p` | Port specification - This flag specifies the port(s) to scan. Ports can be specified as a range or a comma-separated list. | `nmap -p 1-100 192.168.1.1` |
| `-T` | Timing template - This flag specifies the speed of the scan. There are six timing templates: paranoid, sneaky, polite, normal, aggressive, and insane. | `nmap -T4 192.168.1.1` |
| `-v` | Verbose output - This flag enables verbose output, providing more detailed information about the scan. | `nmap -v 192.168.1.1` |
| `-oN` | Output to a file in normal format - This flag outputs the results of the scan to a file in normal format. | `nmap -oN scan_results.txt 192.168.1.1` |
| `-oX` | Output to a file in XML format - This flag outputs the results of the scan to a file in XML format. | `nmap -oX scan_results.xml 192.168.1.1` |
| `-sP` | Ping scan - This flag sends an ICMP echo request to the target host to determine if it is online. | `nmap -sP 192.168.1.1` |
| `-Pn` | No ping - This flag disables ping discovery, assuming that the target is online. | `nmap -Pn 192.168.1.1` |
| `-F` | Fast scan - This flag enables a faster scan by scanning only the most commonly used ports. | `nmap -F 192.168.1.1` |
| `-sL` | List scan - This flag enables Nmap to simply list the targets it would have scanned without actually performing a scan. | `nmap -sL 192.168.1.0/24` |
| `-traceroute` | Traceroute - This flag enables Nmap to perform a traceroute to the target host. | `nmap --traceroute 192.168.1.1` |
| `--script` | Script scanning - This flag enables Nmap to execute specific scripts against the target host. | `nmap --script smb-os-discovery 192.168.1.1` |
| `--script-args` | Script arguments - This flag enables Nmap to pass arguments to the scripts being executed. | `nmap --script smb-os-discovery --script-args=unsafe=1 192.168.1.1` |

| Flag | Description |
|------|-------------|
| `-6` | Enable IPv6 scanning |
| `-A` | Enable OS and version detection, script scanning, and traceroute |
| `-C` | Use the default NSE script categories |
| `-D` | Spoof the source address to appear to come from a specified host |
| `-F` | Fast mode - Scan fewer ports than the default scan |
| `-G` | Send probes to network paths to discover firewalls and filters |
| `-O` | Enable OS detection |
| `-Pn` | Treat all hosts as online, skip host discovery |
| `-PR` | Ping scan - Check if hosts are online |
| `-PS` | TCP SYN Ping scan |
| `-PA` | TCP ACK Ping scan |
| `-PU` | UDP Ping scan |
| `-PY` | SCTP INIT Ping scan |
| `-PE` | ICMP Echo Ping scan |
| `-PP` | ICMP Timestamp Ping scan |
| `-PM` | ICMP Address Mask Ping scan |
| `-PO` | IP Protocol Ping scan |
| `-PS443` | Use a specified port number for Ping scans |
| `-R` | Enable reverse DNS resolution |
| `-S` | Specify a source IP address |
| `-sS` | TCP SYN Scan |
| `-sT` | TCP Connect Scan |
| `-sU` | UDP Scan |
| `-sN` | TCP Null Scan |
| `-sF` | TCP FIN Scan |
| `-sX` | TCP Xmas Scan |
| `-sA` | TCP ACK Scan |
| `-sW` | TCP Window Scan |
| `-sM` | TCP Maimon Scan |
| `-sL` | List Scan - Only list targets, do not scan |
| `-sn` | Ping Scan - Disable port scanning |
| `-SP` | Ping Scan - Send an ICMP echo request to determine if hosts are up |
| `-SS` | TCP SYN Scan |
| `-ST` | TCP Connect Scan |
| `-SU` | UDP Scan |
| `-SR` | TCP SYN-ACK Scan |
| `-sV` | Enable version detection |
| `-sW` | TCP Window Scan |
| `-sX` | Xmas Tree Scan |
| `-sY` | SCTP INIT Scan |
| `-sZ` | SCTP COOKIE-ECHO Scan |
| `-to` | Adjust the packet timeout |
| `-T` | Adjust the timing template |
| `-ttl` | Set the IP time-to-live (TTL) |
| `-v` | Increase verbosity |
| `-vv` | Increase verbosity level |
| `-vvv` | Increase verbosity level |
| `-w` | Set the output file name and path |
| `-y` | Use a fingerprint file to detect hosts and OS |
| `-z` | Send data to a port without establishing a full connection |
| `-A` | Enable OS and version detection, script scanning, and traceroute |
| `-b` | Use a SOCKS4 or SOCKS5 proxy |
| `-c` | Specify the number of packets to send |
| `-d` | Increase debugging level |
| `-e` | Use a specified network interface |
| `-f` | Fragment packets |
| `-g` | Source port number |
| `-h` | Show help and usage information |
| `-iL` | Specify targets from a list |
| `-k` | Send packets directly to the kernel |
| `-l` | Only show open ports |
| `-m` | Maximum number of parallel hosts |
| `-n` | Disable DNS resolution |


# Target Specification

Use file with lists of targets: -iL <filename>

# Target Ports
No port range specified scans 1,000 most popular ports

# Ports and Port Ranges
-F Scan 100 most popular ports
-p<port1>-<port2> Port range
-p<port1>,<port2>,... Port List
--top-ports <n> Scan n most popular ports

# Output Formats

-oN Standard Nmap output
-oX XML format

# Notes on Timing Options

-T0 Paranoid: Very slow, used for IDS evasion
-T1 Sneaky: Quite slow, used for IDS evasion
-T2 Polite: Slows down to consume less
 bandwidth, runs ~10 times slower than
 default
-T3 Normal: Default, a dynamic timing model
 based on target responsiveness
-T4 Aggressive: Assumes a fast and reliable
 network and may overwhelm targets
-T5 Insane: Very aggressive; will likely
 overwhelm targets or miss open ports


**Comprehensive Guide:**
https://highon.coffee/blog/nmap-cheat-sheet/
