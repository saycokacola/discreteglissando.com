---
layout: post
title: "파이썬 Requests 모듈"
date: 2014-08-09 20:23
comments: true
external-url:
categories: [Python, technology]
---
파이썬에는 [HTTP](http://en.wikipedia.org/wiki/Hypertext_Transfer_Protocol)를 이용하는 프로그램을 작성할 때에 사용할 수 있는 urllib 모듈이 기본적으로 포함되어 있다.[^1] 하지만 urllib 모듈은 사용법이 그리 쉽지 않고 간단한 처리를 하려고 해도 제법 많은 양의 코딩을 해야 하는 경우도 종종 있다. 최근 urllib 모듈 대신에 Requests라는 모듈이 널리 사용되고 있다. 

<!--more-->

Requests 모듈은 Apache2 라이센스의 HTTP 라이브러리로, _인간을 위한 HTTP_(HTTP for Humans)라는 모토를 가지고 있다. 2014년 8월을 기준으로 2.3.0 버전까지 개발이 되었고 pip을 사용하여 간단하게 설치할 수 있다.

``` console
$ pip install requests
```

## Requests 모듈을 이용하여 요청 보내기

Requests 모듈을 이용하여 서버에 요청을 보내는 것은 매우 간단하다.

우선 Requests 모듈을 임포트한 후에

``` python 
import requests
```

간단하게 GET method의 HTTP 요청을 보낼 수 있다.

``` python
r = requests.get("http://httpbin.org/get")
```

POST method의 경우도 비슷하다.

``` python
r = requests.post("http://httpbin.org/post")
```

GET과 POST 외에도 PUT, DELETE, HEAD, OPTIONS 모두 이렇게 간단하게 요청을 보낼 수 있다.

``` python 
r = reqeusts.put("http://httpbin.org/put")
r = requests.delete("http://httpbin.org/delete")
r = requests.head("http://httpbin.org/head")
r = requests.options("http://httpbin.org/options")
```

이러한 방법을 통해 요청 오브젝트를 생성한 후에는 그 오브젝트를 이용하여 필요한 정보를 추출할 수 있다.

Requests 모듈에 대한 더 자세한 정보는 다음에서 얻을 수 있다.

* [Requests Documentation](http://docs.python-requests.org/en/latest/)
* [python for beginners](http://www.pythonforbeginners.com/requests/using-requests-in-python)
* [gun.io](https://gun.io/blog/python-for-the-web/)
 
[^1]: 파이썬 2.X에는 urllib과 urllib2 모듈이 분리되어 있다.
