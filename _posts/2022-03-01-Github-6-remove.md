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
