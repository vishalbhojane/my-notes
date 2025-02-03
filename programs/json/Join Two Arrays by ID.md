Create a function join that takes two arrays of objects (arr1 and arr2) as input. Each object has an 'id' property. The function should merge these arrays based on the 'id', with properties from arr2 overriding those from arr1 when there's a conflict. The result should be sorted by 'id' in ascending order.

```javascript
function join(arr1, arr2) {
    const merged = {};
    
    [...arr1, ...arr2].forEach(obj => {
        merged[obj.id] = { ...merged[obj.id], ...obj };
    });
    
    return Object.values(merged).sort((a, b) => a.id - b.id);
}
```

Usage

```javascript
const arr1 = [{"id": 1, "x": 2, "y": 3}, {"id": 2, "x": 3, "y": 6}];
const arr2 = [{"id": 2, "x": 10, "y": 20}, {"id": 3, "x": 0, "y": 0}];
console.log(join(arr1, arr2));
// [{"id": 1, "x": 2, "y": 3}, {"id": 2, "x": 10, "y": 20}, {"id": 3, "x": 0, "y": 0}]
```