---
layout: post
title: "한 개의 DigitalOcean VPS에서 여러 개의 도메인 사용하기"
date: 2015-08-09 19:39:55 +0900
comments: true
categories: technology
---

{% img /images/digitalocean.png %}

지금까지 나의 블로그에서 [hwanho.net](hwanho.net)이라는 도메인만을 사용했지만 얼마 전에 [discreteglissando.com](discreteglissando.com), [discreteglissando.co.kr](discreteglissando.co.kr), [discreteglissando.kr](discreteglissando.kr), 이렇게 세 개의 도메인을 추가로 구입하고, 블로그에서 그 도메인들도 사용하기 위한 작업을 오늘 진행하였다.

<!--more-->

내가 현재 블로그의 서버로 사용하고 있는 [VPS](https://en.wikipedia.org/wiki/Virtual_private_server)의 제공사인 [DigitalOcean](https://www.digitalocean.com/)의 사이트를 이용하니 굉장히 쉽게 한 VPS에 여러 개의 도메인을 연결할 수 있었다. 처음 VPS에 도메인을 연결할 때처럼 도메인의 [DNS](https://en.wikipedia.org/wiki/Name_server)를 DigitalOcean의 네임 서버로 변경하고, `A Record` 또는 `AAAA Record`로 자신의 드롭렛과 도메인을 연결하면 된다. `www`가 추가된 등의 부도메인(subdomain)를 추가할 때에는 `CNAME Record`를 이용하면 된다.

위의 과정을 도메인별로 반복하여, 오늘부터는 내 블로그를 [hwanho.net](hwanho.net), [discreteglissando.com](discreteglissando.com), [discreteglissando.co.kr](discreteglissando.co.kr), [discreteglissando.kr](discreteglissando.kr), 네 개의 도메인을 통해 접속할 수 있게되었다.