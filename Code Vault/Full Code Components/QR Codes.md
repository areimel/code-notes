# QR Code Component

> Designed for Astro with plain HTML/JS and basic props, can be easily abstracted for other frameworks.

```jsx
---
const currentUrl = window.location.href; //use if you need just the page the element appears on.
const {link, id, textLink, corners} = Astro.props;
---
<div class="qrcodeWrapper">
	
	<div 
		class="qrcodeElement" 
		id={id ? id : "qrcode"}
		data-link={link ? link : "test.com"}
	>
		{corners &&
			<div class="CornerBits">
				<div class="bit topLeft"></div>
				<div class="bit topRight"></div>
				<div class="bit bottomLeft"></div>
				<div class="bit bottomRight"></div>
			</div>
		}
	</div>
	{textLink && 
		<a href={link ? link : "test.com"} target="_blank">{link ? link : "test.com"}</a>
	}
</div>

<style>
	.qrcodeWrapper{
		position: relative;
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		.qrcodeElement{
			position: relative;
			margin: 20px;
		}
	}
	a{
		font-size: 0.65rem;
		margin-top: 1rem;
		display: flex;
		flex-direction: row;
		justify-content: center;
		align-items: center;
		text-decoration: none;
		background-color: var(--accent-color);
		color: var(--background-color);
		padding: 0.5rem 1rem;
		&::before{
			content: "[";
			font-size: 1.5em;
			text-decoration: none;
		}
		&::after{
			content: "]";
			font-size: 1.5em;
		}
	}

	.CornerBits{
		position: absolute;
		width: 100%;
		height: 100%;
		pointer-events: none;
		--size: 50px;
		--thickness: 8px;
		--offset: -20px;


		.bit{
			width: 50px;
			height: 50px;
			position: absolute;
		}
		.topLeft{
			top: var(--offset);
			left: var(--offset);
			border-top: solid var(--thickness) var(--border-color);
			border-left: solid var(--thickness) var(--border-color);
		}
		.bottomRight{
			top: var(--offset);
			right: var(--offset);
			border-top: solid var(--thickness) var(--border-color);
			border-right: solid var(--thickness) var(--border-color);
		}
		.bottomLeft{
			bottom: var(--offset);
			left: var(--offset);
			border-bottom: solid var(--thickness) var(--border-color);
			border-left: solid var(--thickness) var(--border-color);
		}
		.topRight{
			bottom: var(--offset);
			right: var(--offset);
			border-bottom: solid var(--thickness) var(--border-color);
			border-right: solid var(--thickness) var(--border-color);
		}
	}
	
</style>
```

```js
function QRCodesSet(){
	let elements = document.querySelectorAll('.qrcodeElement');
	elements.forEach(element => {
		const link = element.getAttribute("data-link");
		const elID = element.getAttribute("id");
		new QRCode(elID, link);
	});
}

document.addEventListener("DOMContentLoaded", function(){	
	QRCodesSet();
});
```