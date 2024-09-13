### Question: What does a doctype do?
Answer: The doctype declaration tells the browser which version of HTML the page is using. It ensures that the document is parsed the same way by different browsers. For HTML5, it's simply.

```html
<!DOCTYPE html>
```

### Question: How do you serve a page with content in multiple languages?
Answer: Use the lang attribute on the html tag and specify the language in the content. For example:

```html
<html lang="en">
  <head>
    <meta charset="UTF-8">
  </head>
  <body>
    <p>Hello</p>
    <p lang="es">Hola</p>
  </body>
</html>
```

### Question: What kind of things must you be wary of when designing or developing for multilingual sites?
Answer: Consider text expansion/contraction in different languages, use Unicode encoding, handle right-to-left languages, use appropriate date and number formats, and be mindful of cultural differences in color meanings and imagery.

### Question: What are data- attributes good for?
Answer: Data attributes (data-*) are used to store custom data private to the page or application. They're useful for passing data from HTML to JavaScript without using non-standard attributes or extra properties on the DOM.

### Question: Consider HTML5 as an open web platform. What are the building blocks of HTML5?
Answer: HTML5's building blocks include:
- Semantics: New elements like `<header>, <nav>, <article>`
- Connectivity: WebSockets, Server-sent events
- Offline & Storage: Local storage, IndexedDB
- Multimedia: `<audio>` and `<video>` elements
- 2D/3D graphics: `<canvas>`, WebGL, SVG
- Performance & Integration: Web Workers, History API
- Device Access: Geolocation, Camera API

### Question: Describe the difference between a cookie, sessionStorage and localStorage.
Answer: 
- Cookies: Small data stored by the browser, sent with every HTTP request. Can be set to expire.
- sessionStorage: Stores data for one session (until the browser window is closed).
- localStorage: Stores data with no expiration date, persists even when the browser is closed and reopened.

### Question: Describe the difference between `<script>`, `<script async>` and `<script defer>`.
Answer: 
- `<script>`: Blocks parsing while fetching and executing.
- `<script async>`: Fetches in parallel, executes as soon as it's downloaded.
- `<script defer>`: Fetches in parallel, executes after parsing is complete.

### Question: Why is it generally a good idea to position CSS `<link>`s between <head></head> and JS `<script>`s just before` </body>`? Do you know any exceptions?
Answer: CSS in the head allows for faster rendering as styles are loaded before content. JS at the end of the body prevents blocking page rendering. Exceptions: JS that's critical for initial rendering might be placed in the head.

### Question: What is progressive rendering?
Answer: Progressive rendering is the technique of sequentially rendering parts of a webpage in the browser as they are received from the server. This improves perceived load time for users.

### Question: Why you would use a srcset attribute in an image tag? Explain the process the browser uses when evaluating the content of this attribute.
Answer: srcset allows serving different images based on device capabilities. The browser evaluates the viewport width, device pixel ratio, and available image sizes to choose the most appropriate image.

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

### Question: Have you used different HTML templating languages before?
Answer: Yes, examples include Handlebars, Pug (formerly Jade), and EJS. They offer features like variables, loops, and conditionals to generate HTML dynamically.

### Question: What is the difference between canvas and svg?
Answer: Canvas renders pixel-based graphics and is better for complex scenes with many objects. SVG is vector-based, scalable, and better for illustrations and icons that need to be resolution-independent.

### Question: What are empty elements in HTML?
Answer: Empty elements have no content and don't have a closing tag. Examples include <br>, `<img>, <input>, and <meta>.` They're typically written as self-closing tags in HTML5.