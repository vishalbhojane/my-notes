## **Web Knowledge:**

1. _**Caching**_: Caching is a technique used to store copies of frequently accessed web resources (such as images, stylesheets, or JavaScript files) closer to the user, either on their device or on intermediate servers. This helps improve website performance and reduces the load on the server.

2. _**HTTP/2:**_ HTTP/2 is a major revision of the HTTP protocol, designed to improve the efficiency of web communication. It introduces features like multiplexing, header compression, and server push, which help reduce latency and increase the overall speed of web page loading.

3. _**Security:**_ Web security involves protecting web applications and users from various threats, such as unauthorized access, data breaches, and attacks. It encompasses practices like secure authentication, encryption, input validation, and protection against common vulnerabilities like Cross-Site Scripting (XSS) and Cross-Site Request Forgery (CSRF).

## **Web Performance:**

1. _**Critical Rendering Path:**_ The critical rendering path is the sequence of steps a browser takes to render a web page, from fetching resources to displaying the content on the screen. Optimizing the critical rendering path involves minimizing render-blocking resources, optimizing CSS and JavaScript, and prioritizing above-the-fold content for faster rendering.

2. _**Reflow:**_ Reflow, also known as layout or re-layout, is the process by which a browser recalculates the positions and dimensions of elements on a web page. It can be triggered by changes to the DOM, CSS, or viewport dimensions. Reflows are computationally expensive and should be minimized for better performance.

3. _**preload, preconnect, prefetch, prerender:**_ These are resource hints that allow web developers to provide the browser with advance information about resources needed by a web page.

3.1. **preload:** Suggests the browser to fetch a resource as soon as possible, to be used in the current or subsequent pages.

3.2. **preconnect:** Instructs the browser to set up early connections to a specific origin before an actual request is made, reducing the latency for subsequent requests.

3.3. **prefetch:** Indicates that a resource will be needed in the future, allowing the browser to fetch it preemptively during idle time.

3.4. **prerender:** Specifies that a page or resource should be loaded in the background, as if the user is about to visit it, to provide a near-instantaneous response when the user navigates.

4. _**Rendering Performance:**_ Rendering performance refers to the speed at which a web browser processes and displays web content. It involves optimizing factors like layout, painting, and compositing. Techniques like CSS and JavaScript minification, efficient DOM manipulation, and reducing unnecessary paint operations can improve rendering performance.

5. _**Workers:**_ Web Workers are JavaScript scripts that run in the background, separate from the main browser thread. They enable concurrent execution and allow offloading computationally intensive tasks, such as complex calculations or data processing, without blocking the user interface.

6. _**Image Optimization:**_ Image optimization techniques aim to reduce the file size of images while maintaining an acceptable level of visual quality. This can involve compressing images, choosing appropriate image formats (e.g., JPEG, PNG, SVG), lazy loading, and utilizing responsive images to serve the most suitable version based on device capabilities and screen size.

## **DOM:**

1. _**Elements:**_ In the Document Object Model (DOM), elements represent the individual HTML tags in a web page. Each element is an object that can be accessed and manipulated through JavaScript, allowing dynamic changes to the content, style, and structure of the web page.

2. _**Manipulation:**_ DOM manipulation refers to the process of programmatically modifying elements, attributes, and content within the DOM tree. It involves tasks like creating, removing, or modifying elements, changing styles or classes, updating text or attribute values, and responding to user interactions.

3. _**Document Fragment:**_ A document fragment is a lightweight container that can hold a group of DOM nodes. It is useful for efficiently manipulating multiple elements before appending them to the main DOM tree, reducing the number of reflows or repaints that would occur if each element were modified individually.

4. _**Event delegation and bubbling:**_ Event delegation is a technique where you attach an event listener to a parent element to handle events that occur on its child elements. This can improve performance and simplify event handling, especially when dealing with dynamically added or large numbers of elements. Event bubbling refers to the propagation of an event from the target element to its parent elements up the DOM tree, allowing multiple elements to receive and respond to the same event.

## **HTML:**

