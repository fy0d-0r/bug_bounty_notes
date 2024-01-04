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

### Cross Domain Access Controls

Same Origin Policy (Same Domain, Same Schema, Same TCP Port)

![url](https://github.com/fy0d-0r/notes/blob/main/web/fundamentals/images/url.png)





