### Object 생성자 함수에 대해 설명하시오.
- new 연산자와 함께 Object 생성자 함수를 호출하면 빈 객체를 생성하여 반환한다. 빈 객체를 생성한 이후 프로퍼티 또는 메서드를 추가하여 객체를 완성할 수 있다.
- Object 생성자 함수를 사용해 객체를 생성하는 방식은 특별한 이유가 없다면 그다지 유용하지 않다. 객체 리터럴 사요이 더 유용하다.

### 객체 리터럴에 의한 객체 생성 방식의 문제점은?
객체 리터럴에 의한 객체 생성 방식은 단 하나의 객체만 생성한다. 따라서 동일한 프로퍼티를 갖는 객체를 여러 개 생성해야 하는 경우 매번 같은 프로퍼티를 기술해야 하기 때문에 비효율적이다.

### 생성자 함수에 의한 객체 생성 방식의 장점은?
생성자 함수에 의한 객체 생성 방식은 마치 객체(인스턴스)를 생성하기 위한 템플릿(클래스)처럼 생성자 함수를 사용하여 프로퍼티 구조가 동일한 객체 여러 개를 간편하게 생성할 수 있다.

### this 바인딩에 대해 설명하시오.
- this 바인딩은 함수 호출 방식에 따라 동적으로 결정된다.
- 일반 함수로서 호출 => 전역 객체
- 메서드로서 호출 => 메서드를 호출한 객체(마침표 앞의 객체)
- 생성자 함수로서 호출 => 생성자 함수가 (미래에) 생성할 인스턴스

### 생성자 함수의 인스턴스 생성 과정에 대해 설명하시오.
1. 인스턴스 생성과 this 바인딩
  - 암묵적으로 빈 객체가 생성된다. 이 빈 객체가 바로 (아직 완성되지는 않았지만) 생성자 함수가 생성한 인스턴스다. 
  - 빈 객체, 즉 인스턴스는 this에 바인딩된다. 이 처리는 런타임 이전에 실행된다.
2. 인스턴스 초기화
  - 런타임에 this에 바인딩되어 있는 인스턴스를 초기화한다. 
3. 인스턴스 반환
  - 생성자 함수 내부의 모든 처리가 끝나면 완성된 인스턴스가 바인딩된 this가 암묵적으로 반환된다.
  - this가 아닌 다른 객체를 명시적으로 반환하면 this가 반환되지 못하고 return 문에 명시한 객체가 반환된다.
  - 명시적으로 원시값을 반환하면 원시값 반환은 무시되고 암묵적으로 this가 반환된다.

### 바인딩(binding)이란?
식별자와 값을 연결하는 과정을 의미한다. 예를 들어, 변수 선언은 변수 이름(식별자)과 확보된 메모리 공간의 주소를 바인딩하는 것이다. this 바인딩은 this(키워드로 분류되지만 식별자 역할을 한다)와 this가 가리킬 객체를 바인딩하는 것이다.

### 내부 메서드 [[Call]]과 [[Construct]]가 무엇인가?
- 함수가 일반 함수로서 호출되면 함수 객체의 내부 메서드 [[Call]]이 호출되고 new 연산자와 함께 생성자 함수로서 호출되면 내부 메서드 [[Construct]]가 호출된다.
- 내부 메서드 [[Call]]을 갖는 함수 객체를 callable이라 하며, 내부 메서드 [[Construct]]를 갖는 함수 객체를 constructor, [[Construct]]를 갖지 않는 함수 객체를 non-constructor라고 부른다. callable은 호출할 수 있는 객체, 즉 함수를 말하며, constructor는 생성자 함수로서 호출할 수 있는 함수, non-constructor는 객체를 생성자 함수로서 호출할 수 없는 함수를 의미한다.

### constructor와 non-constructor의 종류는?
- constructor: 함수 선언문, 함수 표현식, 클래스(클래스도 함수다)
- non-constructor: 메서드(ES6 메서드 축약 표현), 화살표 함수

### new.target이 무엇인가?
- 생성자 함수가 new 연산자 없이 호출되는 것을 방지하기 위해 파스칼 케이스 컨벤션을 사용한다 하더라도 실수는 언제나 발생할 수 있다. 이러한 위험성을 회피하기 위해 ES6에서는 new.target을 지원한다.
- new 연산자와 함께 생성자 함수로서 호출되면 함수 내부의 new.target은 함수 자신을 가리킨다. new 연산자 없이 일반 함수로서 호출된 함수 내부의 new.target은 undefined다.
- 함수 내부에서 new.target을 사용하여 new 연산자와 생성자 함수로서 호출했는지 확인하여 그렇지 않은 경우 new 연산자와 함께 재귀 호출을 통해 생성자 함수로서 호출할 수 있다.
```js
// 생성자 함수
function Circle(radius) {
  // 이 함수가 new 연산자와 함께 호출되지 않았다면 new.target은 undefined다.
  if (!new.target) {
    // new 연산자와 함께 생성자 함수를 재귀 호출하여 생성된 인스턴스를 반환한다.
    return new Circle(radius);
  }

  this.radius = radius;
  this.getDiameter = function () {
    return 2 * this.radius;
  };
}

// new 연산자 없이 생성자 함수를 호출하여도 new.target을 통해 생성자 함수로서 호출된다.
const circle = Circle(5);
console.log(circle.getDiameter());
```

### 스코프 세이프 생성자 패턴이란?
- new.target은 ES6에서 도입된 최신 문법으로 IE에서는 지원하지 않는다. new.target을 사용할 수 없는 상황이라면 스코프 세이프 생성자 패턴을 사용할 수 있다.
```js
// Scope-Safe Constructor Pattern
function Circle(radius) {
  // 생성자 함수가 new 연산자와 함께 호출되면 함수의 선두에서 빈 객체를 생성하고
  // this에 바인딩한다. 이때 this와 Circle은 프로토타입에 의해 연결된다.

  // 이 함수가 new 연산자와 함께 호출되지 않았다면 이 시점의 this는 전역 객체 window를 가리킨다.
  // 즉, this와 Circle은 프로토타입에 의해 연결되지 않는다.
  if (!(this instanceof Circle)) {
    // new 연산자와 함께 호출하여 생성된 인스턴스를 반환한다.
    return new Circle(radius);
  }

  this.radius = radius;
  this.getDiameter = function () {
    return 2 * this.radius;
  };
}

// new 연산자 없이 생성자 함수를 호출하여도 생성자 함수로서 호출된다.
const circle = Circle(5);
console.log(circle.getDiameter()); // 10
```

### 빌트인 생성자 함수 호출 시 new 유무에 따른 결과
- Object, Function: new 연산자와 함께 호출했을 때와 동일하게 동작
- String, Number, Boolean: new 연산자와 호출하면 객체를 생성하여 반환하지만 new 없이 호출하면 문자열, 숫자, 불리언 값을 반환한다. 데이터 타입 변환을 한다.
