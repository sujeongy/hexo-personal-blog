---
title: .gitignore not working
date: 2020-02-15 01:01:54
tags:
    - NotWorking
    - git
---

## 현상
.gitignore 파일이 제대로 동작되지 않아, 무시되어야 할 파일과 폴더들이 커밋에 포함된다.


## 시도
> .gitignore 파일을 나중에 적용하는 경우, 주로 사용되는 방법

```
$ git rm -r --cached .
$ git add .
$ git commit -m "fixed .gitignore"
$ git push
```
아래와 같은 이슈 발생
```
E:\hexo-personal-blog>git rm -r --cached .
error: the following files have staged content different from both the
file and the HEAD:
    .deploy_git
    .idea/workspace.xml
(use -f to force removal)
```


## 해결 방법
(!주의) 적용기전, 커밋부터 하자.

커밋되지 않은 변경사항 다 날라갈수 있다.
```
git rm -r --cached .
git reset HEAD --hard
git status
```

## 참조
  - [.gitignore is ignored by Git](https://stackoverflow.com/questions/11451535/gitignore-is-ignored-by-git)
  - [좋은 git 사용 습관](https://cjh5414.github.io/git-habit/)
