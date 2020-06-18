# Tables

Data in web pages can be organized into tables. This can be very useful for many reasons. Tables in HTML are defined with the `<table>`. Data is organized by rows and columns.

## Rows and Columns

In HTML, a column is a child of a row, and a row is a child of a table. So, you can think of a row as a collection of cells. And a table is a collection of rows. A row is defined by the `<tr>` tag, and a cell is defined by the `<td>` tag. Here is an example:

```html
<h2>Employees</h2>
<table>
    <tr>
        <td>Name</td>
        <td>Phone Number</td>
        <td>Department</td>
    </tr>
    <tr>
        <td>John Doe</td>
        <td>555-123-4567</td>
        <td>Development</td>
    </tr>
    <tr>
        <td>Jane Bar</td>
        <td>555-789-1234</td>
        <td>Management</td>
    </tr>
</table>
```

### Adding a Border

When we are able to properly style our HTML, we will change how we add a border, but for now, let's use the outdated `border` attribute on the table:

```html
<table border="1px">
```

## Table Body

However, this HTML is actually technically wrong. The `<tr>` element should not actually be a child of a `<table>` element directly. If you use inspect element on your web browser, you will see that the browser inserted a `<tbody>` tag. This is because the browser will try to correct invalid HTML. This is convenient but it encourages sloppy code, so let's put our table body into the appropriate `<tbody>` tag:

```html
<table border="1px">
    <tbody>
        <tr>
            <td>Name</td>
            <td>Phone Number</td>
            <td>Department</td>
        </tr>
        <tr>
            <td>John Doe</td>
            <td>555-123-4567</td>
            <td>Development</td>
        </tr>
        <tr>
            <td>Jane Bar</td>
            <td>555-789-1234</td>
            <td>Management</td>
        </tr>
    </tbody>
</table>
```

## Table Heading

Excellent, now our code is valid. But is it correct? Some may be satisfied with how this table looks, but it can be better. It's clear that there are two sections of the table, the labels for the columns, and the data itself. We can make this separation by putting the first row in a `<thead>` tag before the `<tbody>` tag:

```html
<table border="1px">
    <thead>
        <tr>
            <td>Name</td>
            <td>Phone Number</td>
            <td>Department</td>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>John Doe</td>
            <td>555-123-4567</td>
            <td>Development</td>
        </tr>
        <tr>
            <td>Jane Bar</td>
            <td>555-789-1234</td>
            <td>Management</td>
        </tr>
    </tbody>
</table>
```

Now the table has two children, a `<thead>` and a `<tbody>`. However, nothing on the web page actually changed. Most tables have the label cells in bold. Now, we could just wrap the text in each cell with a `<strong>` tag, but there is a better way. A header cell can be defined with a `<th>` tag instead of a `<td>` tag:

```html
<thead>
    <tr>
        <th>Name</th>
        <th>Phone Number</th>
        <th>Department</th>
    </tr>
</thead>
```

Any cell can be a `<th>` or a `<td>`, regardless of whether in a `<thead>` or `<tbody>`.

## Colspan

Table cells can span across multiple columns. This is done using the `colspan` attribute:

```html
<table border="1px">
    <thead>
        <tr>
            <th>Name</th>
            <th colspan="2">Phone Number</th>
            <th>Department</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>John Doe</td>
            <td>555-123-4567</td>
            <td>555-314-456</td>
            <td>Development</td>
        </tr>
        <tr>
            <td>Jane Bar</td>
            <td colspan="2">555-789-1234</td>
            <td>Management</td>
        </tr>
    </tbody>
</table>
```

## Rowspan

You can also have cells span multiple rows using the `rowspan` attribute:

```html
<table border="1px">
    <tbody>
        <tr>
            <th>Name</th>
            <td>John Doe</td>
            <td>Jane Bar</td>
        </tr>
        <tr>
            <th rowspan="2">Phone Number</th>
            <td>555-123-4567</td>
            <td rowspan="2">555-789-1234</td>
        </tr>
        <tr>
            <td>555-314-456</td>
        </tr>
        <tr>
            <th>Department</th>
            <td>Development</td>

            <td>Management</td>
        </tr>
    </tbody>
</table>
```

### Formatting Warning

As you can guess, tables can be a bit challenging to keep track of, especially when using `colspan` and `rowspan`. Because of this, it is incredibly important to practice proper code formatting to make sure your table code is readable and maintainable.

## Tables as Layouts

Tables are great for displaying structured data on your web page. If you think about it, a web page itself can be thought of as structured data. Don't believe me? A lot of web pages back in the day were actually made using a table as the entire layout for the page. Though this style has fallen almost completely out of use, it is still worth while understand to help understand different types of web pages. This is because the `<table>` tag may not be used to create layouts any more, web page layouts can still be thought of as tables. It is simply the method of creating that layout in the HTML is a bit modernized, and `<table>` tags are reserved for just displaying structured data. 

### Two Column Layout

A popular web page layout is a two-column layout. This layout has a navigation column, and a content column. A header row and footer row can sit on top of those. Here is a sample two column layout:

```html
<table border="1">
    <thead>
        <th colspan="2">
            <h1>My Awesome Website</h1>
        </th>
    </thead>
    <tbody>
        <tr>
            <td>
                <ul>
                    <li>
                        <a href="#">Page1</a>
                    </li>
                    <li>
                        <a href="#">Page2</a>
                    </li>
                    <li>
                        <a href="#">Page3</a>
                    </li>
                    <li>
                        <a href="#">Page4</a>
                    </li>
                    <li>
                        <a href="#">Page5</a>
                    </li>
                </ul>
            </td>
            <td>

                <h2>Page Title</h2>
                <p>
                    lorem50
                </p>
            </td>
        </tr>
    </tbody>
    <tfoot>
        <tr>
            <th colspan="2">
                &copy; 2020 Tiny Country Games, All Rights Reserved
            </th>
        </tr>
    </tfoot>
</table>
```

Here, I also included the `<tfoot>` tag for the footer. But as you can see, with just basic HTML, we can already create a structured web page layout. There are, of course, many formatting issues, but it is a good start.

## Conclusion

Tables in HTML nowadays are basically only used for structured data on a web page. These tables can be used in many complex ways, including using different column and row spans. Because of this, the code can get a bit more difficult to understand quickly. Whenever this happens, errors are bound to happen. To mitigate this risk, make sure to keep your HTML clean and tidy to prevent readers from being lost in your table code. Lastly, tables can be used to create web page layouts, and once upon a time, they were by many websites. In the next lesson, we will be starting a new language, CSS. 

## Challenge

You challenge is the same as the challenge from lecture four. Recreate your bio website, but this time:

1. Convert your layout into a two column layout.
2. Use an image as your banner instead of just a heading.
3. Make sure the layout is consistent on each page, including the navigation.
    * A well designed website is a site in which only the content area changes when navigating pages. This creates a consistent experience for the user.
4. Self copyright sign your website by adding a copyright notice as the footer of each page of your website. 
