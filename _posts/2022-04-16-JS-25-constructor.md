---
layout: post
title: JS 25 constructor
---

<br><br>

JS는 Prototype-based programming 카테고리에 속해있음

전통적인 함수형 언어+객체지향

기존의 객체지향언어에 익숙한 개발자는 혼란스러울 수 있음

이런 특징은 JS를 어중간한 언어로 보이게 할 수 있겟지만

이런면이 지금 가장 대중적인 언어로 JS를 꼽는 이유라고 생각함

- Prototype-based programming<br>
  prototype(원형) 기반 언어<br>
  JS의 모든 객체는 부모역할의 객체와 연결되어있음<br>
  객체 지향의 상속개념과 같이 부모객체의 property나<br>
  method를 상속받아 사용할 수 있음<br>
  이런 부모객체 = Prototype

<br>

- constructor<br>
  con(함께) + struct(쌓다) + or(사람)<br>
  건설업자, programming에서 생성자

- property<br>
  proper(자신, 적절한,알맞게) + ty(명사)<br>
  고유한 특성, 소유물, 재산

- method<br>
  meta(추구,탐구) + hodos(길) [greek]<br>
  방법, 방식, 순서, 질서

<br><br>

## Constructor & New

demo28.html

<br>

### 객체 생성

<br>

{ } : 중괄호로 object 생성

- 객체 리터럴 / object literal ?

  ```javascript
  const variablename = { key1: value1, key2: value2 };
  ```

```javascript
const person = {};
//객체를 생성하고

person.name = "dotoli";
//name이라는 property에 "egoing"을 담음

person.introduce = function () {
  return "My name is " + this.name;
};
//introduve라는 property에 함수를 담음
//함수를 담으면 method

document.write(person.introduce());
// : My name is dotoli

//실행했을 때 this는
//this가 속한 함수, 그 함수가 속한 객체 = person
//this.name = person.name = "dotoli"
```

객체를 만드는 과정이 분산되어있음<br>
코드의 집중도를 올리려면

```javascript
const person = {
  name: "dotoli",

  introduce: function () {
    return "My name is " + this.name;
  },
};

document.write(person.introduce());
// : My name is dotoli
```

여러 사람에 대한 정보를 담으려면?

```javascript
const person1 = {
  name: "dotoli",
  introduce: function () {
    return "My name is " + this.name;
  },
};

const person2 = {
  name: "zzphoo",
  introduce: function () {
    return "My name is " + this.name;
  },
};

//name은 구체적인 data를 정의하는 것이기때문에
//중복이라고 하기 애매하지만
//introduce method가 중복
//introduce method를 수정하려면 방대한 반복작업이 필요함
```

code의 중복 = 유지보수 어려워짐<br>
programer로서 반드시 피해야 함

<br><br>

### Constructor 생성자

<br>

constructor?

'객체를 만드는 역할'을 하는 함수

JS에서 함수는 재사용 가능한 logic의 묶음뿐 아니라

객체를 만드는 창조자 이기도 함

```javascript
function Person() {}

const p = new Person();
//new : 객체 생성자

p.name = "dotoli";
p.introduce = function () {
  return "My name is " + this.name;
};

document.write(p.introduce());
// : My name is dotoli
```

- 중요 : 함수에 new를 붙이면 return값이 객체가 됨

<br>

여러사람에 대한 정보를

새로배운 생성자로 담아보면?

```javascript
function Person() {}
var p1 = new Person();
p1.name = "dotoli";
p1.introduce = function () {
  return "My name is " + this.name;
};

document.write(p1.introduce() + "<br />");

var p2 = new Person();
p2.name = "zzphoo";
p2.introduce = function () {
  return "My name is " + this.name;
};

document.write(p2.introduce());

//생성자로 만들었지만 개선된 점이 없음
```

```javascript
function Person(name) {
  this.name = name;
  this.introduce = function () {
    return "My name is " + this.name;
  };
}
//함수를 먼저 정의하고

const p1 = new Person("dotoli");
const p2 = new Person("zzphoo");
// new를 붙여서 함수를 생성자로 사용

console.log(p1.introduce());
console.log(p2.introduce());
// : My name is dotoli
// : My name is zzphoo
// document.write issue concole.log사용

// introduce method가 중복되지 않음
```

<br>

객체에 대한 초기화

초기화?

어떤 property, method를 가질지

생성자 함수 안에 기술하는 것을 통해서

그 객체가 가지고 있는 정보 / 하는 일을 '세팅'하는 행위

- init<br>
  initialize : 초기화

<br>

### plus

<br>

생성자함주는 일반 함수와 구분하기 위해<br>
첫글자를 대문자로 표시할 것

<br>

JS 생성자의 특징?

일반적인 객체지향 언어에서 생성자는 class 소속이지만<br>
JS에서 객체를 만드는 주체는 함수임<br>
함수에 new를 붙여 객체를 만들 수 있다는 점은 <br>
JS에서 함수의 위상을 암시하는 단서이며<br>
JS가 추구하는 자유로움을 보여주는 사례

<br><br><br>

### references

- [mdn object literal](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Operators/Object_initializer)
