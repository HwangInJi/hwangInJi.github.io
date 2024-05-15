---
layout: post
title: JAVASCRIPT 이벤트 버블링 & 이벤트 캡처
date: 2024-05-15 17:29 +0900
description: JAVASCRIPT 이벤트 버블링 & 이벤트 캡처에 대해서 알아보기
image: ../assets/img/eventbubble.jpg
category: 자바스크립트
tags: 자바스크립트 javascript 동기 비동기
published: true
sitemap: true
---

## 이벤트 캡처(Event Capturing)란?

1. 이벤트 캡처는 이벤트가 발생한 요소의 부모 요소부터 시작해서 해당 요소까지 이벤트가 전파되는 단계입니다.
즉, 이벤트가 가장 먼저 발생한 부모 요소부터 해당 요소까지 이벤트가 캡처되는 과정을 이벤트 캡처라고 부릅니다.
<br>

2. 이벤트 캡처는 일반적으로 이벤트 리스너를 등록할 때 세 번째 인자로 { capture: true }를 전달하여 설정할 수 있습니다.

## 이벤트 버블링(Event Bubbling)이란?

1. 이벤트 버블링은 이벤트가 발생한 요소에서 시작해서 상위 요소로 이벤트가 전파되는 단계입니다.
즉, 이벤트가 발생한 요소에서부터 부모 요소, 그 다음 상위 요소로 이벤트가 버블링되는 과정을 말합니다.
<br>

2. 이벤트 버블링은 기본적으로 자바스크립트 이벤트 모델에서 사용되는 방식이며, 대부분의 경우 이벤트가 버블링되는 것을 기본 동작으로 사용합니다.

## 간단한 예시를 통해 이해해보기

▶ 결론적으로 이벤트가 발생하면, 이벤트 캡처 단계에서는 최상위 요소(document)에서 시작하여 내려오는 방식으로 이벤트를 캡처하고, 이후 이벤트 버블링 단계에서는 이벤트가 발생한 요소에서 시작하여 상위 요소로 올라가는 방식으로 이벤트를 전파하는 과정으로 진행이 됩니다.<br>
간단한 예시로 아래와 같은 HTML구조가 있다고 가정해볼게요!

````javascript
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>이벤트 캡처와 이벤트 버블링</title>
</head>
<body>
  <div id="parent">
    <div id="child">
      <button id="btn">클릭하세요</button>
    </div>
  </div>

  <script>
    const parent = document.getElementById('parent');
    const child = document.getElementById('child');
    const button = document.getElementById('btn');

    parent.addEventListener('click', () => console.log('부모 요소'));
    child.addEventListener('click', () => console.log('자식 요소'));
    button.addEventListener('click', () => console.log('버튼'));
  </script>
</body>
</html>
````

- 위의 코드에서는 parent라는 부모 요소와 그 안에 있는 child 자식 요소, 그리고 btn이라는 버튼 요소가 있고 각 요소에는 클릭 이벤트에 대한 이벤트 리스너가 등록되어 있습니다.<br>
- **1단계 이벤트 캡처**<br>
▶ 클릭이 발생하면 이벤트는 이벤트 캡처 단계에서 시작됩니다. 따라서 document에서 시작하여 parent -> child -> btn 순서로 이벤트가 캡처가 진행됩니다. 이 과정에서는 parent 이벤트 캡처 단계에서 등록된 이벤트 리스너가 실행되고 이어서 child 이벤트 캡처 단계에서 등록된 이벤트 리스너가 실행되어 아래와 같은 결과가 출력됩니다.

````bash
// 출력값
부모 요소
자식 요소
버튼
````

<br>

- **이벤트 버블링(Event Bubbling) 단계**<br>
▶ 이벤트 캡처 단계가 끝나면 이벤트는 이벤트 버블링 단계로 넘어갑니다. 이제는 클릭된 요소인 btn에서부터 이벤트가 버블링됩니다. 즉, 이벤트 캡처와는 반대로 btn -> child -> parent 순서로 이벤트가 버블링됩니다. 이 과정에서는 child 이벤트 버블링 단계에서 등록된 이벤트 리스너가 실행되고 이어서 parent 이벤트 버블링 단계에서 등록된 이벤트 리스너가 실행되어 아래와 같은 결과가 출력됩니다.

````bash
// 출력값
버튼
자식 요소
부모 요소
````

<br>

이렇게 오늘은 자바스크립트의 이벤트 캡처와 버블링에 대해 알아봤는데요,<br>
이렇게 예시로 살펴보니 어떤 차이가 있는 확실히 이해가 되시겠죠??<br>
오늘 정리한 내용도 면접을 준비할 때 나올 수 있는 질문인만큼 미리미리 숙지해서 알아두면 좋을 것 같네요.<br>
그럼 다음엔 또 다른 면접 정보들을 가져와보도록 하겠습니다 😁!