# HTML and CSS Fundamentals

HTML and CSS, together with JavaScript are the three pilars of modern web development. Together, they form a (almost) complete "tech stack" which is sufficient for building performant web applications which meet today's business requirements. This "stack" does have its shortcomings, but also strengths, and is a good place to start learning web development.

## This lesson will cover:
* HTML fundamentals
* CSS fundamentals
* In-line styling
* Importing CSS files
* Arranging elements

## HTML (Hypertext Markup Language) Fundamentals
HTML is one of the fundamental building blocks of the internet, being the tool which allows us to lay out web pages and structure content. The authorative reference for it is [w3schools](https://www.w3schools.com/html/default.asp)

### Commonly Used Elements
``` html
<!-- This tag does not have a closing tag, and indicates the type of the file -->
<!DOCTYPE html>

<!-- This is the uppermost element, or root, and tells machines reading it that it's HTML they're looking at -->
<html></html>

<!-- The head element contains meta data which helps search engines understand your website, adds the title you can see in the browser tab, imports scripts for analytics, is the place to import CSS, JavaScript, libraries and a number of other things -->
<head>
  <title>My awesome site! :)</title>
</head>

<!-- The majority of content of the page goes in the body element -->
<body></body>

<!-- The footer sits at the bottom of the page and usually has additional / ancilliary information about the business -->
<footer>Copyright 2019, Tuna Corporation</footer>

<!-- h1, h2, h3 are standardized headers for titles and subtitles you use throughout your web page -->
<h1>This is one title</h1>
<h2>This is a smaller title</h2>
<h3>This is an even smaller title</h3>

<!-- div(s) are the basic "box" component of HTML which is used for holding different elements and helps arrange them -->
<div>
  <h1 class="simple-style">This 'div' holds 1 element</h1>
</div>

<!-- Sometimes you need an image on your page! -->
<img style="width: 100%" src="https://tinyurl.com/y4ud8rjc" /> <!-- this is the shorthand syntax for closing a tag -->

<!-- the link element allows you to connect your site to different webpages using the href attribute (hypertext reference) -->
<a href="https://google.com">Take me to the googlez!</a>

<!-- Unordered list element holds bullet points (list items: <li>) -->
<ul>
  <li>banana</li>
  <li>peach</li>
  <li>cucmber</li>
</ul>

<!-- Ordered lists hold numbered list items -->
<ol>
  <li>I'm first!</li>
  <li>I'm second :(</li>
</ol>

<!-- This element is for making buttons which do something when you click on them, usually using JavaScript which is specified in the `onClick` attribute -->
<button onClick="alert('huzzah, you clicked me');"></button>

<!-- Tables hold data! -->
<table>
  <thead> <!-- table headings -->
    <th>Age</th> <!-- column header -->
    <th>Profession</th>
  </thead>
  <tr> <!-- table row -->
    <td>400</td> <!-- table data -->
    <td>Jedi</td>
  </tr>
  <tr>
    <td>35</td>
    <td>Ninja</td>
  </tr>
</table>

<!-- Used for importing CSS into HTML -->
<style>
  .simple-style {
    background-color: red;
    width: 200px;
  }
</style>
```

## CSS (Cascading Style Sheets) Fundamentals 
CSS is used for styling HTML documents, as well as more advanced things like creating [animations](https://codepen.io/donovanh/pen/KJdoh). The authorative reference for CSS is [w3schools](https://www.w3schools.com/css/default.asp).

### [Selectors](https://www.w3schools.com/cssref/css_selectors.asp) 
Selectors allow us to 'target' HTML elements to change their appearance on the web page. There are two main selectors we will be using very often, and more can be found in the reference link in the title of this section.

* The first selector is '.' which indicates we are targetting a class. For example, if we wanted to create a class which turns the color of the text red and makes the font size 16px, it would look like this:
``` css
.my-new-class {
  color: red; /** Colors (like background, color etc.) can also be a [hex code](https://www.color-hex.com/): #FFC0CB - or rgb code: rgb(255, 192, 203, 1) */
  font-size: 16px;
}
```

To use this class in a div we would do the following:
``` html
<div class="my-new-class">
  This text is red and its size is 16px!
</div>
```

* Similarly we can use the '#' selector which indicates we are targetting an id. The thing to keep in mind is that id(s) are unique, and should only be used on one element per page. For example:
``` css
#my-unique-selector {
  color: blue;
}
```

``` html
  <div id="my-unique-selector">
    I am the only element on the page with this id! And my text is blue :)
  </div>
```

### [Properties](https://www.w3schools.com/cssref/default.asp)
```css
.class-example {
  /** Determines which way an element "floats" */
  float: none|left|right|initial|inherit;

  /** Size of the text - it's preferrable to use px */
  font-size: 1em|1rem|1px;

  /** Adds 'padding' inside of the element */
  padding-top: 0px;
  padding-right: 10px;
  padding-bottom: 10px;
  padding-left: 10px;
  padding: 10px 10px 10px 10px;

  /** Adds a margin on the outside of the element */
  margin: 10px 10px 10px 10px;

  /** Aligns the text or element */
  text-align: none|center|left|right;
  
  /** Color of the background, or a background image */
  background: lightblue url("img_tree.gif") no-repeat fixed center; 
}

```
## In-line Styling and <style> Element
Although this is typically not advised, the HTML attribute `style` allows us to style elements by addings CSS directly to the HTML element like so:
```html
<div style="font-size: 100px, color: red">
  I'm size 100px and red
</div>
```

We can also add CSS to a file using the `<style>` tag:
```html
<style>
  .class-example {
    background: blue;
    padding: 40px;
    margin: auto;
  }
</style>
```

## Importing CSS Files
To keep files organized and clean it's advisable to keep CSS in one or more separate files. To do this, create a file, for example `styles.css` and put it into the same directory as your website. Then use the `<link>` attribute.
```html
<head>
  <link href="styles.css" rel="stylesheet" type="text/css">
</head>
```

## Flexbox, Float and Grid
There are many ways to arrange elements on a web page. The one I resort to the most is using `float` properties with `div`s. That's probably not the best way to do it so I'll show you how to use the [**flexbox** layout](https://css-tricks.com/snippets/css/a-guide-to-flexbox/).

```html
<div class="parent-container">
  <div class="item"></div>
  <div class="item"></div>
  <div class="item"></div>
</div>

<style>
  .parent-container {
    display: flex;
    flex-direction: row|column;
  }

  .item {
    width: 33%;
  }
</style>
```

## Frameworks
Most modern front-end work is done using [React.js](https://reactjs.org/) but we most likely won't end up having time to get into it. React.js uses a special syntax called JSX which mixes JavaScript and HTML and is based around building "components" which are reusable units of code so that you don't have to repeat yourself.

Additionally, there are CSS preprocessors which give us the ability to do more with our CSS, namely [LESS](http://lesscss.org/) and [SASS](https://sass-lang.com/). They give us more capabilities which are typical found in a programming language such as doing logic, storing values etc.

Lastly, there are some low level HTML frameworks such as [Bootstrap](https://getbootstrap.com/) and [Foundation](https://foundation.zurb.com/) which are meant to give you access to components which are often used in building web pages such as navigation bars, hero sections, buttons, drop-down menus etc. These are very useful but it's important to understand the basics of HTML so that when you need to 'look under the hood' or do some custom work, you know how.
