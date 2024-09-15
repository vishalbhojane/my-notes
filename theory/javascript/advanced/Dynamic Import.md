Allows you to load modules dynamically at runtime instead of statically during compilation time (ES6)

Syntax

```js
import('./path-to-my-module.js');
```

Dynamic import returns a Promise

```js
// new-module.js
const USERNAME_ID_KEY = 'id';
export const DEFAULT_USERNAME = 'John';
export const getUserId = (user) => user.id;
export default USERNAME_ID_KEY;
```

```js
// index.js
import('./new-module.js')
  .then(module => {
    console.log(module.DEFAULT_USERNAME);
    // => 'John'
    console.log(module.getUserId({ id: 123 }));
    // => 123
    console.log(module.default);
    // => 'id'
  })
  .catch(error => console.log('Error!'));
```

Using `async` and `await`

```js
async function moduleLoading() {
  const {
    DEFAULT_USERNAME,
    getUserId,
    default: defaultModule,
  } = await import('./new-module.js');

  console.log(DEFAULT_USERNAME);
  // => 'John'
  console.log(getUserId({ id: 123 }));
  // => 123
  console.log(defaultModule);
  // => 'id'
}
moduleLoading();
```

### When using dynamic imports?

Conditional imports

```js
if (user.role === 'author') {
  import('./author')
    .then((authorModule) => {
       console.log(authorModule.version);
    });
}
```

Computed import path

```js
const VEHICULES = {
  CAR: 'car',
  BOAT: 'boat',
};
const pathToUse = `./${VEHICLES.CAR}-module.js`;
import(pathToUse)
  .then((module) => {
    // ...
  })
  .catch((error) => console.log("Error!"));
```

### Advantages

Reduces bundle size by deferring module loading until needed
Improving page load times
Enhancing code organization by separating related modules