---
layout: post
title: jQuery로 이미지 레이아웃 애니메이션 넣기
date: 2024-04-15 17:29 +0900
description: jQuery 이미지 애니메이션에 대해서 알아보기
image: ../assets/img/javaani.jpg
category: 제이쿼리
tags: jQuery 제이쿼리 애니메이션
published: true
sitemap: true
---

# 자바스크립트 이미지 레이아웃 애니메이션 효과

![Frame 37](https://github.com/HwangInJi/class2024/assets/163365140/ce292624-b2d9-41fc-a66e-9435c4ab2ed8)

빨간 표시된 슬라이드 레이아웃 영역에 이미지를 넣고 번갈아가며 보여지는 애니메이션 효과를 자바스크립트로도 간단하게 넣을 수 있다는 사실 알고 계신가요??<br>

지금부터 알려드리는 방법으로 한번 따라해보세요!

<br>

## 1. slider영역에 sliderWrap 영역 추가하기
▶ 가장 먼저 만들고자 하는 레이아웃 영역을 만들었다면 slider영역에 'sliderWrap'이라는 큰 틀의 class를 만들어줍니다.


````javascript
<main id="slider">
            <div class="sliderWrap"></div>
</main>
````

<br>

## 2. sliderWrap에 원하는 이미지 수 만큼 img 추가하기
▶ 큰 틀을 만들었다면 그 다음엔 'sliderWrap' 안에 추가하고자 하는 이미지 개수만큼 img 링크를 추가해줍니다. 저는 총 3장의 이미지를 넣어보았어요!<br>
이 때 span태그를 추가해 이름을 지정해준다면 좀 더 헷갈리지 않을 수 있겠죠?


````javascript
 <main id="slider">
        <div class="sliderWrap">
            <div class="slider s1">
                <img src="https://webstoryboy.github.io/webstoryboy/w_webd/slider/slider01.jpg" alt="이미지1">
                <span>이미지1</span>
            </div>
            <div class="slider s2">
                <img src="https://webstoryboy.github.io/webstoryboy/w_webd/slider/slider02.jpg" alt="이미지2">
                <span>이미지2</span>
            </div>
            <div class="slider s3">
                <img src="https://webstoryboy.github.io/webstoryboy/w_webd/slider/slider03.jpg" alt="이미지3">
                <span>이미지3</span>
            </div>
        </div>
 </main>
````

<br>

## 3. style css 추가 입력하기
▶ 기존 레이아웃에 새로운 'sliderWrap' 이라는 영역이 추가되었으니 style css에도 수정이 필요하겠죠?<br>
먼저 slider안에 img가 들어가되, 영역을 벗어나면 안되기 때문에 우선 부모라는 큰 틀인 sliderWrap에 'position: relative;'를 이용해 상대적인 위치를 지정해줍니다.

````css
.sliderWrap {
    position: relative;
}
````

<br>

▶ 그 다음 자식 요소인 .slider에 left: 0; top: 0; position: absolute;을 줌으로서 위치를 지정한 요소는 부모 요소를 기준으로 좌표를 설정해줍니다.<br>
left: 0;과 top: 0;을 주었기 때문에 해당 요소는 부모 요소의 좌상단(좌측 상단 모서리)에 배치됩니다.

````css
.sliderWrap {
    position: relative;
}

.sliderWrap .slider {
    position: absolute;
    left: 0;
    top: 0;
}
````

<br>

▶ 마지막으로 left: 50%; top: 50%;을 줌으로서 span태그를 .slider의 가로와 세로 중앙에 위치시킨 후 transform: translate(-50%, -50%);: translate 함수를 사용하여 span 요소를 가운데 정렬시켜줍니다. span태그 또한 sliderWrap의 자식 요소이기 때문에 position: absolute;를 추가해줍니다.<br>
❗ 이 부분은 생략해도 되지만 저는 예시를 보여주기 위해 추가해보았어요.

````css
.sliderWrap {
    position: relative;
}

.sliderWrap .slider {
    position: absolute;
    left: 0;
    top: 0;
}

.sliderWrap .slider span {
    position: absolute;
    left: 50%;
    top: 50%;
    transform: translate(-50%, -50%);
    background-color: rgba(0, 0, 0, 0.4);
    padding: 10px 20px;
    color: #fff;
}
````

여기까지 잘 따라오셨다면 이미지가 slider영역에 들어간 게 보이실거에요!

<br>

## 4. jQuery를 활용해 애니메이션 효과주기
▶ 이제 마지막 단계로 script에 jQuery 코드를 활용해 애니메이션 이벤트를 실행시켜주면 됩니다.<br>

먼저 큰 틀인 '$(function () {});' 영역은 jQuery의 문서 준비 이벤트(Document Ready Event)입니다. 즉, HTML 문서가 완전히 로드되고 준비된 후에 실행된다는 것을 의미합니다.

````javascript
 $(function () {});
````

<br>

▶ 그 다음 변수인 let을 이용해 0부터 시작하도록 index를 초기화해줍니다. 제가 넣은 이미지는 3장이기 때문에 변수는 [0],[1],[2]가 되겠죠?<br>
추가로 저는 3초 간격으로 이미지가 나왔으면 해서 JavaScript에서 사용되는 타이머 함수 중 하나인 'setInterval'함수를 활용해 3초라는 시간 간격마다 지정된 함수를 반복적으로 실행하도록 명령해줍니다.<br>
setInterval 함수는 일정한 주기로 특정 작업을 반복적으로 수행할 수 있게 해주는 함수라고 생각하시면 됩니다!

````javascript
 $(function () {
    let currentIndex = 0; // 현재 이미지

    setInterval(() => {},3000);
 });
````

<br>

▶ 이제 각각의 이미지가 3초 동안 보여지도록 지정해줄건데, 이 때에는 수학적인 개념도 살짝 필요합니다.<br>
우선 현재 이미지를 currentIndex로 지정했기 때문에 그 다음에 나오는 이미지는 nextIndex로 지정해줍니다. 그 다음 제가 넣은 이미지는 총 3장으로 변수값이 [0], [1], [2]이기 때문에 0, 1, 2가 무한 반복될 수 있게 currentIndex가 1씩 늘어날 때 마다 나머지 값이 0, 1, 2가 될 수 있게 3으로 나눠줍니다. 

````javascript
 $(function () {
    let currentIndex = 0; // 현재 이미지

    setInterval(() => {
        let nextIndex = (currentIndex + 1) % 3; // 0 1 2 0 1 2 ... 무한반복
    }, 3000);
});
````

<br>

▶ 마지막으로 eq() 메서드를 사용해 현재 인덱스에 해당하는 .slider 요소를 선택하고 fadeOut() 메서드를 호출해 이미지가 사라지도록 처리해줍니다. 반대로 이미지가 나타나게 하려면 fadeIn을 해주면 됩니다. 저는 각각의 이미지가 1초마다 사라지고 나타나도록 시간을 지정해주었어요.<br>
여기서 끝나는 게 아니라 currentIndex = nextIndex;를 추가해 다음 이미지의 인덱스로 현재 이미지의 인덱스가 반복될 수 있게 만들어주면 추가한 이미지들이 슬라이드 영역 안에서 반복되어 보여지게 됩니다.

````javascript
 $(function () {
    let currentIndex = 0; // 현재 이미지

    setInterval(() => {
        let nextIndex = (currentIndex + 1) % 3; // 0 1 2 0 1 2 ... 무한반복

        $(".slider").eq(currentIndex).fadeOut(1000); // 첫번째 이미지 사라지게 처리
        $(".slider").eq(nextIndex).fadeIn(1000);     // 두번째 이미지 나타나게 처리

        currentIndex = nextIndex;
    }, 3000);
});
````

<br>
오늘은 간단하게 레이아웃 영역에 애니메이션 효과를 주는 방법에 대해 알아봤는데요,<br>
간단한 코드만으로도 그럴싸한 효과를 낼 수 있으니 한번 따라해보는 것도 좋을 것 같습니다😊