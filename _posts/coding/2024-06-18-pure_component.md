---
layout: post
title: Pure Component
date: 2024-06-18 18:22 +0900
description: Pure Component에 대해 알아보기
image: ../assets/img/purecomponent.jpg
category: ETC
tags: Pure Component
published: true
sitemap: true
---

### Pure Component란?

▶ 리액트에서 Pure Component는 React.PureComponent 클래스를 상속받아 정의된 컴포넌트를 의미합니다.<br>
이 때, PureComponent는 shouldComponentUpdate 라이프사이클 메서드를 구현하여, 컴포넌트의 상태나 props가 변경될 때 불필요한 렌더링을 방지합니다.

- **shouldComponentUpdate 메서드**
▶ React.PureComponent는 shouldComponentUpdate 메서드를 자동으로 구현하여, 새로운 props와 상태를 얕은 비교(shallow comparison)하는데<br>
이 때, 얕은 비교는 객체의 참조만을 비교하는 것으로, 객체의 속성 값까지 깊게 비교하지 않습니다.

### 1. Pure Component 사용법

▶ Pure Component를 사용하려면 클래스 컴포넌트가 React.PureComponent를 상속받도록 정의하면 됩니다.<br>
아래는 일반 클래스 컴포넌트와 Pure Component의 차이점에 대한 예시입니다.

- 일반 클래스 컴포넌트

````javascript
import React, { Component } from 'react';

class MyComponent extends Component {
  render() {
    console.log('MyComponent rendered');
    return <div>{this.props.value}</div>;
  }
}

export default MyComponent;
````

- Pure Component 사용

````javascript
import React, { PureComponent } from 'react';

class MyComponent extends PureComponent {
  render() {
    console.log('MyComponent rendered');
    return <div>{this.props.value}</div>;
  }
}

export default MyComponent;
````

- 위의 예시에서 MyComponent는 Pure Component로 변경되었으며, 이는 동일한 props와 상태로 인해 불필요하게 렌더링되지 않습니다.


### 2. Pure Component의 장점

1. 성능 최적화
: Pure Component는 상태나 props가 변경되지 않는 한, 다시 렌더링되지 않으므로 성능이 최적화됩니다. 주로 많은 수의 컴포넌트가 자주 업데이트되는 애플리케이션에서 유용합니다.

2. 간결한 코드
: shouldComponentUpdate 메서드를 수동으로 구현할 필요 없이 Pure Component를 사용하면 자동으로 얕은 비교가 적용됩니다.

### 3. Pure Component의 한계

1. 얕은 비교의 한계
: Pure Component는 얕은 비교를 사용하기 때문에, props나 상태가 객체나 배열인 경우, 그 내부의 값이 변경되더라도 참조가 같다면 변경을 감지하지 못합니다.<br>
때문에 이러한 경우, 깊은 비교를 수동으로 구현하거나 불변성을 유지하여 새로운 객체나 배열을 생성해야 합니다.

2. 모든 경우에 적합하지 않음
: 모든 컴포넌트를 Pure Component로 만들면 오히려 성능이 저하될 수 있다. 특히, props나 상태가 자주 변경되는 경우, 매번 얕은 비교를 수행하는 비용이 높아질 수 있다.

### 4. 사용예시

````javascript
import React, { PureComponent } from 'react';

class ListItem extends PureComponent {
  render() {
    const { item } = this.props;
    return <li>{item.name}</li>;
  }
}

class ItemList extends PureComponent {
  render() {
    const { items } = this.props;
    return (
      <ul>
        {items.map(item => (
          <ListItem key={item.id} item={item} />
        ))}
      </ul>
    );
  }
}

export default ItemList;
````

- 위의 예시에서는 ListItem과 ItemList 컴포넌트는 Pure Component로 정의되었으며, 이는 불필요한 렌더링을 방지하여 성능을 최적화했습니다.

### 5. 결론

▶ 리액트의 Pure Component는 성능 최적화에 매우 유용한 도구로 shouldComponentUpdate 메서드를 자동으로 구현하여 얕은 비교를 통해 불필요한 렌더링을 방지합니다.<br>
그러나 얕은 비교의 한계를 이해하고, 모든 상황에서 Pure Component를 사용하는 것이 항상 최선은 아니라는 점을 명심해야 해야하며,<br>
올바르게 사용하면 Pure Component는 리액트 애플리케이션의 성능을 크게 향상시킬 수 있습니다.

<br>

이렇게 오늘은 Pure Component에 대해 알아봤는데요,<br>
면접에서도 충분히 나올 수 있는 질문이기 때문에 미리 공부해두면 좋을 것 같네요!<br>
그렇다면 저는 다음에 또다른 면접에 대비한 내용을 들고오도록 하겠습니다 😁!