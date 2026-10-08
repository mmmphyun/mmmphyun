# 한승윤 (@mmmphyun)

컴퓨터공학을 전공하며 클라우드 인프라·운영 자동화 엔지니어를 준비하고 있습니다.  
지연 시간과 보안 제약 속에서 시스템 병목을 계측하고, 자동화와 방어적 설계를 통해 운영 안정성을 확보합니다.

- 웹 포트폴리오: https://mmmphyun.github.io/security-agent-toolkit/portfolio/
- 기술 블로그: https://mmmphyun.github.io/security-agent-toolkit/blog/
- 연락처: gksdmqdbs@gmail.com

---

## 핵심 프로젝트 요약

| 프로젝트 | 역할 / 기여 | 핵심 제약 및 해결 메커니즘 | 실측 성과 | 링크 |
| :--- | :--- | :--- | :--- | :--- |
| **CloudShield** | 4인 팀장<br>L4·L7 차단 코어 구현 | 176ms SSH 공격 세션 비동기 수집 지연 한계 인정<br>사후 L4 보안그룹 교체 및 L7 WAF 차단 병행 | 15스레드 동시 경합·DynamoDB 3버킷 원자적 누적: 쓰기 유실 0%, P50 쓰기 지연 36.47ms<br>단위·통합 테스트 663건 통과 | [저장소](https://github.com/mmmphyun/aleph-project) · [분석](https://mmmphyun.github.io/security-agent-toolkit/blog/?category=%ED%94%84%EB%A1%9C%EC%A0%9D%ED%8A%B8%2Fcloudshield+%EC%84%9C%EB%B2%84%EB%A6%AC%EC%8A%A4+%EB%B3%B4%EC%95%88+%EC%98%A4%EC%BC%80%EC%8A%A4%ED%8A%B8%EB%A0%88%EC%9D%B4%EC%85%98) |
| **RPG Sync System** | 1인 단독 설계<br>백엔드·인프라 풀스택 | 미국-한국 간 200ms 물리 지연과 1GB RAM 호스트<br>커널 TCP Keepalive 설정 및 소켓 자가 치유 데코레이터 | 쿼리 응답 405.66ms → 243.41ms (캐시 16.18ms)<br>20건 동시 승인 경합 시 오류율 0% | [저장소](https://github.com/mmmphyun/rpg_sync_project) · [분석](https://mmmphyun.github.io/security-agent-toolkit/blog/?category=%ED%94%84%EB%A1%9C%EC%A0%9D%ED%8A%B8%2F%EC%8B%A4%EC%8B%9C%EA%B0%84+rpg+%EB%8F%99%EA%B8%B0%ED%99%94+%EC%97%94%EC%A7%84) |
| **PrfVault** | 1인 단독 연구<br>암호화 코어·호스트 개발 | 윈도우 11 WebAuthn PRF 폐쇄 플랫폼 한계 실증<br>Windows CNG Native Host 및 Rust Wasm 메모리 소거 | 32바이트 하드웨어 대칭키 유도 왕복 검증 완료<br>국내 50대 웹 스캔(가상 키패드 6.7% 자동완성 차단 규명) | [저장소(동결)](https://github.com/mmmphyun/PrfVault) |
| **ru-beacon** | 1인 단독 설계<br>API·워커·플러그인 개발 | 마인크래프트 메인 틱 0ms 격리 및 RDBMS 풀 고갈 방어<br>Redis Streams 비동기 버스 및 Redis Lua 1차 사전 차단 | k6 피크 1,000 RPS에서 요청의 99.36%를 평균 1.17ms에 Fast-Fail<br>선착순 보상 초과 발급(Overselling) 0건 | [저장소](https://github.com/mmmphyun/ru-beacon) · [분석](https://mmmphyun.github.io/security-agent-toolkit/blog/?category=%ED%94%84%EB%A1%9C%EC%A0%9D%ED%8A%B8%2F%EB%A7%88%EC%9D%B8%ED%81%AC%EB%9E%98%ED%94%84%ED%8A%B8%20%EB%B6%84%EC%82%B0%20%EC%97%B0%EB%8F%99%20%ED%94%8C%EB%9E%AB%ED%8F%BC) |

---

## 기술 스택

- Core: Python (FastAPI, asyncio, Boto3, Pydantic v2, pytest), Linux, Git, GitHub Actions
- Secondary: Docker, AWS (EC2, WAF, DynamoDB), PostgreSQL, Redis, Kotlin, Java
- Research: WebAuthn Level 3 PRF, TPM 2.0, Rust (Wasm, zeroize)

---

## 협업 및 엔지니어링 거버넌스

- **캡스톤 팀 협업 하네스 (aleph-project)**: 4인 팀 병렬 개발 시 Pydantic v2 불변 계약과 CI 작업 영역 검사기를 구축하여 **Git 병합 충돌 0건** 달성, 모의 데이터 단절 결함 식별 후 수집·탐지·대응 전 구간 교차 계약 테스트 5종 구축.
- **기술 문서 검수 파이프라인 (security-agent-toolkit)**: 실습 자산과 Frontmatter 스키마 검증, 엔지니어 최종 직접 검수를 결합하여 **37편 배포: 빌드 실패 0건, 라우팅 오류 0건** 유지.
