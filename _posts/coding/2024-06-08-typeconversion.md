---
layout: post
title: JAVASCRIPT 데이터 형 변환
date: 2024-06-08 12:24 +0900
description: JAVASCRIPT 데이터 형 변환에 대해 알아보기
image: ../assets/img/typeconversion.jpg
category: 자바스크립트
tags: JAVASCRIPT HTML CSS TypeConversion
published: true
sitemap: true
---

## 데이터 형 변환(Type Conversion)이란?

▶ 자바스크립트에서 데이터 형 변환(Type Conversion)은 값의 데이터 타입을 변경하는 과정입니다.<br>
자바스크립트는 동적 타입 언어이므로 값의 타입이 자동으로 변환될 수 있는데 이 형 변환은 **암시적(Implicit)**으로 또는 **명시적(Explicit)**으로 이루어질 수 있습니다.

### 1. 암시적 형 변환(Implicit Type Conversion)

▶ 암시적 형 변환 또는 타입 강제 변환(Type Coercion)은 자바스크립트 엔진이 자동으로 수행하는 형 변환을 의미하며 주로 연산자에 의해 발생합니다. 간단한 예시를 통해 살펴보겠습니다.

#### 01. 문자열 변환

- 자바스크립트는 문자열과 다른 타입의 값을 더할 때, 다른 타입의 값을 문자열로 변환합니다.

````javascript
let result = '5' + 2;
console.log(result); // '52' (문자열)

result = 'Hello' + true;
console.log(result); // 'Hellotrue' (문자열)
````

#### 02. 숫자 변환

- 덧셈을 제외한 산술 연산자는 문자열을 숫자로 변환합니다.

````javascript
let result = '5' - 2;
console.log(result); // 3 (숫자)

result = '10' * 2;
console.log(result); // 20 (숫자)

result = '10' / '2';
console.log(result); // 5 (숫자)
````

#### 03. 불리언 변환

- 조건문에서 사용될 때, 자바스크립트는 값을 불리언으로 변환합니다. 0, NaN, null, undefined, 그리고 빈 문자열('')은 false로 변환되고, 나머지 값은 true로 변환됩니다.

````javascript
console.log(Boolean(0)); // false
console.log(Boolean('')); // false
console.log(Boolean('Hello')); // true
console.log(Boolean(1)); // true
````

### 2. 명시적 형 변환(Explicit Type Conversion)

▶ 명시적 형 변환은 개발자가 명시적으로 타입 변환을 수행하는 것을 의미하며 자바스크립트는 이를 위한 여러 가지 방법을 제공합니다.

#### 01. 문자열 변환

- String() 함수를 사용하거나, .toString() 메서드를 호출하여 값을 문자열로 변환할 수 있습니다.

````javascript
let value = 123;
let strValue = String(value);
console.log(strValue); // '123' (문자열)

value = true;
strValue = value.toString();
console.log(strValue); // 'true' (문자열)
````

#### 02. 숫자 변환

- Number() 함수를 사용하거나 parseInt(), parseFloat() 함수를 사용하여 값을 숫자로 변환할 수 있습니다.

````javascript
let str = '123';
let num = Number(str);
console.log(num); // 123 (숫자)

str = '123.45';
num = parseInt(str);
console.log(num); // 123 (숫자, 정수)

num = parseFloat(str);
console.log(num); // 123.45 (숫자, 부동 소수점)
````

#### 03. 불리언 변환

- Boolean() 함수를 사용하여 값을 불리언으로 변환할 수 있습니다.

````javascript
let value = 0;
let boolValue = Boolean(value);
console.log(boolValue); // false

value = 'Hello';
boolValue = Boolean(value);
console.log(boolValue); // true
````

#### 04. 산술 연산과 암시적 형 변환

- 산술 연산자(+, -, *, /)는 피연산자를 숫자로 변환하려고 시도합니다.

````javascript
let result = '5' - '2';
console.log(result); // 3 (숫자)

result = '5' * '2';
console.log(result); // 10 (숫자)

result = '10' / '2';
console.log(result); // 5 (숫자)
````

#### 05. 비교 연산과 암시적 형 변환

- 비교 연산자(==, !=, <, >, <=, >=)는 피연산자를 숫자나 문자열로 변환합니다.

````javascript
console.log('5' == 5); // true (암시적 형 변환)
console.log('5' === 5); // false (엄격한 비교, 형 변환 없음)
console.log('5' < 10); // true (숫자 비교)
console.log('10' > 5); // true (숫자 비교)
````

#### 06. 논리 연산과 암시적 형 변환

- 논리 연산자는 피연산자를 불리언 값으로 변환합니다.

````javascript
console.log(!0); // true
console.log(!!1); // true
console.log('Hello' && 'World'); // 'World' (모두 참일 때 마지막 값을 반환)
console.log('' || 'Default'); // 'Default' (하나가 참이면 그 값을 반환)
````

### 결론

▶ 자바스크립트에서 데이터 형 변환은 코드를 작성하고 디버깅할 때 자주 접하게 되는 중요한 개념입니다.<br>
암시적 형 변환은 코드의 간결함을 제공하지만 예기치 않은 결과를 초래할 수 있어 명시적 형 변환을 사용하면 코드의 가독성과 명확성을 높일 수 있습니다.<br>
따라서, 자바스크립트 개발자는 형 변환이 어떻게 작동하는지 잘 이해하고 필요에 따라 명시적 형 변환을 적절히 사용하면 효율성을 높일 수 있습니다.

<br>

이렇게 오늘은 자바스크립트의 데이터 형 변환에 대해 알아봤는데요,<br>
면접에서도 충분히 나올 수 있는 질문이기 때문에 미리 공부해두면 좋을 것 같네요!
그렇다면 저는 다음에 또다른 면접에 대비한 내용을 들고오도록 하겠습니다 😁!