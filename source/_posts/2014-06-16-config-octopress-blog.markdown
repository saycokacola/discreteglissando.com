---
layout: post
title: "Octopress 블로그의 설정"
date: 2014-06-16 21:22
comments: true
external-url:
categories: [technology, octopress]
---

{% img /images/octopress.png %}

[Octopress](http://octopress.org/)의 설정은 비교적 간단하게 할 수 있도록 되어있는데, 대부분의 경우 Octopress 디렉토리 밑의 `Rakefile`과 `_config.yml`을 변경하여 설정을 수행한다. `Rakefile`에서는 주로 [Rsync를 이용하여 서버로 블로그의 소스를 올리는 것](http://hwanho.net/blog/2014/06/16/deploy-octopress-with-rsync/)에 대한 설정을 다루게 되고, 블로그 자체의 설정은 `_config.yml`을 변경해서 진행한다.

<!--more-->

`_config.yml`은 크게 세 개의 구간으로 나뉘어서 설정을 하게 되어있다. 

## 기본 설정(Main Configs)

```
# ----------------------- #
#      Main Configs       #
# ----------------------- #

url:                # For rewriting urls for RSS, etc
title:              # Used in the header and title tags
subtitle:           # A description used in the header
author:             # Your name, for RSS, Copyright, Metadata
simple_search:      # Search engine for simple site search
description:        # A default meta description for your site
date_format:        # Ruby의 date strftime 신텍스를 이용한 날짜 서식
subscribe_rss:      # Url for your blog's feed, defauts to /atom.xml
subscribe_email:    # Url to subscribe by email (service required)
category_feeds:     # Enable per category RSS feeds (defaults to false in 2.1)
email:              # Email address for the RSS feed if you want it.
```

만약에 블로그가 여러 명의 저자가 공유하는 블로그인 경우에는, 위의 설정 중 `author` 항목을 회사 또는 프로젝트의 이름으로 지정하고 각자의 포스트에 저자 정보를 추가하는 방법을 쓰는 방법을 사용할 수도 있다.

## Jekyll과 플러그인(Jekyll & Plugins)

이 구간의 설정들은 [Jekyll](https://github.com/jekyll/jekyll)과 Octopress 플러그인들에 관련되어 있다. Jekyll에 익숙하지 않은 경우에는 이곳의 설정들은 변경하지 않는 것이 권장된다.

```
# ----------------------- #
#    Jekyll & Plugins     #
# ----------------------- #

# If publishing to a subdirectory as in http://site.com/project set 'root: /project'
root:               # Mapping for relative urls (default: /)
permalink:          # Permalink structure for blog posts
source:             # Directory for site source files
destination:        # Directory for generated site files
plugins:            # Directory for Jekyll plugins
code_dir:           # Directory for code snippets (for include_code plugin)
category_dir:       # Directory for generated blog category pages
 
pygments:           # Toggle python pygments syntax highlighting
paginate:           # Posts per page on the blog index
pagination_dir:     # Directory base for pagination URLs eg. /blog/page/2/
recent_posts:       # Number of recent posts to appear in the sidebar 

default_asides:     # Configure what shows up in the sidebar and in what order
blog_index_asides:  # Optional sidebar config for blog index page
post_asides:        # Optional sidebar config for post layout
page_asides:        # Optional sidebar config for page layout
```

블로그의 permalink가 표시되는 방법을 바꾸고 싶다면 [Jekyll의 permalink 문서](http://jekyllrb.com/docs/permalinks/)를 참고하기 바란다.

## 외부 플러그인 설정(3rd Party Settings)

`_config.yml` 파일에는 다음의 외부 플러그인을 사용할 수 있도록 미리 준비가 되어 있다. 간단한 설정 사항만 입력하면 추가적인 설치 없이 바로 사용할 수 있다.

* 깃허브  
* 트위터  
* 구글+1
* 핀보드  
* 딜리셔스  
* 디스쿠스  
* 구글애널리틱스
* 페이스북  




