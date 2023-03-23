---
title: "GitHub Pages 블로그 태그, 카테고리 화면 추가"
date: "2023-03-23 14:10:00 +0900"
tags: [github, github-pages, jekyll, minimal-mistakes]
---
GitHub Pages 블로그에 태그와 카테고리를 지원하는 화면을 추가합니다.

## 태그 화면 추가

- 루트에 `_pages` 폴더가 없을 경우 생성하고 `tag-archive.md` 파일을 생성합니다.
- 아래의 코드를 입력합니다.

```yml
---
title: "태그 목록"
permalink: /tags/
layout: tags
author_profile: true
---
```
- 이제 포스트의 태그를 클릭하면 아래 화면처럼 해당 태그가 포함된 포스트들을 보여줍니다.

![GitHub Pages 포스트 태그 클릭](/assets/images/github-pages-click-posts-tag.png)

## 태그 목록 화면 링크 추가

포스트에 있는 태그 링크를 클릭하지 않고 사이드바나 상단에 항상 태그 목록 화면으로 이동할 수 있게 태그 링크를 추가하겠습니다.

`_data/navigation.yml` 파일(이전 `Quick-Start Guide` 링크를 삭제했던 파일)을 열고 다음과 같이 수정합니다.

```yml
# main links
main:
  - title: "태그"
    url: /tags/
```

이제 상단 우측에 `태그` 링크가 생성되었습니다. 클릭하면 태그 목록 화면으로 이동합니다.

## 카테고리 화면 추가

- `_pages` 폴더에 `category-archive.md` 파일을 생성합니다.
- 아래의 코드를 입력합니다.

```yml
---
title: "카테고리 목록"
layout: categories
permalink: /categories/
author_profile: true
---
```
- 이제 포스트의 카테고리를 클릭하면 해당 카테고리가 포함된 포스트들을 보여줍니다.

## 카테고리 목록 사이드바에 추가

카테고리에 쉽게 접근할 수 있게 사이드바에 카테고리를 추가하겠습니다.

`config.yml`의 `defaults` 설정에 다음과 같이 사이드바에 네비게이션을 추가합니다.

```yml
# Defaults
defaults:
  - scope:
    values:
      sidebar:
        # title: "카테고리"
        nav: sidebar-category
```

`_data/navigation.yml`에 실제 카테고리의 링크를 추가합니다.
> __Warning:__
> 향후 새로운 카테고리를 만들때 마다 `_data/navigation.yml` 파일에 추가해야 합니다.
{: .notice--warning}

```yml
sidebar-category:
  - title: GitHub
    url: /categories/#github
    children:
      - title: GitHug-Pages
        url: /categories/#github-pages
```

`defaults` 설정의 `values`에 추가한 설정은 포스트의 기본값으로 포스트에만 적용되기 때문에 포스트를 보지 않을 경우에는 사이드바에 카테고리가 존재하지 않습니다.

항상 사이드바에 카테고리가 있게 하기 위해 `index.html`에 다음과 같이 사이드바 네비게이션을 추가합니다.

```yml
---
layout: home
author_profile: true
sidebar:
  # title: "카테고리"
  nav: sidebar-category
---
```

이제 화면의 우상단에 태그 목록 화면 링크가 주가되었고 사이드바에 카테고리 링크가 추가되었습니다. 포스트의 태그와 카테고리도 정상 작동합니다.

![GitHub Pages 태그, 카테고리 추가](/assets/images/github-pages-tag-category.png)

## 참고

- [Layouts - Minimal Mistakes](https://mmistakes.github.io/minimal-mistakes/docs/layouts/#archive-layout)
- [Layout: Sidebar with Navigation List](https://mmistakes.github.io/minimal-mistakes/layout-sidebar-nav-list/)