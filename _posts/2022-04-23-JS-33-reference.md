---
layout: post
title: JS 33
---

<br><br>

## Reference

demo36.html

<br><br>

### Copy

<br>

전자화된 시스템의 가장 중요한 특징은 복제

현실의 사물과 다르게 전자화된 시스템 위의 데이터를

복제하는데는 비용이 거의 들지 않음

프로그래밍에서 복제란?

```javascript
var a = 1;
var b = a; //copy
b = 2;

console.log(a);
//: 1

//a에 담겨있는 값을 copy해서
//b가 가지고 있게 해서 같은 값이었지만
//b를 2로 바꾸더라도 a에는 영향을 주지않음
```

![ref1](https://ifh.cc/g/DRda2d.png)

<br><br>

### Reference

<br>

자연의 산물이 아닌 거대한 약속의 집합인

소프트웨어의 세계에서 당연한 것은 없음

```javascript
var a = { id: 1 };
var b = a; //reference
b.id = 2;

console.log(a.id);
//: 2

//b에 담겨있는 object의 property값을 변경하면
//a에 담긴 property의 값도 변경된다?
```

![ref2](https://ifh.cc/g/bnAl5o.png)

<br><br>

두 구문의 차이

```javascript
a = 1;
```

```javascript
a = { id: 1 };
```

primitive data로 이루어진 값은 copy함

object로 이루어진 data값은 <br>
새로만들어진 변수도 똑같이 참조함

때문에 b의 id값을 바꾸면 a값도 바뀌게 됨

- 담겨있는 값이
  - primitive data면 : copy한 실제 data가 변수에 담기고
  - object면 : object에 대한 reference가 들어감

<br>

```javascript
var a = { id: 1 };
var b = a;
/* b.id = 2; */

b = { id: 2 };
//객체를 새로 생성해서 b에 할당
//이 순간 객체b는 더이상 a를 참조하지 않음

console.log(a.id);
//: 1
```

<br>

- Reference?

  symbolic link와 같은 개념 <br>
  원본파일에 대한 symbolic link를 만들면 원본이 수정될 때<br>
  symbolic link에도 그 내용이 실시간으로 반영 됨<br>

  symbolic link를 통해 만든 파일은 <br>
  원본 파일에 대한 주소 값이 담겨 있기 때문에 <br>
  symbolic link에 접근하는 경우 담겨있는 원본의 주소를<br>
  reference해 원본에 대한 작업을 하게 되는 것<br>

  이렇게 함으로써 저장 장치의 용량을 절약할 수 있고<br>
  원본 파일을 사용하는 모든 복제본이<br>
  동일한 내용을 유지할 수 있음

  reference는 전자화된 세계의 극치

<br><br>

### Function

<br>

method의 parameter는 어떻게 동작할까

<br>

primitive data

```javascript
var a = 1;
function func(b) {
  b = 2;
}
//parameter b의 값을 2

func(a);
//a를 b로 전달 : b = a

console.log(a);
//: 1

// a = 1
// b = 2
// b = a 이순간 a에 담긴 값을 b에 copy(함수안에서 b = 2, a에 영향을 주지 않음)
// 결과는 : 1
```

object

```javascript
var a = { id: 1 };
function func(b) {
  b = { id: 2 };
}

func(a);

console.log(a.id);
//: 1

// a = { id : 1 };
// b = { id : 2 }; 이순간 b에 새로운 object를 담아서 link 끊김
// b = a ;
// 결과는 a에 담긴 그대로 : 1
```

plus

```javascript
var a = { id: 1 };
function func(b) {
  b.id = 2;
}

func(a);

console.log(a.id);
//: 2

// a = { id : 1 };
// b = a ; data가 object라서 reference 함
// b.id = 2 reference상태에서 값을 변경하면 원본의 값도 변경
// 결과는 : 2
```

<br><br>

다시한번 기억 해 둘 것

number, string, boolean 등은 객체처럼 사용할 수 있지만<br>
실제로는 primitive data이며,<br>
이를 객체처럼 사용할 수 있는 것은<br>
wrapper 객체로 감싸는 과정이 있기때문이란는 것

이 사실을 기억해둬야 오늘배운 내용이 논리적으로 무너지지 않음

<br>

전제들을 파악해 논리적으로 생각하면 쉽게 알 수 있는 내용이지만

단순히 현상들만 기억하려고 한다면 외워야 할 것들이 많아짐

<br>

- [Code & open Source](https://opentutorials.org/course/1189/6340)
