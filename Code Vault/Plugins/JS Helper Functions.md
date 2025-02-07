# JS Helper Functions - Final Name TBD

## Possible Names
- utility.js
- helper-functions.js
- 

Functions to package into a globally-available package similar to jQuery, but just functions I find I need in my day-to-day work or that I feel are basic features that should exist but are lacking.

## Browsing Behavior
- ==UrlParameterLogger()==
	- Mostly completed already, can still be optimized

- ==Timestamp()==
	- suggested method: sets absolute-millisecond value - time since standard global computer calendar start date
	- TO-DO: figure out best way to tie timestamp to data - individual items or batch?
	- Sub-Functions:
		- ==TimestampToDate()==
			- Converts absolute milliseconds to human-readable date.
		- ==TimestampExpireSet()==
			- Sets a secondary value for how long until timestamped data expires and is cleared from user's session.
			- Find how many milliseconds are in 1 day, 7 days, 30 days, 90 days, etc
			- Give preset options OR number of days as a parameter
		- ==TimestampExpireCheck()==
			- Checks the main timestamp value against the expiration value
		- ==TimestampExpireClear()==
			- Clears/resets UrlParameterLogger() data tied to timestamp.

- ==LinkTagHelper()==
	- set all PDFs to open in a new tab
	- set all external site links to open in a new tab
	- set all '#' or 'no href' links to preventDefault
	- Off-site link alert handler - popup activation with new tab link button

## DOM Element Manipulation
- Functions that check if things exist:
	- ex: `if(CheckForAttr('.target','data-attr') == 'true'){//do something}`
	- return true/false
	- ==CheckForClass()==
	- ==CheckForAttr()==
	- ==IfElementExists()==
	- ToggleDisplay(target, toggleClass)
	- ToggleClass(target, toggleClass)
	- ToggleActive(target, toggleAttr)

## Design Helper Functions
- ==ViewportToPixels()==
	- Set up to work as a function called inside the inline HTML for width/height attributes that are normally pixel-only
	- Use with anything that accepts only absolute numeric value
	- set up rounding to nearest pixel
	- set up re-running on viewport resize
- ==MediaQuery(min/max, pixelSize)==
	- Media Queries in JS

## Brainstorming
Ideas to explore:
- 'do this action to all of this selector' - shorthand version
- 'do this thing on interaction with a form'