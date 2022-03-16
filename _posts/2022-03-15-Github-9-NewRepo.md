---
layout: post
title: Github 9 NewRepo
---

<br><br>

## New repository

<br>

Toy project로 Calculator를 코딩해 보는중인데

코딩중인 계산기를 github에 추가하고 배포가 가능한지 찾아봄

github에 Pages라는 기능으로 Repository에 올려둔 내용을

배포할 수 있다는 것을 알아냄

<br><br>

### Repository 연결

<br>

- local에서 코딩중인 파일을 github에 upload하기(push)

  - New repository 만들기(remote저장소: origin-편의상 명칭)

  - local 저장소 원하는 장소에 폴더를 만들고<br>
    해당폴더에 터미널로 접근한 후<br>
    git init으로 저장소 초기화(.git 폴더 생성됨)

  - ```bash
    remote 저장소 주소복사하고
    git remote add 주소
    (git remote, remote -v로 연결 점검)
    ```

  - ```bash
      git config user.name 이름<br>
      git config user.email 메일 입력
      (git config --list로 확인)

    ```

  - ```bash
    git add .
    git commit -m"메세지"
    git push origin main lacal파일을 remote저장소로 push해줌
    (git branch -m master main: main으로 branch명 변경)
    ```

  - readme.md파일을 repository 생성중 만들었기 때문에
    - git pull로 readme파일을 먼저 가져오고 나서 push 했음

<br><br>

### 배포

<br>

local과 remote저장소를 연결시킨 후 repository에 들어가서

- setting > pages > source 부분을<br>
  branch: main, /(root) 로 설정하고 save<br>
  적용하면 다른 이상이 없는이상 5-20min후에 배포적용됨

  - 5-20분: 서버문제상 배포에 시간이 항상 오래 걸리기때문에<br>
    기다려줘야 함(성급하게 바꾸면 어떤 설정이 맞는지 알 수 없음)
  - 다른 설정이 정상인데 배포가 안된다면<br>
    실행파일 이름을 index.html로 바꿔보길 추천함

<br><br>

적용에 성공함

저장소 연결부터, 배포적용까지 시간이 많이 걸렸지만

어떤 문제에 맞닥뜨렸을 때 스스로 문제를 해결할 수 있는

능력이 생겼다는 것을 체험할 수 있어서 좋은 공부/증명이 되었음
