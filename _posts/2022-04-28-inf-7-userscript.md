---
layout: post
title: inf 7 userscript
---

<br><br>

## WEB service

demo4.html

<br><br>

폼 입력 대신하기

간편 결제를 더 유용하게 하기

- QR스캔 또는 전화번호와 생년월일을 매번 입력하기 번거로움

- 프로그래밍으로 대신 전화번호, 생년월일을 넣을 수 있을지<br>
  HTMLInputElement.value - element의 값을 읽거나 대입<br>
  HTMLElement.click() - element를 click

<br>

userscript manager

- 영구적으로 코드를 주입할 수 있는 확장기능
- browser별로 별도의 userscript manager를 선택해야 함
  - Opera : Tampermonkey, Violentmonkey
  - Chrome : Tampermonkey, Violentmonkey
  - Safari : Tampermonkey
  - Firefox : Greasemonkey, Tampermonkey, Violentmonkey
  - Microsoft Edge : Tampermonkey

<br>

작업을 할 WEBpage

- naver login화면
  - 결제page는 괜히 꺼림칙<br>
    로그인할 때 일일이 id입력하는게 귀찮아서 선정

작업할 내용

- id에 zzphoo입력

id값 추출, code작성

- 개발자 도구사용<br>
  id값 : #id.input_text
- code

  ```javascript
  document.querySelector("#id.input_text").value = zzphoo;
  ```

  id값의 위치에 value로 입력하려는 id값 지정

- localStorage에 id 값을 저장해 봤는데 불러오기 실패<br>
  사용법 더 찾아볼 것

  - localStorage는 Documetn출처의 Storage객체에 data저장<br>
    concole창에서 미리 setting 해놓으니 적용 성공

  ```javascript
  const id = localStorage.setItem("id", "zzphoo");
  //setting
  const id = localStorage.getItem("id");
  //작동
  ```

  콘솔창에서 localStorage를 미리 세팅해두고
  userscript manager에 저장

  ```javascript
  // ==UserScript==
  // @name         naver_id
  //               ㄴ식별가능한 이름으로 변경
  // @namespace    http://tampermonkey.net/
  // @version      0.1
  // @description  try to take over the world!
  // @author       You
  // @match        https://nid.naver.com/nidlogin.login?mode=form&url=https%3A%2F%2Fwww.naver.com
  //               ㄴ사용할 page 설정
  // @icon         https://www.google.com/s2/favicons?sz=64&domain=naver.com
  // @grant        none
  //               ㄴ원래 Storage를 사용하려면 localStorage를 적용해야하는데
  //                 입력해도, none상태에서도 작동함.. 이유 모름
  // ==/UserScript==

  (function () {
    "use strict";
    const id = localStorage.getItem("id");
    document.querySelector("#id.input_text").value = id;
  })();
  ```

  - page가 새로고침될 때 계속 바뀌는 문자열이 있으면<br>
    `*` 별표로 치환해서 입력 : 문자열이 계속 바뀌어도 적용가능

<br><br>

강의를 처름 틀어놓고 영상아래 부연설명 구간을 살펴 보면서<br>
'아 이걸 어떻게 하지', '설명도 상당히 조잡하네' 등 온갖 부정정인 생각을 함<br>
localStrage 부분이나 몇가지 code는 처음보는 것 인데도 불구하고<br>
해석, 설명이 하나도 없어서 'DOM공부까지는 했으니 이 부분은 넘어갈까?'<br>
라는 생각까지 할 정도로 벽에 가로막힌 기분이 들었음

하지만 '일단 다 들어보긴 하자' 라는 마음으로 강의를 듣고<br>
모르는 부분은 MDN이나 Googling해서 공부하며 진행함<br>
결과적으로 내가 개발자의 길을 걷지 않더라도 실생활에서 가볍게 적용해서<br>
사용할 수 있을만한 재밌는 공부를 했음

- '기술부채 청산의 날'을 정해야 겠음
