# jQuery AJAX
## Style Guide


## Variable Naming

* It is best practice to either **prefix** or **postfix** variable names that refer to jQuery objects with a `$` symbol.

```
var myTitle = $("h1#title"); // bad
var $myDiv = $("div#greeting"); // good;
var myTotal$ = $("div#total"); // okay
```

Note: don not go wild and just add `$` symbols to every variable

```
var $myNum = 1; // bad
```

## Three Rules Of `$`

* If you give the `$` an HTML like string it will return a jQuery wrapped collection of elements that represent it.

```
var $myDiv = $("<div>Hello World</div>");
```

That would be the equivalent of writing out something like the follwoing:

```
var myDiv = document.createElement("div");
var innerText = document.createTextNode("Hello World");
myDiv.appendChild(innerText);
```
* If you give jQuery a **css selector** it will find it and return it as an object wrapped in jQuery.

```
var $myDiv = $("div#greeting");
```

* If you give jQuery a `function () {}` it will run that function after `document` is ready.

```
$(function () {
  console.log("DOCUMENT READY!");
});
```

Which is equivalent to the following:

```
$(document).ready("ready", function () {
  console.log("DOCUMENT READY!");
});
```


## Events

When setting events you should use the `jQuery#on` method.


```
var $myDiv = $("div#greeting");
$myDiv.on("click", function (e) {
  console.log("clicked");
});
```

Be sure to remember to `preventDefault()` for certain events


```
var $articleForm = $("form#newArticle");
$articleForm.on("click", function (e) {
  e.preventDefault();
  console.log("The form was stopped!");
});
```

If you just have an `input` field not in a form you might listen for a `change` event.

```
var $input = $("input#playerName");
$input.on("change", function (e) {
  var $this = $(this);
  var playerName = $this.val();
  console.log("Player name", playerName);
});
```

If you want to quickly gather all the input field name and value pairs from a form you should use `jQuery#serialize`


```
var $newArticle = $("form#newArticle");
$newArticle.on("change", function (e) {
  var $this = $(this);
  console.log("Article info", $this.serialize());
});

```








