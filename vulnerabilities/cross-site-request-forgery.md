# Cross Site Request Forgery (CSRF/XSRF)

CSRF is an attack where the attacker causes the victim user to carry out an action unintentionally while that user is authenticated.
It is also known as one-click attack or session riding


> CSRF attacks exploit the trust a Web application has in an authenticated user
>
> XSS attacks exploit the trust a user has in a particular Web application


## CSRF Token

The csrf token should be transmitted to the client within a hidden field in an HTML form, submitted using HTTP POST requests

## Examples

A example post request for deleting an account.
```
POST /delete_my_account HTTP/1.1
Host: vulnerable.com
Content-Type: application/x-www-form-urlencoded
Cookie: SessionId=d34dc0d3

delete=1
```

On the malicious site
```
<form
	action="http://vulnerable.com/delete_my_account"
	method="POST"
	id="csrf_form">
	<input type="hidden" name="delete" value="1" />
</form>

<script>
	document.getElementById('csrf_form').submit();
</script>
```




### Cross Domain Access Controls

Same Origin Policy (Same Domain, Same Schema, Same TCP Port)

![url](https://github.com/fy0d-0r/bug_bounty_notes/blob/main/images/sop.png)


CORS (Cross origin Resource Sharing) is basically a bypass for same origin policy in a good way.
This is only allowed if the server explicitly lets you.

## JSON CSRF with appropriate Content-Type header via AJAX requests

The browser does not just allow you to set any headers you want unless
the server explicitly lets you do it using CORS.

You can only set your Content-Type header if the server sends back 
your domain and the header that you want to set which has Content-Type
in the response header.
```
Access-Control-Allow-Origin: your website
Access-Control-Allow-Headers: Content-Type
```

### Adobe Flash
You can forge the Content-Type header using flash files but the thing is
the cookie won't be sent along with it unless we have that cross domain XML
and other things.
A simple redirect(like 307) can solve this.
We add a Content-Type header in the flash file and 
all the json post data that we want to send.
We also specify the request endpoint which is NOT the vulnerable site
but instead to our 307 redirect page which in turn redirects to vulnerable website
In this way, we can make the cookie sent along with our forged request.

