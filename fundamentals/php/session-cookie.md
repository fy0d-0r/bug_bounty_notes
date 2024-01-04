# Setting Cookie
```
<?php
setcookie("name", "value"); //Set-Cookie: name=value
?>

<?php
setcookie("name", "value", time() + 86400);
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
