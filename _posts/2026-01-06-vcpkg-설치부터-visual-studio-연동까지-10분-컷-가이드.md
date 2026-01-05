---
layout: post
title: "[vcpkg] 설치부터 Visual Studio 연동까지 10분 컷 가이드"
date: '2026-01-06 00:44:36 +0900'
image: /assets/img/20260106/vs-vcpkg.png
categories:
- Open Source
- vcpkg
tags:
- vcpkg
---

> <strong>vcpkg로 C++ 라이브러리 지옥 탈출하기!</strong> 설치부터 Visual Studio 자동 연동, 그리고 실제 프로젝트 적용까지 한 번에 끝내는 완벽 가이드를 확인하세요.

C++ 개발을 하다 보면 가장 골치 아픈 게 바로 외부 라이브러리 설정이죠? 저도 예전에는 프로젝트 하나 만들 때마다 헤더 파일 경로 설정하고, 라이브러리 파일 링크하느라 반나절을 다 보낸 적도 있답니다. 😂 "누가 좀 알아서 딱딱 붙여줬으면 좋겠다"라는 생각, 다들 해보셨을 거예요.

그런데 마이크로소프트의 <strong>vcpkg</strong>를 만나고 나서는 이 모든 고민이 사라졌어요! 마치 파이썬의 pip처럼, 명령어 한 줄이면 라이브러리 설치부터 프로젝트 연결까지 마법처럼 해결되거든요. 오늘은 초보자도 10분이면 끝낼 수 있는 <strong>vcpkg 설치 방법과 Visual Studio 연동 꿀팁</strong>을 아주 쉽게 알려드릴게요. 이제 설정 말고 코딩에만 집중해 보자구요! 😊

## <strong>1. vcpkg가 도대체 뭔가요?</strong> 🤔
간단히 말해 <strong>C++용 패키지 관리자</strong>입니다. 마이크로소프트에서 개발했으며, Windows, Linux, macOS를 모두 지원합니다. 가장 큰 장점은 Visual Studio와 함께 사용할 때 빛을 발하는데요, 라이브러리를 설치만 하면 별도의 프로젝트 속성 설정 없이 바로 `#include`해서 사용할 수 있다는 점이에요.

<div style="background-color: #222222; border-left: 4px solid #aaaaaa; padding: 15px; margin: 20px 0; border-radius: 0 8px 8px 0;">
    <strong>💡 알아두세요!</strong><br>
    vcpkg를 사용하려면 기본적으로 <strong>Git</strong>과 <strong>Visual Studio (C++ 워크로드 포함)</strong>가 컴퓨터에 설치되어 있어야 합니다. 아직 설치 전이라면 이 두 가지를 먼저 준비해 주세요!
</div>

## <strong>2. vcpkg 설치하기 (딱 2단계!)</strong> 📊
설치 과정은 정말 간단합니다. 복잡한 인스톨러 없이, 소스 코드를 다운로드하고 스크립트만 실행하면 끝이에요. 차근차근 따라와 보세요.

### <strong>STEP 1: Git 클론 (다운로드)</strong>
먼저 vcpkg를 설치할 폴더를 정합니다. 저는 보통 `C:\dev\vcpkg`나 `C:\vcpkg` 처럼 경로가 짧은 곳을 추천해요. 명령 프롬프트(CMD)나 PowerShell을 열고 해당 폴더로 이동한 뒤 아래 명령어를 입력합니다.

```bash
git clone https://github.com/microsoft/vcpkg
```

### <strong>STEP 2: 부트스트랩 실행</strong>
다운로드가 완료되면 생성된 `vcpkg` 폴더로 들어갑니다. 그리고 설치 스크립트를 실행해 주세요. 이 과정에서 vcpkg 실행 파일(.exe)이 만들어집니다.

```bash
cd vcpkg
.\bootstrap-vcpkg.bat
```

잠시 기다리면 폴더 안에 <strong>vcpkg.exe</strong> 파일이 생긴 것을 볼 수 있을 거예요. 이제 준비 완료입니다!

