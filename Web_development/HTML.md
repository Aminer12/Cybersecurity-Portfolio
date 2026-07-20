
# HTML Basics
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

div -> element is used as a container to group other elements || often used to group HTML elements that will share a set of CSS styles. 
``` html
<div>
	<p> Example paragraph element</p>
</dev>
```

id -> attribute adds a unique identifier to an HTML element || these id can be referenced within Javascript and CSS code. || for this purpose they should only be used once and remain unique || They cannot have spaces 
```html
<h1> id="title"> header title</h1>
```

class -> attribute values does not need to be unique and can contain spaces || Add multiple classes by providing spaces between them || best used if you want to apply a set of styles to many classes 
```
<div class="box red-box"></div>
```

HTML Entities (character reference) is a set of characters used to represent a reserved character in HTML 
```
say to wanted to type out a sentence using html tag without them being called, you would used HTML Entities 

<p> learning is fun </p> -> wanted to type this exact senetence without applying the paragraph element

would translate into 

&lt;p&gt; learning is fun &lt;p&gt;

named character references start with a & and end with a ; 

decimal numeric reference starts with a &# followed by one or more decimal points, followed by a semicolon

&#174; -> registered trademark symbol

hexadecimal numeric reference -> &#x followed by one or more ASCII hex digits and ends with a semicolon
&#x20AC; -> euro symbol
```

script -> element is used to embed executable code. || like JavaScript code || best practice is to link to a JavaScript file that contains the executable code 
```
<script src="path-to-javascript-file.js"></script>
```

Button -> element is used to create clickable buttons on a webpage
```html
<button> text </button>
```

#### Role of the Meta Description and its affect on SEO
```html
<meta name="desciption" content="content" />
name="descritpion" -> ensure the web browser understand the content 
```

#### Open Graph Tags and SEO
Open graph protocol enables you to control how your website's content appears across various social media platforms like Facebook, Linkedin.
```html
These tags are placed in the header of a file 

First important OG property is title 
<meta content="freeCodeCamp.org" property="og:title" />
content -> information is what will be displayed on the social media platform

Next important is the type -> used to represent the type of content being shared on social media like articles, website, videos, or music 

<meta property="og:type" content="website" />

og Images 
<meta content=" Image location url" property="og:image" />

og URL 
<meta property="og:url" content="full url" />
```

#### HTML Audio and Video Elements 
audio -> element supports popular audio formats like mp3, wav, and ogg. 
video -> element supports mp4, ogg, and webm formats 
```html
<audio src="location of file" 
controls
loop
muted> 

</audio>
controls -> attribute makes the audio visible on the webpage.
```
control -> is a Boolean attribute that can be added to an element to enable built-in-playback controls
loop -> attribute is a boolean that makes the audio replay continuously 
muted-> boolean attribute will start the audio in a muted state

Audio with multiple sources
```html
<audio controls>
  <source src="audio.ogg" type="audio/ogg" />
  <source src="audio.wav" type="audio/wav" />
  <source src="audio.mp3" type="audio/mpeg" />
</audio>
```
The source attribute will cause the browser to select the first source, if it is unable to play the audio it will move down to the second source. 

All the attributes shown above also work with videos 
```html
<video
  src="source of video file"
  loop
  controls
  muted
  width="400"
  poster="source of poster image while video is loading"
></video>
```
width -> attribute is used to effect the start size of the video
poster (unique to video) -> attribute displays a poster while the video loads 

#### Optimize Media Assets
size 
	Like about the resolution and the corresponding file size 
File format
	optimized web formats - WEBP or AVIF 
Compression 
	running compression algorithms on images to reduce file size (Tools like pngcrush)
	Understanding the difference between lossless compression (losing no image data) and lossy (which does permanently lose image data)

pixabay and unsplash for free open domain pictures 

What are SVG 
PNG and JPG are classified as raster formats | pixel based, with the data tracking the color value in each pixel  || downside in upscaling 

SVG - scalable vector graphic | tracking data based on paths and equations to plot points, lines, and curves. || storing data in XML meaning you can use them in raw HTML code with the 

