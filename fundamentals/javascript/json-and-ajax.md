# JSON (JavaScript Object Notation)

# AJAX (Asynchronous JavaScript And XML)
AJAX loads in data without refreshing the browser.

## XMLHttpRequest or AJAX Request

```
var ourRequest = new XMLHttpRequest();
ourRequest.open('GET', 'https://learnwebcode.github.io/json-example/animals-1.json');
ourRequest.onload = function() {
  var ourData = JSON.parse(ourRequest.responseText);
  console.log(ourData[0]);
};
ourRequest.onerror = function() {
  console.log("Connection error");
};
ourRequest.send();

console.log(ourRequest.status);
```
