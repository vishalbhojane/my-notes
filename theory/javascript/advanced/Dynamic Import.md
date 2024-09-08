Allows you to load modules dynamically at runtime instead of statically during compilation time (ES6)

reduces bundle size by deferring module loading until needed
improving page load times
enhancing code organization by separating related modules

```js
// app.js
const moduleAPromise = import('./moduleA');
const moduleBPromise = import('./moduleB');

(async () => {
    const { fooA } = await moduleAPromise;
    const { barB } = await moduleBPromise;

    console.log(fooA());
    console.log(barB());
})();
```

more ex

```js
if (user.role === 'author') {
    import('./author')
        .then((authorModule) => {
            console.log(authorModule.version);
        });
}
```