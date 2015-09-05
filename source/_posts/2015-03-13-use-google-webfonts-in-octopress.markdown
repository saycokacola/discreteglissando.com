---
layout: post
title: "Octopress에서 구글 웹폰트 사용하기"
date: 2015-03-13 20:40:54 +0900
comments: true
categories: [technology, octopress] 
---

{% img /images/octopress.png %}

[구글](http://en.wikipedia.org/wiki/Google)에서 서비스하고 있는 [구글 웹폰트](http://www.google.com/fonts)는 웹개발과 웹사이트 사용에 유용하게 쓰이고 있다. 한글 폰트 또한 [early access](http://www.google.com/fonts/earlyaccess)를 통하여 사용할 수 있는데 나의 Octopress 블로그에도 적용하여 보기로 하였다.
구글에서 제공하는 웹폰트는 무료로 자유로운 이용이 가능한 폰트들인 [나눔 글꼴](http://hangeul.naver.com/font)과 [제주 서체](http://www.jeju.go.kr/index.jeju?menuCd=DOM_000000302008006000&sso=ok), 그리고 [KoPub 서체](http://www.kopus.org/Biz/electronic/Font.aspx) 등에 기반하여 제작된 것이다.
비교적 최근에 발표된 공개 폰트인 [나눔바른고딕](http://hangeul.naver.com/2014/nanum) 폰트는 아직 구글에서 제공하지 않으므로 [깃허브](http://github.com)에 공개된 [웹폰트](https://github.com/hiun/NanumBarunGothic)를 이용했다.

<!--more-->

블로그에서 웹폰트를 사용하기 위해서는 먼저 다음과 같이 `source/_includes/custom/head.html`에서 폰트를 로딩해야 한다.

``` html
⋮
⋮
<link rel="stylesheet" type="text/css" href="http://fonts.googleapis.com/earlyaccess/nanumgothic.css">
<link href='https://cdn.rawgit.com/openhiun/hangul/14c0f6faa2941116bb53001d6a7dcd5e82300c3f/nanumbarungothic.css' rel='stylesheet' type='text/css'>
```

폰트를 로딩한 후에는 Octopress 디렉토리 밑의 `sass/custom/_styles.scss`를 다음과 같이 변경해야 한다. Octopress에서 한글 폰트와 함께 다른 영어 폰트를 사용하고자 할 때에는 두 개의 폰트를 지정하는 순서가 중요하다. Octopress에서는 먼저 지정된 폰트를 적용한 후에, 그 폰트가 적용되지 않은 글자에 두 번째로 지정된 폰트를 적용하기 때문에 영어 폰트를 먼저 지정한 후에 한글 폰트를 지정해야 한다. 나의 경우에는 영어 폰트로는 Open Sans를, 한글 폰트로는 나눔바른고딕을 사용하였다.

``` scss
⋮
⋮
body {
    font-family: 'Georgia', serif; font-size: 17px; color: #000;
    max-width: 750px;
    padding-left: 0.5em;
    padding-right: 0.5em;

    a:hover { color: #3b185f; background: #f9f8fa; }

    > header {
        background: #FFFFFF;
        padding-top: .5em;
        h1 {
            a, a:visited, a:hover {
                color: #8C8C8C;
                font-family: "Nanum Gothic";
            }
        }
    }
⋮
⋮
}
⋮
⋮
#content {
    ⋮
    ⋮
    h1 {
            a {
                font-weight: 400;
                font-family: "Open Sans", "Nanum Gothic";
            }

            a:hover {
                text-decoration: none;
                font-family: "Open Sans", "Nanum Gothic"
            }
        }
    }

    .hentry {
        h1.entry-title {
            font-weight: 400;
            font-size: 2.2em;
            font-family: "Open Sans", "Nanum Gothic";
        }
    }

}
⋮
⋮
div.entry-content p, ul, ol{
    font-family: "Open Sans", "Nanum Barun Gothic";
    text-align: justify;
}
div.entry-content img{
    margin-left: auto;
    margin-right: auto;
    display: block;
}
```

