---
layout: post
title: Github 1 rule
---

---

## git commit

<br><br>

## Git commit rule

<br>
commit : 프로젝트에 변화가 생겼을때 시점과 변경점을 메시지와 함께 기록해두는 기능. (기록하다, 기억하다)<br>
커밋은 개발자마다 다를 수 밖에 없지만 코드를 잘개 쪼개어 자주 커밋해두면 여러가지 장점이 있음. 한번에 여러가지 수정사항을 기재하면 협업시 동료가 확인하기 어려울 수 있음. 특정 역할이나 수정사항에 대해서만 커밋을 남기면 협업시 코드리뷰가 용이하고 특정 부분만 언급하기 쉬움  
<br><br>

### 커밋의 종류

- fix : 버그 수정(오타수정:fix typo) / ex) fix a in b , fix a to b
- docs : 문서 수정
- style : 코드 스타일 변경(코드 포매팅, 세미콜론 누락 등)
- rename : 파일, 폴더명 수정
- remove : 파일 삭제
- feat : 새로운 기능 추가
- design : 사용자 UI 디자인 변경(CSS 등)
- test : 테스트 코드
- refactor : 리팩토링(Production code)
- build : 빌드 파일 수정
- ci : CI설정 파일 수정
- Perf : 성능 개선
- chore : 자잘한 빌드 업무 수정, 패키지 매니저 수정
- WIP : work in process 작업중
  <br><br>

### 커밋 구성

- subject : 첫글자 대문자, 50자 이내, 명령문의 형태
- body : 각줄 72자 이내, 무엇을 왜 (어떻게x)
- footer : 선택사항, 이슈 언급, <br>
  ex) Close(종료), Fixes(수정), Resolves(해결), Ref(참조), Related to(관련)
  <br><br>

### References

[How to Write a Git Commit Message](https://cbea.ms/git-commit/)<br>
[Udacity Git Commit Message Style Guide](https://udacity.github.io/git-styleguide/)<br>
[좋은 git commit 메시지를 위한 영어 사전](https://blog.ull.im/engineering/2019/03/10/logs-on-git.html)<br>
[좋은 git 커밋 메시지를 작성하기 위한 7가지 약속](https://meetup.toast.com/posts/106)<br>
