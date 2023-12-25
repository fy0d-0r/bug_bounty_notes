# note on curl utility

>  curl Stands for client url

```
-o <path>=> output (custom download)
-O => output at cwd (download at cwd with original name)
-T/--upload-file <path> => transfer local file

-L => redirect to appropriate link

--head/-I (CAP i) => only print response headers
-i => print response headers and body

-X <method> => specify HTTP request method (GET,POST,PUT,...)
-H "<header>" => specify Http headers
-v => return entire TLS handshake
--data/-d => inject data in request body
--user-agent/-A  [whatever you write] => specify user agent
-u => basic auyhentication
```

> cwd here means current working directory

#Define proxy
```
export http_proxy=http://your.proxy.server:port
export https_proxy=https://your.proxy.server:port
```

Examples

$ `curl --data "log=admin&pwd=password" https://wordpress.com/wp-login.php`

$ `curl -d "log=admin&pwd=password" -X POST https://wordpress.com/wp-login.php`

$ `curl --data "{'option': 'value', 'something': 'anothervalue'}" -H "Content-Type: application/json" -H "User-Agent: Mozilla firefox" -H "Cookie: mycookie=chocolate" -X POST https://wordpress.com/wp-login.php`

$ `curl -d "@myfile.json" -X POST https://example.com` #sent file from cwd

$ `curl -u user:pass https://example.com/`

$ `curl -u user@example.com:pass https://example.com/`

$ `curl -u user@example.com:pass -T hello.txt ftp://ftp.example.com #upload to ftp server`

$ `curl -u user@example.com:pass -O ftp://ftp.example.com/hello.txt #download from ftp server`

$ `curl -u user:pass --upload-file payload.war http://tabby.htb:8080/manager/text/deploy?path=/payload.war`

$ `curl ipinfo.io/80.91.144.2`

> Note: Curl does not store cookies. Cookies are set manually in header of the request by using -H option. 
