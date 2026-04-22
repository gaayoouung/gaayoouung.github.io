---
title: GitHub Pages 블로그 만들어보기! (+Jekyll, Chirpy)
date: 2026-04-22 
categories: [Blog]
tags: [github-pages, jekyll, chirpy, blog, github]
---

## 1. 블로그 저장소 준비
먼저 GitHub에 사용자 페이지 저장소를 준비합니다.  
이름.github.io 형식으로 만들어주시면 됩니다.

그리고 로컬에서 저장소를 클론합니다.  
터미널에서 명령어 똑같이 치면 됩니다. (주소만 바꾸시면 됩니다.)
```bash
mkdir ~/git
cd ~/git
git clone https://github.com/gaayoouung/gaayoouung.github.io.git
cd gaayoouung.github.io
```
## 2. 테마 가져오기
이제 테마를 적용할 차례입니다.  
[jekyll themes](https://jekyllthemes.io/free)
해당 사이트에서 마음에 드는 테마를 골라주시면 되는데요, 저는 국룰 테마([Chirpy](https://github.com/cotes2020/jekyll-theme-chirpy))를 사용했습니다.  

테마를 클론해서 현재 블로그 저장소에 복사해주시면 됩니다.
```bash
cd ~/git
git clone https://github.com/cotes2020/chirpy-starter.git
rsync -av --exclude='.git' ~/git/chirpy-starter/ ~/git/gaayoouung.github.io/
```

## 3. 블로그 프로필 설정
_config.yml 파일에서 블로그 이름, 설명 등을 수정할 수 있습니다.
```yml
lang: ko-KR
timezone: Asia/Seoul

title: GY
tagline: 공부 기록
description: >-
  Computer Science & Engineering

url: "https://gaayoouung.github.io"

github:
  username: gaayoouung

twitter:
  username:

social:
  name: 김가영
  email: banalite2412@gmail.com
  fediverse_handle:
  links:
    - https://github.com/gaayoouung
    - https://www.instagram.com/gaayoouung
```
위 항목들만 본인에 맞게 수정하면 됩니다.

## 4. 로컬에서 실행하기
```bash
bundle install
bundle exec jekyll serve
```
bundle install 이후 설치가 되지 않는다면, 보통 Ruby 버전 문제 입니다.  
테마에 맞는 Ruby 버전으로 맞춰주시면 정상적으로 설치됩니다. 

정상적으로 실행이 되면, 아래처럼 로컬 주소가 나옵니다.
```
Server address: http://....
Server running... press ctrl-c to stop.
```
이제 해당 주소를 복사해서, 브라우저로 접속해줍니다.  
테마가 문제 없이 적용되었다면, 마지막으로 GitHub에 push를 해주면 됩니다.

```bash
git status
git add -A
git commit -m "Apply Chirpy starter"
git push origin main
```
가끔 토큰의 권한 때문에 push에서 에러가 발생할 수도 있습니다.
```
refusing to allow a Personal Access Token to create or update workflow `.github/workflows/pages-deploy.yml` without `workflow` scope
```
여기서는 workflow 권한이 없다고 합니다.  
그럼 workflow를 포함해준 토큰을 새로 발급하고 다시 push 해주면 됩니다.

마지막으로, 실제 블로그 주소에 접속해서 정상적으로 만들어졌는지 확인하면 끝!

## 5. 글은 어떻게 써요?
블로그를 만들었으면, 이제 글을 올려볼 차례입니다.  
`_posts` 폴더에 Markdown 형식의 파일을 만들어서 작성하면 됩니다.  
파일 이름은 아래 형식을 지켜야 합니다.
```text
YYYY-MM-DD-파일명.md
```
터미널에서 touch 명령어를 통해 파일을 만들면 됩니다.  
이런 식으로 만들면 됩니다.

```bash
touch _posts/2026-11-11-mypost.md
```  

그리고 해당 파일을 VS Code 같은 편집기를 열어 내용을 작성하면 됩니다.   
글을 작성한 뒤에는 로컬에서 먼저 확인해볼 수 있습니다.

```bash
bundle exec jekyll serve
```

실행 후 브라우저에서 로컬 주소로 접속해서 확인하면 됩니다.  
문제가 없다면, 아까처럼 GitHub에 push 해주면 끝!