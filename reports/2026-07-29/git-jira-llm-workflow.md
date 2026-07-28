# Git·Jira 연동 LLM 워크플로와 사내 품질지식 활용 조사 — 2026-07-29

> **조사 방식**: last30days v3.11.1로 2026-06-28~2026-07-28 공개 자료를 수집하고, GitHub·Atlassian 공식 문서를 배경 자료로 교차검토했다.
> **공개 자료 범위**: Reddit 8건, YouTube 2건, TikTok 8건, Instagram 10건, Hacker News 28건, GitHub 25건, Digg 31개 클러스터. X는 인증하지 않아 제외했다.
> **보안 경계**: 일반화한 공개 검색어만 외부로 전송했다. 사내 사양서, TestCase, 결함이력, 저장소 및 브라우저 쿠키는 조사에 사용하지 않았다.
> **주의**: 소셜 조회수와 반응 수는 관심도이지 품질 또는 생산성의 증거가 아니다. 사내 문서 RAG와 Qwen 2.5 7B의 효과는 회사 환경에서 별도로 검증해야 한다.

## 요약

이번 조사에서 확인된 가장 현실적인 패턴은 `이슈 → 계획 → 작은 코드 변경 → 자동 검사 → PR → 사람 승인`이다. 최근 GitHub 사례에서도 이슈 추적 링크와 여러 AI 리뷰 봇이 한 PR에 연결됐다. 그러나 AI가 결함을 정확히 발견했다는 정량 근거는 확인되지 않았다.

귀사에 적합한 구조는 로컬 소형 모델이 사양·TestCase·결함·Git 변경의 관련 근거를 찾고 구조화한 뒤, 결정적 규칙과 테스트가 사실을 검증하고, 충돌이 남은 사례만 사람 또는 승인된 Enterprise LLM이 최종 판단하는 방식이다.

## 관찰된 워크플로

### 1. Jira 이슈를 실행 가능한 계약으로 사용

이슈를 바로 코드 생성 명령으로 넘기지 않는다. 관련 사양 ID, acceptance criteria, 허용 변경 범위, 검증 명령, 금지 사항과 완료 조건을 먼저 구조화한다. Atlassian은 Jira 이슈의 컨텍스트로 계획을 만들고, 사용자가 계획을 검토한 후 코드·시험·PR로 진행하는 흐름을 제시한다.