svg -> element for svg images 
```html
<svg width="100" height="100" viewBox="0 0 100 100" xmlns="http://www.w3.org/2000/svg">
  <circle cx="50" cy="50" r="45" stroke="black" stroke-width="4" fill="yellow" />
  <circle cx="35" cy="40" r="5" fill="black" />
  <circle cx="65" cy="40" r="5" fill="black" />
  <path d="M35 65 Q50 80 65 65" stroke="black" stroke-width="4" fill="transparent" />
</svg>

The output of this code is a smiley face 
viewBox -> first two digits represent the start position (0 0 -> top left) next two represent the viewbox width and height
```
Font Awesome a good source of SVG images 

#### Iframe Elements 

replacement elements -> element whose content is determined by an external resource rather than by CSS itself. || With replacement elements, you can control the position, or layout of an element -- but CSS cannot directly modify the content of that element 

iframe (inline frame) -> element which embeds an external site on your webpage || often used for embedded Youtube videos or maps || it embeds other HTML content directly within the HTML page
```html
<iframe 
	width="400" 
	height="200" 
	src="https://www.youtube.com/embed/u43gJJrVa1I?si=BoDW_puFsy8OEr_Z" -> need the /embed/ to get a normal youtube video to work on a website in HTML 
	title="Professional Cloud Architect Certification Course – Pass the Exam! (YouTube video)" 
	allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" 
	referrerpolicy="strict-origin-when-cross-origin" 
	allowfullscreen></iframe>
	
allow -> determines what an iframe can and cannot do || if we added clipboard-write it would allow the embedded page to write items to your clipboard. || items in an allowlist can be seperated by semicolons or spaces, and both can be used together. 
	accelerometer -> use motion sensors so ti can detect things like device tilting and rotation 
	autoplay -> lets the video start playing automatically
	clipboard-write -> write data to the user's clipboard
	encrypted-media -> allow the use of encrypted media extensions to protect the video 
	gyroscope -> grant access to the devices motion and orientation sensors
	web-share -> sharing the content through the device's native share dialogs
	
	
referrerpolicy -> rule that determines how much detail you share when your page connects to another page. 
	-> the policy show above shares the full address on the same site, only the site name on other sites, and nothing on insecure sites
```
Other replaced elements like video and embed
If you want to embed direct HTML within the iframe element you have to use the srdoc attribute instead of src. 

#### Working with Links
target -> attribute tells the browser where to open the URL for the anchor element || four important values this attribute can have 
	\_self -> which is the default value. This opens the link in the current browsing context. 
	\_blank -> opens the link in a new browsing context. Typically this will open a new tab
	\_parent -> opens the link in the parent of the current context || for example when clicking on a youtube video this value would play it from your site instead of opening up youtube.
	\_top -> opens the link in the top-most browsing context || will always open in the full browser tab/window, even for nested embedded frames
	\_unfencedTop -> used for experimental FencedFrame API


##### Absolute and Relative Path

absolute path -> complete link to a resource starting from the root directory ||when linking a resource on your local machine, use an absolute path. 

Absolute URL -> complete address used to access a resource || including the protocol, file, and domain name || file:// used to connect local assets 

relative path -> specifies the location of a file relative to the directory of the current file. || not including the protocol or the domain name

**Rules**
- Use absolute paths when you want to reference a resource from a fixed location, such as from the root of your site or a known directory on your local machine.
- Use absolute URL when linking to a resource hosted on an external website.
- Use relative paths when linking to resources within the same website.
- Use relative paths if you want to keep your code cleaner and easier to maintain during development.
- Use relative paths during local testing to ensure links work without an internet connection.

**Different link states / Importance** 
First (default state) -> :link -> represents a link which the user has not visited 

second state -> :visited -> applies when a user has already visited the page being linked to. || turning the link purple by default 

third state -> :hover -> applies when a user is hovering their curser over a link || often changing the color of the link 

fourth state -> :focus -> applies when we focus on a link || changing colors when someone tabs through a page 

fifth state -> :active -> applies to links that are being activated by the user. 

When you use these states to style your links, there is a specific order you need to write your CSS in -> link, visited, hover, focus, active

# Semantic HTML

The semantic meaning of an element refers to what special information that element conveys 

font (not recommended) -> a deprecated /outdated element used to set the font size and color of the text. 
center (not recommended) -> center font to the middle of the screen
big (not recommended) -> makes the font one size large than the font around it 
```html
<font size="number" color="blue"> text here </font>
<center> text </center>
<big> text </big> 
```

