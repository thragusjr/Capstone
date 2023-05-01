---
title: hydra**
updated: 2023-04-23 00:10:10Z
created: 2023-04-23 00:08:27Z
latitude: 45.52306220
longitude: -122.67648160
altitude: 0.0000
---

# Hydra

Hydra is a powerful network login cracker that supports many different services and protocols. It can perform brute-force attacks to crack passwords and find login credentials.


This tool does not have a native default wordlist, using the Rockyou/seclists/wordlists is suggested**

## Basic Usage

The basic syntax for using Hydra is:

```
hydra -L <username_list> -P <password_list> <target> <protocol>
```

Here, `<username_list>` and `<password_list>` are the paths to the files containing the lists of usernames and passwords, `<target>` is the IP address or hostname of the target system, and `<protocol>` is the protocol to be used (e.g. ssh, ftp, telnet).

## Flags and Options

Hydra has several flags and options that can be used to customize the attack. Here is a list of some of the most common ones:

| Flag | Description | Example |
| --- | --- | --- |
| `-L` | Path to a file containing a list of usernames | `hydra -L usernames.txt` |
| `-P` | Path to a file containing a list of passwords | `hydra -P passwords.txt` |
| `-l` | Single username to use for the attack | `hydra -l admin` |
| `-p` | Single password to use for the attack | `hydra -p password123` |
| `-t` | Number of threads to use for the attack | `hydra -t 16` |
| `-w` | Time to wait between login attempts (in seconds) | `hydra -w 5` |
| `-f` | Stop on first valid login found | `hydra -f` |
| `-v` | Verbose output (shows all login attempts) | `hydra -v` |
| `-V` | Show version information | `hydra -V` |
| `-s` | Port to use for the attack (default is protocol-specific) | `hydra -s 8080` |
| `-o` | Write output to a file instead of the console | `hydra -o results.txt` |
| `-M` | Use a list of targets instead of a single target | `hydra -M targets.txt` |
| `-S` | Use SSL/TLS for the attack | `hydra -S` |
| `-U` | Attempt null (empty) password logins | `hydra -U` |
| `-e` | Use a specific character set for the password brute-force attack | `hydra -e nsr` |
| `-x` | Use a specific range of characters for the password brute-force attack | `hydra -x 1-10` |

## Examples

Here are some examples of how to use Hydra with different protocols:

### SSH

```
hydra -L users.txt -P passwords.txt ssh://192.168.1.100
```

This command will attempt to brute-force the SSH login on the IP address `192.168.1.100` using the usernames and passwords in the files `users.txt` and `passwords.txt`.

### FTP

```
hydra -l admin -P passwords.txt ftp://192.168.1.100
```

This command will attempt to brute-force the FTP login on the IP address `192.168.1.100` using the username `admin` and the passwords in the file `passwords.txt`.

### Telnet

```
hydra -L users.txt -p password1 telnet://192.168.1.100:23
```

This command will attempt to brute-force the Telnet login on the IP address `192.168.1.100` on port 23

**Detailed example of brute force crack on ftp server**
hydra -t 1 -l admin -P [path to password.lst] -vV [IPaddress] ftp
--> -t # = preform # tasks
--> -l NAME = try to log in with NAME
--> -P [filepath] = Try password
--> -vV = verbose mode, showing the login+pass for each attempt

check for joe accounts by adding modifier -e s

**to write found login+pass combinations to file, add modifier -0 [fileanme]**
