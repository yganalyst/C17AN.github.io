---
title:  "[Typescript] - 타입스크립트의 변수 선언"
search: true
toc : true
toc_label : 네비게이션
header:
  teaser: "/assets/images/header/typescript.png"
toc_sticky : true
tag:
  - 타입스크립트
categories:
  - Typescript
excerpt: "타입스크립트 기초 - 변수 선언하기"
last_modified_at: 2020-03-27T17:06:00-05:00
---
<img src = "/assets/images/header/typescript.png">

---

## 1. 타입스크립트의 기본 타입

자바스크립트의 타입은 크게 수 / 불리언 / 문자열 / 객체 타입으로 나뉜다.

타입스크립트 역시 타입의 첫글자가 소문자로 변한 것 말고는 큰 차이는 없다. 😄

| 유형  | 자바스크립트 타입  |  타입스크립트 타입 |
|:-:|:-:|:-:|
| 숫자  | Number   | number  |
| 문자열  | String  | string  |
| 불리언  | Boolean  | boolean  |  
| 객체  | Object  | object  |  

---

```javascript
let a = 24;
```

자바스크립트에서 변수를 사용할 때는 그저 var, let 등 변수를 선언하는 키워드와 함께 변수명에 값을 대입하는 게 끝이었다.   

하지만 타입스크립트는 C++ 이나 자바와 같은 타입 기반 언어처럼 변수를 선언할 때 타입을 지정해야만 한다.

```typescript
let a : number = 24;
```

타입스크립트에서는 이렇게 변수명 옆에 콜론 `(:)` 을 추가하고, 지정할 타입명을 정해준다.

---

## 2. 타입스크립트의 타입 검사

**- 자바스크립트 코드 (index.js)**
{: .notice--info}

```typescript
let a = 24;
a = "hello!";
console.log(a);
// hello!
```

자바스크립트의 변수는 변수의 리터럴에 따라 타입이 달라지고, 다른 타입간의 변수의 대입이 가능하다.

따라서 위의 코드는 아무런 문제가 없다. 😀

---

**- 타입스크립트 코드 (index.ts)**
{: .notice--info}

```typescript
let a : number = 24;
a = "hello!";
console.log(a);
// Err : Type "hello!" is not assignable to type 'number'
```

그러나 타입스크립트는 변수를 선언할 때 정의한 타입이 지켜져야만 해, 위의 코드는 타입 오류를 출력한다.

---

**- index.ts**
{: .notice--info}

```typescript
let a = 24; // 해당 시점에서 타입이 number 로 결정됨.
a = "hello!";
console.log(a);
// Err : Type "hello!" is not assignable to type 'number'
```

타입을 명시하지 않고 타입스크립트 변수를 사용하는 것도 가능하다.     
하지만 이 경우에는 가리키는 리터럴에 따라 변수의 타입이 결정된 후, 다른 타입의 리터럴을 가리키는 것이 불가능하다.   

만약 자바스크립트를 사용할 때처럼 변수를 사용하고 싶다면, `any` 타입으로 변수를 선언해주면 된다.   

**- index.ts**
{: .notice--info}

```typescript
let a : any = 24;
a = "maybe a string instead";
console.log(a);
// maybe a string instead
```

`any` 타입으로 선언된 변수는 리터럴에 따라 타입이 결정되지만, 타입을 명시하지 않았을 때와 다르게 다른 타입의 대입이 가능하다.

---

**- index.ts**
{: .notice--info}

```typescript
let a : undefined = undefined;
a = "maybe a string instead";
console.log(a);
// Type "maybe a string instead" is not assignable to type 'undefined'
```

자바스크립트에서는 값이 정해지지 않았을 때 `undefined` 라는 값을 가진다.  

타입스크립트 역시 값이 정해지지 않았을 때 `undefined` 라는 값을 갖지만, TS에서는 변수의 타입으로도 `undefined` 를 지정해줄 수 있다. 👍
