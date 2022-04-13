---
layout: post
title: JS 22 arguments
---

<br><br>

## Arguments

demo26.html

<br>

함수에는 arguments라는 변수에 담긴

숨겨진 유사 배열이 있음

이 배열에는 함수를 호출할 때 입력한 인자가 담겨있음

<br>

- 그 전에 parameter / argument 엄격하게 구분하자면

  - DevJ님이 알려주신것과 완벽하게 같음 <br><br>

  ```javascript
  func a(arg1) {

  }

  a(1)
  //1 = argument
  //arg1 = parameter
  ```

<br>

```javascript
function sum() {
  var i,
    _sum = 0;
  for (i = 0; i < arguments.length; i++) {
    //arguments : JS에 약속된 특수한 변수명
    //arguments라는 유사배열이 담겨있음
    //사용자가 전달한 arguments가 들어가 있음 여기서는 1,2,3,4

    document.write(i + " : " + arguments[i] + "<br />");
    _sum += arguments[i];
    // += :
    // a=0;
    // a+=1; a=a+1;
  }
  return _sum;
}
document.write("result : " + sum(1, 2, 3, 4));
// :10
// 1+2=3 +3=6 +4=10

//JS는 parameter에 들어가는 arguments의 수를 마음대로 지정해도 됨

//arguments는 .length를 통해서 인자의 개수를 확인할 수 있게하고
//arguments[i] index를 통해서 특정 자리수의 값도 확인할 수 있음
```

<br><br>

매개변수의 수

- .length
- 함수이름.length

<br>

```javascript
function zero() {
  console.log("zero.length", zero.length, "arguments", arguments.length);
}
function one(arg1) {
  console.log("one.length", one.length, "arguments", arguments.length);
}
function two(arg1, arg2) {
  console.log("two.length", two.length, "arguments", arguments.length);
}
zero();
// zero.length 0 arguments 0
one("val1", "val2");
// one.length 1 arguments 2
two("val1");
// two.length 2 arguments 1
```

```javascript
function one(arg1) {
  console.log(
    "one.length",
    one.length,
    // 1
    //parameter의 개수

    "arguments",
    arguments.length
    // 2
    // parameter말고 실제 들어간 arguments 개수
  );
}

one("val1", "val2");
// one.length 1 arguments 2
```
