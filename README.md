# 한승윤 (@mmmphyun)

컴퓨터공학을 전공하며 클라우드 인프라와 DevSecOps 엔지니어링 직무를 준비하고 있습니다.  
추측 대신 계측 데이터로 물리적 리소스 제약(대륙 간 200ms 왕복 지연, 1GB RAM 호스트, 176ms 공격 세션)을 해결하고, 불변 데이터 계약과 자동화 하네스로 배포 무결성을 통제합니다.

- 웹 포트폴리오: https://mmmphyun.github.io/security-agent-toolkit/portfolio/
- 기술 블로그: https://mmmphyun.github.io/security-agent-toolkit/blog/
- 연락처: gksdmqdbs@gmail.com

---

## 핵심 프로젝트 요약

| 프로젝트 | 핵심 제약 및 해결 메커니즘 | 실측 성과 | 상세 링크 |
| :--- | :--- | :--- | :--- |
| **CloudShield** | 176ms SSH 공격 세션 비동기 수집 지연 극복, 사후 보안 그룹 전면 교체 및 웹 방화벽 IP 차단 병행 | DynamoDB 3버킷 충돌 0% (P50 36.47ms), 663건 단위·통합 테스트 통과 | [블로그](https://mmmphyun.github.io/security-agent-toolkit/blog/?category=%ED%94%84%EB%A1%9C%EC%A0%9D%ED%8A%B8%2Fcloudshield+%EC%84%9C%EB%B2%84%EB%A6%AC%EC%8A%A4+%EB%B3%B4%EC%95%88+%EC%98%A4%EC%BC%80%EC%8A%A4%ED%8A%B8%EB%A0%88%EC%9D%B4%EC%85%98) |
| **RPG Sync System** | 미국-한국 간 200ms 물리 지연 환경, 커널 TCP Keepalive 설정과 소켓 자가 치유 데코레이터, 15초 Safe TTL 분산 락 | 질의 응답 405ms -> 243ms (인메모리 캐시 16.18ms), 동시 승인 경합 20건 중 오류 0% | [블로그](https://mmmphyun.github.io/security-agent-toolkit/blog/?category=%ED%94%84%EB%A1%9C%EC%A0%9D%ED%8A%B8%2F%EC%8B%A4%EC%8B%9C%EA%B0%84+rpg+%EB%8F%99%EA%B8%B0%ED%99%94+%EC%97%94%EC%A7%84) |
| **PrfVault** | 윈도우 11 WebAuthn PRF 규격 거부 실증, Windows CNG Native Host 구현 및 Rust Wasm 메모리 물리 소거 | 32바이트 대칭키 유도 왕복 검증, 국내 50대 웹 스캔(가상 키패드 6.7% 차단, 길이 제약 엔트로피 20% 손실 규명) | [저장소 (공식 동결)](https://github.com/mmmphyun/PrfVault) |
| **ru-beacon** | 마인크래프트 메인 틱 0ms 격리, Redis Streams 분산 메시지 버스 및 2단계 분산 동시성 제어(Redis Lua 사전 차단 + DB 트랜잭션) | k6 1,000 RPS 버스트 중 99.36% 평균 1.17ms 사전 차단 (초과 발급 0건) | [블로그](https://mmmphyun.github.io/security-agent-toolkit/blog/?category=%ED%94%84%EB%A1%9C%EC%A0%9D%ED%8A%B8%2F%EB%A7%88%EC%9D%B8%ED%81%AC%EB%9E%98%ED%94%84%ED%8A%B8%20%EB%B6%84%EC%82%B0%20%EC%97%B0%EB%8F%99%20%ED%94%8C%EB%9E%AB%ED%8F%BC) |

---

## 기술 스택

- Core: Python (FastAPI, asyncio, Boto3, Pydantic v2, pytest), Linux, Git, GitHub Actions
- Secondary: Docker, AWS (EC2, WAF, DynamoDB), PostgreSQL, Redis, Kotlin, Java
- Research: WebAuthn Level 3 PRF, TPM 2.0, Rust (Wasm, zeroize)

---

## 협업 및 엔지니어링 거버넌스

- **캡스톤 팀 협업 하네스 (aleph-project)**: Pydantic v2 계약 모델 및 디렉터리 수정 제한 CI 가드로 다중 AI 에이전트와 비전공자 협업 시 브랜치 충돌 0건 달성.
- **기술 문서 배포 하네스 (security-agent-toolkit)**: Frontmatter 스키마 검증 및 AST 린팅 파이프라인으로 AI 생성 마크다운 오류 사전 차단.
