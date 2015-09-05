---
layout: post
title: "OS X에서 Octropress 설치하기"
date: 2014-06-15 22:49
comments: true
external-url:
categories: [technology, octopress]
---

{% img /images/octopress.png %}

[Octopress](http://octopress.org/)는 [Github Pages](https://pages.github.com/)에서 사용되는 정적 웹사이트 생성 도구인 [Jekyll](https://github.com/jekyll/jekyll)을 위해 [Brandon Mathis](http://brandonmathis.com/)이 디자인한 프레임워크이다. 보통 Jekyll을 이용하여 블로그를 시작 할 때에는 직접 HTML 템플릿과, CSS, 자바스크립트를 작성하고 설정해야하지만 Octopress를 사용할 때에는 그러한 수고를 하지 않고, Octopress를 clone하거나 fork한 후 필요한 패키지들과 테마를 설치하면 바로 블로그 운영을 시작할 수 있다.

<!--more-->

Octopress를 사용할 때에는 버전 1.9.3 이상의 Ruby를 필요로 한다. OS X에 기본적으로 포함되어 있는 Ruby를 사용할 수도 있겠지만 Rbenv를 이용하여 설치한 Ruby를 사용하는 것이 권장되고 있다.

## Ruby 설치

Rbenv는 Homebrew를 이용하여 간단하게 설치할 수 있다.

``` shell-session
$ brew update
$ brew install rbenv
$ brew install rbenv-build
```

Rbenv가 설치된 후에는 Rvenv를 이용해 루비 1.9.3을 설치한다.

``` shell-session
$ rbenv install 1.9.3-p0
```

이 때 이 디렉토리 안에서만 Ruby 1.9.3-p0을 사용하고 싶다면

``` shell-session
$ rbenv local 1.9.3-p0
$ rbenv rehash
```

를 실행하고, OS X 전체에서 1.9.3-p0을 사용하고 싶다면

``` shell-session
$ rbenv global 1.9.3-p0
$ rbenv rehash
```

를 실행해주면 된다.

## Octopress 설치

``` shell-session
$ git clone git://github.com/imathis/octopress.git www.mydomain.com
$ cd www.mydomain.com
```

그 후 Ruby의 패키지 매니저인 gem을 이용하여 bundler를 설치한다.

``` shell-session
$ gem install bundler
$ rbenv rehash
$ bundle install
```

Octopress의 기본 테마를 설치하면 기본적인 설치 과정은 끝난다.

``` shell-session
$ rake install
```

블로그를 생성한 후

```
$ rake generate
```

미리보기 명령을 실행하면

```
$ rake preview
```

[http://localhost:4000](http://localhost:4000)에 접속하여 블로그의 모양새를 미리 확인할 후 있다.

설치 이후의 단계들은 다음 링크들에서 찾아볼 수 있다.

* [Rsync를 이용하여 서버에 블로그 소스 올리기](/blog/2014/06/16/deploy-octopress-with-rsync/)   
* [블로그 설정하기](/blog/2014/06/16/config-octopress-blog/)  
* [Octopress 블로깅의 기초](/blog/2014/06/18/octopress-blogging-basics/)

