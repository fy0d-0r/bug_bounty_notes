## XMLHTTPRequest

```
var ourRequest = new XMLHTTPRequest();
ourRequest.open('GET', 'https://learnwebcode.github.io/json-example/animals-1.json');
ourRequest.onload = function() {
  var ourData = ourRequest.responseText;
  console.log(ourData[0]);
};
ourRequest.send();
```
