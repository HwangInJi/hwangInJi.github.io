---
layout: post
title: jQuery로 이미지 슬라이드 애니메이션 넣기
date: 2024-04-16 17:29 +0900
description: jQuery 이미지 슬라이드 애니메이션에 대해서 알아보기
image: ../assets/img/sliderani.jpg
category: jQuery
tags: jQuery 제이쿼리 애니메이션
published: true
sitemap: true
---

# 자바스크립트 이미지 레이아웃 애니메이션 효과

![Frame 42](https://github.com/HwangInJi/class2024/assets/163365140/9130dff1-7470-43d9-9b7e-88e6d8a5a4e1)

오늘은 어제에 이어 슬라이드 영역에 왼쪽으로 이미지가 한장씩 넘어가며 보여지는 방법을 알려드리려고 하는데요,<br>

이번에도 어렵지 않으니 한번 따라해보세요!

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
▶ 큰 틀을 만들었다면 그 다음엔 'sliderWrap' 안에 추가하고자 하는 이미지 개수만큼 img 링크를 추가해줍니다.<br>
만약 이미지 가운데에 문구를 넣고 싶다면 하나의 text class를 만들어 내용을 넣어주는 것도 하나의 디자인 방법이 되겠죠?<br>
저는 이 방식으로 총 3장의 이미지와 그에 어울리는 문구를 넣어보았어요!


````javascript
<article id="slider">
    <div class="slider-wrap">
        <div class="slider s1">
            <a href="#"><img src="images/banner1.jpg" alt="미래를 구축하는 혁신"></a>
            <div class="text">
                <h2>미래를 구축하는 혁신</h2>
                <p>여러분의 비전을 현실로 만들어 드립니다.</p>
            </div>
        </div>
        <div class="slider s2">
            <a href="#"><img src="images/banner2.jpg" alt="안전과 품질을 최우선으로.."></a>
            <div class="text">
                <h2>안전과 품질을 최우선으로..</h2>
                <p>고객 만족을 넘어 고객 감동 추구</p>
            </div>
        </div>
        <div class="slider s3">
            <a href="#"><img src="images/banner3.jpg" alt="지속 가능한 건축을 선도"></a>
            <div class="text">
                <h2>지속 가능한 건축을 선도</h2>
                <p>환경을 생각하는 건설 솔루션</p>
            </div>
        </div>
    </div>
</article>
````

<br>

## 3. style css 추가 입력하기
▶ 기존 레이아웃에 새로운 'sliderWrap' 이라는 영역이 추가되었으니 style css에도 수정이 필요하겠죠?<br>
먼저 slider안에 img가 들어가되, 왼쪽으로 옮겨지면서 이동할 예정이기 때문에 sliderWrap에 'display: flex;'를 이용해 가로 정렬을 해줍니다.

````css
.sliderWrap {
    display: flex;
}
````

<br>

▶ 그 다음 .slider라는 부모 요소에 img라는 자식 요소가 있기 때문에 부모에는 position: relative;을 이용해 상대적인 위치를 지정해주고 img에는 vertical-align: top;을 넣어 이미지의 여백을 없애줍니다.

````css
.slider-wrap {
    display: flex;
}

.slider-wrap .slider {
    position: relative;
}

.slider-wrap .slider img {
    vertical-align: top;
}
````

<br>

▶ 오늘은 어제와 달리 text요소를 추가했기 때문에 left: 50%; top: 50%;을 줌으로서 .slider의 가로와 세로 중앙에 위치시킨 후 transform: translate(-50%, -50%);: translate 함수를 사용하여 요소를 가운데 정렬시켜줍니다.<br>
text요소 또한 sliderWrap의 자식 요소이기 때문에 position: absolute;를 추가해줄게요! 여기에 padding과 background-color값까지 준다면 문구를 둘러싼 틀이 만들어져 내가 쓴 글이 더 잘 보일 수 있겠죠?<br>


````css
.slider-wrap {
    display: flex;
}

.slider-wrap .slider {
    position: relative;
}

.slider-wrap .slider img {
    vertical-align: top;
}

.slider-wrap .slider .text {
    position: absolute;
    left: 50%;
    top: 50%;
    transform: translate(-50%, -50%);
    text-align: center;
    background-color: rgba(0, 0, 0, 0.658);
    color: #fff;
    padding: 10px 20px;
}
````

여기까지 잘 따라오셨다면 이미지가 slider영역에 들어간 게 보이실거에요!

<br>

## 4. jQuery를 활용해 애니메이션 효과주기
▶ 이제 마지막 단계로 script에 jQuery 코드를 활용해 애니메이션 이벤트를 실행시켜주면 되는데<br>
💡 오늘의 핵심 포인트는 3장의 이미지가 순서대로 한번씩 나온 후 다시 첫번째 이미지가 나왔을 때 초기화를 시켜준다는 점이에요!<br><br>

먼저 변수인 let을 이용해 현재의 이미지를 currentIndex로 지정하고 0으로 초기화를 시켜줍니다.<br>
여기에 전체 슬라이드 이미지 중에서 첫번째 슬라이드 이미지를 복사해 추가해주는 수식을 만들어줍니다.<br>
append: 추가 / first: 첫번째 요소 / clone : 복사<br>
그 다음 JavaScript에서 사용되는 타이머 함수 중 하나인 'setInterval'함수를 활용해 3초라는 시간 간격마다 지정된 함수를 반복적으로 실행하도록 명령해줍니다.(시간은 본인 마음대로!)

````javascript
 let currentIndex = 0; //현재 이미지
$(".slider-wrap").append($(".slider").first().clone(true));
//첫번째 이미지를 복사해서 마지막에 추가

setInterval(() => {

});
````

<br>

▶ 이 때 지정된 함수는 이미지가 1장씩 증가할 때마다 값이 달라지며 왼쪽으로 일정 시간안에 이동해야하는 애니메이션 효과를 주어야하는데요,<br>
전체 슬라이드 이미지 영역에서 현재의 이미지가 0, -100, -200, 0, -100, -200...무한으로 나올 수 있도록 현재의 이미지값에 100을 곱해준 후 나눈다는 의미의 "%"를 적용해주면 전체 슬라이드 장수 만큼 자동으로 나눗셈이 되기 때문에 0, -100, -200이 반복적으로 나오겠죠?
````javascript
let currentIndex = 0; //현재 이미지
$(".slider-wrap").append($(".slider").first().clone(true)); //첫번째 이미지를 복사해서 마지막에 추가

setInterval(() => {
    currentIndex++;     //현재 이미지 1씩 증가

    $(".slider-wrap").animate({ marginLeft: -currentIndex * 100 + "%" }, 600);
});
````

<br>

▶ 마지막으로 위에서 처음에 핵심 포인트로 언급했던 것 처럼 3장의 이미지가 순서대로 한번씩 나온 후 다시 첫번째 이미지가 나왔을 때 초기화를 시켜야 하기 때문에 이 부분에 대한 작업이 필요합니다.<br>
여기선 if문을 사용하면 편한데, 만약 currentIndex가 3(마지막 이미지)일 때 setTimeout이라는 메서드를 이용해 일정 시간이 지난 후에 특정한 작업을 실행하도록 예약시켜줍니다. 이 때 저는 그 일정 시간을 0.7초로 지정해주었어요.

````javascript
let currentIndex = 0; //현재 이미지
$(".slider-wrap").append($(".slider").first().clone(true)); //첫번째 이미지를 복사해서 마지막에 추가

setInterval(() => {
    currentIndex++;     //현재 이미지 1씩 증가

    $(".slider-wrap").animate({ marginLeft: -currentIndex * 100 + "%" }, 600);

    if (currentIndex == 3) { //마지막 이미지 일 때
        setTimeout(() => {   
           
        }, 700);
    }
}, 3000);
````

<br>

▶ 여기에 다시 애니메이션 효과를 주는데 위에와 달리 이번엔 초기화가 목적이기 때문에 값을 모두 0으로 처리해 애니메이션 효과를 정지시켜줍니다.<br>
여기서 끝나는 게 아니라 currentIndex = 0;이라는 현재 이미지 초기화를 추가해주면 0.7초안에 3장의 이미지가 나오고 다시 처음 이미지가 왔을 때 초기화되어 다시 0, -100, -200에 해당하는 이미지들이 슬라이드 영역 안에서 반복되어 옆으로 이동하게 됩니다.

````javascript
 let currentIndex = 0; //현재 이미지
$(".slider-wrap").append($(".slider").first().clone(true)); //첫번째 이미지를 복사해서 마지막에 추가

setInterval(() => {
    currentIndex++;     //현재 이미지 1씩 증가

    $(".slider-wrap").animate({ marginLeft: -currentIndex * 100 + "%" }, 600);

    if (currentIndex == 3) { //마지막 이미지 일 때
        setTimeout(() => {   //setTimeout은 한번만 실행
            $(".slider-wrap").animate({ marginLeft: 0 }, 0); //애니메이션 정지
            currentIndex = 0; //현재 이미지 초기화
        }, 700);
    }
}, 3000);
````

<br>
오늘도 간단한 방법으로 레이아웃 영역에 애니메이션 효과를 주는 방법에 대해 알아봤는데요,<br>
간단한 코드만으로도 그럴싸한 효과를 낼 수 있으니 한번 따라해보는 것도 좋을 것 같습니다😊