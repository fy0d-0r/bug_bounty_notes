# Server-side Request Forgery (SSRF)

In a typical SSRF attack, the attacker might cause the server to make a connection to internal-only services within the organization's infrastructure. In other cases, they may be able to force the server to connect to arbitrary external systems. This could leak sensitive data, such as authorization credentials. 

Server-Side Request Forgery (SSRF) is a type of web application vulnerability that allows an attacker to make unauthorized requests from a vulnerable server to other web applications or internal systems that are not intended to be accessible from the internet.


![SSRF](https://github.com/fy0d-0r/bug_bounty_notes/blob/main/images/How-Server-SSRF-works.png)

Original Request
```
POST /booking

availabilityApi=http://api.booking-example.com/booking?start=0122023&end=20122023
```

Malicious Request
```
POST /booking

availabilityApi=http://127.0.0.1/admin
```
Here, instead of making a request with legitimate url, the attacker calls the admin page on the loopback address.Because the request is coming from the server itself which is trusted, the page is served without complaint.

SSRF Port Scanning Bash Script (GET)
```
#!/bin/bash
for x in {1..65535};
	do cmd=$(curl -so /dev/null http://10.10.93.91:8000/attack?url=http://2130706433:${x} -w '%{size_download}');
	if [ $cmd != 1045 ]; then
		echo "Open port: $x"
	fi
	
done
```

Using &x to cancell out the what is appended

![url](https://github.com/fy0d-0r/bug_bounty_notes/blob/main/images/Screenshot_2024-01-09_07-40-03.png)

## DNS Rebinding
Allowing arbitrary cross-origin requests is known to be extremely dangerous. Therefore most modern browsers block these requests(by SOP). However, DNS rebinding provides a way to bypass this restriction.

DNS rebinding is a method of manipulating resolution of domain names that is commonly used as a form of computer attack. In this attack, a malicious web page causes visitors to run a client-side script that attacks machines elsewhere on the network. In theory, the same-origin policy prevents this from happening: client-side scripts are only allowed to access content on the same host that served the script. Comparing domain names is an essential part of enforcing this policy, so DNS rebinding circumvents this protection by abusing the Domain Name System (DNS).

### Implementation of DNS Rebinding


### References
```
https://medium.com/@adithyakrishnav001/server-side-request-forgery-ssrf-bf23802cfb12
```
```
https://www.imperva.com/learn/application-security/server-side-request-forgery-ssrf/
```
```
https://en.wikipedia.org/wiki/DNS_rebinding
```



