# Milestone 3 - Forms, Lists, and Tables

### Forms

Forms are used to collect user input. The submitted values can be sent to a server for processing. Forms can any number of input elements.

#### Types of Inputs

1. Text
2. Email
3. Password
4. Checkbox
5. Radio
6. Submit

```html
<form action="/submit" method="post">
  <label for="name">Enter your Name:</label>
  <input type="text" id="name" name="name" />

  <label for="email">Enter your Email:</label>
  <input type="email" id="email" name="email" />

  <button type="submit">Submit</button>
</form>
```

### Lists

HTML has three types of lists:

1. Unordered lists (`<ul>`) - Attributes - types: disc, circle, square
2. Ordered lists (`<ol>`) - Attributes - type: 1, A, a, I, i, start, reversed
3. Description lists (`<dl>`)

```html
<ul>
  <li>1</li>
  <li>2</li>
</ul>

<ol>
  <li>1</li>
  <li>2</li>
</ol>

<dl>
  <dt>Term</dt>
  <dd>Description about the term</dd>
</dl>
```

### Tables

HTML tables are used to display data in rows and columns.

#### Attributes

1. `<table>` - Creates a table
2. `<tr>` - Creates a row
3. `<th>` - Creates a header cell
4. `<td>` - Creates a data cell
5. `<thead>` - Groups header content
6. `<tbody>` - Groups body content
7. `<tfoot>` - Groups footer content
8. `colspan` - if a column has to span for more than one column
9. `rowspan` - if a row has to span for more than one row

_`Nested tables` are also possible._

```html
<table>
  <thead>
    <tr>
      <th>1</th>
      <th>2</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>1,1</td>
      <td>1,2</td>
    </tr>
  </tbody>
</table>
```

## Accessibility

Web accessibility ensures that websites are usable by people with disabilities. Some key practices include:

- Using semantic HTML elements
- Providing alternative text for images
- Ensuring keyboard navigation
- Using ARIA (Accessible Rich Internet Applications) attributes for elements

```html
<img src="image.jpg" alt="About the image" />

<button aria-label="Close" onclick="close()">Close</button>

<!--  or  -->

<button aria-labelledby="Close button" onclick="close()">Close</button>
```

_`Using getElementById() to get the element by its ID and set the ARIA_LABEL`_

```html
<p id="close">Close</p>

<script>
  const closeButton = document.getElementById("close");
  closeButton.addEventListener("click", function () {
    closeButton.setAttribute("aria-label", "close button");
  });
</script>
```

## SEO (Search Engine Optimization)

SEO involves optimizing your web pages to make them reach a high position in search results. Some HTML-related SEO practices include:

- Using descriptive title tags
- Using header tags (h1 - h6) correctly
- Atmost one h1 tag per page
- Providing alt text for images
- Creating a sitemap
- Server-side rendering for better SEO
- You can use the `meta` tag to provide description about your content.
- Using semantic HTML to tell search engines about the structure of your content

```html
<head>
  <title>Hello</title>
  <meta name="description" content="Description about your page content" />
</head>
```

## HTML APIs

HTML5 introduced several APIs that allow for more interactive web experiences. Some popular ones include:

- Geolocation API
- Drag and Drop API
- Web Storage API
- Canvas and WebGL

**Geolocation API:**

```html
<button onclick="getLocation()">Get Location</button>

<script>
  function getLocation() {
    if (navigator.geolocation) {
      navigator.geolocation.getCurrentPosition(showPosition);
    } else {
      console.log("Geolocation is not supported by this browser.");
    }
  }

  function showPosition(position) {
    console.log(
      "Latitude: " +
        position.coords.latitude +
        " Longitude: " +
        position.coords.longitude
    );
  }
</script>
```

**Drag and Drop API:**

#### An example of dropping a file and displaying its name

```javascript
document.addEventListener("DOMContentLoaded", function () {
  alert("DOM loaded");
  const draggable = document.getElementById("draggable");

  const dropLocation = document.getElementById("drop");

  draggable.addEventListener("dragstart", function (event) {
    dropLocation.classList.add("opacity-80");
  });

  dropLocation.addEventListener("dragover", function (event) {
    event.preventDefault();
  });

  draggable.addEventListener("dragend", function (event) {
    dropLocation.classList.remove("opacity-80");
  });

  dropLocation.addEventListener("drop", function (e) {
    e.preventDefault();
    const file = e.dataTransfer.files[0];

    const p = document.createElement("p");

    const body = document.body;

    p.textContent = file.name;

    body.appendChild(p);
  });
});
```

## HTML Comments

HTML comments are used to insert notes in the HTML source code. They are not displayed in the browser.

```html
<!-- This is a comment -->

<!--
 This is a
 multi-line comment
-->
```
