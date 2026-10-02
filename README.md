# 한승윤 (`@mmmphyun`)

컴퓨터공학 전공 4학년으로, 클라우드 인프라 및 DevSecOps 엔지니어링 직무를 준비하고 있습니다.  
지연 시간과 보안 제약 속에서 시스템 병목을 계측하고, 자동화와 방어적 설계를 통해 운영 안정성을 확보합니다.

- **Tech Blog**: [mmmphyun.github.io/security-agent-toolkit/blog/](https://mmmphyun.github.io/security-agent-toolkit/blog/)
- **Contact**: [gksdmqdbs@gmail.com](mailto:gksdmqdbs@gmail.com)

---

## 프로젝트

### 1. [aleph-project (CloudShield)](https://github.com/mmmphyun/aleph-project)
**클라우드 침해사고 대응 SecOps 파이프라인 | [4인 팀 캡스톤 · 조장 / 시나리오 검증]**
- **과제**: 단일 SSH 무차별 대입 공격 세션이 176ms 만에 종료되어 실시간 인라인 패킷 차단이 불가능함.
- **엔지니어링**: CloudWatch Logs 비동기 배치를 수신해 DynamoDB 슬라이딩 윈도우 원자적 카운터로 집계하고, 임계치 도달 즉시 L4 보안그룹 격리와 L7 WAF IP 차단을 멱등하게 적용.
- **주요 기술**: `Python`, `AWS WAFv2`, `Security Group`, `DynamoDB`, `Pydantic v2`, `Moto`

### 2. [rpg_sync_project](https://github.com/mmmphyun/rpg_sync_project)
**단일 노드 환경 실시간 분산 동기화 시스템 | [개인 프로젝트 · 1인 개발 / 실운영]**
- **과제**: 미국 GCP 단일 노드(1GB RAM)와 한국 Supabase DB 간 200ms 물리 지연 및 유휴 연결 종료 빈발.
- **엔지니어링**:
  - `SELECT 1` 검증 지연을 제거하고 소켓 상태를 직접 검사하며 자동 1회 재연결 데코레이터 적용.
  - 안전 만료 시간(15초)과 명시적 해제를 결합한 Redis 분산 락으로 저사양 환경의 동시성 경합 제어.
  - 동기 DB 호출을 전용 스레드 풀로 격리해 비동기 이벤트 루프 블로킹 차단.
- **주요 기술**: `Python`, `FastAPI`, `discord.py`, `Redis`, `PostgreSQL`, `GCP VM`

### 3. [PrfVault](https://github.com/mmmphyun/PrfVault)
**WebAuthn PRF 기반 하드웨어 바인딩 로컬 볼트 | [개인 연구 · 1인 개발 / 프로토타입]**
- **과제**: 중앙 서버 없는 종단 간 암호화 환경에서 브라우저 메모리 내 암호키 잔류 위험 및 엔드포인트 보안 솔루션 간섭.
- **엔지니어링**: W3C WebAuthn Level 3 PRF 규격으로 기기 TPM 2.0에서 대칭키를 직접 유도하고, Rust Wasm 메모리 소거(`zeroize`) 강제 및 STRIDE 위협 모델링 적용.
- **주요 기술**: `WebAuthn PRF`, `Rust (Wasm)`, `Chrome MV3`, `AES-GCM`, `HKDF`, `Playwright`

### 4. [ru-beacon](https://github.com/mmmphyun/ru-beacon)
**이벤트 기반 분산 워크플로우 플랫폼 | [개인 프로젝트 · 1인 개발 / 아키텍처 검증]**
- **과제**: 외부 게임 서버의 메인 틱 지연을 유발하지 않고 대규모 비동기 이벤트 트래픽을 안정적으로 수용해야 함.
- **엔지니어링**: Redis Streams를 메시지 버스로 채택해 틱 지연을 분리하고, KEDA 기반 이벤트 주도 워커 자동 확장 및 2단계 Lua 원자적 검증 파이프라인 구축.
- **주요 기술**: `Kotlin`, `Ktor`, `Redis Streams`, `PostgreSQL`, `K3s`, `KEDA`

---

## 사용 기술

- **주력 언어**: `Python` (비동기 I/O, FastAPI, Pydantic v2, 단위·통합 테스트)
- **데이터 및 런타임**: `PostgreSQL`, `Redis`, `Docker`
- **인프라 및 환경**: `Linux / Shell`, `Git`, `Cloud (GCP VM 실운영 / AWS 캡스톤 실습)`

---

## 협업 및 엔지니어링 거버넌스

- **캡스톤 팀 협업 하네스 (`aleph-project`)**: 구두 규약이나 사후 리뷰에 의존하는 대신, Git Hook과 Pydantic v2 계약 모델로 모듈 경계를 시스템 레벨에서 강제하여 인터페이스 충돌 없이 Mock 데이터 기반 병렬 개발 파이프라인 구축.
- **기술 문서 배포 하네스 (`security-agent-toolkit`)**: 사후 수동 검수에 의존하지 않고, GitHub Actions에 Frontmatter 스키마 검증과 AST 린팅을 연동해 AI 생성 마크다운의 포맷 파괴를 빌드 단계에서 조기 차단하는 자동 배포 파이프라인 구축.
- **디자인 레퍼런스 엔진 (`init-design-reference`)**: 모호한 자연어 프롬프트 지시 대신, 디자인 토큰과 UI 규칙을 구조화된 레퍼런스로 주입하여 AI 생성 코드의 컴포넌트 파편화와 디자인 시스템 이탈을 방지하는 규격화 도구.
