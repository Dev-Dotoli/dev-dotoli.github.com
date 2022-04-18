---
layout: post
title: JS 26 Global object
---

<br><br>

## Global object

demo29.html

<br>

Global object(전역객체)는 특수한 객체

모든 객체는 Global object의 property임

```javascript
function func() {
  alert("sup?");
}

func();
// : sup?

window.func();
// : sup?

// 둘다 실행되며 같은 동작을함
```

func =<br>
window라는 global object의 사용자 정의 함수 method 라는 것

<br>

```javascript
var o = {
  func: function () {
    alert("sup?");
  },
};

o.func();
// : sup?

window.o.func();
// : sup?

// 객체 o 역시 global object의 property
```

모든 global variable, function은

객체를 따로 명시하지 않으면 암시적으로

window객체(global object)의 property

- host환경에 따라 다름<br>
  JS : window<br>
  node.js : global

<br><br>

### references

- [Global obect API](https://opentutorials.org/course/50/44)
