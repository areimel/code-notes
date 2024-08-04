# Common CSS Snippets

## Comments Format
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

Box-Size Reset
```css
*,
*:before,
*:after {
	box-sizing: border-box;
}
```

Image Reset
```css
img {
	max-width: 100%;
	width: 100%;
	height: auto;
	display: block;
}
```

Link reset
```css
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
## Layout Snippets

Simple Responsive Max Width
``` css
div{
	display: block; 
	width: 100%;
	max-width: 400px; 
	margin: auto;
}
```

Flexbox
```css
div{
	display: flex;
	flex-direction: row;
	justify-content: center;
	align-items: center;
}
```

## Show/Hide Snippets

Hide element while preserving it's space
```css
opacity:0;
pointer-events:none;
```


``` css 


```

---
## Responsive Code

Basic Media Query
```css
@media (max-width: 1000px) {
  /*Activates BELOW 1000px*/
}

@media (min-width: 1000px) {
  /*Activates ABOVE 1000px*/
}

@media (min-width: 600px) and (max-width: 1000px){
  /*Activates BETWEEN 600px - 1000px*/
}
```