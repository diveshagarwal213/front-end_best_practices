## Table of Contents
+ Good Practice 
	+ [Box-sizing](#box-sizing)
	+ [Css Variables](#root-selector-variables)
	+ [Font-size 62.5%](#font-size)
	+ [Styling button and anchor tag](#button-and-a-tag-styling)
	+ [Avoid using 'gap' property with 'flex'](#flex-box)
	+ [table-of-contents](#table-of-contents)

+ Bad Practice
	+ [over using important rule](#over-using-the-important-rule)
	+ [Using-inefficient-css-selectors](#using-inefficient-css-selectors)	

+ Css tips,tricks and guides
	+ [UseFul links](#css-tipstricks-and-guides-useful-links)	
	+ [The trick to viewport units on mobile](#The-trick-to-viewport-units-on-mobile)	


# Box-Sizing

	*{
		margin: 0;
  		padding: 0;
  		box-sizing: border-box;
	}

+ If you set box-sizing: border-box; on an element, padding and border are included in the width and height. [click here](https://www.w3schools.com/css/css3_box-sizing.asp) to read more about box-sizing property. 
+ Removing all default margin and padding will maintain your un-defined styling same across all browsers.   

# Root Selector (variables)

### Creating variables

	:root{ 
		--primary: #2f4bc9;  
		--primary-text: #fff;

		--secondary: #fff;
		--secondary-text: #151515;
		
		--primary-font-family: "Oswald", sans-serif;
		--secondary-font-family: "Roboto", sans-serif;
		
		--primary-radius: 4px;
		--primary-border: 1px solid #2f4bc9;
	}
+ variable name always start with '--'.

### Using variables
	.className{
		property-name : var(--primary);
		property-name : var(--primary, fallBackValue);
	}	

+ You can create variables of any value and then use them anywhere in the css
+ optional fallback-value will be use if var is undefined  	



# Font Size

	html {
  		font-size: 62.5%;
	}
	body {
  		font-size: 1.6rem;
	}

 [click here](https://www.aleksandrhovhannisyan.com/blog/62-5-percent-font-size-trick/) to read why we set font-size  to 62.5%.
  
> ✅ Always set font-size of input, select & textarea (user input tags) greater or equal to __16px__ So, we can avoid auto-zoom in safari browsers.


# button and a tag Styling
###	 Fixing default styling 
	a {
		text-decoration: none;
		outline: none;
	}

	button {
		cursor: pointer;
		border: none;
		outline: none;
		background: transparent;
	}

### Style them using theme based classes

	.btn-primary{
		/* css declarations */
	}
	.btn-primary:focus { 
		/* css declarations */
	}
	.btn-primary:active {
		/* css declarations */
	}

	@media (hover: hover) {
		.btn-primary:hover {
			/* css declarations */
		}
	} 

> ✅ Always define on **focus** css for button and a tags, because on desktop user can use tab-key to focus on clickable elements 

+ after removing default border and background, we can easily warp icons,svg,img with button tag.  
+ outline: none; will remove default focus styling. 
+ @media (hover: hover) only applies styles when the user's primary input mechanism (such as a mouse) can hover over elements.

+ try to style btn-theme classes in a way, that if we apply it on button or anchor tag the style look approximately same. 

+ if you are applying a border effect on-focus or on-hover then give it a default transparent border the exact size(px). it will prevent small ui shifting.   

# Flex-Box

### Try not to use gap, row, column gap properties with flex.
	
	.className{
		display: flex;
		❌ gap: value;  
		❌ row-gap: value; 
		❌ column-gap: value; 
	}

+ Safari browser v14 and below version dose not support gap property with flex. 	

###	✅ You can use '>' and '*' to achieve similar behaviour. 
	
	.className{
    	display: flex;
	}
	.className > * {
		margin-bottom: 10px; /* similar to row gap */
		margin-right: 10px; /* similar to column gap */
	}
	.className > :last-child{
		margin-bottom: 0;
		margin-right: 0;
	}

+ last-child selector is used to remove extra margin in the end. 

# Use a CSS Table of Contents 

	/* Project Meta */

	/* reset */
	
	/* themes */

	/* general  */

	/* header */

	/* footer */

	/* Page template A */

	/* Page template B */

	/* Media Queries */

+ it will help you track down your code easily as you move along. Keep things organized and you will write styles more efficiently.

+ for example see [sample.scss](./Sample.scss) 


# Over Using the !important Rule

+ Using the __!important__ rule is often considered a bad practice due to the clutter it can bring with one of CSS’s core mechanisms which is specificity.

+ __Recommendation:__ You should only use the !important rule when overriding styles in a user style sheet, overriding 3rd party code and inline styles as well as utility classes.

# Using Inefficient CSS Selectors

When you are using selectors, the longer it is, the higher specificity it will comprise. This can break the CSS cascade and mess up the styles of your site.

This can be avoided by not using IDs within the selectors as they are directly specific.

For instance, we have these long selectors:
	
	#header #intro h1.big a {... }

	#header #intro h1.big a.normal {... }

We can compress it up to two or three levels deep:

	.big a {... }

	.big .normal {... }


	

# css tips,tricks and guides (useful links)

### Tricks
+ for css tricks, text-trim, multiline-trim..and much more  [30secondsofcode.org](https://www.30secondsofcode.org/css/p/1)

+ for css button examples [getcssscan.com/css-buttons-examples](https://getcssscan.com/)

+ for css box-shadow examples [getcssscan.com/css-box-shadow-examples](https://getcssscan.com/css-box-shadow-examples)

+ A collection of popular layouts and patterns made with CSS [csslayout.io](https://csslayout.io/) 

+ css-code-examples [freefrontend.com](https://freefrontend.com/css-code-examples/) 
### Guides
+ for css Guides [css-tricks.com](https://css-tricks.com/guides/)

# The trick to viewport units on mobile
+ Artical [Link](https://css-tricks.com/the-trick-to-viewport-units-on-mobile/) 

```css
.my-element {
  height: 100vh; /* Fallback for browsers that do not support Custom Properties */
  height: calc(var(--vh, 1vh) * 100);
}
```
```js
// First we get the viewport height and we multiple it by 1% to get a value for a vh unit
let vh = window.innerHeight * 0.01;
// Then we set the value in the --vh custom property to the root of the document
document.documentElement.style.setProperty('--vh', `${vh}px`);
```
