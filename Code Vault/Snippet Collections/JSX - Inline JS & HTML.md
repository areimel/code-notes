# JSX | Inline JS & HTML

## Simple Conditional Renders

```jsx
//if-render
{varName && varName}
{varName && "text"}
{varName && 
	<div>HTML</div>
}

//if-else-render
{varName ? varName : "default value"}

{varName ? 
	<div>
		{varName}
	</div> 
: 
	<div>Default HTML</div>
}
```

## Map | Loop Through Items In Array
```jsx
import React from 'react';

const ItemList = () => {
    const items = ['Apple', 'Banana', 'Cherry', 'Date'];

    return (
        <ul>
            {items.map((item, index) => (
                <li key={index}>{item}</li>
            ))}
        </ul>
    );
};

export default ItemList;
```
