The Proxy object enables you to create a proxy for another object,
which can intercept and redefine fundamental operations for that object

proxy provides an alternative way to control access to objects
as well as the ability to intercept and manipulate operations performed on those objects
ES6 feature

The Proxy constructor takes two arguments:
- the target object you want to wrap
- a handler object containing traps responsible for handling specific types of operations such as property gets/sets, function calls, and more

```js
const person = {
    name: "John Doe",
    age: 25,
};

// Creating a Proxy with custom handlers
const proxyPerson = new Proxy(person, {
    // Handler for getting properties
    get(target, propKey, receiver) {
        console.log(`Getting ${propKey}...`);
        return Reflect.get(...arguments);
    },
});

console.log(proxyPerson.name); // Output: Getting name... John Doe
```

Another useful aspect of proxies is their capability to enforce data validation rules at runtime.

```js
const student = {
    id: 101,
    name: "Jane Smith",
};

// Disallow updates to ID field
const proxyStudent = new Proxy(student, {
    set(target, key, value, receiver) {
        if (key === 'id') {
            throw new Error("ID Cannot Be Changed!");
        } else {
            return Reflect.set(...arguments);
        }
    },
});

proxyStudent.id = 102; // Throws Error: ID Cannot Be Changed!
proxyStudent.age = 27; // Works Normally
```