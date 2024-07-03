---
layout: post
title: 리액트 생명주기 메서드
date: 2024-07-01 18:00 +0900
description: 리액트 컴포넌트의 생명주기 메서드에 대해 알아보기
image: ../assets/img/lifecyclemethods.jpg
category: JavaScript
tags: JavaScript React Lifecycle
published: true
sitemap: true
---

## 리액트 생명주기 메서드

▶ 리액트 컴포넌트는 생성, 업데이트, 제거의 세 가지 주요 단계로 이루어지는 생명주기를 가지고 있습니다. 각 단계에서 특정 메서드가 호출되며, 이를 통해 컴포넌트의 상태나 UI를 조작할 수 있습니다. 이번 포스트에서는 리액트 컴포넌트의 생명주기 메서드에 대해 자세히 알아보겠습니다.

### 생명주기 단계

1. **마운트(Mount)**: 컴포넌트가 처음 DOM에 삽입될 때 호출되는 메서드들.
2. **업데이트(Update)**: 컴포넌트가 리렌더링되는 과정에서 호출되는 메서드들.
3. **언마운트(Unmount)**: 컴포넌트가 DOM에서 제거될 때 호출되는 메서드들.

### 마운트 단계

마운트 단계에서 호출되는 주요 메서드는 다음과 같습니다.

#### `constructor()`

`constructor`는 컴포넌트가 생성될 때 가장 먼저 호출되는 메서드로, 초기 상태를 설정하거나 메서드를 바인딩하는데 사용됩니다.

```javascript
class MyComponent extends React.Component {
  constructor(props) {
    super(props);
    this.state = { count: 0 };
  }
}
```

#### `static getDerivedStateFromProps()`

`getDerivedStateFromProps`는 컴포넌트가 마운트되기 전에 호출되며, props로부터 파생된 state를 설정할 수 있습니다.

```javascript
static getDerivedStateFromProps(nextProps, prevState) {
  if (nextProps.count !== prevState.count) {
    return { count: nextProps.count };
  }
  return null;
}
```

#### `componentDidMount()`

`componentDidMount`는 컴포넌트가 처음 렌더링된 후 호출되며, 여기서 네트워크 요청이나 DOM 조작을 수행할 수 있습니다.

```javascript
componentDidMount() {
  fetch('/api/data')
    .then(response => response.json())
    .then(data => this.setState({ data }));
}
```

### 업데이트 단계

업데이트 단계에서 호출되는 주요 메서드는 다음과 같습니다.

#### `shouldComponentUpdate()`

`shouldComponentUpdate`는 리렌더링 여부를 결정하며, 성능 최적화를 위해 사용할 수 있습니다. 기본적으로 `true`를 반환하지만, 조건에 따라 `false`를 반환하여 리렌더링을 방지할 수 있습니다.

```javascript
shouldComponentUpdate(nextProps, nextState) {
  return nextState.count !== this.state.count;
}
```

#### `getSnapshotBeforeUpdate()`

`getSnapshotBeforeUpdate`는 실제 DOM 업데이트가 발생하기 전에 호출되며, 업데이트 전의 상태를 기록할 수 있습니다.

```javascript
getSnapshotBeforeUpdate(prevProps, prevState) {
  if (prevProps.scrollPosition !== this.props.scrollPosition) {
    return this.props.scrollPosition;
  }
  return null;
}
```

#### `componentDidUpdate()`

`componentDidUpdate`는 컴포넌트가 업데이트된 후 호출되며, 여기서 네트워크 요청이나 DOM 조작을 수행할 수 있습니다.

```javascript
componentDidUpdate(prevProps, prevState, snapshot) {
  if (snapshot !== null) {
    // DOM 업데이트 작업 수행
  }
}
```

### 언마운트 단계

언마운트 단계에서 호출되는 주요 메서드는 다음과 같습니다.

#### `componentWillUnmount()`

`componentWillUnmount`는 컴포넌트가 DOM에서 제거되기 전에 호출되며, 여기서 타이머나 네트워크 요청을 정리할 수 있습니다.

```javascript
componentWillUnmount() {
  clearTimeout(this.timer);
}
```

### 그 외 생명주기 메서드

#### `componentDidCatch()`

`componentDidCatch`는 컴포넌트 내에서 발생한 에러를 캐치하며, 이를 통해 오류 경계(Error Boundary)를 구현할 수 있습니다.

```javascript
componentDidCatch(error, info) {
  console.error("Error caught in component: ", error, info);
}
```

### 요약

리액트의 생명주기 메서드는 컴포넌트의 생성, 업데이트, 제거 과정에서 호출되는 메서드들로, 컴포넌트의 상태나 UI를 조작할 수 있는 강력한 도구를 제공합니다. 생명주기 메서드를 잘 이해하고 활용하면 더 효율적이고 반응성 좋은 리액트 애플리케이션을 개발할 수 있습니다.

<br>

이렇게 오늘은 리액트 컴포넌트의 생명주기 메서드에 대해 알아보았는데요,<br>
생명주기 메서드를 잘 활용하면 더 나은 사용자 경험을 제공할 수 있겠죠?<br>
그럼 전 다음에 또 다른 유익한 내용을 가지고 돌아오겠습니다 😁!
