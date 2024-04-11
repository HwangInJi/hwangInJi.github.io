---
layout: post
title: BOX MODEL
date: 2024-04-09 17:29 +0900
description: CSS BOX MODEL에 대해서 알아보기
image: ../assets/img/boxmodel.jpg
category: CSS
tags: CSS boxmodel BOXMODEL
published: true
sitemap: true
---

# BOX MODEL이란?
▶ CSS의 Box Model(박스 모델)은 웹 페이지에서 요소(element)의 레이아웃(layout)을 정의하는 중요한 개념입니다.<br />
여기서 BOX는 콘텐츠(content)가 자리하는 영역을 말하며, 여기에 나올 속성들은 안쪽 여백(padding), 테두리(border), 바깥 여백(margin)등 주로 블록 요소에서 적용됩니다.
<br />

## 01. width, height
▶ width는 요소의 가로 크기, height는 요소의 세로 크기를 말하며, 기본적으로 여백과 테두리는 포함되지 않습니다.<br />
px, %, em 등 각종 단위를 함께 사용할 수 있고, min과 max를 사용해 최소, 최대값을 지정할 수 있습니다.

````css
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Width와 Height CSS 예제</title>
<style>
    /* 스타일링을 위한 CSS 코드 */
    .box {
        width: 200px; /* 너비 200px 지정 */
        height: 150px; /* 높이 150px 지정 */
        background-color: #f0f0f0; /* 배경색 지정 */
    }
</style>
</head>
<body>
    <!-- div 요소에 box 클래스를 적용하여 스타일을 적용함 -->
    <div class="box">
        이 상자의 너비는 200px이고 높이는 150px입니다.
    </div>
</body>
</html>
````

|속성 값|속성 설명|
|:---:|:---:|
|width|요소의 가로폭|
|height|요소의 세로(높이)폭|
|min-width: 1000px;|요소의 가로폭을 1000px이상으로 지정함을 의미|
|min-height: 1000px;|요소의 높이값을 1000px이상으로 지정함을 의미|
|max-width: 1000px;|요소의 너비값을 1000px이하로 지정함을 의미|
|max-height: 1000px;|요소의 높이값을 1000px이하로 지정함을 의미|

🔔<br />
일정 크기 이상의 공간을 유지하고자 하려면 min-width, min-height 지정<br />
브라우저를 늘려도 일정 크기 이상 늘어나지 않도록 하려면 max-width, max-height 지정
<br />

## 02. padding
▶ padding은 요소의 안쪽 여백인 내용과 테두리 사이의 여백을 의미합니다.<br />
주의할 점은 padding의 여백값은 width에 포함되지 않는다는 점입니다.

````css
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Padding을 사용한 CSS 예제</title>
<style>
    /* 스타일링을 위한 CSS 코드 */
    .container {
        padding: 10px 20px 30px 40px; /* 상, 우, 하, 좌 순으로 안쪽 여백 지정 */
        background-color: #f0f0f0; /* 배경색 지정 */
    }
</style>
</head>
<body>
    <!-- .container 클래스를 가진 div 요소 -->
    <div class="container">
            이 텍스트 주위에는 padding 속성을 사용하여 여백이 적용됩니다.
        </div>
    </div>
</body>
</html>
````

|속성 값|속성 설명|
|:---:|:---:|
|padding: 10px;|위, 아래, 왼, 오 각각 10px의 여백을 준다는 의미|
|padding: 10px 20px;|위&아래: 10px / 왼&오: 20px의 여백을 준다는 의미|
|padding: 10px 20px 30px;|위: 10px / 왼&오: 20px / 아래: 30px의 여백을 준다는 의미|
|padding: 10px 20px 30px 40px;|위: 10px / 오: 20px / 아래: 30px / 왼: 40px의 여백을 준다는 의미|
|padding-top: 10px;|위: 10px의 여백을 준다는 의미|
|padding-right: 10px;|오: 10px의 여백을 준다는 의미|
|padding-bottom: 10px;|아래: 10px의 여백을 준다는 의미|
|padding-left: 10px;|왼: 10px의 여백을 준다는 의미|

<br />

