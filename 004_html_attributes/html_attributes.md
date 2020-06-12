# HTML Attributes

Basic HTML elements as we have seen them are often insufficient in order to create complete websites. Many elements need additional information other than just the content within the tag. To accomplish this, attributes. 

## Attributes

Most of the time, an attribute is represented by a **key value pair**. Key value pairs are an incredibly important concept in programming, basically, the idea is that a certain value is given an identifier, known as the key. We will explore this idea further in the future. For now, as far as HTML attributes are concerned, the key describes what kind of attribute is being set, and the value is the data stored inside the attribute.

HTML attributes are defined with the following syntax:

```
key="value"
```

The following is also valid: 

```
key='value'
```

Basically, you can choose to either use double quotes or single quotes to enclose the value. I will use double quotes for attributes throughout the course. Like tags, quotes are considered to have starting, or opening quotes, and ending, or closing quotes. Whenever there is an opening quote, there must be an accompanying closing quote somewhere after. The text between the quotes is considered the value of the attribute. 

### Attribute Lists

Many elements that uses attributes will have more than one attribute associated with it. These are defined with attribute lists. An attribute list is created with either of the the following syntax:

1. 
    ```
    <empty>
    ```
2. 
    ```
    <attribute>
    ```
3. 
    ```
    <attribute> <attribute-list>
    ```

This may look scary, but it's just saying that an attribute list is a space separated string of attributes that can have zero to many attributes. So a tag can have zero, one, two, or one thousand attributes by the way the attribute list is defined. Also, keep in mind that attribute lists are in no particular order.

### Attributes in Tags

Now, finally, we can look at the final syntax for an HTML tag that includes attributes. For content tags, the attribute list only goes in the opening tag, like so:

```html
<tag [attribute-list]>CONTENT</tag>
```

Keep in mind the space between the tag name and the attribute list is how the browser tells them apart so make sure not to forget it. Attribute lists can also be added to self closing tags like so:

```html
<tag [attribute-list]>
<tag [attribute-list] />
```

I included examples with and without the slash, which remains optional with self closing tags. 

Let's take a look at attributes in action:

```html
<h1 id="page-title">Fun with Attributes</h1>
```

Now adding this attribute did not do much to the content of the web page, but later on with links we can make use of it. 

### Quotes in Attribute Value

Before moving on, due to the way computers process text, having quotes inside the value of an attribute can be a problem. Consider the following code:

```html
<h1 id="This name has "quotes" in it">Heading</h1>
```

As you can tell by syntax highlighting, something about this is quite off. This is because after an opening quote, the computer only looks for the next quote to be the closing quote. So in this case, by the time the value gets to the `quotes` part, the value had already been closed. There are different ways of fixing this issue, the first being simply using single quotes for the value instead:

```html
<h1 id='This name has "quotes" in it'>Heading</h1>
```

Here, since the value is opened with a single quote, it must be closed with a single quote, so the double quotes in the value are not considered. A similar strategy can be used when using single quotes:

```html
<h1 id='Jose's website'>Heading</h1>
```

Would become:

```html
<h1 id="Jose's website">Heading</h1>
```

Solving this problem this way works in most cases but has two major problems. First of all, doing this would mean that single quotes and double quotes will be used seemingly randomly through your HTML and it's generally good coding practice to always use on or the other for all attributes in order for your code to have consistency. The other issue arises if you need to use both single quotes and double quotes inside your value. To fix this, the quotes could be represented using an HTML entity instead. HTML entities are defined with the following syntax:

```html
&[entity];
```

The `[entity]` is either the name of the entity, or a numerical code to represent it. Every character actually has an HTML entity that can be used. For double quotes, you would use `&quot;`, and for single quotes you would use `&apos;`. So here are the two examples from before using HTML entities instead:

```html
<h1 id="This name has &quot;quotes&quot; in it">Heading</h1>
<h1 id='Jose&apos;s website'>Heading</h1>
```

Now it looks correct! Of course, we are still mixing using single quotes and double quotes, but it is just to show both uses.

