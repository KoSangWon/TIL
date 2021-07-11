## 배열
### 배열 맨 앞 또는 맨 뒤에 값을 추가하기
- shift(): 배열 맨 앞의 값을 제거
- unshift(): 배열 맨 앞에 새로운 값을 추가

### 2차원 배열 만들기
```js
// arr[5][2] (빈 배열 생성)
const arr1 = Array.from(Array(5), () => new Array(2)

// arr[5][2] (null로 초기화하여 생성)
const arr2 = Array.from(Array(5), () => Array(2).fill(null))
```

### 2진수 만들기
```js
const num = 23;
num.toString(2); // 10111
```

### 숫자 비교할 때
- 문자열 숫자인지 확인 잘하기

### 객체 키값
- Object.keys(dict);
- key in dict

### 대문자, 소문자 만들기
- str.toUpperCase()
- str.toLowerCase()

### 문자열 자르기
- string.substr(start,length)
- subString(start, end)

### for..in vs for..of
- for..in: key에 접근
```js
var obj = {
    a: 1, 
    b: 2, 
    c: 3
};

for (var prop in obj) {
    console.log(prop, obj[prop]); // a 1, b 2, c 3
}
```
- for..of: for of 반복문은 ES6에 추가된 새로운 컬렉션 전용 반복 구문입니다. for of 구문을 사용하기 위해선 컬렉션 객체가 [Symbol.iterator] 속성을 가지고 있어야만 합니다
```js
var iterable = [10, 20, 30];

for (var value of iterable) {
  console.log(value); // 10, 20, 30
}
```

