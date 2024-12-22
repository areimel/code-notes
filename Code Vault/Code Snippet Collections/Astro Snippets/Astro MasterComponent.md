# Astro MasterComponent Code

Use this basic component to clone out new Astro components with the basic code you'll typically use already pre-set-up for you.

## File Structure
### MasterComponent.astro
```jsx
---
//Imports
//import MasterComponent from '@components/MasterComponent.astro';
import SubComponent from './SubComponent.astro';

//vars & props
const onPageVar = "variableValue";
const { title, subtitle, fallbackVar="defaultFallbackValue" } = Astro.props;
---

<div class="MasterComponent">
	<h2 class="title">
		{title ? title : "Title Text"}
	</h2>
	<p class="tagline">
		{subtitle && "Subtitle Text"}
	</p>
	
	<div>
		<!-- Child Content Slot -->
		<slot>
			This is the fallback content for this component's main child section
		</slot>
	</div>
	
	<div>
		<!-- Inner Content -->
		<slot name="namedSlot1">
			This is the fallback contnent for namedSlot1
		</slot>
		<slot name="namedSlot2">
			This is the fallback contnent for namedSlot1
		</slot>
	</div>
</div>

<style lang="scss">
	.MasterComponent{

	}
</style>

```

## Children / Slots
```jsx
<MasterComponent>
	<Fragment slot="namedSlot1"> 
		Named Slot #1 Inner Content
	</Fragment>
	
	<Fragment slot="namedSlot2"> 
		Named Slot #2 Inner Content
	</Fragment>
</MasterComponent>
```

### SubComponent.astro
Sub-Components work exactly the same as any other component, they're just placed inside a sub-folder and typically only used by another higher-level component.
```jsx
---
//Imports
//import MasterComponent from '@components/MasterComponent.astro';

//vars & props
const {} = Astro.props;
---

<div class="SubComponent">
	SubComponent Content
</div>

<style lang="scss">
	.SubComponent{
		border: solid 1px #000;
		padding: 1rem 2rem;
	}
</style>

```
