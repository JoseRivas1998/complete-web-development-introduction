# Intro to CSS

The web pages that we have built so far have been fairly boring. All the text is completely left aligned, with few exceptions, and the websites are completely black and white. The font of the text is at the mercy of the default font for your web browser, which usually ends up being Times New Roman. Clearly, we should be able to do better. 

In the early days, the formatting problem was attempted to be solved through HTML, they started adding tags and attributes that would change the formatting of the page. There would be a tag to change text color, or to center on the page, and as we saw in the last texture, there were attributes to set things like borders on elements. 

This violated the purpose of HTML, which is to define the structure of a web page, not the formatting. This strongly coupled structure and formatting and made working on websites much harder. Because of this, Cascading Style Sheet, CSS, was invented.

## Why CSS

A well renowned software engineer and author, Robert C. Martin defined a coding practice known as the Single Responsibility Principle. In this, he says that a code module should only have one responsibility, further defined as only have one reason to change. 

So, if the structure of a web page needs to change, it is the HTML that should be changed. If the formatting of a web page needs to be changed, it should be something else. That something else is CSS. With the addition of CSS, the formatting of web pages is decoupled from their structure. 

There are many places to place CSS styles in a web page, three in particular, and you will likely use all of them. There is a hierarchy how how much each place should be used. In this lecture, they are listed from worst place to put CSS to the best.

## Inline CSS

The first and worst place you can write CSS code is inline with an HTML attribute. Here, CSS code is written as a value of the `style` attribute of the element that the style applies to. Let's say for example I wanted to make a heading that is center aligned on the page, this is how that would be done:

```html
<h1 style="text-align: center;">My First CSS Style!</h1>
```

### CSS Property

The CSS code inside the the `style` tag is called a CSS property. The syntax for a property is as follows:

```css
property-name: value;
```

The `property-name` defines what kind of style is being set, and `value` defines the value for that property. The kind of value given depends on the property, some may be words such as `center` or numerical. Here is an example of using a numerical value for a font size:

```html
<p style="font-size: 24px;">
    Lorem ipsum dolor sit amet.
</p>
```

#### Value Units

Most numerical values come with a unit. In the example above, the unit `px` refers to pixels. This is not the only way to set font size, you can use `pt`, which is for point, as well as other units that will be discussed later. Numbers that define a size of an element without units are generally considered to be invalid CSS, with a single exception: `0`. If a property has a value of zero, then the proper CSS form is to simply write `0` as the value. Notice how there is no space between the number and its unit, this is how all values with units should be written. We will see several properties that contain numerical values that are unitless, however they will likely not have any impact on the size of an element.

#### Multiple Properties

You can add more properties to an element to create a more interesting style. Let's place a `p` tag that is right aligned and red:

```html
<p style="text-align: right; color: red;">
    Lorem, ipsum.
</p>
```

Notice the space between the `;` at the end of the first property. This is entirely optional, but is necessary for clean code formatting. You can probably start to see one of the problems with using inline styles. If you want to add more and more styles, you have to add them horizontally in the tag, making it a lot harder to read, and can obscure the other HTML details of that element. Much worse, having many elements with inline styles will completely obscure the structure of the web page, which is supposed to be the sole responsibility of HTML in the first place. And worst of all, the page formatting and the page structure is still heavily coupled! We might as well not use CSS at all if we are just going to write it all inline with the HTML. There has to be a better way.

## Style Tag

There certainly is a better way, the next best way is to define a `<style>` tag. In a `<style>` tag, CSS code can be written and applies to the whole web page. The common place to put a `<style>` tag is in the head of the document. Here is an example:

```html
<head>
    <style>
        body {
            background-color: aqua;
            font-family: Arial;
        }
    </style>
</head>
```

Woah what's going on here? Is what you may be asking, do not worry, this code shows very well an important part of CSS. A style applied to an element will also apply to all of it's child elements. So, when setting a style for the `body` element, all the elements receive the same style, that being the background color and the font family. A child can of course overwrite its parent's style, which creates a cascading and predictable prioritization of styles, hence the name: *Cascading* Style Sheet. The prioritization also cascades downwards in terms of where the style appears, for example, styles defined in a `style` attribute will always have highest priority.

