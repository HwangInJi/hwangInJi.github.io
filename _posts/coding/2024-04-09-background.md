---
layout: post
title: 배경(background)
date: 2024-04-09 17:29 +0900
description: CSS 배경(background)에 대해서 알아보기
image: ../assets/img/background.jpg
category: CSS
tags: CSS 배경 background
published: true
sitemap: true
---

# 배경(background)란?
▶ 배경(background)이란 색상, 이미지, 반복여부, 위치, 고정여부 등의 기술적인 부분을 시각적 요소로 표현한 것을 말합니다.
   CSS에서는 일반적으로 색상, 이미지, 그라디언트 등을 사용하여 요소를 꾸미는 데 사용됩니다.
<br />

## 01. background-color
▶ 요소의 배경 색상을 지정하는 속성으로 아래와 같은 형식처럼 사용합니다.

````bash
background-color: #abcdef;
````

|속성 값|속성 설명|
|:---:|:---:|
|색상값|색상명, HEX값, RGB값, HSL값, RGBA값, HSLA값|
|transparent|투명 (기본값)|
<br />

## 02. background-image
▶ 요소의 배경에 들어갈 이미지를 지정하는 속성으로 아래와 같은 형식처럼 사용합니다.<br />
용량이 클 경우 속도 저하의 원인이 될 수 있기 때문에 해상도가 큰 이미지는 꼭 필요한 상황이 아니면 지양하는 것이 좋습니다.

````bash
background-image: url(img/bgimg.png);
````

|속성 값|속성 설명|
|:---:|:---:|
|url(~)|이미지의 경로와 파일명을 기술함|
|none|배경 이미지 없음 (기본값)|
<br />

## 03. background-repeat
▶ 배경 이미지를 어떻게 반복시킬지 지정하는 속성으로 아래와 같은 형식처럼 사용합니다.

````bash
background-repeat: no-repeat;
````

|속성 값|속성 설명|
|:---:|:---:|
|repeat|배경 이미지를 가로, 세로 반복하여 배치 (기본값)|
|no-repeat|배경 이미지를 한 개만 배치|
|repeat-x|배경 이미지를 가로로만 반복 배치|
|repeat-y|배경 이미지를 세로로만 반복 배치|
|space|배경 이미지를 반복하다가 마지막 이미지가 가로로 잘리지 않도록 배치하기 위해 이미지 사이가 벌어짐|
|round|배경 이미지를 반복하다가 마지막 이미지가 세로로 잘리지 않도록 배치하기 위해 이미지가 납작하게 찌그러짐|
<br />
▶ 만약 배경 이미지가 요소 안에 있는 콘텐츠들과 겹치지 않도록 하고 싶을 경우 padding속성과 함께 사용하면 됩니다.<br />
※ padding: 100px -> 상하, 좌우 모두 100px 만큼의 여백을 두라는 의미

````bash
padding: 100px
background-repeat: no-repeat;
````
<br />

## 04. background-position
▶ 배경 이미지를 원하는 위치로 옮겨주는 속성으로 아래와 같은 형식처럼 사용합니다.<br />
한 개만 배치할 경우 기본적으로는 좌측 상단에 나타나는데 background-position을 이용하면 가로, 세로 위치 지정이 가능합니다.

````bash
background-position: 50% top;
````

|위치|속성 설명|
|:---:|:---:|
|가로 위치|left, right, center, px값 등 (기본값: left)|
|세로 위치|top, bottom, center(middle아님), px값, %값 등 (기본값: top)|
<br />
▶ 만약 배경 이미지가 요소 안에 있는 콘텐츠들과 겹치지 않도록 하고 싶을 경우 padding속성과 함께 사용하면 됩니다.<br />
※ padding: 100px -> 상하, 좌우 모두 100px 만큼의 여백을 두라는 의미

````bash
padding: 100px
background-position: 50% top;
````
<br />

## 05. background-attachment
▶ 배경 이미지를 요소 내에 고정시킬지, 화면에 고정시킬지 지정하는 속성으로 아래와 같은 형식처럼 사용합니다.

````bash
background-attachment: fixed;
````

|속성 값|속성 설명|
|:---:|:---:|
|scroll|배경 이미지가 화면을 스크롤하면 따라감 (기본값)|
|fixed|배경 이미지가 화면을 스크롤해도 따라가지 않음|
<br />

## 06. background-size
▶ CSS3에서 배경 이미지의 크기를 변경하는 속성으로 아래와 같은 형식처럼 사용합니다.

````bash
background-size: 120px(=가로) 90px(=세로);
````

|속성 값|속성 설명|
|:---:|:---:|
|background-size: 120px 90px;|배경 이미지의 가로 크기 80px,세로 크기 60px라는 의미|
|background-size: 50% 100%;|배경 이미지의 가로 크기 50%,세로 크기 100%라는 의미|
|background-size: auto;|배경 이미지를 원래 크기로 배치하고 남는 공간은 비움|
|background-size: contain;|배경 이미지를 잘리지 않도록 배치하고 남는 공간은 비움|
|background-size: cover;|배경 이미지를 빈 공간없이 요소에 꽉 채우고 나머지는 잘림|
<br />

## 07. background-origin
▶ CSS3에서 배경 이미지의 시작점을 정하는 속성으로 아래와 같은 형식처럼 사용합니다.

````bash
background-origin: border-box;
````

|속성 값|속성 설명|
|:---:|:---:|
|border-box|배경 이미지가 테두리 좌측 상단 모퉁이에서 시작함|
|padding-box|배경 이미지가 안여백의 좌측 상단 모퉁이에서 시작함 (기본값)|
|content-box|배경 이미지가 콘텐츠의 좌측 상단부터 시작함|
<br />

## 08. background-clip
▶ CSS3에서 배경의 영역을 지정하는 속성으로 아래와 같은 형식처럼 사용합니다.

````bash
background-clip: border-box;
````

|속성 값|속성 설명|
|:---:|:---:|
|border-box|배경이 테두리를 포함한 영역에 배치 (기본값)|
|padding-box|배경이 테두리를 제외한 안쪽 영역에 배치|
|content-box|배경이 안여백을 제외한 콘텐츠 영역에만 배치|
<br />

## 09. Image Sprit
▶ 이미지가 많아지면 속도가 느려지는 단점을 보완하기 위해 사용하는 속성으로 아래와 같은 형식처럼 사용합니다.<br />
Image Sprit은 사용하는 여러 이미지들을 하나로 저장한 후 background-position을 이용하여 잘라 사용합니다.

````javascript
.nav {
display: flex;
}

.nav a {
display: block;
width: 40px;
height: 40px;
<span style="color:yellow">background-image: url('sprites.png');</span>
}

.home {
<span style="color:yellow">background-position</span>: 0 0; /* 스프라이트 이미지 내에서 홈 아이콘의 위치 */
}

.about {
<span style="color:yellow">background-position</span>: -40px 0; /* 스프라이트 이미지 내에서 about 아이콘의 위치 */
}

.contact {
<span style="color:yellow">background-position</span>: -80px 0; /* 스프라이트 이미지 내에서 contact 아이콘의 위치 */
}
````
## 10. 배경에 gradient 적용하기
## 11. multiple background