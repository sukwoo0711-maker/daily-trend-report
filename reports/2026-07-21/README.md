# 🧰 AI Personal Stack 트렌드 리포트 — 2026-07-21 (TOP 10)

> **검증 상태: `LEGACY_UNVERIFIED`** — 이 보고서는 현재의 [근거 계약](../../METHODOLOGY.md) 도입 전 작성됐습니다. 수치·링크·“인기도” 순위는 재사용 전에 원문과 관측 시점을 다시 확인하십시오.

> **조사 방식**: last30days 스킬(v3.16.0) DISCOVERY 스윕(Reddit·HN·Digg 실측 참여도) + 웹 리서치 보강. 조사 윈도우: 2026-06-21 ~ 2026-07-21.
> **범위**: AI Personal Stack 구축에 유용한 것만 — 사용 방법론, 자동화, Skills, MCP, GitHub Rising Star.
> **제외**: 일반 뉴스, 모델 출시 소식, 정책/시장 동향, 에이전틱 브라우저, **최근 7일 내 리포트에서 다룬 항목**.
> **정렬 기준**: **주목도순**(성장 속도·실측 참여·규모·스택 중요도 종합 — 이질 지표라 항목별 근거를 함께 노출). *auto-grill 지적 반영: 기존 '인기도순' 라벨을 '주목도순'으로 교정.*
> **검증**: 본 리포트는 선정·중복·순위 결정을 auto-grill(비판자 3인 blind 심문 + 신선한 판정자)로 검증. 결정 로그는 하단 참조.

## 요약 순위표

| 순위 | 트렌드 | 분류 | 주목도 근거(지표) |
|---|---|---|---|
| 1 | MCP 스펙 대개정 (2026-07-28 RC) | MCP/방법론 | 출시 이후 최대 개정·스택 구조 영향 (7/28 확정 예정) |
| 2 | OpenMontage — 코딩 에이전트→영상 제작 | Rising Star | 주당 +12,000 스타 → ⭐약 32k (성장 최상) |
| 3 | MinerU — 문서→LLM Markdown 변환 | 인프라 | 최근 3.4 릴리스 + 전일 소형툴 대비 기능 델타 (⭐약 70k) |
| 4 | DeerFlow 2.0 — 장기 슈퍼에이전트 하네스 | 자동화/프레임워크 | ⭐약 68k, 2.0 트렌딩 석권 (ByteDance) |
| 5 | Haystack — context-engineering 오케스트레이션 | 방법론/인프라 | ⭐약 24k (deepset) |
| 6 | SkillOpt — 스킬을 학습가능 파라미터로 | Skills/방법론 | Claude Code 내 +19pt (Microsoft Research) |
| 7 | microsoft/agent-framework | 프레임워크 | ⭐약 12k, .NET/Windows 친화 |
| 8 | "에이전트, 다들 같은 걸 말하나?" 정의 논쟁 | 방법론 | HN 405pt·댓글 180 (실측) |
| 9 | 에이전트 스웜과 모델 이코노믹스 | 방법론/비용 | HN 182pt, planner/worker 실비용 데이터 |
| 10 | Ontheia — 셀프호스팅 MCP 네이티브 플랫폼 | 자동화/로컬 | Docker·pgvector·벤더중립 |

---

## 상세