1. _**Semantic Elements:**_ Semantic elements in HTML provide meaning and structure to the content they wrap. Examples include `<header>, <nav>, <section>, <article>, <aside>, <footer>`, which clarify the purpose and role of specific sections within the page. Semantic elements improve accessibility, search engine optimization, and maintainable code.
2. _**Accessibility:**_ Web accessibility ensures that websites and web applications are usable by individuals with disabilities. It involves following standards and best practices to make content perceivable, operable, understandable, and robust for all users. This includes considerations for screen readers, keyboard navigation, color contrast, alternative text for images, and more.
3. _**Responsive web:**_ Responsive web design is an approach to building websites that adapt and respond to different screen sizes and devices. It involves using flexible layouts, fluid grids, and media queries to adjust the design and content presentation, ensuring an optimal user experience on desktops, tablets, and mobile devices.

## **Javascript:**

1. _**“this” keyword:**_ In JavaScript, the “this” keyword refers to the object that is currently executing the code. Its value can vary depending on how a function is called. It can represent the global object (window in a browser), the object on which a method is called, or it can be explicitly bound using functions like call(), apply(), or bind().

2. _**Closure:**_ A closure is a function bundled together with its lexical environment (the variables it has access to). It allows the function to retain access to those variables even after the outer function has finished executing. Closures are commonly used for encapsulation, data privacy, and creating functions with persistent state.

3. _**Inheritance:**_ In JavaScript, inheritance is a mechanism that allows objects to inherit properties and methods from other objects. It can be achieved through prototype-based inheritance, where objects are linked together through prototypes, or using class-based inheritance introduced in ECMAScript 6 with the “class” syntax.

4. _**Asynchronous JavaScript:**_ Asynchronous JavaScript refers to executing code asynchronously, allowing non-blocking execution and avoiding UI freezes. Prominent techniques include callbacks, promises, and async/await syntax. Asynchronous operations are commonly used when making network requests, handling user interactions, or performing time-consuming tasks without blocking the main thread.

5. _**Hoisting:**_ Hoisting is a JavaScript behavior where variable and function declarations are moved to the top of their containing scope during the compilation phase. This means that you can use variables or call functions before they are declared in the code. However, only the declarations are hoisted, not the initializations or assignments.

6. _**Currying:**_ Currying is a technique in functional programming where a function with multiple arguments is transformed into a sequence of functions, each taking a single argument. This allows partial application of arguments, creating more reusable and composable functions.

7. _**Higher-order functions:**_ Higher-order functions are functions that can accept other functions as arguments or return functions as their results. They enable powerful functional programming paradigms like function composition, abstraction, and encapsulation of behavior.

## **Design patterns:**

1. _**Mixin:**_ A mixin is a design pattern that allows the selective combination of multiple classes or objects’ functionalities into a single class. It promotes code reuse and provides flexibility in adding or removing behaviors without the need for deep inheritance hierarchies.

2. _**Factory:**_ The factory pattern is a creational design pattern that provides an interface for creating objects without specifying their exact class. It encapsulates the object creation logic and allows subclasses or configurations to determine the type of objects to be created.

3. _**Singleton:**_ The singleton pattern ensures that a class has only one instance globally accessible. It restricts the instantiation of a class to a single object, providing a central point of access to that instance throughout the application.

4. _**Facade:**_ The facade pattern provides a simplified interface or entry point to a complex system or set of classes. It hides the underlying complexity and provides a higher-level interface that is easier to use and understand.

5. _**MVC, MVVM:**_ MVC (Model-View-Controller) and MVVM (Model-View-ViewModel) are architectural patterns commonly used in web development. MVC separates the application into three components: the model (data and business logic), the view (presentation and UI), and the controller (handles user input and orchestrates interactions). MVVM is a variation of MVC that adds a view model as an intermediary between the model and view, allowing data binding and easier testing.

6. _**Server vs Client-Side Rendering:**_ Server-side rendering (SSR) and client-side rendering (CSR) are approaches to rendering web pages. SSR renders the initial HTML on the server and sends it to the client, where it is hydrated with JavaScript. CSR relies on JavaScript executing on the client’s browser to render the content. SSR improves initial page load times and SEO, while CSR allows for more dynamic and interactive experiences.