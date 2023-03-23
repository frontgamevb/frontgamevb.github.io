---
title: "GitHub Pages 블로그 테마 설치"
date: "2023-03-21 14:17:00 +0900"
tags: [github, github-pages, ruby, jekyll, minimal-mistakes]
---
GitHub Pages 사이트에서 블로그를 운영할 수 있게 해주는 블로그 테마를 설치합니다.

## Ruby & Jekyll 설치하기

GitHub Pages에 Jekyll이 내장되어 있지만 알다시피 GitHub에서 직접 코드를 작성하는 일은 불편하고 비효율적이기 때문에 하지 않습니다.
따라서 PC에도 Jekyll이 설치되어 있어야 GitHub로 코드를 올리기 전에 웹 사이트가 어떻게 작동할지 테스트해볼 수 있겠죠.

Jekyll은 Ruby로 작성되었기 때문에 Ruby를 먼저 설치해야 합니다.

- [Downloads (rubyinstaller.org)](https://rubyinstaller.org/downloads/)를 클릭하고 WITH DEVKIT의 첫 번째 버전을 선택하고 설치합니다. 특별한 이유가 없다면 기본 옵션으로 설치하면 됩니다.
- 설치 마법사 마지막에 `rudk install`이 실행되면 아래와 같은 화면이 나오는데 3번을 선택합니다.

```
   1 - MSYS2 base installation
   2 - MSYS2 system update (optional)
   3 - MSYS2 and MINGW development toolchain

Which components shall be installed? If unsure press ENTER [1,3]
```
- 명령 프롬프트에서 아래의 명령을 실행해 JekyII를 설치합니다.

```
gem install jekyll bundler
```

## Repository clone 및 Repository에 jekyll 테마 추가

- 전 글에서 만들었던 Repository의 Clone을 PC의 원하는 위치에 만듭니다.
- 이 글에서는 Jekyll 테마로 `Minimal Mistakes`를 선택하였습니다. 다른 테마를 선택하기를 원한다면 이후의 작업은 선택한 테마의 설정 문서를 참고하기를 바랍니다.
- [Minimal Mistakes Theme](https://github.com/mmistakes/minimal-mistakes/archive/master.zip)를 다운로드 받고 압축을 Clone의 루트 폴더에 해제합니다.
- 필요없는 파일과 폴더를 제거합니다.
  - /.github
  - /docs
  - /test
  - .editorconfig
  - .gitattributes
  - CHANGELOG.md
  - minimal-mistakes-jekyll.gemspec
  - README.md
  - screenshot.png
  - screenshot-layouts.png
- `Gemfile`을 다음과 같이 수정합니다.

```
source "https://rubygems.org"
gem "jekyll"
gem "minimal-mistakes-jekyll"
group :jekyll_plugins do
end
```
- 루트 폴더에서 다음 명령을 실행합니다.

```
bundle
bundle exec jekyll serve
```
> __Info:__
> `bundle exec jekyll serve` 명령은 Jekyll 서버를 실행하는 명령입니다.
{: .notice--info}

- [http://127.0.0.1:4000](http://127.0.0.1:4000) 주소를 클릭하면 테마가 설치된 화면을 확인할 수 있습니다.

![Github Pages jekyll 테마 설치](/assets/images/github-pages-theme-installed.png)

## 참고

- [GitHub Pages 설명서](https://docs.github.com/ko/pages)
- [Jekyll](https://jekyllrb-ko.github.io/)
- [Quick-Start Guide - Minimal Mistakes](https://mmistakes.github.io/minimal-mistakes/docs/quick-start-guide/)