---
layout: post
title: JS 28 inheritance
---

<br><br>

## Inheritance

demo31.html

- in(make) + herit(상속) + ance(상태,성질,행위)

<br>

object는 연관된 logic들로 이루어진 작은 program<br>
inheritance는 object의 logic을 그대로 물려받는<br>
또 다른 object를 만들수 있는 기능을 의미함

단순히 물려받는 것은 복제이상의 의미가 없음<br>
기존의 logic을 수정하고 변경해서<br>
파생된 새로운 object를 만들 수 있게 해주는 것

<br>

### 사용방법

상속 자체를 해보기 위해서 이번 여기서는 복제만

```javascript
function Person(name) {
  this.name = name;
  this.introduce = function () {
    return "My name is " + this.name;
  };
}

const p1 = new Person("dotoli");
document.write(p1.introduce() + "<br />");
//: My name is dotoli
```

원래 썻던 코드를

```javascript
function Person(name) {
  this.name = name;
}
Person.prototype.name = null;
Person.prototype.introduce = function () {
  return "My name is " + this.name;
};
//prototype은 다음 강의

var p1 = new Person("dotoli");
document.write(p1.introduce() + "<br />");
```

상속준비를 위해 변경

```javascript
function Person(name) {
  this.name = name;
}
Person.prototype.name = null;
Person.prototype.introduce = function () {
  return "My name is " + this.name;
};

function Programmer(name) {
  this.name = name;
}
Programmer.prototype = new Person();

var p1 = new Programmer("dotoli");
document.write(p1.introduce() + "<br />");
//: My name is dotoli

//그런데, Programmer생성자에는
//introduce라는 method를 정의한 적이 없음
```

```javascript
Programmer.prototype = new Person();
//name과 introduce method를 가지고 있는 prototype,
//그 prototype을 가지고있는 Person
//따라서 Person을 통해 만든 Programmer도
//Person의 property와 method를 intheritance 함 ?
```

- 요약<br>
  Programmer라는 생성자를 만들고<br>
  이 생성자의 prototype과 Person의 객체를 연결했더니<br>
  Programmer객체로 method introduce를 사용할 수 있게 됨

<br>

### 기능의 추가

```javascript
Programmer.prototype.coding = function () {
  return "hello world";
};
```

```javascript
function Person(name) {
  this.name = name;
}
Person.prototype.name = null;
Person.prototype.introduce = function () {
  return "My name is " + this.name;
};
function Programmer(name) {
  this.name = name;
}
Programmer.prototype = new Person();
Programmer.prototype.coding = function () {
  return "hello world";
};
var p1 = new Programmer("dotoli");
document.write(p1.introduce() + "<br />");
document.write(p1.coding() + "<br />");
//: My name is dotoli
//  hello world
```

plus

```javascript
function Person(name) {
  this.name = name;
}
Person.prototype.name = null;
Person.prototype.introduce = function () {
  return "My name is " + this.name;
};
function Programmer(name) {
  this.name = name;
}
Programmer.prototype = new Person();
Programmer.prototype.coding = function () {
  return "hello world";
};
function Designer(name) {
  this.name = name;
}
Designer.prototype = new Person();
Designer.prototype.design = function () {
  return "beautiful world";
};
var p1 = new Programmer("dotoli");
document.write(p1.introduce() + "<br />");
document.write(p1.coding() + "<br />");
//: My name is dotoli
//  hello world
var p2 = new Designer("zzphoo");
document.write(p2.introduce() + "<br />");
document.write(p2.design() + "<br />");
//: My name is zzphoo
//  beautiful world
```

object Person (부모)

- (상속)
  - object Programmer
  - object Designer

수정

```javascript
Person.prototype.introduce = function () {
  return "My name is " + this.name;
};

//name을 nickname으로 수정하면
//부모 object를 상속받는 모든 자식 object의 결과가 변경
```

<br><br>

inheritance에서 가장 중요한 역할을 한 것은

.prtotype 임

JS는 Prototype-based language라는 언급을 했음

이 prototype에대해서 다음시간에 알아볼 예정
