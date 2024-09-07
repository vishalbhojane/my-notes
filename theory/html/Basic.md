## What does a `doctype` do?

Short for 'Document Type Declaration'
Tells the web browser which version of HTML (or XML) the document is written in

```html
<!DOCTYPE html>
```

---
## How do you serve a page with content in multiple languages?

Use the Correct HTML Language Declaration

```html
<html lang="en">
```

You can also use the lang attribute on individual elements

```html
<p lang="fr">Bonjour le monde</p>
<p lang="es">Hola mundo</p>
```

You can create language specific pages

Include the meta tag for specifying character encoding

```html
<meta charset="UTF-8">
```

Implement Hreflang for Multilingual Pages

```html
<link rel="alternate" href="https://example.com/en" hreflang="en">
<link rel="alternate" href="https://example.com/fr" hreflang="fr">
<link rel="alternate" href="https://example.com/es" hreflang="es">
```

Right-to-Left (RTL) Languages

```html
<html lang="ar" dir="rtl">
```

---
## What kind of things must you be wary of when designing or developing for multilingual sites?

#### Text Length Variations
Translated content often varies in length. For example, English text is generally shorter than languages like German or French
**Solution**: Responsive UI
#### Font and Character Support
Different languages may use unique characters or scripts (e.g., Chinese, Cyrillic, Arabic)
**Solution**: Use fonts that support a wide range of character
#### Right-to-Left (RTL) Language Support
Languages like Arabic and Hebrew are written from right to left
#### Content Localization vs. Translation
Simply translating text doesn’t always provide an optimal user experience
**Solution**: Use content localization, where translations are adjusted for regional preferences, idioms, or context
#### Performance and Load Time
Multilingual sites often include more content, which can increase load times, especially if the site dynamically loads different language versions
**Solution**: Optimize images, scripts, and other assets for fast loading, CDN, Lazy loading

---
## What are data- attributes good for?

`data-` attributes in HTML allow you to embed custom data directly into HTML elements without affecting the visual display or the functionality of the page itself

#### Embedding Custom Data Without Affecting HTML Validation
`data-` attributes allow you to attach custom data to HTML elements while keeping the document valid according to HTML specifications

```html
<div data-product-id="12345" data-user-status="active">Product Name</div>
```
#### JavaScript Interactivity
JavaScript can easily access and manipulate the data stored in data- attributes. This is useful when you need to pass information from the HTML layer to the JavaScript laye

```js
const productId = document.querySelector('div').dataset.productId;
console.log(productId); // Outputs: 12345
```

## Consider HTML5 as an open web platform. What are the building blocks of HTML5?

HTML5 is the latest standard of HTML, Here are the main building blocks of HTML5
#### New Semantic Elements
`<header>`: Defines the header section of a page or a section.
`<footer>`: Defines the footer section of a page or a section.
`<article>`: Defines independent, self-contained content.
`<section>`: Represents a thematic grouping of content.
`<nav>`: Represents navigation links.
`<aside>`: Defines content that is related but separate from the main content.
`<main>`: Specifies the main content of a document.
`<figure>` and `<figcaption>`: Represents self-contained content like images with captions

#### New Form Controls and Attributes
###### New Input Types
`<input type="email">`, `<input type="url">`, `<input type="tel">`, `<input type="date">`, `<input type="number">`, `<input type="range">`, `<input type="search">`, etc
###### New Attributes
`placeholder`, `autofocus`, `required`, `pattern`, `min`, `max`, `step`, etc
###### Form Elements
`<datalist>`: Provides an autocomplete feature for input fields.
`<output>`: Represents the result of a calculation or action.
`<progress>`: Displays the progress of a task
#### Multimedia Elements
**`<audio>`**: Embeds audio files directly in a webpage.
**`<video>`**: Embeds video files with built-in controls.
**`<track>`**: Adds text tracks (such as subtitles or captions) to video and audio content.
**`<canvas>`**: A versatile drawing surface for rendering graphics and animations via JavaScript.
**`<svg>`**: Supports scalable vector graphics natively in HTML, allowing for responsive and resolution-independent images
#### APIs for Web Applications
Geolocation API, localStorage and sessionStorage
#### Responsive Web Design Features
- **Media Queries** (in combination with CSS3): Enable different styles for different screen sizes, orientations, and resolutions.
- **Viewport Meta Tag**: Controls the layout on mobile devices

