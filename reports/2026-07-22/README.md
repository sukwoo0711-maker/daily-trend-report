# 🧰 AI Personal Stack 트렌드 리포트 — 2026-07-22 (TOP 10)

> **조사 방식**: last30days 스킬(v3.16.0) DISCOVERY 스윕(Reddit·HN·Digg 실측 참여도) + 웹 리서치 보강. 조사 윈도우: 2026-06-22 ~ 2026-07-22.
> **범위**: AI Personal Stack 구축에 유용한 것만 — 사용 방법론, 자동화, Skills, MCP, GitHub Rising Star.
> **제외**: 일반 뉴스, 모델 출시 소식, 정책/시장 동향, 에이전틱 브라우저, **최근 7일 내 리포트에서 다룬 항목**.
> **정렬 기준**: 주목도순(성장 속도·실측 참여·규모·스택 중요도 종합, 항목별 근거 노출).

## 요약 순위표

| 순위 | 트렌드 | 분류 | 주목도 근거(지표) |
|---|---|---|---|
| 1 | Graphify — 코드베이스→로컬 지식그래프 스킬 | Skills/인프라 | ⭐약 90k, +7.2k/7d (최고 성장) |
| 2 | ponytail — "가장 게으른 시니어" 코드 최소화 스킬 | Skills | ⭐약 87k, +4.2k/7d |
| 3 | SingGuard-NSFA — 프롬프트 인젝션 인라인 차단 | 보안 | Ant Group, 에이전트 랜섬웨어 실사례 직후 공개 |
| 4 | Arize Phoenix — 에이전트 평가·관측성 | 관측성 | OTel 기반, 프리빌트 스코어러 |
| 5 | Mastra — TS 단일 패키지(에이전트+RAG+평가) | 프레임워크 | ex-Gatsby 창업자 |
| 6 | Claude Code 엔터프라이즈 MCP 커넥터 관리 | MCP | Okta 제로터치 프로비저닝 |
| 7 | Agent Zero Trust 부상 | 보안/방법론 | 툴 포이즈닝·메모리 포이즈닝까지 |
| 8 | Traceloop/OpenLLMetry + Future AGI | 관측성/계측 | OTel 네이티브 계측 표준, 셀프호스팅 |
| 9 | "다들 덕테이핑?" 멀티에이전트 현실점검 | 방법론 | HN 37pt·Reddit 댓글 164 (실측) |
| 10 | hermes-agent — 선호 학습형 개인 에이전트 | Rising Star | ⭐약 218k, +3.5k/7d |

---

## 상세

