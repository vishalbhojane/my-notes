A JavaScript Proxy is an object that wraps another object (target) and intercepts the fundamental operations of the target object.

The fundamental operations can be the property lookup, assignment, enumeration, function invocations, etc
### Creating a proxy object

```js
let proxy = new Proxy(target, handler);
```

- `target` – is an object to wrap.
- `handler` – is an object that contains methods to control the behaviours of the `target`. The methods inside the `handler` object are called traps.
##### A simple proxy example

First, define an object called `user`

```js
const user = {
    firstName: 'John',
    lastName: 'Doe',
    email: 'john.doe@example.com',
}
```

Second, define a `handler` object

```js
const handler = {
    get(target, property) {
        console.log(`Property ${property} has been read.`);
        return target[property];
    }
}
```

Third, create a `proxy` object

```js
const proxyUser = new Proxy(user, handler);
```

The `proxyUser` object uses the `user` object to store data. The `proxyUser` can access all properties of the `user` object

![[proxy.png]]

Fourth, access the `firstName` and `lastName` properties of the `user` object via the `proxyUser` object

```js
console.log(proxyUser.firstName);
console.log(proxyUser.lastName);
```

When you access a property of the `user` object via the `proxyUser` object, the `get()` method in the `handler` object is called

```
Property firstName has been read.
John
Property lastName has been read.
Doe
```

Fifth, if you modify the original object `user`, the change is reflected in the `proxyUser`

```js
user.firstName = 'Jane';
console.log(proxyUser.firstName);
```

```
Property firstName has been read.
Jane
```

Similarly, a change in the `proxyUser` object will be reflected in the original object (`user`)

```js
proxyUser.lastName = 'William';
console.log(user.lastName);
```

```
William
```

---
### Proxy Traps

##### `get()` trap

The `get()` trap is fired when a property of the `target` object is accessed via the proxy object

The `user` object does not have a property `fullName`, you can use the `get()` trap to create the `fullName` property based on the `firstName` and `lastName`

```js
const user = {
    firstName: 'John',
    lastName: 'Doe'
}

const handler = {
    get(target, property) {
        return property === 'fullName' ?
            `${target.firstName} ${target.lastName}` :
            target[property];
    }
};

const proxyUser = new Proxy(user, handler);

console.log(proxyUser.fullName);
// John Doe
```

##### `set()` trap

The `set()` trap controls behaviour when a property of the `target` object is set

Suppose that the `age` of the user must be greater than 18. To enforce this constraint, you develop a `set()` trap as follows

Suppose that the `age` of the user must be greater than 18. To enforce this constraint, you develop a `set()` trap as follows

```js
const user = {
    firstName: 'John',
    lastName: 'Doe',
    age: 20
}

const handler = {
    set(target, property, value) {
        if (property === 'age') {
            if (typeof value !== 'number') {
                throw new Error('Age must be a number.');
            }
            if (value < 18) {
                throw new Error('The user must be 18 or older.')
            }
        }
        target[property] = value;
    }
};

const proxyUser = new Proxy(user, handler);

proxyUser.age = 'foo';
// Error: Age must be a number.

proxyUser.age = '16';
// The user must be 18 or older.

proxyUser.age = 21; // no error
```

##### `apply()` trap

The `handler.apply()` method is a trap for a function call

```js
let proxy = new Proxy(target, {
    apply: function(target, thisArg, args) {
        //...
    }
});
```

See the following example

```js
const user = {
    firstName: 'John',
    lastName: 'Doe'
}

const getFullName = function (user) {
    return `${user.firstName} ${user.lastName}`;
}


const getFullNameProxy = new Proxy(getFullName, {
    apply(target, thisArg, args) {
        return target(...args).toUpperCase();
    }
});

console.log(getFullNameProxy(user)); // 
```

##### `has(target, prop)`
The `has` trap is triggered when using the `in` operator to check if a property exists in an object.

##### `deleteProperty(target, prop)`
The `deleteProperty` trap is called when using the `delete` operator to remove a property from an object.

---
### More traps

The following are more traps:

- `construct` – traps usage of the `new` operator
- `getPrototypeOf` – traps an internal call to `[[GetPrototypeOf]]`
- `setPrototypeOf` – traps a call to `Object.setPrototypeOf`
- `isExtensible` – traps a call to `Object.isExtensible`
- `preventExtensions` – traps a call to `Object.preventExtensions`
- `getOwnPropertyDescriptor` – traps a call to `Object.getOwnPropertyDescriptor`

---
### Use Cases of Proxy Objects

##### Validation
Proxies can be used to enforce constraints on data by validating or modifying property values

```js
const validatedUser = new Proxy({}, {
  set(target, prop, value) {
    if (prop === 'age' && (typeof value !== 'number' || value < 0 || value > 120)) {
      throw new Error('Invalid age');
    }
    target[prop] = value;
    return true;
  },
});

validatedUser.age = 30; // Valid assignment  
validatedUser.age = -5; // Throws an error: Invalid age
```

##### Logging
Proxies enable easy logging of property access, providing insights into object usage for debugging or performance monitoring

```js
const loggedObject = new Proxy({}, {
  get(target, prop) {
    console.log(`Accessing property: ${prop}`);
    return target[prop];
  },
});

loggedObject.name = 'Alice'; // Accessing property: name  
console.log(loggedObject.name); // Accessing property: name
```
##### Security
Proxies can enhance object security by preventing unauthorized access to certain properties or operations

```js
const securedObject = new Proxy({ secret: 'classified' }, {
  get(target, prop) {
    if (prop === 'secret') {
      throw new Error('Unauthorized access');
    }
    return target[prop];
  },
});

console.log(securedObject.publicInfo); // Access allowed  
console.log(securedObject.secret); // Throws an error: Unauthorized access
```

##### Memoization
Proxies can be used for memoization, caching the results of expensive function calls for better performance.

```js
function fibonacci(n) {
  if (n <= 1) {
    return n;
  }
  return fibonacci(n - 1) + fibonacci(n - 2);
}
```

```js
const memoizedFibonacci = new Proxy({}, {
  get(target, prop) {
    if (!(prop in target)) {
      target[prop] = fibonacci(Number(prop));
    }
    return target[prop];
  },
});
console.log(memoizedFibonacci[10]); // Calculated and cached
console.log(memoizedFibonacci[5]);  // Retrieved from cache
```

---
### Real-time Example in E-commerce

Consider an e-commerce scenario where you want to enforce some business rules using Proxy objects.

In this example, the Proxy ensures that the quantity of product cannot be set to a negative value, enforcing a business rule within the e-commerce context.

```js
const product = {
  name: 'Smartphone',
  price: 500,
  quantity: 10,
};
```

```js
const securedProduct = new Proxy(product, {
  set(target, prop, value) {
    if (prop === 'quantity' && value < 0) {
      throw new Error('Invalid quantity');
    }
    target[prop] = value;
    return true;
  },
});
securedProduct.quantity = 15; // Valid assignment
securedProduct.quantity = -5; // Throws an error: Invalid quantity
```