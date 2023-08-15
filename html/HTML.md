# Markup Validation

```
<span>
    <div>
        ❌this is not allowed
    </div>
</span>
```

+  Element __div__ not allowed as child of element __span__ in this context.

+ You can check your Markup on [validator.w3.org](https://validator.w3.org/)

# IMG Tag

```
❌ <img src="example/source" >

✅ <img src="example/source" alt="message">
```
+ Always define __img__ tag with __alt__ message.

# onClick Events

```
❌ <div onclick="myFunction()">Click me</div> 
❌ <svg onclick="myFunction()">...</svg> 
❌ <img onclick="myFunction() src="example/source" /> 
❌ <span onclick="myFunction()">Click me</span> 

✅ <button onclick="myFunction()">Click me</button>

✅ <button onclick="myFunction()">
        <img src="example/source" alt"message" />
    </button>
```
+ Always bind click events to button tags only. Because on desktop user can use tab-key to focus on a clickable elements.

# SEO Meta Tags 
### Meta Tags

    <meta name="description" content="Some des.."/>
    
    <meta name=”robots” content=”noindex, nofollow”>

+ learn about Meta Tags [click here](https://clutch.co/seo-firms/resources/meta-tags-that-improve-seo)     

### OP Meta Tags
```
<meta property="og:title" content="example title" />

<meta property="og:description" content="A small description" />

<meta property="og:image" content="https://example.com/image.png" />
```
+ learn more about [open-graph meta tags](https://ahrefs.com/blog/open-graph-meta-tags/)