# HTML and CSS

## BEST Practices

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Title</title>
  <link rel="stylesheet" href="./style.css">
  <script src="./script.js" defer></script>
  <!-- Google Font: XXX Regular(400), Regular(400) italic, Bold(700) -->
  <!-- website thumbnail meta properties: -->
</head>
<body>

<a href="https://www.theodinproject.com" target="_blank">click me</a>
<img src="./img/dog.jpg" alt="" width="100" height="100">
<!-- alt should be blank alt="" for any image that is purely aesthetic -->
<!-- link images should use alt="link to youtube channel" -->
    
  <header class="container">
    <div class="wrap">
      <div>More</div>
      <div>Sign Up</div>
      <div>Login</div>
    </div>
  </header>
    
  <section class="hero container">
    <div class="wrap">
       <h1>Welcome!</h1>   
       <p>Learn to cook here</p>
    </div>
  </section>

  <nav class="container">
    <div class="wrap">
      <div>Recipes</div>
      <h1>How To's</h1>
      <div>Equipment</div>
    </div>
  </nav>

  <main class="container">
    <div class="wrap">
    </div>
  </main>

  <section class="even-more container">
    <div class="wrap">
    </div>
  </section>
  
  <footer>
    <p>Copyright © <script>document.write(new Date().getFullYear())</script> parktart</p>
    <a href="https://github.com/parktart/missing-number" target="_blank">
      <img src="./github-white.svg" alt="Link to GitHub repo" width="28" height="28">
    </a>
  </footer>

</body>
</html>
```

NOTE: use an HTML Markup Validator for every html file you code

```javascript
'use strict';
```

```css
*, *::before, *::after {
  box-sizing: border-box;  /* Alternative Box Model */
}

* {
  margin: 0;
  padding: 0;
  font: inherit; /* wipe all User Agent fonts, sizes, and weights */
  color: inherit;
  /* background-color: inherit; */
}

html {
  min-height: 100vh; /* body fills the viewport */
  min-height: fill-available;
  min-height: -webkit-fill-available;
  display: flex;     /* body fills the viewport */
}

body {
  font-family: 'Arial', sans-serif;
  font-size: 1.125rem;  /* 18px */
  /* color: rgb(42, 43, 42); */
  color: white;
  background-color: black;
  background-image: linear-gradient(black, rgb(42, 43, 42));
  flex: 1; /* body fills the viewport */
  display: flex;
  flex-direction: column;
}

.container {
  /* border: 2px solid blue; */
}

.wrap {
  /* border: 2px solid red; */
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 16px;
}

header.container {
  background-color: lightblue;
}

header .wrap {
  padding-top: 20px;
  padding-bottom: 20px;
  /* display: flex; */
  /* justify-content: space-between; */
  /* align-items: center; */
}

h1 {
  margin-top: 5vh;
  font-size: 32px;
  font-weight: bold;
}

main .wrap > * {
  margin-bottom: 30px;
}

img, picture, svg, video {
  display: block; /* remove the small whitespace that renders under each */
  max-width: 100%; /* allow to shrink with its container when forced */
  height: auto;
}

ul, ol {
    list-style-type: none;
}

a {
  text-decoration: none;
}

a:hover {
  opacity: 0.7;
}

button {
  background-color: black;
  padding: 6px 12px;
  border-radius: 12px;
  box-shadow: 0px 0px 2px 1px lightgreen;
  opacity: 0.8;
  font-weight: bold;
}

button:hover {
  opacity: 1;
  transform: scale(1.05);
}

button:active {
  opacity: 0.5;
}

a#reset {
  /* margin-top: auto; */
}

footer {
  display: flex;
  align-items: center;
  gap: 8px;
  margin-top: auto;
  margin-bottom: 20px;
}

footer a {
  transition: transform 0.3s ease-in-out;
}

footer a:hover {
  transform: rotate(360deg) scale(1.2);
}

@media screen and (max-width: 470px) {

  body {
    font-size: 1rem;  /* 16px */
  }

  h1 {
    font-size: 30px;
  }

}

/* 
CSS text-shadow HOW TO??
	text-shadow: 3px 3px 1px #bebebe;
   CSS box-shadow HOW TO??
	box-shadow: 6px 6px 5px 0 #bebebe;
note it is easy to visualize/manipulate both of these in DevTools!   

  CSS transition-timing-function HOW TO??
  CSS animation-timing-function HOW TO??
*/

/*
pixels = rem = User Agent Stylesheet (chrome)
10px = 0.625rem = h6, 10.72px
12px = 0.75rem
14px = 0.875rem = h5, 13.28px
16px = 1rem = base/body/h4
18px = 1.125rem = h3, 18.72px
20px = 1.25rem
22px = 1.375rem
24px = 1.5rem = h2
26px = 1.625rem
30px = 1.875rem
32px = 2rem = h1
*/
```



Limit **line length** to about **50-70 characters per line** for the best readability (and only **30-40 characters** for mobile device reading)

**Navigation elements** like "Read More", "Previous", "Next" and "Search" have a **minimum required size of 50x50px** according to modern web standards

Configure the Webpage **Thumbnail** (Open Graphic Object)



## HTML and CSS intro

HTML and CSS are two languages that work together to create everything that you see when you look at something on the internet

HTML is the raw data that a webpage is built out of (all the text, links, cards, lists, and buttons are HTML)

CSS is what adds style to those plain elements

HTML puts information on a webpage, and CSS positions that information, gives it color, and makes it look pretty

HTML and CSS are technically not *programming languages* but rather just *languages* as they are not used to program any logic

JavaScript is a programming language - used to make webpages do things - add interactivity to a webpage

these aren't the only 'languages' used to develop websites.. some of the most common web development languages include HTML, CSS, JavaScript, PHP, Python, Ruby, and SQL

choosing one of these as the main language used to develop a certain website depends entirely on the specific project and/or business goals of that project

HTML = hypertext markup language

CSS = cascading style sheets - used to improve the presentation of HTML elements

JavaScript = the most complex of the three as it is actually used to program logic - used to alter the behavior of the HTML and CSS elements on a website (for example a menu button)

NOTE: use an HTML Markup Validator for every html file you code!!! Things may parse without problems on a browser - but still have errors!



## HTML

almost all elements on an HTML page are just pieces of content wrapped in **opening** and **closing** HTML **tags**
**opening tags** mark the start of an HTML element
`<p>` is the opening tag for a paragraph
**closing tags** mark the end of an HTML element
`</p>` is the closing tag for a paragraph
note: some HTML elements do not have a closing tag (these do not wrap any content and so are known as empty elements)

using the correct tags for your content is obviously important - and it has a name - **semantic HTML**

all HTML documents have the same basic structure that needs to be in place before anything useful can be done (this basic structure is called the boilerplate)

### HTML Boilerplate

first off - we should ALWAYS name the HTML file that will contain the **homepage** of our website **index.html**
because web servers will by default look for an index.html file

LINE 1 = DOCTYPE declaration - the first line always declares which version of HTML the browser should use to render the document - the latest version of HTML is HTML5, and to specify HTML5 we use simply `<!DOCTYPE html>` \- note the doctype declarations for earlier versions of html were complicated and sucky

LINE 2 = the HTML element - also known as the root element because every other element in the document will be wrapped in it - it is included on every html document - for us it is simply..
`<html lang="en">`
`</html>`
note: the specification of english is mainly for improving accessibility for people who use screen readers

LINE 3 = Head element `<head>` is where you put important meta-information about your webpages like..
`<meta charset="UTF-8">` the charset meta element will set the charset encoding of the webpage - ensuring that special symbols and characters will display correctly
`<meta http-equiv="X-UA-Compatible" content="IE=edge">` another meta element - **not required** but is included in VSCode's html boilerplate
`<meta name="viewport" content="width=device-width, initial-scale=1.0">` another meta element - **not required** but is included in VSCode's html boilerplate
`<title>My First Webpage</title>` the Title element defines how an open tab of the page will be labeled in a browser - if not included, it will default to the file name

Body element `<body>` which will contain all the content you want to display

for example a header can be added with `<h1> </h1>` or a paragraph with `<p> </p>`

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8">
    <title>My First Webpage</title>
  </head>

  <body>
    <h1>Hello World!</h1>
  </body>
</html>
```



### HTML Elements

each comment is wrapped in `<!-- -->` and is only visible in the source code - note you should always leave spaces around your text or you could run into problems. should look like.. `<!-- This is a comment -->`

each heading is wrapped in `<h1> </h1>` with 1-6 levels.. with h1 being the highest level and h6 being the lowest (note h1 is always used for the heading of the overall page) also note this marks the text as more important than body text (for google, searches, etc)

each paragraph is wrapped in `<p> </p>`

