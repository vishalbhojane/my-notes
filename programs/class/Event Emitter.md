Design an EventEmitter class with two methods:

1. subscribe(eventName, callback):
   - Adds a callback function for the given event.
   - Returns an object with an unsubscribe method.

2. emit(eventName, args):
   - Triggers all callbacks for the given event with optional arguments.
   - Returns an array of results from the callbacks.

## Solution

```javascript
class EventEmitter {
    constructor() {
        this.events = {};
    }

    subscribe(eventName, callback) {
        if (!this.events[eventName]) {
            this.events[eventName] = [];
        }
        this.events[eventName].push(callback);

        return {
            unsubscribe: () => {
                this.events[eventName] = this.events[eventName].filter(cb => cb !== callback);
                if (this.events[eventName].length === 0) {
                    delete this.events[eventName];
                }
            }
        };
    }

    emit(eventName, args = []) {
        if (!this.events[eventName]) {
            return [];
        }
        return this.events[eventName].map(cb => cb(...args));
    }
}
```
