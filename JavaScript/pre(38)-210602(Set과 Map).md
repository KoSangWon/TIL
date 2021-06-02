# Set과 Map
## 1. Set
- **Set 객체는 중복되지 않는 유일한 값들의 집합(set)이다.** Set 객체는 **배열과 유사**하지만 차이가 있다
  - 동일 값 중복 포함 여부, 요소 순서의 의미 여부, 인덱스로 요소 접근 여부

- 이러한 Set 객체의 특성은 수학적 집합의 특성과 일치한다. Set은 수학적 집합을 구현하기 위한 자료구조다. 따라서 Set을 통해 교집합, 합집합, 차집합, 여집합 등을 구현할 수 있다.

### 1.1. Set 객체의 생성
- Set 객체는 Set 생성자 함수로 생성한다. 인수를 전달하지 않으면 빈 Set 객체가 생성된다.
```js
const set = new Set();
console.log(set); // Set(0) {}
```
- **Set 생성자 함수는 이터러블을 인수로 전달받아 Set 객체를 생성한다. 이때 이터러블의 중복된 값은 Set 객체에 요소로 저장되지 않는다.**
```js
const set1 = new Set([1, 2, 3, 3]);
console.log(set1); // Set(3) {1, 2, 3}

const set2 = new Set('hello');
console.log(set2); // Set(4) {"h", "e", "l", "o"}
```

- 중복 요소 제거 가능
```js
// 배열의 중복 요소 제거
const uniq = array => array.filter((v, i, self) => self.indexOf(v) === i);
console.log(uniq([2, 1, 2, 3, 4, 3, 4])); // [2, 1, 3, 4]

// Set을 사용한 배열의 중복 요소 제거
const uniq = array => [...new Set(array)];
console.log(uniq([2, 1, 2, 3, 4, 3, 4])); // [2, 1, 3, 4]
```

### 1.2. 요소 개수 확인
- Set.prototype.size 프로퍼티를 사용한다.
```js
const { size } = new Set([1, 2, 3, 3]);
console.log(size); // 3
```

- size 프로퍼티는 setter 함수 없이 getter 함수만 존재하는 접근자 프로퍼티다. 따라서 size 프로퍼티에 숫자를 할당하여 Set 객체의 요소 개수를 변경할 수 없다.
```js
const set = new Set([1, 2, 3]);

console.log(Object.getOwnPropertyDescriptor(Set.prototype, 'size'));
// {set: undefined, enumerable: false, configurable: true, get: ƒ}

set.size = 10; // 무시된다.
console.log(set.size); // 3
```

### 1.3. 요소 추가
- Set.prototype.add 메서드를 사용한다.
```js
const set = new Set();
console.log(set); // Set(0) {}

set.add(1);
console.log(set); // Set(1) {1}
```

- add 메서드는 새로운 요소가 추가된 Set 객체를 반환한다. 따라서 add 메서드를 호출한 후에 add 메서드를 연속적으로 호출할 수 있다. 
```js
const set = new Set();

set.add(1).add(2);
console.log(set); // Set(2) {1, 2}
```

- Set 객체에 중복된 요소의 추가는 허용되지 않는다. 이때 에러가 발생하지는 않고 무시된다.
```js
const set = new Set();

set.add(1).add(2).add(2);
console.log(set); // Set(2) {1, 2}
```

- 일치 비교 연산자 ===를 사용하면 NaN과 NaN을 다르다고 평가한다. 하지만 Set객체는 같다고 평가하여 중복 추가를 허용하지 않는다. 또한 비교 연산자 ===와 마찬가지로 +0과 -0도 같다고 평가하여 중복 추가를 허용하지 않는다.

```js
const set = new Set();

console.log(NaN === NaN); // false
console.log(0 === -0); // true

// NaN과 NaN을 같다고 평가하여 중복 추가를 허용하지 않는다.
set.add(NaN).add(NaN);
console.log(set); // Set(1) {NaN}

// +0과 -0을 같다고 평가하여 중복 추가를 허용하지 않는다.
set.add(0).add(-0);
console.log(set); // Set(2) {NaN, 0}
```

- Set 객체는 객체와 배열과 같이 자바스크립트의 모든 값을 요소로 저장할 수 있다.

### 1.4. 요소 존재 여부 확인
- Set.prototype.has 메서드를 사용한다. has 메서드는 특정 요소의 존재 여부를 나타내는 불리언 값을 반환한다. 
```js
const set = new Set([1, 2, 3]);

console.log(set.has(2)); // true
console.log(set.has(4)); // false
```


