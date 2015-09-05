---
layout: post
title: "Titanium 프로젝트 테스트하고 배포하기(iOS): iOS 앱 스토어로 배포하기"
date: 2015-08-30 22:44
comments: true
categories: [technology, titanium, ios, development]
---

{% img /images/ios_developer.jpg %}

어플리케이션 빌드와 테스트를 모두 마친 후에 Titanium 프로젝트에서 아무런 문제를 발견하지 못했다면 [iOS 앱 스토어](https://en.wikipedia.org/wiki/iOS_App_Store)통해서, 혹은 In House 또는 Ad Hoc의 방식으로 앱을 배포할 준비가 끝난 것이다. 나의 경우에는 앱 스토어를 통해 앱을 배포하는 과정을 따랐다. 

<!--more-->

## iTunes Connect에서 App ID 생성

iOS 앱 스토어를 통해 어플리케이션을 배포하기 위해서는 먼저 [iTunes Connect](https://itunesconnect.apple.com/) 계정을 만들어야 한다. 계정을 만든 후에는 iTunes Connect에서 `나의 App`으로 이동하고 `+` 버튼을 클릭한다. `신규 iOS App`과 `신규 Mac App`을 선택할 수 있는데 나는 iOS 앱의 개발을 마치고 배포하려 하고 있었기 때문에 `신규 iOS App`을 선택하여 진행하였다. 어플리케이션 이름, 기본 언어, 번들 ID, 버전 정보, SKU를 입력한 후에는 앱에 대한 더 자세한 정보를 입력할 수 있는 페이지로 이동하게 된다. 

어플리케이션 페이지에서는 다음의 정보를 입력하거나 업로드해야 한다.

* 출시 일자(현재 일자가 기본값)  
* 가격  
* 버전 정보  
* 앱 설명(4000자 이내)  
* 카테고리  
* 키워드(100자 이내)  
* 저작권 정보  
* 이메일 주소  
* 지원 URL  
* 등급  
* 앱 아이콘(1024px x 1024px)  
* 1개 이상의 스크린샷(앱이 지원하는 모든 화면 크기별로 최소 1개씩 필요하다.)

모든 정보를 입력한 후에는 `저장`을 한번 클릭해 준다. 심사 제출은 어플리케이션을 빌드하고 업로드한 후, 출시될 때에 사용할 binary를 선택해야 진행할 수 있다.

## 스튜디오로 어플리케이션 빌드하기

[Appcelerator 다큐멘테이션](http://docs.appcelerator.com/platform/latest/#!/guide/Distributing_iOS_apps)에서는 [스튜디오](http://www.appcelerator.com/platform/appcelerator-studio/)를 이용해서 어플리케이션을 빌드하고 패키징하는 방법을 안내한다. 하지만 내가 이 방법을 이용하려 했을 때에는 오류가 발생하면서 빌드가 되지 않았다. [iOS 기기로 테스트 할 때](/blog/2015/08/26/deploy-titanium-app-to-appstore-pt-2/)와 마찬가지로 이는 나뿐만 아니라 다른 사용자들도 경험하고 있는 문제인데, 이 역시도 신속하게 해결이 되어야 할 것이다.

## CLI로 어플리케이션 빌드하고 업로드 하기

Appcelerator 다큐멘테이션에서는 언급되지 않지만, iOS 앱 스토어 배포를 위해 어플리케이션을 빌드할 때에도 [CLI](https://en.wikipedia.org/wiki/Command-line_interface)를 이용할 수 있다. CLI를 이용하기 위해서는 [터미널](https://en.wikipedia.org/wiki/Computer_terminal#Emulation)을 실행하고 프로젝트의 위치로 이동하여 다음 명령어를 입력한다.

``` bash
$ titanium build -p ios -b -f -T dist-appstore
```

명령을 입력한 후에는 앱이 빌드된 후 [Xcode](https://developer.apple.com/kr/xcode/index.html)가 실행될 것이다. Titanium 프로젝트가 Xcode Archive로 성공적으로 빌드되었다면 해당 archive를 선택한 후 `Validate...`를 클릭하여 업로드 과정에서 오류가 발생할지에 대한 검사를 실행한다. 아무런 문제도 발생하지 않았다면 `Submit to App Store...` 버튼을 클릭하여 업로드를 시작하면 된다. 업로드 과정은 개발자 정보를 선택하고 앱 정보를 확인한 후에 모두 자동으로 진행된다. 

Xcode에서 binary들을 모두 업로드한 후에는 다시 웹 브라우저에서 iTunes Connect의 어플리케이션 페이지로 이동한다. 이 때 앱의 `빌드` 항목을 확인해보면 빌드를 Xcode에서 업로드했음에도 새로운 빌드를 선택할 수 없을텐데, 이는 아직 업로드 과정이 완전하게 끝나지 않았기 때문이다. 나의 경우에는 약 20분 정도를 기다린 후에 나타난 `+` 버튼을 통해 빌드를 추가할 수 있게 되었다. 빌드까지 선택을 마친 후에는 어플리케이션을 제출하여 심사를 기다리면 된다. 애플의 앱 심사에서 아무런 문제도 발견되지 않고 앱을 배포해도 되겠다는 판단이 내려진다면 자신이 개발한 앱을 iOS 앱 스토어에서 다운로드 받을 수 있게 될 것이다.

* [Titanium 프로젝트 테스트하고 배포하기(iOS): Certificates, Identifiers & Profiles](/blog/2015/08/24/deploy-titanium-app-to-appstore-pt-1/)  
* [Titanium 프로젝트 테스트하고 배포하기(iOS): 어플리케이션 빌드하여 테스트하기](/blog/2015/08/26/deploy-titanium-app-to-appstore-pt-2/)


