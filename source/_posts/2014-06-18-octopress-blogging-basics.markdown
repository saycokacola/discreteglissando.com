---
layout: post
title: "Octopress 블로깅의 기초"
date: 2014-06-18 23:08
comments: true
external-url:
categories: [technology, octopress]
---

{% img /images/octopress.png %}

## 블로그 포스트

[Octopress](http://www.octopress.org/)의 포스트는  모두 Octopress 디렉토리 밑의 `source/_posts` 디렉토리 안에 `YYYY-MM-DD-post-title.markdown`의 형식으로 저장되어야 한다. 파일의 이름에서 포스트의 이름에 해당되는 부분은 url slug에서 사용되고, 날짜는 파일 식별과 배열 순서 결정에 사용된다. 

<!--more-->

Octopress에는 다음과 ​같이 포스트의 제목을 입력하면 알맞은 형식의 [마크다운](http://en.wikipedia.org/wiki/Markdown) 파일을 생성해주는 `rake` 명령이 있다.

``` shell-session
$ rake new_post["My Post Title"]
$ # Creates source/_posts/2014-06-18-my-post-title.markdown
```

`rake new_post` 명령어를 이용하여 파일을 생성할 때는 기본적으로 `markdown` 확장자로 파일 만들어지게 되는데 다른 확장자를 사용하고 싶다면 `Rakefile`에서 설정을 변경하는 것이 가능하다.

파일을 생성한 후 텍스트 에디터로 파일을 열어보면 다음 같은 [YAML](http://en.wikipedia.org/wiki/YAML) 설정 사항들이 보일 것이다.

``` text
---
layout: post
title: "My Post Title"
date: 2014-06-18 23:08
comments: true
external-url
categories:
---
```

여기에서 댓글의 허용 여부를 바꾸고 카테고리를 추가할 수 있다. 만약에 여러 명의 저자가 공동으로 운영하는 블로그를 사용하고 있다면 `author: Your Name`을 추가하여 자신의 이름을 해당 포스트의 저자로 설정할 수 있다. 포스트를 아직 완성하지 않아서 `rake generate` 명령어를 사용했을 때 포스팅되는 것을 막고 싶다면 `published: false`를 추가하면 된다. [linklog](http://en.wikipedia.org/wiki/Linklog) 스타일의 포스트를 작성하고 싶을 때에는 `external-url` 항목에 해당 url을 추가해주면 된다.

카테고리의 경우 한 개 또는 여러 개를 추가할 수 있다.

``` text
# 카테고리 한 개 예시
categories: Sass
 
# 카테고리 여러 개 예시 1
categories: [CSS3, Sass, Media Queries]
 
# 카테고리 여러개  예시 2
categories:
- CSS3
- Sass
- Media Queries
```

## 페이지 추가

`source` 디렉토리 밑에 새로운 페이지 파일을 추가하면 [Jekyll](http://jekyllrb.com/)이 자동적으로 파싱을 통해 페이지를 생성한다. 해당 페이지의 url은 페이지 파일의 파일 경로와 일치되도록 생성된다. 예를 들어 `about.markdown`은 `mydomain.com/about.html`로 접속할 수 있게 되고, `about/index.markdown`은 `mydomain.com/about/`로 접속할 수 있게 된다. 포스트의 경우와 마찬가지로 페이지 또한 `rake` 명령을 이용하여 쉽게 생성할 수 있다.

``` shell-session
$ rake new_page[my-page]
  # creates /source/my-page/index.markdown

$ rake new_page[my-page/page.html]
  # creates /source/my-page/page.html
```

새로운 페이지 또한 포스트처럼 기본적으로 사용되는 `markdown` 확장자를 `Rakefile`에서 변경할 수 있고, 텍스트 에디터로 열었을 때 YAML 설정 사항들을 볼 수 있다.

``` text
---
layout: page
title: "My Page"
date: 2014-06-18 23:08
comments: true
sharing: true
footer: true
---
```

페이지에는 카테고리를 설정할 수 없고, 댓글의 허용 여부, 공유 가능 여부, 푸터의 존재 여부를 결정할 수 있다. 페이지에서 날짜를 보고싶지 않다면 해당 YAML을 지우면 된다.

## 소스 생성과 프리뷰

``` shell-session
$ rake generate   # 블로그의 포스트와 페이지를 생성한다.
$ rake watch      # source 디렉토리와 sass 디렉토리의 변화를 감지하여 자동으로 소스를 생성한다.
$ rake preview    # rake watch의 기능을 하면서, http://localhost:4000에 웹서버를 가동하여 블로그를 미리 볼 수 있다.
```

포스트에 `published: false` YAML을 추가한 경우에도 `rake preview`를 실행했을 때에는 로컬 서버에서 포스트를 미리 볼 수 있다.

블로그의 소스를 서버에 올리는 과정은 다음 링크를 참고하길 바란다.

[Rsync를 이용하여 서버에 Octopress 블로그 소스 올리기](/blog/2014/06/16/deploy-octopress-with-rsync/)



