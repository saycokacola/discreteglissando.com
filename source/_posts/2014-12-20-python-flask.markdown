---
layout: post
title: "Flask 프레임워크"
date: 2014-12-20 16:40
comments: true
categories: technology
---

Flask는 파이썬으로 짜여진 [웹 어플리케이션 프레임워크](http://en.wikipedia.org/wiki/Web_application_framework)로, [Werkzeug](http://werkzeug.pocoo.org/) [WSGI](http://en.wikipedia.org/wiki/Web_Server_Gateway_Interface) 툴킷과 [Jinja2](http://jinja.pocoo.org/)에 기반을 두고 있다. Python 2와 3 모두 지원하고 있지만 Python 3에서 Flask를 사용할 때에 약간의 문제가 발생할 수 있어 개발자인 Armin Ronacher는 Python 2.6 또는 2.7 버전을 권장하고 있다.

Flask는 Armin Ronacher가 2010년 4월 1일에 재미삼아 개발을 시작했는데, 큰 인기를 얻게 되자 본격적으로 개발이 되기 시작하여 2014년 12월을 기준으로 0.10.1 버전까지 공개되었다.

<!--more-->

Flask는 '마이크프레임워크'로 소개되는데, 여기서 '마이크로'는 웹 어플리케이션의 모든 코드를 하나의 파이썬의 파일에 포함시켜야 하거나 기능이 제한적이라는 뜻이 아니라 프레임워크의 핵심 요소가 단순하고 유연하다는 의미이다. Flask에는 어떠한 데이터베이스를 필수적으로 사용해야 한다던지의 지정된 사항이 많지 않고 지정된 사항들도 간단하게 변경할 수 있다.

Flask를 이용하여 웹 개발을 할 때는 Python에 Flask를 임포트하여 간단한 템프리트를 따라서 코딩을 하면 된다. 이러한 방법을 사용하면 웹 개발에 걸리는 시간을 단축할 수 있다. Flask 프레임워크를 이용하여 개발된 어플리케이션의 몇 가지 예시로는 [Pinterest](https://www.pinterest.com/), [LinkedIn](https://kr.linkedin.com/), 그리고 [Flask의 웹사이트](http://flask.pocoo.org/) 등이 있다.

Flask 프레임워크에 대한 더 자세한 정보는 다음에서 얻을 수 있다.

* [Flask Documentation](http://flask.pocoo.org/docs/0.10/)
* [Full Stack Python](http://www.fullstackpython.com/flask.html)

