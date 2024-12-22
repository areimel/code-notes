# React and Next.js Snippets

## Importing Components

### Standard Components
```jsx
/*===== Standard Imports =====*/
	import React, { useState, useEffect } from 'react';
	import Script from 'next/script'
	import Image from 'next/image'
	import Link from 'next/link'

/*===== Custom Component Imports =====*/
	import SubComponent from './SubComponent'
	import Button1 from '@components/Button1'

/*===== Site/App Global Data =====*/
	import data from "@data/data.json"

/*===== Styles =====*/
	import componentStyles from './styles.module.scss'
	import globalStyles from '@styles/globalStyles.module.scss'
```

### Base-Level Layout Components
```jsx
/*===== Standard Imports =====*/
	import React, { useState, useEffect } from 'react';
	import Script from 'next/script'
	import Image from 'next/image'
	import Link from 'next/link'
	import Head from 'next/head'
	import { router } from 'next/router'

/*===== Custom Component Imports =====*/
	import Button1 from '@components/Button1'

/*===== Site/App Global Data =====*/
	import data from "@data/data.json"

/*===== Styles =====*/
	import 'normalize.css';
	import componentStyles from './styles.module.scss'
	import globalStyles from '@styles/globalStyles.module.scss'

/*===== 3rd Party JS Code =====*/
	//import $ from 'jquery' //only if jQuery is needed
	//import {isTablet, isSafari, isIPad13} from 'react-device-detect';
	import { GoogleTagManager } from '@next/third-parties/google'

//Swiper
/*===== Swiper Code - only use if needed =====*/
	/* import { register } from 'swiper/element/bundle';
	import { Controller } from 'swiper/modules';
	// register Swiper custom elements
	register(); */
```