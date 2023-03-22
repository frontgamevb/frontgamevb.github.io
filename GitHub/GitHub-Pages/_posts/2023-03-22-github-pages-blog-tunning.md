---
title: "GitHub Pages 블로그 꾸미기"
date: "2023-03-22 15:09:00 +0900"
tags: [github, github-pages, jekyll, minimal-mistakes]
---
GitHub Pages 블로그를 꾸밉니다.

## 최근 포스트 화면

![GitHub Pages 최근 포스트](/assets/images/github-pages-recent-posts.png)

포스트를 몇 개 올린 후 홈페이지를 확인하면 위와 같은 결과를 확인할 수 있습니다.

위의 화면을 더 효율적으로 꾸며보겠습니다.

### `Quick-Start Guide` 삭제

맨위 우측 공간은 `_data/navigation.yml` 파일에 있는 링크들을 보여줍니다. 아래처럼 코멘트 처리를 하거나 삭제합니다.

```yml
# main links
main:
  # - title: "Quick-Start Guide"
  #   url: https://mmistakes.github.io/minimal-mistakes/docs/quick-start-guide/
```

### Footer 삭제

아래쪽 Footer는 RSS를 구독할 수 있는 링크를 제외하면 자리만 차지하고 있습니다. RSS 피드는 왼쪽 사이드바의 링크 목록으로 옮기고 Footer를 삭제합니다.

왼쪽 사이드바의 링크 목록은 [GitHub Pages 블로그 기본 설정](http://localhost:4000/github/github-pages/github-pages-blog-config/#site-author) 글에서 다뤘던 글을 참고하여 `_config.yml` 파일 `author`의 `links`에 RSS 피드 링크를 추가하면 됩니다.

```yml
  links:
    - label: "RSS 피드"
      icon: "fas fa-fw fa-rss-square"
      url: "/feed.xml"
```

Footer를 제거하기 위해서는 `_layouts` 폴더의 `default.html` 파일을 수정해야 합니다. 아래와 같이 Footer를 출력하는 부분을 코멘트 처리합니다. 

```html
    <!--
    <div id="footer" class="page__footer">
      <footer>
        { % include footer/custom.html % }
        { % include_cached footer.html % }
      </footer>
    </div>
    -->
```
주의할 점은 Liquid 템플릿 언어의 시작을 나타내는 기호는 코멘트 내에 포함되어 있어도 번역이 되기 때문에 위와 같이 `{ %`, `% }` 식으로 사이에 공백을 넣어 Liquid 템플릿 언어로 인식되지 않게 해야 합니다.

### 타이틀바 색 Footer 색으로 변경

`_sass/minimal-mistakes/skins` 폴더에는 `_config.yml` 파일의 `minimal_mistakes_skin`에 설정한 스킨이 있습니다. 이 글에서는 `_air.scss`를 선택하였기 때문에 `_air.scss` 파일을 수정합니다. 다른 스킨을 설정하였다면 스킨에 해당하는 파일을 수정하면 됩니다.

```css
/* Colors */
$background-color: #eeeeee !default;
$text-color: #222831 !default;
$muted-text-color: #393e46 !default;
$primary-color: #0092ca !default;
$border-color: mix(#fff, #393e46, 75%) !default;
$footer-background-color: $primary-color !default;
$link-color: #393e46 !default;
$masthead-text-color: #fff !default; // 추가
$masthead-link-color: $masthead-text-color !default; // 수정
$masthead-link-color-hover: mix($masthead-text-color, $footer-background-color, 85%) !default; // 수정
$navicon-link-color-hover: mix(#fff, $text-color, 80%) !default;

.page__footer {
  color: #fff !important; // override
}

.page__footer-follow .social-icons .svg-inline--fa {
  color: inherit;
}

// 추가
.masthead {
  background-color: $footer-background-color !important;

  nav {
    background-color: transparent;
  }
}
```
코드 중 코멘트로 추가 또는 수정이라고 표시 되어있는 줄만 자신의 스킨에 추가, 수정하면 됩니다.

여기서 주의할 점은 `$masthead-text-color`의 색상은 아래 `.page__footer`의 `color`와 동일하게 설정해야 한다는 것입니다.

## 최근 포스트 수정 화면

![GitHub Pages 최근 포스트 수정](/assets/images/github-pages-blog-home-edited.png)

이제 최근 포스트 화면이 더 깔끔해 졌습니다.