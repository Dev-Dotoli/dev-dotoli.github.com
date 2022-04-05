---
layout: post
title: JS 17 regular expression
---

<br><br>

## Regular Expression

<br><br>

JS > regular expression

- JS안에서 정규표현식을 어떻게 사용하는지 배움<br>
  하지만 정규표현식자체는 많은 언어들에서 사용하는 개념<br>
  정규표현식 패턴을 반드시 따로 공부해야 함<br>

<br><br>

### Regular expression 생성

<br>

regular expression 단계

<br>

- compile (컴파일)<br>
  검출하고자 하는 패턴을 찾거나 만드는 일

  - regular expression 리터럴

    ```javascript
    var pattern = /a/;
    ```

    ```javascript
    var pattern = new RegExp("a");
    ```

    찾고자 하는 정보(a)를 pattern이라고하는 변수에 저장

<br>

- execution (실행)<br>
  찾은 패턴에 대해 어떠한 작업을 구체적으로 하는 것

  ```
  정규표현식으로 할 수 있는 것

  필요한 정보를 추출,<br>
  확인하고자하는 정보가 있는지 test,<br>
  검색된 정보를 다른정보로 치환<br>
  ```

  RegExp.exec();

  ```javascript
  var pattern = /a/;
  //문자열 a를 찾고 싶다

  객체.메서드("정보");
  pattern.exec("abcde");
  ["a"];

  var pattern = /a./;
  // . = 어떤 문자건 간에 하나의 문자
  pattern.exec("abcde");
  ["ab"];
  ```

  ```javascript
  var pattern = /a/;

  pattern.exec("bcde");
  //null
  //찾는 a가 없기때문에 null이 return됨
  ```

  <br>

  RegExp.test();

  ```javascript
  var pattern = /a/;

  pattern.test("abcde");
  //true
  ```

  ```javascript
  var pattern = /a/;

  pattern.test("bcde");
  //false
  ```

  <br>

  문자열 메서드 실행

  <br>

  string.match();

  ```javascript
  var pattern = /a/;

  var str = "abcdef";

  str.match(pattern);
  ["a"];
  ```

  ```javascript
  var pattern = /a/;

  var str = "bcdef";

  str.match(pattern);
  //null
  ```

  string.replace();

  ```javascript
  var pattern = /a/;

  var str = "abcdef";

  str.replace(pattern, "A");
  ("Abcdef");
  ```

  <br>

  Option

  - 정규 표현식을 만들 때 옵션을 설정할 수 있고<br>
    설정한 옵션에 따라 검출되는 데이터가 달라짐

  <br>

  i<br>
  i를 붙이면 대소문자 구별X

  ```javascript
  var xi = /a/;
  // xi = i옵션을 사용하지 않는다는 의미로 명명

  "Abced".match(xi);
  //null
  ```

  ```javascript
  var oi = /a/i;

  "Abced".match(oi);
  ["A"];
  ```

  g (global) <br>
  g를 붙이면 검색된 모든 결과를 return

  ```javascript
  var xg = /a/;

  "abceda".match(xg);
  ["a"];
  //중복된 a를 한번만 return함
  ```

  ```javascript
  var og = /a/g;

  "abceda".match(xg);
  ["a", "a"];
  //중복된 a 두개를 모두 return함
  ```

  plus

  ```javascript
  var ig = /a/gi;
  //해당되는 문자 a릐 대소문자 구분없이 '모든'문자를 찾겠다

  "AabcdAa".match(ig);
  ["A", "a", "A", "a"];
  //포함된 모든 a를 return
  ```

  <br>

  캡쳐 <br>

  - 그룹을 지정하고, <br>
    지정된 그룹을 가져와서 <br>
    사용하는 기능, 개념

  - 괄호(그룹)안의 패턴은 마치 변수처럼 재사용할 수 있다.

  <br>

  ```javascript
  var pattern = /(\w+)\s(\w+)/;

  var str = "coding everyday";

  var result = str.replace(pattern, "$2, $1");
  // pattern에 해당되는 문자를 인자 $2, $1로 치환해라
  // $2 = 패턴에서 등장하는 두번째 그룹

  // 문자열.치환해라(패턴안에, "그룹2 콤마 그룹1")

  console.log(result);
  // everyday, codidng
  ```

  ```javascript
  var pattern = /(\w+)\s(\w+)/;
  // ( ) = group
  // \w = string, 문자 (A~Z, a~z, 0~9)
  // + = 수량자, 앞에 있는 문자가 하나이상 이라는 뜻
  // /s = space, 공백

  // (\w+)\s(\w+) = 문자하나이상 공백 문자하나이상
  ```

  - [regexper시각화](https://regexper.com/) 개념
  - [regexper builder](https://regexr.com/) test

  <br>

  치환

  ```javascript
  var urlPattern = /\b(?:https?):\/\/[a-z0-9-+&@#\/%?=~_|!:,.;]*/gim;

  var content =
    "생활코딩 : http://opentutorials.org/course/1 입니다. 네이버 : http://naver.com 입니다. ";

  var result = content.replace(urlPattern, function (url) {
    return '<a href="' + url + '">' + url + "</a>";
  });
  ```

  ```javascript
  console.log(result);

  생활코딩 : <a href="http://opentutorials.org/course/1">http://opentutorials.org/course/1</a> 입니다. 네이버 : <a href="http://naver.com">http://naver.com</a> 입니다.

  ```
