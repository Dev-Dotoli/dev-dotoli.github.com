---
layout: post
title: JS 15 module,library
---

<br><br>

## Module

demo20.html

<br>

program은 작고 단순한 것에서 크고 복잡한 것으로 진화함

그 과정에서 code의 재활용성을 높이고 유지/보수를 쉽게 할 수 있는

다양한 기법이 사용됨

그 중 하나가 code를 여러개의 file로 분리하는 것 (module화)

- 자주 사용되는 code를 별도의 file로 만들어서 필요할 때 마다 재활용
- code를 개선하면 이를 사용하는 모든 application의 동작이 개선
- code 수정 시에 필요한 logic을 빠르게 찾을 수 있음
- 필요한 logic만을 load해서 memory의 낭비를 줄일 수 있음
- 한번 download 된 module은 web browser에 저장됨
  동일한 logic을 load 할 때 시간과 network traffic을 절약

<br>

순수한 Javascript에서는 module이라는 개념이 분명하게 존재하진 않음

but JS가 구동되는 host환경에 따라 서로 다른 module화 방법이 제공됨

<br>

- host환경<br>
  : JS가 구동되는 환경<br>
  JS는 browser를 위한 언어로 시작, but browser만을 위한 언어X<br>
  node.js는 server측에서 실행되는 JS임 <br>
  JS의 문법을 따르지만 구동되는 환경은 browser가 아니라 server<br>
  Google Apps Script역시 JS이지만 google제품에서 동작<br>

<br><br>

### web browser logic module화

<br>
예제
```html
<!DOCTYPE html>
<head>
    <title>main</title>
</head>
<body>
    <script>
    function welcome() {
            return "hello world";
    }
    alert(welcome());
    </script>
</body>
</html>
```
<br>

예제의 welcome function을 module화

```html
<!DOCTYPE html>
<head>
    <title>main</title>
    <script src="greeting.js"> </script>
</head>
<body>
    <script>
        alert(welcome());
    </script>
</body>
</html>
```

```javascript
// greeting.js

function welcome() {
  return "hello world";
}
```

<br>

HTML과 JS는 완전히 다른 문법을 가짐<br>
근데 HTML문서안에 JS도 동시에 표기<br>
이 때 browser에게 JS, HTML을 구분해서 알려주는 script태그

```html
<script src="~.js"></script>
```

html문서 안에 없어도 src JS파일에 정의되어있기 때문에<br>
welcome함수가 실행됨

<br><br>

### Library

<br>
library는 module과 비슷한 개념

module이 program을 구성하는 작은 부품 logic이라면

library는 자주 사용되는 logic을

재사용하기 편리하게 잘 정리한 code들의 집합

- 훌륭한 library가 많음 <br>
  좋은 library를 선택하고 잘 사용하는 것 은 programming의 핵심

<br>

```html
<!DOCTYPE html>
<head>
    <script type="text/javascript" src="jquery.js"></script>
</head>
<body>
    <ul id="list">
        <li>empty</li>
        <li>empty</li>
        <li>empty</li>
        <li>empty</li>
    </ul>
    <input type="button" value="execute" id="execute_btn"/>
    <script type="text/javascript">
        $('#execute_btn').click(function(){
            $('#list li').text('coding');
        });
    </script>
</body>
</html>
<!--

jquery삽입, network탭에서 삽입여부 확인가능

jquery는 $로 문법사용

# name1 name2 : id값이 name1인 태그의 하위태그가 name2인 태그를 선택

.text(~) : 선택자를 ()안 ~ text로 변경

.click(~) : 선택자를 click했을때 (~)실행

-->
```

<br>

jquery없이 JS만으로 위의 code를 구현하면

몹시 복잡한 code를 짜야함

```javascript
function addEvent(target, eventType, eventHandler, useCapture) {
  if (target.addEventListener) {
    // W3C DOM
    target.addEventListener(
      eventType,
      eventHandler,
      useCapture ? useCapture : false
    );
  } else if (target.attachEvent) {
    // IE DOM
    var r = target.attachEvent("on" + eventType, eventHandler);
  }
}
function clickHandler(event) {
  var nav = document.getElementById("list");
  for (var i = 0; i < nav.childNodes.length; i++) {
    var child = nav.childNodes[i];
    if (child.nodeType == 3) continue;
    child.innerText = "Coding everybody";
  }
}
addEvent(document.getElementById("execute_btn"), "click", clickHandler);
```

이 코드조차도 완벽하지않고 잠재적인 문제를 가지고 있음

= library는 몹시 중요