## <strong>3. Visual Studio와 연동하기 (핵심!) 🧮</strong>
이 부분이 vcpkg의 꽃이라고 할 수 있어요. 이 명령어 한 방이면 앞으로 Visual Studio에서 라이브러리 경로를 설정할 필요가 전혀 없어집니다.

<div style="background-color: #222222; padding: 15px; border-radius: 8px; margin: 20px 0; text-align: center;">
    <h3 style="font-size: 18px; color: #1a73e8; margin: 0 0 10px;"><strong>✨ 마법의 명령어</strong></h3>
    <p style="margin-bottom: 0; font-family: monospace; font-size: 1.1em; font-weight: bold;">.\vcpkg integrate install</p>
</div>

명령어를 입력했을 때 `"Applied user-wide integration for this vcpkg root."`라는 메시지가 뜬다면 성공입니다! 이제 vcpkg로 설치하는 모든 라이브러리는 Visual Studio가 자동으로 인식하게 됩니다. 정말 편하죠?

<div style="background-color: #222222; border-left: 4px solid #f44336; padding: 15px; margin: 20px 0; border-radius: 0 8px 8px 0;">
    <strong>⚠️ 주의하세요!</strong><br>
    혹시 권한 오류가 발생한다면, 명령 프롬프트나 PowerShell을 <strong>'관리자 권한으로 실행'</strong>하여 다시 시도해 보세요.
</div>

## <strong>4. 연동 확인: 실제 프로젝트 만들기 👩‍💼👨‍💻</strong>
설정이 잘 되었는지 확인해봐야겠죠? 아주 유용한 문자열 포맷팅 라이브러리인 `fmt`를 설치하고, Visual Studio에서 바로 사용해 보겠습니다.

<div style="background-color: #222222; padding: 20px; border-radius: 8px; margin: 25px 0; border: 1px solid #222222;">
    <h3 style="font-size: 18px; color: #1a73e8; margin: 0 0 15px;"><strong>🔢 vcpkg 명령어 도우미</strong></h3>
    <p style="font-size: 14px; margin-bottom: 10px;">원하는 작업을 선택하면 명령어를 보여드립니다.</p>
    <div style="display: flex; margin-bottom: 15px; align-items: center;">
        <div style="width: 30%; font-weight: bold;">작업 선택:</div>
        <div style="width: 70%;">
            <select id="actionSelect" style="width: 100%; padding: 8px; border: 1px solid #ddd; border-radius: 4px;">
                <option value="search">라이브러리 검색 (예: fmt)</option>
                <option value="install">라이브러리 설치 (32bit)</option>
                <option value="install64">라이브러리 설치 (64bit)</option>
                <option value="list">설치된 목록 확인</option>
            </select>
        </div>
    </div>
    
    <button onclick="showCommand()" style="background-color: #1a73e8; color: white; border: none; padding: 10px 15px; border-radius: 4px; cursor: pointer; font-weight: bold;">명령어 보기</button>
    
    <div id="commandResultBox" style="margin-top: 20px; padding: 15px; border: 1px solid #ddd; border-radius: 4px; display: none; background-color: #fff;">
        <p style="margin-bottom: 5px;"><strong>입력할 명령어:</strong></p>
        <p id="commandText" style="margin-bottom: 0; font-family: monospace; color: #d63384; font-weight: bold;"></p>
    </div>
</div>
<script>
    function showCommand() {
        const action = document.getElementById('actionSelect').value;
        let command = "";
        
        if (action === "search") {
            command = ".\\vcpkg search fmt";
        } else if (action === "install") {
            command = ".\\vcpkg install fmt";
        } else if (action === "install64") {
            command = ".\\vcpkg install fmt:x64-windows";
        } else if (action === "list") {
            command = ".\\vcpkg list";
        }
        
        document.getElementById('commandText').textContent = command;
        document.getElementById('commandResultBox').style.display = 'block';
    }
