# Reconnaissance

## Port Scaning with Nmap
```
$ nmap -A -F -T1 <ip_addr> -v
```
scanning the target with lower Timing Template value and fewer number of ports.

## Directory Fuzzing with Ffuf
```
$ ffuf -w /usr/share/wordlists/dirb/common.txt -u http://somewebsite.com/FUZZ -fc 403 -p 2
```
Fuzzing directory using Ffuf by filtering out specified HTTP status code from response with 2 seconds delay.
