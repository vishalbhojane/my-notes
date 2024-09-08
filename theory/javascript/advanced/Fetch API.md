The Fetch API provides a JavaScript interface for making HTTP requests and processing the responses.
`fetch()` returns a Promise which is fulfilled with a Response object representing the server's response

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

converting above promise to async await

```js
async function doStuff() {
    const response = await fetch(URL)
    const users = await response.json()
    console.log(users.map(user => user.name))
}
doStuff()
```

checking the response for error

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

to send data to server

```js
const BLOG_URL = "https://jsonplaceholder.typicode.com/posts"
async function doStuff() {
    const response = await fetch(BLOG_URL, {
        method: 'POST', // this is not related to word posts in url, here we are telling that we are sending data
        headers: {
            'Content-Type': "application/json"
        },
        body: JSON.stringify({
            title: "Hello world"
        })
    })
    const post = await response.json()
    console.log(post)
}
doStuff()
```