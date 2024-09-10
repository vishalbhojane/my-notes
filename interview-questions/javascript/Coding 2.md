## Implement `sum(1)(2)(3)(4)()`

```js
// recursion
let sum = function sum(a) {
    return function (b) {
        if (b) {
            return sum(a + b)
        }
        return a
    }
}
let result = sum(1)(2)(3)();
```

## Get sum array except for current element

```js
function getSum(arr) {
    const newArr = new Array(arr.length).fill(0);

    for (let i = 0; i < arr.length; i++) {
        for (let j = 0; j < arr.length; j++) {
            if (j == i) {
                continue
            }
            newArr[i] += arr[j]
        }
    }
    console.log(newArr);
}
getSum([2, 7, 11, 4, -2])
```

Normalize the Object

```js
// input 
const arr = [
    { key: 'test1', data: 'data1' },
    { key: 'test1', data: 'data1' },
    { key: 'test2', data: 'data1' },
    { key: 'test1', data: 'data1' },
    { key: 'test3', data: 'data1' },
    { key: 'test4', data: 'data1' },
]

// expected output
{
    test1: [
        { key: 'test1', data: 'data1' },
        { key: 'test1', data: 'data1' },
        { key: 'test1', data: 'data1' }
    ],
    test2: [{ key: 'test2', data: 'data1' }],
    test3: [{ key: 'test3', data: 'data1' }],
    test4: [{ key: 'test4', data: 'data1' }]
}

// solution
function normalize(arr) {
    const output = {}

    arr.forEach(({ key, data }) => {
        if (!output[key]) {
            output[key] = []
        }
        output[key] = [...output[key], { key, data }]
    })
    return output
}

console.log(normalize(arr))
```

```js
// input
const data = {
    page: 1,
    products: [
        {
            id: "123",
            description: "Product 1 description",
            title: "Product 1",
        },
        {
            id: "234",
            description: "Product 2 description",
            title: "Product 2",
        }
    ],
    images: [
        {
            id: "444",
            productId: "123",
            url: "/imageSrc",
        },
        {
            id: "555",
            productId: "234",
            url: "/imageSrc",
        },
        {
            id: "666",
            productId: "123",
            url: "/imageSrc",
        }
    ]
}

// array
const productsArr = data.products.map(product => {
    return {
        ...product,
        images: data.images.filter(image => image.productId === product.id)
    }
})
console.log(products)

const productsObj = data.products.reduce((acc, curr) => {
    return {
        ...acc,
        [curr.id]: {
            ...curr,
            images: data.images.filter(image => image.productId === curr.id)
        }
    }
}, {});
console.log(productsObj);
```

## array to object

```js
function arrayToObj(arr) {
    return arr.reduce(function (acc, curr, i) {
        return {
            ...acc,
            [i]: curr
        }
    }, {})
}
console.log(arrayToObj(['a', 'b', 'c']));
```

## Count By

```js
// console.log(countBy([6.1, 4.2, 6.3], Math.floor));
// => { '4': 1, '6': 2 }

//   console.log(countBy([{ n: 3 }, { n: 5 }, { n: 3 }], (o) => o.n));
// => { '3': 2, '5': 1 }

function countBy(array, iteratee) {
    const result = {}

    if (array.length == 0) return result

    for (let i = 0; i < array.length; i++) {
        let value = iteratee(array[i]);
        if (result[value]) {
            result[value]++
        } else {
            result[value] = 1
        }
    }
    return result

}
```

## Cycle

```js
function cycle(...values) {
    let currentIndex = -1;
    return function () {
        currentIndex = currentIndex + 1 >= values.length ? 0 : (currentIndex + 1);
        return values[currentIndex]

    }
}

const helloFn = cycle('hello');
console.log(helloFn()); // "hello"
console.log(helloFn()); // "hello"

const onOffFn = cycle('on', 'off');
console.log(onOffFn()); // "on"
console.log(onOffFn()); // "off"
console.log(onOffFn()); // "on"
```