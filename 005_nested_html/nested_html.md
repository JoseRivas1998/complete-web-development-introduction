# Nested HTML

Inside of HTML content tags, you can include simple text, or you could include more HTML elements. When you have an HTML element inside of another HTML element, it is called nesting. Nesting is a larger concept that we will run into a lot in this course. 

## Nesting Code

Whenever you are nesting code, you are adding a sort of hierarchical structure to your code. This is often necessary, and in HTML, it is completely unavoidable. Because of this, it is important to practice clean coding when writing HTML. Clean code is a huge topic across all of software engineering, and we will see the ideas of clean code pop up again and again. For now, let's take a look at some nested HTML code:

```html
<body>

    <h1>Page Title</h1>

    <a href="#">
        <h2>This is a clickable header!</h1>
    </a>

</body>
```

So, the `<h1>` and `<a>` tags are said to be nested in the `<body>` tag, and the `<h2>` is nested in the `<a>`. The tabbing of the code may not make a difference to the browser, but it allows us to see the hierarchy much more clearly and understand which elements are nested inside which other elements. Here is the same code without the tabbing:

```html
<body>

<h1>Page Title</h1>

<a href="#">
<h2>This is a clickable header!</h1>
</a>

</body>
```

As you can see, it's not as clear anymore, and it can even be taken to an extreme and all be put on one line:

```html
<body><h1>Page Title</h1><a href="#"><h2>This is a clickable header!</h1></a></body>
```

To the browser, all of these code segments will produce an identical result. However, the first one is much cleaner, making it easier to read and maintain. Perhaps in this example may seem like all three segments are easy enough to deal with, but as HTML gets more complex, it gets much more deeply nested, making this clean coding much more important. Writing clean code from the beginning will save you a lot of headache and make finding or preventing errors and bugs much easier.

## Lists

Some HTML elements can only really exist as nested elements. I will be talking about several of them throughout this course, but mostly one or two at a time. The first of these elements is a list. Well, there's two types of lists, unordered and ordered. Unordered lists allow you to arrange items into bullet points, and ordered lists arrange them with ascending numbers.

### Unordered Lists

The unordered list HTML element is defined by the `<ul>` tag. This is a content tag. Each item in the list is a nested HTML element, called this list item element. The list item element is defined by the `<li>` tag. The only content that is in an unordered list should be nested list item elements. Here is an example:

```html
<h3>Ingredients:</h3>
<ul>
    <li>5 tbsp salted butter, plus extra for the tin</li>
    <li>250g crunchy peanut butter</li>
    <li>8 tbsp strawberry or raspberry jam</li>
    <li>80g light brown soft sugar</li>
    <li>200g rolled oats</li>
</ul>
```

As you can see, the list items are arranged into a list with bullet points. Always remember to keep in mind the tabbing, the `<li>` tags are inside the `<ul>` tag, and are tabbed over. If a tag simply contains a short amount of text, it is often opened and closed on the same line, as you can see with the `<li>` tags.

### Ordered Lists

The ordered list element is defined by the `<ol>` tag. It is created basically the same was as an unordered list:

```html
<h3>My Favorite Drinks</h3>
<ol>
    <li>Water</li>
    <li>Soda</li>
    <li>Iced Tea</li>
    <li>Coffee</li>
</ol>
```

The difference here is that the browser renders each element with a number in ascending order. The count by default starts at one, but can be changed with the `start` attribute:

```html
<h3>My Favorite Drinks</h3>
<ol start="50">
    <li>Water</li>
    <li>Soda</li>
    <li>Iced Tea</li>
    <li>Coffee</li>
</ol>
```
## Conclusion

When writing HTML, nesting is an inevitability. Learning how to write clean code early will help build the discipline to always write clean code in the future. With the ability to nest code, elements such as the unordered list and ordered list are made possible. However, any element can have nested elements, and this will be used to make more complex web pages in the future. 

## Challenge

1. Write a web site with three cooking recipes.
2. Each recipe should be on its own web page.
3. Include a navigation that goes to each page.
4. On each recipe, use an unordered list for the ingredients.
5. Use an ordered list for the steps.
6. Make sure to include images!
