---
title: "GitHub Pages 블로그 댓글 기능 추가"
date: "2023-03-23 20:35:00 +0900"
tags: [github, github-pages, jekyll, minimal-mistakes]
---
GitHub Pages 블로그에 댓글을 달 수 있는 기능을 추가합니다.

## utterances

[Configuration - Minimal Mistakes](https://mmistakes.github.io/minimal-mistakes/docs/configuration/#comments) 문서의 Comments 항목을 보면 댓글을 지원하는 다양한 공급자들을 볼 수 있습니다.

일단 공급자 선택의 기준을 세워보겠습니다.

- 광고가 추가되지 않아야 합니다.
- 알림을 통해 댓글이 달렸는지 확인할 수 있어야 합니다.
- 댓글을 편하게 관리할 수 있어야 합니다.
- 블로그의 테마에 어울리게 댓글의 색상이나 디자인을 조정할 수 있어야 합니다.
- 제공자가 사라질 확률이 없어야 합니다.

위의 모든 조건을 만족하는 댓글 기능을 제공하는 공급자는 GitHub에서 지원하는 utterances로 몇 가지 특징이 있습니다.

- 댓글은 GitHub의 Public repository의 Issues에 기록됩니다.
- GitHub 계정에 로그인해야 댓글을 남길 수 있습니다.
- 마크다운으로 댓글을 달 수 있습니다.

## utterances 댓글 Repository 생성

utterances는 댓글을 GitHub의 지정한 Repository에 저장합니다.

GitHug Pages는 경우에 따라 Private으로 전환할 수도 있기 때문에 댓글 전용 Repository를 적당한 이름(BlogComment 등)에 Public으로 만듭니다.

## utterances 설치

- [GitHub Apps - utterances](https://github.com/apps/utterances) 링크를 클릭 한 후 `Install`을 클릭합니다.
- utternaces를 모든 Repository에 설치할 Repository를 다음과 같이 선택하고 `Install`을 클릭합니다.

![GitHub Pages utterances 설치](/assets/images/github-pages-blog-install-utternaces.png)
- 다음에 설정을 하는 화면이 나오는데 Minimal Mistakes 테마를 사용할 경우 `_config.yml` 파일에서 설정합니다.

```yml
repository               : "frontgamevb/BlogComments"
comments:
  provider               : "utterances" # false (default), "disqus", "discourse", "facebook", "staticman", "staticman_v2", "utterances", "giscus", "custom"
  utterances:
    theme                : "github-light" # "github-light" (default), "github-dark"
    issue_term           : "pathname" # "pathname" (default)

defaults:
  - scope:
    values:
      comments: true
```

이제 모든 내용을 GitHub에 올리고 배포가 완료되기를 기다리면 댓글을 입력할 수 있습니다.