# Common HTML Snippets

## Comments Format
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

