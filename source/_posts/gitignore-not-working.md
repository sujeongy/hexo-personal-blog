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
$ git commit -m "apply .gitignore"
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
> (!주의) 커밋되지 않은 변경사항을 다 잃을 수 있다.
>
> 현재 어떠한 수정사항이 없는 경우에서 진행되면 좋다.
>
> 또는 ignore 될 파일들을 부분적으로 제외시키고 커밋된 상태에서 진행하자. 


```
$ git reset HEAD --hard // solved

// it would work!
$ git rm -r --cached . 
$ git add .
$ git commit -m "fixed .gitignore"
$ git push
```

## 참조
  - [.gitignore is ignored by Git](https://stackoverflow.com/questions/11451535/gitignore-is-ignored-by-git)
  - [좋은 git 사용 습관](https://cjh5414.github.io/git-habit/)
