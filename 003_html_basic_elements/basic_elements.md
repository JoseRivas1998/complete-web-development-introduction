# Basic Elements

Today we will be talking about some of the basic HTML elements that make up a web page. 

## HTML Template

In the first lesson, we looked at some sample HTML. That HTML, along with basically all HTML files will start from the same boilerplate code:

```html
<!DOCTYPE html>
<html>

<head>
    <title></title>
</head>

<body>

</body>

</html>
```

It may be useful to create a file called `template.html`, and duplicating and renaming the file as you want to create more HTML files to save time. 

Alternatively, in VS Code, when you create an HTML file, you could type `html:5` and as you see it pop up, hit enter, and it will also produce the following boilerplate:

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>

<body>

</body>

</html>
```

There may be some new stuff on this boilerplate but it is fine to keep.

The HTML elements we will be looking at today are all contained between the `<body>` tag.

## Headings

When designing web pages, it may be useful to be able to split your web page into multiple sections and subsections. You can denote these sections using heading tags. Headings are defined using `<h1>`, `<h2>`, `<h3>`, and so on. The number after the `h` represents the heading level, with `1` being the highest level. As the number after the `h` increases, the size of the heading decreases. Try out this code:

```html

<h1>This is a large heading!</h1>
<h2>This is a smaller heading!</h2>
<h3>This is an even smaller heading!</h3>
<h4>This is basically just bold text!</h4>
<h5>This is probably further than you will go with headings!</h5>
```

As you can see, the headings got smaller and smaller. By the time you reach `<h4>`, the heading starts to just look like bold text, and is even smaller than regular text beyond that. You will likely only really need the first three headings. Usually `<h1>` is used for page titles, `<h2>` is used for section titles, and `<h3>` is used for subsections. However, you are free to use headings in whatever way suites your own website.

## Paragraphs

Although plain text could always be written directly into the `<body>` tag, and any tag, usually text is wrapped in a paragraph. A paragraph is denoted with the `<p>` tag. Using a paragraph will separate the text from the elements around it and also include some spacing around the text. It is also a useful way to separate different blocks of text. You can see that in action with the following code:

```html
<p>This text is insde of a paragraph tag!</p>

<p>This text is inside of another paragraph tag.</p>
```

The text is separated off with some space in between.

### Lorem Ipsum

Sometimes, you want to lay out a web page and you want to figure out the spacing for text but don't necessarily know what the text is going to be yet. For this, Lorem Ipsum text is used. You can read more about it [here](https://www.lipsum.com/), and even use that same web page to generate Lorem Ipsum. In VS Code, you can simply type `lorem` and hit enter and that will generate a few sentences of Lorem Ipsum:

```html
<p>
    Lorem ipsum dolor sit, amet consectetur adipisicing elit. Sint fugit alias, assumenda libero corporis aliquam tempore doloremque neque, nobis error labore. Odit quisquam mollitia molestiae adipisci beatae exercitationem voluptate eius?
</p>
```

You can also control exactly how much Lorem Ipsum is generated using Emmet syntax built into VS Code. Simply type `lorem5`, or however many words you would like to generate, and hit tab. Doing so will insert that many words into your file:

```html
<p>Lorem ipsum dolor sit amet.</p>
```

## Break Rule

If you remember from the first lecture, most white space in HTML is completely ignored. This includes newlines. So, if you wanted to have text appear on multiple lines, but not necessarily as separate paragraphs, the following code will not work:

```html
<p>
    Hands, do what you're bid:
    Bring the balloon of the mind
    That bellies and drags in the wind
    Into its narrow shed.
</p>
```

In order for that to work, you would need a break rule element. A break rule will force all content after the element to be rendered on the next line. It is defined by the self closing `<br>` tag. Here is is in action:

```html
<p>
    Hands, do what you're bid:<br>
    Bring the balloon of the mind<br>
    That bellies and drags in the wind<br>
    Into its narrow shed.<br>
</p>
```

As you can see, the text now appears correctly. An important thing to keep in mind is that the spacing here is completely arbitrary. It is only a stylistic choice to always put the `<br>` at the end of the line. Also, keep in mind that `<br/>` would have also worked exactly the same, and you might run into HTML code that puts the `/` at the end of self closing tags.

## Horizontal Rule

The horizontal rule element places a horizontal line between all the elements before it and all the elements after. It extends across its entire container. It can be used to further separate portions of a web page. To create a horizontal rule, use the `<hr>` tag:

```html
<p>Before the horizontal rule.</p>

<hr>

<p>After the horizontal rule.</p>
```

## Text Formatting 

The last set of basic elements are used to format text. By formatting text, I mean making text bold, italic, and super/sub scripts.

### Bold Text

To create bold text, you can use either the `<strong>` or `<b>` tags, I prefer to use the `<strong>` tag:

```html
<p>
    Using the strong tag creates <strong>bold</strong> text!
</p>
```

Notice the `<strong>` tag is nested in the `<p>` tag. It can also be stated that the `<strong>` tag is an inline tag, since it is not blocked off like a heading or paragraph tag would be.

### Italic Text

Italic text is made using either the `<em>` or the `<i>` tag. My preference is the `<em>` tag:

```html
<p>
    Using the em tag creates <em>italic</em> text!
</p>
```

### Nesting Inline Tags

If, for example, you wanted to make text that was both bold and italic, you would do something like this:

```html
<p>
    <strong><em>This text is very important.</em></strong>
</p>
```

Now, this is where it is very important to not only close each tag correctly, but it is also bad practice to not close tags in the same order they are opened. This is where browsers can sometimes not be helpful in terms of finding bad code. For example, the following HTML code is technically invalid, but the browser will still render it the same as before:

```html
<p>
    <strong><em>The tags are closed wrong!</strong></em>
</p>
```

What is important to keep in mind is that if you open a tag inside of another tag, a hierarchy is created. In this example, the `<em>` tag belongs to, or is a child of `<strong>` tag. And the `<strong>` tag is a child of the `<p>`. It does not makes sense to close a child tag before its parent. This is why in the valid HTML, the `<em>` is closed before the `<strong>`.

### Subscripts and Superscripts

There are many reasons to create subscripts and superscripts on a web page. They are defined using the `<sub>` and `<sup>` tags respectively:

```html
<p>
    This is some text<sub>with a subscript.</sub>
</p>

<p>
    This is some text<sup>with a superscript.</sup>
</p>
```

## Comments

Sometimes, you want to leave notes inside your code but do not want them to appear on the web page. For that, comments are used. In HTML, you create a comment by using `<!-- Your comment here! -->` and it will not at all affect the actual web page.

## Conclusion

These basic HTML elements are a small portion of the many HTML elements that there are to use. However, with just these basic elements you can start to see how web pages are mostly built and maybe even start building your own. In the next lesson, we will explore HTML attributes and how to use them to create links and images on your web page.

## Challenge

Now that you have learned some basic HTML elements, try to make a web page of your own! Here is your challenge:
* Make a web page of your favourite song or poem. 
* Make sure that the formatting is correct, and broken up into stanzas properly. 
* Use separate appropriate headings to denote the title and artist. 
* Make the last word of each line **bold**.
* Make each rhyming word *italic*. 
