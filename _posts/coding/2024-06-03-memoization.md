---
layout: post
title: 메모이제이션(memoization)
date: 2024-06-03 11:39 +0900
description: 메모이제이션(memoization)에 대해 알아보기
image: ../assets/img/memoization.jpg
category: 리액트
tags: memoization 메모이제이션 REACT
published: true
sitemap: true
---

### 메모이제이션(memoization)이란?

▶ 메모이제이션(Memoization)은 동일한 계산을 반복하지 않도록 함수의 결과를 캐시(저장)하여 성능을 최적화하는 기술입니다. React에서 메모이제이션은 컴포넌트의 재렌더링을 최소화하고 컴포넌트 내에서 불필요한 연산을 방지하여 애플리케이션의 성능을 개선하는 데 사용되는데 **React.memo, useMemo, useCallback** 3가지 방식을 사용합니다.

### 1. React.memo

▶ React.memo는 고차 컴포넌트(Higher-Order Component)로 함수형 컴포넌트를 메모이제이션하여 props가 변경되지 않으면 해당 컴포넌트를 재렌더링하지 않습니다. 예시를 통해 살펴볼게요!

````jsx
import React from 'react';

const MyComponent = React.memo(({ value }) => {
  console.log('MyComponent rendered');
  return <div>{value}</div>;
});

export default function App() {
  const [count, setCount] = React.useState(0);

  return (
    <div>
      <button onClick={() => setCount(count + 1)}>Increment</button>
      <MyComponent value={count} />
    </div>
  );
}
````

- 위 예시에서 MyComponent는 React.memo로 래핑되어, value라는 props가 변경되지 않으면 재렌더링되지 않습니다.<br>
즉, 버튼을 클릭해도 value가 변경되지 않는다면 MyComponent는 다시 렌더링되지 않습니다.

### 2. useMemo

▶ useMemo는 값의 메모이제이션을 위한 훅으로, 연산 비용이 큰 계산의 결과를 캐싱하여 불필요한 재계산을 방지하며 주로 컴포넌트 내에서 복잡한 계산을 최적화할 때 사용됩니다. 예시를 통해 살펴볼게요!

````jsx
import React, { useState, useMemo } from 'react';

function expensiveCalculation(num) {
  console.log('Calculating...');
  return num * 2;
}

export default function App() {
  const [count, setCount] = useState(0);
  const [value, setValue] = useState(1);

  const result = useMemo(() => expensiveCalculation(value), [value]);

  return (
    <div>
      <button onClick={() => setCount(count + 1)}>Increment Count</button>
      <button onClick={() => setValue(value + 1)}>Increment Value</button>
      <div>Result: {result}</div>
    </div>
  );
}
````

- 위 예시에서 useMemo는 value가 변경될 때만 expensiveCalculation 함수를 호출하여 계산을 수행하며, count가 변경될 때는 result를 재계산하지 않습니다.

### 3. useCallback

▶ useCallback은 함수의 메모이제이션을 위한 훅으로, 컴포넌트가 렌더링될 때마다 동일한 함수를 재생성하지 않도록 해주며 주로 자식 컴포넌트에 콜백 함수를 props로 전달할 때 유용합니다. 예시를 통해 살펴볼게요!

````jsx
import React, { useState, useCallback } from 'react';

const MyButton = React.memo(({ onClick, children }) => {
  console.log('Button rendered:', children);
  return <button onClick={onClick}>{children}</button>;
});

export default function App() {
  const [count, setCount] = useState(0);

  const handleClick = useCallback(() => {
    setCount(count + 1);
  }, [count]);

  return (
    <div>
      <MyButton onClick={handleClick}>Increment</MyButton>
      <div>Count: {count}</div>
    </div>
  );
}
````

- 위 예시에서 useCallback은 handleClick 함수를 메모이제이션하고 있으며, count가 변경되지 않으면 MyButton 컴포넌트가 재렌더링되지 않도록 합니다.

### 4. 메모이제이션 사용 시 고려사항

▶ 메모이제이션을 사용할 땐 다음과 같은 사항들을 고려해야합니다.

1. 적절한 사용
: 메모이제이션은 성능 최적화에 도움이 되지만 불필요하게 사용하면 메모리 사용량이 증가하고 코드가 복잡해질 수 있습니다. 따라서 실제로 성능 문제를 겪고 있는 경우에만 사용하는 것이 좋습니다.

2. 의존성 배열
: useMemo와 useCallback 훅은 의존성 배열을 통해 언제 값을 다시 계산할지를 결정합니다. 이 배열을 정확하게 지정하지 않으면 메모이제이션의 장점을 잃거나 예상치 못한 버그가 발생할 수 있습니다.

3. 불변성
: 메모이제이션을 올바르게 활용하려면 상태나 props가 불변 객체임을 보장해야 합니다. 불변성을 유지하면 객체의 참조 값이 변경되지 않아 비교가 효율적으로 이루어집니다.

<br>

이렇게 오늘은 Pure Component에 대해 알아봤는데요,<br>
면접에서도 충분히 나올 수 있는 질문이기 때문에 미리 공부해두면 좋을 것 같네요!
그렇다면 저는 다음에 또다른 면접에 대비한 내용을 들고오도록 하겠습니다 😁!