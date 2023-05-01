 ## **Tool overview:**
- **Options**:
  **-h, --help**         Show this help message and exit
  **-d DOMAIN, --domain DOMAIN**
                          Target domain.
  **-n NS_SERVER, --name_server NS_SERVER**
                          Domain server to use. If none is given, the SOA of the target will be used. Multiple servers can be specified using a comma    separated list.
  **-r RANGE, --range RANGE**
                          IP range for reverse lookup brute force in formats   (first-last) or in (range/bitmask).
  **-D DICTIONARY, --dictionary DICTIONARY**
                         Dictionary file of subdomain and hostnames to use for brute force.
  **-f**                     Filter out of brute force domain lookup, records that resolve to the wildcard defined IP address when saving records.
  **-a**                    Perform AXFR with standard enumeration.
  **-s**                    Perform a reverse lookup of IPv4 ranges in the SPF record with standard enumeration.
  **-b**                    Perform Bing enumeration with standard enumeration.
  **-y**                    Perform Yandex enumeration with standard enumeration.
  **-k**                    Perform crt.sh enumeration with standard enumeration.
  **-w**                   Perform deep whois record analysis and reverse lookup of IP ranges found through Whois when doing a standard enumeration.
  **-z**                    Performs a DNSSEC zone walk with standard enumeration.
  **--threads THREADS**  Number of threads to use in reverse lookups, forward lookups, brute force and SRV record enumeration.
  **--lifetime LIFETIME**   Time to wait for a server to respond to a query. default is 3.0
  **--tcp**                 Use TCP protocol to make queries.
  **--db DB**            SQLite 3 file to save found records.
  **-x XML, --xml XML**   XML file to save found records.
  **-c CSV, --csv CSV**     Save output to a comma separated value file.
  **-j JSON, --json JSON**  Save output to a JSON file.
  **--iw**                   Continue brute forcing a domain even if a wildcard record is discovered.
  **--disable_check_recursion**
                           Disables check for recursion on name servers
  **--disable_check_bindversion**
                           Disables check for BIND version on name servers
  **-V, --version**     Show DNSrecon version
  **-v, --verbose**    Enable verbose
  **-t TYPE, --type TYPE**  Type of enumeration to perform.
-   ## **Usage**
    -   Brute-force: `dnsrecon -d target.com -D wordlist.txt -t brt`
    -   DNS cache snooping: `dnsrecon -t snoop -D wordlist.txt -n 2.2.2.2` where 2.2.2.2 is the IP of the target’s NS server
    -   Options
        -   `--threads 8`: Number of threads
        -   `-n nsserver.com`: Use a custom name server
        -   Output options
            -   `--db`: SQLite 3 file
            -   `--xml`: XML file
            -   `--json`: JSON file
            -   `--csv`: CSV file

### Dirb Cheat Sheet

Dirb is a web application scanner that can be used to discover hidden directories and files on a web server. Here's a cheat sheet with some commonly used Dirb commands:

| Command | Description |
|---------|-------------|
| `dirb URL` | Start scanning the specified URL for directories and files. |
| `dirb URL wordlist.txt` | Use the specified wordlist file for the directory and file scanning. |
| `dirb URL -o output.txt` | Save the output of the scan to the specified output file. |
| `dirb URL -r` | Recursive mode - follow links within found directories. |
| `dirb URL -e extension1,extension2,...` | Limit scanning to the specified file extensions. |
| `dirb URL -x exclusion1,exclusion2,...` | Exclude the specified directories or files from the scan. |
| `dirb URL -S` | Use SSL for the scan. |
| `dirb URL -t N` | Use N threads for the scan. |
| `dirb URL -a user:password` | Use HTTP Basic Authentication with the specified credentials. |

- ### **Enumerate Directory with Specific Ext**
	- dirb http://192.168.1.106/dvwa/ -X .php
- ### **Save Output to disk: **
	- dirb http://192.168.1.106/dvwa/ -o output.txt
- ### **Ignore Specific Status Code**
	- dirb http://192.168.1.106/dvwa/ -N 302
- ### **Prevent Stop on Warning Message:**
	- dirb http://192.168.1.106/ -w
- ### **Use Authorization**
	- dirb http://testphp.vulnweb.com/login.php -u  test:test
- ### **Run Through Proxy Using -p Parameter**
	- dirb http://192.168.1.108 –p 192.168.1.108:3129
