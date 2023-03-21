---
layout: single
title: "GitHub Pages 사이트 만들기"
date: "2023-03-21 14:10:00 +0900"
tags: [github, github-pages]
---
## About GitHub Pages

GitHub에서 제공하는 정적 사이트 호스팅 서비스로 데이터베이스나 서버를 다룰 수 없기 때문에 간단한 웹사이트 제작에 알맞습니다.

GitHub Pages의 사용 제한은 다음과 같습니다.

- 상업적 거래 웹 사이트의 무료 웹 호스팅 서비스로 사용할 수 없습니다.
- GitHub Pages 사이트는 1GB를 초과할 수 없습니다.
- GitHub Pages 사이트는 매월 100GB의 네트워크 대역폭 제한이 있습니다.

## Repository 생성

- GitHub에 로그인한 후 `New repository`를 클릭해 Repository를 생성합니다.
- `Repository name`을 `Owner.github.io` 형식으로 입력해야 GitHub Pages로 설정됩니다.  
  예를 들어 Owner가 `frontgamevb`이면 `frontgamevb.github.io`가 되겠죠.
- `Description`에 웹 사이트 설명을 간단하게 입력합니다.
- `Create repository`를 클릭해 Repository 생성을 완료합니다.
- 이제 이 Repository에 올리는 마크다운, HTML 파일은 `https://Owner.github.io`에서 웹 페이지로 볼 수 있습니다.
- Repository에 올린 파일은 일정 시간이 지나야 웹 페이지로 볼 수 있으니 올린 후 곧바로 나오지 않는다고 당황하지 말고 몇 분 정도 기다리기를 바랍니다.

> __Warning__  
> GitHub Free 계정 사용자는 Repository를 `Public`으로만 설정할 수 있기 때문에 GitHub Pages의 모든 소스 코드가 공개됩니다. 소스 코드 공개를 원하지 않을 경우 계정을 유료로 업그레이드 하기 바랍니다.
{: .notice--warning}

## 웹사이트 꾸미기

GitHub Pages에는 기본적으로 Jekyll이 내장되어 있습니다. Jekyll은 Markdown과 HTML 파일을 읽어서 포함되어 있는 Liquid 템플릿 언어를 번역한 후 결과물을 HTML 파일로 생성합니다. 서버 사이드 프로그래밍이 불가능한 대신 템플릿 언어를 이용해 동적으로 HTML 파일을 생성하는 것을 지원하는 것이죠.

Jekyll이 있다고 해도 웹사이트의 모든 것을 직접 작성하는 것은 힘든 일입니다. GitHub Pages의 Jekyll을 다양하게 꾸밀 수 있는 많은 테마가 있습니다. 다음 글에서는 이 테마 중 하나를 선택하여 GitHub Pages에서 블로그를 운영하는 방법을 알려드리겠습니다.

## 참고

- [GitHub Pages 설명서](https://docs.github.com/ko/pages)