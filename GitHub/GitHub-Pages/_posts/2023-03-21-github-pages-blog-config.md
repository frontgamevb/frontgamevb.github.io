---
title: "GitHub Pages 블로그 기본 설정"
date: "2023-03-21 14:21:00 +0900"
last_modified_at: "2023-03-21 19:20:00 +0900"
tags: [github, github-pages, jekyll, minimal-mistakes]
---
![Github Pages jekyll 테마 설치](/assets/images/github-pages-theme-installed.png)

위의 테마가 설치된 화면을 다시 보면 `Site Title`, `Your Name` 등 많은 수정해야 할 부분들이 보입니다.

`_config.yml` 파일의 수정을 통해 사이트의 많은 부분을 설정할 수 있습니다. 설정의 중요한 항목들을 설명하겠습니다. 설명한 내용을 보고 `_config.yml` 파일을 수정하기를 바랍니다.

> __Info__  
> Jekyll 서버에서 대부분의 파일의 수정이나 추가는 서버의 재시작 없이 실시간으로 반영이 되지만 `config.yml` 파일의 수정은 반드시 서버를 재시작해야 반영됩니다.
{: .notice--info}

## Site Settings

```yml
# 테마가 사용하는 색상을 선택합니다. 아래의 주소에서 미리보기로 확인할 수 있습니다.
# https://mmistakes.github.io/minimal-mistakes/docs/configuration/#skin
minimal_mistakes_skin    : "air" # "air", "aqua", "contrast", "dark", "dirt", "neon", "mint", "plum", "sunrise"

# 사이트의 주 언어입니다.
locale                   : "ko-KR"

# 사이트의 제목으로 위의 테마가 설치된 화면의 Site Title에 위치할 텍스트입니다.
title                    : "FrontGame's Programming & Optimization"

# 사이트의 제목 아래 적을 부제입니다.
subtitle                 : ".Net Cross Platform Programming & Windows Optimization"

# 사이트의 저자입니다.
name                     : "FrontGame"

# 사이트의 설명으로 검색 엔진에서 사용됩니다.
description              : "닷넷 크로스 플랫폼 프로그래밍과 Autohotkey, Powershell 등 스크립트 언어를 이용한 윈도우 최적화를 다룹니다."

# 사이트의 주소로 도메인을 따로 설정하지 않았다면 GitHub Pages의 주소를 설정합니다.
url                      : "https://frontgamevb.github.io"

# 블로그의 시작 주소를 서브 폴더로 설정할 수 있습니다.
baseurl                  : # the subpath of your site, e.g. "/blog"

# GitHub의 repository를 설정합니다. GitHub Pages가 아니더라도 연결하고 싶은 repository를 설정하면 됩니다.
repository               : "frontgamevb/frontgamevb.github.io"

# 사이트 제목 앞에 보여줄 로고입니다.
logo                     : # path of logo image to display in the masthead, e.g. "/assets/images/88x88.png"

# Site Title 위치에 사이트의 제목인 title의 내용이 아닌 다른 내용이 출력되기를 원할 때 설정합니다.
masthead_title           : # overrides the website title displayed in the masthead, use " " for no title
```

## Site Author

```yml
# Site Author
author:
  # 사이트의 저자입니다.
  name             : "FrontGame"

  # 저자를 나타낼 사진입니다.
  avatar           : # path of avatar image, e.g. "/assets/images/bio-photo.jpg"

  # 소개 글입니다.
  bio              : "Apple II에서 윈도우까지 다양한 플랫폼을 다룹니다."

  # 살고 있는 위치입니다.
  location         : # "대한민국"

  # Email이나 본인의 계정이 있는 사이트들의 링크입니다. icon은 아래 주소에서 검색해서 설정합니다.
  # https://fontawesome.com/icons
  links:
    - label: "Email"
      icon: "fas fa-fw fa-envelope-square"
      url: "mailto:frontgamevb@gmail.com"
    - label: "Website"
      icon: "fas fa-fw fa-link"
      # url: "https://your-website.com"
    - label: "Twitter"
      icon: "fab fa-fw fa-twitter-square"
      # url: "https://twitter.com/"
    - label: "Facebook"
      icon: "fab fa-fw fa-facebook-square"
      # url: "https://facebook.com/"
    - label: "GitHub"
      icon: "fab fa-fw fa-github"
      url: "https://github.com/frontgamevb/"
    - label: "Instagram"
      icon: "fab fa-fw fa-instagram"
      # url: "https://instagram.com/"
```

## 설정 결과 확인

Jekyll 서버를 다시 실행하고 [http://127.0.0.1:4000](http://127.0.0.1:4000) 주소를 클릭하면 결과를 확인할 수 있습니다.

![Github Pages jekyll 테마 설치](/assets/images/github-pages-config-edited.png)

## 참고

- [Configuration - Minimal Mistakes](https://mmistakes.github.io/minimal-mistakes/docs/configuration/)