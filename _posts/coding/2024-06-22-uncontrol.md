---
layout: post
title: REACT 제어 컴포넌트 & 비제어 컴포넌트
date: 2024-06-22 15:10 +0900
description: 리액트의 제어 컴포넌트 & 비제어 컴포넌트에 대해 알아보기
image: ../assets/img/uncontrol.jpg
category: 리액트
tags: REACT Components
published: true
sitemap: true
---

## 제어 컴포넌트(Control Component)란?

▶ 제어 컴포넌트는 컴포넌트의 상태(state)가 폼 데이터와 함께 리액트 컴포넌트에 의해 제어되는 폼 요소입니다.<br>
이 컴포넌트는 사용자가 입력한 값을 컴포넌트 상태에 저장하고, 입력 값을 업데이트하는 방식으로 동작합니다. 이로 인해 상태와 폼 입력 값이 항상 일치하게 됩니다.

### 제어 컴포넌트의 특징

1. **상태 관리**: 입력 값이 컴포넌트의 상태로 관리되므로, 상태를 통해 입력 값을 제어할 수 있습니다.
2. **양방향 데이터 바인딩**: 입력 값이 상태에 의해 결정되며, 상태가 변경되면 입력 값도 변경됩니다.
3. **쉽고 명확한 데이터 흐름**: 컴포넌트 상태가 입력 값을 제어하므로, 데이터 흐름이 명확하고 디버깅이 용이합니다.

### 제어 컴포넌트 예시

```javascript
import React, { useState } from "react";

function ControlledComponent() {
  const [value, setValue] = useState("");

  const handleChange = (event) => {
    setValue(event.target.value);
  };

  return (
    <div>
      <input type="text" value={value} onChange={handleChange} />
      <p>입력한 값: {value}</p>
    </div>
  );
}

export default ControlledComponent;
```

- 위의 예시에서 `input` 요소의 값은 `value` 상태에 의해 제어됩니다. 사용자가 입력할 때마다 `handleChange` 함수가 호출되어 상태가 업데이트됩니다.

## 비제어 컴포넌트(Uncontrolled Component)란?

▶ 비제어 컴포넌트는 폼 데이터가 리액트 컴포넌트의 상태가 아닌 DOM 자체에서 관리되는 폼 요소입니다.<br>
이 컴포넌트는 리액트의 레퍼런스를 사용하여 DOM 요소에 직접 접근하고, 값을 읽거나 설정하는 방식으로 동작합니다.

### 비제어 컴포넌트의 특징

1. **DOM 접근**: 입력 값이 DOM에서 직접 관리되므로, 레퍼런스를 통해 값을 읽거나 설정할 수 있습니다.
2. **간단한 구현**: 상태를 사용하지 않으므로 구현이 간단하고, 간단한 폼에서 유용합니다.
3. **데이터 흐름 복잡성**: 상태를 사용하지 않기 때문에 데이터 흐름이 복잡해질 수 있으며, 디버깅이 어려울 수 있습니다.

### 비제어 컴포넌트 예시

```javascript
import React, { useRef } from "react";

function UncontrolledComponent() {
  const inputRef = useRef(null);

  const handleSubmit = (event) => {
    event.preventDefault();
    alert(`입력한 값: ${inputRef.current.value}`);
  };

  return (
    <form onSubmit={handleSubmit}>
      <input type="text" ref={inputRef} />
      <button type="submit">제출</button>
    </form>
  );
}

export default UncontrolledComponent;
```

- 위의 예시에서 `input` 요소는 `ref` 속성을 사용하여 DOM 요소에 접근합니다. 폼이 제출될 때 `inputRef.current.value`를 통해 입력 값을 읽습니다.

## 제어 컴포넌트와 비제어 컴포넌트의 비교

| 특성          | 제어 컴포넌트                        | 비제어 컴포넌트                  |
| ------------- | ------------------------------------ | -------------------------------- |
| 상태 관리     | 컴포넌트의 상태로 관리               | DOM에서 직접 관리                |
| 데이터 바인딩 | 양방향 데이터 바인딩                 | 단방향 데이터 흐름               |
| 구현 복잡성   | 상태 관리가 필요하여 상대적으로 복잡 | 간단한 구현 가능                 |
| 데이터 흐름   | 명확하고 예측 가능                   | 흐름이 불명확하고 복잡할 수 있음 |
| 유용한 상황   | 복잡한 폼, 유효성 검사 필요          | 간단한 폼, 빠른 구현 필요        |

## 결론

▶ 제어 컴포넌트와 비제어 컴포넌트는 각각의 장단점이 있으며, 상황에 따라 적절히 선택하여 사용할 수 있습니다.<br>
제어 컴포넌트는 복잡한 폼과 상태 관리가 필요한 경우에 적합하며, 비제어 컴포넌트는 간단한 폼과 빠른 구현이 필요한 경우에 유용합니다. 두 가지 방식의 차이를 이해하고 적절히 활용하면, 리액트에서 효율적인 폼 처리를 할 수 있습니다.

<br>

이렇게 오늘은 리액트의 제어 컴포넌트와 비제어 컴포넌트에 대해 알아봤는데요,<br>
면접에서도 충분히 나올 수 있는 질문이기 때문에 미리 공부해두면 좋을 것 같네요!
그렇다면 저는 다음에 또 다른 유익한 내용을 들고 오도록 하겠습니다 😁!
