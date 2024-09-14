In mathematics, the **Euclidean distance** between two points in Euclidean space is the length of a line segment between the two points.
It can be calculated from the Cartesian coordinates of the points using the Pythagorean theorem, therefore occasionally being called the Pythagorean distance.
## Distance formulas

#### One Dimension
`d = | x2 - x1 |

#### Two Dimension
`d = Squareroot((x2 - x1)^2 + (y2 - y1)^2)

Three Dimension
`d = Squareroot((x3 - y3)^2 + (x2 - x1)^2 + (y2 - y1)^2)`

The `Math.hypot()` static method returns the square root of the sum of squares of its arguments. That is

```js
console.log(Math.hypot(3, 4));
// Expected output: 5
// Squareroot(9 + 16)
```

### Implementation (2D)

```js
const distance = (x0, y0, x1, y1) => Math.hypot(x1 - x0, y1 - y0);

distance(1, 1, 2, 3); // ~2.2361
```

### 3D

```js
const distance = ([x0, y0, z0], [x1, y1, z1]) =>
  Math.hypot(x1 - x0, y1 - y0, z1 - z0);

distance([1, 1, 1], [2, 3, 2]); // ~2.4495
```

### Any Dimension

```js
const euclideanDistance = (a, b) =>
  Math.hypot(...Object.keys(a).map(k => b[k] - a[k]));

euclideanDistance([1, 1], [2, 3]); // ~2.2361
euclideanDistance([1, 1, 1], [2, 3, 2]); // ~2.4495
euclideanDistance([1, 1, 1, 1], [2, 3, 2, 3]); // ~3.1623
```
