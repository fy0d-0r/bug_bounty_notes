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

### References
```
https://medium.com/@adithyakrishnav001/server-side-request-forgery-ssrf-bf23802cfb12
```
```
https://www.imperva.com/learn/application-security/server-side-request-forgery-ssrf/
```
