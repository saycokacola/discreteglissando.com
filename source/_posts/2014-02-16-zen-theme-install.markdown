---
layout: post
title: "Nikola Zen 테마의 설치"
date: 2014-02-16 21:52
comments: true
external-url:
categories: [Python, technology, nikola]
---
{% img /images/zen.png %}

Nikola에는 사이트에 적용할 수 있는 몇 가지의 기본 테마(theme)가 포함되어 있다. 지금 나의 블로그에서 사용 중인 테마는 zen이다.[^1] zen 계열의 테마들은 다른 nikola 테마와는 달리 설치하는 과정이 조금 복잡하다. 

<!--more-->

## Zen 테마의 설치

Zen 테마 자체는 다른 테마들과 마찬가지로 다음과 같이 간단하게 설치할 수 있다.

``` shell-session
$ nikola install_theme zen
```

zen을 설치하면 다른 테마들과는 달리 아래와 같은 안내 메시지가 표시된다.

``` shell-session
[2014-01-30T12:54:21Z] NOTICE: install_theme: This plugin has a sample config file.  Integrate it with yours in order to make this theme work!
Contents of the conf.py.sample file:

    NAVIGATION_LINKS = {
        DEFAULT_LANG: (
            ('/index.html', 'Home', 'icon-home'),
            ('/archive.html', 'Archives', 'icon-folder-open-alt'),
            ('/categories/index.html', 'Tags', 'icon-tags'),
            ('/rss.xml', 'RSS', 'icon-rss'),
            ('http://getnikola.com', 'About me', 'icon-user'),
            ('https://twitter.com/getnikola', 'My Twitter', 'icon-twitter'),
            ('https://github.com/getnikola', 'My Github', 'icon-github'),
        )
    }

[2014-01-30T12:54:21Z] NOTICE: install_theme: Remember to set THEME="zen" in conf.py to use this theme
```

Zen 테마는 위에 보인 것과 같이 `conf.py`의 `NAVIGATION_LINKS` 설정 형식이 다른 테마들과 다르다. 그러므로 위의 내용을 잘 메모해 두었다가 이후의 설정에 참고해야 한다.

## Node, npm, lessc 설치

Zen이 정상적으로 작동하기 위해서는 스타일시트 언어인 [LESS](http://en.wikipedia.org/wiki/LESS_\(stylesheet_language\))의 컴파일러인 lessc가 필요하다. lessc를 설치하기 위해서는 [npm](http://en.wikipedia.org/wiki/Npm_\(software\))(Node Package Manager)이 필요하고 npm을 설치하기 위해서는 당연히 [Node.js](http://en.wikipedia.org/wiki/Node.js)가 필요하다. Node는 내가 사용하는 [OS X](http://en.wikipedia.org/wiki/OS_X)에서는 [Homebrew](http://en.wikipedia.org/wiki/Homebrew_\(package_management_software\))를 이용해서 간단하게 설치할 수 있다.
    
``` shell-session
$ brew install node
⋮
⋮
⋮
⋮
```

brew를 이용해서 Node를 성공적으로 설치했다면 npm도 자동적으로 같이 설치되었을 것이다. 다음은 lessc를 설치할 차례이다. lessc는 Node 패키지로 제공되므로 다음과 같이 npm으로 설치한다.

``` shell-session
$ npm install -g less
```

이 때 `-g` 선택사항을 반드시 지정해야 한다.

## conf.py 수정

Zen을 사용할 준비가 모두 끝났다면 Nikola의 `conf.py` 파일을 수정해야 한다. Zen에서는 다른 테마와 다르게 사이드바에서 아이콘을 사용한다.
이의 설정은 위에서 언급한 `NAVIGATION_LINKS`를 이용해 한다. 즉, `conf.py`에서

``` python
# Links for the sidebar / navigation bar.
# You should provide a key-value pair for each used language.
NAVIGATION_LINKS = {
    DEFAULT_LANG: (
        ('/archive.html', 'Archives'),
        ('/categories/index.html', 'Tags'),
        ('/rss.xml', 'RSS'),
    ),
} 
```

를 

``` python
# Links for the sidebar / navigation bar.
# You should provide a key-value pair for each used language.
#NAVIGATION_LINKS = {
#    DEFAULT_LANG: (
#        ('/archive.html', 'Archives'),
#        ('/categories/index.html', 'Tags'),
#        ('/rss.xml', 'RSS'),
#    ),
#}

NAVIGATION_LINKS = {
  DEFAULT_LANG: (
    ('/index.html', 'Home', 'icon-home'),
    ('/archive.html', 'Archives', 'icon-folder-open-alt'),
    ('/categories/index.html', 'Tags', 'icon-tags'),
    ('/rss.xml', 'RSS', 'icon-rss'),
    ('http://getnikola.com', 'About me', 'icon-user'),
    ('https://twitter.com/getnikola', 'My Twitter', 'icon-twitter'),
    ('https://github.com/getnikola', 'My Github', 'icon-github'),
  )
} 
```

와 같이 Zen을 설치했을 때 나온 안내 메시지를 참고하여 수정하면 된다. 구체적인 링크와 메뉴 항목은 사이트의 상황에 맞추어 수정하면 된다. 그리고 다음과 같이 설치된 테마를 적용한다.

``` python
# Name of the theme to use.
THEME = "zen"
```

이제 다음과 같이 사이트를 빌드하여 테마가 적용된 결과를 확인할 수 있다.

``` shell-session
$ nikola build
$ nikola serve
```

[^1]: 2014년 6월부터 Nikola가 아닌 Octopress를 사용하고 있다.
