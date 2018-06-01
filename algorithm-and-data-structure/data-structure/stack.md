# 스택 \(Stack\)

![](../../.gitbook/assets/image%20%284%29.png)

* LILO \(Last-In-Last-Out\)
* Stack Over Flow

  아이템 추가 시, 메모리 공간에 스택이 가득찼을 때 에러

* Stack Uner Flow 아이템 삭제 시, 더이상 삭제할 아이템이 없을 때

```javascript
class Stack {
    constructor() {
        this.dataStore = [];
        this.top = 0;
    }

    push (item){
        // 예를 들어 메모리에 최대 5개의 아이템이 들어갈 경우
        if (this.top < 3) {
            this.dataStore.push(item);
            this.top++;
        } else {
            // stack overflow 발생
            console.log("stack is full, adbort push to prevent stack overflow");
        }
    }

    pop (){
        if (this.top > 0) {
            this.dataStore.pop();
            this.top--;
        } else {
            // stack underflow 발생
            console.log("stack is emtpy, adbort pop to prevent stack underflow");
        }
    }

    peek (){
        return this.dataStore[this.top - 1];
    }

    length (){
        return this.top;
    }

    clear (){
        this.dataStore = [];
        this.top = 0;
    }

    print (){
        return this.dataStore.join(', ');
    }
}
```



