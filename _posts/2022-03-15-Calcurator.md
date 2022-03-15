---
layout: post
title: Calculator
---

<br><br>

## Toy Project

2022-03-14-Calculator.html

<br><br>

JS로 caculator 만들어보기 시작

- 기능 : 사칙연산, 숫자가 표기되는 display, 초기화, 소수점

- 형태 : 보편적으로 사용되는 버튼 배치

- 구현 : main, div, button 구성<br>
  안에 grid 형태는 이해가 안됨 따라서 만듦 공부할 것

<br>

```html
<link rel="stylesheet" htref="style.css" />
<!--css 따로 삽입-->
```

```html
<button>n</button>
<!--버튼에 쓰일 연산기호는 ㄷ+한자로 넣어야 깔끔-->
```

<br>

```css
main {
  width: 280px;
}
/*main: body요소의 주요 contents(반복되지 않는)
크기를 지정해주지 않으면 page에 자동 맞춤=안예쁨*/

* {
  box-sizing: border-box;
  /*textbox 사이즈가 아래 버튼과 일치하게만듦*/
  color: white;
  /*버튼내부 글자를 흰색으로 지정함*/
} /* '*'전체 선택자 모든 contents에 속성부여 */

input,
button {
  height: 70px;
} /*input display랑 button 높이*/

input {
  width: 100%;
  /*button과 width맞춤*/
  text-align: right;
  background-color: #5b5b5d;
}

button {
  background-color: #828284;
  font-size: 2rem;
} /*rem: responsible site 만들기위한 font 단위
  (root em)최상위 요소 html에 비례하여 크기를 가지는 상대적길이*/

button:hover {
  opacity: 0.5;
} /* hover: 마우스오버
    opacity: 불투명도 */
```
