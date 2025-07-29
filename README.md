# 🚀 FastAPI CI/CD with GitHub Actions & DockerHub

이 프로젝트는 FastAPI 애플리케이션을 대상으로  
GitHub Actions를 활용한 **자동 빌드 & DockerHub 배포 파이프라인(CI/CD)**을 구성합니다.

---

## ✅ 주요 구성

| 항목 | 설명 |
|------|------|
| **CI 도구** | GitHub Actions |
| **이미지 빌드** | Docker |
| **이미지 저장소** | DockerHub |
| **트리거 조건** | `main` 브랜치에 Push 시 자동 실행 |

---

## ⚙️ 워크플로우 구성 (`.github/workflows/deploy.yml`)

- main 브랜치에 Push → GitHub Actions 실행
- 프로젝트 소스 코드 checkout
- Docker 환경 설정 및 DockerHub 로그인
- Docker 이미지 빌드 및 푸시

```yaml
name: CI/CD FastAPI Docker

on:
  push:
    branches: [main]

jobs:
  build-and-push:
    runs-on: ubuntu-latest

    steps:
      - name: Checkout code
        uses: actions/checkout@v3

      - name: Set up Docker Buildx
        uses: docker/setup-buildx-action@v3

      - name: Login to DockerHub
        uses: docker/login-action@v3
        with:
          username: ${{ secrets.DOCKER_USERNAME }}
          password: ${{ secrets.DOCKER_PASSWORD }}

      - name: Build and push Docker image
        uses: docker/build-push-action@v5
        with:
          context: .
          push: true
          tags: ${{ secrets.DOCKER_USERNAME }}/fastapi-ci-cd:latest