**bold** text is wrapped in `<strong> </strong>` note this marks the text as important for screen readers and other technology - you can avoid this by instead using CSS to bold (later)

note **bold** text can alternatively be achieved with `<b> </b>` but this will not assign importance to that text - it is not good practice to use `<b> </b>`

*emphasized* text is wrapped in `<em> </em>` note this marks the text as important for screen readers and other technology - you can avoid this by instead using CSS to italicize (later)

note `emphasized` text can alternatively be achieved with `<i> </i>` but this will not assign importance to that text - it is not good practice to use `<i> </i>`

when you nest elements within other elements, for example..

```html
<html lang="en">
    
  <head>
    <title>the title</title>
  </head>

  <body>
    <p>the paragraph</p>
  </body>

</html>
```

we refer to the **head** element here as **the parent** of the **title** element (which is **the child**)

and the **body** element is **the parent** of the **paragraph** element

and the **head** and **body** are **siblings** (siblings are nested at the same level *and* have the same parent)

so **title** and **paragraph** are **not siblings** here

NOTE indenting is only really for human readability - it is recommended to **indent** any child element by **two spaces**



### Lists

**unordered** lists - for when order doesn't matter - each item gets a bullet point

```html
<ul>
    <li>Item 1</li>
    <li>Item 2</li>
    <li>Item 3</li>
</ul>
```

**ordered** lists - for when order does matter - like step by step instructions or a top 10 list - each item gets a number

```html
<ol>
    <li>Item 1</li>
    <li>Item 2</li>
    <li>Item 3</li>
</ol>
```

