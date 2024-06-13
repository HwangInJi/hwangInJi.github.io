---
layout: post
title: REACT Side Effect
date: 2024-06-09 17:49 +0900
description: REACT Side Effect에 대해 알아보기
image: ../assets/img/sideeffect.jpg
category: 리액트
tags: REACT SideEffect
published: true
sitemap: true
---

## 사이드 이펙트(Side Effect)란?

▶ 사이드 이펙트는 컴포넌트가 렌더링되는 동안 순수하지 않은 작업을 수행하는 것을 의미합니다.<br>
이러한 작업은 컴포넌트의 외부 세계와 상호 작용하거나 렌더링 결과에 영향을 주지 않는 작업을 포함하는데 대표적인 사이드 이펙트로는 데이터 가져오기, DOM 조작, 구독 설정 및 해제 등이 있습니다. 아래에서 좀 더 자세히 살펴보도록 하겠습니다.

### 사이드 이펙트의 개념

▶ 리액트 컴포넌트는 기본적으로 입력(프롭스)과 출력(렌더링 결과) 간의 순수한 함수처럼 동작해야 합니다.<br>
순수 함수는 동일한 입력에 대해 항상 동일한 출력을 반환하며, 함수 외부의 상태를 변경하지 않지만 실제 애플리케이션에서는 이러한 순수성만으로는 충분하지 않습니다.<br>
때문에 네트워크 요청을 통해 데이터를 가져와야 하거나, 브라우저의 로컬 스토리지에 데이터를 저장해야 할 때가 있고 보통 이러한 작업들을 바로 사이드 이펙트라 합니다.

### 리액트에서 사이드 이펙트 관리

▶ 리액트에서 사이드 이펙트를 관리하는 주요 방법은 **useEffect 훅을 사용하는 것**입니다.<br>
useEffect는 함수 컴포넌트 내에서 사이드 이펙트를 수행할 수 있게 해주는데, 클래스 컴포넌트에서는 componentDidMount, componentDidUpdate, componentWillUnmount와 같은 생명주기 메서드를 사용합니다.

#### 01. useEffect 훅

- useEffect 훅은 컴포넌트가 렌더링된 이후에 특정 작업을 수행하도록 하며, 기본 사용법은 다음과 같습니다.

````javascript
import React, { useEffect } from 'react';

function ExampleComponent() {
  useEffect(() => {
    // 여기에 사이드 이펙트 코드를 작성합니다.
    console.log('Component has been rendered or updated.');

    // 클린업 함수를 반환하여, 컴포넌트가 언마운트되거나 업데이트되기 전에 실행할 코드를 작성할 수 있습니다.
    return () => {
      console.log('Cleanup before component unmount or update.');
    };
  }, []); // 두 번째 인자로 빈 배열을 전달하여, 마운트와 언마운트 시에만 실행되도록 합니다.

  return <div>Example Component</div>;
}
````

- 위의 예시에서 useEffect는 컴포넌트가 처음 렌더링된 후와 이후 업데이트된 후에 호출됩니다.
- 두 번째 인자인 배열은 효과의 종속성을 지정하며, 배열에 포함된 값들이 변경될 때만 효과가 다시 실행됩니다.
- 빈 배열을 전달하면 컴포넌트가 마운트될 때만 효과가 실행되고, 언마운트될 때 클린업 함수가 실행됩니다.

#### 02. 종속성 배열

- useEffect의 두 번째 인자인 종속성 배열은 사이드 이펙트가 다시 실행될 조건을 정의하며, 특정 상태나 프롭스가 변경될 때만 다시 실행되도록 할 수 있습니다.

````javascript
import React, { useState, useEffect } from 'react';

function ExampleComponent() {
  const [count, setCount] = useState(0);

  useEffect(() => {
    console.log(`Count has been updated to: ${count}`);
  }, [count]); // count가 변경될 때마다 이 효과가 실행됩니다.

  return (
    <div>
      <p>Count: {count}</p>
      <button onClick={() => setCount(count + 1)}>Increment</button>
    </div>
  );
}
````

- 위의 예시에서는 count가 변경될 때마다 useEffect가 다시 실행됩니다.

### 일반적인 사이드 이펙트 사용 예시

#### 01. 데이터 가져오기

- 가장 일반적인 사이드 이펙트 중 하나는 API 호출을 통해 데이터를 가져오는 것입니다.

````javascript
import React, { useState, useEffect } from 'react';

function DataFetchingComponent() {
  const [data, setData] = useState(null);

  useEffect(() => {
    async function fetchData() {
      const response = await fetch('https://api.example.com/data');
      const result = await response.json();
      setData(result);
    }

    fetchData();
  }, []); // 빈 배열을 전달하여 컴포넌트가 마운트될 때만 데이터를 가져옵니다.

  return (
    <div>
      {data ? <pre>{JSON.stringify(data, null, 2)}</pre> : 'Loading...'}
    </div>
  );
}
````

#### 02. 이벤트 리스너 등록 및 해제

- 컴포넌트가 마운트될 때 이벤트 리스너를 등록하고 언마운트될 때 이를 해제하는 경우입니다.

````javascript
import React, { useEffect } from 'react';

function EventListenerComponent() {
  useEffect(() => {
    function handleResize() {
      console.log('Window resized');
    }

    window.addEventListener('resize', handleResize);

    // 클린업 함수에서 이벤트 리스너를 해제합니다.
    return () => {
      window.removeEventListener('resize', handleResize);
    };
  }, []); // 빈 배열을 전달하여, 컴포넌트가 마운트되고 언마운트될 때만 효과를 실행합니다.

  return <div>Resize the window and check the console.</div>;
}
````

#### 03. 생명주기 메서드 사용

- 클래스 컴포넌트에서는 생명주기 메서드인 componentDidMount와 componentWillUnmount를 사용하여 마운트 및 언마운트 시에 작업을 수행할 수 있습니다.

````javascript
import React, { Component } from 'react';

class ClassComponent extends Component {
  componentDidMount() {
    console.log('Component mounted');
  }

  componentWillUnmount() {
    console.log('Component will unmount');
  }

  render() {
    return <div>Class Component</div>;
  }
}
````

### 결론

▶ 리액트에서 사이드 이펙트는 컴포넌트의 순수성을 유지하면서도 외부와 상호작용하기 위해 필수적인 개념입니다.<br>
useEffect 훅을 사용하여 사이드 이펙트를 관리함으로써 데이터 가져오기, 이벤트 리스너 등록 및 해제 등의 작업을 효율적으로 수행할 수 있으며,<br>
리액트의 훅 기반 접근 방식은 코드의 가독성을 높이고 생명주기 메서드의 복잡성을 줄여주어 더욱 간결하고 유지보수하기 쉬운 코드를 작성할 수 있게 합니다.

<br>

이렇게 오늘은 리액트의 사이드 이펙트에 대해 알아봤는데요,<br>
면접에서도 충분히 나올 수 있는 질문이기 때문에 미리 공부해두면 좋을 것 같네요!
그렇다면 저는 다음에 또다른 면접에 대비한 내용을 들고오도록 하겠습니다 😁!