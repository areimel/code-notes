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
	color: var(--list-marker-color, inherit);
}

h1, h2, h3, h4, h5, h6{
	margin: 0;
	line-height: 1.2;
	margin: 0;
	font-size: var(--heading-reset-size, 3.5rem);
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

### Prevent Highlight Utility
```scss
*[data-prevent-highlight="true"] {
	-webkit-user-select: none; /* Safari */
	-ms-user-select: none; /* IE 10 and IE 11 - deprecated */
	user-select: none; /* Standard syntax */
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
#### Basic Usage
```css
div{
	display: flex;
	flex-direction: row;
	justify-content: center;
	align-items: center;
}
```

#### Flex parent container with evenly-heighted child elements
```css
.flexContainer{
	display: flex;
	justify-content: center;
	align-items: flex-start;
	flex-direction: row;
	flex-wrap: wrap;
	margin: 0 -1rem;
}

.flexCard{
	align-self: stretch; /* critical - enforces same-height of child elements */
	max-width: 100%;
	width:350px;
	border: solid 1px #000;
	padding: 1rem;
	margin: 1rem;
}
```

### Fixed/Dynamic Side-by-Side Layout
Notes:
- 2 side-by-side sections, one with a fixed pixel width, and the other filling up the rest of the parent element width. 
- Ideal for presenting content such as a featured or lockup image (fixed side) next to a block of text (dynamic side).
```css
.parentContainer{
	--fixedWidth: 500px;
	display: flex;
	flex-direction: row;
	justify-content: center;
	align-items: center;
}

.innerSection{
	align-self: stretch;
	padding: 2rem;
}

.fixedSide{
	width: var(--fixedWidth);
	background: #000;
	color: #FFF;
}

.dynamicSide{
	width: calc(100% - var(--fixedWidth));
	background: #FFF;
	color: #000;
}
```
## Show/Hide Snippets

### Hide element while preserving it's space
```css
.showHide{
	transition: 0.15s ease-in-out;
	opacity: 1;
	pointer-events: auto;
}
.showHide[data-hidden="true"]{
	opacity:0;
	pointer-events:none;
}
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
@media print {
  /* Activates BELOW 1000px, aka DESKTOP-FIRST */
}
```

### Go-to Breakpoints
```css
/* Expected default range: 1200px-2560px */
/* Responsive behavior: 
	- Desktop-first
	- tablet & mobile device breakpoints
	- 4k & large screen support 
	- print support
*/

@media screen and (max-width: 1025px) {
  /* Activates BELOW 1025px, Laptop treatment */
}

@media screen and (max-width: 768px) {
  /* Activates BELOW 768px, Tablet treatment */
}

@media screen and (max-width: 425px) {
  /* Activates BELOW 425px, Mobile-L treatment */
}

@media screen and (max-width: 375px) {
  /* Activates BELOW 375px, Mobile-M treatment */
}

@media screen and (max-width: 320px) {
  /* Activates BELOW 320px, Mobile-S treatment - smallest size */
}

@media screen and (min-width: 2560px) {
  /* Activates ABOVE 2559px - 4K / Large Screen treatment - largest size */
}


```


## Typography

### Nicer Headlines
```css
h1{
 text-align: center;
 text-wrap: balance;
 /* OR: text-wrap: pretty; */
}
```

### No Wrap Text
```css
.noWrap{
	text-wrap: nowrap;
}
```


## Gradients

### Basic Stripes

Tool: https://stripesgenerator.com/ 
```scss
--color1: #000000;
--color2: #FFFFFF;

background-image: linear-gradient(45deg, var(--color1) 25%, var(--color2) 25%, var(--color2) 50%, var(--color1) 50%, var(--color1) 75%, var(--color2) 75%, var(--color2) 100%);
background-size: 56.57px 56.57px; //translates to 20px wide stripes due to triangle equation
```