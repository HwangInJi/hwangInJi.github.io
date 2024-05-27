---
layout: post
title: REACT useEffect
date: 2024-05-26 17:29 +0900
description: REACT useEffect에 대해서 알아보기
image: ../assets/img/useEffect.jpg
category: 리액트
tags: 리액트 REACT useEffect
published: true
sitemap: true
---

### useEffect란?

▶ useEffect는 리액트 훅 중 하나로, 함수형 컴포넌트에서 부수 효과(side effects)를 수행할 수 있게 해줍니다.
여기서 말하는 부수 효과는 데이터 가져오기(fetching data), 구독(subscription), DOM 직접 조작, 타이머 설정 등을 말합니다.

#### useEffect의 기본 사용법

▶ 간단한 예시를 통해 기본 사용법에 대해 알아보도록 하겠습니다.

````javascript
import React, { useState, useEffect } from 'react';

function Example() {
  const [count, setCount] = useState(0);

  useEffect(() => {
    // 컴포넌트가 마운트될 때와 count 상태가 변경될 때 실행됩니다.
    document.title = `You clicked ${count} times`;

    // 선택적인 정리(cleanup) 함수를 반환할 수 있습니다.
    return () => {
      // 컴포넌트가 언마운트되거나, 다음 이펙트가 실행되기 전에 호출됩니다.
    };
  }, [count]); // 의존성 배열에 count를 포함합니다.

  return (
    <div>
      <p>You clicked {count} times</p>
      <button onClick={() => setCount(count + 1)}>
        Click me
      </button>
    </div>
  );
}
````

- 위의 예시에서는 useState 훅을 임포트하여 함수형 컴포넌트에서 상태를 관리할 수 있도록 먼저 지정해주었는데, count에는 현재 클릭 횟수를, setCount에는 클릭 횟수 상태를 갱신하도록 한 후 count의 초기 값을 0으로 설정하였습니다.
- 그 다음 useEffect 훅을 사용하여 부수 효과를 정의하였는데 설정은 아래와 같습니다.
1. 함수 내부에서 document.title을 업데이트하여 현재 클릭 횟수를 제목에 반영합니다.
2. 배열에 있는 count를 두 번째 인자로 전달하여, count 값이 변경될 때마다 이펙트가 다시 실행됩니다.<br>
만약 배열이 비어 있으면([]), 이펙트는 컴포넌트가 마운트될 때 한 번만 실행됩니다.

#### 데이터 가져올 경우의 사용법

▶ 기본적인 사용 외에도 데이터를 가져올 때 주로 사용하는 경우가 많은데, 아래의 예시를 통해 알아보도록 하겠습니다.

````javascript
import React, { useState, useEffect } from 'react';

function DataFetchingComponent() {
  const [data, setData] = useState(null);

  useEffect(() => {
    fetch('https://api.example.com/data')
      .then(response => response.json())
      .then(data => setData(data))
      .catch(error => console.error('Error fetching data:', error));

    return () => {
      // Cleanup, if necessary
    };
  }, []); // 빈 의존성 배열: 마운트 시에만 실행

  return (
    <div>
      {data ? <p>Data: {JSON.stringify(data)}</p> : <p>Loading...</p>}
    </div>
  );
}
````

- 위의 예시는 fetch를 사용하여 json파일의 데이터를 가져오고, setData를 통해 상태를 업데이트하고 있습니다.
- 여기에선 배열이 비어 있으므로 컴포넌트가 마운트될 때 한 번만 실행됩니다.
- 정리하자면 아래와 같습니다.<br>
1. useEffect는 함수형 컴포넌트에서 부수 효과를 수행하기 위해 사용됩니다.
2. useEffect는 두 인자를 받습니다 -> 실행할 함수와 의존성 배열.
3. 배열을 통해 이펙트가 언제 실행되고 정리되는지 제어할 수 있습니다.
4. 여기서 return은 정리 함수로, 컴포넌트가 언마운트되거나 다음 이펙트가 실행되기 전에 호출됩니다.

<br>

이렇게 오늘은 useEffect에 대해 알아봤는데요,<br>
면접에서도 충분히 나올 수 있는 질문인만큼 미리 공부해두면 좋을 것 같네요!
그렇다면 저는 다음에 또다른 면접에 대비한 내용을 들고오도록 하겠습니다 😁!