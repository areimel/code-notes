## Comments Format

Some simple comment styles for easier readability
```javascript
/* ============================================================ */
/*
	Notes Comments Section
	- Notes content
	- Notes content
*/
/* ============================================================ */

/* ===== ==================== ===== */
/* ===== Comment Header Block ===== */
/* ===== ==================== ===== */

/* ===== Comment SubHeader Block ===== */

/* Comment Minor Block */

//Inline Comment

```


## Variable Syntax
```js
var variableName = "value"; //old, avoid using

//new syntax
let variableThatCanChange = "value"; //variable can be updated
const variableThatNeverChanges = "value"; //variable MUST stay the same

//if variable is empty, give it a default value
myVariable = myVariable || 'defaultValue';
```

---
## Basic Functions

### Basic Function Syntax
```js
function FunctionName(parameter){
	let newVar = parameter;
}
```

### Event Listener Syntax
```js
element.addEventListener('click', function() {
	element.setAttribute("data-analytics-proximity-state", "false");
});
```

### Page Content Loaded
```javascript
//short
document.addEventListener('DOMContentLoaded', functionToRun); 
window.addEventListener('readPageUpdated', functionToRun);

//long
document.addEventListener("DOMContentLoaded", function(e){
	//runs code after DOM load
});
```

### Selector-Abstracted Function Template
Plug in a selector as the function prop/variable and use that as the base
```js
//Targets a single element and it's children
function singleAbstractedFunction(elementID){
	const target = document.querySelector(`${elementID}`);
	const var1 = document.querySelector(`${elementID} .element1`);
	const var2 = document.querySelector(`${elementID} .element2`);

	target.innerHTML = 'updated';

}
```


---
## Targeting and Modifying Elements

### Target a single **instance** of `#targetElement` and add/remove an `.active` class
```js
let element = document.querySelector('#targetElement');
//do the thing
element.classList.add("active");
//element.classList.remove("active");
```

### Target all instances of `.targetElement` and add/remove an `.active` class
```js
let elements = document.querySelectorAll('.targetElement');
elements.forEach(element => {
	//do the thing
	element.classList.add("active");
	//element.classList.remove("active");
});
```

### Target a parent class, and then use that to target child elements
```js
//Parent Element
	let parentElement = document.querySelector('#targetElement');
//Child Elements
	let childElement1 = parentElement.querySelector('.class1');
	let childElement2 = parentElement.querySelector('.class2');
	let childElement3 = parentElement.querySelector('.class3');

//do the thing
	childElement1.classList.add("active");
	childElement2.classList.add("active");
	childElement3.classList.add("active");
```


### Grab an element's data-attribute value
```js
let dataAttrVar = element.getAttribute("data-attr-var");
```

### Update an element's data-attribute value
```js
element.setAttribute("data-attr-var", "value");
```

## Update/Replacing/Modifying Text

```js
element.innerHTML = "new text";
```

### Add HTML text before/after and inside/outside another element
```Javascript

element.insertAdjacentHTML("beforebegin", htmlString); //insert before/outside
element.insertAdjacentHTML("afterbegin", htmlString); //insert inside/start
element.insertAdjacentHTML("beforeend", htmlString); //insert inside/end
element.insertAdjacentHTML("afterend", htmlString); //insert after/outside
```

---
```

```
## User Actions

### Event Listener
```javascript
element.addEventListener("click", FunctionToRun, false);
//OR
element.addEventListener('click', function() {
	//do the thing
	console.log(this.className); 
	// logs the className of element - works like jquery
}, false);
```

Target the element you just referenced
```js
var onClickThis = event.currentTarget;
```

---
## URL-Related

```js
//url ex: https://ui.dev/get-current-url-javascript/#hashVal?comments=false

//shorthand use like: window.location.href / window.location.hash / window.location.origin / etc

const {
  host, hostname, href, origin, pathname, port, protocol, hash, search
} = window.location

host // "ui.dev"
hostname // "ui"
href // "https://ui.dev/get-current-url-javascript/?comments=false"
origin // "https://ui.dev"
pathname // "/get-current-url-javascript/""
port // ""
protocol // "https:"
hash // "#hashVal"
search // "?comments=false"
```

URL Redirect
```js
window.location.replace("/redirect-url")
```

If current page is index/home page
```js
//If current page is equal to base url, ie is this currently the home page?
//extra slash "/" on href gets trimmed off for comparison
//href: current page, origin: base URL
if(location.href.slice(0, -1) == location.origin){
  //currently on index page
} else{
  //currently not on index page
}
```

Get URL parameters
```js
// You can get url_string from window.location.href if you want to work with
// the URL of the current page
// example: var url_string = "http://www.example.com/t.html?a=1&b=3&c=m2-m3-m4-m5"; 
var url = new URL(window.location.href);
var urlParamValue = url.searchParams.get("urlParamName");
console.log(urlParamValue);
```

---

## Timing-Related

### setTimeout()
```js
setTimeout(() => {
  console.log("Delayed for 1 second.");
}, 1000); //time in ms
```

### setInterval()
```js 
function CycledFunctions(){
  function1();
  function2();
  //generic code to execute
}
setInterval(CycledFunctions, 1000); //time in ms
```
## Console.log Tools

console.log Groups
```js 
//Pre-collapsed
console.groupCollapsed("===== Console.log Group =====");
  console.log("line 1: ["+variable_1+"]");
  console.log("line 2: ["+variable_2+"]");
  console.log("line 3: ["+variable_3+"]");
console.groupEnd();

//Pre-opened
console.group("===== Console.log Group =====");
  console.log("line 1: ["+variable_1+"]");
  console.log("line 2: ["+variable_2+"]");
  console.log("line 3: ["+variable_3+"]");
console.groupEnd();
```

---

## Mixing CSS & JS

### Access CSS custom var values from inside JS
```js
const root = document.querySelector(`:root`);
const element = document.querySelector(`.element`);

// get variable from root
getComputedStyle(root).getPropertyValue("--my-var");

// get variable from specific element
getComputedStyle(element).getPropertyValue("--my-var");

// set variable on inline style
element.style.setProperty("--my-var", "#FFF");
```

### Access pseudo-element content values
```js
const element = document.querySelector(".element");
const result = getComputedStyle(element, ":after").content; //:after
//const result = getComputedStyle(element, ":before").content; //:before
console.log(`pseudo-element content value is: ${result}`)
```