much more about lists: [LINK](https://learn.shayhowe.com/html-css/creating-lists/)



### Anchors

the **anchor** tag `<a>` is used to create links in HTML, for ex `<a>click me</a>`

along with an HTML attribute - an HTML **attribute** gives additional information to an element and always goes in the element's opening tag

an HTML **attribute** usually has two parts - a **name** and a **value** but not all attributes require a value

for our link element we add the attribute with name **href** (or hyperlink reference) and value (destination URL)

```html
<a href="https://www.theodinproject.com">click me</a>
```

note anchor tags `<a>` can be used to link to any kind of resource on the internet, not just HTML documents, like videos, pdf files, images, etc



**Absolute** links - are links to pages on other websites on the internet and look like `protocol://domain/path`

**Relative** links - are links to pages on your own website - they assume the domain name will be the same as the current page - so only include the **file path** to the other page *relative* to the current page - for example..

`<a href="example.html">click for example</a>` when `example.html` is in the same directory as the current page

`<a href="path/example.html">click for example</a>`

note: it is recommended to always start the path with `./` even if the file is in the current directory you would use..

`<a href="./example.html">click for example</a>`



## HTML charsets

`<charset="UTF-8">` the charset meta element will set the **charset encoding** of the webpage - setting the right HTML encoding will prevent the browser from failing to display special characters correctly

there are so many characters out there - from other languages to entire alphabets, mathematical symbols and more - all the available characters are grouped into specific sets (called charsets) - so by defining the HTML encoding you tell the browser which particular set to use

`ASCII` is the most basic charset - it was the first and was developed from telegraph code in the 1960s and contains 128 characters - 95 of which are printable and 33 are unprintable characters (aka control characters) which are the transparent symbols which denote the separation of words and paragraphs - the 95 printable characters are..
~ Lowercase Latin letters
~ Uppercase Latin letters
~ Punctuation symbols
~ Numbers from 0 to 9

note **Unicode** is now the industry standard for character encoding - published in the 1990s - there are a few charsets which classify as Unicode such as `UTF-8   UTF-16   UTF-32`

`UTF-8` stands for Unicode Transformation Format 8-bit and has been the most popular HTML charset since 2008 with more than 90% of all websites using `UTF-8` in 2019

this is because.. it supports many languages, is completely compatible with ASCII, is natively used by XML, and uses less space than other Unicode encodings

note: not all fonts have a full library of special characters - if your chosen font does not have a symbol you need, it may display a question mark in its place



## Fonts

### Basic Fonts

`font-family` defines what font an element uses

`sans-serif` is a *generic font family*

`"Times New Roman"` is a *font family name* and bc it has spaces in the name, we use "quotes"

we use a comma-separated list of values, rather than a single value, so that if a browser does not support the first font, it will use the next one, etc

ending with a *generic font family*

`font-family: "Times New Roman", sans-serif;`



In CSS there are five **generic font families**:

1. **Serif** fonts have a small stroke at the edges of each letter. They create a sense of formality and elegance.
2. **Sans-serif** fonts have clean lines (no small strokes attached). They create a modern and minimalistic look.
3. **Monospace** fonts - here all the letters have the same fixed width. They create a mechanical look. 
4. **Cursive** fonts imitate human handwriting.
5. **Fantasy** fonts are decorative/playful fonts.

Each *font family name* belongs to one of the *generic font families*

**Sans-serif fonts** are considered **easier to read** on computer screens

**Arial** is the most widely used font for both online and printed media - it is one of the safest web fonts

Best **Font Family Names** for each generic font family..

![font-fam-names](/home/parker/Dropbox/objects-photos-etc/font-family-names.png)



### Google Fonts

go to the [Google Fonts website](https://fonts.google.com/) 

search for a font

select the `+` icons next to the styles you want to include

copy the provided `<link>` element into your HTML's `<head>`

copy the provided CSS to your CSS file

best practice to grab *at least*..

`Regular(400)`

`Regular(400) italic`

`Bold(700)`



## Text

`text-align: left, center, right` will align text horizontally within an element



`font-weight` defines the boldness of text, rendered only if the font supports the specified weight

values in increments of 100 ranging from 100 to 900

`font-weight: normal` same as `font-weight: 400`

`font-weight: bold` same as `font-weight: 700`

`lighter` and `bolder` are values relative to the element's parent



`color` defines the font color

make sure you have sufficient color contrast

the W3C recommends the following contrast ratios for body text and image text:

- *Small text* (16pt regular or 12pt bold and below) should have a contrast ratio of at least 4.5:1 against its background
- *Large text* (18pt regular or 14pt bold and up) should have a contrast ratio of at least 3:1 against its background

also avoid coloring text in **red** or **green** because of color blindness



## rem em and qem + font-size

of all the units you can use in CSS, **rem** is the most reliable for `font-size`

using **rem** for `font-size` allows your text to scale appropriately when a user changes their preferred browser font size (in browser settings)

and so it is best to avoid using **px** for font sizing - this is not to say you should avoid using pixels altogether - pixels are useful for **padding**, **margin** (in certain cases), **border width**, **border radius**, and for **text** elements like **headers** that you don't want to grow even if the user changes their browser settings

the **html tag** is the **root** of any html document

modern browsers apply a **root font size** of `16px` meaning any unstyled body text will render as `16px`

note both developers and users can alter this behavior - developers can define a new `font-size` of the root (html) element with CSS - and users can use their browser settings to specify their preferred font size

when you hard code a pixel font size the text will always render in that size - regardless of the users settings - and we don't want that

note users can also **zoom in** for all web pages globally through their browser settings - in which case pixes aren't problematic - but we want both browser-setting and zoom to work

pixels are an **absolute length unit**

luckily CSS also has **relative length units** - like `%, em,` and `rem` - which reference other elements on the page

note percentages `%` actually behave the same as `em` with respect to font sizing

so let's compare just `em` vs `rem`



### em

`em` for `font-size` is calculated **relative** to the **element's parent** - so `1em` is equal to the parent's `font-size`

```css
.parent {
  font-size: 24px;
}

.child {
  font-size: 0.5em;  /* 0.5 * 24px = 12px */
}
```

note that using `em` for font sizing is problematic - if a child is too deeply nested, and its font size is in `em`, it creates a compounding effect and may be hard to track

```css
.parent {
  font-size: 24px;
}

.child {
  font-size: 0.5em;  /* 0.5 * 24px = 12px */
}

.deeply-nested {
  font-size: 0.5em;  /* 0.5 * 0.5 * 24px = 6px */
}
```

so `em` is not recommended for `font-size` but `em` can still be useful if you want to define certain properties of an element, like padding relative to an element's font size



### rem

`rem` or **root em** is calculated **relative** to the **root element's** `font-size` which by default is usually `16px`

and since the user is changing the root element's font size with their browser preferences --> `rem` is the ideal unit for font sizing



**User Agent Stylesheet** in **bold**

`10px = 0.625rem` - **h6** (well 10.72px)

`12px = 0.75rem`

`14px = 0.875rem` - **h5** (well 13.28px)

`16px = 1rem = 100%` **(base) body** and **h4**

`18px = 1.125rem` - **h3** (well 18.72px)

`20px = 1.25rem`

`22px = 1.375rem` 

`24px = 1.5rem` - **h2**

`26px = 1.625rem`

`30px = 1.875rem`

`32px = 2rem` - **h1**



### qem

the unit `qem` is used to handle quirky margins in reflow roots (body, td, and th) like WinIE - and when a site is in Quirks Mode

modern sites should never be in Quirks Mode, so you're **safe to assume that it's the same** as `em` 



## Images on the web

### HTML img

the `<img>` tag is used to display an image in HTML - it is a **self-closing** or **empty** element and so requires no closing tag

along with the `src` attribute - which works similarly to **href** for anchors

`<img src="https://www.theodinproject.com/mstile-310x310.png">` example with absolute path

`<img src="./../images/dog.jpg">` example with relative path

you should also include the `alt` (alternative text) attribute with every image (contributes to SEO, appears if the image doesn't load, and is read by screen readers)

and explicit width and height values, which will reserve space on the page, decreasing CLS (cumulative layout shift)

```html
<img src="./img/logo-310x310.png" alt="site logo" width="24" height="24">
```



### Width and Height

by default, an `<img>` element's width and height values will match the image file's actual width and height

Change an image's rendered width and height:

with HTML..

```html
<img src="./img/dog.jpg" alt="doggo" width="500" height="600">
```

with CSS..

```css
img {
  width: 500px;
  height: 600px;
}
```

it is best practice to always include explicit width and height properties in the **HTML** `<img>` element

this will reserve space on the webpage as it loads, which can reduce CLS (cumulative layout shift)

ommitting or using `auto` for either value would require the image to be downloaded first

then if you want to make the image more responsive - you want to *also* write some CSS rules to do so - as the CSS will override the HTML if needed

you can make all images more responsive by adding to your CSS..

```css
img {
    max-width: 100%; /* allow to shrink with its container when forced */
    height: auto;
}

and/or

img {
    min-width: 100%; /* allow to grow with its container (fill container) */
    height: auto;
}
```



### Alt text

*image alt text contributes to SEO, appears if the image doesn't load, and is read by screen readers

*alt should be used on every single image - but it should be left **blank** as `alt=""` for any image that is purely aesthetic and is not meaningful content

*image links (like a youtube link) should state where the link goes `alt="link to youtube channel"`



### Image Formats

There are many image formats floating around the internet - lets focus on the main ones..

transparancy = alpha = 

0-1 (semi)

0 or 1 (binary)

**JPG** - for **photos** \- bc photos generally contain lots of data - JPGs store that data efficiently without a ridiculous file size - **don't allow transparent pixels** (cover their background)

**PNG** - for anything not a photo or animation - a PNG file for a photo would likely be bigger than the quality-equivalent JPG file - have a wide color palette and are great for **icons**, **diagrams**, and **logos** - **allow semi transparent pixels**

**SVG** (vector-based rather than pixel-based) meaning they scale up/down without loss of quality - use for images containing simple geometric shapes, just like PNGs.. **icons**, **diagrams**, and **logos** \- use whenever possible - don't use SVGs for images containing lots of text - **allow semi transparent pixels**

**WebP** - newer - provides superior **lossless** and **lossy** **compression** for images on the web - meaning smaller file sizes for similar quality - use to replace any PNG or JPG scenerio - **allow semi transparent pixels**

**GIF**s - for simple **animations** \- have a limited color palette - **allow only binary transparent pixels**

**WebP animations** can provide reduced file sizes compared to GIFs

NOTE for something like a **Logo** try not to use an image.. use a custom web font and CSS instead



### Legal Notice

You do not have the legal right to use just any image on the web

make sure the image you use is actually free - and make sure to credit the creator of the image in your project - an easy way to give credit is to include the creator's name and contact info in the README of your repo



### Get rid of whitespace under images

the small whitespace rendered under images is a feature brought about back when images more commonly appeared wrapped in text on a webpage - the small whitespace corresponds to the needed line height for the image to be inline with the text

so images are by default `display: inline` and we can get rid of this white space by declaring..

```css
img {
    display: block;
}
```



### Image Optimization

format, file size, aspect ratio, and resolution



use **Webp**, with a **jpg** or **png** fallback, for **most images**

use **SVG** for **icons** 

use **SVG** for **logos** (if they don't contain too much text) else use **WebP** or just use **CSS** (if possible)

use `srcset` for images that will **shrink dramatically** between desktop and mobile



ORIGINAL images should ideally be **2500px** wide - bc you can convert them down to anything from there..



### JPEG PNG and ImageMagick

`ls -lh image.png` show human readable size of *image.png*

`convert` is a command in the `imagemagick` apt package



`convert <INPUT_FILE> -quality 90 <OUTPUT_FILE>` convert to 90% of original quality (default is 92%)

`convert <INPUT_FILE> -resize 200 <OUTPUT_FILE>` convert to width 200px - retain original aspect ratio

`convert <INPUT_FILE> -resize 200x200 <OUTPUT_FILE>` convert to width x height (px) - but retain the original aspect ratio - aka squeeze the image to fit inside a 200x200px box while retaining the original aspect ratio

`convert <INPUT_FILE> -resize 200x200! <OUTPUT_FILE>` convert to width x height (px) - neglect the original aspect ratio

`convert myfile.png myfile.jpg` convert file format

`man convert` for more - the convert command has hundreds of options



to **process multiple** images at once --> `mogrify` command

`mogifry` applies the operations on the original image file - so make a copy first and work on that

`mogrify -quality 90 *jpg` mogrify works similarly to `convert`



to **process PNGs** specifically see [LINK](https://www.digitalocean.com/community/tutorials/reduce-file-size-of-images-linux) --> `pngcrush` command

to **process JPGs** specifically see [LINK](https://www.digitalocean.com/community/tutorials/reduce-file-size-of-images-linux) --> `jpegoptim` command - supports target file size as a parameter



### WebP Images

to serve **WebP** - you should create two images..

```markdown
FORMAT: 1 x WebP   and   1 x jpg or png
FILE SIZE: < 300KB
WIDTH: (max expected rendered width)x3      - so they are crisp on 3x DPR screens
```



about WebP: [LINK](https://web.dev/serve-images-webp/)

Use WebP images whenever possible - to replace JPG or PNG - it can do both and file sizes are **much smaller**

WebP images are usually 25-35% smaller (file size) than their JPG counterparts

WebP images are usually 80% smaller (file size) than their PNG counterparts

WebP offers both **lossless** and **lossy** compression

**lossless** compression - reduces file size - no data is lost - commonly used for **PNGs**

**lossy** compression - reduces file size but at the expense of reducing image quality



instead of `ImageMagick` we will use the `cwebp` command..

`cwebp image.jpg -o image.webp -q 100` - simply convert image to WebP

`cwebp image.jpg -o image.webp -q 75` - convert image to WebP and 75% quality (the default)

`cwebp image.jpg -o image.webp -resize {width} {height} -q 75` - convert image to WebP, resize, and 75% quality

NOTE ommitting the `q` quality parameter will default to 75% quality reduction (watch out for this when resizing)



note if we want to save the complete, original data of images during compression, we use `-lossless` in place of `-q`

this is commonly used to maintain the quality of PNG images

`cwebp image.png -o image.webp -lossless`



to **convert all files** in a directory..

```bash
for file in ./*; do cwebp "$file" -o "${file%.*}.webp" -lossless; done
```

```bash
for file in ./*; do cwebp "$file" -o "${file%.*}.webp" -q 100; done
```

```bash
for file in ./*; do cwebp "$file" -o "${file%.*}.webp" -resize {width} {height} -q 75; done
```



### Serve WebP images in HTML

```html
<picture>
  <source type="image/webp" srcset="image.webp">
  <source type="image/jpeg" srcset="image.jpg">
  <img src="image.jpg" alt="" width="" height="">
</picture>
```

*note the `width` and `height` in the `img` tag are still respected - bc the `img` tag is techinically still the one serving the image - therefore you should still apply CSS styles to the `img` tag (don't try to style the `picture` element)

*of course, you can serve the webp image directly in the image tag if you don't care to support people with outdated browsers or on mobile

```html
<img src="image.webp" alt="" width="" height="">
```



### SVG Images

Scalable Vector Graphics - are files written in an XML based markup containing two dimensional vectors - [LINK](https://svgontheweb.com/)

they are more similar to a webpage than to a jpg - we can manipulate them with CSS and/or JavaScript

use for **icons**, **logos**, and **illustrations**



you can implement **SVGs** just as we did with **WebP** images..

```html
<picture>
  <source type="image/svg+xml" srcset="image.svg">
  <source type="image/jpeg" srcset="image.jpg">
  <img src="image.jpg" alt="" width="" height="">
</picture>
```

*but at this point SVG support is wide and we shouldn't have to provide any fallback, just use..

```html
<img src="image.svg" alt="" width="" height="">
```



for more functionality, like manipulating the actual image with CSS or JavaScript (usually not needed), you can use..

```html
<object type="image/svg+xml" data="image.svg">
    <img src="image.jpg" alt="" width="" height="">
</object>
```

*the child of `<object>` is displayed in the case that the object fails to display



### AVIF Images

.

```markdown
IMAGE
FORMAT:
FILE SIZE:
ASPECT RATIO:
RESOLUTION:
```

.



### Background Images

```css
div {
    padding: 20px 0;
    background-color: XXX /* included as a fallback */
    background-image: url(X); /* X = absolutue or relative path */
    
    /* if you want repeat, as with the images from subtlepatterns.com, use.. */
    background-repeat: no-repeat, repeat-x, or repeat-y;
    
    /* else you will likely use.. */
    
    background-size: cover; /* display as much of the image as possible - maintain aspect ratio */    
    background-position: center; /* center of image matches up with center of div */
    or
    background-position: top center; /* y-direction x-direction - top, center, left, right */
    
    /* think of background-position as setting the focal point of the image - the point on the image that will be 'pinned' and won't move as the container grows/shrinks */    
}

/* use PADDING to add more background area to the div */
```



NOTE we can actually style `<img>` elements in a similar fashion to background images if we declare..

```css
img {
    object-fit: cover; /* covers its container - crops the image if needed */
    object-position: /* can now be used just like 'background-position' */
}
```



### Banner Background Images

to **serve banner images** as **WebP** you will need..

```markdown
FORMAT: 1 x WebP   and   1 x jpg or png
FILE SIZE: < 300kB ?
ASPECT RATIO: 16:9
RESOLUTION: 2400 x 1350px
		or  1200 x  675px
```

*then serve them with CSS, as detailed below..



### Serve WebP images in CSS

in some cases, like with background images (banners), we add the image using CSS

CSS does not provide a built-in solution for fallback images

we use [Modernizr](https://modernizr.com/), a well-known **feature detection** library, to detect if the browser supports WebP

by creating a custom Modernizr build with WebP detection [LINK](https://modernizr.com/download?setclasses)

(I created the js file already --> copy it from the general-website-objects folder to your project directory)

add to your **html**..

```html
<html lang="en" class="no-js">

<body>
    <script>document.documentElement.classList.remove("no-js");</script>
    <!-- removes the .no-js class from the html element if browser has javascript enabled -->
    <script src="detect-webp.js"></script>
    <!-- detects if browser supports WebP and assigns class .webp or .no-webp to the html element - used to determine which background image to serve (see css) -->
```

add to your **css**..

```css
.no-js .target-div {
  background-image: url(./../img/banner.jpg);
}

.no-webp .target-div {
  background-image: url(./../img/banner.jpg);
}

.webp .target-div {
  background-image: url(./../img/banner.webp);
}
```



### Webpage Thumbnail

docs: [The Open Graph protocol](https://ogp.me/)

when you send a webpage URL in a message, share it to facebook, or other social site..

it will display as an Open Graph Object - a clickable box containing.. a thumbnail image, title, and description

```markdown
FORMAT: jpg jpeg png or webp
FILE SIZE: 5MB   (max)
ASPECT RATIO: 1.91:1   (imortant!)
RESOLUTION: 1200 x 628px   (recommended)
```

add your thumbnail image to your project directory

you will need the image URL (relative or absolute)

`./img/pasta-thumbnail.jpg`   or
`https://parktart.github.io/recipe-blog-site/img/pasta-thumbnail.jpg`

add to your html `<head>`..

```html
<!-- website link thumbnail meta properties: -->
<meta property="og:title" content="TITLE OF YOUR WEBPAGE"> <!-- 88 character max -->
<meta property="og:image" content="THUMBNAIL IMAGE URL - relative or absolute">
<meta property="og:description" content="DESCRIPTION OF YOUR WEBPAGE"> <!-- between 100-200 characters -->
<meta property="og:url" content="URL OF YOUR WEBPAGE">
<meta property="og:image:type" content="image/jpeg"> <!-- /png /jpeg /avif /svg+xml /webp -->
<meta property="og:image:width" content="1200">
<meta property="og:image:height" content="628">
<!-- choose the type of object, usually "website" or "article", below -->
<meta property="og:type" content="website">

<!-- NOTE the MIME type for both jpeg and jpg is image/jpeg -->
```

``property og:image:type` about [LINK](https://developer.mozilla.org/en-US/docs/Web/HTTP/Basics_of_HTTP/MIME_types/Common_types) -> or search 'MIME Type file-extension'

`property og:type` about https://ogp.me/#types



test it using the Sharing Debugger of your choice..

[Facebook Sharing Debugger](https://developers.facebook.com/tools/debug/)

[LinkedIn Sharing Debugger](https://www.linkedin.com/post-inspector/)

[Twitter Sharing Debugger](https://cards-dev.twitter.com/validator)

troubleshooting: [LINK](https://stackoverflow.com/questions/19632323/default-website-image-for-social-sharing)

*note some websites (Facebook) cache the image URL so if you want to change thumbnail images you have to use a different URL for the new image (use a different file name)



### Responsive Images - srcset

`srcset` is used by default in **wordpress** but it can be a bit cumbersome to implement by hand.. therefore it is recommended to instead focus on serving smaller (file size) images first before resorting to `srcset` and maybe not even using `srcset` ??



image (px width and/or file size) suitable for desktop may be too large for mobile (using 2-4x more data than necessary)

therefore we serve different image sizes using `srcset`

`srcset` evaluates the viewing device (screen size, resolution, etc) and serves the most appropriate image size

this can reduce data usage on phones and tablets and decrease your Largest Contentful Paint (LCP)

it's common to serve **3-5** different image sizes for each image

*use `imagemagick` or `cweb` to manipulate images (see section "JPEG PNG and ImageMagick")



if your image **will not grow/shrink** on the webpage (will maintain the same wxh) you *can* use..

```html
<img src="pasta-500.jpg"
     srcset="pasta-500.jpg 1x,
             pasta-1000.jpg 2x,
             pasta-1500.jpg 3x"
     alt="" width="" height="">
```

where 1x, 2x, and 3x refer to the DPR (density pixel ratio) of the viewing device - if the browser detects a 2x DPR device, it will display the 2x image



but for **most cases** where we want **responsive images** we should use the below methods

which also take DPR into account, so you can actually just **ALWAYS** use these methods..



when the image **will not grow/shrink** on the webpage..

```html
<img src="pasta-500.jpg"
     srcset="pasta-500.jpg 500w,
             pasta-1000.jpg 1000w,
             pasta-1500.jpg 1500w"
     sizes="600px"
     alt="" width="600" height="800">
<!-- where sizes = the width we expect the image to render at -->
```



when the image **width** will always be approximately 100% of the viewport width (**100vw**)..

```html
<img src="pasta-500.jpg"
     srcset="pasta-500.jpg 500w,
             pasta-1000.jpg 1000w,
             pasta-1500.jpg 1500w"
     sizes="100vw"
     alt="" width="" height"">
```



when the image **width** changes and is not **100vw**..

```html
<img src="pasta-500.jpg"
     srcset="pasta-500.jpg 500w,
             pasta-1000.jpg 1000w,
             pasta-1500.jpg 1500w"
     sizes="50vw"
     alt="" width="" height"">
```

`sizes` tells the browser how wide we expect the image to be when displayed (and can be approximate)

`sizes="100px"` `sizes="50vw"` `sizes="20em"` `sizes="calc(100vw-20px)"` are all valid



when the image **width** changes are related to **media queries**..

```html
<img src="pasta-500.jpg"
     srcset="pasta-500.jpg 500w,
             pasta-1000.jpg 1000w,
             pasta-1500.jpg 1500w"
     sizes="(max-width: 1160px) 100vw, 50vw"
     alt="" width="" height"">
```

`sizes="(media query) size-at-that-media-query, size-for-all-other-cases"`

and these should match your CSS **media queries**, if those queries are related to the image's change in width

BUT if this is too bothersome you can just approximate the `sizes` attribute very loosely (use 100vw)



`src` is used here as a fallback for browsers that don't support `srcset`

if supported, the browser will choose an image from `srcset`

*there is debate whether to use the highest or lowest quality image for the fallback `src`



*you can use DevTools > (mobile layout) > Dimensions = responsive > Network tab > Disable Cache > and reload to see what version of the image loads as you vary the screen width



## Colors on the web

the `color` property sets an element's text color

the `background-color` sets the element's background color

there are several types of **values** you can use to specify color (see CSS bookmarks for a full list)

some keyword examples..
~ the `currentcolor` keyword takes on the current (already defined) color of an element - for example to make a border the same color as the (already defined) text
~ the `transparent` keyword is transparent

examples for HEX, RGB, and HSL..

```css
p {
  color: #1100ff;
  color: rgb(100, 0, 127);
  color: hsl(15, 82%, 56%);
}
```

```css
/* alpha values */

div {
  background-color: rgb(0, 0, 0, 0.2);
}

div:hover {
  background-color: rgb(0, 0, 0, 0.4);
}
```



## CSS Selectors

<u>Basic Syntax of CSS</u>:

CSS at its most basic level is made up of various rules - these rules are defined by a **selector** and a list of one or more **declarations** - each declaration is a **property:value** pair and the declarations are seperated by semi-colons ;

![CSS syntax](https://user-images.githubusercontent.com/70952936/130702428-4808becb-cbc4-4a4d-8fa7-f9aa5409768d.jpg)

### Selectors

the **selector** defines *which* HTML elements will be styled by the CSS rule

the **universal selector** = `*` will target all elements

----

a **type selector** (or element selector) is used to define which type of element you want to target - its syntax is simply the same as the element you want to target - for example to target all `<div>` elements..

```css
/* styles.css */

div {
  color: white;
}
```

----

a **class selector** is used to define which class you want to target - you can assign any element a class individually - for example..

```html
<!-- index.html -->

<div class="alert-text">
  Please agree to our terms of service.
</div>
```

```css
/* styles.css */

.alert-text {
  color: red;
}
```

note: you can add multiple classes to a single element `class="alert-text severe-alert"`

----

an **id selector** is used to select elements with a given ID - it is similar to class - for example..

```html
<!-- index.html -->

<div id="title">My Awesome 90's Page</div>
```

```css
/* styles.css */

#title {
  background-color: red;
}
```

note: it is best practice to use **class** instead of the **id selector** when possible - the **id selector** should be used *sparingly* (if at all) because..
~ an element can only have **one** id
~ an id cannot be repeated on the same page

----

**Grouping**: you can style multiple classes in the same block of code - seperate the classes with a comma - for example..

```css
/* styles.css */

.read,
.unread {
  color: white;
  background-color: black;
}
```

----

**Chaining**: you can chain selectors together to target only elements with both *this* and *that* class - for example..

```html
<!-- index.html -->

<div>
  <div class="subsection header">Latest Posts</div>
  <p class="subsection preview">This is where a preview for a post might go.</p>
</div>
```

```css
/* styles.css */

.subsection.header {
  color: red;
}
```

will target only elements that have **both** the .subsection and .header classes

you can use this to chain **classes** with an **id** `.subsection#someid` not sure why you would tho

----

### Combinators

**Combinators** allow you to combine multiple selectors differently than either grouping or chaining - **combinators** describe a relationship between the selectors

there are four types of combinators - we will look at only one for now..

### 1. Descendant Combinator

the **descendant combinator** is represented by **a single space** between selectors - and will only effect elements that *match the last selector* if they also *have an ancestor (parent, grandparent, etc) that matches the previous selector*

```html
<!-- index.html -->

<div class="ancestor"> <!-- A -->
  <div class="contents"> <!-- B -->
  </div>
</div>

<div class="contents"></div> <!-- C -->
```

```css
/* styles.css */

.ancestor .contents {
  /* some declarations */
}
```

(B is targeted)

for example `.ancestor .child` would select an element with class `child` only if it has an ancestor with class `ancestor` (no matter how deep)

so `.one .two .three .four` would be totally valid - this would just select an element that has a class of `four` if it has an ancestor with a class of `three`, and if that ancestor has its own ancestor with a class of `two`, and if that ancestor has its own ancestor with a class of `one`

you may want to avoid this, however, as it can get confusing



## CSS Cascade

<u>The Cascade of CSS</u>:

CSS does what we tell it to do - but one exception to that is the default styles that are provided by a browser - which vary from browser to browser - and can cause some elements to create a large gap between themselves and other elements - or can style **buttons** without us writing any CSS rules ourselves

so, if you end up with some unexpected behavior, default browser styles could be the cause - or your own code - or it could be the cascade..

ahh the cascade

**the cascade** determines which rules will actually be applied to our HTML - it uses several factors to make its decision - we will discuss three of them below..

### 1. Specificity

a CSS declaration that is more specific will take precedence over less specific ones - for example..

**Inline Styles** have a higher specificity than **Selectors** - and so take precedence

further, each type of **Selector** has a different specificity level which contributes to how specific a declaration is - for the ones mentioned earlier, the order is..

1. ID selectors (most specific)
2. Class selectors
3. Type selectors

note this will only matter when an element has multiple conflicting declarations targeting it - so you can use an ID selector to override any number of class selectors and so on

a larger amount of a single selector will beat a smaller amount of the same selector (if no other winner is present) - for example..

```html
<!-- index.html -->

<div class="main">
  <div class="list subsection"></div>
</div>
```

```css
/* rule 1 */
.subsection {
  color: blue;
}

/* rule 2 */
.main .list {
  color: red;
}
```

red wins here - more examples of [specificity](https://www.theodinproject.com/lessons/foundations-css-foundations) (control f)



### 2. Inheritance

Inheritance refers to certain CSS properties that, when applied to an element, are inherited by that element’s descendants

Typography based properties (`color`, `font-size`, `font-family`, etc.) are usually inherited, while most other properties aren’t

The exception to this is when directly targeting an element, as this always beats inheritance



### 3. Rule Order

the final factor - the tie-breaker of the tie-breaker - if no other factor has won over the others and it is still tied - how does the cascade determine which rule to apply?

really simple, actually, whichever rule is further down in the CSS file



## Cascade Layers

is a relatively new CSS rule you can utilize for more explicit control of the cascade and to prevent specificity conflicts

using Cascade Layers promotes clear CSS and avoids unexpected style overrides

`@layer` allows you to introduce a *new layer* to your CSS cascade

the new layer can be given precendence over other layers - note layered CSS will not override non-layered (normal) CSS

Layered styles create new cascade "planes"

probably best to add layers near the end of your CSS file..

with mulitple layers, their precedence is determined by when they are introduced in the CSS file - with the most specific being last

```css
/* normal CSS */

a {
   background-color: yellow; /* is applied - layers do not override normal CSS */
}

/* layers */

@layer least-specific {
  .links {
    color: red; /* ignored */
  }
}

@layer middle {
  a {
    color: green; /* styles all links - overrides specificity of class .links */
    background-color: black; /* is ignored */
  }
}

@layer most-specific {
  .pink {
    color: hotpink;  /* styles elements of class .pink */
  }
}
```

**layer precedence** beats **element specificity**

Layer order is established by the first time each layer name appears in your code

therefore you can make it more obvious by adding..

```css
@layer least-specific,
       middle,
       most-specific;
```

to the top of your CSS file



you can use Layers to import specific styles from another css file: see [organizing imports](https://developer.chrome.com/blog/cascade-layers/#organizing-imports)



## Adding CSS to HTML

there are three different methods to add CSS to HTML

### 1. External CSS

**External CSS** is the most common method - you create a separate file for the CSS - and link to it in your HTML file's `<head>` element using a self-closing (empty) `<link>` tag

```html
<!-- index.html -->

<head>
  <link rel="stylesheet" href="style.css">
</head>
```

```css
/* styles.css */

div {
  color: white;
  background-color: black;
}

p {
  color: red;
}
```

note `style.css` is a very common file name

This method..

~ keeps your HTML and CSS separate - making your HTML file smaller and cleaner

~ keeps the CSS in one place - and the same CSS file can be used to style multiple pages



### 2. Internal CSS

**Internal CSS** - or embedded CSS - you add the CSS within the HTML file - you place all of the rules inside a `<style>` element - which is inside the `<head>` element

the CSS syntax works the same as if it were in a seperate css file

```html
<head>
  <style>
    div {
      color: white;
      background-color: black;
    }

    p {
      color: red;
    }
  </style>
</head>
<body>...</body>
```

This method is useful for adding unique styles to a *single page* of a website - but best to avoid if possible - it could make your HTML file pretty big



### 3. Inline CSS

**Inline CSS** makes it possible to add styles directly to HTML elements using the `style` attribute

note this method should be avoided in order to keep your html clean

```html
<body>
  <div style="color: white; background-color: black;">...</div>
</body>
```

you don't actually use any selectors since the style is added directly to the element

Inline CSS really isn't reccommended unless you need to add a *unique* style for a *single* element

note: Inline CSS will override any other method of targeting an element with style



## User Agent Stylesheet

a web browser fed with an HTML document that has no styling (CSS) information attached will render the html using minimal formatting

this minimal formatting is defined in the **User Agent Stylesheet** which is a key component of *the cascade*

each User Agent (UA aka web browser) will have a default style sheet that presents documents in a reasonable, but arguably mundane, manner

there are few instances where one should completely reset this default stylesheet - but usually we overwrite specific parts of it indivually, for example..

```css
* {
  margin: 0;
  padding: 0;
  font: inherit; /* wipe all User Agent fonts, sizes, and weights */
}
```



## CSS best practices

how i will style Odin Projects..

### Use the External Method

use the **external method** to add CSS to all Odin projects

store your `style.css` file(s) in a folder called `css`

```html
<!-- html -->
<head>
  <link rel="stylesheet" href="./css/style.css">
</head>
```



### Use Selectors

use the `<div>` or `<span>` tag in your `html` to divide sections to be styled (if needed)



use **type selectors** for things like `font-weight`

```css
p {
   font-weight: bold; /* 100 up to 900 with 400 = normal and 700 = bold */
}
```

use **class selectors** for more specific things

```html
<!-- html -->
<p class="gray-background">
  This is some text.
</p>
```

```css
/* css */
.gray-background {
  background-color: gray;
}
```

use **id selectors** for even *more* specific things

```html
<!-- html -->
<div id="logo">Parktart Recipes</div>
```

```css
/* css */
#logo {
  background-color: blue;
}
```

use **Grouping**..

```css
.header,
.content {
  color: white;
  background-color: gray;
}
```

use **Chaining**..

```css
.header.main {
  font-size: 30px;
}
```

use the **descendant combinator** to reduce the amount of classes or IDs needed to style your html

```css
.ancestor .child {
  background-color: blue;
}
```

rely on **inheritence** to express the same functionality with fewer or shorter declarations



## Inspecting HTML and CSS  (DevTools)



<u>HTML versus the DOM</u>:

HTML represents initial page content - and the DOM represents current page content - after any JavaScript or other scripts run - if they add, remove, or edit nodes, the DOM becomes different than the HTML - for more info see [this link](https://developer.chrome.com/docs/devtools/dom/#appendix)



<u>Chrome DevTools</u>:

Chrome DevTools will allow you to see detailed info about your HTML elements and CSS rules - and help fix problems in your code

it's simple..

to open **DevTools** - use `ctrl + shift + I`

to inspect elements - use `ctrl + shift + C`

or right click on any element of a webpage --> Inspect 

to open the **Console Panel** - use `ctrl + shift + J`

to **close** DevTools - use `ctrl + shift + I`



when an element is selected (in the Elements panel) the Styles pane will show all the currently applied styles, as well as any styles that are being overwritten (indicated by a strikethrough of the text)

you can also navigate to different nodes in the DOM with the `up` and `down` arrow keys on your keyboard - use the `left` and `right` arrow keys to collapse/expand nodes - note, if already collapsed, the `left` arrow key will take you to the parent of the current node

`right-click` any node in the DOM and press **Scroll into view** - this will take you to that node on the webpage

also you can `ctrl F` in the Elements pane to search the DOM

the Styles pane also allows you to edit styles directly in the browser - you can click inside of any individual selector to add a new rule or click on an existing attribute or value to alter it

in the Styles pane, use the **element.style** section to add **inline** CSS to the selected element

press the `.cls` button (in the Styles pane) to view all CSS classes for the currently selected element

press the `:hov` button (in the Styles pane) to view all CSS pseudostates for the currently selected element - you can force states from here - you can also force states by `right clicking` the node in the DOM tree -> Force state -> :hover

use the **box model** found at the bottom of the Styles pane to alter the margin, border, and padding of an element

`right click` on any node to edit as HTML with syntax highlighting and autocomplete (you will press `ctrl + enter` to submit the changes)

you can **drag and drop** nodes in the DOM tree to rearrange them

when inspecting CSS.. instead of the `Styles` pane select the `Computed` pane to show..

- only the CSS that's actually being applied to the element
- in alphabetical order
- inherited properties are opaque - check **Show All** to see all inherited values

To view a page in **print mode** --> Open DevTools --> `Ctrl Shift P` (commands) --> Show Rendering --> change 'Emulate CSS media type' to 'print'

To view what CSS and/or JS is actually used on a page --> Open DevTools --> `Ctrl Shift P` (commands) --> **Show Coverage** --> click record/reload --> the coverage pane shows an overview of how much CSS (and JavaScript) is used from each file the browser loads

- green represents used CSS - red represents unused CSS

- click on a file to see a line-by-line breakdown of what CSS is being used



## The Box Model

the most important skills you need to master with CSS are *positioning* and *layout*

that starts with understanding **The Box Model**..

every single thing on a webpage is a rectangular box - these boxes can have other boxes in them and can sit alongside one another 

you can get a rough idea of this by applying a border to every item on your page

```css
* {
    border: 2px solid red;
}
```

note any cirlces you see as a result of this also behave just like rectangles (well, squares) when side by side

laying out a webpage and positioning all its elements = deciding how you are going to nest and stack these boxes

to manipulate the size of boxes, and the space between them, we use `width`, `height`, `margin`, `border`, and `padding`

![margin-border-padding](/home/parker/Dropbox/objects-photos-etc/margin-border-padding.png)

![margin-border-padding-2](/home/parker/Dropbox/objects-photos-etc/margin-border-padding-2.png)

`width` is the width of the 'content box' (unless `border-box` is specified)

`height` is the height of the 'content box' (unless `border-box` is specified)

`padding` is the (background-color) space surrounding the 'content box'

`margin` is the space between an element's border and another element's border

`border` is the space (even if it’s only a pixel or two) between the margin and the padding



## How to apply the box model

```css
.class {
    width: 500px;  /* width of the 'content box' */
    height: 30px;  /* height of the 'content box' */
    padding: 20px;
    border: 2px solid red;
    margin: 20px;
}
```

note we use `margin` to change the spacing between elements

NOTE when tools like DevTools display `height` and `width` of an element - they may be giving you the `border-box` width and height..

`width + left padding + right padding + left border + right border`

`height + bottom padding + top padding + bottom border + top border` 

so it is using everything but the `margin` for the element's 'size'

what would be the 'size' of the above code??

w x h = 544 x 74px

now if you want to skip all this math, and you know you want your `content + padding + border` to be, say `100 x 100px`  you can add the `border-box` rule..

```css
.class {
    width: 100px;
    height: 100px;
    box-sizing: border-box;
}
```

which will calculate and implement the correct 'content box' size to meet your specs, so..

```css
.class {
    width: 100px;  /* width of the 'content box + padding + border' */
    height: 100px;  /* height of the 'content box + padding + border' */
    padding: 20px;
    border: 2px solid black;
    margin: 20px;
    box-sizing: border-box;
}
```

would have a 'content box' size of w x h = 56 x 56px

note using `box-sizing: border-box;` is preferred by many developers - using `border-box` may also be called "using The Alternative Box Model"

to use The Alternative Box Model for all of your elements, set all elements to inherit the value..

```css
*,
*::before,
*::after {
  box-sizing: border-box;
}
```



## Using The Box Model

### Divs and Spans

`<div>` and `<span>` give no particular meaning to their contents - they are just containers

we use them to contain things we want to style with CSS

or to group elements and position them on a page

`<div>` is a block element by default

`<span>` is an inline element by default

```html
<p>
  We will highlight <span class="highlight">this</span> for fun.   
</p>
```

```css
.highlight {
  background-color: yellow;
}
```

### Normal Flow

the way browsers layout elements if you haven't changed their layout yourself is called **normal flow**

starting with a solid well-structured document that's readable in normal flow is the best way to begin any webpage

### More on The Box Model

each box is further defined by two display types..

1 --- the **outer display type** defines **how the box will behave** on the webpage, and by default will be either..

`block` \- which means..

- note: `<body> <h1> <p> <ul> <ol>` have `display: block;` by default
- the box will be surrounded by line breaks (be on its own line on the webpage)
- the `width` and `height` properties can be changed
- `margin`, `padding`, and `border` will push/pull other elements away from the box
- the box will extend in the inline direction to fill the space available in its container (the box will become as wide as its container by default)

or `inline` \- which means..

- note: `<a> <span> <em> <strong>` have `display: inline;` by default
- the box will not create line breaks (box will be inline)
- an inline element cannot contain a block element
- the `width` and `height` properties cannot be changed
- **vertical** margin, padding, and border will apply but **will not** cause other inline boxes to move away from the box
- **horizontal** margin, padding, and border will apply and **will** cause other inline boxes to move away from the box

2 --- the **inner display type** defines **how elements inside the box** are laid out

by default the **inner display type** is already set to either `block` or `inline` (depending on the element) - yo some of the wording here isn't completely accurate - just roll with it and learn flexbox

but **inner display type** can be changed to values like `flex` or `grid` (and the outer display type will remain `block` or `inline`)

by defining `display: flex;`

NOTE - any *direct* children of this box will also have their **outer display type** set to `flex` (the children in the container are flex items)

for example, applying `display: flex;` to an `<ul>` will keep the `<ul>` outer display type `block` but change the inner display type to `flex` making its children (the `<li>` items) into flex items

NOTE - to change both the **outer** and **inner** would look like `display: inline-flex`

NOTE - in practice you will probably use `flexbox` more than `inline-flex` or `inline-block` for dealing with things like this

## Block and Inline

elements with a display type of `block` are called **block boxes**, **block elements**, or **block-level elements**

elements with a display type of `inline` are called **inline boxes**, **inline elements**, or **inline-level elements**

#### The Block Elements of HTML

```html
<address> <article> <aside> <blockquote> <canvas> <dd> <div> <dl> <dt> <fieldset> <figcaption> <figure> <footer> <form> <h1>-<h6> <header> <hr> <li> <main> <nav> <noscript> <ol> <p> <pre> <section> <table> <tfoot> <ul> <video>
```

#### The Inline Elements of HTML

```html
<a> <abbr> <acronym> <b> <bdo> <big> <br> <button> <cite> <code> <dfn> <em> <i> <img> <input> <kbd> <label> <map> <object> <output> <q> <samp> <select> <small> <span> <strong> <sub> <sup> <textarea> <time> <tt> <var> <script>
```

### for Block Boxes

#### Margins

margin pushes or pulls other elements away from the box

margins can have positive or negative values, percentages, or the keyword `auto`

margin collapse only happens in the vertical direction

<u>Defining Margin</u>

```css
margin: 20px;  /* all four margins 20px */

margin-top: 20px;  /* top, right, bottom, or left margin 20px */

margin: 0 10px 0 20px;  /* top right bottom left */

margin: 0 10px;  /* top-and-bottom right-and-left */

margin: 0 10px 8px;  /* top right-and-left bottom */
```

<u>Horizontal Centering</u>

you can also use `auto` for margin - which will be equivalent to 0 in most cases - or whatever space is available on that side of the element

`auto` is useful for **horizontal centering**..

```css
body {
    max-width: 750px;
    margin: 8px auto; /* 8px is UA default - but top margin is collapsed to = h1 margin anyway */
    margin: 0 auto;  /* so this would give the same result in most cases - and should be used */
    /* unless you specify a body top margin which exceeds the h1 margin */
}
```

<u>Collapsing Margins</u>

Margins collapse if they are *vertical* (top and bottom) and adjacent

note that *vertical nested* (like a `<p>` in a `<div>`) margins also collapse

*horizontal* margins do not collapse but rather add

for collapsing (vertical) margins for **block boxes**..

- if two positive margins meet - the largest of the two will be used
- if two negative margins meet - the smallest (furthest from zero) will be used - negative margins can cause boxes to overlap
- if one positive and one negative meet - they will be added (the margin is shrunk by the negative)

#### Borders

there are four borders, it's a rectangle after all, and each border has a width, style, and color

`border: 2px solid red;`

`border-top, right, bottom, left: 2px;`

#### Padding

you cannot have negative padding (only margins can be negative)

`padding: 10px;`

`padding-top, right, bottom, left: 10px;`

### for Inline Boxes

NOTE all of the above 'Using The Box Model' applies to **block boxes** \- and some of it can be applied to **inline boxes**

for example: the `<span>` element, though it is default inline, can have margin, border, and padding applied (not height and width) but it will display slightly different behavior

note `display: inline-block;` is a special value of `display` which allows you to keep an **inline element** inline (and not break to a new line) while allowing you to manipulate its values as if it were a **block box** \- the only difference being it will only become larger than its content if you define explicit `width` and `height`

this can be used to give a **link** a larger area by adding **padding** to your `<a>` element (if not using flexbox)

```html
<!-- html -->

<a class="big-link" href="foo.com">Click Me</a>
```

```css
.big-link {
    display: inline-block;
    background-color: gray;
    color: white;
    text-decoration: none;
    padding: 1em 2em;
}

.big-link:hover {
    background-color: darkslategray;
}
```



## Flexbox intro

Flexbox is a relatively new way of manipulating elements in CSS - and it has been a game changer - older methods (like float, table, inline-block, etc) have since fallen out of style

it is recommended to use flexbox to lay out your webpages as much as possible - and only use floats when you need text to flow *around* a box (like a magazine-style layout) or when you need to support legacy web browsers

Flexbox layouts can get a little complicated - if something isn't behaving the way you'd expect - inspecting it with DevTools should be your first reaction

Flexbox at its core is a way to arrange items into rows or columns - these items can flex (grow or shrink) based on simple rules you define

Flexbox is not just a single CSS property but a whole toolbox of properties that you can use to put things where you need them

Some of these properties belong on the *flex container* - while some go on the *flex items* - this is a simple yet important concept

a **flex container** is any element that has `display: flex`

a **flex item** is any element that lives directly inside of a flex container

![flexbox](/home/parker/Dropbox/objects-photos-etc/flexbox.png)

Note you can also apply `display: flex` to a **flex item** and use flexbox to arrange *its* childred - meaning an element can be both a **flex item** and **flex container**

![flexbox2](/home/parker/Dropbox/objects-photos-etc/flexbox2.png)

Creating and nesting multiple flex containers and items will enable us to create complex layouts. 

The following image was achieved using *only* flexbox to arrange, size, and place the various elements.

![flexbox3](/home/parker/Dropbox/objects-photos-etc/flexbox3.png)

remember that these flexbox properties are just a language that lets you tell browsers how to arrange a bunch of HTML elements - the hard part isn’t actually writing the HTML and CSS, but figuring out conceptually (on a piece of paper), the behavior of all the necessary boxes to create a given layout



## Flexbox Summary

note **flex items** can be manipulated individually - but for the most part it's up to the container to determine their layout

flex containers only know how to position elements that are one level deep (their direct children)

in practice you will likely not be using complex values for `flex-grow`, `flex-shrink` or `flex-basis`

for most purposes, authors should use `flex:` `auto`, `initial`, `none`, or `1, 2, 3, etc`

```css
.flex-container {
  color: white;
  background-color: blue;
  padding: 20px 0; /* if you want more height but dont need to adjust vertical alignment */
  height: 100px;   /* if you do need to adjust vertical alignment */
  display: flex; /* or inline-flex */
  justify-content: flex-start (default); /* "center" "flex-end" "space-around" "space-between" "space-evenly" - horizontal alignment */
  align-items: stretch (default); /* "center" "flex-start" "flex-end" "baseline" - vertical alignment */
  align-content: flex-start (default); /* similar to align-items but used to space out rows/columns of wrapped content - "center" "flex-end" "space-between-around-evenly" "stretch" */
  gap: 8px; /* sets gap all around the items */
  gap: 8px 10px /* row-gap column-gap */
  row-gap: 8px;
  column-gap: 8px;
  /* use gap as a sort of minumum by defining along with, say, justify-content:"space-around" */
  flex-wrap: nowrap (default); /* "wrap" forces items that don't fit to be wrapped to the next row */
  flex-direction: column; /* for column.. align-items=horizontal alignment / justify-content=vertical alignment */
  flex-flow: row-reverse wrap; /* a shorthand which combines flex-direction and flex-wrap */ 
}


.flex-item {

  /* DEFAULT */
  (flex item w no styling) /* will render as content width - will not grow - will shrink to its minimum content size if forced */
  
  /* DEFAULT */
  width: 500px; /* will render as width - will not grow - will shrink if forced */

  /* DEFAULT */
  width: 500px;
  flex: initial;
  flex: 0 1 auto; /* will render as width - will not grow - will shrink if forced */
    
  flex: 0 1 800px; /* render as 800px - will not grow - will shrink if forced */
  flex: 0 1 90%;   /* render as 90% width of parent container - will not grow - will shrink if forced */
  flex: 0 1 content; /* will render as content width - will not grow - will shrink to its minimum content size if forced */
    
  min-width: 50px;   /* wont shrink below min */  
  min-height: 100px; /* wont shrink below min */  
  max-width: 500px;  /* wont grow beyond max */
  max-height: 200px; /* wont grow beyond max */
    
  width: 500px; /* explicit width will be respected hard */
  flex: none;
  flex: 0 0 auto; /* will render as width and will not flex in any way */

  width: 500px; /* explicit width will be ignored bc of flex-basis 0 */
  flex: 1; 
  flex: 1 1 0; /* will fill its container - will grow - will shrink */
  
  width: 500px; /* will fill its container - will grow - will shrink - similar to flex:1 */
  flex: auto;   /* but explicit or content width is not ignored - and the amount of available space a flex:auto item grabs does depend on its width - the bigger the width/content -> the more space it grabs */
  flex: 1 1 auto;

  width: 500px;
  flex: 1 0 auto; /* will fill its container - will grow - will not shrink less than width */

  /* INDIVIDUAL */

  flex-grow: 0; /* DEFAULT - will render as width - will not grow */
  flex-grow: 1; /* will fill its container */

  flex-shrink: 1; /* DEFAULT - will shrink */
  flex-shrink: 0; /* will not shrink at all or will not shrink less than width */

  flex-basis: auto; /* DEFAULT - explicit width is not ignored */
  flex-basis: 0; /* explicit width will be ignored */
  
  justify-self: center;   /* "flex-start" "flex-end" "space-around" "space-between" */
  align-self: center;     /* "flex-start" "flex-end" "stretch" "baseline" */
  margin: auto; /* push things away by taking up all remaining available space */
}
```

note `flex` is actually a **shorthand property**

**shorthand properties** are CSS properties that enable you to set the values of multiple other CSS properties simultaneously

note by default, **flex items** won’t shrink below their minimum content size (the length of the longest word or fixed-size element) - use `min-width` to change this

note when you change to `flex-direction: column` --\> replace every instance of the word `width` on this page with `height` (in your head)

Example: 3 columns - the middle column does not shrink below `width: 250px`..

```html
<div class="flex-container">
  <div class="one"></div>
  <div class="two"></div>
  <div class="three"></div>
</div
```

```css
.flex-container {
  display: flex;
}

.flex-container div {
  background: peachpuff;
  border: 4px solid brown;
  height: 100px;
  width: 250px;
  flex: 1 1 auto;
}

.flex-container .two {
  flex-shrink: 0;
}
```

## Using Flexbox

from [interneting is hard](https://www.internetingishard.com/html-and-css/flexbox/)

we will use flexbox to build this:

![flexbox-example](/home/parker/Dropbox/objects-photos-etc/flexbox-example.png)

$ code ~/Desktop/testing/flexbox (open this folder to view code)

let's start with clearing margin and padding..

```css
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  /* border: 1px solid red; */
}
```

and then make a simple horizontal menu at the top of the webpage..

```html
<body>
    <div class="menu-container">
      <div class="menu">
        <div class="date">Oct 13, 2022</div>
        <div class="links">
          <div class="signup">Sign Up</div>
          <div class="login">Login</div>
        </div>
      </div>
    </div>
```

```css
.menu-container {
  color: white;
  background-color: blue;
  padding: 20px 0;
  display: flex;
  justify-content: center; /* defines horizontal alignment of this container's items */
  /* other values include "flex-start" "flex-end" "space-around" "space-between" */
}

.menu {
  width: 900px;
  /* margin: 0 auto;  is replaced with justify-content seen above */
  display: flex;
  justify-content: space-between;
}

.links {
  display: flex;
  justify-content: flex-end;
}

.login {
  margin-left: 20px;
}
```

we can actually do this with less divs by using auto-margin between date and signup..

```html
<body>
    <div class='menu-container'>
      <div class='menu'>
        <div class='date'>Aug 14, 2016</div>
        <div class='signup'>Sign Up</div>
        <div class='login'>Login</div>
      </div>
    </div>
```

```css
.signup {
  margin-left: auto;
}
```

think of auto-margins as a 'divider' for flex items in the same container - they eat up all the extra space in a flex container

auto-margins can be used to reduce the amount of divs you need - reducing the amount of HTML and CSS needed for the same result

now lets make a horizontal header below the horizontal menu..

```html
    <div class='header-container'>
      <div class='header'>
        <div class='subscribe'>Subscribe</div>
        <div class='logo'><img src='images/awesome-logo.svg'></div>
        <div class='social'><img src='images/social-icons.svg'></div>
      </div>
    </div>
```

```css
.header-container {
  color: blue;
  background-color: lightblue;
  display: flex;
  justify-content: center;
}

.header {
  width: 900px;
  height: 300px; /* we use height to make it taller, vs padding used for the menu above - defining height allows room to also define vertical alignment */
  display: flex;
  justify-content: space-between;
  align-items: center; /* defines vertical alignment of this container's items */
  /* other values include "flex-start" "flex-end" "stretch" "baseline" */
}
```

when you define an explicit height for a flex container - items can then be positioned vertically inside of it (this is called cross-axis alignment)

`align-items: stretch` can be used to create equal-height columns with variable amounts of content in each one

a key part of responsive design is presenting the same HTML for both mobile and desktop users - and since most mobile layouts are a single column, while most desktop layouts stack elements horizontally --> using `flex-direction: column;` will become very useful for building responsive websites

now lets make a container for our content, which is 5 photos that we want to display..

```html
    <div class='photo-grid-container'>
      <div class='photo-grid'>
        <div class='photo-grid-item first-item'>
          <img src='images/one.svg'>
        </div>
        <div class='photo-grid-item'>
          <img src='images/two.svg'>
        </div>
        <div class='photo-grid-item'>
          <img src='images/three.svg'>
        </div>
        <div class='photo-grid-item'>
          <img src='images/four.svg'>
        </div>
        <div class='photo-grid-item last-item'>
          <img src='images/five.svg'>
        </div>
      </div>
    </div>
```

```css
.photo-grid-container {
  display: flex;
  justify-content: center;
}

.photo-grid {
  width: 900px;
  display: flex;
  justify-content: center;
  flex-wrap: wrap; /* forces items that don't fit to be wrapped to the next row */
}

.photo-grid-item {
  width: 300px; /* making the divs which contain each image the same wxh as each image - not sure why */
  height: 300px;
}
```

note we could use..

```css
.photo-grid {
  flex-direction: row-reverse; /* allows us to reverse the order of items without editing the underlying html */
  /* it reverses each row separately and not the whole string as one - its really not a great property to use */
    or
  flex-direction: column; /* defines whether a container renders its items horizontally or vertically */
  /* the other value is "row" which is the default */
  /* note when you rotate the direction of a container like this - you also rotate the direction of the align and justify properties */
  align-items: center; /* we now use align-items for horizontal alignment and justify-content for vertical alignment */
}
```

above we have used flex *containers* to manipulate their contents - you can also manipulate flex items individually

we can position individual items with `justify-self` or `align-self`

```css
.social,
.subscribe {
  align-self: flex-end; /* vertically aligns the individual items */
    /* other values include "center" "flex-start" "stretch" and "baseline" */
  margin-bottom: 20px;
}
```

the "order" property for a flex item defines its order in the container without affecting surrounding items

the default value is 0 and increasing or decreasing it moves the item right or left

```css
.first-item {
  order: 1
}

.last-item {
  order: -1;  /* not really sure why but this switches them instead of moving them */
}
```

everything above has used fixed widths - and so they don't flex

the `flex` property allows for flexible widths - defining how the container should distribute extra space to each item

an item with a flex value of 2 will grow twice as fast as an item with the default value of 1

whereas `justify-content` distributes space *between* items - using `flex` instead distributes the space *into* the items

let's add a footer..

```html
    <div class='footer'>
      <div class='footer-item footer-one'></div>
      <div class='footer-item footer-two'></div>
      <div class='footer-item footer-three'></div>
    </div>
```

```css
.footer {
  display: flex;
  justify-content: space-between;
}

.footer-item {
  border: 1px solid white;
  background-color: lightblue;
  height: 200px;
  flex: 1;   /* stretch widths of .footer-items to fill .footer */ 
}
```

it is common for a webpage to have some boxes with fixed-widths and some that flex..

```css
.footer-one,
.footer-three {
  background-color: blue;
  flex: initial;
  width: 300px; /* this would be ignored if we didn't reapply the default value of flex: initial */
  /* items with flex initial will not grow more than their explicit width, but will shrink if there is nothing else left to shrink */
}
```

this is a pretty common layout, and not just for footers, for example many websites have a fixed-width sidebar and a flexible content block containing the main text



## Media queries

we can set up a flexbox of multiple items to be organized **in a row** for desktop viewing and **in a column** when a mobile device is being used

by specifying a **screen width** below wich we will **switch from** `flex-direction: row` to `flex-direction: column`

so, say we have..

```html
<div class="container">
    <div class="item">Content Content Content Content Content Content Content Content Content </div>
    <div class="item">More More More More More More More More More More More More More More More More More More More More</div>
    <div class="item">Less Less Less Less Less Less Less Less Less Less Less </div>
</div>
```

```css
.container {
    display: flex;
    gap: 32px;
    border: 10px solid red;
}

.item {
    flex: 1;
    background-color: green;
}

@media (max-width: 750px) { /* below 750px window width --> flex-direction is column */ 
    .container {
        flex-direction: column;
    }
}
```



