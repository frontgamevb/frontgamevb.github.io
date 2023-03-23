---
title: "GitHub Pages 블로그 디자인 수정"
date: "2023-03-23 14:39:00 +0900"
tags: [github, github-pages, jekyll, minimal-mistakes]
---
GitHub Pages 블로그의 글자 크기나 버튼 크기 등 디자인을 수정합니다.

## 글자 크기 수정

`Minimal Mistakes` 테마는 반응형 웹 디자인으로 설계되어 화면의 크기와 비율에 따라 요소들의 배치가 변화하고 글자 크기 또한 변합니다.

`_sass/minimal-mistakes/_reset.scss` 파일에서 아래의 `font-size` 값을 변경하면 화면 크기에 따라 변하는 글자의 크기를 조절할 수 있습니다. 또는 `@include`를 모두 코멘트 처리 하여 글자의 크기를 고정할 수 있습니다.

화면의 크기를 조절해 보면서 원하는 크기로 조절하기 바랍니다.

```css
html {
  /* apply a natural box layout model to all elements */
  box-sizing: border-box;
  background-color: $background-color;
  font-size: 16px;

  @include breakpoint($medium) {
    font-size: 18px;
  }

  @include breakpoint($large) {
    font-size: 18px; /* 20px */
  }

  @include breakpoint($x-large) {
    font-size: 18px; /* 22px */
  }

  -webkit-text-size-adjust: 100%;
  -ms-text-size-adjust: 100%;
}
```

## 사이드바 너비 수정

사이드바의 너비가 화면 크기에 따라 필요 이상 커져 본문의 너비가 좁아질 때가 있습니다. `_sass/minimal-mistakes/_variables.scss` 파일에서 아래의 값들을 수정해서 사이드바의 너비를 조절할 수 있습니다.

화면의 크기를 조절해 보면서 원하는 크기로 조절하기 바랍니다.

```css
$right-sidebar-width-narrow: 200px !default;
$right-sidebar-width: 200px !default; /* 300px */
$right-sidebar-width-wide: 200px !default; /* 400px */
```

## 포스트 링크의 밑줄 제거

아래의 화면을 보면 다른 링크들에는 밑줄이 없는데 오직 포스트 링크에만 밑줄이 있습니다. 이 밑줄을 제거하겠습니다.

![GitHub Pages 최근 포스트 수정](/assets/images/github-pages-blog-home-edited.png)

`_sass/minimal-mistakes/skins/_air.scss` 파일에 다음의 코드를 추가합니다. 다른 스킨을 선택했다면 선택한 스킨 파일에 코드를 추가해야 겠죠.

```css
// 추가
a {
  text-decoration: none;
}
```

이제 모든 종류의 링크에는 밑줄이 없습니다.

## 링크 버튼 테두리 크기 조절

아래의 화면을 보면 태그, 카테고리, 이전, 다음 링크들의 테두리가 필요이상으로 큽니다.

![GitHub Pages 포스트 하단](/assets/images/github-pages-blog-post-bottom.png)

`_sass/minimal-mistakes/_page.scss` 파일에서 다음 코드를 수정하면 태그와 카테고리 링크의 테두리 크기를 조절할 수 있습니다.

```css
.page__taxonomy-item {
  margin-right: 3px; /* 5px */
  margin-bottom: 5px; /* 8px */
  padding: 2px 5px; /* 5px 10px; */
}
```

`_sass/minimal-mistakes/_navigation.scss` 파일에서 다음의 코드를 수정하면 이전, 다음 링크의 테두리 크기를 조절할 수 있습니다.

```css
&--pager {
    display: block;
    padding: 0.5em 1em; /* 1em 2em */
}
```