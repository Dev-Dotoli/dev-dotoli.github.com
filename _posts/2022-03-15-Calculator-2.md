---
layout: post
title: Calculator 2
---

<br><br>

## Toy Project

220314-Cal/index.html

<br><br>

### CSS Grid

<br>
Grid로 button의 배치를 해볼예정인데 gird가 처음이라 먼저 공부해 볼 것

![grid](https://studiomeal.com/wp-content/uploads/2020/01/03-2.jpg)

- grid **Container** <br>
  display: grid를 적용하는 grid의 전체 영역<br>
  grid container안의 요소들이 grid 규칙의 영향을 받아 정렬됨<br>

<br>

- grid **Item**<br>
  grid container의 자식 요소들<br>
  grid규칙에 의해 배치됨<br>

<br>

- grid **Track**<br>
  grid의 row, column<br>

  ```css
  grid-template-(rows,columns): (크기);
  /*
  grid track의 크기를 설정
  
  여러가지 단위를 쓸 수 있고 섞어서 사용할 수도 있음
  
  px pixel: 고정값으로 지정
  fr fraction: 파편화 비율, 상대값으로 지정
  */
  ```

<br>

- grid **Cell**<br>
  grid의 한 칸<br>
  item이 들어가는 가상의 틀(칸)<br>

- grid **Line**<br>
  grid cell을 구분하는 선<br>

- grid **Number**<br>
  grid line의 각 번호<br>
  line 사이가 한 cell이 됨<br>

  ```css
  grid-column: 1/4;
  /*column 1번line부터 4번line 까지 차지해라*/
  ```

  ```css
  grid-column-start
  grid-column-end

  grid-column
  /*start,end 속성을 한번에 쓰는 축약형*/


  grid-row-start
  grid-row-end

  grid-row
  ```

  ![gridcell](https://studiomeal.com/wp-content/uploads/2020/01/07-2.jpg)
  start num, end num으로 cell의 영역을 지정해줌<br>
  그림속 빨간 영역으로 코드로 지정하면 아래와 같고<br>
  아래의 두 코드는 같은 영역을 지정함

  ```css
  .item:nth-child(1) {
    grid-column-start: 1;
    grid-column-end: 3;
    grid-row-start: 1;
    grid-row-end: 2;
  }
  ```

  ```css
  .item:nth-child(1) {
    grid-column: 1/3;
    grid-row: 1/2;
  }
  ```

  <br>

- grid **Gap**<br>
  grid cell 사이의 간격<br>

  ```css
  row-gap: px;
  colums-gap: px;

  gap: 20px;
  /* row와 column모두 20px */
  gap: 10px 20px;
  /* gap을 각각 row 10px, column 20px */

  grid-gap: 20px;
  gap: 20px;
  /*버전에 따라 grid-gap 으로 사용하기도 하기때문에
  둘다 지정해서 호환범위를 넓힐 수 있음*/
  ```

<br>

- grid **Area**<br>
  grid line으로 둘러싸인 사각형 cell의 집합<br>

  영역이름으로 grid 정의 할 수 있음<br>

  ```css
  grid-template-areas
  /*Grid Area에 이름을 붙이고
    그 이름을 이용해서 배치하는 방법
  */
  ```

  ![grid area](https://studiomeal.com/wp-content/uploads/2020/01/08-2.jpg)

  ```css
  .container {
    grid-template-area:
      "header header header"
      "   a    main     b  "
      "   .      .      .  "
      "footer footer footer";
  }
  ```

  시멘틱 태그?
  위의 형태로 차지하는 셀의 개수만큼 해당 위치에 이름을 써줌<br>
  각 셀마다 공백을 하나씩 넣어서 구분<br>
  header는 첫번째 row에서 3개의 column을 차지해서 3번 씀<br>
  빈칸은 마침표, "none" 으로 표시하고 여러개 써도 됨<br>

  ```css
  .header {
    grid-area: header;
  }
  .sidebar-a {
    grid: a;
  }
  .main-content {
    grid-area: main;
  }
  .sidebar-b {
    grid-area: b;
  }
  .footer {
    grid-area: footer;
  }
  /*이름 값에 따옴표 없음*/
  ```

  매칭할 때는 위와같이<br>
  해당 item 요소에 grid-area 속성으로 이름을 지정

  <br><br>

Calculator CSS에 적용한 Grid

```css
CSS에서 class를 부여한 곳은 "." 을 붙여서 선택해줘야 함
.button
.ac
.zero
까먹지마
```

<br>

```css
.button {
  display: grid;
  /* 버튼에 grid 적용*/

  grid-template-columns: repeat(4, 1fr);
  /*한 colums에 4개를 넣는데, 각 1비율로 넣어라
  = grid-template-columns: 1fr 1fr 1fr 1fr;

  fr: fraction(파편,분수)
  template-columns: grid 형태 정의 
  row 행, columns 열
  */
}

.ac {
  grid-column: 1/4;
  /*첫 번째 line부터 4번째 line까지 지정
  grid에서 ac버튼은 1-4번(3칸)까지 차지함(1-5까지 line중에)
  */
}

.zero {
  grid-column: 1/3;
  /*
  gird
  첫 번째 line부터 3번째 line까지 지정
  grid에서 zero버튼은 1-3번(2칸)까지 차지함(1-5까지 line중에)
  */
}
```

<br><br>

### css button - pseudo selector로 패턴 색 넣기

<br>

pseudo selector: 가상(거짓) 선택자

- pseudo: 거짓, 가짜 고대 그리스어에서 파생 ψ(psi)

selector는 문서에 존재하는 class, id등을 지정하는데
pseudo selector는 실제로 존재하지 않는 '어떠한 상태' 자체를 지정함
여러가지가 있지만 그 중에서 nth(n번째) pseudo selector

```css
$:nth-child(odd)
$:nth-child(2n+1) /*HTML표 홀수번째 행*/

$:nth-child(even)
$:nth-child(2n)   /*HTML표 짝수번째 행*/

$:nth-child(7)    /*임의의 7번째 요소*/

$:nth-child(5n)   /*5[=5x1], 10[=5x2]...번째 요소*/

$:nth-child(n+7)  /*7번째와 이후의 모든요소 7[=0+7], 8[=1+7], 9...*/

$:nth-child(3n+4) /*4[=(3x0)+4], 7[=(3x1)+4], 10, 13...번째 요소*/
/* 4번째칸 부터 각 3칸씩 에 해당하는 요소*/

$:nth-child(-n+3) /*앞에서 3개의 요소
                    3[=(-0)+3], 2[=(-1)+3], 1[=(-2)+3] */
/* 0, -n 번째는 존재할 수 없으므로 */

p:nth-child(n)    /*형제 그룹 내의 모든 <p> 요소*/
/* 단순한 p 선택자와 동일하지만 더 높은 명시도를 가짐*/

p:nth-child(1), p:nth-child(0n+1)
/* 형제 그룹 내의 모든 첫 번째 <p>요소
   :fist-child 선택자와 동일하며 같은 명시도를 가짐 */

P:nth-child(n+8):nth-child(-n+15)
/* 형제 그룹 내에서 8번째 부터 15번째 까지의 <p> 요소*/
```

적용한 css

```css
button:nth-child(4n + 2),
/* 2[=(4x0)+2, 6[=(4x1)+2], 8[=(4x2)+2]
2번째 칸부터 각 4번째칸에 해당하는 요소*/
button:last-child {
  background-color: rgb(231, 77, 136);
  /*위에 지정한 요소중 마지막 자식요소에 지정색을 넣어라*/
}
```

<br><br>

### Refernces

[이번에야말로 CSS Grid를 익혀보자 - 1분코딩](https://studiomeal.com/archives/533)
<https://developer.mozilla.org/ko/docs/Web/CSS/:nth-child>