i (idiomatic text element) -> used to highlighting alternative voice or mood, idiomatic terms from another language, technical terms, and thoughts
```
< i lang="fr"> text in italic</i>
```
While em should be used to provide more context or special emphasis to a particular part of the text. 

If you need to display the text in italics, but the text doesn't have a special purpose, style, or meaning in the paragraph, you should use CSS instead. 

##### Strong vs Bring Attention To Elements 

b (Bring Attention To) -> used to highlight keywords in summaries , product names in reviews || displaying the text in boldface 
```html
<b> text </b> 
```

strong should be used to emphasize the importance of the text || crucial or urgent text 
```html
<strong> text </strong> 
```

##### Description List 
-> presenting terms and definitions in an organized and easy to read format, like a glossary, or dictionary 
```html
<dl>
	<dt>HTML</dt>
	<dd>HyperText Markup Language</dd>
</dl>
```
dl (description list) -> contains the whole list 
dt (description term) -> for each term
dd(description detail) -> providing description or details associated with the term 

##### Block and Inline Quotes 

blockquote -> element should be used for representing a section quoted from another source || mainly for extended quotes || the cite attribute can take an address URL if you have one 
```html
<blockquote cite="location"> quoted text </blockquote>
```
Quotation marks for the quote must be written within the text block, html does not do it on its own. 
cite -> element (different than the attribute) used outside the blockquote -- use to mark up the title or referenced creative work like a book, article, song, film, website, or research paper. 
```html
<cite> text </cite>
```

q (inline quotation element) -> used to have inline quotations || most modern browser will auto put quotation marks
```html
<q cite="source"> text </q>
```

##### Display Abbreviations 
abbr (abbreviation) -> element used to specify abbreviations
```html
<abbr title="HyperText Markup Language">HTML</abbr>
Title -> attribute used to explain the meaning, when the word is hovered over it will display the title 
```

##### Display Addresses 

address -> element can be used for business pages, author pages, personal sites, and more 
```html
<address>
  <h2>Company Name</h2>
  <p>
    1234 Elm Street<br />
    Springfield, IL 62701<br />
    United States
  </p>
  <p>Phone: <a href="tel:+15555555555">+1 (555) 555-5555</a></p>
  <p>Email: <a href="mailto:contact@company.com">contact@company.com</a></p>
</address>

br - break element used to show division between the information
href="tel:+ -> creates a clickable link to initiate a phone call on certain devices that support it 
href="mailto:" -> links are used in HTML documents to allow users to open a new email within their preferred email client || can be percieved as spam mail
```

##### Display Time and Dates 

time -> element used to represent a specific moment in time 
```html
<time datetime="20:20">20:00</time>

datetime -> attribute used to translate dates and times into a machine-readable format || must be a valid year, month, time, local date, global date, or duration string || following the ISO 8601 format 
```

##### Mathematical Equations and Chemical Formulas || Computer Code || U,S and Ruby elements 

superscript -> element is used to display a piece of text as a superscript || a symbol or letter printed above the normal line of text || only used for typographical reasons 
```html
<p>2<sup>2</sup> (2 squared) is 4. </p>
```

subscript -> element displays a lowered baseline using smaller text || used for chemical formulas, footnotes, and variable subscripts 
```html
<p>CO<sub>2</sub></p>
```

inline code -> element is used to represent short snippets of code inside text || default style is monospaced font || designed to represent a single line of code
```html
<code> color:blue;</code>
```

Multiple lines of code need the preformatted text element || be mindful of spaces as pre will display exactly what you have written
```html
<pre>
	<code>
		coded text
	</code>
</pre>
```

unarticulated annotation element (u) -> used to represent inline text that has non-textual annotations applied || default style is black underline 
```html
<u> text </u>
```

strikethrough (s) -> element should be used to represent when text is no longer accurate or relevant || never used to show changes to a document
```html
<s> text </s>
```

ruby -> element represents small text shown above or belove the main text || often used to show pronunciation of East Asian Characters 
```html
<ruby> 明日 <rp>(</rp><rt>Ashita</rt><rp>)</rp> </ruby>

The `rp` element, or ruby fallback parenthesis element, is used as a fallback for browsers lacking support for displaying ruby annotations.

The `rt` element, or ruby text element, is used to indicate text for the ruby annotation. This text is usually used for pronunciation, or translation details in East Asian typography.
```

# Forms and Tables

form -> element used to gather user information, such as name and email address
```html
<form action="URL
```