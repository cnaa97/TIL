---
description: >-
  링크드리스트는 데이터 요소들의 선형 콜렉션이다. 메모리에서 물리적으로 정렬되어있는 선형을 말하는 것이 아니라 각각의 요소는 다음 포인트에
  대한 정보를 가지고 있다. 각 노드는 연속으로 구성되어있다. 이 구조는 효과적으로 요소를 삽입, 삭제할 수 있다.
---

# 링크드 리스트 \(Linked List\)

![Linked List](../../.gitbook/assets/image%20%282%29.png)

#### 노드로 사용할 클래스 정의

```javascript
class Node {
    constructor(value, next = null) {
        this.value = value;
        this.next = next;
    }

    toString(callback) {
        return this.value;
    }
}
```

#### 링크드리스트 클래스 정의

```javascript
class LinkedList {
    constructor() {
        this.head = null;
        this.tail = null;
    }

    add (value) {
        const newNode = new Node(value);

        if (!this.head) {
            this.head = newNode;
            this.tail = newNode;
            return this;
        }

        // 링크드리스트의 마지막 데이터 tail에 새 노드를 지정한다.
        this.tail.next = newNode;
        this.tail = newNode;
        return this;
    }

    remove(pointer) {
        if (!this.head) { return null; }

        let current = this.head;
        let before;
        let remove;
        let count = 0;

        if (pointer === 0) { // 첫 노드를 삭제
            remove = this.head;
            this.head = this.head.next;
            return remove;
        } else {
            while (count < pointer) {
                // 해당 포지션까지 이동해서 삭제
                before = current;
                remove = current.next;
                count++;
                current = current.next;
            }

            if (this.tail.value === remove.value) {
                this.tail = current;
            }

            before.next = remove.next;
            return remove;
        }
    }

    search (pointer) {
        let current = this.head;
        let count = 0;
        while (count < pointer) { // pointer 위치로 이동
            current = current.next;
            count++;
            console.log(current);
        }

        if (!current) {
            console.log("There is no result.");
            return false;
        }

        return current.value;
    }

    removeHead() {
        if (!this.head) { return null; }

        const deletedHead = this.head;

        if (this.head.next) {
            this.head = this.head.next;
        } else {
            this.head = null;
            this.tail = null;
        }

        return deletedHead;
    }

    toArray() {
        const nodes = [];
        let currentNode = this.head;
        while (currentNode) {
            nodes.push(currentNode);
            currentNode = currentNode.next;
        }
        return nodes;
    }

    toString() {
        return this.toArray().map(node => node.toString()).toString();
    }
}
```