</script>

### <strong>테스트 과정</strong>
<ol style="margin: 0 0 15px 20px; padding: 0;">
    <li style="margin-bottom: 8px;"><strong>라이브러리 설치:</strong> 터미널에 <code>.\vcpkg install fmt</code>를 입력하여 설치합니다.</li>
    <li style="margin-bottom: 8px;"><strong>Visual Studio 실행:</strong> 새 'C++ 빈 프로젝트'를 생성합니다.</li>
    <li style="margin-bottom: 8px;"><strong>코드 작성:</strong> <code>main.cpp</code>를 만들고 아래 코드를 붙여넣습니다.</li>
</ol>

```cpp
#include <fmt/core.h>

int main() {
    fmt::print("Hello, vcpkg! 연동 성공! 😊\n");
    return 0;
}
```

별도의 설정 없이 위 코드가 에러 없이 컴파일되고 실행된다면? <strong>축하합니다! 완벽하게 연동된 것입니다.</strong> 이제 복잡한 설정 없이 <code>install</code> 명령어 하나면 어떤 라이브러리든 가져다 쓸 수 있게 되었어요.

## <strong>마무리: 핵심 내용 요약 📝</strong>
오늘 배운 내용을 한 장의 카드로 정리해 드릴게요.

<style>
    .single-summary-card-container {
        font-family: 'Noto Sans KR', sans-serif;
        display: flex;
        justify-content: center;
        align-items: center;
        padding: 20px 10px;
        background-color: #f0f2f5;
        margin: 20px 0;
    }
    .single-summary-card {
        width: 100%;
        max-width: 700px;
        background-color: #ffffff;
        border-radius: 12px;
        box-shadow: 0 6px 18px rgba(0,0,0,0.12);
        padding: 25px;
        display: flex;
        flex-direction: column;
        overflow: hidden;
        border: 1px solid #e0e0e0;
        box-sizing: border-box;
        height: auto;
    }
    .single-summary-card .card-header {
        display: flex;
        align-items: center;
        border-bottom: 2px solid #1a73e8;
        padding-bottom: 12px;
        margin-bottom: 12px;
    }
    .single-summary-card .card-header-icon {
        font-size: 34px;
        color: #1a73e8;
        margin-right: 14px;
    }
    .single-summary-card .card-header h3 {
        font-size: 26px;
        color: #1a73e8;
        margin: 0;
        line-height: 1.3;
        font-weight: 700;
    }
    .single-summary-card .card-content {
        flex-grow: 1;
        display: flex;
        flex-direction: column;
        justify-content: space-around;
        font-size: 17px;
        line-height: 1.65;
        color: #333;
    }
    .single-summary-card .card-content .section {
        margin-bottom: 10px;
    }
    .single-summary-card .card-content strong {
        color: #005cb2;
        font-weight: 600;
    }
    .single-summary-card .card-content .highlight {
        background-color: #fffde7;
        padding: 2px 6px;
        border-radius: 3px;
        font-weight: bold;
    }
    .single-summary-card .card-content .formula {
        background-color: #e8f4fd;
        padding: 6px 10px;
        border-radius: 4px;
        font-size: 0.9em;
        text-align: center;
        margin-top: 5px;
        color: #155724;
    }
    .single-summary-card .card-footer {
        font-size: 14px;
        color: #777;
        text-align: center;
        padding-top: 12px;
        border-top: 1px dashed #ddd;
        margin-top: auto;
    }
    @media (max-width: 768px) {
        .single-summary-card { padding: 18px; }
        .single-summary-card .card-header h3 { font-size: 20px; }
        .single-summary-card .card-content { font-size: 15px; }
    }
</style>

