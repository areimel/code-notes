# Astro SiteLayout Code

Description Text

---
## File Structure
### Layout.astro
```jsx
---
//Styles
	import "@styles/main.scss"

//Components
	//import MasterComponent from '@components/MasterComponent.astro';
	import Header from '@components/Header.astro';
	import Footer from '@components/Footer.astro';

//Props
	const titleTail = "Site/Company Name";
	const defaultTitle = "Default Site Title";
	const defaultDescription = "Default Description Text";
	const { title, description, heading } = Astro.props;
---

<!doctype html>
<html lang="en" data-theme="light">
	
	<head>
		<meta charset="utf-8"/>
		<meta name="viewport" content="width=device-width, initial-scale=1" />
		
		<title>{title ? title : defaultTitle} | {titleTail}</title>
		<meta name="description" content={description ? description : defaultDescription} />
		<link rel="icon" type="image/svg+xml" href="/favicon.svg" />
		<meta name="generator" content={Astro.generator} />	

		<!-- Head scripts -->
		<!-- jQuery - old, only use if needed -->
		<script 
			is:inline 
			src="https://cdnjs.cloudflare.com/ajax/libs/jquery/3.7.1/jquery.min.js" 
			integrity="sha512-v2CJ7UaYy4JwqLDIrZUI/4hqeoQieOmAZNXBeQyjo21dadnwR+8ZaIJVT8EE2iyI61OV8e6M8PP2/4hpQINQ/g==" 
			crossorigin="anonymous" referrerpolicy="no-referrer"
		></script>
		
		
	</head>
	
	<body>
		
		<Header/>
		
		<main>
			<!-- Inner page content -->
			<slot />
		</main>

		<Footer />
		
		<!-- Post-Footer scripts -->
		<script is:inline src="/functions.js"></script>
		
	</body>
	
</html>

<style lang="scss" is:global>
	/* is:global applies this snippet globally, not component-scoped */
</style>

<style lang="scss">
	/* component-scoped css*/
</style>	

```