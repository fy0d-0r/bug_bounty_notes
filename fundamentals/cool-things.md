## One Command Website

### Python
```
$ python3 -m http.server 8080
```

### PHP
```
$ php -S 127.0.0.1:8080
```

### NPM (Node Package Manager)
```
$ npx http-server -p 8080
```

## Apache Web Server
### Port Number Configuration
```
/etc/apache2/ports.conf

Listen 80 #CHANGE HERE

<IfModule ssl_module>
	Listen 443
</IfModule>

<IfModule mod_gnutls.c>
	Listen 443
</IfModule>
```
### Enable SSL Cert

## Curl

```
$ curl 127.0.0.1:8080 #Basic Request
$ curl http://127.0.0.1:8080 #Also Basic Request
$ curl -I 127.0.0.1:8080 #Headers
$ curl -o response.html 127.0.0.1:8080 #save to output file
$ curl ipinfo.io/<IPADDRESS> #IP Information
$ curl -v 127.0.0.1:8080 #Also show request data
```

If the server reports that the requested page has moved to a different location (indicated with a Location: header and a 3XX response code), this option makes curl redo the request on the new place.
```
$ curl -L http://127.0.0.1
```

Redirect with Location Header
```
$ curl -I http://127.0.0.1/login 
HTTP/1.1 301 Moved Permanently
Date: Sat, 06 Jan 2024 15:26:59 GMT
Server: Apache/2.4.57 (Debian)
Location: http://127.0.0.1/login/
Content-Type: text/html; charset=iso-8859-1

$ curl -I http://127.0.0.1/login/
HTTP/1.1 200 OK
Date: Sat, 06 Jan 2024 15:27:07 GMT
Server: Apache/2.4.57 (Debian)
Set-Cookie: PHPSESSID=ng11k6r2ldfdc3q5lhacv48nje; path=/
Expires: Thu, 19 Nov 1981 08:52:00 GMT
Cache-Control: no-store, no-cache, must-revalidate
Pragma: no-cache
Content-Type: text/html; charset=UTF-8
```


```
$ curl -X POST --data "log=admin&pwd=password" https://wordpress.com/wp-login.php
$ curl -X POST --data "{'option': 'value', 'something': 'anothervalue'}" -H "Content-Type: application/json" -H "User-Agent: Mozilla firefox" -H "Cookie: mycookie=chocolate" https://wordpress.com/wp-login.php
$ curl -X POST --data "@myfile.json" https://example.com #sent file from cwd
```

### Defining Proxy Server

```
#Define proxy
export http_proxy=http://your.proxy.server:port
export https_proxy=https://your.proxy.server:port
```

## Wget

```
$ wget 127.0.0.1:8080
```











