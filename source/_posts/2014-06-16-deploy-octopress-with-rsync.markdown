---
layout: post
title: "rsync를 이용하여 서버에 Octopress 블로그 HTML 파일 올리기"
date: 2014-06-16 19:33
comments: true
external-url:
categories: [technology, octopress]
---

{% img /images/octopress.png %}

[Octopress](http://octopress.org/)를 이용하여 블로그 사이트를 운영할 때 [GitHub Pages](https://pages.github.com/)를 이용할 수도 있고, [Heroku](https://www.heroku.com/)와 같은 클라우드 플랫폼을 이용할 수도 있으며, 서버 호스팅 혹은 개인 가상 서버 서비스를 이용할 수도 있다. 독립된 서버를 사용하면서 데스크탑에서 블로그 소스를 작성한 뒤 생성된 HTML과 관련 파일들을 서버에 올릴 때에 [rsync](https://rsync.samba.org/)를 이용하면 매우 편리하다.

<!--more-->

우선 Octopress 디렉토리 밑의 `Rakefile`을 열어서 rsync deploy 설정을 해주어야 한다. 이 때 중요한 것은 서버의 `~/.ssh/authorized_keys` 파일에 해당되는 기기의 [퍼블릭 키](http://en.wikipedia.org/wiki/Public-key_cryptography)가 저장되어 있어야 한다는 것이다.

``` 
## -- Rsync Deploy config -- ##
# Be sure your public key is listed in your server's ~/.ssh/authorized_keys file
ssh_user       = "user@.mydomain.com"
ssh_port       = "22"
document_root  = "~/website.com/"
rsync_delete   = true
rsync_args     = ""  # Any extra arguments to pass to rsync
deploy_default = "rsync"
```

설정을 마친 후에 터미널에서

``` shell-session
$ rake generate
$ rake deploy
```

를 실행하면 Octopress의 `public` 디렉토리가 서버의 도큐먼트 루트로 싱크된다.