### 1.5. 요소 삭제
- Set.prototype.delete 메서드를 사용한다. delete 메서드는 삭제 성공 여부를 나타내는 불리언 값을 반환한다.
- delete 메서드에는 인덱스가 아니라 삭제하려는 요소값을 인수로 전달해야 한다. Set 객체는 순서에 의미가 없다. 다시 말해, 배열과 같이 인덱스를 갖지 않는다.
```js
const set = new Set([1, 2, 3]);

// 요소 2를 삭제한다.
set.delete(2);
console.log(set); // Set(2) {1, 3}

// 요소 1을 삭제한다.
set.delete(1);
console.log(set); // Set(1) {3}
```
- 존재하지 않는 Set 객체의 요소를 삭제하려 하면 에러없이 무시된다.

- delete 메서드는 삭제 성공 여부를 나타내는 불리언 값을 반환한다. 따라서 add 메서드와 달리 연속적으로 호출(method chaining)할 수 없다.
```js
const set = new Set([1, 2, 3]);

// delete는 불리언 값을 반환한다.
set.delete(1).delete(2); // TypeError: set.delete(...).delete is not a function
```

### 1.6. 요소 일괄 삭제
- Set.prototype.clear 메서드를 사용한다. clear 메서드는 언제나 undefined를 반환한다.
```js
const set = new Set([1, 2, 3]);

set.clear();
console.log(set); // Set(0) {}
```

### 1.7. 요소 순회
- Set.prototype.forEach 메서드를 사용한다. 
- Set.prototype.forEach 메서드는 Array.prototype.forEach 메서드와 유사하게 콜백 함수와 forEach 메서드의 콜백 함수 내부에서 this로 사용될 객체(옵션)를 인수로 전달한다. 이때 콜백 함수는 3개의 인수를 전달받는다.
  - 첫 번째 인수: 현재 순회 중인 요소값
  - 두 번째 인수: 현재 순회 중인 요소값
  - 세 번째 인수: 현재 순회 중인 Set 객체 자체

- 첫 번째 인수와 두 번째 인수는 같은 값이다. 이처럼 동작하는 이유는 Set.prototype.forEach 메서드와 인터페이스를 통일하기 위함이며 다른 의미는 없다. 
- Array.prototype.forEach 메서드의 콜백 함수는 두 번째 인수로 현재 순회 중인 요소의 인덱스를 전달받는다. 하지만 Set 객체는 순서에 의미가 없어 배열과 같이 인덱스를 갖지 않는다.
```js
const set = new Set([1, 2, 3]);

set.forEach((v, v2, set) => console.log(v, v2, set));
/*
1 1 Set(3) {1, 2, 3}
2 2 Set(3) {1, 2, 3}
3 3 Set(3) {1, 2, 3}
*/
```

- **Set 객체는 이터러블이다.** 따라서 for...of 문으로 순회할 수 있으며, 스프레드 문법과 배열 디스트럭처링 할당의 대상이 될 수도 있다.
```js
const set = new Set([1, 2, 3]);

// Set 객체는 Set.prototype의 Symbol.iterator 메서드를 상속받는 이터러블이다.
console.log(Symbol.iterator in set); // true

// 이터러블인 Set 객체는 for...of 문으로 순회할 수 있다.
for (const value of set) {
  console.log(value); // 1 2 3
}

// 이터러블인 Set 객체는 스프레드 문법의 대상이 될 수 있다.
console.log([...set]); // [1, 2, 3]

// 이터러블인 Set 객체는 배열 디스트럭처링 할당의 대상이 될 수 있다.
const [a, ...rest] = [...set];
console.log(a, rest); // 1, [2, 3]
```

- Set 객체는 요소의 순서에 의미를 갖지 않지만 Set 객체를 순회하는 순서는 요소가 추가된 순서를 따른다. 이는 ECMAScript 사양에 규정되어 있지는 않지만 다른 이터러블의 순회와 호환성을 유지하기 위함이다.

### 1.8. 집합 연산
- Set 객체는 수학적 집합을 구현하기 위한 자료구조다. 따라서 Set 객체를 통해 교집합, 합집합, 차집합 등을 구현할 수 있다. 

## 2. Map
- **Map 객체는 키와 값의 쌍으로 이루어진 컬렉션이다.** Map 객체는 **객체와 유사**하지만 다음과 같은 차이가 있다.
- 객체의 키로 사용할 수 있는 값은 문자열 또는 심벌 값, Map 객체는 객체를 포함한 모든 값
- 객체는 이터러블이 없지만 Map 객체는 이터러블이 있다.
- 객체는 요소 개수 확인 시 Object.keys(obj).length, Map 객체는 map.size

