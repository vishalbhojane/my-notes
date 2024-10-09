JavaScript is a programming language initially designed to interact with elements of web pages. Within web browsers, JavaScript consists of three main parts:

- ECMAScript provides the core functionality.
- The [Document Object Model (DOM)](https://www.javascripttutorial.net/javascript-dom/) provides interfaces for interacting with elements on web pages
- The [Browser Object Model (BOM)](https://www.javascripttutorial.net/javascript-bom/) provides the browser API for interacting with the web browser.

JavaScript allows you to add interactivity to a web page. Typically, you use JavaScript with HTML and CSS to enhance a web page’s functionality, such as [validating forms](https://www.javascripttutorial.net/javascript-dom/javascript-form-validation/), creating interactive maps, and displaying animated charts.

When a web page is loaded, i.e., after HTML and CSS have been downloaded, the JavaScript engine in the web browser executes the JavaScript code. The JavaScript code then modifies the HTML and CSS to update the user interface dynamically.

The JavaScript engine is a component of web browsers responsible for interpreting and executing JavaScript code. It includes a parser to analyze the code, a compiler to convert it into machine code, and an interpreter to run the compiled code.

Notable JavaScript engines include V8 in Chrome, SpiderMonkey in Firefox, and JavaScriptCore in Safari.

Initially, JavaScript engines were implemented as interpreters. However, modern JavaScript engines are commonly implemented as just-in-time compilers that compile JavaScript code to bytecode for improved performance.

## Client-side vs. Server-side JavaScript

When JavaScript is used on a web page, it is executed in web browsers, serving as a client-side language.

JavaScript can run on both web browsers and servers. A popular JavaScript server-side environment is [Node.js](https://www.javascripttutorial.net/nodejs-tutorial/). Unlike client-side JavaScript, server-side JavaScript executes on the server and allows you to access databases, file systems, etc.

## JavaScript History

In 1995, JavaScript was developed by [Brendan Eich](https://en.wikipedia.org/wiki/Brendan_Eich), a Netscape developer. Initially named Mocha, it was later renamed to LiveScript.

Netscape decided to rebrand LiveScript to JavaScript to capitalize on the popularity of Java. The decision was made shortly before the release of Netscape Navigator 2 web browser, leading to the introduction of JavaScript version 1.0.

Netscape launched JavaScript 1.1 in Netscape Navigator 3. In the meantime, Microsoft introduced its web browser called [Internet Explorer](https://en.wikipedia.org/wiki/Internet_Explorer) 3 (IE 3) as a competitor to Netscape. However, IE featured its own JavaScript implementation called [JScript](https://en.wikipedia.org/wiki/JScript). Microsoft used the name JScript to avoid potential licensing conflicts with Netscape.

Hence, two distinct versions of JavaScript were in the market:

- JavaScript in Netscape Navigator
- JScript in Internet Explorer.

At this time, JavaScript lacked standardized syntax and features, prompting the community to advocate for the standardization of the language.

In 1997, JavaScript 1.1 was proposed to the [European Computer Manufacturers Association](https://www.ecma-international.org/) (ECMA) as a proposal. [Technical Committee #39](https://www.ecma-international.org/memento/tc39-m.htm) (TC39) was assigned the task of standardizing the language, maiming to transform it into a general-purpose, cross-platform, and vendor-neutral scripting language.

TC39 came up with ECMA-262, establishing a standard for defining a new scripting language called ECMAScript (often pronounced Ek-ma-script).

Following that, the International Organization for Standardization and International Electrotechnical Commissions (ISO/IEC) adopted ECMAScript (ISO/IEC-16262).