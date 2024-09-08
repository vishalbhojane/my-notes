HTML events are "things" that happen to HTML elements.
When JavaScript is used in HTML pages, JavaScript can "react" on these events.

#### Here are some examples of HTML events

An HTML web page has finished loading
An HTML input field was changed
An HTML button was clicked

```html
<element event="some JavaScript">
```

```html
<button onclick="document.getElementById('demo').innerHTML = Date()">The time is?</button>
```

#### Common HTML Events

`onchange`, `onclick`, `onmouseover`, `onmouseout`, `onkeydown`, `onload` (The browser has finished loading the page)