### 2.1. Map 객체 생성
- Map 객체는 Map 생성자 함수로 생성한다. 인수가 없으면 빈 Map 객체 생성.
```js
const map = new Map();
console.log(map); // Map(0) {}
```
- **Map 생성자 함수는 이터러블을 인수로 전달받아 Map 객체를 생성한다. 이때 인수로 전달되는 이터러블은 키와 값의 쌍으로 이루어진 요소로 구성되어야 한다.**
```js
const map1 = new Map([['key1', 'value1'], ['key2', 'value2']]);
console.log(map1); // Map(2) {"key1" => "value1", "key2" => "value2"}

const map2 = new Map([1, 2]); // TypeError: Iterator value 1 is not an entry object
```

- Map 생성자 함수의 인수로 전달한 이터러블에 중복된 키를 갖는 요소가 존재하면 값이 덮어써진다. 따라서 Map 객체에는 중복된 키를 갖는 요소가 존재할 수 없다.
```js
const map = new Map([['key1', 'value1'], ['key1', 'value2']]);
console.log(map); // Map(1) {"key1" => "value2"}
```

### 2.2. 요소 개수 확인
- Map 객체의 요소 개수를 확인할 때는 Map.prototype.size 프로퍼티를 사용한다.
```js
const { size } = new Map([['key1', 'value1'], ['key2', 'value2']]);
console.log(size); // 2
```
- size프로퍼티는 접근자 프로퍼티다. 따라서 요소 개수를 변경할 수 없다.

### 2.3. 요소 추가
- Map.prototype.set 메서드를 사용한다.
```js
const map = new Map();
console.log(map); // Map(0) {}

map.set('key1', 'value1');
console.log(map); // Map(1) {"key1" => "value1"}
```
- set 메서드는 새로운 요소가 추가된 Map 객체를 반환한다. 따라서 set 메서드를 호출한 후에 set 메서드를 연속적으로 호출(method chaining)할 수 있다.
- Map 객체에는 중복된 키를 갖는 요소가 존재할 수 없기 때문에 중복된 키를 갖는 요소를 추가하면 값이 덮어써진다. 이때 에러가 발생하지는 않는다.

```js
const map = new Map();

map
  .set('key1', 'value1')
  .set('key1', 'value2');

console.log(map); // Map(1) {"key1" => "value2"}
```

- NaN, +0/-0 에 대해 중복 추가를 허용하지 않는다.
```js
const map = new Map();

console.log(NaN === NaN); // false
console.log(0 === -0); // true

// NaN과 NaN을 같다고 평가하여 중복 추가를 허용하지 않는다.
map.set(NaN, 'value1').set(NaN, 'value2');
console.log(map); // Map(1) { NaN => 'value2' }

// +0과 -0을 같다고 평가하여 중복 추가를 허용하지 않는다.
map.set(0, 'value1').set(-0, 'value2');
console.log(map); // Map(2) { NaN => 'value2', 0 => 'value2' }
```

- 객체는 문자열 또는 심벌 값만 키로 사용할 수 있다. 하지만 Map 객체는 키 타입에 제한이 없다. 따라서 객체를 포함한 모든 값을 키로 사용할 수 있다. 이는 Map 객체와 일반 객체의 가장 두드러지는 차이점이다.
```js
const map = new Map();

const lee = { name: 'Lee' };
const kim = { name: 'Kim' };

// 객체도 키로 사용할 수 있다.
map
  .set(lee, 'developer')
  .set(kim, 'designer');

console.log(map);
// Map(2) { {name: "Lee"} => "developer", {name: "Kim"} => "designer" }
```

### 2.4. 요소 취득
- Map.prototype.get을 사용한다. get 메서드의 인수로 키를 전달하면 Map 객체에서 인수로 전달한 키를 갖는 값을 반환한다. Map 객체에서 인수로 전달한 키를 갖는 요소가 존재하지 않으면 undefined를 반환한다.
```js
const map = new Map();

const lee = { name: 'Lee' };
const kim = { name: 'Kim' };

map
  .set(lee, 'developer')
  .set(kim, 'designer');

console.log(map.get(lee)); // developer
console.log(map.get('key')); // undefined
```

### 2.5. 요소 존재 여부 확인
- Map.prototype.has 메서드를 사용한다. has 메서드는 특정 요소의 존재 여부를 나타내는 불리언 값을 반환한다.
```js
const lee = { name: 'Lee' };
const kim = { name: 'Kim' };

const map = new Map([[lee, 'developer'], [kim, 'designer']]);

console.log(map.has(lee)); // true
console.log(map.has('key')); // false
```

