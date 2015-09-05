---
layout: post
title: "Titanium 프로젝트 테스트하고 배포하기(iOS): Certificates, Identifiers & Profiles"
date: 2015-08-24 22:01
comments: true
categories: [technology, titanium, ios, development]
---

{% img /images/ios_developer.jpg %}

내가 지금까지 Titanium을 이용해 개발하고 있던 어플리케이션을 어제 완성하여 오늘은 Titanium 프로젝트를 실제 iOS 기기에서 테스트하고, [iOS 앱 스토어](https://en.wikipedia.org/wiki/iOS_App_Store)에 등록하기 위한 과정을 밟게 되었다. [Appcelerator 다큐멘테이션](http://docs.appcelerator.com/platform/latest/#!/guide/Distributing_iOS_apps)에서 안내하는 방법으로는 잘 되지가 않아서 조금 불편하기도 했지만 무사히 마칠 수 있었다.

<!--more-->

## iOS Certificates

iOS 어플리케이션을 개발하고 배포할 때에는 iOS Devolpment Certificate와 iOS Distribution Certificate, 총 두개의 certificate가 필요하다. iOS Devolpment Certificate는 Titanium 프로젝트를 실제 iOS 기기에서 실험할 때, iOS Distribution Certificate는 프로젝트를 배포 가능한 [Xcode](https://developer.apple.com/kr/xcode/) 아카이브로 빌드(build)할 때 사용될 것이다. 이 certificate들은 다음의 과정을 통해 다운로드 받고 설치할 수 있다.[^1]

먼저 [Apple Developer Member Center](https://developer.apple.com/membercenter)에 로그인한 후 `Certificates, Identifiers & Profiles`를 클릭한다. 여러 개의 항목이 나타날 테인데, 이 중에서 `iOS Apps` 밑의 `Certificates`로 이동해야 한다. `Certificates` 페이지에서는 오른쪽 상단의 `+`을 클릭하여 필요한 certificate를 추가한다. 먼저 iOS Devolpment Certificate를 생성하기 위해 `iOS App Development`를 선택한 후, `Worldwide Developer Relations Certificate Authority`를 클릭해 WWDR certificate를 다운로드 받는다. 그 후에는 안내를 따라서 CSR을 생성하고 업로드하여 iOS Devolpment Certificate를 다운로드 받은 후, 파인더에서 다운로드된 .cer 파일을 더블클릭하여 키체인에 설치한다. 이 때 WWDR certificate도 같이 설치해준다. iOS Devolpment Certificate 설치를 마친 후에는 이 과정에서 `iOS App Development`항목 대신에 `App Store and Ad Hoc`를 선택하여 iOS Distribution Certificate도 다운로드 받아서 설치한다.[^2]

## 테스트 기기 등록하기

꼭 거쳐야하는 과정은 아니지만, 컴퓨터에서 실행하는 [iOS Simulator](https://developer.apple.com/library/ios/documentation/IDEs/Conceptual/iOS_Simulator_Guide/)와 실제 iOS 기기의 환경은 다르기 때문에 어플리케이션을 배포하기 전에 실제 기기에서 테스트를 하는 것이 권장된다. 

테스트용 기기들은 `Certificates, Identifiers & Profiles` 페이지에서 등록을 한 후에 테스트 목적으로 사용할 수 있는데, 애플에서는 개발자가 자신의 앱을 연간 100대의 기기에서만 테스트할 수 있도록 제한을 두고있고 한번 등록한 기기는 제거할 수 없기 때문에 많은 기기에서 앱을 테스트할 계획이 있다면 주의해서 기기를 등록하는 것이 좋다. 기기를 등록하기 위해서는 기기의 고유번호인 [UDID](https://www.theiphonewiki.com/wiki/UDID)를 알아야 한다. UDID는 자신의 iOS 기기를 맥에 연결한 후 Xcode를 실행하여 `Window>Devices`에서 확인할 수 있다. 이 UDID는 입력할 때 편하기 위해 클립보드로 복사한다. 

테스트용으로 사용할 기기의 UDID를 확인한 후에는 Apple Developer Member Center에 로그인하여 `Certificates, Identifiers & Profiles`, 이어서 `iOS Apps` 밑의 `Devices`로 이동한다. 해당 페이지에서 오른쪽 상단의 `+` 버튼을 클릭하여 기기의 이름을 지정하고 UDID를 입력하면 iOS 기기에서 자신의 앱을 테스트할 수 있게 된다.

## App ID 생성

App ID는 자신의 어플리케이션의 고유한 등록 번호로, `Certificates, Identifiers & Profiles`에서 `iOS Apps` 밑의 `Indentifiers`로 이동하여 생성할 수 있다. `+`버튼을 클릭한 후 나타나는 생성 페이지에서 앱의 이름을 입력한 후 App ID Suffix를 선택해야 하는데 Explicit App ID와 Wildcard App ID, 두 개의 종류가 있다. 푸시 알림, iAD, Game Center 기능을 사용하는 앱의 경우에는 필수적으로 Explicit App ID를 선택해야 하지만, 그렇지 않은 경우에는 다른 앱을 테스트하거나 등록할 때마다 새롭게 App ID를 생성하지 않고 다시 사용할 수 있는 Wildcard App ID를 선택할 수도 있다. 나의 경우에는 Wildcard App ID를 선택하였다.

## iOS Provisioning Profile

Provisioning Profile은 certificate, 등록된 테스트 기기 목록, App ID를 하나로 묶는 역할을 하는데, 어플리케이션을 iOS 기기에서 테스트할 때는 iOS Development profile, iOS 앱 스토어로 배포할 때는 iOS Distribution profile이 필요하다.

필요한 iOS Provisioning Profile들은 Apple Developer Member Center에 로그인한 후 `Certificates, Identifiers & Profiles`, `iOS AppsProvisioning Profiles`로 이동하면 나타나는 페이지에서 `+`버튼을 클릭하여 생성할 수 있다. iOS Development profile은 iOS App Development을 선택한 다음 사용할 App ID, iOS Devolpment Certificate, 테스트용 기기를 선택하여 profile 이름 입력 후에 생성하고 다운로드 받을 수 있다. 

iOS Distribution profile의 경우, App Store와 Ad Hoc 중 하나를 선택하여 진행해야 한다. iOS 앱 스토어를 통해 앱을 배포할 예정이라면 App Store를 선택해야 하고, 한정된 수의 지정된 기기에만 앱을 설치할 수 있도록 할 예정이라면 Ad Hoc를 선택하면 된다. 나의 경우에는 App Store를 선택한 후 App ID, iOS Devolpment Certificate, profile 이름을 지정하여 profile을 다운로드 받았다.

* [Titanium 프로젝트 테스트하고 배포하기(iOS): 어플리케이션 빌드하여 테스트하기](/blog/2015/08/26/deploy-titanium-app-to-appstore-pt-2/)  
* [Titanium 프로젝트 테스트하고 배포하기(iOS): iOS 앱 스토어로 배포하기](/blog/2015/08/30/deploy-titanium-app-to-appstore-pt-3/)


[^1]: Apple Developer Program 신청을 마친 후에 진행할 수 있다.
[^2]: WWDR certificate는 다시 다운로드 받을 필요가 없다.