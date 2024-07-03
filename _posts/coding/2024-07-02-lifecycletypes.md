---
layout: post
title: 리액트 생명주기 메서드 종류
date: 2024-07-02 20:48 +0900
description: 리액트 컴포넌트의 생명주기 메서드 종류에 대해 알아보기
image: ../assets/img/lifecycletypes.jpg
category: JavaScript
tags: JavaScript React Lifecycle
published: true
sitemap: true
---

## 리액트 생명주기 메서드 종류

▶ 리액트 컴포넌트는 특정 시점마다 자동으로 호출되는 생명주기 메서드를 가지고 있습니다. 이 메서드들은 컴포넌트의 생성, 업데이트, 제거 과정에서 호출되며, 개발자가 특정 작업을 수행할 수 있게 도와줍니다. 이번 포스트에서는 리액트 컴포넌트의 생명주기 메서드 종류와 그 사용법에 대해 자세히 알아보겠습니다.

### 생명주기 메서드 종류

리액트 생명주기 메서드는 크게 세 단계로 나뉩니다: 마운트(Mount), 업데이트(Update), 언마운트(Unmount). 각 단계마다 호출되는 메서드가 다르며, 각 메서드의 역할과 사용법을 이해하는 것이 중요합니다.

### 마운트(Mount) 단계

마운트 단계는 컴포넌트가 DOM에 삽입되는 시점에 호출됩니다. 이 단계에서 호출되는 주요 메서드는 다음과 같습니다.

#### 1. `constructor()`

`constructor`는 컴포넌트가 생성될 때 호출되며, 초기 상태를 설정하거나 메서드를 바인딩하는데 사용됩니다.

```javascript
class MyComponent extends React.Component {
  constructor(props) {
    super(props);
    this.state = { count: 0 };
  }
}
```

#### 2. `static getDerivedStateFromProps()`

`getDerivedStateFromProps`는 컴포넌트가 마운트되기 전에 호출되며, props로부터 파생된 state를 설정할 수 있습니다.

```javascript
static getDerivedStateFromProps(nextProps, prevState) {
  if (nextProps.count !== prevState.count) {
    return { count: nextProps.count };
  }
  return null;
}
```

#### 3. `render()`

`render` 메서드는 컴포넌트의 UI를 정의하는 메서드로, 필수적으로 구현해야 합니다. JSX를 반환하며, 실제 DOM에 렌더링됩니다.

```javascript
render() {
  return <div>{this.state.count}</div>;
}
```

#### 4. `componentDidMount()`

`componentDidMount`는 컴포넌트가 처음 렌더링된 후 호출되며, 여기서 네트워크 요청이나 DOM 조작을 수행할 수 있습니다.

```javascript
componentDidMount() {
  fetch('/api/data')
    .then(response => response.json())
    .then(data => this.setState({ data }));
}
```

### 업데이트(Update) 단계

업데이트 단계는 컴포넌트가 리렌더링될 때 호출됩니다. 이 단계에서 호출되는 주요 메서드는 다음과 같습니다.

#### 1. `static getDerivedStateFromProps()`

업데이트 단계에서도 호출되며, 새로운 props에 따라 state를 업데이트할 수 있습니다.

#### 2. `shouldComponentUpdate()`

`shouldComponentUpdate`는 리렌더링 여부를 결정하며, 성능 최적화를 위해 사용할 수 있습니다.

```javascript
shouldComponentUpdate(nextProps, nextState) {
  return nextState.count !== this.state.count;
}
```

#### 3. `render()`

마운트 단계와 마찬가지로, 업데이트 단계에서도 UI를 다시 렌더링합니다.

#### 4. `getSnapshotBeforeUpdate()`

`getSnapshotBeforeUpdate`는 실제 DOM 업데이트가 발생하기 전에 호출되며, 업데이트 전의 상태를 기록할 수 있습니다.

```javascript
getSnapshotBeforeUpdate(prevProps, prevState) {
  if (prevProps.scrollPosition !== this.props.scrollPosition) {
    return this.props.scrollPosition;
  }
  return null;
}
```

#### 5. `componentDidUpdate()`

`componentDidUpdate`는 컴포넌트가 업데이트된 후 호출되며, 네트워크 요청이나 DOM 조작을 수행할 수 있습니다.

```javascript
componentDidUpdate(prevProps, prevState, snapshot) {
  if (snapshot !== null) {
    // DOM 업데이트 작업 수행
  }
}
```

### 언마운트(Unmount) 단계

언마운트 단계는 컴포넌트가 DOM에서 제거될 때 호출됩니다. 이 단계에서 호출되는 주요 메서드는 다음과 같습니다.

#### 1. `componentWillUnmount()`

`componentWillUnmount`는 컴포넌트가 DOM에서 제거되기 전에 호출되며, 타이머나 네트워크 요청을 정리할 수 있습니다.

```javascript
componentWillUnmount() {
  clearTimeout(this.timer);
}
```

### 에러 처리

리액트는 컴포넌트 내에서 발생한 에러를 처리할 수 있는 메서드도 제공합니다.

#### `componentDidCatch()`

`componentDidCatch`는 컴포넌트 내에서 발생한 에러를 캐치하며, 이를 통해 오류 경계(Error Boundary)를 구현할 수 있습니다.

```javascript
componentDidCatch(error, info) {
  console.error("Error caught in component: ", error, info);
}
```

### 요약

리액트 생명주기 메서드는 컴포넌트의 생성, 업데이트, 제거 과정에서 호출되는 메서드들로, 컴포넌트의 상태나 UI를 조작할 수 있는 강력한 도구를 제공합니다. 각 생명주기 메서드의 역할과 사용법을 잘 이해하면 더 효율적이고 반응성 좋은 리액트 애플리케이션을 개발할 수 있습니다.

<br>

이렇게 리액트 컴포넌트의 생명주기 메서드 종류와 사용법에 대해 알아보았는데요,<br>
각 메서드의 특성과 활용 방법을 잘 이해하고 적용하면 더 나은 사용자 경험을 제공할 수 있습니다.<br>
그럼 전 다음에 또 다른 면접 질문을 가지고 돌아오겠습니다 😁!
