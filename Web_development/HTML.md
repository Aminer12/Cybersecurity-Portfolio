tag formatting 
\<tag>content\</tag>
- start tag \<tag>
- placeholder/end tag -> \</tag
Void elements cannot have context and only have an opening tag 

```
In this book, you learn that HTML is <em>awsome</em>. 

This tag is the emphasis (em),which always italizes the world within the tag -- in this case (awsome). 
```

tags can be modified using attributes, often formatted as shown
```
<tag attribute="value"> 
or 
<element attribute="value"></element>

example of creating a link using this format 

Be sure to stop by my <a href="https://paulmcfedries.com/">home page</a>. 
<a> -tag
attribute = link 

```

#### Structures of a Web Page 

HTML files always lead with this tag 
```
<!DOCTYPE html> -> know as the doctype declaration

<html lang="en"> -> this tells web browser that its dealing with an html file and the language is english 

</html> -> this line should end all of the html files 
```

Basic page setup
```
<!DOCTYPE html>
<html lang="en">
	<head>
		<meta charset="utf-8"> 
	</head>
	<body>
	</body>
</html
```
\<meta charset="utf-8"> -> tells the web browser the page uses this character set which contains most characters used

**Best Practice** -> use the structural tags show above only once on each html page 

Title
```
<title> Title name </title> -> should be placed in between the header
```
Titles should make sense, use less than 60 characters 

**Body Text Tips** 
- Whitespace is ignored | this includes tabs 
- \<br> can be used as a line break
- \<p> \</p> is used for paragraph tags

#### Basic Text Tags
\<i> \</i> tags for alternative text, also turning the text within italic 
\<strong> \</strong> tag used to bold text | \<b> \</b> does the same 

Nesting of tags || nested elements should be placed two spaces further to the right of the element they are nested in. 
```
<b> This line has a <em> nested tag </em> of emphasis and bold.</b>
```

Headers -> a total of six header are possible following the h1 - h6 format \<h1> \</h1>
```
<h1> A level 1 header </h>
```

Quotations -> gives the quote its own paragraph and is indented toward the left margin
```
<blockquote> 
	Place quote here 
</blockquote>
```

links 
```
<a href="address" target="_blank"> linked text </a>

href -> hypertext reference 
The text that is both the link and explains the link 

target="_blank" -> cause the link to open in a new tab
```

Local web page in same directory as homepage of website -> address is simple the filename 

Local web page in different directory -> address is /directory_name/file_name 

remote website -> full URL of the page 

Image
``` html
<img scr ="image location" alt=" image text descriptor" > -> the alt only shows if the image does not load 
```

link -> element is used to link to external resources like stylesheets and site icons. 
``` html
<link rel="stylesheet" href="./style.css" />

link should be placed inside the head element 

rel -> used to specify the relationship between the linked resource and the HTML document 

href -> used to specify the location of the URL for the external resource 

< link rel="preconnect" href="https://fonts.googleapis.com" />

preconnect -> increased load time by early connecting 
```

HTML Boilerplate -> basic structure and essential elements every HTML document needs 
```html
<!DOCTYPE html>
<html lang="en">
  <head> -> meta data goes here 
    <meta charset="UTF-8" />
    <meta
       name="viewport"
       content="width=device-width, initial-scale=1.0" />
    <title>freeCodeCamp</title>
    <link rel="stylesheet" href="./styles.css" />
  </head>
  <body> -> headings, paragraphs, images etc go here 
  </body>
</html>
```
Basic boilerplate
```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta
       name="viewport"
       content="width=device-width, initial-scale=1.0" />
    <title></title>
    <link/>
  </head>
  <body> 
  </body>
</html>
```

UTF-8 Character Encoding -> a method of storing characters as data widely used across the web. 

Comments in code 
```html
<!-- comment are are ignored when the program runs -->

format <!-- comment --> 
```

main -> element used to represent the main content of the body of an HTML document || only one per page || can effect the Search Engine Optimization SEO accessibility 
```html
```html
<main>
  <h1>Most important content of the document</h1>
  <p>Some more important content...</p>
</main>
```

Section -> element used to define sections in a document - such as chapters, headers, footers || its semantic element that helps with SEO and accessibility 
``` html
<section> content </section>
```

unordered list (ul) element | li element -> used to create a list item in an ordered or unordered list || ol -> ordered list 
```html
<ul> or <ol>
  <li> content </li>
</ul> or </ol>
```

figure -> element represents self-contained content and will allow you to associate an image with a caption || figcaption -> element is used to add a caption to describe the image contained 
```html
<figure>
	<img>
	<figcaption> A caption of image</figcaption>
	
</figure>
```

footer -> element used to define a footer for a document or section. A footer typically contains information about the author of the document, copyright data, links to terms of use, contact information, and more. 
```html
<footer>

</footer>
```

div -> elem