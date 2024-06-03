---
layout: post
title: Pure Component
date: 2024-06-02 18:39 +0900
description: Pure Component에 대해 알아보기
image: ../assets/img/purecomp.jpg
category: 리액트
tags: PureComponent REACT
published: true
sitemap: true
---

### 1. Pure Component란

▶ Pure Component는 React에서 컴포넌트의 성능을 최적화하기 위해 사용되는 중요한 개념 중 하나입니다.<br>
Pure Component는 컴포넌트의 상태 또는 props가 변경되지 않으면 불필요한 렌더링을 방지하여 성능을 최적화하며, 이를 통해 애플리케이션의 효율성을 크게 향상시킬 수 있습니다.

### 2. Pure Component의 작동 원리

▶ Pure Component는 shouldComponentUpdate 메서드를 자동으로 구현합니다.<br>
이 메서드는 다음 상태와 props를 현재 상태와 props와 얕게 비교(shallow compare)하여 다를 경우에만 컴포넌트를 렌더링하는데, 여기서 **얕은 비교는 객체의 참조값을 비교하는 것을 의미**합니다. 즉, 객체나 배열의 경우 내부 값이 같더라도 참조값이 다르면 다른 것으로 간주한다는 뜻입니다. 아래의 예시를 통해 비교해볼게요!

#### (1) 일반 컴포넌트

- 일반적인 React 컴포넌트는 상태나 props가 변경될 때마다 렌더링됩니다.

````jsx
import React, { Component } from 'react';

class RegularComponent extends Component {
  render() {
    console.log('Regular Component Rendered');
    return <div>{this.props.value}</div>;
  }
}

export default RegularComponent;
````

#### (2) Pure Component

- Pure Component는 React.PureComponent를 상속받아 구현되며, 아래 예시에서 PureComponentExample은 상태나 props가 변하지 않으면 재렌더링되지 않습니다.

````jsx
import React, { PureComponent } from 'react';

class PureComponentExample extends PureComponent {
  render() {
    console.log('Pure Component Rendered');
    return <div>{this.props.value}</div>;
  }
}

export default PureComponentExample;
````

### 3. Pure Component의 장점

1. 성능 최적화
: Pure Component는 불필요한 렌더링을 방지하여 성능을 향상시킵니다. 특히 많은 하위 컴포넌트를 가진 대규모 애플리케이션에서 성능 이점을 얻을 수 있습니다.

2. 코드 간결성
: shouldComponentUpdate 메서드를 직접 구현할 필요 없이 자동으로 얕은 비교를 수행하여 코드가 간결해집니다.

### 4. Pure Component의 단점

1. 얕은 비교의 한계
: 얕은 비교는 객체나 배열의 내부 값을 비교하지 않기 때문에 복잡한 데이터 구조를 다루는 경우 적절하지 않을 수 있습니다. 즉, Pure Component의 특징으로 인해 배열의 내용이 변했더라도 참조값이 동일하면 변경으로 간주되지 않습니다.

2. 함수형 프로그래밍 필요
: 데이터 불변성(immutability)을 유지해야 하기 때문에 상태나 props를 직접 변경하지 않고 새로운 객체를 반환하는 방식으로 업데이트해야 합니다. 이는 React의 성능 최적화 전략과 일치하지만 개발자가 이를 항상 인지하고 코딩해야 하는 불편함이 있습니다.

3. 사용의 복잡성
: 모든 상황에서 Pure Component를 사용하는 것이 적절하지 않을 수 있습니다. 간단한 컴포넌트나 상태 변화가 빈번하지 않은 경우에는 일반 컴포넌트를 사용하는 것이 더 간단하고 효율적일 수 있습니다.

#### 사용 사례

1. 리스트 렌더링
: 대규모 리스트를 렌더링할 때 각 항목을 Pure Component로 만들어 불필요한 재렌더링을 방지할 수 있습니다.

2. Form 입력 처리
: 입력 필드와 같은 빈번히 업데이트되는 UI 요소를 Pure Component로 만들어 성능을 최적화할 수 있습니다.

<br>

이렇게 오늘은 Pure Component에 대해 알아봤는데요,<br>
면접에서도 충분히 나올 수 있는 질문이기 때문에 미리 공부해두면 좋을 것 같네요!
그렇다면 저는 다음에 또다른 면접에 대비한 내용을 들고오도록 하겠습니다 😁!