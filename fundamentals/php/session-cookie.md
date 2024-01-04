## Setting Cookie
```
<?php
setcookie("name", "value");
// Set-Cookie: name=value
// $_COOKIE['name'] => value //This globle variable assign automatically and exclusively on setcookie() and not on session_start()
?>

<?php
setcookie("name", "value", time() + 86400);
// Set-Cookie: name=value; expires=Fri, 05 Jan 2024 17:56:34 GMT; Max-Age=86400
?>
```

## Destroying Cookie

```
<?php
setcookie("name", "value", time() - 1);
// Set-Cookie: name=value; expires=Wed, 03 Jan 2024 18:13:55 GMT; Max-Age=0
?>
```

# PHPSessionID

### Starting Session

```
<?php
session_start(); //Set-Cookie: PHPSESSID=qu99kc5vp9vnro63fvidopci98; path=/
$_SESSION['name'] = "value";
?>
```

Diff: a session ends as soon as you close down your browser while a cookie has a time limit.
