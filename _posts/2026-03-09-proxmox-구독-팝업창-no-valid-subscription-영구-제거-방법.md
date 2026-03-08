---
layout: post
title: "[Proxmox] 구독 팝업창(No valid subscription) 영구 제거 방법"
date: '2026-03-09 00:20:50 +0900'
image: /assets/img/common/proxmox-logo.png
category:
- Open Source
- Proxmox
tags:
- Proxmox
---

> Proxmox를 설치하면 구독 팝업창이 나타나는데, 이를 제거하는 방법에 대해 정리해둔다.

### 1. 개요
Proxmox는 오픈소스 기반이라 무료로 사용이 가능하지만, 기본적으로 유료 기업용(Enterprise) 저장소가 바라보게 설정되어 있어 구독 키가 없으면 이 알림이 발생한다. 매번 `OK`를 누르기 귀찮다면, 터미널 명령어 한 줄로 이 팝업을 영구적으로 비활성화할 수 있다.

![](/assets/img/20260309/no-valid-subscription-popup.png)

### 2. 자바스크립트 파일 수정

```bash
sed -Ezi.bak "s/(Ext.Msg.show\(\{\s+title: gettext\('No valid subscription'\),)/void\(\{ \/\/\1/g" /usr/share/javascript/proxmox-widget-toolkit/proxmoxlib.js
```