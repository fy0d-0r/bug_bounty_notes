# Open Redirection

when an application allows a user to control 
a redirect or forward to another URL.

an attacker could supply a URL that redirects 
an unsuspecting victim from a legitimate domain to an attacker’s phishing site.


Check for Open Redirect
- Login
- Sign-up
- Check out
- Register
- Password Reset
also often found inside a flask.


`mysite.com/open?url=mysite.com/home`

```
mysite.com/open?password_reset?token=ashdtevxisb73h6_4gs911h3v&url=attacker.com/home
```


