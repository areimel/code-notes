# Next.js MasterComponent Code

Use this basic component to clone out new React/Next.js components with the basic code you'll typically use already pre-set-up for you.

## File Structure
### index.js
```jsx
export { default } from './MasterComponent'
```
### styles.scss
```scss
@import "@styles/vars.module.scss";

.MasterComponent{
	.image{}
	.title{}
	.previewText{}
}

.SubComponent{}
```
### MasterCompnent.js
```jsx
/*===== Components =====*/
import React, { useState, useEffect } from 'react';
import Script from 'next/script'
import Image from 'next/image'
import Link from 'next/link'

import Button1 from '@components/Button1'

/*===== Styles =====*/
import componentStyles from './styles.module.scss'


export default function MasterComponent({ 
  //Props
  id, image, title, 
  previewText, author, date
}) {
	
//pre-render JS goes here
//console.log("MasterComponent | pre-render js test");
useEffect(() => {
	//post-render JS goes here
	//anything that needs DOM/window interaction
	//console.log("MasterComponent | useEffect() js test");
}); //END useEffect()

return (
	<div className={componentStyles.MasterComponent}>
		{image ? 
			<img src={image} alt="" />
			:
			<span>[NO IMAGE]</span>
		}
       
        <Link href={`/posts/${id}`}>
          <a className={componentStyles.title}>{title}</a>
        </Link>
        
        {previewText && 
          <p className={componentStyles.previewText}>
            {previewText}
          </p>
        }
        
        <div className={componentStyles.readMore}>
          <Button1
             href={`/posts/${id}`}
             text="READ MORE"
          />
        </div>
        
        <div className={componentStyles.postMetas}>
          {author &&
            <span className={componentStyles.author}>{author} | </span>
          }
          {date &&
            <span className={componentStyles.date}>
              <Date dateString={date}  />
            </span>
          }          
        </div> 
             
    </div>
) //END component return
} //END component export

```