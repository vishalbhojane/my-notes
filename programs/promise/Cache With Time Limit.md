Implement a TimeLimitedCache class with the following methods:
1. set(key, value, duration): Adds or updates a key-value pair with an expiration time. Returns true if the key existed and was unexpired, false otherwise.
2. get(key): Returns the value of an unexpired key, or -1 if not found.
3. count(): Returns the count of unexpired keys.

```javascript
class TimeLimitedCache {
    constructor() {
        this.cache = new Map();
    }

    set(key, value, duration) {
        const existingEntry = this.cache.get(key);
        if (existingEntry) clearTimeout(existingEntry.timeoutId);

        const timeoutId = setTimeout(() => this.cache.delete(key), duration);
        this.cache.set(key, { value, timeoutId });

        return Boolean(existingEntry);
    }

    get(key) {
        return this.cache.has(key) ? this.cache.get(key).value : -1;
    }

    count() {
        return this.cache.size;
    }
}
```

usage

```javascript
const cache = new TimeLimitedCache();
console.log(cache.set(1, 42, 100)); // false
setTimeout(() => console.log(cache.get(1)), 50); // 42
setTimeout(() => console.log(cache.count()), 50); // 1
setTimeout(() => console.log(cache.get(1)), 150); // -1
```