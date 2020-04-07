---
layout: post
title: Github committer 변경하기
tags: [Github]
---

# Github committer 변경하기

한참 블로그를 제작하고 있는데 아무리 `commit`을 하더라도 로그가 안 찍히는 형상이 발견됐다. 이게 무엇이지하고 로그를 보니
![스크린샷 2020-04-06 오후 10 13 24](https://user-images.githubusercontent.com/35090976/78562525-7abcc900-7854-11ea-9021-97fc4e5b7e20.png)
커밋이 내 깃허브 계정(kyun92)이 아닌 맥북 계정(skyun lim)으로 진행되고 있었다.
`committer`가 꼬여버린 것이다.

# committer 변경하기

이 현상은 `github config`의 `username` 설정이 꼬여서 발생한 문제로 아래의 커맨드로 변경해줘야한다.

```
$ git config --global user.name "원하는이름"

// 이메일도 꼬여있을 수 있으니 수정해줬다
$ git config --global user.email 이메일
```

그리고 최근 했던 커밋을 리셋해주자

```
$ git commit --amend --reset-author
```

[https://cs09g.tistory.com/5](https://cs09g.tistory.com/5)
