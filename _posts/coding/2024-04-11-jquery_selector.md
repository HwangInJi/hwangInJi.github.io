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
▶ jQuery의 선택자는 HTML 문서에서 요소를 선택하기 위해 사용되는 표현식입니다. jQuery를 사용하면 CSS 선택자와 유사한 방식으로 요소를 선택할 수 있고 아래와 같은 형식을 기본으로 사용합니다.<br />
그 외에 다양한 선택자 종류를 표로 알아봅니다.

````javascript
$(selector)
````

<br />

## 01. 기본 선택자

|선택자 종류| |설명|
|:---:|:---:|:---:|
|태그 선택자|$("p")|p요소를 선택함|
|id 선택자|$("#gnb")|#gnb요소를 선택함|
|class 선택자|$(".logo")|.logo요소를 선택함|
|자식 선택자|$("#gnb > ul > li")|#gnb의 자식요소의 자식요소 li를 선택함|
|하위 선택자|$("#gnb ul)|#gnb의 하위에 있는 모든 ul요소를 선택함|
|인접 선택자|$("#visual + #content")|#visual요소 다음에 오는 #content요소를 선택함|
|형제 선택자|$("#visual ~ #footer"")|#visual요소의 형제 요소인 #footer를 선택함|
|종속 선택자|$("div.util")|div요소 중 class가 util인 요소를 선택함|
|그룹 선택자|$(".left, .right, #banner")|.left, .right, #banner요소들을 선택함|
|전체 선택자|$("*")|모든 요소를 선택함|

<br />

## 02. 속성 선택자

|선택자 종류| |설명|
|:---:|:---:|:---:|
|요소[속성]|$("span[class]")|span요소 중 class속성을 가진 요소를 선택함|
|요소[속성='값']|$("span[class='abc']")|span요소 중 class가 'abc'인 요소를 선택함|
|요소[속성!='값']|$("span[class!='abc']")|span요소 중 class가 'abc'가 아닌 요소를 선택함|
|요소[속성~='값']|$("span[class~='abc']")|span요소 중 class가 'abc'를 포함하는 요소를 선택함|
|요소[속성*='값']|$("span[class*='abc']")|span요소 중 class가 'abc'를 포함하는 요소를 모두 선택함|
|요소[속성│='값']|$("span[class│='abc']")|span요소 중 class가 'abc'나 'abc-'로 시작하는 요소를 선택함|
|요소[속성^='값']|$("span[class^='abc']")|span요소 중 class가 'abc'로 시작하는 요소를 선택함|
|요소[속성$='값']|$("span[class$='abc']")|span요소 중 class가 'abc'로 끝나는 요소를 선택함|

🔔 $("span[class~='abc']")의 형식으로 사용할 경우 'abc' 앞뒤로 연결된 문자가 없어야 합니다.<br />
즉, 'bg abc'는 선택되나 'bg_abc'는 선택되지 않습니다.

<br />

## 03. 필터 선택자
① 필터 선택자의 종류

|선택자 종류| |설명|
|:---:|:---:|:---:|
|:even|$("tr:even")|tr요소 중 짝수 행만 선택함|
|:odd|$("tr:odd")|tr요소 중 홀수 행만 선택함|
|:first|$("td:first")|첫번째 td요소를 선택함|
|:last|$("td:last")|마지막 td요소를 선택함|
|:header|$(":header")|헤딩(h1~h6) 요소를 선택함|
|:eq()|$("li:eq(0)")|index가 0인 li요소를 선택함. index는 0번이 첫번째 요소|
|:gt()|$("li:gt(0)")|index가 0보다 큰 li요소를 선택함|
|:lt()|$("li:lt(2)")|index가 2보다 작은 li요소를 선택함|
|:not()|$("li:not(.bg)")|li요소 중 class명이 bg가 아닌 요소를 선택함|
|:root|$(":root")|html을 의미함|
|:animated|$(":animated")|움직이는 요소를 선택함|

<br />
② 자식 필터 선택자의 종류

|선택자 종류| |설명|
|:---:|:---:|:---:|
|:first-child|$("span:first-child")|첫번째 span요소를 선택함|
|:last-child|$("span:last-child")|마지막 span요소를 선택함|
|:first-of-type|$("span:first-of-type")|span요소 중 첫번째 span요소를 선택함|
|:last-of-type|$("span:last-of-type")|span요소 중 마지막 span요소를 선택함|
|:nth-child|$("span:nth-child(2)")|두번째 span요소를 선택함. 2n은 짝수 요소만, 2n+1은 홀수 요소만|
|:nth-last-child|$("span:nth-last-child(2)")|마지막에서 두번째 span요소를 선택함|
|:nth-of-type|$("span:nth-of-type(2)")|span요소 중 두번째 span요소를 선택함|
|:nth-last-of-type|$("span:nth-last-of-type(2)")|span요소 중 마지막 span요소를 선택함|
|:only-child|$("div > span:only-child")|div의 자식요소에서 오직 span요소가 하나만 있는 span요소를 선택함|
|:only-of-type|$("div > span:only-of-type")|div의 자식요소에서 span요소가 하나만 있는 span요소를 선택함|

🔔 child가 붙은 선택자는 요소가 순차적으로 나열되어 있을 때 사용하고,<br />
of-type이 붙은 선택자는 순차적이 아니더라도 동일한 요소면 선택이 가능합니다.

<br />
③ 콘텐츠 필터 선택자의 종류

|선택자 종류| |설명|
|:---:|:---:|:---:|
|:contains()|$("p:contains('html')")|p요소 중 html텍스트를 포함하고 있는 p요소를 선택함|
|:empty|$("div:empty")|div요소 중 자식 요소가 없는 div요소를 선택함|
|:parent|$("span:parent")|span요소 중 자식 요소가 있는 span요소를 선택함|
|:has|$("section:has(article)")|section요소 중 article을 하위 요소로 갖고 있는 section요소를 선택함|

<br />
④ 폼 필터 선택자의 종류

|선택자 종류| |설명|
|:---:|:---:|:---:|
|:text|$("input:text")|<input type="text">요소를 선택함|
|:password|$("input:password")|<input type="password">요소를 선택함|
|:image|$("input:image")|<input type="image">요소를 선택함|
|:file|$("input:file")|<input type="file">요소를 선택함|
|:button|$(":button")|<input type="button">, <button>요소를 선택함|
|:checkbox|$("input:checkbox")|<input type="checkbox">요소를 선택함|
|:radio|$("input:radio")|<input type="radio">요소를 선택함|
|:submit|$("input:submit")|<input type="submit">요소를 선택함|
|:reset|$("input:reset")|<input type="reset">요소를 선택함|
|:input|$(":input")|모든 <input>요소를 선택함|
|:checked|$("input:checked")|<input>요소에 checked 속성이 있는 요소를 선택함|
|:selected|$("option:selected")|<option>요소에 selected 속성이 있는 요소를 선택함|
|:focus|$("input:focus")|현재 <input>요소에 focus가 있는 요소를 선택함|
|:disabled|$("input:disabled")|<input>요소에 disabled속성이 있는 요소를 선택함|
|:enabled|$("input:enabled")|<input>요소 중 enabled가 아닌 요소를 선택함|

<br />
⑤ 가시성 필터 선택자의 종류

|선택자 종류| |설명|
|:---:|:---:|:---:|
|:hidden|$("div:hidden")|div요소 중 hidden인 요소를 선택함|
|:visible|$("div:visible")|div요소 중 visible인 요소를 선택함|

<br />

## 04. 탐색 선택자
① 기본 탐색 선택자의 종류

|선택자 종류| |설명|
|:---:|:---:|:---:|
|children()|$("div").children()|div요소의 자식 요소를 선택함|
|parent()|$("p").parent()|p요소의 부모 요소를 선택함|
|parents()|$("p").parents("div")|p요소의 부모가 되는 모든 div 요소를 선택함|
|closet()|$("p").closet("div")|p요소의 부모가 되는 첫번째 div 요소를 찾음|
|next()|$("div.m").next()|div.m요소의 다음 요소를 선택함|
|nextAll()|$("div.m").nextAll()|div.m요소의 다음 요소들을 모두 선택함|
|nextUntil()|$("div.m").nextUntil("p")|div.m 다음 요소부터 p요소 전까지의 요소를 선택함|
|prev()|$("div.m").prev()|div.m요소의 이전 요소를 선택함|
|prevAll()|$("div.m").prevAll()|div.m요소의 이전 요소들을 모두 선택함|
|prevUntil()|$("div.m").prevUntil("p")|div.m이전 요소부터 p요소 다음 요소까지를 선택함|
|siblings()|$("div").siblings("p")|div요소의 형제 요소 중 p요소를 선택함|
|find()|$("div").find("span")|div의 하위요소 중 span요소를 선택함|
|filter()|$("div").filter(".m")|div요소 중 class가 m인 요소를 선택함|
|not()|$("div").not(".m")|div요소 중 class가 m이 아닌 요소를 선택함|
|has()|$("div").has("span")|div요소 중 span요소를 포함하고 있는 요소를 선택함|
|eq()|$("div").eq(0)|div요소 중 index가 0인 요소들을 선택함. index 0번이 첫번째 요소|
|gt()|$("div").gt(0)|index가 0보다 큰 div 요소들을 선택함|
|lt()|$("div").lt(3)|index가 3보다 작은 div 요소들을 선택함|

<br />
② 기타 탐색 선택자의 종류

|선택자 종류| |설명|
|:---:|:---:|:---:|
|add()|$("div").add("p")|div요소와 p요소를 선택함|
|addBack()|$("div").children("p").addBack()|p요소와 이전 선택요소 div를 선택함|
|end()|$("div").find("span").css(...).end().find("em")|.css(...)까지의 실행이 끝나면 다시 $("div")로 돌아와 find("em")부터 실행|
|is()|if("div").children().is("p")|선택한 요소를 판별해주는 선택자로 보통 if문의 조건식으로 사용|