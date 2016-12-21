# fsBanner

## What it is
A simple jQuery plugin that allows you to create a stacked banner based on a set of divs. 

<img src="https://raw.github.com/fiote/fsbanner/master/images/giphy.gif" width="100%" />

## Is something else required?
Yes. You'll need Jquery 2.1+.

Ok, you probably wont need that exactly version, but since I created this using it, that's what I can recomend.

Examples
--------
Want to see fsBanner in action? Check http://murilo.codware.com/fsbanner/example.html :)

## Usage
Download the package and reference the JavaScript and CSS files manually:

```html
<!-- Jquery 2.1.4 from CDN, or from wherever you want to load it -->
<script type="text/javascript" src='https://code.jquery.com/jquery-2.1.4.min.js'></script>

<!-- fsBanner (from wherever you copied/pasted it) -->
<link rel="stylesheet" type="text/css" href="fsbanner/fsbanner.css">
<script type="text/javascript" src="fsbanner/fsbanner.js"></script>
```

Html 
--------

fsBanner expects a set of divs that will be used to create the stacked banner. Your html code should look something like this:

```html
<!--list of banners to be stacked -->
<div class='fsbanner'>
	<!-- first banner -->
	<div style='background-image:url(images/black.jpg)' /><span class='name'>BLACK</span></div>
	<!-- second banner -->
	<div style='background-image:url(images/brown.jpg)' /><span class='name'>BROWN</span></div>
</div>
```
You may add as many banners as you want. The .name span can be omited, and others spans can be added. Check the options and the examples to know more about it.

CSS
--------
faBanner already come with some css set to make it work, but you'll probably want to need to set the div.fsbanner rules to fit your needs.

Javascript
--------
You can call it simply by using (options are optional, duh):

```javascript
// the div must have the fsbanner class for styling, 
// but you can use any selector that would match the div here.
$('.fsbanner').fsBanner(options);
```
Options
--------
Of course, you can set up options!

| Option        | Values        | Default | Description |
| :-----        | :----         | ------- | :-- |
| showName      | true / false  | true    | If set to true, the .name element will be show at the bottom-left of the banner. |
| trigger       | click / mouse | click   | If set to 'click', clicking a banner will expand it (while shrinking the others) and clicking it again will reset the banners to the initial widths. If set to 'mouse', moving the mouse over a banner will expand it (and shrink the others) and moving it out of the banners container will reset the widths.
| toUpdate      | object        | {}      | Whenever you expand a banner, the script will get the info from its spans on the html. You can use this option to update other elements using those values. This hash should composed of pairs of -banner-span-classname- and -selector-that-will-receive-its-html-. Checking the example should clear any doubts on this.  |
| whenEmpty     | object        | {}      | When there is no banner expanded (on load, or after a width reset), there is no info to show on the selectors defined on the toUpdate option. You can use this hash to set default values for them. This hash should be composed of pairs of -banner-span-classname- and the -default-html-for-it-. This option only works if the spans are defined on the toUpdate option. Check the example for clarifications. If you want to HIDE and -to-update-element- when there is no banner select, just don't include its -span-classname- on this hash, since setting the -default-html- to an empty string will simply update its html with that, an empty string. |
| hideParent    | selector      | null    | If set, the whenEmpty option will be ignored. When there is no banner and hideParent is set, the script will hide the element based on the selector passed. | 
| onChanged     | function      | null    | Whenever there is a change on the expanded banner (you just expanded one, or a width reset occured) this function will be fired. It receives 2 parameters: the expanded banner (if any) and the expanded-before-that banner (if any). Those parameters are jQuery $elements, so you may want to use $param[0] or $param.eq(0) if you really need to DOM element. |

