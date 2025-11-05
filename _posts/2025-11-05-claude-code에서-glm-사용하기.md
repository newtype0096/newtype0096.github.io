---
layout: post
title: Claude Code에서 GLM 사용하기
date: '2025-11-05 09:18:03 +0900'
image: /assets/img/20251105/claude-code-z-ai-logo.png
category:
- AI
- Claude Code
tags:
- GLM
- Claude Code
- Z.ai
- LLM
---

> Claude Code에서 Z.ai의 GLM 모델을 사용하는 방법에 대해 정리해둔다. (Windows 환경 기준)

### 1. Z.ai 계정 생성하기

먼저 [Z.ai](https://chat.z.ai/)에 접속하여 계정을 생성한다.

![Z.ai 홈페이지](/assets/img/20251105/z-ai-home.png)

### 2. API 키 발급받기

계정 생성이 완료되면, [API 관리페이지](https://z.ai/manage-apikey/apikey-list)로 이동하여 API 키를 발급받는다. `API Keys` 메뉴로 이동하여 새 키를 생성한다. 키 이름은 자유롭게 지정한다.

![Z.ai API 키 발급 화면](/assets/img/20251105/z-ai-api-management.png)

### 3. Claude Code 로그아웃하기

터미널에서 Claude Code를 실행하여 `/logout` 명령어를 입력하여 현재 로그인된 계정에서 로그아웃한다.

### 4. 환경변수 설정하기

PowerShell을 관리자권한으로 실행하고 아래 명령어를 입력해서 환경변수를 등록한다. 위에서 발급한 API 키로 `your_zai_api_key` 부분을 변경한다.

```bash
[System.Environment]::SetEnvironmentVariable('ANTHROPIC_AUTH_TOKEN', 'your_zai_api_key', 'User')
[System.Environment]::SetEnvironmentVariable('ANTHROPIC_BASE_URL', 'https://api.z.ai/api/anthropic', 'User')
```

### 5. Claude Code 모델에 GLM 모델 매핑하기

.claude.json 파일에 아래 내용을 추가한다.

```json
{
    "env": {
        "ANTHROPIC_DEFAULT_HAIKU_MODEL": "glm-4.5-air",
        "ANTHROPIC_DEFAULT_SONNET_MODEL": "glm-4.6",
        "ANTHROPIC_DEFAULT_OPUS_MODEL": "glm-4.6"
    }
}
```

### 6. Claude Code 재실행 및 확인하기

Claude Code를 재실행한 후, `/status` 명령어를 입력하여 GLM 모델이 정상적으로 매핑되었는지 확인한다.

![Claude Code 상태 확인 화면](/assets/img/20251105/claude-code-status.png)