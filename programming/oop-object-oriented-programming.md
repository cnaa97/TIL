# OOP \(Object-Oriented Programming\)

### Class

클래스는 템플릿이며, 오브젝트 데이터 필드와 메서드를 가지고 있다.

```javascript
class Car {
    constructor(model) {
        this.model = model;
    }

    getModel() {
        return this.model;
    }

    getYear() {
        return this.year;
    }

    setYear(year) {
        this.year = year;
    }

    printDescription(){
        console.log(`This is a car ${this.model}`);
    }
}
```

### Object

오브젝트는 클래스의 인스턴스이다.

```javascript
let camry = new Car('camry');
soul.setYear(2008);
camry.printDescription();
```

### Encapsulation

데이터와 메서드를 안전하게 유지하기 위해 변경되지 않도록 한다.

자바스크립트에서 객체 속성을 숨기는 방법은 없기 때문에, 일종의 hack을 써야 한다. 먼저 접두사\(prefix\)를 이용하는 방법인데, 

```javascript
class Car {
    constructor(model) {
        this._model = model; 
    }
    getModel() {
        return this._model;
    }
}    
```

두 번째 방법은 생성자에서 클로저를 이용하는 방법이다. \(단 메서드는 생성자 내에서 정의되어야 한다.\)

```javascript
class Car {
    constructor(model) {
        let _model = model;
        
        this.getModel = function(){
            return _model;
        }
    }
}
```

심볼\(symbol\)을 이용할 수도 있다.

```javascript
let Car = (function () {
    let _modelKey = Symbol();

    class Car {
        constructor(model) {
            this[_modelKey] = model;
        }
        getModel() {
            return this[_modelKey];
        }
    }

    return Car;
})();
```

### Inheritance \(상속\)

상속은 부모 자식간의 관계이다. 코드의 재사용성을 위해 사용되는 개념이다.

### Polymorphism \(다형\)

같은 이름의 함수이지만, 다른 기능을 하는 것.

### Abstraction \(추상화\)

가상 클래스. 가상 함수는 가상 클래스에서 구현하지 않고, 부모를 가지고 있는 자식 클래스는 가상 함수를 구현해야 한다.

