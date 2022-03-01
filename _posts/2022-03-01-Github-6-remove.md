---
layout: post
title: Github 6 remove
---

---

<br><br>

## Rename, Remove

<br>

새로 작성한 파일을 add하는 방법은 잘 작동하는데<br>
Rename 하거나 Remove 한 파일은 git status에 add되지 못한채 남아있음<br>
변경된 파일을 add하고 push하려면 어떻게 해야할지 궁금해짐<br>

```javascript
git add -u
//rename, remove 파일만 반영

git commit -a -m"comment"
//rename, remove 파일만 commit
```

아주 잘 작동함

<br><br>

## Definition

<br>
Git이랑 Github는 정확하게 뭐가 다른지 궁금
<br><br>

Git : 버전 관리 '프로그램'(local)

- 오픈소스 버전 관리 시스템(VCS:Version Control System)
- 로컬에서 버전 관리
- 소프트웨어 개발 및 소스 코드 관리에 사용

git은 본인의 코드와 그 수정내역을 기록하고 관리도록 돕는 프로그램<br>
로컬에서 프로젝트 기록을 스스로 관리할 수 있도록 해줌<br>
git을 통해 브랜치를 생성하고 복구 삭제 병합등이 가능<br>
로컬 저장소를 사용하기 때문에 다른개발자와 실시간으로 작업공유 불가능<br>
<br><br>

Github : git의 기능을 확장해서 쓸수있는 원격저장소(remote)

- Git Repositiory를 위한 웹 기반 호스팅 서비스
- 클라우드 서버를 사용해 로컬에서 버전 관리한 소스코드를 업로드하여 공유
- 분산 버전제어, 엑세스 제어, 소스코드 관리, 버그추적, 기능요청등 작업관리

github는 git repository를 관리하는 클라우드 기반 호스팅 서비스임<br>
git repository hosting service는 cloud기반으로 다른사람과 소스코드 공유가 가능하고 git의 기본적인 기능을 확장해서 제공함<br>
이런 작업을 cloud서버에서 하기 때문에 프로젝트에 여럿을 개발자가 참여하여 버전제어 및 공동작업 가능<br>
