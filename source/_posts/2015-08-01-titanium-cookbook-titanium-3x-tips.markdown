---
layout: post
title: "타이타늄 모바일 앱 프로그래밍과 현재의 iOS 개발"
date: 2015-08-01 23:12:27 +0900
comments: true
categories: [technology, ios, titanium, development]
---

{% img /images/titanium_alloy.jpg %}

몇달 전부터 모바일 애플리케이션 개발을 공부하기 위해 Titanium을 공부하고 있다. [Packt](https://www.packtpub.com/)에서 출판된 보이들리 플렌타인의 "타이타늄 모바일 앱 프로그래밍"이라는 책을 보며 공부하고 있는데, 이 책은 출판된지가 오래되어 현재의 [iOS](https://en.wikipedia.org/wiki/IOS) 앱 개발에 있어서 조금 맞지 않는 부분들이 있다.

<!--more-->

처음에 시작할 때에 책에 적힌대로 따라했더니 앱의 모양이 제대로 나오지 않아서 당황스러웠다. 알아보니, 책이 출판된 이후 새로운 버전의 [아이폰](https://www.apple.com/kr/iphone/)들이 출시되면서 아이폰의 화면 픽셀 비율이 다양해진 것이 원인이었다. 이 문제를 해결하기 위해서는 [애플](https://en.wikipedia.org/wiki/Apple_Inc.)의 [Objective-C](https://en.wikipedia.org/wiki/Objective-C)와 [Swift](https://en.wikipedia.org/wiki/Swift_programming_language)에서도 쓰이고 잇는 `auto` 사이징 기능을 사용해야 한다. 예를 들어 다음과 같은 예제를

``` javascript
var win1 = Ti.UI.createWindow({
    width: 320
    height: 480,
    top: 0,
    left: 0,
    backgroundImage: 'background.png'
    });
```

를 이렇게 바꾸면 된다.

``` javascript
var win1 = Ti.UI.createWindow({
    width: 'auto',
    height: 'auto',
    top: 0,
    left: 0,
    backgroundImage: 'background.png'
    });
```

또한 책의 예제들을 똑같이 따라했을 때 [iOS 7](https://en.wikipedia.org/wiki/IOS_7) 전과 후의 앱 스타일이 혼합되어 있는듯한 결과물이 나왔는데, 이도 역시 이 책이 쓰여졌을 당시와 현재의 환경이 다르기 때문에 생기는 현상이다. 책의 예제들에서는 다음과 같이 윈도우(window)보다 너비와 높이가 각각 40 픽셀씩 작은 뷰(view)를 생성하여 그것에 모든 UI 컨트롤을 올리게 되어있지만

``` javascript
var view = Ti.UI.createView({
    widht;300,
    height: win1.height = 40,
    left: 10,
    top:10,
    blackgroundColor: '#fff',
    borderRadius: 5
    });
```

요즈음에는 [미너멀리스틱](https://en.wikipedia.org/wiki/Minimalism)하고 깔끔한 디자인을 위해서 뷰는 쓰이지 않는다. 실제로 내가 뷰를 제거하고 윈도우에 직접 UI 컨트롤을 올렸더니 요즘 볼 수 있는 디자인에 가까운 앱이 실행되었다. 책에서 제공하는 소스코드에 포함된 로고들이 현재의 디자인과 다른 예전 디자인이라는 문제도 있다. 이는 iOS 7 이후의 앱들을 위한 아이콘을 무료로 다운로드 받을 수 있는 사이트들을 이용하면 해결할 수 있다. 나는 [icons8](https://icons8.com/)과 [iconBeast Lite](http://www.iconbeast.com/free/)를 이용하고 있다.
