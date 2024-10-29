- side-by-side layout
- sidebar-article-sidebar layout
- Toggle Visibility/State on/off in an ideal way
- Grouped items using list elements, default list styling overridden
- 


## Toggle State On/Off
```html

```

```scss
.parentClass{
	&[data-status="inactive"]{
        .toggleButton{
            transform: translate(0em,0em);
        }
        .AnimationHelper{
            transform: translate($offPageDistance,$offPageDistance);
        }
    }
    &[data-status="active"]{
        .toggleButton{
            transform: translate($offPageDistance,$offPageDistance);
        }
        .AnimationHelper{
            transform: translate(0em,0em);
        }
	}
}
```