Let's also take a look at the syntax for the code above, which is known as a rule set. A rule set defines styles for every element that matches a given selector is has this syntax:

```css
selector {
    property-name: value;
    property-name: value;
    ...
}
```

Here, the `...` means, "and so on", because a rule set can contain as many properties as you would like. A `style` tag can also consist of as many rule sets as you want, let's add another rule set to make all `<h2>` tags have indigo text:

```html
<style>
    body {
        background-color: aqua;
        font-family: Arial;
    }

    h2 {
        color: indigo;
    }
</style>
```

The empty line between the rule sets is optional, but I like to have it there because it makes them a bit more readable for me. Also, notice the indentation, always remember to have proper indentation in your code.

### CSS Selector

The selector of a rule set defines how the browser chooses which elements to apply the styles to. 

#### Element Selector

The selectors we used in the above example are both element selectors. Rule sets defined with an element selector apply to every element of that type. For example, let's clean up the inline style for the `<h1>` tag by making all `<h1>` tags center aligned instead of in a attribute. So, remove the `style` attribute from the first `<h1>` tag, so that it looks like this:

```html
<h1>My First CSS Style!</h1>
```

Now, go ahead and add the following rule set to your `<style>` tag:

```css
h1 {
    text-align: center;
}
```

#### Grouping Selector

Now, let's say we actually want all headings to be centered, you may be inclined to do this:

```css
h1 {
    text-align: center;
}

h2 {
    text-align: center;
}

h3 {
    text-align: center;
}

h4 {
    text-align: center;
}
```

This will work of course, but it violates the Don't Repeat Yourself (DRY) principle, and CSS has a tool for this, where you can apply multiple selectors to the same rule set. This is the grouping selector. Let's update our rule set to use this instead:

```css
h1, h2, h3, h4 {
    text-align: center;
}
```

So you can apply many selectors, separated by commas, to a single rule set. That rule set will apply to elements that match any of the selectors. These selectors don't have to be of the same type. 

#### Id Selector

What about our paragraphs? How could we move their styles to the `<style>` tag without applying styles to each other? This is where the `id` selector will come in. So, let's take the first paragraph as an example. If you recall from several lectures ago, any HTML element can be given a `id` attribute that is unique within the web page. Let's give an `id` to the first paragraph and remove the style tag:

```html
<p id="first-paragraph">
    Lorem ipsum dolor sit amet.
</p>
```

And now we can add the following rule set to our `<style>` tag:

```css
#first-paragraph {
    font-size: 24px;
}
```

So here, the syntax for an `id` selector is:

```css
#id
```

So with this, any inline style can and ***should*** converted into an `id` selector. Now we can also clean up the second paragraph with the following code:

```html
<p id="second-paragraph">
    Lorem, ipsum.
</p>
```

```css
#second-paragraph {
    text-align: right;
    color: red;
}
```

#### Class Selector

Now, let's consider the following HTML code:

```html
<p>
    This is a paragraph with a link that is <a href="#" style="color: red">red</a>. The rest of the text is not red.
</p>

<ul>
    <li style="color: red;">Red</li>
    <li>Not Red</li>
    <li>Not Red</li>
    <li style="color: red;">Red</li>
    <li style="color: red;">Red</li>
    <li style="color: red;">Red</li>
    <li>Not Red</li>
</ul>
```

So not great, there are a ton of inline styles applied to random elements. Now, we could use individual id's for each element but then we will be violating the DRY principle quite a bit. Let's use a `class` instead. An element can be given a `class` attribute to group it with elements that will have similar styles. Let's give all the red elements a `class` with the value of `red`:

```html
<p>
    This is a paragraph with a link that is <a href="#" class="red">red</a>. The rest of the text is not red.
</p>

<ul>
    <li class="red">Red</li>
    <li>Not Red</li>
    <li>Not Red</li>
    <li class="red">Red</li>
    <li class="red">Red</li>
    <li class="red">Red</li>
    <li>Not Red</li>
</ul>
```

