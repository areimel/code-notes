# Common CSS Snippets

## Comments Formats
```css
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

```

## Variables & Functions

Variables - MUST be inside a selector, use html/root/body to make it global, inside a class to make it scoped.

### Soft Black/White Color Vars
```scss
:root{
	--black: #28282B;
	--white: #FAF9F6;
	
	--lightGray: #DAD9D6;
	--darkGray: #3A3936;
}
```
### Cyberpunk 2077 Color Vars
```css
:root{
  /* Color Scheme - Cyberpunk 2077 pallete */
  --black: #050A0E;
  --white: #FAFAFA;
  --yellow: #F3E600;
  --red: #FF003C;
  --teal: #00F0FF;
}
```

---
## Reset Snippets

### HTML/Body Reset
```scss
html,body {
	padding: 0;
	margin: 0;
	//system font stack
	font-family: -apple-system, BlinkMacSystemFont, Segoe UI, Roboto, Oxygen,
	  Ubuntu, Cantarell, Fira Sans, Droid Sans, Helvetica Neue, sans-serif;
	//main font
	font-family: $fontBody, monospace;
	line-height: 1.35;
	font-size: $fontSizeBody;
	color: $textColor;
	background-color: $backgroundColor;
	height: 100vh;
	overflow: hidden;
	overscroll-behavior-x: none;
	
	
	@media (max-width: $phoneBreakpoint) {
		/* height: auto;
		overflow: auto;
		overscroll-behavior-x: none; */
		font-size: $fontSizeBodyMobile;
	}
}
```

### Box-Size Reset
```css
*,
*:before,
*:after {
	box-sizing: border-box;
}
```

### Image Reset
```css
img, picture, video, canvas, svg {
	max-width: 100%;
	width: 100%;
	height: auto;
	display: block;
}
```

### Text Reset
```scss
p, span, ul, li, {
	margin: 0;
}
ul{
	margin: 0px;
}
li::marker {
	color: $accentColor;
}

h1, h2, h3, h4, h5, h6{
	margin: 0;
	line-height: 1.2;
	margin: 0;
	font-size: $fontSizeHeading;
}

hr{
	//border-width: 2px;
	border: none;
	height: 2px;
	background-color: $black;
}
```

### Link reset
```scss
/*all links*/
a{
	text-decoration: none;
	&:hover{
		text-decoration: underline;
		text-decoration-style: dotted;
	}
}
/*all links without a class*/
a:not([class]){
	color: #0070f3;
	&:hover {
		text-decoration: underline;
	}
}
```

---


## Global Page-Level Tweaks

### Selection / Text Highlight
```css
::selection{
	background-color: $accentColor;
	color: $white;
}
```

### Custom Scrollbar
```css
*::-webkit-scrollbar {
	width: clamp(2px, 0.25vw, 5px);
}
*::-webkit-scrollbar-track {
	box-shadow: inset 0 0 6px rgba(0, 0, 0, 0.3);
}
*::-webkit-scrollbar-thumb {
	background: $accentColor;
}

*{
	-webkit-backface-visibility: hidden;
	-moz-backface-visibility:    hidden;
	-ms-backface-visibility:     hidden;
	backface-visibility: hidden;
}
```


## Utility CSS

### Will-Change Utility
Notes: 
- 'will-change' eats up device resources, so don't overuse it. 
- It can also cause unexpected animation or rendering issues in very specific cases where having the animation ready to go might cause a state change on its own.
```css
*[data-will-change="transform"]{
  will-change: transform;
}
*[data-will-change="color"]{
  will-change: color;
}
*[data-will-change="opacity"]{
  will-change: opacity;
}
```
## Layout Snippets

### Simple Responsive Max Width
``` css
div{
	display: block; 
	width: 100%;
	max-width: 400px; 
	margin: auto;
}
```

### Flexbox
```css
div{
	display: flex;
	flex-direction: row;
	justify-content: center;
	align-items: center;
}
```

## Show/Hide Snippets

### Hide element while preserving it's space
```css
opacity:0;
pointer-events:none;
```

Don't use this a basic `display: none;`, unless you need to remove the element from the content flow.
``` css 
div{
	display: none;
	/* Removes element from content flow, surrounding elements may re-flow to fill space */
}

```

---
## Responsive Code

### Basic Media Queries
```css
@media (max-width: 1000px) {
  /* Activates BELOW 1000px, aka DESKTOP-FIRST */
}

@media (min-width: 1000px) {
  /* Activates ABOVE 1000px, aka MOBILE-FIRST */
}

@media (min-width: 600px) and (max-width: 1000px){
  /* Activates BETWEEN 600px - 1000px */
}
```

### Advanced Media Queries

### Niche Media Queries
```scss
//Print-only
<link rel="stylesheet" media="print" href="print.css">
```