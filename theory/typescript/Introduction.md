## Basic Types

### Number
Represents both integer and floating-point numbers.

```typescript
let age: number = 30;            // An integer
let temperature: number = 36.5; // A float
````

**Example**: Performing arithmetic operations:

```typescript
let sum: number = age + 5; // 35
```

### String

Used for representing text data, enclosed in single, double, or backticks.

```typescript
let firstName: string = "John";
let lastName: string = 'Doe';
let greeting: string = `Hello, ${firstName} ${lastName}!`;
```

**Example**: String concatenation:

```typescript
let fullName: string = firstName + " " + lastName; // "John Doe"
```

### Boolean

Represents a value that can be either `true` or `false`.

```typescript
let isActive: boolean = false; 
let isLoggedIn: boolean = true;
```

**Example**: Conditional statements:

```typescript
if (isLoggedIn) {
    console.log("Welcome!");
}
```

### Array

An array can hold multiple values of the same type. Defined using the `Type[]` syntax or `Array<Type>`.

```typescript
let numbers: number[] = [1, 2, 3, 4, 5];
let fruits: Array<string> = ["Apple", "Banana", "Cherry"];
```

**Example**: Accessing elements:

```typescript
let firstFruit: string = fruits[0]; // "Apple"
```

### Tuples

A fixed-size array where each element can have a different type.

```typescript
let user: [string, number] = ["Alice", 30];
```

**Example**: Decomposing tuples:

```typescript
let [username, userAge]: [string, number] = user; // username = "Alice", userAge = 30
```

### Any

A type that can hold any value; essentially opting out of type checking.

```typescript
let variable: any = 5;
variable = "Hello"; // No error
variable = true;    // Still valid
```

**Example**: Caution with `any`:

```typescript
let data: any = 42;
let result: string = data; // No error, but could lead to runtime errors
```

### Unknown

Similar to `any`, but safer. You must do type-checking before using an `unknown` type.

```typescript
let value: unknown = 30;
// let strLength: number = value.length; // Error: Object is of type 'unknown'

if (typeof value === "number") {
    let numLength: number = value.toString().length; // Now it’s safe
}
```

**Example**: Ensuring type before access:

```typescript
let data: unknown = "TypeScript";
if (typeof data === "string") {
    console.log(data.length); // Safe to access
}
```

### Never

Indicates that a function never finishes executing (not returnable). Often used in functions that throw exceptions or have infinite loops.

```typescript
function throwError(message: string): never {
    throw new Error(message);
}
```

**Example**: Used in exhaustive checks:

```typescript
function handleResponse(response: string | number): void {
    if (typeof response === "string") {
        console.log(response);
    } else if (typeof response === "number") {
        console.log(response);
    } else {
        // Using never to enforce exhaustiveness
        const _: never = response; // Causes a compile-time error if there’s an unhandled case
    }
}
```

### Void

Used as the return type for functions that do not return a value.

```typescript
function logMessage(message: string): void {
    console.log(message);
}
```

**Example**: No return statement:

```typescript
function doNothing(): void {
    // Intentionally left blank
}
```

### Enum

A way to define a set of named constants, improving code readability.

```typescript
enum Color {
    Red,
    Green,
    Blue
}

let c: Color = Color.Green; // c is now 1
```

**Example**: Assigning specific values:

```typescript
enum Status {
    Active = 1,
    Inactive = 0,
    Pending = 2
}
```

## Type Inference

TypeScript infers the types based on the value assigned to a variable at the time of declaration. This reduces the need for explicit type annotations.

```typescript
let num = 10; // inferred as number
let message = "Hello"; // inferred as string
```

**Example**: Array type inference:

```typescript
let nums = [1, 2, 3]; // inferred as number[]
```

## Union and Intersection Types

### Union Types

A union type allows a variable to hold multiple types. You define it by separating the types with a pipe `|`.

```typescript
let value: string | number;
value = "Hello"; // okay
value = 100;     // okay
// value = true; // Error
```

**Example**: Creating functions that work with multiple types:

```typescript
function printId(id: string | number) {
    console.log("Id: " + id);
}
printId(101);
printId("202");
```

### Intersection Types

An intersection type combines multiple types into one. All the properties of all the types must be satisfied.

```typescript
interface User {
    name: string;
}

