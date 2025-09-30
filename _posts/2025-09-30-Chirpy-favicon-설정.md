---
layout: post
title: Chirpy favicon 설정
date: '2025-09-30 15:43:02 +0900'
image: /assets/img/common/chirpy-logo.png
tags:
- Jekyll
- Blog
- Chirpy
- Favicon
categories:
- GitHub
- Blog
---

> Jekyll의 Chirpy 테마에서 favicon을 설정하는 방법에 대해 정리한다.

### Favicon 이미지 준비
[Real Favicon Generator](https://realfavicongenerator.net/) 사이트를 이용하여 다양한 크기의 favicon 이미지를 생성할 수 있다. 이 사이트에서는 여러 플랫폼에 맞는 아이콘을 한 번에 생성해준다.

### Favicon 설정
`assets/img/favicons/` 디렉토리에 favicon 이미지를 추가한다. favicons 폴더가 없다면 생성한다.

![favicons 폴더](/assets/img/20250930/favicons-folder.png)

### 결과 확인
이제 브라우저에서 확인하면, 설정한 favicon이 정상적으로 표시되는 것을 볼 수 있다.

![브라우저에서의 favicon 확인](/assets/img/20250930/favicon-browser.png)

### 참고
- [Customize the Favicon - Chirpy](https://chirpy.cotes.page/posts/customize-the-favicon/)