<div class="single-summary-card-container">
    <div class="single-summary-card">
        <div class="card-header">
            <span class="card-header-icon">🚀</span>
            <h3>vcpkg 빠른 시작 요약</h3>
        </div>
        <div class="card-content">
            <div class="section">
                <strong>1. 다운로드:</strong> <code>git clone</code>으로 소스 받기
            </div>
            <div class="section">
                <strong>2. 설치:</strong> <span class="highlight">bootstrap-vcpkg.bat</span> 실행
            </div>
            <div class="section">
                <strong>3. 연동(필수):</strong>
                <div class="formula">.\vcpkg integrate install</div>
            </div>
            <div class="section">
                <strong>4. 사용:</strong> <code>install [라이브러리명]</code> 후 바로 코딩!
            </div>
        </div>
        <div class="card-footer">
            이제 헤더/라이브러리 경로 설정에서 해방되세요!
        </div>
    </div>
</div>

vcpkg 덕분에 C++ 개발 환경 설정이 정말 쾌적해졌죠? 이제 라이브러리 설정 때문에 스트레스받지 마시고, 여러분의 멋진 아이디어를 구현하는 데 집중하시길 바랍니다. 혹시 진행하다가 막히는 부분이 있다면 언제든 댓글로 물어봐 주세요! 😊

## <strong>자주 묻는 질문 ❓</strong>
<div style="margin: 30px 0;">
    <div style="margin-bottom: 20px;">
        <div style="font-weight: bold; margin-bottom: 5px;">Q: 설치했는데 Visual Studio에서 헤더 파일을 못 찾아요.</div>
        <div style="padding-left: 15px;">A: <code>integrate install</code> 명령어를 실행했는지 꼭 확인하세요. 또한, 설치한 라이브러리의 비트수(x86/x64)와 프로젝트의 플랫폼 설정이 일치하는지 확인해야 합니다.</div>
    </div>

    <div style="margin-bottom: 20px;">
        <div style="font-weight: bold; margin-bottom: 5px;">Q: 64비트(x64) 라이브러리는 어떻게 설치하나요?</div>
        <div style="padding-left: 15px;">A: 기본적으로는 x86이 설치됩니다. 64비트용은 패키지 이름 뒤에 <code>:x64-windows</code>를 붙여주세요. (예: <code>.\vcpkg install fmt:x64-windows</code>)</div>
    </div>

    <div style="margin-bottom: 20px;">
        <div style="font-weight: bold; margin-bottom: 5px;">Q: 특정 프로젝트에만 vcpkg를 적용하고 싶어요.</div>
        <div style="padding-left: 15px;">A: 전역 연동(integrate install) 대신, 해당 프로젝트의 솔루션 폴더에 vcpkg를 복사하거나 NuGet 패키지 방식을 활용할 수도 있습니다.</div>
    </div>
</div>

<script type="application/ld+json">
{
    "@context": "https://schema.org",
    "@type": "FAQPage",
    "mainEntity": [
        {
            "@type": "Question",
            "name": "설치했는데 Visual Studio에서 헤더 파일을 못 찾아요.",
            "acceptedAnswer": {
                "@type": "Answer",
                "text": "👉 integrate install 명령어를 실행했는지 꼭 확인하세요. 또한, 설치한 라이브러리의 비트수(x86/x64)와 프로젝트의 플랫폼 설정이 일치하는지 확인해야 합니다."
            }
        },
        {
            "@type": "Question",
            "name": "64비트(x64) 라이브러리는 어떻게 설치하나요?",
            "acceptedAnswer": {
                "@type": "Answer",
                "text": "👉 기본적으로는 x86이 설치됩니다. 64비트용은 패키지 이름 뒤에 :x64-windows를 붙여주세요. (예: .\\vcpkg install fmt:x64-windows)"
            }
        },
        {
            "@type": "Question",
            "name": "특정 프로젝트에만 vcpkg를 적용하고 싶어요.",
            "acceptedAnswer": {
                "@type": "Answer",
                "text": "👉 전역 연동(integrate install) 대신, 해당 프로젝트의 솔루션 폴더에 vcpkg를 복사하거나 NuGet 패키지 방식을 활용할 수도 있습니다."
            }
        }
    ]
}
</script>