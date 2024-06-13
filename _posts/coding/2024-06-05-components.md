---
layout: post
title: 제어 & 비제어 컴포넌트
date: 2024-06-05 11:24 +0900
description: 제어 & 비제어 컴포넌트에 대해 알아보기
image: ../assets/img/components.jpg
category: 리액트
tags: REACT Components
published: true
sitemap: true
---

## 1. 제어 컴포넌트 (Controlled Components)란?

▶ 제어 컴포넌트는 리액트 상태(state)를 통해 입력값을 제어하는 컴포넌트입니다.<br>
이는 입력 요소의 값이 리액트 컴포넌트의 상태에 의해 관리됨을 의미하는데 사용자가 입력 필드에 값을 입력할 때마다 onChange 이벤트 핸들러가 호출되어 컴포넌트의 상태를 업데이트하고, 그 상태가 다시 입력 필드의 값으로 설정됩니다. 이런 구조 덕분에 입력값이 언제나 컴포넌트의 상태와 동기화됩니다. 간단한 예시를 살펴보겠습니다.

````jsx
import React, { useState } from 'react';

function ControlledInput() {
  const [value, setValue] = useState('');

  const handleChange = (event) => {
    setValue(event.target.value);
  };

  const handleSubmit = (event) => {
    event.preventDefault();
    alert('입력된 값: ' + value);
  };

  return (
    <form onSubmit={handleSubmit}>
      <label>
        입력:
        <input type="text" value={value} onChange={handleChange} />
      </label>
      <button type="submit">제출</button>
    </form>
  );
}

export default ControlledInput;
````

- 위의 예시에서 input 요소의 value 속성은 컴포넌트의 상태(value)와 연결되어 있습니다.
- 여기서 onChange 이벤트가 발생할 때마다 handleChange 함수가 호출되고, 이 함수는 상태를 업데이트합니다.
- 만약 상태가 변경되면 리액트는 render 메서드를 호출하여 UI를 갱신하게 되고, 이런 방식으로 입력값은 언제나 상태와 일치하게 유지됩니다.

### 제어 컴포넌트의 장점

1. 입력값에 대한 완전한 제어
: 컴포넌트는 사용자의 입력을 즉시 반영하고 검증할 수 있습니다.

2. 예측 가능한 상태 관리
: 상태는 항상 컴포넌트에 의해 관리되므로, 입력값을 쉽게 추적하고 디버깅할 수 있습니다.

3. 간편한 데이터 검증
: 입력값을 즉시 검증하고 피드백을 제공할 수 있습니다.

### 제어 컴포넌트의 단점

1. 더 많은 코드 작성
: 입력값을 처리하기 위해 상태와 이벤트 핸들러를 작성해야 합니다.

2. 성능 이슈
: 매우 큰 양의 데이터나 많은 입력 필드가 있는 경우, 모든 입력 변화에 대해 상태 업데이트와 다시 렌더링이 발생하여 성능 문제가 생길 수 있습니다.

## 2. 비제어 컴포넌트 (Uncontrolled Components)란?

▶ 비제어 컴포넌트는 입력값을 컴포넌트의 상태가 아닌 DOM 자체에서 직접 관리하는 컴포넌트입니다.<br>
여기서 입력 필드의 값은 리액트 상태와 동기화되지 않고, DOM 노드의 ref를 통해 직접 접근하여 값을 읽어옵니다. 간단한 예시를 살펴보겠습니다.

````jsx
import React, { useRef } from 'react';

function UncontrolledInput() {
  const inputRef = useRef(null);

  const handleSubmit = (event) => {
    event.preventDefault();
    alert('입력된 값: ' + inputRef.current.value);
  };

  return (
    <form onSubmit={handleSubmit}>
      <label>
        입력:
        <input type="text" ref={inputRef} />
      </label>
      <button type="submit">제출</button>
    </form>
  );
}

export default UncontrolledInput;
````

- 위의 예시에서 input 요소는 ref 속성을 통해 DOM 노드에 접근합니다.
- 여기서 handleSubmit 함수에서는 inputRef.current.value를 사용하여 입력값을 직접 읽어옵니다.
- 이 때 입력값은 리액트 상태에 저장되지 않고 DOM에서 직접 관리됩니다.

### 비제어 컴포넌트의 장점

1. 적은 코드
: 상태와 이벤트 핸들러를 사용하지 않으므로 코드가 더 간단합니다.

2. 성능 최적화
: 매우 많은 양의 입력 필드를 처리할 때, 상태 업데이트와 재렌더링을 피할 수 있어 성능이 향상될 수 있습니다.

### 비제어 컴포넌트의 단점

1. 제어 어려움
: 입력값에 대한 즉각적인 검증이나 동기화가 어렵습니다.

2. 데이터 흐름의 일관성 부족
: 컴포넌트 상태와 DOM 상태가 분리되어 있어, 데이터 흐름을 추적하고 디버깅하기가 어려울 수 있습니다.

3. 참조 관리 필요
: ref를 사용하여 DOM 노드를 직접 참조해야 하므로, 코드가 복잡해질 수 있습니다.

### 결론

▶ 리액트에서 제어 컴포넌트와 비제어 컴포넌트는 각각의 장단점이 있으며, 상황에 맞게 선택하여 사용해야 합니다.<br>
먼저, 제어 컴포넌트는 입력값을 컴포넌트 상태로 관리하여 데이터 흐름을 예측 가능하게 만들지만 더 많은 코드 작성과 성능 이슈가 있을 수 있습니다.<br>
반면, 비제어 컴포넌트는 DOM을 직접 참조하여 입력값을 관리하므로 간단하고 성능이 좋을 수 있지만 입력값에 대한 제어가 어렵고 데이터 흐름이 일관되지 않을 수 있습니다.<br>
따라서 단순한 입력 필드나 성능이 중요한 경우 비제어 컴포넌트를 사용하고, 입력값의 즉각적인 검증이 필요하거나 상태 관리를 명확하게 해야 하는 경우 제어 컴포넌트를 사용하는 것이 좋으며 리액트에서는 두 가지 방식을 혼합하여 사용하는 것도 가능하므로 요구사항에 맞게 적절히 조합하여 사용하면 효율을 높일 수 있습니다.

<br>

이렇게 오늘은 제어 & 비제어 컴포넌트에 대해 알아봤는데요,<br>
면접에서도 충분히 나올 수 있는 질문이기 때문에 미리 공부해두면 좋을 것 같네요!
그렇다면 저는 다음에 또다른 면접에 대비한 내용을 들고오도록 하겠습니다 😁!