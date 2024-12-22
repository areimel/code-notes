## Basic

### Flashing on/off
```css
.flashingElement{
	animation: flash 1.5s linear infinite;
	
	@keyframes flash {
		0%, 49% { opacity: 1; }
		50%, 99% { opacity: 0; }
		100% { opacity: 1; }
	}
}
```