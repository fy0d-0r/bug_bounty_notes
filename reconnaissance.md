# Reconnaissance

## Nmap
```
$ nmap -A -F -T1 <ip_addr> -v
```
scanning the target with lower Timing Template value and fewer number of ports.

## Ffuf 
```
$ ffuf -w /usr/share/wordlists/dirb/common.txt -u http://somewebsite.com/FUZZ -fc 403 -p 2
```
