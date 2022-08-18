---
layout: post
title: React team repo
---

<br><br>

## Sparta coding

<br><br>

### Innovation Camp

<br>

#### w1 day18

<br><br>

Javascript에서 유사배열과 배열의 차이
유사배열의 각 요소를 수정하고 싶을 때 거쳐야 하는 과정은?

- 배열은 변수 하나에 서로 관련있는 데이터를 할당해 관리하는 데이터타입
- 유사배열은 배열처럼 보이지만 key가 숫자이고 length를 가진 객체

- Array.from() method를 사용해 유사배열객체를 복사해
  새로운 배열객체를 만듦
- 유사배열에서 사용할 수 있는 call, apply, bind등을 사용

부모 component A, 자식 component B.
A는 state로 지닌 {name:"르탄이"}를 B에게 넘김.
B는 받아온 name을 화면에 뿌림.
A의 state가 {name:"진도사우르스"}로 바뀔 때 lifecycle은?

- 으.. 모르겠음
- props에서 받아온 값을 state에 동기화시켜 update될 때 호출
  componentDidUpdate ?

양방향 바인딩이란?
이를 사용할 때 rerendering은?
(부모A, 자식B)

- data binding : 화면의 객체와 data 일치 = JS data를 HTML과 일치
- user의 입력값이 코드상의 변수에 바로 바인딩 됨
- 단방향에서는 A는 B에거 props로 늘 data를 보내고
  event를 통해서만 B가 A에게 줄수있음
  2-way binding은 watacher라는 매개를 통해
  data가 수정될때 바로 rerendering

event listener는 등록되면 반드시 해제
class형 component에서 unmount 될 때 event listener를 해제 (componentWillUnmount)
함수형 component에서는 event listner를 어떻게 해제?

- event listener는 momory누수때문에 필요없어지면 반드시 해제
- 함수형은 lifecycle method사용불가, react hook으로 해제

react에서 DOM에 접근할 때 ref사용
document.getElementsByClassName등이아니라 ref를 쓰는 이유는?

- 실제DOM이 아니라 가상DOM을 사용하기 때문에
  getElementsByClassName등으로 접근불가

SPA방식과 MPA방식은 무엇?

- Single Page Application:한개의 page로 구성됨
  웹 application에 필요한 resource를 최초 한번에 다운로드
  : 필요한 부분만 갱신, 자연스러운 page이동, UX제공

- Multiple Page Application:여러개의 page로 구성
  새로운 page를 요청할 때 마다 resource 다운로드, 매번 전체가 rendering
  : 첫 로딩이 짧고 완성된 HTML을 전달받아 검색엔진이 크롤링하기 적합함

DIY section

- life cycle의 이해?

  - react의 life cycle을 이해하지 못하면.. react로 programing할 수 없음

- Code Convention 이 존재하는 이유 / 장점

  - 폴더, 파일, 변수, 함수등 naming할 일이 많음
    원하는대로 지어도 되지만 code convention을 지켜
    code의 일관성을 높이면
    협업을 할 때 가독성이 올라가 code의 의도나 오류를 파악하기 쉽고
    팀원 간의 code 충돌을 줄일 수 도 있음
    결론적으로 유지보수 비용을 줄일 수 있기 때문에
    사전회의를 통해 미리 스타일을 정하고 지켜주는것이 좋음

- react의 특징

  - 가상DOM, 단방향 binding

    - memory에 표시되는 DO과 동일한 가상DOM을 만들고 연산한 후
      실제 DOM을 갱신함으로써 연산을 최소화
    - 2 way binding은 동기화를 신경쓰지않고 program을 작성할 수 있지만
      수많은 watcher가 생성되어 성능저하가 발생할 수 있기 때문에 1way biding사용
