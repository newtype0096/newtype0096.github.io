---
layout: post
title: "[NSIS] Windows용 설치 프로그램 만들기"
date: '2025-11-26 10:15:24 +0900'
image: /assets/img/common/nsis-logo.png
category:
- Installer
- NSIS
tags:
- NSIS
---

> NSIS를 사용하여 Windows용 설치 프로그램을 만드는 방법에 대해 정리해둔다.

### 1. NSIS 다운로드 및 설치

먼저 [NSIS 공식 웹사이트](https://nsis.sourceforge.io/Download)에서 최신 버전의 NSIS 설치 파일을 다운로드하여 설치한다.

![NSIS 홈페이지](/assets/img/20251126/nsis-home.png)

### 2. HM NIS Edit 다운로드 및 설치

설치 스크립트를 쉽게 작성하기 위해 [HM NIS Edit](https://hmne.sourceforge.net/)를 다운로드하여 설치한다.

![HM NIS Edit 홈페이지](/assets/img/20251126/hm-nis-edit-home.png)

### 3. 설치 스크립트 작성하기

HM NIS Edit를 실행하고, 스크립트 작성 마법사를 사용하여 스크립트를 작성한다.

**스크립트 작성 마법사**: 파일 - 스크립트 작성 마법사를 선택한다.

![스크립트 작성 마법사](/assets/img/20251126/script-wizard-1.png)

**프로그램 정보**: 설치 대상 프로그램의 정보를 입력한다.

![프로그램 정보](/assets/img/20251126/script-wizard-2.png)

**설치 옵션**: 설치를 위한 옵션을 선택한다. 설치언어에 Korean이 이미 선택되어있다.

![설치 옵션](/assets/img/20251126/script-wizard-3.png)

**프로그램 디렉토리 및 라이센스**: 설치 대상 디렉토리와 라이센스 파일을 지정한다. 라이센스 파일이 필요없다면 입력창을 비워둔다.

![프로그램 디렉토리 및 라이센스](/assets/img/20251126/script-wizard-4.png)

**프로그램 파일**: 설치할 파일들을 추가한다. 처음에 추가되어 있는 항목은 지우면 된다.

![프로그램 파일](/assets/img/20251126/script-wizard-5.png)

**프로그램 아이콘**: 프로그램 시작메뉴의 및 바로가기를 지정한다.

![프로그램 아이콘](/assets/img/20251126/script-wizard-6.png)

**설치 후 실행**: 설치 완료 후 실행할 프로그램을 지정한다.

![설치 후 실행](/assets/img/20251126/script-wizard-7.png)

**언인스톨러**: 언인스톨러 정보를 지정한다.

![언인스톨러](/assets/img/20251126/script-wizard-8.png)

**마법사 완료**: 체크 박스를 선택하고 완료한다.

![마법사 완료](/assets/img/20251126/script-wizard-9.png)

### 4. 설치 스크립트 컴파일하기
스크립트 작성이 완료되면, 이제 컴파일을 해야한다. HM NIS Edit 상단 메뉴에서 해도 되지만 진행상황을 확인할 수 없다. 따라서 NSIS를 직접 사용한다.

**Compile NSI scripts**: NSIS를 실행하고, 메인메뉴의 `Compile NSI scripts`를 선택한다.

![Compile NSI scripts](/assets/img/20251126/nsis-1.png)

**컴파일 완료**: 컴파일이 완료되면, 아래와 같은 화면이 출력된다.

![컴파일 완료](/assets/img/20251126/nsis-2.png)

**설치 파일 생성**: 컴파일이 완료되면, 스크립트 파일이 위치한 폴더에 설치파일이 생성된다.