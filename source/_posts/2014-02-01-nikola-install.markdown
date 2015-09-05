---
layout: post
title: "Nikola의 설치와 설정"
date: 2014-02-01 20:50
comments: true
external-url:
categories: [Python, technology, nikola]
---
{% img http://getnikola.com/assets/img/logo.svg %}

[Nikola](https://github.com/getnikola/nikola)는 파이썬으로 구현된 정적 웹사이트 생성 도구이다. 블로그의 운영을 하면서 파이썬 공부도 할겸 Nokola를 설치해 보았다.[^1]

<!--more-->

## Nikola의 설치

Nikola는 파이썬으로 만들어졌기 때문에 파이썬 패키지 관리자를 이용하여 다음과 같이 간단히 설치할 수 있다.

``` shell-session
$ pip install nikola
```

이 때 중요한 점은 설치된 파이썬의 버전이 2.6 이상 또는 3.3 이상이어야 한다는 것이다. nikola를 설치하는 도중에 다른 
패키지를 설치해야 한다는 에러 메시지가 뜰 수도 있는데 그런 경우에는 그 패키지를 설치하면 된다.
예를 들어 requests 패키지를 설치해야한다고 하면

``` shell-session
$ pip install requests
```

와 같이 설치하면 된다.

## 사이트 생성 및 작동 실험

설치를 마친 후에는 다음과 같이 nikola를 실행하여 데모 사이트를 포함하고 있는 mysite라는 디렉토리를 만든다.

``` shell-session
$ nikola init --demo mysite
```

설치가 잘 되었는지 확인하기 위해 생성된 디렉토리로 이동하여 데모 사이트를 생성한다.

``` shell-session
$ cd mysite
$ nikola build
```

위의 과정을 거치면 웹 서버로 서비스할 수 있는 html 파일 등의 리소스가 만들어진다. 리소스가 제대로 생성되었는지를
확인하기 위해 내장 웹 서버를 실행한다.

``` shell-session
$ nikola serve
Serving HTTP on 127.0.0.1 port 8000 ...
```

이 작업을 마친 후에 웹 브라우저에서 [http://localhost:8000](http://localhost:8000)에 접속하면 샘플 사이트를 볼 수 있다. 
이 기능는 작성한 글을 미리 확인하는 데에 유용하게 사용할 수 있다. 

기본적으로 `serve` 명령은 웹 서버를 127.0.0.1라는 IP와 8000 포트에서 실행하지만 `-a`와 `-p` 선택사항을 사용하여 IP와 포트를 지정할 수 있다.

## 테마의 설치와 적용

Nikola는 몇 가지 기본 테마를 지원한다. 설치 가능한 테마들은 다음과 같이 하여 확인할 수 있다.

``` shell-session
$ nikola install_theme -l
Themes
-------
base-jinja
blogtxt
⋮
⋮
```

설치는 `install_theme` 명령으로 한다.

``` shell-session
$ nikola install_theme blogtxt
[2013-10-12T16:46:13Z] NOTICE: install_theme: Downloading
http://themes.getnikola.com/v6/blogtxt.zip
[2013-10-12T16:46:15Z] NOTICE: install_theme: Extracting: blogtxt into themes
```

테마를 성공적으로 설치했다면 mysite 디렉토리의 `conf.py` 파일을 텍스트 에디터로 편집하여 설치한 테마를 적용한다. 예를 들어,

``` python
# Name of the theme to use.
THEME = "bootstrap"
```

를

``` python
# Name of the theme to use.
THEME = "blogtxt"
```

과 같이 설정한다.

[^1]: 2014년 6월부터 Nikola가 아닌 Octopress를 사용하고 있다.
