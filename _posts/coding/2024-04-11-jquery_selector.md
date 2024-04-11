---
layout: post
title: jQuery 선택자
date: 2024-04-11 17:29 +0900
description: jQuery 선택자에 대해서 알아보기
image: ../assets/img/jqueryselect.jpg
category: jQuery
tags: jQuery 제이쿼리 선택자 select
published: true
sitemap: true
---

# jQuery 선택자란?
▶ jQuery의 선택자는 HTML 문서에서 요소를 선택하기 위해 사용되는 표현식입니다. jQuery를 사용하면 CSS 선택자와 유사한 방식으로 요소를 선택할 수 있고 아래와 같은 형식을 기본으로 사용합니다.

````javascript
$(selector)
````

## 01. 기본 선택자
▶ 요소의 배경 색상을 지정하는 속성으로 아래와 같은 형식처럼 사용합니다.

|선택자 종류|설명|
|:---:|:---:|:---:|
|태그 선택자|$("p")|p요소를 선택함|
|id 선택자|$("#gnb")|#gnb요소를 선택함|
|class 선택자|$(".logo")|.logo요소를 선택함|
|자식 선택자|$("#gnb > ul > li")|#gnb의 자식요소의 자식요소 li를 선택함|
|하위 선택자|$("#gnb ul)|#gnb의  선택함|
|인접 선택자|$("p")|p요소를 선택함|
|형제 선택자|$("p")|p요소를 선택함|
|종속 선택자|$("p")|p요소를 선택함|
|그룹 선택자|$("p")|p요소를 선택함|
|전체 선택자|$("p")|p요소를 선택함|