- 배경 자료: [Rovo Dev](https://www.atlassian.com/software/rovo-dev)
- 배경 자료: [Rovo Dev in Jira](https://www.atlassian.com/blog/announcements/rovo-dev-in-jira)
- 상태: `PROJECT-CLAIM` — Atlassian이 설명한 제품 워크플로이며 독립 성과 검증은 아님

### 2. PR에는 좁은 자동 검토자를 여러 개 배치

최근 GitHub PR 사례에는 이슈 `LIM-201` 링크와 CodeRabbit, Gitar 등 여러 봇이 함께 나타났다. 이는 단일 범용 에이전트보다 이슈 연결, 변경 요약, 리뷰를 분리하는 운용이 실제로 쓰이고 있음을 보여준다. 다만 해당 PR만으로 리뷰 정확도나 결함 감소를 입증할 수는 없다.

- 최근 30일 관찰: [Limen-Neural/kinetic-signals PR #39](https://github.com/Limen-Neural/kinetic-signals/pull/39)
- 상태: `OBSERVED` — 도구 연결은 직접 관찰, 효과는 미검증

### 3. AI 리뷰는 승인자가 아니라 1차 필터

GitHub Copilot code review도 최종 승인 대신 comment review를 남기며, 저장소 지침과 경로별 지침을 사용하도록 설계돼 있다. 회사 환경에서도 LLM은 테스트 누락, 주석 불일치, 기존 패턴 위반과 관련 없는 리팩터링을 지적하되 merge와 결함 종결은 사람이 맡아야 한다.

- 배경 자료: [GitHub Copilot code review](https://docs.github.com/en/copilot/how-tos/copilot-on-github/use-copilot-agents/copilot-code-review)
- 상태: `OBSERVED` — 공식 기능 동작, 실제 팀의 품질 개선 폭은 별도 측정 필요

### 4. Git과 지식 데이터베이스의 역할을 분리

최근 r/LLMDevs에서는 Git을 에이전트 데이터베이스로 사용하자는 제안이 관심을 받았으나, 높은 지지를 받은 반론은 JSON blob 증가와 Git 확장성 문제를 지적했다. Git은 코드·규칙·프롬프트·평가셋의 변경 이력에 사용하고, 사양·시험·결함 관계 및 검색 인덱스는 SQLite/PostgreSQL 같은 데이터 저장소에 두는 편이 타당하다.

- 최근 30일 관찰: [Git을 에이전트 DB로 사용하는 제안과 토론](https://www.reddit.com/r/LLMDevs/comments/1v0aw41/i_stopped_building_a_database_for_my_ai_agents/)
- 상태: `OBSERVED` — 공개 토론의 주장과 반론, 성능 비교 실험은 없음

### 5. 에이전트 메모리와 외부 도구는 공격면

최근 소셜 자료에서는 코딩 도우미의 장기 메모리와 저장소 전체 탐색이 악성 문서 또는 오염된 컨텍스트의 영향을 확대할 수 있다는 경고가 상위 신호로 나타났다. 문서 원문은 명령이 아니라 비신뢰 데이터로 취급하고, 네트워크 호출·Jira 쓰기·Git push는 별도 권한과 승인으로 통제해야 한다.

- 최근 30일 관찰: [AI coding assistant memory 보안 경고](https://www.tiktok.com/@thom.code/video/7667474359463742742)
- 상태: `UNVERIFIED` — 관심도 높은 소셜 설명이며 원 취약점 보고서 교차검증 필요

## 귀사 자료를 이용한 우선 아이디어

### 1순위: 변경 영향 리포트

입력은 Jira 이슈 또는 PR diff와 제품·버전이다. 출력은 관련 사양, 영향 TestCase, 유사 결함, 과거 해결 방식, 변경 예상 모듈, 충돌 및 사람이 확인할 질문이다. 모든 문장은 원문 ID와 링크를 가져야 한다.

### 2순위: 사양·TestCase 커버리지 검사

사양 요구사항과 TestCase의 precondition, stimulus, expected result를 연결해 누락, 삭제된 기능, 단위·경계값 충돌을 찾는다. 숫자·ID·단위는 규칙 엔진으로 비교하고 LLM은 표현이 다른 의미 대응 후보만 만든다.

### 3순위: 유사 결함 및 재발 방지 검색

신규 결함을 증상, 발생 조건, 로그 시그니처, 모듈, root cause, 해결 방식으로 나눠 과거 결함과 비교한다. 단일 유사도 점수 대신 어떤 축이 유사한지 근거를 표시한다.

### 4순위: 결함 종료 품질 게이트

root cause, 해결 유형, commit/PR, regression TestCase와 영향 제품 기록이 존재하는지 검사한다. LLM은 초안과 누락 후보를 만들고 결함 종결은 사람이 승인한다.

## 권장 역할 분담

| 단계 | 권장 실행 주체 | 외부 토큰 |
|---|---|---:|
| 문서 파싱, ID·숫자·단위 추출 | 결정적 로컬 코드 | 0 |
| 하이브리드 검색, 후보 분류·요약 | Qwen 2.5 7B급 로컬 모델 | 0 |
| 컴파일, 테스트, lint, 정적분석 | 기존 검증 도구 | 0 |
| 사양 충돌에 대한 대안 비교 | 승인된 Enterprise LLM, 필요 시 | 최소 |
| 사양 변경, 결함 종결, merge | 담당자 | 0 |

## 회사 PC PoC 검증 항목

RTX 3070급 8 GB VRAM과 64 GB RAM을 기준으로 7B 4-bit 모델을 후보로 삼되, 다음을 회사 PC에서 측정하기 전에는 충분하다고 단정하지 않는다.

- 관련 사양 검색 Recall@5
- 유사 결함 Top-3 적중률
- TestCase 누락 탐지율과 오탐률
- 존재하지 않는 ID 또는 근거를 만드는 비율
- 개발자 검토시간의 전후 차이
- 외부 LLM으로 escalation되는 비율
- VRAM, RAM, 디스크, 초기 구동시간, 처리량 및 동시성

## 판단

`INFERRED`: 최근 30일 자료는 이슈와 PR 사이에 AI 리뷰·요약 자동화를 배치하는 패턴을 지지한다. 그러나 제품사양서·TestCase·결함이력을 Qwen 2.5 7B로 연결했을 때의 품질과 비용 절감은 공개 자료에서 직접 확인하지 못했다. 따라서 첫 도입은 읽기 전용 변경 영향 리포트로 제한하고, 내부 평가셋에서 검색 정확도와 허위 근거율을 측정한 뒤 PR comment 초안과 Jira comment 초안으로 확대하는 것이 가장 안전하다.

후속 검토: [과거 결함 검색용 Operational Memory Retrieval 도입 검토와 auto-grill](operational-memory-retrieval-auto-grill.md)

---

*생성: last30days v3.11.1 공개 자료 조사 + 공식 문서 교차검토 · 조사 기간: 2026-06-28 ~ 2026-07-28 · 관찰 시점: 2026-07-29 KST*