## 03. margin
▶ margin 요소의 바깥 여백인 테두리와 다음 박스 사이의 여백을 의미합니다.<br />
주의할 점은 margin은 여백값은 width에 포함되지 않는다는 점이며, margin을 좌우로 주면 가로 길이가 줄어듭니다.

````css
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Margin을 사용한 CSS 예제</title>
<style>
    /* 스타일링을 위한 CSS 코드 */
    .box {
        width: 200px; /* 너비 200px 지정 */
        height: 150px; /* 높이 150px 지정 */
        background-color: #f0f0f0; /* 배경색 지정 */
        margin: 20px; /* 바깥 여백 지정 */
    }
</style>
</head>
<body>
    <!-- div 요소에 box 클래스를 적용하여 스타일을 적용함 -->
    <div class="box">
        width와 height 속성을 사용하여 200px × 150px 크기의 상자가 만들어졌고,
        이 상자 주위에는 20px의 바깥 여백이 적용됩니다.
    </div>
</body>
</html>
````

|속성 값|속성 설명|
|:---:|:---:|
|margin: 10px;|위, 아래, 왼, 오 각각 10px의 여백을 준다는 의미|
|margin: 10px 20px;|위&아래: 10px / 왼&오: 20px의 여백을 준다는 의미|
|margin: 10px 20px 30px;|위: 10px / 왼&오: 20px / 아래: 30px의 여백을 준다는 의미|
|margin: 10px 20px 30px 40px;|위: 10px / 오: 20px / 아래: 30px / 왼: 40px의 여백을 준다는 의미|
|margin-top: 10px;|위: 10px의 여백을 준다는 의미|
|margin-right: 10px;|오: 10px의 여백을 준다는 의미|
|margin-bottom: 10px;|아래: 10px의 여백을 준다는 의미|
|margin-left: 10px;|왼: 10px의 여백을 준다는 의미|

🔔<br />
margin은 세로의 겹침이 발생할 수 있는데, 이 때 두 박스 사이의 간격은 둘 중 가장 큰 값으로 지정이 됩니다.
<br />
▶ 추가로 margin: 0 auto;를 사용하면 중앙정렬을 할 수 있으며, 아래와 같은 형식처럼 사용합니다.

````css
.box_inner {
  width: 1000px;
  margin: 0 auto;
}
````

<br />

## 04. border
▶ border는 박스의 테두리를 말하며, 다양한 방식으로 테두리를 지정할 수 있습니다.

① 테두리 선 종류

|선의 종류|속성 설명|
|:---:|:---:|
|solid|실선|
|dotted|점선|
|dashed|긴 점선|
|double|두 줄 실선 (굵기가 적어도 3px이상)|
|none|테두리 없음|
|groove, ridge, inset, outset|각종 액자 형태의 테두리|

<br />
② style, width, color

|속성 값 예문|속성 설명|
|:---:|:---:|
|border-color: blue;|테두리 색상 파란색으로 지정함을 의미 (색상명, HEX, RGB, HSL, RGBA, HSLA 모두 가능)|
|border-width: 2px;|테두리 굵기를 2px로 지정함을 의미|
|border-style: solid;|테두리 선을 실선으로 지정함을 의미|
|border-top: 1px solid red;|위쪽 테두리만 1px 굵기의 빨간색 실선으로 지정함을 의미|
|border-left: 1px solid red;|왼쪽 테두리만 1px 굵기의 빨간색 실선으로 지정함을 의미|
|border-right: 1px solid red;|오른쪽 테두리만 1px 굵기의 빨간색 실선으로 지정함을 의미|
|border: 1px solid red;|테두리 사방 모두 1px 굵기의 빨간색 실선으로 지정함을 의미|

<br />
③ 둥근 테두리 모서리 : border-radius를 사용하면 테두리를 둥글게 만들 수 있으며, 아래와 같은 형식처럼 사용합니다.

````bash
border-radius: 5px; // 값이 하나인 경우 네 모서리 모두 동일하게 적용
````

````bash
border-radius: 10px 20px 30px 40px; // 값이 네 개인 경우 좌측 상단을 시작점으로 하여 시계방향 순으로 적용
````

<br />
④ 테두리에 무늬 입히기 : border-image를 사용하면 테두리를 도형 패턴으로 만들 수 있으며, 종류는 3가지가 있습니다.