### 1. MCP 스펙 대개정 — 2026-07-28 릴리스 후보 🔌
Model Context Protocol 출시 이후 **최대 규모 개정**의 RC가 락, 7/28 최종 확정 예정(아직 미출시·SDK 검증 중). 핵심은 ① **stateless 코어** — 스티키 세션·공유 세션스토어·게이트웨이 DPI 없이 평범한 로드밸런서 뒤에서 구동, ② **MCP Apps** — 서버 렌더링 UI, ③ **Tasks 확장** — 장시간 작업, ④ OAuth/OIDC 정렬. 지금 당장 쓰는 게 아니라 **곧 붙일 MCP 구성의 재호스팅·인증 방식을 미리 재설계**하라는 신호라 1위. (제품 출시 '뉴스'가 아니라 빌더 영향 관점에서 선정.)
- 출처: [MCP Blog — 2026-07-28 RC](https://blog.modelcontextprotocol.io/posts/2026-07-28-release-candidate/), [WorkOS — MCP 2026 spec](https://workos.com/blog/mcp-2026-spec-agent-authentication)

### 2. OpenMontage — 코딩 에이전트를 영상 제작 시스템으로 🎬
calesthio 프로젝트로 **주당 +12,000 스타**(일부 집계 +17k)를 더하며 ⭐약 32k, 이번 주 성장 최상. 리서치·스크립팅·에셋 생성·편집까지 영상 제작 전 공정을 코딩 어시스턴트에 위임. Windows 구동 가능. **영상/콘텐츠 워크플로를 다루는 경우 한정 유용** — '부분 자동화 → 완결된 제작 잡 위임'이라는 이번 주 트렌딩의 핵심 패턴 대표.
- 출처: [Implicator — Repo Radar](https://www.implicator.ai/repo-radar-5-github-projects-worth-your-week-10/), [GeekFence](https://geekfence.com/top-10-trending-ai-github-repositories-in-july-2026/)

### 3. MinerU — 문서→LLM Markdown 변환 📄
opendatalab의 대형 프로젝트(⭐약 70k), **최근 3.4 릴리스**. 7/20에 다룬 소형 추출 도구군(Hyper-Extract·MDFlux 등)과 층위가 다름 — PDF뿐 아니라 **오피스·PPTX·LaTeX 수식·HTML 표·GPU 가속**까지 보존해 LLM 친화 Markdown으로 변환. 개인 지식베이스 입구(문서 인제스천)의 헤비웨이트. (규모가 아니라 이 기능 델타가 선정 근거 — 전일 카테고리 인접성 명시.)
- 출처: [opendatalab/MinerU](https://github.com/opendatalab/MinerU), [Implicator — Repo Radar](https://www.implicator.ai/repo-radar-5-github-projects-worth-your-week-10/)

### 4. DeerFlow 2.0 — 장기 슈퍼에이전트 하네스 🦌
ByteDance의 오픈소스(MIT) 하네스가 2.0으로 GitHub 트렌딩 석권, ⭐약 68k. 샌드박스·메모리·툴·스킬·서브에이전트·메시지 게이트웨이로 수 분~수 시간짜리 작업을 오케스트레이션. 7/19의 멀티에이전트 오케스트레이션이 '조율'이라면 DeerFlow는 **자기완결형 장기 실행 런타임** — 개인이 무거운 리서치·코딩·제작 잡을 통째로 맡기는 셀프호스팅 대안.
- 출처: [bytedance/deer-flow](https://github.com/bytedance/deer-flow), [Pandaily](https://pandaily.com/byte-dance-open-sources-deer-flow-2-0-tops-git-hub-trending)

### 5. Haystack — context-engineering 중심 오케스트레이션 🧱
deepset의 오픈소스 프레임워크(⭐약 24k). 철학 자체가 **context engineering + 프로덕션 준비**에 맞춰져, 7/15에 다룬 방법론(Context Engineering)을 코드로 구현하는 대표 도구. 프로덕션 RAG·멀티모달·에이전트를 한 틀에서 구성하고 Langfuse(7/19) 등 관측성과 결합하는 셀프호스팅 스택의 코어.
- 출처: [deepset-ai/haystack](https://github.com/deepset-ai/haystack), [O'Reilly — OSS Agent Toolkit 2026](https://www.oreilly.com/radar/the-open-source-agent-toolkit-in-2026/)

### 6. SkillOpt — 스킬을 '학습 가능한 파라미터'로 🧪
Microsoft Research의 텍스트공간 옵티마이저. 모델 가중치를 건드리지 않고 **skill.md 자체를 학습 대상**으로 삼아, 궤적 기반 편집→검증 통과분만 채택→배포 가능한 best_skill.md 산출. 6개 벤치·7개 모델·3개 하네스에서 최고/공동최고, **Claude Code 루프 내 평균 +19.1pt**, GPT-5.5 직접대화 +23.5pt. 스킬을 손으로 튜닝하던 개인 스택에 '스킬 자동 개선' 계층을 추가.
- 출처: [microsoft/SkillOpt](https://github.com/microsoft/SkillOpt), [VentureBeat](https://venturebeat.com/orchestration/microsofts-open-source-skillopt-automatically-upgrades-ai-agent-skills-without-touching-model-weights)

### 7. microsoft/agent-framework 🏗️
Microsoft 공식 에이전트 프레임워크(⭐약 12k, Semantic Kernel+AutoGen 후계). .NET/Python·MIT. **Windows(.NET 네이티브) 사용자에게 가장 친화적**이라 인기가 아니라 실효성으로 선정. LangGraph·CrewAI·OpenAI/Claude Agent SDK와 함께 2026 주류 프레임워크군에 안착.
- 출처: [microsoft/agent-framework](https://github.com/microsoft/agent-framework/releases), [JetBrains — Top Agentic Frameworks 2026](https://blog.jetbrains.com/pycharm/2026/06/top-agentic-frameworks-for-building-applications-2026/)

### 8. "다들 에이전트 만든다는데, 같은 걸 말하나?" 정의 논쟁 🧭
"Everyone Is Building AI Agents—But Do We Mean the Same Thing?" 스레드가 HN 405pt·댓글 180, 총 상호작용 1,218회(last30days 실측, velocity 751)로 이번 주 방법론 담론 1위. 실전 시사는 명확 — **개인 스택 설계 전에 '에이전트'를 무엇으로 정의할지(단순 워크플로 vs 자율 목표추구)부터 확정**하라. 정의가 흔들리면 도구 선택도 흔들린다.
- 출처: last30days DISCOVERY 실측 (r/AI_Agents·r/AgentsOfAI·HN)

### 9. 에이전트 스웜과 모델 이코노믹스 💸
Cursor 블로그발 "Agent swarms and the new model economics"가 HN 182pt·Reddit 댓글 346, 총 상호작용 1,842회(실측). 다수 에이전트 실행 시 **모델 믹스별 실비용 데이터**를 제시 — 예: 하이브리드(Opus 4.8 섞음) 약 $1,339 vs GPT-5.5 단독 약 $10,565, planner=소수 토큰·비용 2/3 / worker=다수 토큰·비용 1/3. 개인 스택의 비용 설계(frugal-agent-stack)에 그대로 투입 가능한 방법론.
- 출처: [Cursor — Agent swarm economics](https://cursor.com/blog/agent-swarm-model-economics), last30days DISCOVERY 실측 (HN 48982535)

### 10. Ontheia — 셀프호스팅 MCP 네이티브 에이전트 플랫폼 🏠
MCP를 표준으로 삼아 외부 클라우드로 데이터를 보내지 않고 자체 인프라에서 에이전트·워크플로를 돌리는 오픈소스 플랫폼. Docker 배포, pgvector RAG 내장, 다중 사용자 RBAC, Claude·ChatGPT·Gemini·Ollama 등 벤더중립. 프라이버시 우선 개인 스택의 '통합 실행 계층' 후보.
- 출처: [Ontheia](https://ontheia.ai/), [mcp.so — Ontheia client](https://beta.mcp.so/client/ontheia/wbrangl)

---

## 오늘의 스택 시사점

1. **즉시 점검**: MCP 스펙 대개정(#1) — 이미 MCP를 쓰는 스택이라면 7/28 전후로 stateless 재호스팅·OAuth 인증 재설계 검토.
2. **자동 개선 도입**: SkillOpt(#6)로 손으로 튜닝하던 스킬을 검증 기반 자동 최적화로 전환 — 스킬 중심 스택의 유지비 절감.
3. **비용 먼저**: #9의 planner/worker 이코노믹스는 다에이전트를 늘리기 전에 비용 구조부터 설계하라는 실측 근거 — 스웜 규모는 지갑이 정한다.

## 전일 대비 변화

- **중복 skip (최근 7일 규칙)**: last30days DISCOVERY 상위 6건 중 4건(Gemma 4 템플릿, 1인 기업 프레임워크, Slack 자동응답 실패담, 에이전트 메모리 논쟁)은 7/19~7/20과 중복되어 제외. page-agent·Grok(모델 출시)·Safari MCP(에이전틱 브라우저 계열)도 규칙상 제외.
- **auto-grill로 드롭/홀드된 항목**: MCP 코어 서버 유지보수 릴리스(P와 'MCP 2연타'되어 뉴스 인상 → 드롭), CS 학생 진로 논쟁(참여 최저·범위 경계 → 드롭), design.md(3일 연속 디자인 피로 우려 → **오늘 홀드**, 판정자가 open query로 남김).
- **차순위 주목**: OpenManus(⭐56k, 오픈 에이전틱 프레임워크), Taste Skill(디자인 감각 스킬 — 디자인 피로로 보류), awesome-llm-apps(실행 가능한 예제 모음)

---

## 🔍 auto-grill 결정 로그

비판자 3인(규칙정합·근거정합·사용자대변)을 blind 병렬 심문 → 다툼 쟁점을 신선한 판정자에게 익명 패킷 전달. 비판자·판정자 원문은 세션 scratchpad에 보존(`grill-critics-2026-07-21.md`).

| 결정 지점 | 검토 대안 | 최강 공격(개연성) | 채택·근거 | 판정 주체 | 신뢰도 |
|---|---|---|---|---|---|
| MinerU 포함 | 포함 / 제외 / 포함+델타 | 어제 문서추출과 중복 체감, 인기순 채우기로 읽힘(높음) | **포함+기능델타 명시**, 스타는 부차. 규칙은 항목 단위·층위 상이·3.4 릴리스 | 판정자(수정채택) | 높음 |
| design.md 유지 | 유지 / 홀드 | 3일 연속 디자인 피로(중~높음) | **오늘 홀드**(계층은 다르나 주관적 피로 판단, alpha 단계) | 판정자(open query)→사용자대변 우려 존중 | 중간 |
| S(정의 논쟁) 유지 | 유지 / 제외 | 손에 안 남는 철학 담론(중~높음) | **유지**. 실측 참여 최고(405pt), X 제외로 담론 비중 정상, '정의 먼저' 실전 프레이밍 | 판정자(채택) | 높음 |
| 순위축 정합성 | 인기도순 유지 / 주목도순 개칭 | 이질지표(절대스타·성장률·HN pt·무수치) 단일축 부당(높음) | **'주목도순'으로 개칭 + 항목별 지표 노출**. T·U 스타수치 실재로 정정 | blind 수렴(A·B) | 높음 |
| W(코어서버) 드롭 | 유지 / 드롭 | P와 'MCP 2연타'로 뉴스 인상(중) | **드롭**. 유지보수 버전업·무수치·신규성 최저 | blind 수렴(A·C) | 높음 |
| X(진로 논쟁) 드롭 | 유지 / 드롭 | 참여 최저·범위 경계·채우기(중~높음) | **드롭**. 전원 일치 | blind 수렴(전원) | 높음 |
| 교체 항목 투입 | 억지 10건 / 품질우선 축소 | 검증 안 된 항목으로 채우기(중) | 드롭 3건을 **검증된 신규 3건**(SkillOpt·DeerFlow·Ontheia)으로 교체 | 판정자(품질우선) + 웹검증 | 높음 |

**구조적 한계(명시)**: 제안자·비판자·판정자가 모두 동일 모델(Claude)의 상관 표본 — blind·익명·신선 판정자는 이해충돌과 앵커링만 제거하며, 공유 훈련분포의 맹점은 남는다. '높음' 신뢰도도 이 상한 아래. design.md 홀드는 사용자가 뒤집을 수 있는 **open query**로, 원하면 내일 복원 가능.

---

*생성: Claude Code 자동 트렌드 리서치 · last30days 스킬 DISCOVERY + 웹 보강 · auto-grill 검증(비판자 3 + 판정자 1) · 조사 기간: 2026-06-21 ~ 2026-07-21*
