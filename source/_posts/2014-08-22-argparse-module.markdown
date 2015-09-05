---
layout: post
title: "파이썬 argparse 모듈"
date: 2014-08-22 19:29
comments: true
external-url:
categories: [Technology, python]
---

[명령행 인터페이스(커맨드 라인 인터페이스)](http://en.wikipedia.org/wiki/Command-line_interface)에서 명령행 인자를 받아서 실행되는 프로그램의 경우 주어진 인자들을 파싱하는 작업이 필요하다. 여러 가지 방법이 있겠지만 파이썬 3의 표준 라이브러리에 추가된 argparse 모듈을 사용하면 매우 간단하게 명령행 인자 파싱을 할 수 있고, 문법 안내와 헬프 메시지를 자동으로 생성해주어서 매우 편리하다.

<!--more-->

argparse는 앞에서 설명했던 대로 파이썬 3에서 새롭게 추가된 모듈이다. 파이썬 2에서 사용할 때에는 pip으로 설치하면 된다.​

``` console
$ pip install argparse
```

## argparse 모듈의 기본적인 사용법

우선 argparse를 임포트한다.

``` python
import argparse
```

그후 파서를 선언하고 명령행 인자를 파싱하는 메소드를 이용하여 파싱을 수행한다.

``` python
parser = argparse.ArgumentParser()
parser.parse_args()
```

이렇게 코드에서 argparse를 사용하게 되다면 커맨드 라인에서 실행할 때 `--help` 또는 `-h` 옵션으로 이 코드를 실행하는 데에 필요한 명령행 인와 그에 대한 설명을 확인할 수 있다.

``` console
$ python3 prog.py --help
usage: prog.py [-h]

optional arguments:
  -h, --help  show this help message and exit
```

또한 명령행 인자를 지정하지 않았거나 잘못된 인자를 지정했을 때에도 자동적으로 에러 메시지를 출력한다.

``` console
$ python3 prog.py
usage: prog.py [-h] echo
$ python3 prog.py --verbose
usage: prog.py [-h]
prog.py: error: unrecognized arguments: --verbose
```

## argparse 모듈을 이용하여 명령행 인자 파싱하기

다음은 argparse를 이용해 위치 명령행 인자(필수 명령행 인자)를 파싱하 간단한 예제이다.

``` python
import argparse
parser = argparse.ArgumentParser()
parser.add_argument("echo")
args = parser.parse_args()
print(args.echo)
```

그 후 코드를 실행하면 다음과 같은 결과를 얻을 수 있다.

``` console
$ python3 prog.py
usage: prog.py [-h] echo
prog.py: error: the following arguments are required: echo
$ python3 prog.py --help
usage: prog.py [-h] echo

positional arguments:
  echo

optional arguments:
  -h, --help  show this help message and exit
$ python3 prog.py foo
foo
```

명령행 인자를 추가한 경우, 아무 인자가 주어지지 않았을 때에도 에러 메시지가 출려되는 것을 확인할 수 있다.

위와 같은 경우, `--help` 옵션을 통해 볼 수 있는 도움말이 실질적으로 큰 도움을 주지는 못하고 있다. 현재로서는 `echo`라는 위치 인자가 있다는 것은 확인할 수 있지만 소스 코드를 참고하지 않으면 그 인자가 어떠한 일은 하는지는 알 수가 없다. 하지만 이것은 다음과 같이 설명을 붙여서 해결할 수 있다.

``` python
import argparse
parser = argparse.ArgumentParser()
parser.add_argument("echo", help="echo the string you use here")
args = parser.parse_args()
print(args.echo)
```

이 코드를 실행하면

``` console
$ python3 prog.py -h
usage: prog.py [-h] echo

positional arguments:
  echo        echo the string you use here

optional arguments:
  -h, --help  show this help message and exit
```

이와 같이 명령행 인자에 대한 설명이 추가된 것을 볼 수 있다.

기본적으로 인자의 타입은 스트링으로 지정이 되는데 인자의 타입을 스트링이 아닌 다른 타입으로 지정하고 싶은 경우에는 다음과 같이 지정할 수 있다.

``` python
import argparse
parser = argparse.ArgumentParser()
parser.add_argument("square", help="display a square of a given number",
                    type=int)
args = parser.parse_args()
print(args.square**2)
```

위와 같이 인자의 타입을 정수로 지정했을 때는 정수가 아닌 스트링을 주었을 때 에러 메시지가 출력된다.

``` console
$ python3 prog.py 4
16
$ python3 prog.py four
usage: prog.py [-h] square
prog.py: error: argument square: invalid int value: 'four'
```

위치 인자가 아닌 선택 인자는 다음과 같이 추가한다.

``` python
import argparse
parser = argparse.ArgumentParser()
parser.add_argument("--verbosity", help="increase output verbosity")
args = parser.parse_args()
if args.verbosity:
    print("verbosity turned on")
```

실행 결과는 다음과 같다.

``` console
$ python3 prog.py --verbosity 1
verbosity turned on
$ python3 prog.py --help
usage: prog.py [-h] [--verbosity VERBOSITY]

optional arguments:
  -h, --help            show this help message and exit
  --verbosity VERBOSITY
                        increase output verbosity
$ python3 prog.py --verbosity
usage: prog.py [-h] [--verbosity VERBOSITY]
prog.py: error: argument --verbosity: expected one argument
```

선택 인자의 짧은 버전도 간단하게 지정할 수 있다.

``` python
import argparse
parser = argparse.ArgumentParser()
parser.add_argument("-v", "--verbose", help="increase output verbosity",
                    action="store_true")
args = parser.parse_args()
if args.verbose:
    print("verbosity turned on")
```

argparse 모듈에 대한 더 자세한 사용법은 다음에서 확인할 수 있다.

https://docs.python.org/3/howto/argparse.html