### 2.6. 요소 삭제
- Map.prototype.delete 메서드를 사용한다. 삭제 성공 여부를 불리언 값으로 반환한다. 
```js
const lee = { name: 'Lee' };
const kim = { name: 'Kim' };

const map = new Map([[lee, 'developer'], [kim, 'designer']]);

map.delete(kim);
console.log(map); // Map(1) { {name: "Lee"} => "developer" }
```

- 만약 존재하지 않은 키를 삭제하면 에러 없이 무시된다.
- method chaining을 할 수 없다.

### 2.7. 요소 일괄 삭제
- Map.prototype.clear 메서드를 사용한다. clear 메서드는 언제나 undefined를 반환한다.
```js
const lee = { name: 'Lee' };
const kim = { name: 'Kim' };

const map = new Map([[lee, 'developer'], [kim, 'designer']]);

map.clear();
console.log(map); // Map(0) {}
```

### 2.8. 요소 순회
- Map.prototype.forEach 메서드를 사용한다. Array.prototype.forEach와 유사하게 콜백함수, forEach 메서드의 콜백 함수 내부에서 this로 사용될 객체(옵션)을 인수로 받는다. 
- 이때 콜백 함수는 다음과 같이 3개의 인수를 전달받는다.
  - 첫 번째 인수: 현재 순회 중인 요소값
  - 두 번째 인수: 현재 순회 중인 요소키
  - 세 번째 인수: 현재 순회 중인 Map 객체 자체

```js
const lee = { name: 'Lee' };
const kim = { name: 'Kim' };

const map = new Map([[lee, 'developer'], [kim, 'designer']]);

map.forEach((v, k, map) => console.log(v, k, map));
/*
developer {name: "Lee"} Map(2) {
  {name: "Lee"} => "developer",
  {name: "Kim"} => "designer"
}
designer {name: "Kim"} Map(2) {
  {name: "Lee"} => "developer",
  {name: "Kim"} => "designer"
}
*/
```

- **Map 객체는 이터러블이다.** 따라서 for...of 문으로 순회할 수 있으며, 스프레드 문법과 배열 디스트럭처링 할당의 대상이 될 수도 있다.
```js
const lee = { name: 'Lee' };
const kim = { name: 'Kim' };

const map = new Map([[lee, 'developer'], [kim, 'designer']]);

// Map 객체는 Map.prototype의 Symbol.iterator 메서드를 상속받는 이터러블이다.
console.log(Symbol.iterator in map); // true

// 이터러블인 Map 객체는 for...of 문으로 순회할 수 있다.
for (const entry of map) {
  console.log(entry); // [{name: "Lee"}, "developer"]  [{name: "Kim"}, "designer"]
}

// 이터러블인 Map 객체는 스프레드 문법의 대상이 될 수 있다.
console.log([...map]);
// [[{name: "Lee"}, "developer"], [{name: "Kim"}, "designer"]]

// 이터러블인 Map 객체는 배열 디스트럭처링 할당의 대상이 될 수 있다.
const [a, b] = map;
console.log(a, b); // [{name: "Lee"}, "developer"]  [{name: "Kim"}, "designer"]
```

- Map 객체는 이터러블이면서 동시에 이터레이터인 객체를 반환하는 메서드를 제공한다.
  - Map.prototype.keys => Map 객체에서 요소키를 값으로 갖는 이터러블이면서 동시에 이터레이터인 객체를 반환한다.
  - Map.prototype.values => Map 객체에서 요소값을 값으로 갖는 이터러블이면서 동시에 이터레이터인 객체를 반환한다.
  - Map.prototype.entries => Map 객체에서 요소키와 요소값을 값으로 갖는 이터러블이면서 동시에 이터레이터인 객체를 반환한다.

```js
const lee = { name: 'Lee' };
const kim = { name: 'Kim' };

const map = new Map([[lee, 'developer'], [kim, 'designer']]);

// Map.prototype.keys는 Map 객체에서 요소키를 값으로 갖는 이터레이터를 반환한다.
for (const key of map.keys()) {
  console.log(key); // {name: "Lee"} {name: "Kim"}
}

// Map.prototype.values는 Map 객체에서 요소값을 값으로 갖는 이터레이터를 반환한다.
for (const value of map.values()) {
  console.log(value); // developer designer
}

// Map.prototype.entries는 Map 객체에서 요소키와 요소값을 값으로 갖는 이터레이터를 반환한다.
for (const entry of map.entries()) {
  console.log(entry); // [{name: "Lee"}, "developer"]  [{name: "Kim"}, "designer"]
}
```
- Map 객체는 요소의 순서에 의미를 갖지 않지만 Map 객체를 순회하는 순서는 요소가 추가된 순서를 따른다. 이는 ECMAScript 사양에 규정되어 있지는 않지만 다른 이터러블의 순회와 호환성을 유지하기 위함이다.



