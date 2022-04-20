---
layout: post
title: JS 29 prototype
---

<br><br>

## Prototype

demo32.html

<br>

Inheritance의 구체적 수단인 prototype

prototype?<br>
한국어로는 '원형' 말그대로 object의 원형이라고 할 수 있음<br>
function은 object임 <br>
그러므로 constructor로 사용 될 function도 object<br>
object는 property를 가질 수 있는데 <br>
prototype이라는 property는 그 용도가 약속되어 있는<br>
특수한 property임<br>

prototype에 저장된 속성들은 <br>
constructor를 통해 object가 만들어 질 때<br>
그 object에 연결됨

```javascript
function Ultra() {}
Ultra.prototype.ultraProp = true;

function Super() {}
Super.prototype = new Ultra();

function Sub() {}
Sub.prototype = new Super();

var o = new Sub();
console.log(o.ultraProp);
//: true

//Sub constructor로 생성된 object o는
//Sub의 부모인 Super,Super의 부모인 Ultra의
//protperty인 .ultraprop을 inheritance함
```

object literal을 통해서 object를 만들 수도 있지만<br>
constructor를 통해 생성하면 부모를 inheritance할 수 있고<br>
inheritance한 property는 prototype을 통해 불러올 수 있음

<br><br>

### Prototype chain

<br>

prototype chain?<br>
object와 object를 연결하는 chain역할

```javascript
function Ultra() {}
Ultra.prototype.ultraProp = true;

function Super() {}
var t = new Ultra();
//t.ultraProp = 4;
Super.prototype = t;
//Super.prototype = new Ultra();

function Sub() {}
var s = new Super();
//s.ultraProp = 3;
Sub.prototype = s;
//Sub.prototype = new Super();
//Sub.prototype.ultraProp = 2;

var o = new Sub();
//o.ultraProp = 1;

console.log(o.ultraProp);
//: 1
//: 2
//: 3
//: 4
//: true
```

constructor Sub를 통해 만들어진 object o가<br>
Ultra의 property ultraProp에 접근 가능한 것은<br>
prototype chain으로 Sub와 Ultra가 연결되어 있기 때문임<br>

- 내부동작 순서
  1. object o에서 ultraProp를 찾는다
  2. 없다면 Sub.protoype.ultraProp를 찾는다
  3. 없다면 Super.prototype.ultraProp를 찾는다
  4. 없다면 Ultra.prototype.ultraProp를 찾는다

<br>

<br>

plus

```javascript
function Super() {}
Super.prototype = new Ultra();

function Sub() {}
Sub.prototype = new Super();
//Super.protoype = new Super();
//이렇게 코드를 작성하는 오류가 종종 생기는데
//실행은 똑같이 되기때문에 문제가 없어보이지만

//자식객체에대한 수정이 이루어졌을때
//수정내용이 부모객체에도 반영이 되기 때문에
//심각한 문제를 초래할 수 있음
```
