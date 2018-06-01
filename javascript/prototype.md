# 프로토타입 \(Prototype\)

### 프로토타입 패턴

* 모든 함수는 **프로토타입 프로퍼티**를 가진다.
* 참조 타입의 인스턴스가 가져야 할 프로퍼티, 메서드를 담고있는 객체이다.
* **프로토타입 프로퍼티**는 객체 인스턴스 전체에서 공유된다.

### 프토토타입 동작

* 함수가 생성될 때마다 특정 규칙에 따라 prototype 프로퍼티가 생성된다.
* 모든 프로토타입은 constructor 프로퍼티를 갖는다.
  * constructor 는 프토토타입이 프로터피로서 소속된 함수를 가리킨다.
    * `Person.prototype.constructor` -&gt; `Person`
* 인스턴스 내부에서는 생성자의 프로토타입을 가르키는 포인터가 생성된다.
  * 인스턴스와 직접 연결되는 것은 **생성자의 프로토타입**이며, 생성자 자체가 아니다.

```javascript
Person.prototype.isPrototypeOf(person1); // true
Person.prototype.isPrototypeOf(person2); // true
```

* 객체에서 프로퍼티를 참조할 때, 인스턴스에서부터 검색을 하며, **프로퍼티가 없으면 포인터를 프로토타입으로 올려서** 검색을 계속한다.
* 인스턴스에서 프로토타입의 값은 읽기만 가능하며, **수정 불가능**하다.

### 동적 성질

```javascript
function Person (name){
  this.name = name;
}

var juno = new Person('Junho Park');
juno.sayName(); // error

Person.prototype.sayName = function(){
  console.log(this.name);
}
juno.sayName(); // 'Junho Park' 출력
```

* `juno` 객체가 생성된 후에도 `Person` 의 프토토타입이 바뀌면,  반영된다.
* 인스턴스와 프로토타입 사이의 느슨한 연결 때문이다.

### 상속

객체 지향 언어는 인터페이스 상속과 구현 상속을 지원한다. 자바스크립트에서는 시그너처\(매개변수에 따라 동작방식이 달라지는 개념\)가 없으므로 인터페이스 상속은 불가능하고, **구현 상속만 지원**한다.

자바스크립트에서 상속은 프로토타입 체인을 통해서 이루어진다. 두 가지 참조 타입 사이에서 프로퍼티와 메서드를 상속한다. 

```javascript
function Person (name){
  this.name = name;
}
Person.prototype.aboutMe = function(){
  console.log(this.name);
}

function Man () {
  this.gender = 'MALE';
}
// Man은 Person을 상속받는다.
Man.prototype = new Person();

// 상속받은 메서드 재정의
Man.prototype.aboutMe = function(){
  console.log(this.gender, this.name);
}

console.log(Man.prototype.constructor === Person); // true
```



