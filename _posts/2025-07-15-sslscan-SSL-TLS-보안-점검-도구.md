---
layout: post
title: "[sslscan] SSL/TLS 보안 점검 도구"
date: 2025-07-15 22:06:28 +0900
image: /assets/img/common/sslscan-logo.png
tags:
- sslscan
categories:
- Security
---

국가용 보안요구사항에는 중요 정보 전송 시 권고 암호 알고리즘을 사용해야 한다고 명시되어 있다. 따라서 암호화 통신을 할 때 서버가 지원하는 Cipher Suite를 확인할 필요가 있다. 해당 내용을 간단히 확인할 수 있는 도구가 `sslscan`이다.

## 1. sslscan이란?
`sslscan`은 서버가 지원하는 SSL/TLS 프로토콜 버전, Cipher Suite, 인증서 정보를 빠르게 점검할 수 있는 오픈소스 도구다. 보안 점검, 취약점 진단, 운영 환경의 암호화 설정 검증 등에 널리 활용된다.

## 2. 설치 방법
대부분의 리눅스 배포판에서 패키지 매니저로 간단히 설치할 수 있다.

### Ubuntu/Debian
```bash
sudo apt update && sudo apt install sslscan
```

### CentOS/RHEL
```bash
sudo yum install sslscan
```

### macOS (Homebrew)
```bash
brew install sslscan
```

소스코드로 직접 빌드할 수도 있다. [공식 저장소](https://github.com/rbsec/sslscan) 참고.


## 3. 기본 사용법
가장 기본적인 사용법은 다음과 같다. 
`sslscan` 명령어 뒤에 도메인이나 IP 주소를 입력해서 해당 서버의 SSL/TLS 설정을 점검한다.

```bash
sslscan example.com
```

실행하면 다음과 같은 정보를 확인할 수 있다.
- 서버에서 활성화 중인 SSL/TLS 프로토콜 (예: TLSv1.2, TLSv1.3)
- 지원되는 Cipher 목록 (암호화 알고리즘, 키 교환 방식 등)
- 인증서 정보 (유효기간, 발급자, Subject, SAN 등)
- 취약한 Cipher Suite(예: RC4, 3DES 등) 지원 여부

## 4. 주요 옵션
`sslscan`은 다양한 옵션을 제공한다. 자주 쓰는 옵션은 다음과 같다.

- `--no-failed` : 실패한 테스트(지원하지 않는 프로토콜/암호)는 출력하지 않음
- `--tls1_2` : TLS 1.2만 테스트
- `--tls1_3` : TLS 1.3만 테스트
- `--show-certificate` : 인증서 상세 정보 출력

예시:
```bash
sslscan --tls1_2 --no-failed example.com
```

## 5. 결과 해석 예시
테스트 결과는 다음과 같이 출력된다.

```
Supported Server Cipher(s):
  Accepted  TLSv1.2  256 bits  ECDHE-RSA-AES256-GCM-SHA384
  Accepted  TLSv1.2  128 bits  ECDHE-RSA-AES128-GCM-SHA256
  Rejected  SSLv3    128 bits  RC4-SHA
...
```

- **Accepted**: 서버가 지원하는 암호화 방식
- **Rejected**: 서버가 지원하지 않거나 비활성화된 방식

## 6. 실무 활용 팁
- 보안 요구사항에 따라 취약한 Cipher Suite(예: RC4, 3DES, NULL, EXPORT 등)가 활성화되어 있지 않은지 반드시 확인
- 인증서 유효기간, SAN(Subject Alternative Name) 등도 함께 점검
- PCI DSS, ISMS 등 컴플라이언스 준수 여부 확인 시 유용

## 7. 보안 점검 시 주의사항
- 점검 대상 서버의 운영 환경(서비스 영향, 트래픽 등) 고려
- 최신 버전의 sslscan 사용 권장 (구버전은 TLS 1.3 미지원 등 한계)
- 점검 결과는 보안 정책에 따라 주기적으로 재확인 필요

## 8. 참고 자료
- [sslscan 공식 GitHub](https://github.com/rbsec/sslscan)
- [OWASP SSL/TLS Cheat Sheet](https://cheatsheetseries.owasp.org/cheatsheets/Transport_Layer_Security_Cheat_Sheet.html)
