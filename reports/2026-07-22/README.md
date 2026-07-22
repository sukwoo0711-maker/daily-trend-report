# 🧰 AI Personal Stack 트렌드 리포트 — 2026-07-22 (TOP 10)

> **조사 방식**: last30days 스킬(v3.16.0) DISCOVERY 스윕(Reddit·HN·Digg 실측 참여도) + 웹 리서치 보강. 조사 윈도우: 2026-06-22 ~ 2026-07-22.
> **범위**: AI Personal Stack 구축에 유용한 것만 — 사용 방법론, 자동화, Skills, MCP, GitHub Rising Star.
> **제외**: 일반 뉴스, 모델 출시 소식, 정책/시장 동향, 에이전틱 브라우저, **최근 7일 내 리포트에서 다룬 항목**.
> **정렬 기준**: 편집 주목도순(성장·참여·규모·스택 중요도를 참고하되 단일 객관 점수로 간주하지 않음).
> **정정/재검증**: 2026-07-22 23:35 KST에 GitHub API와 프로젝트 원문으로 재검증. 과거 별 성장치는 독립 스냅샷이 없어 미검증으로 표시.

## 요약 순위표

| 순위 | 트렌드 | 분류 | 주목도 근거(지표) |
|---|---|---|---|
| 1 | Graphify — 코드베이스→지식그래프 스킬 | Skills/인프라 | ⭐93,612(API 관측); 7일 성장 미검증 |
| 2 | ponytail — 코드 최소화 스킬 | Skills | ⭐87,693(API 관측); 교정 벤치 평균 약 54% LOC 감소(프로젝트 자기보고) |
| 3 | SingGuard-NSFA — 에이전트 입력/출력 가드레일 | 보안 | ⭐47(API 관측); 논문·모델 공개, 성능은 프로젝트 자기보고 |
| 4 | Arize Phoenix — 에이전트 평가·관측성 | 관측성 | ⭐10,675(API 관측), OTel 기반 |
| 5 | Mastra — TS 에이전트 프레임워크 | 프레임워크 | ⭐26,435(API 관측) |
| 6 | Claude Code 엔터프라이즈 MCP 커넥터 관리 | MCP | Okta 제로터치 프로비저닝 |
| 7 | Agent Zero Trust 부상 | 보안/방법론 | 툴 포이즈닝·메모리 포이즈닝까지 |
| 8 | Traceloop/OpenLLMetry + Future AGI | 관측성/계측 | OTel 네이티브 계측 표준, 셀프호스팅 |
| 9 | "다들 덕테이핑?" 멀티에이전트 현실점검 | 방법론 | 원문 스레드 URL 미보존 — 정량 근거 제외 |
| 10 | hermes-agent — 학습 루프형 개인 에이전트 | Rising Star | ⭐218,799(API 관측); 7일 성장 미검증 |

---

## 상세

