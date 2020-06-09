# HTML Hello World

Welcome to this introduction to web development course! Here, you will learn the basics that will allow you to dive right into web development. There are many aspects to web development, as well as several languages and technologies you need to learn. The first language you will need to learn in HTML.

## HTML

HTML stands for Hyper Text Markup Language. An HTML document is used to create web pages by describing their structure. A web browser parses HTML code and renders a web page. HTML describes web pages using elements. An element tells the browser how to render a certain part of a website, for example, an element can be a heading, paragraph, link, image, and so on. 

Let's take a look at some basic HTML code:

`example_01.html`:
```html
<!DOCTYPE html>
<html>

<head>
    <title>Title of Document!</title>
</head>

<body>
    <h1>Hello world!</h1>
    <p>This is my first web page!</p>
</body>

</html>
```

In the code, there are several elements, some elements are even inside of other elements. This is called nesting. In most cases, when code is nested, an indentation is added. The browser itself does not really care about indentation or even the separate lines. In fact, the code can be written all on a single line with basically no spacing and the result would be the same. We only write code with newlines and indentations to make the code more readable to human beings. It is important to make code as readable as possible, this is called writing clean code. Clean code makes code scalable and easy to manage. 

### Explanation
1. `<!DOCTYPE html>` This tells the browser that the HTML code will be in the latest version of HTML: HTML5.
2. `<html>` This is the root element for the web page, all HTML code will be inside the `<html>` tag.
3. `<head>` Contains all the metadata for a web page. Metadata is information that describes the document but does not necessarily get displayed to the user. This can include a page description, the language the page is written in, and several other details about the page.
4. `<title>` This is the main title of the web page, it is what is shown at the top of the browser in the tab for the page.
5. `<body>` This is where the main content of the web page is shown, only elements inside the `<body>` tag will be rendered in the document.
6. `<h1>` Defines a large heading.
7. `<p>` Defines a paragraph.

## HTML Elements

To define an HTML element, something called a tag is used. There are two main types of tags. 

### Content Tags

A content tag defines an element that will contain other elements, or just plain text inside of it. They have the following format:

```html
<tag>CONTENT</tag>
```

In this example, `<tag>` is the starting tag, the `tag` defines what kind of element the tag is describing. The `CONTENT` is what will be contained within the element. This can be simple plain text, or more elements. Finally, the `</tag>` is the end tag, or closing tag. It defines where the element ends. It is important to always include a starting tag, and an ending tag for all content tags or else the web page may not look right. 

### Self Closing Tags

Consider the following HTML code:

```html
<!DOCTYPE html>
<html>

<head>
    <title>Title of Document!</title>
</head>

<body>
    This will all appear
    on the same line!<br>
    But this is on a new line!
</body>

</html>
```

The `<br>` tag defines a break rule in the web page, meaning the content after the `<br>` will be rendered on a new line. The break rule is known as a Void Element, because it does not contain any content. Void Elements are defined by Self Closing Tags, which only have a single start tag. Self closing tags usually have a `/` character, so `<br />` is also a valid tag, but does the exact same thing. 

## Writing HTML Code

Writing HTML code is simple, you don't need any special tools in order to get started, just a text editor. On Windows, you can use Notepad, and on Mac you can use TextEdit. Open up a text editor for the operating system you are using, and copy the `example_01.html` code into the editor and save it with the same name. I recommend creating a folder for each lecture to hold each HTML sample. Now, you can simply open the HTML file with your web browser and see your code. 

This is less than ideal, there are special text editors that have more features, such as code completion, syntax highlighting, and many other tools to make coding much easier. A text editor that I would recommend the most is [Visual Studio Code](https://code.visualstudio.com/). VS Code is a free and open source editor made by Microsoft. I would also recommend installing the Live Server extension, a guide to do that can be found here: https://www.youtube.com/watch?v=WzE0yqwbdgU

## Conclusion

In this lecture, you wrote your first HTML document! We talked about the basics of what an HTML is made out of, elements, and how to use tags to define elements. In the next lecture, I will be going over a tool known as `Git` which you should be using throughout the rest of this course.
