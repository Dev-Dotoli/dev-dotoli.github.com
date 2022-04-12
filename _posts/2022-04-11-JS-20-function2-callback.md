---
layout: post
title: JS 19 funcrion2 callback
---

<br><br>

## Callback

demo23.html

<br>

콜백? <br>
어떠한 함수가 수신하는 인자값이 함수인 경우<br>

- 예시<br>
  내장메서드 sort가<br>
  사용자정의함수 sortfunc를 인자로 받음

<br><br>

### 처리의 위임

<br>

예제에서 sortfunc = 콜백(callback) 함수 <br>
이 콜백함수를 인자값으로 받아서 <br>

built in method인 sort가 처리되는 방식을 바꿈

<br>

```javascript
function sortNumber(a, b) {}

var numbers = [20, 10, 9, 8, 7, 6, 5, 4, 3, 2, 1];

console.log(numbers.sort());
// : [1, 10, 2, 20, 3, 4, 5, 6, 7, 8, 9]
// 숫자가 크기가 아니라 문자로 비교한 듯?

// '.'앞은 '객체'
// 여기서는 numbers라고하는 배열형태의 객체
// sort라는 함수가 시스템상 정의되어 있는데
// 객체에 속해있는 함수(sort)이기 때문에 method 임

//이렇게 시스템에 미리 정의 되어있는 것을
//내장객체, 내장메소드 라고 부름
//built in object, built in method

//우리가 그때 그때 정의하는 객체, 메서드는
//사용자 정의 객체, 사용자 정의 메서드 라고 부름
```

<br>

```javascript
const numbers = [20, 10, 9, 8, 7, 6, 5, 4, 3, 2, 1];

const sortfunc = function (a, b) {
  //  console.log(a, b);
  if (a > b) {
    return 1;
  } else if (a < b) {
    return -1;
  } else {
    return 0;
  }
};
// sortfunc = 인자1 인자2 를 비교하는 값을 전달
// return값이 양수인지 음수인지 0인지 비교해서 정렬
// 어려움ㄷ

console.log(numbers.sort(sortfunc));
// [1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 20]

// sortfunc로 sort가 동작하는 방법을 정의
```

<br>

```javascript
const numbers = [20, 10, 9, 8, 7, 6, 5, 4, 3, 2, 1];
const sortfunc = function (a, b) {
  return a - b;
};
// if문으로 설정했던 기준을 최소화

// 역순 : return b - a;

console.log(numbers.sort(sortfunc));
// : [1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 20]
```

이것이 콜백의 정의<br>
이런 기능이 가능한 이유는<br>

JS의 function이 '값'이기때문

<br><br>

### 비동기 처리 (참고만)

<br>

웹서비스에 10000명의 구독자가있고<br>
웹에 글을 작성하면 구독자에게 메일을 보냄<br>
한명에 1초만걸려도 10000초 = 2시간이상<br>

- 동기적처리(순서대로실행)<br>
  글작성 - 메일발송 - 작성완료 = 3시간<br>

- 비동기적처리<br>
  글작성 - 메일발송예약 - 작성완료 = 짧은시간
  내부적으로 사용자에게는 보이지않는 프로그램이 <br>
  메일발송예약이 있을 때 발송시키는 작업을<br>
  3시간동안 백그라운드에서 혼자서 진행<br>

  - 비동기처리의 예시<br>
    JS의 Ajax

    - asynchronous 비동기<br>
      javascript<br>
      and<br>
      XML<br>

      웹페이지가 계속 로드 될 필요 없이<br>
      서버에서 필요한 정보만 받아와서 사용,출력하는 기능?

<br>

Jquery library를 이용하면 조금 쉽게 구현할 수 있음

```json
{ "title": "JavaScript", "author": "egoing" }
//json이라는 형태의 데이터
//json은 JS에 객체를 만드는 방법
```

```html
<!DOCTYPE html>
<html>
  <head>
    <script src="//code.jquery.com/jquery-1.11.0.min.js"></script>
    <!--jquery를 includ-->
  </head>
  <body>
    <script type="text/javascript">
      $.get(
        "./datasource.json.js",
        function (result) {
          console.log(result);
        },
        "json"
      );
      <!-- Ajax기능흘 하고록하는 객체$.메서드get
      인자1 : url, 인자2 : 함수 result 호출-->
    </script>
  </body>
</html>
```

<br><br>

### ect

<br>

매개변수 확인

sort 동작방식 참고

- [JS 사전 sort](https://opentutorials.org/course/50/109)