### 1. Graphify — 코드베이스+문서+SQL+PDF → 로컬 지식그래프 스킬 🕸️
여러 에이전트 런타임용 `/graphify` 스킬. **코드는** tree-sitter AST로 로컬 처리하며 `--code-only`에서는 API가 필요 없다. 반면 문서·PDF·이미지·비디오는 설정한 모델 또는 API의 semantic pass를 사용할 수 있으므로 “모든 입력이 항상 로컬”이라는 기존 문구는 정정한다. GitHub API 관측 별은 93,612개였으며 7일 성장치는 독립 스냅샷이 없어 확인하지 못했다.
- 출처: [Graphify-Labs/graphify](https://github.com/Graphify-Labs/graphify), [graphify.net](https://graphify.net/)

### 2. ponytail — "가장 게으른 시니어처럼 생각하게" 코드 최소화 스킬 🐴
DietrichGebert의 스킬/플러그인. 프로젝트가 공개한 교정된 agentic benchmark는 12개 기능 과제·Haiku 4.5·반복 n=4에서 **평균 약 54% LOC 감소, 일부 과제 최대 94%**라고 보고한다. 기존의 “80~94%” 평면 표현은 프로젝트 자체가 대화형 baseline artifact를 인정해 정정했으므로 함께 수정한다. 이는 프로젝트 자기보고 벤치이며 외부 재현은 별도다.
- 출처: [DietrichGebert/ponytail](https://github.com/DietrichGebert/ponytail), [교정된 agentic benchmark](https://github.com/DietrichGebert/ponytail/blob/main/benchmarks/results/2026-06-18-agentic.md)

### 3. SingGuard-NSFA — 프롬프트 인젝션·자격증명 탈취 인라인 차단 🛡️
Ant Group AI Security Lab이 공개한 입력/출력 텍스트 가드레일 연구·모델. 프로젝트는 185개 위험 변형, 133개 언어, 분류 모드 약 45~57ms, 자체 벤치마크 F1 94% 초과를 보고하지만 이는 논문·프로젝트 자기보고이며 운영 환경의 코드 실행 차단을 자동으로 보장하지 않는다. 따라서 기존의 “비가역 실행 전에 차단하는 필수 방어” 표현을 “방어심층의 후보 계층”으로 낮춘다.
- 출처: [inclusionAI/SingGuard-NSFA](https://github.com/inclusionAI/SingGuard-NSFA), [arXiv:2607.13081](https://arxiv.org/abs/2607.13081)

### 4. Arize Phoenix — 에이전트 평가·관측성 🔭
OpenTelemetry 기반 오픈소스 관측성·평가 플랫폼. GitHub API 관측 별은 10,675개였다. “양강” 같은 시장 서열은 객관 기준이 없어 삭제하고, 기능 채택 전 공식 문서와 실제 통합 요구사항을 확인한다.
- 출처: [Arize-ai/phoenix](https://github.com/Arize-ai/phoenix), [Phoenix 문서](https://arize.com/docs/phoenix)

### 5. Mastra — TS 단일 패키지 에이전트 프레임워크 📦
에이전트·워크플로·RAG·평가 기능을 제공하는 TypeScript 프레임워크. GitHub API 관측 별은 26,435개였다. 창업자 이력이나 “단일 패키지로 전부 해결” 같은 마케팅 요약보다 공식 저장소의 현재 모듈·라이선스·배포 요구를 기준으로 평가해야 한다.
- 출처: [mastra-ai/mastra](https://github.com/mastra-ai/mastra), [Mastra 문서](https://mastra.ai/docs)

### 6. Claude Code 엔터프라이즈 MCP 커넥터 관리 (Okta) 🔑
엔터프라이즈 관리형 MCP 커넥터와 Okta 프로비저닝 관련 소식이 2차 변경로그 사이트에 등장했다. 이번 재검증에서는 동일 문구를 뒷받침하는 공식 Anthropic 원문을 확보하지 못했으므로 **UNVERIFIED**로 낮춘다. 도입 판단에는 공식 관리자 문서나 계약 환경의 릴리스 노트가 필요하다.
- 보조 출처: [Releasebot](https://releasebot.io/updates/anthropic/claude-code), [Gradually changelog](https://www.gradually.ai/en/changelogs/claude-code/)

### 7. Agent Zero Trust 부상 🚧
7월 보안 글들에서 “Agent Zero Trust”라는 표현이 반복됐다. 다만 기존 문구의 “Anthropic 엔터프라이즈 프레임워크” 귀속은 이번 재검증에서 공식 원문을 확보하지 못했다. 최소권한, 도구 결과의 비신뢰 입력 취급, 메모리 오염 대비, 결정론적 정책 게이트라는 일반 원칙은 유용하지만 특정 업체의 공식 프레임워크로 단정하지 않는다.
- 출처: [Adversa — Agentic AI Security July 2026](https://adversa.ai/blog/top-agentic-ai-security-resources-july-2026/), [Help Net Security — OWASP prompt injection](https://www.helpnetsecurity.com/2026/06/11/owasp-prompt-injection-ai-security-failures/)

### 8. Traceloop/OpenLLMetry + Future AGI — OTel 계측·셀프호스팅 평가 📊
Traceloop/OpenLLMetry는 OpenTelemetry 기반 계측 프로젝트(관측 별 7,318개), Future AGI는 평가·관측·가드레일을 포함하고 셀프호스팅을 설명하는 프로젝트(관측 별 1,486개)다. “계측 표준으로 자리잡았다”는 채택률 근거가 없어 삭제하고, OTel 호환 후보군이라는 수준으로 표현한다.
- 출처: [traceloop/openllmetry](https://github.com/traceloop/openllmetry), [future-agi/future-agi](https://github.com/future-agi/future-agi)

### 9. "다들 덕테이핑 중인가?" 멀티에이전트 오케스트레이션 현실점검 🩹
멀티에이전트 오케스트레이션의 운영 복잡성을 지적하는 토론을 후보로 선정했지만, 당시 수집한 HN·Reddit 원문 URL과 항목별 수치를 저장하지 않았다. 따라서 기존 참여도 합산과 “커뮤니티 합의” 표현은 재현 불가로 철회한다. 이 항목은 정성적 관찰로만 남긴다.
- 출처: `PORTING-DECISION-002` — 원문 ID/URL이 없는 커뮤니티 수치를 복원하거나 삭제할 것

### 10. hermes-agent — 선호 학습형 개인 에이전트 🧑‍🚀
NousResearch의 개인 AI 에이전트. 프로젝트 원문은 대화 검색, 메모리, 사용자 모델링, 경험에서 스킬을 만드는 학습 루프를 설명한다. GitHub API 관측 별은 218,799개였으나 7일 성장치는 독립 스냅샷이 없어 확인하지 못했다. “선호를 학습한다”는 표현은 프로젝트 자기설명 범위로 한정한다.
- 출처: [NousResearch/hermes-agent](https://github.com/NousResearch/hermes-agent), [findarepo — AI Agents](https://findarepo.com/categories/ai-agents/)

---

## 오늘의 스택 시사점

1. **즉시 도입**: Graphify(#1)는 스킬 하나로 코드베이스를 '질의 가능'하게 만듦 — grep 반복을 줄이는 최고 가성비 추가(로컬·프라이버시 안전).
2. **방어 우선**: SingGuard-NSFA(#3) + Agent Zero Trust(#7) — 에이전트 랜섬웨어가 현실이 된 주. 권한·메모리 오염을 '전제'로 설계.
3. **관측성 표준화**: 이번 주 Phoenix·Traceloop·Future AGI가 몰려 뜸 — 자동화를 늘리기 전에 OTel 기반 트레이싱·평가부터 깔 시점.

## 전일 대비 변화

- **중복 skip (최근 7일 규칙)**: last30days DISCOVERY 상위 6건 중 5건(Gemma 4 템플릿, 스웜 이코노믹스, 1인 기업 프레임워크, CS 학생 스킬, 에이전트 정의 논쟁)이 7/19~7/21과 중복되어 제외. OmniRoute·Orca(7/20)도 재등장했으나 제외.
- **design.md**: 어제 홀드한 항목 — 오늘도 신규 우선순위에 밀려 미복원(디자인 테마 냉각 유지).
- **차순위 주목**: OpenManus(⭐56k), Taste Skill(디자인 감각 스킬), Anthropic Zero Trust 상세 프레임워크 문서

---

*생성: Claude Code 자동 트렌드 리서치 · last30days 스킬 DISCOVERY + 웹 보강 · 조사 기간: 2026-06-22 ~ 2026-07-22*
