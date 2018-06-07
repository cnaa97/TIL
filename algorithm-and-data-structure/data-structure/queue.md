# 큐 \(Queue\)

![](../../.gitbook/assets/image%20%283%29.png)

* First-In-First-Out \(FIFO\)

### Javascript Code

```javascript
class Queue {
    constructor() {
        this.dataStore = [];
    }

    enqueue(element) {
        this.dataStore.push(element)
    }

    dequeue() {
        this.dataStore.shift();
    }

    front() {
        return this.dataStore[0];
    }

    back() {
        return this.dataStore[this.dataStore.length - 1];
    }

    empty() {
        return this.dataStore.length === 0
    }

    toString() {
        return this.dataStore.join(' ');
    }
}
```

### Example

* Printer job queue