HTML entities are incredibly useful, especially if you need to include special characters in your web page, you can learn more about them at [w3schools](https://www.w3schools.com/html/html_entities.asp).

## Links

Now that we know about attributes, we can now create links on our web page! Links are basically what make the internet the vast network that we all know and love. With links, you can start making web sites that are made up of multiple pages. Links are created using the anchor element. An anchor element can link you to a different part of a web page, to another page on the same website, or to another website entirely. Anchor elements are defined using the `<a>` tag, and the destination of the link is defined with the `href` attribute. `href` stands for Hypertext Reference. Let's take a look at an example in a file called `index.html`:

```html
<h1 id="page-title">Fun with Attributes</h1>
<h2 id="long-section">Look at this section!</h2>

<p>
    lorem5000
</p>

<h2 id="after-long-section">This section is after the long section!</h2>
```

To keep the file shorter, I left the emmet abbreviation, when doing this on your own, make sure to actually include a large amount of lorem text so that the page scrolls. Now, let's use an anchor tag after the title to skip down after the long section:

```html
<a href="#after-long-section">Skip Long Section!</a>
```

So, if the href starts with `#`, the link will scroll the page to the element that has an `id` attribute that matches the text after the `#`. Putting just `#`, or an `id` that could not be found on the page, will scroll to the top of the page. Another note is that `id`'s on the same web page must all be unique, and we will explore them further later on. The content inside the anchor tag will be whatever the user should click on to trigger the link. This is usually text, but does not necessarily have to be. It can even be complex HTML to create a thumbnail + link combo.

### Multi-Page Websites

Most websites you encounter have multiple pages, and anchors are used to navigate between them. Let's create another `html` file named `page2.html` with the following body:

```html
<h1>This is a second page!</h1>
```

Pretty simple, but now, in `index.html`, let's add a link to that page, add the following above the page title:

```html
<a href="page2.html">Go to page 2!</a>
```

Putting the path to a file (using UNIX formatting) will either download the file, or navigate to the web page if it is one. A side note here is that the `index.html` has that name because it is the home page of the web site. Moreover, if you just give a folder name to the URL bar or in a link, the `index.html` file will be rendered on the page. This behavior may vary depending on your web server but it is generally true. 

Generally, pages should always have a way to get back to the home page, so add the following to `page2.html`:

```html
<a href="index.html">Go to home!</a>
```

### Linking to an External Site

Being able to link within your own website is great, and allows you to create great complex websites. However, what makes the World Wide Web so special is the ability to link to other websites. This is also achieved with anchors! If the `href` begins with `http`, the link will go to another website, here is an example:

```html
<a href="https://google.com">Go to Google!</a>
```

### Link Target

You can add a `target` attribute to change the behavior of the link. For example, the following code will open in a new tab:

```html
<a href="https://tinycountrygames.com" target="_blank">Go to Tiny Country Games on a new tab!</a>
```

You can see the full list of targets [here](https://www.w3schools.com/tags/att_a_target.asp).

An important note is that using targets on an anchor has fallen mostly out of favour with modern web developers. This is because it affects the default behavoir of web pages and can create an experience the user was not expecting. If the user wanted to open a link in a new tab, they could manually, otherwise, that choice should not be forced on them by the web developer.

## Images

Attributes finally allow us to add images to our web pages! Images are added using the `img` tag. Grab an image from your computer or the internet, make sure the image is saved in the same folder as your `index.html` and add the following code:

```html
<img src="jar-jar.jpg">
```

As you can see, the `img` tag is a self closing tag, and the file path of the image is stored in the `src` (short for: source) attribute. The `src` attribute follows the same rule as the `href` attribute, and images from other websites can be added by including the full link including the `http`, like so:

```html
<img src="https://www.tinycountrygames.com/images/layout/banner.png">
```

This can of course be a problem for several reasons, one of those being that the image on another site can be deleted or moved to another address, breaking your site. It is generally best practice to only have images from your own web pages, but there are many situations you may want to out source an image.

### Alternate Text

If you used autocomplete to create your `img` tag, you may have noticed an `alt` attribute was also added to your image. This is for the alternate text of the image. Alternate text is metadata that is meant to describe in words what an image is. It only renders on the page if an image fails to load properly for whatever reason. However, the main reasons to include alternate text are for search engines to know what an image on a page is, and for accessibility. Accessibility is a huge part of web design, and alternate text is one of many requirements in order to make your website accessible. This is because someone who may rely on an automated web page reader in order to interact on a site would need the reader to be able to say out loud what an image is of. For this, a reader would read out the alternate text. Add alternate text to your images like in this example:

```html
<img src="jar-jar.jpg" alt="A picture of Jar Jar Binks">
<img src="https://www.tinycountrygames.com/images/layout/banner.png" alt="Tiny Country Games Logo">
```

You should keep your alternate text brief.

## Conclusion

HTML attributes are defined by a list of key value pairs. These allow us to create more complicated sites, including links and images. Attributes are incredibly important to be able use, as basically most of the HTML we do from here on will include some sorts of attributes. Next, we will be looking more closely at nesting HTML as well as creating lists. 

## Challenge

Now that you can make more complicated websites, make a website about yourself! 

1. Make the home page a short biography and include an image of yourself.
2. Make a page about your dream job/college, make sure to also include images.
3. Make a page about your favourite movie/artist/game/etc. Include an image of the thing, a brief description and why you like it.
4. Make sure to allow the user to navigate to each page from each page.
