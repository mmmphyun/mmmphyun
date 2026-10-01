# 한승윤 (`@mmmphyun`)

컴퓨터공학 전공 4학년으로, 클라우드 인프라 및 DevSecOps 엔지니어링 직무를 준비하고 있습니다.  
무료 인프라나 단일 노드의 자원 한계, 해외 리전 간 네트워크 지연(RTT), 보안 규격 제약 속에서 발생하는 병목을 측정하고 코드로 해결하는 과정에 집중합니다.

---

## 프로젝트

### 1. [aleph-project (CloudShield)](https://github.com/mmmphyun/aleph-project)
**클라우드 침해사고 대응 SecOps 파이프라인 (부트캠프 캡스톤 4인 팀 / 시나리오 검증 단계)**
- **담당**: 조장, 아키텍처 설계, 비전공자 협업용 AI 하네스 구축, 차단 엔진 개발
- **문제**: 단일 SSH 무차별 대입 공격 세션이 176ms 만에 종료되어 실시간 인라인 패킷 차단이 불가능함.
- **해결**: CloudWatch Logs 비동기 배치를 수신해 DynamoDB 슬라이딩 윈도우 원자적 카운터로 집계하고, 임계치 도달 즉시 L4 보안그룹 격리와 L7 WAF IP 차단을 멱등하게 적용.
- **주요 기술**: `Python`, `AWS WAFv2`, `Security Group`, `DynamoDB`, `Pydantic v2`, `Moto`

### 2. [rpg_sync_project](https://github.com/mmmphyun/rpg_sync_project)
**단일 노드 환경 실시간 분산 동기화 시스템 (개인 실운영 서비스 / 벤치마크 완료)**
- **내용**: 디스코드 봇 실시간 서비스 운영 및 최적화
- **문제**: 미국 GCP 단일 노드(1GB RAM)와 한국 Supabase DB 간 200ms 물리 지연 및 유휴 연결 종료 빈발.
- **해결**:
  - `SELECT 1` 검증이 유발하는 지연 누적을 없애고 소켓 상태를 직접 검사하며 자동 1회 재연결 데코레이터 적용.
  - 무거운 백그라운드 프로세스 대신 안전 만료 시간(15초)과 명시적 해제를 결합한 Redis 분산 락으로 메모리 부담 없이 경쟁 상태 해결.
  - 동기 DB 호출을 `asyncio.to_thread`와 전용 스레드 풀로 격리해 비동기 이벤트 루프 지연 차단.
- **주요 기술**: `Python`, `FastAPI`, `discord.py`, `Redis`, `PostgreSQL`, `GCP VM`

### 3. [PrfVault](https://github.com/mmmphyun/PrfVault)
**WebAuthn PRF 기반 하드웨어 바인딩 로컬 볼트 아키텍처 (보안 표준 연구 및 프로토타입)**
- **내용**: W3C 표준 명세 분석 및 TPM 2.0 하드웨어 키 유도 프로토타입 구현
- **중점**: 중앙 서버 없이 기기 TPM 2.0 또는 Secure Enclave의 WebAuthn Level 3 PRF 확장 규격을 활용해 암호키 직접 유도.
- **엔지니어링**: Rust Wasm 메모리 소거(`zeroize`) 강제로 암호키 잔류 위험 차단, STRIDE 위협 모델링, 국내 비표준 웹 보안 솔루션 간섭 벤치마크 설계.
- **주요 기술**: `WebAuthn PRF`, `Rust (Wasm)`, `Chrome MV3`, `AES-GCM`, `HKDF`, `Playwright`

### 4. [ru-beacon](https://github.com/mmmphyun/ru-beacon)
**이벤트 기반 분산 워크플로우 플랫폼 (아키텍처 검증 완료 후 비용 최적화 전환)**
- **내용**: 외부 게임 서버와 커뮤니티 연동 플랫폼 백엔드 설계
- **중점**: 외부 게임 서버의 메인 틱 지연을 완전히 분리하고 대규모 이벤트를 안전하게 처리하는 분산 메시지 버스 설계.
- **엔지니어링**: Redis Streams 메시지 버스, KEDA 기반 이벤트 주도 워커 자동 확장, 2단계 Lua 검증 로직 적용.
- **핵심 기술**: `Kotlin`, `Ktor`, `Redis Streams`, `PostgreSQL`, `K3s`, `KEDA`

---

## 사용 기술

- **주력 언어**: `Python` (비동기 I/O, FastAPI, Pydantic v2, 단위·통합 테스트)
- **데이터 및 런타임**: `PostgreSQL`, `Redis`, `Docker`
- **인프라 및 환경**: `Linux / Shell`, `Git`, `Cloud (GCP VM 실운영 / AWS 캡스톤 실습)`

---

## 협업 및 개발 도구

- **AI 협업 거버넌스**: 비전공자 팀원의 모듈 침범을 차단하고, 모의 데이터와 Pydantic 계약 모델을 기반으로 병렬 개발을 보장하는 CI/CD 하네스 구축.
- **디자인 레퍼런스 엔진 (`init-design-reference`)**: AI 프론트엔드 코드 생성 시 디자인 규칙 일탈과 컴포넌트 파편화를 방지하는 디자인 토큰 규칙화 도구.
- **기술 문서 자동화 파이프라인**: GitHub Actions와 외부 API를 결합한 기술 블로그 배포 및 지식 관리 파이프라인 자동화.