### 1. Graphify — 코드베이스+문서+SQL+PDF → 로컬 지식그래프 스킬 🕸️
Claude Code·Cursor·Codex·Gemini CLI 등 15+ 플랫폼용 `/graphify` 스킬. 코드·docs·SQL 스키마·config·PDF를 **로컬 결정론적 AST 파싱(tree-sitter)**으로 쿼리 가능한 지식그래프로 변환 — 벡터스토어·LLM 없이, 아무것도 기기 밖으로 안 나감. 각 엣지를 EXTRACTED(원문 명시)/INFERRED(그래프 추론)로 태깅해 근거 추적 가능. ⭐약 90k, **주당 +7.2k로 이번 주 최고 성장**. grep 대신 프로젝트를 '질의'하는 개인 스택의 코드 이해 계층.
- 출처: [Graphify-Labs/graphify](https://github.com/Graphify-Labs/graphify), [graphify.net](https://graphify.net/)

### 2. ponytail — "가장 게으른 시니어처럼 생각하게" 코드 최소화 스킬 🐴
DietrichGebert의 스킬/플러그인(⭐약 87k, +4.2k/7d). 철학은 "최고의 코드는 안 쓴 코드" — 에이전트가 불필요한 코드를 덜 쓰게 유도. `ponytail:<skill>` 등록에 `/ponytail-review`·`-audit`·`-debt`·`-gain` 커맨드, 벤치마크상 **베이스라인 대비 80~94% 코드 감소**. 7/15의 Karpathy 행동원칙 CLAUDE.md 계열이나, 벤치까지 갖춘 완성형 스킬 플러그인.
- 출처: [DietrichGebert/ponytail](https://github.com/DietrichGebert/ponytail), [Ponytail 설치 가이드](https://knightli.com/en/2026/06/24/ponytail-ai-agent-coding-plugin-guide/)

### 3. SingGuard-NSFA — 프롬프트 인젝션·자격증명 탈취 인라인 차단 🛡️
Ant Group이 공개한 무료 프레임워크. 자율 에이전트 파이프라인에 **인라인으로 얹어**, 프롬프트 인젝션·자격증명 탈취 패턴·악성 코드 실행·권한 오남용을 실행(비가역 결과) 전에 차단. Sysdig가 최초의 엔드투엔드 AI 에이전트 랜섬웨어를 문서화한 지 12일 만에 공개 — 이번 주 DISCOVERY에서도 "툴 결과는 입력이지 진리가 아니다, 확인 단계는 루프 밖 코드에 둬야 한다"는 커뮤니티 경고가 상위. 에이전트에 실행 권한을 주는 개인 스택의 필수 방어.
- 출처: [TechTimes — Ant Group SingGuard](https://www.techtimes.com/articles/320508/20260714/ant-group-open-sources-agent-security-tool-days-after-agentic-ransomware-hit.htm), [Adversa — Agentic AI Security July 2026](https://adversa.ai/blog/top-agentic-ai-security-resources-july-2026/)

### 4. Arize Phoenix — 에이전트 평가·관측성 🔭
OpenTelemetry 기반 오픈소스 관측성 플랫폼. 환각·관련성·독성·일관성 **프리빌트 스코어러**, 라이브 실패를 평가 실행에 연결하는 프로덕션 모니터링, OpenAI Agents SDK·CrewAI·LangGraph 통합. 7/19에 Langfuse를 다뤘다면 Phoenix는 '평가(eval) 특화' 축의 대표 — 셀프호스팅 관측성의 양강 중 하나.
- 출처: [Confident AI — Best Observability Tools 2026](https://www.confident-ai.com/knowledge-base/compare/best-ai-agent-observability-tools-2026), [Latitude](https://latitude.so/blog/best-ai-agent-observability-tools-2026-comparison)

### 5. Mastra — TS 단일 패키지 에이전트 프레임워크 📦
에이전트·워크플로·RAG·평가를 하나의 TypeScript 패키지로 묶은 프레임워크(ex-Gatsby 창업자). 파이썬 위주 프레임워크(7/21 Haystack·agent-framework)와 달리 **JS/TS 스택 사용자**를 위한 통합 옵션 — 웹 스택에 에이전트를 붙이는 개인 개발자에게 진입점.
- 출처: [O'Reilly — OSS Agent Toolkit 2026](https://www.oreilly.com/radar/the-open-source-agent-toolkit-in-2026/), [Firecrawl — Best OSS RAG Frameworks](https://www.firecrawl.dev/blog/best-open-source-rag-frameworks)

### 6. Claude Code 엔터프라이즈 MCP 커넥터 관리 (Okta) 🔑
Claude Code에 **엔터프라이즈 관리형 MCP 커넥터 접근**이 추가(Okta부터). 관리자가 커넥터를 한 번 프로비저닝하면 사용자는 첫 로그인에 제로터치로 접근 — Claude 챗·Claude Code·Cowork를 아우르는 중앙 인가. 함께 SDK MCP 서버가 다음 턴까지 연결을 지연하던 버그도 수정. MCP를 여러 개 쓰는 스택의 인증·배포 관리 개선.
- 출처: [Anthropic Release Notes — July 2026](https://releasebot.io/updates/anthropic/claude-code), [Claude Code Changelog](https://www.gradually.ai/en/changelogs/claude-code/)

### 7. Agent Zero Trust 부상 🚧
7월 에이전트 보안 담론이 이론적 취약점에서 **구조적·시스템적 방어**로 이동, 핵심 테마가 'Agent Zero Trust'. Anthropic의 엔터프라이즈 에이전트 제로트러스트 프레임워크가 프롬프트 인젝션·**툴 포이즈닝·아이덴티티 남용·메모리 포이즈닝**을 함께 다룸. 선언적 정책 룰(금지 행동)과 모델 기반 분류기(인젝션 탐지)를 겹치는 방어심층(defense-in-depth) 권고. 개인 스택도 권한·메모리 오염을 전제로 설계하라는 방법론 신호.
- 출처: [Adversa — Agentic AI Security July 2026](https://adversa.ai/blog/top-agentic-ai-security-resources-july-2026/), [Help Net Security — OWASP prompt injection](https://www.helpnetsecurity.com/2026/06/11/owasp-prompt-injection-ai-security-failures/)

### 8. Traceloop/OpenLLMetry + Future AGI — OTel 계측·셀프호스팅 평가 📊
Traceloop의 OpenLLMetry가 **OTel 네이티브 LLM 계측 표준**으로 자리잡는 중 — 벤더 종속 없이 트레이싱을 표준 파이프라인에 흘림. Future AGI는 트레이싱·평가·가드레일·게이트웨이를 갖춘 **셀프호스팅 엔드투엔드** 플랫폼. Phoenix(#4)와 함께 이번 주 관측성·평가 계층이 몰려 뜬 흐름의 표준화 축.
- 출처: [Latitude — 15 Observability Platforms 2026](https://latitude.so/blog/15-ai-agent-observability-platforms-2026-agentic-complexity), [Confident AI](https://www.confident-ai.com/knowledge-base/compare/best-ai-agent-observability-tools-2026)

### 9. "다들 덕테이핑 중인가?" 멀티에이전트 오케스트레이션 현실점검 🩹
"Is anyone actually orchestrating multi-agent workflows well, or are we all duct-taping?" 스레드가 HN 37pt·댓글 83, Reddit 댓글 164, 총 상호작용 358회(last30days 실측). 상위 코멘트는 "아무 데나 에이전트를 던지지 말고, AI를 제대로 활용하는 백엔드를 갖춘 소프트웨어를 두는 게 요령"(u/Vaxtin). 7/19~20의 오케스트레이션 도구 붐 이면의 **현실 점검** — 도구보다 구조가 먼저라는 커뮤니티 합의.
- 출처: last30days DISCOVERY 실측 (r/AI_Agents·r/AgentsOfAI·HN)

### 10. hermes-agent — 선호 학습형 개인 에이전트 🧑‍🚀
NousResearch의 개인 AI 에이전트(⭐약 218k, +3.5k/7d). 사용자 선호를 시간에 걸쳐 학습. 대형·성숙 프로젝트지만 '선호를 기억·학습하는 상시 개인 에이전트'라는 AI Personal Stack의 정중앙 카테고리라 이번에 처음 소개 — 7/16의 메모리 레이어(Mem0 등)를 '제품형 개인 에이전트'로 완성한 형태.
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
