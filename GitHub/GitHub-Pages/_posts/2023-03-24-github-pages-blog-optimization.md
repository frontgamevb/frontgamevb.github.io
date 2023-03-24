---
title: "GitHub Pages 블로그 최적화"
date: "2023-03-24 13:10:00 +0900"
tags: [github, github-pages, jekyll]
---
GitHub Pages 블로그의 성능을 높이는 방법에 대해 설명합니다.

## Jekyll의 문제점

Jekyll은 오래되고 GitHub애서 정식 지원되는 만큼 많은 테마, 플러그인, 자료들이 있습니다. 한마디로 GitHub Pages에 블로그를 가장 쉽게 구축할 수 있는 정적 사이트 생성기입니다.

그런데 Jekyll은 치명적인 단점을 갖고 있습니다. 바로 문서를 HTML로 변환하는 속도가 매우 느리다는 점입니다. 그래서 문서가 어느 이상 늘어나면 GitHub에 올릴 때 빌드가 실패하는 경우가 발생합니다.

이 문제는 GitHub Actions를 이용하면 해결할 수 있지만 어찌됐던 느린 빌드 속도는 최적화로 줄일 수는 있어도 Jekyll의 베이스가 스크립트 언어인 이상 완전한 해결이 불가능합니다.

## Jekyll 최적화 예제

`_includes/archive-single.html` 파일을 예로 들어보겠습니다.

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
    {% if include.type == "grid" and teaser %}
      <div class="archive__item-teaser">
        <img src="{{ teaser | relative_url }}" alt="">
      </div>
    {% endif %}
    <h2 class="archive__item-title no_toc" itemprop="headline">
      {% if post.link %}
        <a href="{{ post.link }}">{{ title }}</a> <a href="{{ post.url | relative_url }}" rel="permalink"><i class="fas fa-link" aria-hidden="true" title="permalink"></i><span class="sr-only">Permalink</span></a>
      {% else %}
        <a href="{{ post.url | relative_url }}" rel="permalink">{{ title }}</a>
      {% endif %}
    </h2>
    {% include page__meta.html type=include.type %}
    {% if post.excerpt %}<p class="archive__item-excerpt" itemprop="description">{{ post.excerpt | markdownify | strip_html | truncate: 160 }}</p>{% endif %}
  </article>
</div>{% endraw %}
```

위 코드는 홈페이지에서 볼 수 있는 최근 포스트를 나열하는 코드입니다. 포스트별로 제목, 일자, 발췌를 보여줍니다.

```html
{% raw %}<div class="{{ include.type | default: 'list' }}__item">
  <article class="archive__item" itemscope itemtype="https://schema.org/CreativeWork">
    <div class="archive-oneline">
      <a href="{{ post.url | relative_url }}" rel="permalink">{{ post.title }}</a>
      <span class="page__meta">
        <i class="far fa-fw fa-calendar-alt" aria-hidden="true"></i>
        <time datetime="{{ post.date | date_to_xmlschema }}">{{ post.date | date: site.date_format }}</time>
      </span>
    </div>
  </article>
</div>{% endraw%}
```

위 코드는 이전 글에서 다뤘던 코드로 카테고리를 선택했을 때 포스트별로 제목과 일자를 같은 줄에 보여줍니다. 발췌를 출력하지 않는 것을 제외하면 하는 기능은 동일한데 코드가 훨씬 적죠.

코드를 살펴보면 `_includes/archive-single.html` 파일의 코드에는 여러 옵션을 위해 다양한 liquid 코드가 사용되었는데 아래의 코드에서는 사용되지 않는 코드들을 전부 삭제했습니다.

Jekyll의 최적화는 이런식으로 코드에서 최대한 liquid 코드를 제거하는 방식으로 이루어집니다. 당연히 liquid 코드가 적어야 문서의 HTML으로의 변환이 빠르니까요.