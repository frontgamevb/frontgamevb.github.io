---
title: "GitHub Pages 블로그 카테고리 업그레이드"
date: "2023-03-23 18:00:00 +0900"
tags: [github, github-pages, jekyll, minimal-mistakes]
---
GitHub Pages 블로그의 카테고리 기능을 사용하기 업그레이드 합니다.

## 선택한 카테고리의 포스트만 출력

기본적으로 Jekyll에서 제공하는 카테고리 기능은 카테고리를 선택하면 모든 포스트 목록을 출력하고 그 중에 해당 카테고리의 위치를 보여줍니다.

모든 포스트가 100개이고 그 중에 선택한 카테고리의 포스트가 10개여도 100개를 모두 출력하고 그 중에 해당 카테고리의 위치를 보여주기 때문에 비효율적입니다.

선택한 카테고리의 포스트만 출력되는 기능을 추가하겠습니다.

- `pages` 폴더에 `categories` 폴더를 생성합니다.
- 카테고리의 이름을 소문자로 마크다운 파일을 만듭니다.
  예를 들어 현재 이 글은 카테고리가 `GitHub`, `GitHub-Pages`이니 `github.md`, `github-pages.md` 이렇게 2개의 파일을 만들어야 겠죠.
- 아래와 같이 코드를 입력합니다. `title`과 `site.categories.`의 `GitHub`는 카테고리 `permalink`의 `github`는 해당 카테고리로 접속할 주소입니다.

```yml
---
title: GitHub
layout: archive
permalink: /categories/github
author_profile: true
sidebar:
  nav: sidebar-category
---

{% raw %}{% assign posts = site.categories.GitHub %}
{% for post in posts %} {% include archive-oneline.html type=page.entries_layout %} {% endfor %}{% endraw %}
```

- `_includes` 폴더에 `archive-oneline.html` 파일을 만들고 아래의 코드를 추가합니다.

```html
{% raw %}{% if post.header.teaser %}
  {% capture teaser %}{{ post.header.teaser }}{% endcapture %}
{% else %}
  {% assign teaser = site.teaser %}
{% endif %}

{% if post.id %}
  {% assign title = post.title | markdownify | remove: "<p>" | remove: "</p>" %}
{% else %}
  {% assign title = post.title %}
{% endif %}

<div class="{{ include.type | default: 'list' }}__item">
  <article class="archive__item" itemscope itemtype="https://schema.org/CreativeWork">
    <div class="archive-oneline">
      <a href="{{ post.url | relative_url }}" rel="permalink">{{ title }}</a>
      <span class="page__meta">
        <i class="far fa-fw fa-calendar-alt" aria-hidden="true"></i>
        {% assign date_format = site.date_format | default: "%B %-d, %Y" %}
        <time datetime="{{ post.date | date_to_xmlschema }}">{{ post.date | date: date_format }}</time>
      </span>
    </div>
  </article>
</div>{% endraw %}
```
`archive-oneline.html` 파일은 포스트 목록 출력시 포스트 당 최소한 3줄 이상 차지하던걸 발췌를 삭제하고 제목과 일자를 같이 출력하여 포스트 당 한줄만 차지하게 변경하기 위해 사용합니다.

`_sass/minimal-mistakes/skins/_air.scss` 파일에 다음의 코드를 추가해 포스트 목록 사이의 여백을 설정합니다. 다른 스킨을 선택했다면 선택한 스킨 파일에 코드를 추가해야 겠죠.

```css
// 추가
.archive-oneline {
  line-height: 1.8em;
}
```

## 링크 수정

`_data/navigation.yml` 파일의 링크를 수정합니다. `url`의 `#`을 제거하면 됩니다.

```yml
sidebar-category:
  - title: GitHub
    url: /categories/github
    children:
      - title: GitHug-Pages
        url: /categories/github-pages
```

포스트의 카테고리 링크의 `#`도 제거해야 합니다. `_includes/category-list.html` 파일의 `#`을 `nil`로 수정하거나 `assign path_type = nil`만 남겨두고 전부 삭제합니다.

```liquid
{% raw %}{% case site.category_archive.type %}
  {% when "liquid" %}
    {% assign path_type = nil %} <!-- path_type = "#" -->
  {% when "jekyll-archives" %}
    {% assign path_type = nil %}
{% endcase %}{% endraw %}
```

## 수정된 카테고리 화면

아래의 화면과 같이 카테고리를 선택하면 해당 카테고리의 포스트들을 한 줄에 하나씩 출력합니다.

![](/assets/images/github-pages-category-posts.png)

## 카테고리 추가 요약

앞으로 카테고리를 새롭게 추가할 때 해야할 작업을 요약하겠습니다.

- `_pages/categories` 폴더에 이전에 만든 카테고리 파일을 복사합니다.
- 파일명과 `permalink`는 카테고리를 소문자로 입력합니다.
- `title`과 `site.categories.`는 카테고리의 원래 이름대로 입력합니다.
- `_data/navigation.yml` 파일에 링크를 추가합니다.

카테고리를 처음 설정할 때는 복잡한 과정을 거쳤지만 이제는 카테고리를 추가할 때마다 파일 추가와 링크 수정만 하면 됩니다.

태그 또한 동일한 방법으로 업그레이드 할 수 있습니다.

## 참고

- [Layouts - Minimal Mistakes](https://mmistakes.github.io/minimal-mistakes/docs/layouts/#archive-layout)