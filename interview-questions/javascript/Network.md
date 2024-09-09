Question: Traditionally, why has it been better to serve site assets from multiple domains?
Answer: Serving assets from multiple domains:
1. Increases concurrent downloads (browsers limit connections per domain)
2. Allows for cookie-free domains for static assets
3. Enables CDN usage for global content delivery
4. Potentially improves DNS resolution time

Question: Do your best to describe the process from the time you type in a website's URL to it finishing loading on your screen.
Answer: 
1. DNS lookup to resolve domain to IP address
2. TCP connection established with server
3. TLS handshake for HTTPS
4. HTTP request sent to server
5. Server processes request and sends response
6. Browser begins receiving and parsing HTML
7. Additional resources (CSS, JS, images) are requested
8. DOM and CSSOM are constructed
9. JavaScript is executed
10. Page is rendered and displayed
11. Additional asynchronous requests may continue

Question: What are the differences between Long-Polling, Websockets and Server-Sent Events?
Answer:
Long-Polling:
- Client requests, server holds until data available
- Simulates real-time with repeated requests

Websockets:
- Full-duplex, persistent connection
- Real-time bidirectional communication

Server-Sent Events (SSE):
- Unidirectional, server to client only
- Uses standard HTTP for real-time updates

Question: Explain the following request and response headers:
Answer:

Expires, Date, Age and If-Modified-Since:
- Expires: When the response becomes stale
- Date: When the response was generated
- Age: Time since response generated
- If-Modified-Since: Conditional request based on last modification

Do Not Track:
- User preference for tracking by websites

Cache-Control:
- Directives for caching mechanisms

Transfer-Encoding:
- Form of encoding used to transfer the body safely

ETag:
- Unique identifier for a specific version of a resource

X-Frame-Options:
- Control whether a page can be displayed in a frame

Question: What are HTTP methods? List all HTTP methods that you know, and explain them.
Answer:
1. GET: Retrieve a resource
2. POST: Submit data to be processed
3. PUT: Update an existing resource
4. DELETE: Remove a resource
5. PATCH: Partially modify a resource
6. HEAD: Like GET but without response body
7. OPTIONS: Describe communication options
8. TRACE: Echo the received request
9. CONNECT: Establish a tunnel to the server

Question: What is domain pre-fetching and how does it help with performance?
Answer: Domain pre-fetching resolves domain names before resources are requested. It helps performance by reducing DNS lookup time when the actual request is made. Example:

```js
<link rel="dns-prefetch" href="https://example.com">
```

