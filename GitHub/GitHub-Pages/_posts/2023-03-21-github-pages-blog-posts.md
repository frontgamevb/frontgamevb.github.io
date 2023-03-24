---
title: "GitHub Pages 블로그 포스트 올리기"
date: "2023-03-21 19:22:00 +0900"
tags: [github, github-pages, jekyll, minimal-mistakes]
---
GitHub Pages에 포스트를 작성하고 올립니다.

## 파일명

루트 폴더에 `_posts` 폴더를 생성하고 파일명을 다음과 같은 형식으로 작성하고 파일을 만듭니다.

```
년-월-일-제목.md
```
월과 일이 한자리일 경우 앞에 0을 붙여 두자리로 만듭니다. 이 글의 파일명은 다음과 같습니다.

```
2023-03-21-github-pages-blog-posts.md
```

## 머리말 (Front Matter)

포스트는 항상 머리말로 시작해야 합니다. 머리말에 생략된 설정은 `_config.yml` 파일의 `defaults` 설정을 따릅니다.

```yml
---
# _layouts 폴더에 있는 layout 파일 중 하나를 선택합니다.
layout: single

# 글 제목입니다.
title: "GitHub Pages 블로그 포스트 올리기"

# 글 작성일입니다. +0900은 대한민국 시간대입니다.
date: "2023-03-21 19:22:00 +0900"

# 글의 마지막 수정일입니다.
# last_modified_at: "2023-03-21 19:20:00 +0900"

# 카테고리입니다. 생략 가능합니다.
categories: [GitHub, GitHub-Pages]

# 태그입니다. 생략 가능합니다.
tags: [github, github-pages, jekyll, minimal-mistakes]
---
```

## 카테고리 설정

위의 머리말 설정 중 `categories`는 다른 방법으로 대체할 수 있는데 `_post` 폴더를 루트가 아닌 다른 폴더에 생성한 후 포스트를 올리면 `_post`에 올린 글들은 카테고리가 자동으로 설정이 됩니다.

예를 들어 위의 예제의 카테고리는 `GitHub/GitHub-Pages/_post` 폴더에 포스트를 올리면 카테고리를 생략해도 자동으로 동일한 카테고리가 설정됩니다.

머리말에 카테고리를 설정하는 것보다 폴더를 이용한 카테고리 설정 방법을 사용하기 바랍니다.

## 마크다운 문서 작성

이제 위의 예제에서 코멘트와 카테고리를 제외하면 기본적인 머리말은 다음과 같습니다. 머리말 이후 마크다운 글을 작성하면 됩니다.

```yml
---
title: "GitHub Pages 블로그 포스트 올리기"
date: "2023-03-21 19:22:00 +0900"
tags: [github, github-pages, jekyll, minimal-mistakes]
---
```

> __Info:__
> 이제 블로그를 운영하기 위한 최소한의 세팅이 완료되었습니다. 첫 포스트를 작성하고 GitHub에 올려보기 바랍니다. 
{: .notice--success}

> __Info:__
> 현재 마크다운 문법은 표준화되지 못하고 여러 버전으로 나누어져 있는데 Jekyll은 `Kramdown`이라는 버전을 지원합니다. `Kramdown` 문법은 [Kramdown(마크다운)-사용법](http://gjchoi.github.io/env/Kramdown(%EB%A7%88%ED%81%AC%EB%8B%A4%EC%9A%B4)-%EC%82%AC%EC%9A%A9%EB%B2%95/) 링크를 참고하기 바랍니다.
{: .notice--success}

> __Info:__
> Minimal Mistakes에서 추가적으로 `Buttons`나 `Notices` 등의 추가적으로 화면을 꾸밀 수 있는 기능을 제공합니다. [Utility Classes - Minimal Mistakes](https://mmistakes.github.io/minimal-mistakes/docs/utility-classes/) 링크를 참고하기 바랍니다.
{: .notice--success}

포스트 예제는 [GitHub Pages 블로그 포스트 올리기](https://gist.githubusercontent.com/frontgamevb/1e7363d9f9593348daa48fb49faddac1/raw/8c4cc2bc9009c5c3f9a3594705252a1bc1baa253/2023-03-21-github-pages-blog-posts.md) 링크를 클릭하면 이 글의 마크다운 포스트 문서를 확인할 수 있습니다.

## 참고

- [포스트 - Jekyll](https://jekyllrb-ko.github.io/docs/posts/)