Tree shaking refers to dead code elimination
It means that unused modules will not be included in the bundle during the build process

Tree Shaking helps us to reduce the weight of the application

Tools like `webpack` will detect dead code and mark it as “unused module” but it won’t remove the code.
`Webpack` relies on minifiers to clean up dead code, one of them is `UglifyJS` plugin, which will eliminate the dead code from the bundle.

```js
// modules.js
export function drive(props) {
    return props.gas
}

export function fly(props) {
    return props.miles
}
```

```js
// main.js
import { drive } from modules;

// some code
eventHandler = (event) => {
    event.preventDefault()
    drive({ gas: event.target.value })
}
// some code
```

`fly()` was never imported and won't be included in our bundle

It only works with import and export. It won’t work with `CommonJS` require syntax.
Same applies to `npm` dependencies
great example is `lodash`, just `import pick from 'lodash/pick'` and your bundle will only include one small module instead of entire `lodash` library.