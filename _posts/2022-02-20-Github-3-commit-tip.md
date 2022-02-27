---
layout: post
title: Github 3 commit tip
---

---

<br>

## Git commit tip

<br>

### - Title / Body separate

<br>
commit내용을 제목을 띄우고 작성하면

```bash
        git commit -m"Fix: typo some docs some sentence"

        git commit -m"Fix: typo
                    some docs some sentencs"
```

<br><br>

git log 명령어를 사용했을 경우 큰 차이 없이 보여지지만<br>

```bash
        $ git log
        commit 42e769bdf4894310333942ffc5a15151222a87be
        Author: Kevin Flynn <kevin@flynnsarcade.com>
        Date: Fri Jan 01 00:00:00 1982 -0200

        Fix: typo

        some docs some sentencs
```

<br><Br>

git log --online / git shortlog 명령어를 사용했을 때

```bash
        $ git log --oneline
        42e769 Fix: typo
```

위처럼 그동안 commit해온 내용들의 제목만 잘라서 보여줌

<br><br>

### - Title : 영자 50 / 대문자 / . 금지 / 명령조

<br>

- 영자기준 50자 (출력시 한줄안쪽)<br>
- 첫글자는 대문자<br>
- . 사용금지<br>
- 명령조 : 시각적으로 간결하고 시스템 명령문과도 일치

<br><br>

### - Body : 영자 72자

<br>

- 영자 기준 72자 마다 줄을 바꾸면 출력시 시각적으로 잘 정돈됨
- 어떻게 보다 무엇을, 왜 에 맞춰 작성하기

<br><br>

### References

[Writing good commit messages](https://github.com/erlang/otp/wiki/Writing-good-commit-messages)<br>
[How to Write a Git Commit Message](https://cbea.ms/git-commit/)<br>
[5.2 Distributed Git - Contributing to a Project](https://git-scm.com/book/en/v2/Distributed-Git-Contributing-to-a-Project)<br>
[PRETTY FORMATS](https://git-scm.com/docs/pretty-formats)