````bash
border-image: url(boder.png) 20 round;
border-image: url(boder.png) 20 repeat;
border-image: url(boder.png) 20 stretch;
````

<br />

## 05. outline
▶ outline은 border영역 외곽에 박스의 테두리를 지정하는 속성으로 style, width, color라는 속성들을 사용할 수 있으나,<br />
네 면이 공동으로 적용되는 특징이 있어 위, 아래, 왼쪽, 오른쪽 따로 적용은 불가능합니다.

````bash
outline: 5px solid red;
````

▶ border와 outline 사이의 간격을 주고 싶을 경우, outline-offset을 사용하면 됩니다.

````bash
outline-offset: 5px;
````

<br />

## 06. box-sizing
▶ box-sizing은 box의 크기를 의미하나 기본적으로 width, height 값에 padding, border 값은 포함되지 않습니다.<br />
따라서, width 값이 100%로 설정이 되어 있다면 padding이나 border 속성을 추가할 수 없습니다.<br />
때문에 CSS에서는 box의 크기가 여백과 테두리를 포함해도 원래의 크기를 넘지않도록 하기 위해 box-sizing을 사용합니다.

````bash
box-sizing: boeder-box;
````

|속성 값 예문|속성 설명|
|:---:|:---:|
|box-sizing: content-box;|요소의 전체 크기에 padding, border 값을 포함 시킴|
|box-sizing: boeder-box;|요소의 전체 크기에 padding, border 값을 포함시키지 않음|

<br />

## 07. box-shadow
▶ box-shadow는 CSS에서 그림자를 만들어주는 요소입니다.

````bash
box-shadow: 8px 15px 10px 7px inset rgba(0, 0, 50, 0.4);
````

|속성 값 예시|속성 설명|
|:---:|:---:|
|8px|그림자가 원본과 가로로 떨어진 간격|
|15px|그림자가 원본과 tp로로 떨어진 간격|
|10px|그림자의 흐릿한 정도(=blur)|
|7px|그림자의 확장|
|inset|그림자가 안쪽에 나타남|
|rgba(0, 0, 50, 0.4)|그림자의 색상|

<br />

## 08. resize
▶ resize는 마우스로 box의 모서리를 잡고 드래그했을 때 크기 조절의 가능여부를 지정해주는 요소입니다.

````bash
resize: both;
````

|속성 값|속성 설명|
|:---:|:---:|
|horizontal|박스의 가로방향으로 크기 조절 가능|
|vartical|박스의 세로방향으로 크기 조절 가능|
|both|박스의 가로, 세로 양방향으로 크기 조절 가능|
|none|박스의 크기 조절 불가능|

<br />

## 09. appearance
▶ appearance는 CSS 속성 중 하나로, 표준 컨트롤 요소의 외관을 사용자 지정하는 데 사용됩니다.<br />
이 속성은 주로 웹 폼 요소를 스타일링하는 데 사용되며, 요소의 기본적인 스타일을 브라우저의 네이티브 스타일 대신 사용자가 지정한 스타일로 변경할 수 있습니다.

|속성 값|속성 설명|
|:---:|:---:|
|auto|브라우저가 요소의 외관을 결정 (기본값)|
|none|브라우저의 네이티브 스타일을 사용하지 않고 외관을 사용자가 직접 스타일링할 수 있도록 함|
|menulist-button|셀렉트 박스의 버튼 부분을 스타일링할 때 사용|
|textfield|텍스트 필드 요소를 스타일링할 때 사용|
|searchfield|검색 필드 요소를 스타일링할 때 사용|

````css
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Custom Button with Appearance</title>
<style>
    /* 스타일링을 위한 CSS 코드 */
    .custom-button {
        appearance: none; /* 네이티브 스타일을 사용하지 않음 */
        background-color: #007bff; /* 배경색 */
        color: #fff; /* 글자색 */
        border: none; /* 테두리 없음 */
        padding: 10px 20px; /* 내부 여백 */
        border-radius: 5px; /* 테두리 반경 */
        cursor: pointer; /* 커서 모양 */
        font-size: 16px; /* 글자 크기 */
    }
</style>
</head>
<body>
    <!-- appearance: none을 사용하여 네이티브 스타일을 사용하지 않도록 설정  -->
</body>
</html>
````