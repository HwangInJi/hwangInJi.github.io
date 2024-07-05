---
layout: post
title: Context API에 대해 알아보기
date: 2024-07-04 20:36 +0900
description: Context API에 대해 알아보기
image: ../assets/img/contextapi.jpg
category: 리액트
tags: REACT ContextAPI
published: true
sitemap: true
---

# 리액트에서 말하는 Context API

리액트(React)는 컴포넌트 기반의 사용자 인터페이스 라이브러리로, 상태(state) 관리를 위해 다양한 방법을 제공합니다. 그 중 하나가 **Context API**입니다. Context API는 컴포넌트 트리 전반에 걸쳐 데이터를 손쉽게 공유할 수 있게 해줍니다. 이 글에서는 Context API의 개념, 사용법, 그리고 장단점에 대해 알아보겠습니다.

## Context API란?

Context API는 리액트 v16.3에서 도입된 기능으로, 컴포넌트 트리의 여러 단계에 걸쳐 데이터를 전파하는 방법을 제공합니다. 전통적인 props 전파 방식은 데이터가 필요하지 않은 여러 중간 컴포넌트를 거쳐야 하기 때문에 불편할 수 있습니다. Context API는 이러한 문제를 해결하여, 데이터를 필요한 컴포넌트에 직접 전달할 수 있습니다.

## Context API의 주요 구성 요소

Context API는 `React.createContext()` 함수를 사용하여 생성됩니다. 주요 구성 요소는 다음과 같습니다.

1. **React.createContext()**
2. **Provider**
3. **Consumer**
4. **useContext Hook**

### React.createContext()

`React.createContext()` 함수는 기본값을 인수로 받아서 Context 객체를 생성합니다. 이 객체에는 Provider와 Consumer라는 두 개의 중요한 컴포넌트가 포함됩니다.

```javascript
const MyContext = React.createContext(defaultValue);
```

### Provider

Provider는 Context를 구독하는 컴포넌트들에게 컨텍스트의 변화를 알리기 위해 사용됩니다. Provider는 `value`라는 prop을 받아서 하위 컴포넌트들에게 제공할 데이터를 정의합니다.

```javascript
<MyContext.Provider value={/* some value */}>
  {children}
</MyContext.Provider>
```

### Consumer

Consumer는 Context의 변화를 구독하는 컴포넌트입니다. Consumer는 함수 컴포넌트를 child로 가지며, 이 함수는 현재 컨텍스트 값을 인수로 받습니다.

```javascript
<MyContext.Consumer>
  {value => /* render something based on the context value */}
</MyContext.Consumer>
```

### useContext Hook

`useContext` Hook은 함수 컴포넌트에서 Context를 쉽게 사용할 수 있도록 도와줍니다. `useContext`는 Context 객체를 인수로 받아 현재 컨텍스트 값을 반환합니다.

```javascript
const value = useContext(MyContext);
```

## Context API 사용 예시

Context API의 사용법을 간단한 예제를 통해 알아보겠습니다. 아래는 테마 설정을 위한 Context API 사용 예시입니다.

```javascript
import React, { createContext, useState, useContext } from "react";

// Context 생성
const ThemeContext = createContext();

// Provider 컴포넌트
const ThemeProvider = ({ children }) => {
  const [theme, setTheme] = useState("light");

  const toggleTheme = () => {
    setTheme((prevTheme) => (prevTheme === "light" ? "dark" : "light"));
  };

  return (
    <ThemeContext.Provider value={{ theme, toggleTheme }}>
      {children}
    </ThemeContext.Provider>
  );
};

// Consumer 또는 useContext를 사용하여 Context 값 접근
const ThemedComponent = () => {
  const { theme, toggleTheme } = useContext(ThemeContext);

  return (
    <div
      style={{
        background: theme === "light" ? "#fff" : "#333",
        color: theme === "light" ? "#000" : "#fff",
      }}
    >
      <p>The current theme is {theme}</p>
      <button onClick={toggleTheme}>Toggle Theme</button>
    </div>
  );
};

// App 컴포넌트
const App = () => (
  <ThemeProvider>
    <ThemedComponent />
  </ThemeProvider>
);

export default App;
```

위 예제에서 `ThemeProvider`는 테마 값을 제공하고, `ThemedComponent`는 이 값을 사용하여 UI를 업데이트합니다. `toggleTheme` 함수를 통해 테마를 전환할 수 있습니다.

## Context API의 장단점

### 장점

1. **Prop Drilling 방지**: 중간 컴포넌트를 거치지 않고 데이터 전달이 가능하여, 코드가 간결해집니다.
2. **전역 상태 관리**: 전역 상태를 손쉽게 관리할 수 있습니다.
3. **유연성**: 다양한 종류의 데이터를 Context를 통해 전달할 수 있습니다.

### 단점

1. **복잡성 증가**: 잘못 사용하면 코드의 복잡성이 증가할 수 있습니다.
2. **성능 문제**: Context 값이 자주 변경되면, 많은 하위 컴포넌트들이 불필요하게 다시 렌더링될 수 있습니다.
3. **디버깅 어려움**: Context를 통한 데이터 흐름을 추적하기가 어려울 수 있습니다.

## 결론

Context API는 리액트 애플리케이션에서 전역적으로 데이터를 관리하고 전달하는 강력한 도구입니다. 적절히 사용하면 코드의 가독성과 유지보수성을 높일 수 있지만, 남용하면 오히려 복잡성을 증가시킬 수 있습니다. 따라서 Context API를 사용할 때는 필요한 경우에만 사용하는 것이 좋습니다.
