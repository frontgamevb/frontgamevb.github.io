---
layout: single
title: "GitHub Pages 블로그 포스트 올리기"
date: "2023-03-21 19:22:00 +0900"
# last_modified_at: "2023-03-21 19:20:00 +0900"
tags: [github, github-pages, jekyll, minimal-mistakes]
---
이전 글에서 기본적인 설정이 마무리된 만큼 포스트를 작성하고 올리는 방법을 설명하겠습니다.

## 파일명

루트 폴더에 `_posts` 폴더를 생성하고 파일명을 다음과 같은 형식으로 작성하고 파일을 만듭니다.

```
년-월-일-제목.md
```
예를 들면 이글의 파일명은 다음과 같습니다.

```
2023-03-21-github-pages-blog-posts.md
```
여기서 주의할 점은 월 또는 일이 한 자리일 경우에도 앞에 0을 붙여 두 자리로 만들어야 합니다.

## 머리말 (front-matter)

```md
---
# Jekyll 테마가 지원하는 layout입니다.
# Jekyll 설치 후 따로 테마를 설치하지 않았다면 layout으로 post를 설정하면 되나
# 현재 사용하고 있는 minimal-mistakes 테마는 layout으로 single을 설정하면 됩니다.
layout: single

# 글 제목입니다.
title: "GitHub Pages 블로그 포스트 올리기"

# 글 작성일입니다.
date: "2023-03-21 19:22:00 +0900"

# 글의 마지막 수정일입니다.
# last_modified_at: "2023-03-21 19:20:00 +0900"

# 카테고리입니다. 생략 가능합니다.
categories: [GitHub, GitHub-Pages]

# 태그입니다. 생략 가능합니다.
tags: [github, github-pages, jekyll, minimal-mistakes]
---
```

위의 머리말 설정 중 `categories`는 다른 방법으로 대체할 수 있는데 `_post` 폴더를 루트가 아닌 다른 폴더에 생성한 후 포스트를 올리면 `_post`에 올린 글들은 카테고리가 자동으로 설정이 됩니다.

예를 들어 위의 예제의 카테고리는 `GitHub\GitHub-Pages\_post` 폴더에 포스트를 올리면 카테고리를 생략해도 자동으로 동일한 카테고리가 설정됩니다.

머리말에 카테고리를 설정하는 것보다 폴더를 이용한 카테고리 설정 방법을 사용하기 바랍니다.

이제 위의 예제에서 코멘트와 카테고리를 제외하면 기본적인 머리말은 다음과 같습니다. 머리말 이후 마크다운 글을 작성하면 됩니다.

```md
---
layout: single
title: "GitHub Pages 블로그 포스트 올리기"
date: "2023-03-21 19:22:00 +0900"
tags: [github, github-pages, jekyll, minimal-mistakes]
---
```

## 참고

- [포스트 - Jekyll](https://jekyllrb-ko.github.io/docs/posts/)