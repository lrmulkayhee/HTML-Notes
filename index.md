### HTML Elements

elements
: the building blocks of html. includes a `start tag`, some content, and an `end tag`

ex.

```html
<h1>insert heading here</h1>
```

## types of tags

heading tag
: used for titles and headings of various portions of your page. each heading `<h1>` through `<h6>` is of a different size. content is surrounded by `<hX>` and `</hX>` where X is a number.

```html
<h1>insert heading here</h1>
```

paragraph tag
: used for the body or main informational portion of your page. There is no numbering for paragraphs. content is surrounded by `<p>` and `</p>`.

```html
<p>insert paragraph here</p>
```

strong tag
: used to make portions of your page bold text. content is surrounded by `<strong>` and `</strong>`.

```html
<strong> insert bold text here </strong>
```

italics tag
: used to make portions of your page italic text. content is surrounded by `<em>` and `</em>`.

```html
<em> insert italic text here </em>
```

break tag
: used to insert a break in your page. This type of tag **DOES NOT** need a closing tag. often seen as `<br />`.

```html
<p>hello</p>
<br />
<p>world</p>
```

horizon tag
: used to insert a horizontal line in your page. This type of tag **DOES NOT** need a closing tag. often seen as `<hr />`.

```html
<p>hello</p>
<hr />
<p>world</p>
```

list tag
: used to create a list in conjunction with `<ul>` and `</ul>` for an unnumbered list and `<ol>` and `</ol>` for a numbered list. each bullet/ number point is surrounded by `<li>` and `</li>` respectively.

```html
<ul>
  <li>hello</li>
  <li>world</li>
</ul>
```

or

```html
<ol>
  <li>hello</li>
  <li>world</li>
</ol>
```

### HTML Attributes

attributes
: a piece of language used to adjust the behavior or display of an element. attributes can change an elements size, shape, color, and functionality.

## types of attributes

link tag
: used to insert a link in your page. content is surrounded by `<a href= insert a url here>` and `</a>`. can include `target="_blank"` to link tag to open link in an empty window.

```html
<a href="https://github.com" target="_blank"> Github </a>
```

image tag
: used to insert an image in your page. content is denoted by `<img src= insert a url here>`. There is no end tag. can include alternative text in image tag for acessibility.

```html
<img src="https://miro.medium.com/max/1254.png" alt="women coding" />
```

### HTML documents

- a html document is denoted by `.html` after the file name

## portions of a document

head
: the head of a document contains all of the meta tags for the document, the title of the webpage, as well as the style tag. contained between `<head>` and `</head>`.

body
: the body of teh document is the actual written portion of the document. this includes the headers, paragraphs and images of the webpage as well as and behavioral modifiers like javascript. contained between `<body>` and `</body>`.

### HTML classes

classes
: classes are groupings for tags and are used to add attributes to a tag (ex. <li)>)

```html
<ul>
  <li class="greeting">hello</li>
  <li class="planet">world</li>
</ul>
```

### HTML containers

- containers are used to simplify rules and make the code cleaner

division tag
: can only be used for block elements (ex. paragraphs, headings, images, and links). gives classes to text without adding default styling options. contained between `<div>` and `</div>`. very important in CSS styling.

```html
<div id="paragraphs">
  <p>first paragraph</p>
  <p>second paragraph</p>
</div>
```

span
: can only be used for inline elements (ex. smaller portions of text). gives classes to text without adding default styling options. contained between `<span>` and `</span>`. very important in CSS styling.

```html
<span id="hello">
  <p>hello</p>
</span>
```

```

```
