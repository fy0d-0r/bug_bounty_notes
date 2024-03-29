# Reconnaissance

## Port Scaning with Nmap
```
$ nmap -A -F -T1 <ip_addr> -v
```
scanning the target with lower Timing Template value and fewer number of ports.

## Directory Fuzzing
### Ffuf
```
$ ffuf -w /usr/share/wordlists/dirb/common.txt -u http://somewebsite.com/FUZZ -fc 403 -p 2
```
Fuzzing directory using Ffuf by filtering out specified HTTP status code from response with 2 seconds delay.

### Dirb

## Shodan

```
$ shodan init <API key>
$ shodan info
$ shodan search "wordpress 1.4.7"
$ shodan count wordpress
$ shodan download wordpressfile "wordpress 1.4.7"
$ shodan scan submit 12.34.56.78
```



## DNS Enumeration
### host
### dig and zone transfer
Zone transfer is the process of replicating
DNS Database (zone file) betweeen DNS (Name) Servers.
When the name server is vulnerable in Zone Transfer,
we can enumerate sub domains easily.
#### Testing Zone Transfer
$ dig axfr @<recursive_ip> <target-domain>
```
$ dig axfr @10.10.23.22 targetdomain.org
```

### Whois
```
$ whois google.com
```

### nslookup
```
$ nslookup www.targetdomain.org
```
### The Harvester

```
$ theHarvester -d targetdomain.org -b google 
```

### crt.sh
- used for sub domain enumeration
```
https://crt.sh
```
subdomains of interest
```
dev
api
admin
portal
```

## Directory fuzzing

### Sublist3r
```
$ sublist3r -d targetdomain.org 
```

### Owasp Amass
```
$ ./go/bin/amass enum -d targetdomain.org
$ ./go/bin/amass enum -passive -d targetdomain.org
```







