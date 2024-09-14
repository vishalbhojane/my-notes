*locally storing data to users browser*
it is only available users current browser, also it is specific to device

### There three different types of browser storage

**Cookies** - least useful version of browsers storage
**Local storage** - much easy to use, going to be most useful
**Session storage** - much easy to use

| Local Storage                           | Session Storage     | Cookies                                                                              |
| --------------------------------------- | ------------------- | ------------------------------------------------------------------------------------ |
| 10MB                                    | 5MB                 | 4KB                                                                                  |
| Never Expires                           | Expire on tab close | Manual Exp                                                                           |
| Available only to Client                | Client              | Client/Server                                                                        |
| East to use                             | Easy                | Hard                                                                                 |
| normally shopping carts are stored here |                     | when you want to send data to server from client automatically, cookies are the best |

### `localStorage` and `sessionStorage`

```js
localStorage.setItem("Name", "Asd")
sessionStorage.setItem("Age", "00")
```

Updating the value

```js
localStorage.setItem("Name", "Xyz")
sessionStorage.setItem("Age", "11")
```

Getting the item
```js
console.log(sessionStorage.getItem("Name"))
console.log(sessionStorage.getItem("Age"))
```

Removing the Item

```js
localStorage.removeItem("Name")
sessionStorage.removeItem("Age")
```

Remove All 

```js
localStorage.clear();
sessionStorage.clear();
```

## cookies

```js
const futureDate = new Date(2050, 0, 1).toUTCString() // 2050 jan 1st
const pastDate = new Date(1996, 0, 1).toString() // 1996 jan 1st
document.cookie = `name=Kyle; expires=${futureDate}`
document.cookie = `age=25; expires=${futureDate}`
```

to access the cookie

```js
console.log(document.cookie)
```

to delete the cookie

```js
document.cookie = `name=; expires=${pastDate}`
```