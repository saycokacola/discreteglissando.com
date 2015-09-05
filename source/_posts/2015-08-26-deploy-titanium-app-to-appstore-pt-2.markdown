---
layout: post
title: "Titanium 프로젝트 테스트하고 배포하기(iOS): 어플리케이션 빌드하여 테스트하기"
date: 2015-08-26 23:42
comments: true
categories: [technology, titanium, ios, development]
---

{% img /images/ios_developer.jpg %}

Titanium 프로젝트를 iOS 앱으로 빌드하고 테스트하는 데에 필요한 과정을 모두 마친 후에는 어플리케이션을 빌드하여 실제 iOS 기기에서 테스트를 해보았다. 필수적으로 거쳐야 하는 과정은 아니지만 맥에서 구동하는 [iOS Simulator](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/iOS_Simulator_Guide/)와 실제 iOS 기기의 환경은 다르기 때문에 어플리케이션을 배포하기 전에 실제 기기에서 테스트를 하는 것이 권장된다. 

<!--more-->

Titanium 프로젝트를 어플리케이션으로 빌드하기 위해서는 Indie, Team, Enterprise 중 하나의 플랜을 [결제](http://www.appcelerator.com/pricing/)해야 한다. 나의 경우에는 한 사람의 개발자에게 최소한의 필요한 기능을 제공하는 Indie 플랜을 사용한다.

## 스튜디오로 어플리케이션 빌드하기

[Appcelerator 다큐멘테이션](http://docs.appcelerator.com/platform/latest/#!/guide/Deploying_to_iOS_devices)에서는 [스튜디오](http://www.appcelerator.com/platform/appcelerator-studio/)를 이용하는 방법과 [CLI](https://en.wikipedia.org/wiki/Command-line_interface)를 이용하는 방법, 어플리케이션을 빌브하는 두 가지의 방법을 소개한다. 하지만 내가 스튜디오를 앱을 빌드하려고 했을 때에는 계속해서 에러가 나며 빌드를 진행할 수 없었고 로그아웃과 로그인을 반복해 보아도 해결되지 않았다. 조사를 해보니 나뿐만이 아니라 여러 사용자들에게 이러한 문제가 발생하고 있는데, 왜 그러한 오류가 발생하는지에 대해서는 [Appcelerator](http://www.appcelerator.com/)측에서도 확실하게 알지 못하는듯 하다. 또한 이는 빠르게 해결이 되어야할 사안임에도 몇 개월째 해결이 되지 않고 있다.

## CLI로 어플리케이션 빌드하기

결국에는 스튜디오를 통해서는 앱을 빌드할 수 없다고 판단되어 CLI를 이용하여 빌드를 하게되었다. CLI를 이용하여 앱을 빌드하고 테스트용 iOS 기기에 설치하기 위해서는 먼저 테스트용으로 사용할 기기를 데이터 케이블로 컴퓨터에 연결해야 한다. 그 후에는 [터미널](https://en.wikipedia.org/wiki/Computer_terminal#Emulation)을 실행하고 프로젝트의 위치로 이동하여 다음 명령어를 입력한다.

``` bash
$ appc run -p ios -T device
```

그러면 다음과 같은 결과가 보여질 것이다.

``` bash
Appcelerator Command-Line Interface, version 4.1.2
Copyright (c) 2014-2015, Appcelerator, Inc.  All Rights Reserved.

Which developer certificate would you like to use?
/Users/user-name/Library/Keychains/login.keychain
   1)  <developer-name> (<certificate-ID>)  (expires <expiration-date>)
   ⋮
   ⋮
Select a certificate by number or name:
```

자신이 사용할 iOS Devolpment Certificate를 선택한 후에는 

``` bash
Which provisioning profile would you like to use?
Available Development UUIDs:
   1)  <profile-UUID> iOSTeam Provisioning Profile: com.your-domain.*   (expires <expiration-date>)
   2)  <profile-UUID> iOSTeam Provisioning Profile: com.your-domain.example    (expires <expiration-date>)
   3)  <profile-UUID> example: com.your-domain.*    (expires <expiration-date>)
   ⋮
   ⋮
Select a provisioning profile UUID by number or name:
```

profile를 선택해야 한다. 그 후에는 자동적으로 앱이 빌드되어 연결된 기기에 설치된다. 설치가 완료된 후에는 자유롭게 테스트를 할 수 있고, 기기가 컴퓨터에 연결된 동안에는 터미널에 Titanium API 반응이 표시된다.

* [Titanium 프로젝트 테스트하고 배포하기(iOS): Certificates, Identifiers & Profiles](/blog/2015/08/24/deploy-titanium-app-to-appstore-pt-1/)  
* [Titanium 프로젝트 테스트하고 배포하기(iOS): iOS 앱 스토어로 배포하기](/blog/2015/08/30/deploy-titanium-app-to-appstore-pt-3/)