The Fetch API provides a JavaScript interface for making HTTP requests and processing the responses.

`fetch()` returns a Promise which is fulfilled with a Response object representing the server's response
##### Syntax

```js
fetch('url') // api for the get request
    .then(response => response.json())
    .then(data => console.log(data));
```
##### Parameters

**URL**: The URL to which the request is to be made.

**Options**: It is an array of properties. It is an optional parameter. Options available are:
- Method: Specifies HTTP method for the request. (can be GET, POST, PUT or DELETE)
- Headers
- Body: Data to be sent with the request.
- Mode: Specifies request mode(eg. `cors`, `nocors`, same-origin, etc)
- Credentials: Specifies whether to send user credentials (cookies, authentication headers, etc.) with the request

---
### GET

```js
const fetchRes = fetch("https://jsonplaceholder.typicode.com/todos/1");

fetchRes.then(res =>
    res.json()).then(d => {
        console.log(d)
    })
```
### POST

```js
// Your JSON data
const jsonData = { key1: 'value1', key2: 'value2' };

// Set up options for the fetch request
const options = {
    method: 'POST',
    headers: {
        'Content-Type': 'application/json' // Set content type to JSON
    },
    body: JSON.stringify(jsonData) // Convert JSON data to a string and set it as the request body
};

// Make the fetch request with the provided options
fetch('https://api.example.com/upload', options)
    .then(response => {
        // Check if the request was successful
        if (!response.ok) {
            throw new Error('Network response was not ok');
        }
        // Parse the response as JSON
        return response.json();
    })
    .then(data => {
        // Handle the JSON data
        console.log(data);
    })
    .catch(error => {
        // Handle any errors that occurred during the fetch
        console.error('Fetch error:', error);
    });
```

---
### More Examples

```js
const URL = "https://jsonplaceholder.typicode.com/users"

fetch(URL)
    .then(response => {
        return response.json()
    })
    .then(data => {
        console.log(data.map(user => user.name))
    })
```

Converting above promise to `async` `await`

```js
async function doStuff() {
    const response = await fetch(URL)
    const users = await response.json()
    console.log(users.map(user => user.name))
}
doStuff()
```

Checking the response for error

```js
async function doStuff() {
    try {
        const response = await fetch(URL)
        if (response.ok) { // checking the responce
            const users = await response.json()
            console.log(users.map(user => user.name))
        } else {
            console.log("Failure")
        }
    } catch (e) {
        console.error(e)
    }
}
doStuff()
```