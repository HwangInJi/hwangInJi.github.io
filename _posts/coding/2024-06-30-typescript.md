---
layout: post
title: 자바스크립트 타입스크립트
date: 2024-06-30 13:35 +0900
description: 자바스크립트에 대해 알아보기
image: ../assets/img/typescript.jpg
category: JavaScript
tags: JavaScript TypeScript
published: true
sitemap: true
---

## 자바스크립트에서의 타입스크립트

▶ 타입스크립트(TypeScript)는 자바스크립트의 슈퍼셋(Superset)으로, 자바스크립트에 정적 타입 지정 기능을 추가한 언어입니다. 타입스크립트는 마이크로소프트에 의해 개발되었으며, 대규모 애플리케이션 개발 시 코드의 가독성과 유지보수성을 향상시키기 위해 설계되었습니다.

### 타입스크립트의 주요 특징

#### 정적 타입 지정

타입스크립트는 변수, 함수의 매개변수 및 반환 값 등에 타입을 명시적으로 지정할 수 있습니다. 이를 통해 컴파일 타임에 타입 검사를 수행하여 잠재적인 오류를 사전에 방지할 수 있습니다.

```typescript
let message: string = 'Hello, TypeScript';
message = 42; // 오류: 'number' 타입을 'string' 타입에 할당할 수 없습니다.
```

#### 인터페이스와 타입 별칭

타입스크립트는 인터페이스와 타입 별칭을 통해 객체의 구조를 정의할 수 있습니다. 이를 통해 객체의 타입을 명확하게 지정할 수 있습니다.

```typescript
interface Person {
  name: string;
  age: number;
}

const john: Person = {
  name: 'John Doe',
  age: 25
};
```

#### 클래스와 모듈

타입스크립트는 ES6 클래스와 모듈 시스템을 지원하며, 이를 통해 객체 지향 프로그래밍을 더욱 쉽게 구현할 수 있습니다.

```typescript
class Animal {
  name: string;

  constructor(name: string) {
    this.name = name;
  }

  speak(): void {
    console.log(`${this.name} makes a noise.`);
  }
}

class Dog extends Animal {
  speak(): void {
    console.log(`${this.name} barks.`);
  }
}

const dog = new Dog('Rex');
dog.speak(); // Rex barks.
```

#### 제네릭

타입스크립트는 제네릭을 통해 함수와 클래스를 보다 유연하고 재사용 가능하게 만들 수 있습니다.

```typescript
function identity<T>(arg: T): T {
  return arg;
}

let output = identity<string>('Hello');
let output2 = identity<number>(42);
```

### 타입스크립트 설치 및 설정

타입스크립트를 사용하려면 먼저 Node.js와 npm이 설치되어 있어야 합니다. 그런 다음, npm을 통해 타입스크립트를 설치할 수 있습니다.

```bash
npm install -g typescript
```

타입스크립트 파일(`.ts` 확장자)을 컴파일하려면 `tsc` 명령어를 사용합니다.

```bash
tsc hello.ts
```

### 타입스크립트와 자바스크립트의 차이점

1. **타입 시스템**: 타입스크립트는 정적 타입 지정을 지원하며, 이를 통해 코드의 안정성과 가독성을 높일 수 있습니다. 자바스크립트는 동적 타입 언어로, 런타임에 타입이 결정됩니다.
   
2. **개발 도구**: 타입스크립트는 강력한 타입 시스템 덕분에 코드 에디터에서 더 나은 자동 완성, 타입 검사 및 리팩토링 기능을 제공합니다.

3. **런타임**: 타입스크립트는 컴파일 언어로, 브라우저나 Node.js에서 실행되기 전에 자바스크립트로 트랜스파일(transpile)됩니다. 자바스크립트는 인터프리터 언어로, 바로 실행될 수 있습니다.

### 타입스크립트 사용 예시

#### 기본 타입 사용

```typescript
let isDone: boolean = false;
let decimal: number = 6;
let color: string = "blue";
let list: number[] = [1, 2, 3];
```

#### 함수 타입 지정

```typescript
function add(x: number, y: number): number {
  return x + y;
}

let result = add(2, 3); // 5
```

### 타입스크립트와 자바스크립트의 통합

기존 자바스크립트 프로젝트에 타입스크립트를 점진적으로 도입할 수 있습니다. 자바스크립트 파일(`.js`)에 JSDoc 주석을 추가하여 타입 정보를 제공하거나, 프로젝트를 타입스크립트 파일(`.ts`)로 변환할 수 있습니다.

```javascript
// @ts-check

/**
 * Adds two numbers.
 * @param {number} a
 * @param {number} b
 * @returns {number}
 */
function add(a, b) {
  return a + b;
}
```

### 요약

타입스크립트는 자바스크립트의 확장 언어로, 정적 타입 지정과 다양한 기능을 제공하여 대규모 애플리케이션 개발을 더 효율적으로 만듭니다. 타입스크립트를 잘 활용하면 코드의 안정성과 유지보수성을 크게 향상시킬 수 있습니다.

<br />

이렇게 자바스크립트에서의 타입스크립트 개념과 활용 방법에 대해 알아보았는데요,<br />
타입스크립트를 도입하면 더 안정적이고 관리하기 쉬운 코드를 작성할 수 있습니다.<br />
그럼 전 다음에 또 다른 면접 질문을 가지고 돌아오겠습니다 😁!