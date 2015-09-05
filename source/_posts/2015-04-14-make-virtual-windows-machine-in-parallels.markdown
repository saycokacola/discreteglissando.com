---
layout: post
title: "Parallels Desktop에서 윈도우즈 버추얼 머신 생성하기"
date: 2015-04-14 22:28:19 +0900
comments: true
categories: technology
---

{% img /images/parallels_desktop.jpg %}

[애플](http://en.wikipedia.org/wiki/Apple_Inc.)의 [맥 OS](http://en.wikipedia.org/wiki/OS_X)를 사용하다 보면 인터넷 강의를 시청하거나 인터넷 결제 등을 하려할 때 [윈도우즈]() 환경에서만 실행되는 기능을 사용할 수가 없어 불편함을 느끼는 경우가 있다. 이러한 문제에 대한 해결책 중 하나는 맥에 윈도우즈 [버추얼 머신]()을 생성하여 버추얼 머신을 통해서 윈도우즈의 기능을 사용하는 것이다. 그러한 일을 하는 어플리케이션은 여러 가지가 있는데, 가장 널리 알려져있는 어플리케이션 중 하나는 [Parallels Desktop](http://en.wikipedia.org/wiki/Parallels_Desktop_for_Mac)이다.

<!--more-->

Parallels Desktop에서 버추얼 머신을 생성하여 윈도우즈 환경을 사용하는 것은 몇 가지의 어렵지 않은 과정을 거치면 된다. 

우선 버추얼 머신에서 사용할 윈도우즈 [iso](http://en.wikipedia.org/wiki/ISO_image) 파일을 로컬 기계로 복사한 후, Parallels Desktop을 실행한다. 그 후 `파일>새로 만들기`를 선택하여 안내에 따라 새 버추얼 머신의 설정과 설치를 진행한다. 이 때 Parallels Desktop에서 로컬에 있는 [운영 체제](http://en.wikipedia.org/wiki/Operating_system) 이미지 파일 또는 디스크를 자동으로 탐색하는데 이 때 원하는 운영 체제가 탐색이 되지 않는 경우가 있다. `수동으로 찾기` 옵션으로도 잘 선택이 되지 않을 때도 있는데, 이런 경우에는 `소스를 지정하지 않고 계속` 항목을 체크하고 진행한 후 나중에 iso 파일을 연결하는 방법을 사용하면 된다. 끝으로 몇 분을 기다려 윈도우즈 설치가 완료되면 모든 과정이 끝난다.