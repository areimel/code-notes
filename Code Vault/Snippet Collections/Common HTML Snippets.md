# Common HTML Snippets

Things to add:
- semantic layout
- basic html page boilerplate
- viewport tag
- 

## Comments Formats
```html
<!-- ============================================================ -->
<!--
	Notes Comments Section
	- Notes content
	- Notes content
-->
<!-- ============================================================ -->

<!-- ================================ -->
<!-- ===== Comment Header Block ===== -->
<!-- ================================ -->

<!-- ===== Comment SubHeader Block ===== -->

<!-- Comment Minor Block -->

```
## Basic Layouts

Basic Full Width Section with Inner Container-Sized Content
```html
<section class="fullWidthSection">
	<div class="container">
		Inner Content Goes Here
	</div>
</section>

<style>
	.fullWidthSection{
		display: block; 
		width: 100%;
		background-color: #FFFFFF;
	}
	.container{
		display: block; 
		width: 100%;
		max-width: 1000px; 
		margin: auto;
		padding: 15px 15px;
	}
</style>
```

Basic Split Layout
```html
<div class="splitLayout">
	<div class="cell left">
		<!-- left/top section -->	
	</div>
	<div class="cell right">
		<!-- right/bottom section -->
	</div>
</div>

<style>
	.splitLayout{
		display: flex;
		flex-direction: row;
		justify-content: flex-start;
		align-items: flex-start;
	}
	.splitLayout .cell{
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		width: 50%;
	}
	
	/*RESPONSIVE*/
	@media (max-width: 1000px) {
		/*Activates BELOW 1000px*/
		.splitLayout{
			flex-direction: column;
		}
		.splitLayout.mobileReverse{
			flex-direction: column-reversed;
		}
		.splitLayout .cell{
			width: 100%;
		}
	}
</style>
```


## Head Snippet
```html
<head>
	title="Page Name | Site Name"
	<link rel="icon" href="/favicon.png" />
	<meta
		name="description"
		content="Site description text"
	/>
</head>
```

## CSS & JS File Links

```html
<script src="/js-file-name.js"></script>
```

