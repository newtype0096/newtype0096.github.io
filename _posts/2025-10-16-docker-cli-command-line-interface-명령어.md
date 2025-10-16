---
layout: post
title: "[Docker] CLI(Command Line Interface) 명령어"
date: 2025-10-16 10:28 +0900
image: /assets/img/common/docker-logo.png
category:
- Open Source
- Docker
tags:
- Docker
- CLI
- Command Line Interface
- Command
---

> Docker의 CLI 명령어 몇가지를 정리해둔다.

### 일반 명령어
```bash
# 도커 버전 확인
docker --version

# 도커 정보 확인
docker info

# CLI에서 사용할 수 있는 도커 명령어와 옵션 확인
docker help
```

### 이미지 관련 명령어
```bash
# 로컬에 저장된 도커 이미지 목록 확인
docker images

# Docker Hub 또는 다른 레지스트리에서 이미지를 다운로드
docker pull [이미지 이름]

# 지정된 경로에 있는 Dockerfile을 사용하여 Docker 이미지를 빌드하고 이름으로 태그를 지정
docker build -t [이미지 이름] [경로]

# 이미지를 다른 이름이나 버전으로 태그 지정
docker tag [source 이미지 이름] [target 이미지 이름:태그]

# Docker Hub와 같은 레지스트리에 이미지를 푸시
docker push [이미지 이름]

# ID 또는 이름으로 하나 이상의 이미지를 제거
docker rmi [이미지 이름 또는 ID]
```

### 컨테이너 관련 명령어
```bash
# 실행 중인 컨테이너 목록 확인
docker ps

# 모든 컨테이너(실행 중이거나 중지된)의 목록 확인
docker ps -a

# 새로운 컨테이너를 생성하고 실행
docker run [옵션] [이미지 이름]
    # 주요 옵션
    -d # 백그라운드 실행
    -p [호스트 포트:컨테이너 포트] # 포트 매핑
    --name [컨테이너 이름] # 컨테이너 이름 지정
    -v [호스트 경로:컨테이너 경로] # 볼륨 마운트

# 컨테이너 제거
docker rm [컨테이너 이름 또는 ID]

# 강제 종료 후 컨테이너 제거
docker rm -f [컨테이너 이름 또는 ID]

# 컨테이너 중지
docker stop [컨테이너 이름 또는 ID]

# 컨테이너 시작
docker start [컨테이너 이름 또는 ID]

# 컨테이너 재시작
docker restart [컨테이너 이름 또는 ID]
```

### 컨테이너 내부 명령어
```bash
# 컨테이너 내부에서 명령어 실행
docker exec [컨테이너 이름 또는 ID] [명령어]
    # 예: bash 쉘 접속
    docker exec -it [컨테이너 이름 또는 ID] /bin/bash

# 컨테이너의 로그 확인
docker logs [컨테이너 이름 또는 ID]
    # 주요 옵션
    --follow # 실시간 로그 출력

# 실행 중인 컨테이너에 연결
docker attach [컨테이너 이름 또는 ID]

# 컨테이너 강제 종료
docker kill [옵션] [컨테이너 이름 또는 ID]
    # 주요 옵션
    --signal [신호] # 지정된 신호로 컨테이너 종료
```

### 디버깅 명령어
```bash
# 컨테이너, 이미지 또는 네트워크에 대한 자세한 정보를 표시
docker inspect [ID 또는 이름]

# 실행 중인 컨테이너의 실시간 리소스 사용 통계 표시
docker stats [ID 또는 이름]

# 컨테이너 내부에서 실행 중인 프로세스 표시
docker top [ID 또는 이름]

# Docker 데몬의 실시간 이벤트 스트리밍
docker events
```