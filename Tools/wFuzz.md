[A Detailed Guide on Wfuzz - Hacking Articles](https://www.hackingarticles.in/a-detailed-guide-on-wfuzz/)

# wFuzz Guide

| Flag | Description |
|------|-------------|
| -c \<cookie string> | Use the specified cookie string for the request |
| -d \<data> | Use the specified data for the request. Data should be in "name1=value1&name2=value2" format |
| -f \<file> | Read payloads from the specified file |
| -H \<header> | Use the specified header for the request. Header should be in "Header: Value" format |
| -hh | Print all response headers |
| -help | Display the help menu |
| -hl | Print only response headers and length |
| -hw \<wordlist> | Use the specified wordlist for bruteforcing headers |
| -ic | Ignore certificate errors |
| -j | Output in JSON format |
| -l | Follow redirects |
| -m \<method> | Use the specified HTTP method for the request. Defaults to GET |
| -o \<file> | Write output to the specified file |
| -p \<proxy> | Use the specified proxy for requests |
| -s \<code> | Show only responses with the specified HTTP status code |
| -t \<num> | Set the number of threads to use. Defaults to 20 |
| -u \<url> | Set the target URL |
| -v | Verbose output |

And here are some examples:

### Basic usage
```
wfuzz -u https://example.com/FUZZ -w /path/to/wordlist.txt
```
This command will send requests to `https://example.com/` with the payloads from `/path/to/wordlist.txt` replacing the `FUZZ` keyword in the URL.

### Using a custom header
```
wfuzz -u https://example.com -H "Authorization: Bearer TOKEN"
```
This command will send a request to `https://example.com` with the `Authorization: Bearer TOKEN` header.

### Using POST data
```
wfuzz -u https://example.com/login.php -d "username=admin&password=FUZZ"
```
This command will send POST requests to `https://example.com/login.php` with the `username` field set to `admin` and the `password` field set to the payloads from the wordlist file replacing the `FUZZ` keyword.

### Using a cookie
```
wfuzz -u https://example.com -c "session=1234567890abcdef"
```
This command will send requests to `https://example.com` with the `session` cookie set to `1234567890abcdef`. 

### Using a custom HTTP method
```
wfuzz -u https://example.com/api -m PUT
```
This command will send a PUT request to `https://example.com/api`.

### Limiting output to a specific status code
```
wfuzz -u https://example.com -s 200
```
This command will only display responses with a status code of `200`.
