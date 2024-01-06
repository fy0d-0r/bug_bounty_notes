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