```html
<meta name="viewport" content="width=device-width, initial-scale=1.0">
```

## Why is it generally a good idea to position CSS `<link>`s between `<head></head>` and JS `<script>`s just before `</body>`? Do you know any exceptions?

Best Practice: Place CSS `<link>` tags in the `<head>` to ensure styles are applied as soon as possible, and place JavaScript `<script>` tags just before `</body>` to avoid blocking content rendering.

Exceptions: Critical JavaScript or CSS that must be loaded early can be placed in the `<head>`, often with mechanisms like async or defer to avoid blocking the rendering process.

## Why you would use a `srcset` attribute in an image tag? Explain the process the browser uses when evaluating the content of this attribute

The `srcset` attribute in an `<img>` tag is used for **responsive images**, allowing the browser to choose the most appropriate image to load based on the device's screen size, resolution

Example of `srcset`
```html
<img src="image-small.jpg"
     srcset="image-small.jpg 480w, 
             image-medium.jpg 800w, 
             image-large.jpg 1200w"
     sizes="(max-width: 600px) 480px, 
            (max-width: 900px) 800px, 
            1200px"
     alt="A beautiful scenery">
```

Example of `srcset` with Pixel Density
```html
<img src="image.jpg"
	 srcset="image.jpg 1x,
			 image@2x.jpg 2x"
	alt="An image optimized for high-density screens">
```

## Have you used different HTML templating languages before?

#### EJS (Embedded JavaScript)

Description: EJS is a simple templating language that lets you embed JavaScript code into HTML. It's commonly used with Node.js applications.

Features: Embeds JavaScript code directly within HTML using <%= %> or <%- %> for unescaped output.
Supports includes and partials for modularity

```ejs
<h1><%= title %></h1>
<ul>
  <% items.forEach(function(item){ %>
    <li><%= item %></li>
  <% }); %>
</ul>

```

## Differences Between Canvas and SVG

| Feature            | **Canvas**                                               | **SVG**                                                     |
| ------------------ | -------------------------------------------------------- | ----------------------------------------------------------- |
| **Graphics Type**  | Raster (pixel-based)                                     | Vector (shape-based)                                        |
| **Rendering Mode** | Immediate mode (bitmap)                                  | Retained mode (DOM-based)                                   |
| **Scalability**    | Loses quality when scaled (pixelation)                   | Scales without loss of quality (resolution-independent)     |
| **Interactivity**  | No built-in DOM interaction; needs manual event handling | DOM elements that can be styled, animated, and manipulated  |
| **Performance**    | Better for dynamic, complex, real-time graphics          | Better for static or less dynamic graphics                  |
| **Manipulation**   | Objects can’t be manipulated after drawing               | Individual elements can be manipulated, animated, or styled |
| **File Size**      | Bitmap size can be large (depends on resolution)         | Typically smaller file sizes for simple graphics            |
| **Use Cases**      | Games, real-time rendering, animations                   | Icons, logos, diagrams, charts, and scalable UI elements    |
#### When to Use Canvas:
When rendering complex animations, real-time data visualizations, or game development where performance is critical.
When dealing with a large number of objects that change frequently and require fast redrawing.
#### When to Use SVG:
When creating scalable graphics such as icons, logos, or illustrations that need to look sharp at any resolution.
When you need interactive elements (e.g., charts, graphs) that can be styled or manipulated individually with CSS and JavaScript.

## What are empty elements in HTML?

Empty elements (also known as self-closing or void elements) are HTML tags that do not have any content between an opening and closing tag

```html
<img src="logo.png" alt="Site Logo" width="100" height="50">

<input type="text" name="username" placeholder="Enter your username">

Line one<br>
Line two

<hr>

<meta charset="UTF-8">
<meta name="description" content="A brief description of the webpage">

<link rel="stylesheet" href="styles.css">
```