interface Employee {
    employeeId: number;
}

type EmployeeUser = User & Employee;

let employee: EmployeeUser = {
    name: "Alice",
    employeeId: 1
};
```

**Example**: Using intersection types in functions:

```typescript
function printUserInfo(user: User & Employee) {
    console.log(`Name: ${user.name}, Employee ID: ${user.employeeId}`);
}
```

## Type Aliases

Type aliases provide a way to create a new name for a type. This can simplify complex type declarations.

```typescript
type StringOrNumber = string | number;

let value: StringOrNumber;
value = "Hello"; // okay
value = 42;      // okay
```

**Example**: Creating more complex types:

```typescript
type Point = {
    x: number;
    y: number;
};

function logPoint(point: Point) {
    console.log(`x: ${point.x}, y: ${point.y}`);
}
```

## Interfaces

Interfaces define the structure of an object, including its properties and methods.

```typescript
interface Person {
    name: string;
    age: number;
}

let person: Person = {
    name: "John",
    age: 30
};
```

**Example**: Extending interfaces:

```typescript
interface Employee extends Person {
    employeeId: number;
}

let employee: Employee = {
    name: "Jane",
    age: 28,
    employeeId: 123
};
```

## Functions

### Function Types

You can define the types of parameters and the return type in a function type declaration.

```typescript
let add: (a: number, b: number) => number;
add = (x, y) => x + y; // implementation
```

**Example**: Using function types:

```typescript
let subtract: (a: number, b: number) => number;
subtract = (x, y) => x - y; // works as expected
```

### Optional and Default Parameters

Parameters can be made optional using `?`. Default parameters can also be specified.

```typescript
function greet(name: string, age?: number): string {
    return age ? `Hello, ${name}. You are ${age} years old.` : `Hello, ${name}.`;
}

function multiply(a: number, b: number = 1): number {
    return a * b;
}
```

**Example**: Calling functions:

```typescript
console.log(greet("Alice")); // "Hello, Alice."
console.log(greet("Bob", 25)); // "Hello, Bob. You are 25 years old."
console.log(multiply(5)); // 5
console.log(multiply(5, 2)); // 10
```

## Modules

### Export and Import

Modules allow you to split your code into separate files and control the visibility of variables, functions, and classes using exports and imports.

```typescript
// In file moduleA.ts
export const PI = 3.14;
export function calculateCircumference(diameter: number): number {
    return PI * diameter;
}

// In file moduleB.ts
import { PI, calculateCircumference } from './moduleA';

console.log(PI); // 3.14
console.log(calculateCircumference(10)); // 31.4
```

## Type Assertions

A way to tell the TypeScript compiler to treat a value as a different type. Useful in cases where you know more about the type than TypeScript can infer.

```typescript
let someValue: unknown = "Hello, World!";
let strLength: number = (someValue as string).length; // Using 'as'
```

**Example**: Another syntax for assertion:

```typescript
let anotherValue: unknown = 42;
let numberValue: number = <number>anotherValue; // Using angle-bracket syntax
```

## Literal Types

### String Literal Type

Allows you to restrict a variable to a specific string literal value.

```typescript
let direction: "left" | "right";
direction = "left"; // okay
// direction = "up"; // Error: Type '"up"' is not assignable
```

**Example**: Used in functions to restrict input:

```typescript
function logDirection(direction: "up" | "down") {
    console.log(`Moving ${direction}`);
}
logDirection("up"); // okay
// logDirection("left"); // Error
```

### Numeric Literal Types

Similar to string literals, you can restrict a variable to a specific number.

```typescript
let num: 1 | 2 | 3;
num = 2;  // okay
// num = 4; // Error: Type '4' is not assignable
```

**Example**: Defining finite states:

```typescript
function printStatus(status: 0 | 1) {
    console.log(status ? "Active" : "Inactive");
}
printStatus(1); // "Active"
```

### Boolean Literal Types

Restrict the boolean variable to true or false.

```typescript
let isDone: true = true;  // okay
// isDone = false; // Error: Type 'false' is not assignable
```

**Example**: Useful in configurations:

```typescript
function setFlag(flag: true | false) {
    console.log(`Flag is set to: ${flag}`);
}
setFlag(true); // okay
// setFlag(null); // Error: Type 'null' is not assignable
```