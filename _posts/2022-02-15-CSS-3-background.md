---
layout: post
title: CSS 3 background
---

---

<br><br>

## 12th background

<br>

background img 넣을때 div를 따로 생성해서 넣기보다<br>
body에 바로 넣으면 깔끔할 것 같다<br>

- background-image: url("") 태그<br>
- background-repeat: no-repeat; 패턴이 자동으로 반복될때 해재><br>
- background-position : 백그라운드 이미지를 가운데로 정렬<br>
- background-attachment : 스크롤이 생겨도 백그라운드 이미지는 고정<br>
- background-size: <br>
  cover; no반복 브라우저 전체를 덮음<br>
  contain; 너비 높이가 내용 안쪽에 알맞은 방식으로 가장 크게조절<br>
  initial; 기본값으로 초기화<br>
  %; 부모 요소에 비례한 %값으로 지정(width, height)<br>
  auto; 원래 이미지의 width, height 값으로 표시<br>
  <br><br>
- backround 세부속성 따로 공부해보기<br>
- url : Uniform Resouce Locator (균일한 자원 위치)<br>
- contain : 포함하다<br>
- initial : 초기의<br>
- attachment : 부착, 부착물<br>

<br>

```css
body {
  color: rgb(168, 165, 165);
  font-size: 25px;
  background-image: url("../background.png");
  background-repeat: no-repeat;
  background-size: contain;
  background-position: cover;
  background-attachment: fixed;
}
```

<br>

```css
.content {
  width: 200px;
  height: 500px;
  background-image: url("../background2.jpg");
  background-repeat: no-repeat;
  background-size: cover;
  background-position: center;
}
```

<br>
