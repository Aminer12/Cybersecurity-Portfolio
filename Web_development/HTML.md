tag formatting 
\<tag>content\</tag>
- start tag \<tag>
- placeholder/end tag -> \</tag>

```
In this book, you learn that HTML is <em>awsome</em>. 

This tag is the emphasis (em),which always italizes the world within the tag -- in this case (awsome). 
```

tags can be modified using attributes, often formatted as shown
```
<tag attribute="value"> 

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
- \<p> \<\p> is used for paragraph tags

#### Basic Text Tags