This took away our styling, so let's put it back by adding the following rule set:

```css
.red {
    color: red
}
```

Here, we are using the class selector in order to apply styles to each element with the class `red`. Now, another thing we can do is use the element class selector to make only certain elements with a class be affected. In this example, we will make the red list items also be bold:

```css
li.red {
    font-weight: bold;
}
```

We can now mix using id's and classes. We can take our second paragraph and change the rule set to this:

```css
#second-paragraph {
    text-align: right;
}
```

And then, we can add the class to the HTML element:

```html
<p id="second-paragraph" class="red">
    Lorem, ipsum.
</p>
```

And since having right aligned text is fairly common, let's move that to a class as well, so remove the `#second-paragraph` rule set entirely and replace it with this:

```css
.right {
    text-align: right;
}
```

But now, the paragraph has lost it's alignment. We can add it back by using the fact that an element can belong to multiple classes. This is done by separating all the classes with spaces in the `class` attribute:

```html
<p class="red right">
    Lorem, ipsum.
</p>
```

This is why class names can't have spaces in them. Id names also cannot have spaces in them. 

We can go a lot deeper with selectors, but we will explore those later on.

## External CSS

So, now we have all of our styling inside of the `<style>` tag like this:

```html
<style>
    body {
        background-color: aqua;
        font-family: Arial;
    }

    h2 {
        color: indigo;
    }

    h1,
    h2,
    h3,
    h4 {
        text-align: center;
    }

    #first-paragraph {
        font-size: 24px;
    }

    .right {
        text-align: right;
    }

    .red {
        color: red
    }

    li.red {
        font-weight: bold;
    }
</style>
```

And while this is great, and separates the structure of the page from the formatting, it still forces us to updated the HTML file when we just want to update the styles. So the two are less coupled, but can still be decoupled further. Let's do this by using an external style sheet. Highlight all of the code between the `<style>` tag, cut it, and paste it to a new file called `styles.css`:

```css
body {
    background-color: aqua;
    font-family: Arial;
}

h2 {
    color: indigo;
}

h1, h2, h3, h4 {
    text-align: center;
}

#first-paragraph {
    font-size: 24px;
}

.right {
    text-align: right;
}

.red {
    color: red
}

li.red {
    font-weight: bold;
}
```

Go ahead and also remove the `<style>` tag when you have saved the `styles.css`. Now, our page has gone back to looking all boring, but that is all right. All we have to do is link our style sheet to the web page by using the following tag in the `<head>`:

```html
<link rel="stylesheet" href="styles.css">
```

The `<link>` tag tells the browser to link together two documents, the `rel` attribute defines what kind of relationship the HTML file has to the other document, and the `href` is the URL or path to that file. Adding this now should have returned the styles to your web page.

So now, if just the formatting needs to be changed, the HTML file can theoretically be completely left alone, and only the CSS file has to change, and, if the structure needs to change, it's the other way around. This s strong decoupling and follows the SRP very well. Another advantage that using external style sheets gives us is the ability to reuse styles. Now, you only really need to write one main style sheet for your entire web site in order to create a consistent look and feel. Page specific style sheets can be added in `<style>` tags, or even in their own separate `.css` files. You can add as many `<link>` tags as you want. 

## Conclusion

With CSS, we can add formatting to our web pages. We talked about how using a separate styling language decouples the web page formatting and structure, adhering to the Single Responsibility Principle. We talked about where we can put CSS, which can be either inline, in a `<stlye>` tag, or in a separate stylesheet. The separate stylesheet is the most desirable. We explored selectors, and using id's and classes to create styles for specific elements, as well as using elements with multiple classes. Next, we will be exploring text formatting as our first deep dive into different CSS properties. 

## Challenge

Your challenge is to update your web site from the last challenge to include CSS styles:

1. Put all your styles in an external CSS file.
2. Make sure that your website has a consistent style, so your pages would have to have at least one main stylesheet.
3. Have the table and the body have different colors to differentiate the web page from the background.
