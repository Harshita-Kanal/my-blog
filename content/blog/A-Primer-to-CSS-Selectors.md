---
title: A Primer to CSS Selectors
og_image: start-blog-gatsby-twitter.png
---
## CSS Selectors
CSS or Cascading Style Sheets is used to style HTML elements.
Element styling typically involves: <br/>
* Selecting the element
* Applying the specific styles.

A Typical example of an HTML element could be: <br/>

```html
<h1> hello </h1>
```
Here the h1 is an HTML element. 
Now we need to select this specific element in our CSS file, this would be done by using 
a selector.

## A simple selector
The simplest CSS selector could be, an Element selector.<br/> 
```css
h1{
color: red;
}
```
The above is an example of an element selector, it would do exactly what its name says, select all specified elements on the page and apply the said styles,in this case it would select all h1 elements and make it red.

## Let's get more specific!
Element selectors are good, but we may not need to apply the same styles to all instances of the selected element on the page,
i.e. All h1 elements may not be red! <br/>
There could be situations when only some h1 elements need to be red, here we use more specific Selectors.

## Class selectors
A class selector looks like this: <br/>
```css
.myColoredTag{
color: red;
}
```
We apply a class to an HTML element as: <br/>
```html
<h1 class="myColoredTag"> hello </h1>
```
In this case, the same set of styles would be applied to all the elements having the same class name.
This could be considered as one of the most used tags, as it can later help you to use various CSS frameworks, example: bootstrap and apply framework specific styles.

## ID Selectors
An ID selector looks like this: <br/>

```css
#myColoredTag{
color: red;
}
```
We can apply an ID to an HTML element as: <br/>

```html
<h1 id="myColoredTag"> hello </h1>

```
Each page can have only one element with same id, an id is thus unique.

