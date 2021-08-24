---
title: jekyll-theme-chirpy 사용법
author: 서동섭
date: 2021-08-17 22:53:00 +0800
categories: [Blogging, Tutorial]
tags: [jekyll-theme-chirpy]
pin: true
---

## Intro

jekyll-theme-chirpy 사용법(기록)
<br/>
3일째 해매다가...결국 공식 문서에 나와있는데로 하는게 답이였다...
<br/>
참고로 theme 마다 조금씩 사용법이 다르니 꼭 사용하는 theme의 공식 문서나 블로그를 참고 하기를 권장한다.

참고 | https://github.com/cotes2020/jekyll-theme-chirpy 
OS | window

## Installation

- `Ruby` 설치 버전 : `gemspec` 확인 필수
- `git`, `visual code` 설치

## 1. Git Repository 생성

[git id].github.io로 생성

## 2. 작업할 폴더에 theme 압축 풀기

```
 https://github.com/cotes2020/jekyll-theme-chirpy/archive/master.zip
```

## 3. _config.ym 수정

- timezone: Asia/Seoul
- title : sup blog
- tagline : developer
- description : 기록용 블로그
- url : "hptts://seodongsup.github.io"
- 기타... 본인 기준으로 작성

## 4. terminal 

`visual code terminal` 실행
```terminal
git init
bundle
./tools/init.sh
git branch -M master
git remote add origin [본인 git 저장소 주소]
git push -u origin master
```

## 5. test or sample post 작성후 커밋
visual stuido code 에서 post 작성하여 커밋 진행

## 6. Action 탭 automatic build 확인

5번을 진행하면 아래와 같이 자동으로 빌드가 된다.

![automatinc build](/assets/img/capture/mk_blog/action.PNG){: width="100%" height="100%"}

![automatinc build](/assets/img/capture/mk_blog/build.PNG){: width="100%" height="100%"}

## 7. 자동 빌드 완료

자동 빌드가 완료되면 `gh-pages` branch 가 추가 생성된다.
![gh-pages](/assets/img/capture/mk_blog/gh-pages.PNG){: width="100%" height="100%"}

## 8. branch 변경

`settings > Pages` 에서 branch 를 `gh-pages`로 변경후 저장.

![set page](/assets/img/capture/mk_blog/settings-1.PNG){: width="100%" height="100%"}

위와 같이 branch를 변경하지 않으면 아래와 같은 텍스트만 나온다.

```
 layout : home
```

필자는 처음에 여유있게 기다리지 못하고 위 방법이 잘못된줄 알고 이것저것 시도하다 맨붕...
<br/>
바로 적용되지 않으니 여유있게 기다려준다. ( 몇분 뒤에 적용됨 )
<br/>
본인이 설정한 URL로 접속하여 확인.

## 9. 로컬에서 실행 방법

```terminal
bundle exec jekyll s
```
