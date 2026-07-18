# 🧰 AI Personal Stack 트렌드 리포트 — 2026-07-19 (TOP 10)

> **조사 방식**: last30days 방식 — 최근 30일(2026-06-19 ~ 2026-07-19) 웹 리서치 기반.
> **범위**: AI Personal Stack 구축에 유용한 것만 — 사용 방법론, 자동화, Skills, MCP, GitHub Rising Star.
> **제외**: 일반 뉴스, 모델 출시 소식, 정책/시장 동향, 에이전틱 브라우저, **이전 리포트에서 이미 다룬 항목**.
> **정렬 기준**: 인기도(스타 수·성장 속도·언급량 추정) 내림차순.

## 요약 순위표

| 순위 | 트렌드 | 분류 | 인기도 근거 |
|---|---|---|---|
| 1 | Vibe-Trading — 개인 트레이딩 에이전트 | Rising Star/자동화 | ⭐23.9k, 7/12 트렌딩 1위 |
| 2 | airi — 셀프호스팅 AI 컴패니언 | Rising Star | 주간 트렌딩 상위 고정 |
| 3 | hallmark — 안티 AI-slop 디자인 스킬 | Skills | 7/17 트렌딩 2위 |
| 4 | Apache Ossie — 시맨틱 메타데이터 표준 | 방법론/표준 | 7/17 트렌딩 1위, Apache 재단 |
| 5 | Langfuse 에이전트 그래프 뷰 | 관측성 | OSS LLM 엔지니어링 플랫폼 채택 1위 |
| 6 | 멀티 코딩에이전트 오케스트레이션 | 자동화 | open-multi-agent ⭐6.4k 외 |
| 7 | PixelRAG · semble — 비전·정적 임베딩 검색 | 인프라 | 각 ⭐5.4k |
| 8 | Mirage — 에이전트용 가상 파일시스템 | 인프라 | ⭐3.2k, 백엔드 50+ |
| 9 | 대화형 데이터 분석 에이전트 | 자동화 | Data-Analysis-Agent ⭐2.0k 외 |
| 10 | 특화 MCP 신작 (mcp2cli·CVE·Figma) | MCP | mcp2cli ⭐2.2k 외 |

---

## 상세

### 1. Vibe-Trading — 개인 트레이딩 에이전트 📊
HKUDS의 ⭐23.9k 프로젝트, 7/12 GitHub 트렌딩 1위. 자연어로 질문하면 기관급 리서치·백테스트를 돌려주는 개인 금융 에이전트 — ReAct 엔진에 도구 21종·**스킬 68종**, LLM 프로바이더 11종, 시장별 백테스트 엔진 6종(글로벌 주식·크립토·선물·외환). '스킬 아키텍처'가 코딩을 넘어 도메인 에이전트의 표준 설계로 확산되는 대표 사례. 한국어 README 제공.
- 출처: [HKUDS/Vibe-Trading](https://github.com/HKUDS/Vibe-Trading), [AIToolly](https://aitoolly.com/ai-news/article/2026-07-14-vibe-trading-hkuds-launches-new-personal-ai-trading-agent-on-github), [SkillsLLM](https://skillsllm.com/skill/vibe-trading)

### 2. airi — 셀프호스팅 AI 컴패니언 🧸
"당신이 소유한" 자체 호스팅 AI 컴패니언. 실시간 음성 대화에 Minecraft·Factorio 플레이까지 하는 사이버 존재를 WebGPU·WebAudio·WASM 등 웹 기술만으로 구동(Web/macOS/Windows). 주간 트렌딩 상위에 장기 체류 — '클라우드 구독 컴패니언'의 로컬 소유 대안이라는 새 축.
- 출처: [moeru-ai/airi](https://github.com/moeru-ai/airi)

### 3. hallmark — 안티 AI-slop 디자인 스킬 🎨
Nutlope의 Claude Code·Cursor·Codex용 디자인 스킬, 7/17 트렌딩 2위. 'AI가 만든 티 나는 디자인(AI slop)'을 걷어내는 데 특화 — frontend-design(7/15 리포트)이 연 '디자인 스킬' 장르가 안티패턴 교정이라는 세부 분화 단계로 진입했다는 신호.
- 출처: [Nutlope/hallmark](https://github.com/nutlope/hallmark), [Trendshift](https://trendshift.io/repositories/33587)

### 4. Apache Ossie — 시맨틱 메타데이터 교환 표준 📐
7/17 트렌딩 1위. 분석·AI·BI 플랫폼 간 시맨틱 메타데이터를 교환하는 벤더 중립 JSON/YAML 명세의 Apache 표준화 프로젝트. AGENTS.md가 코드 컨텍스트의 표준이 됐듯, 데이터 의미 계층에서도 '에이전트가 읽는 단일 진실 소스'가 표준화되는 흐름 — 데이터 분석 에이전트를 스택에 넣으려면 주시할 표준.
- 출처: [apache/ossie](https://github.com/apache/ossie)

### 5. Langfuse 에이전트 그래프 뷰 — 셀프호스팅 관측성 🔭
가장 널리 채택된 오픈소스(MIT 코어) LLM 엔지니어링 플랫폼 Langfuse가 7월 에이전트 그래프 뷰(베타)를 공개 — 에이전트 실행을 집계/단계별 두 모드로 시각화해 "어디서 틀어졌는지"를 특정. 셀프호스팅 진영에서는 Arize Phoenix와 양강 구도(둘 다 OpenTelemetry 기반). 에이전트가 늘어난 개인 스택의 디버깅 계층.
- 출처: [Langfuse](https://langfuse.com/blog/2024-07-ai-agent-observability-with-langfuse), [AIMultiple](https://aimultiple.com/agentic-monitoring), [QASkills](https://qaskills.sh/blog/langfuse-llm-observability-guide-2026)

### 6. 멀티 코딩에이전트 오케스트레이션 🎼
open-multi-agent(⭐6.4k)는 목표를 병렬 태스크 DAG로 분해하는 TypeScript 오케스트레이터, squad(⭐2.9k)는 에이전트 팀 구성을 repo 파일로 영속화해 GitHub과 통합, mercury-agent(⭐2.7k)는 권한 게이팅+Telegram 제어의 상시 구동형. '에이전트 1개'에서 '팀 구성'으로 개인 스택의 단위가 커지는 중.
- 출처: [AI Tool Radar — July 2026](https://aitoolradar.io/blog/open-source-ai-radar-july-2026)

### 7. PixelRAG · semble — 검색의 두 갈래 실험 🔍
PixelRAG(⭐5.4k)는 문서를 텍스트 추출 없이 **스크린샷째로** 비전 임베딩 검색 — 표·도면이 많은 문서에 강함. semble(⭐5.4k)은 tree-sitter+정적 임베딩으로 **API 키 없이** 코드 검색. 임베딩 API 의존을 끊는 로컬 검색 실험들이 동시에 5k대에 진입.
- 출처: [AI Tool Radar — July 2026](https://aitoolradar.io/blog/open-source-ai-radar-july-2026)

### 8. Mirage — 에이전트용 가상 파일시스템 🗂️
S3·Slack·Gmail 등 50+ 백엔드를 가상 파일시스템으로 마운트해 에이전트가 파일 읽듯 접근(⭐3.2k). 서비스마다 MCP 서버를 붙이는 대신 'FS 하나로 통일'하는 접근 — 개인 스택의 통합 계층 설계에 시사점.
- 출처: [AI Tool Radar — July 2026](https://aitoolradar.io/blog/open-source-ai-radar-july-2026)

### 9. 대화형 데이터 분석 에이전트 📈
Data-Analysis-Agent(⭐2.0k)는 SQL 생성부터 차트까지 대화로 처리, OpenScience(⭐2.1k)는 문헌 읽기·실험까지 자율 수행하는 리서치 워크벤치, marimo-pair는 반응형 노트북 marimo를 에이전트 스킬로 연결. '분석 도구를 다루는 나' → '분석을 시키는 나'로의 전환 클러스터.
- 출처: [AI Tool Radar — July 2026](https://aitoolradar.io/blog/open-source-ai-radar-july-2026)

### 10. 특화 MCP 신작: mcp2cli · CVE · Figma 🔌
mcp2cli(⭐2.2k)는 MCP 서버를 토큰 효율적 TOON 인코딩의 CLI로 노출 — MCP 없는 환경에서도 재사용. cve-mcp-server(⭐1.1k)는 NVD/EPSS/KEV 등 24개 보안 데이터 소스를 에이전트에 연결, Figwright는 디자인 토큰을 존중하는 양방향 Figma→코드 MCP. 범용 MCP 시대에서 '용도 특화 MCP' 시대로.
- 출처: [AI Tool Radar — July 2026](https://aitoolradar.io/blog/open-source-ai-radar-july-2026)

---

## 오늘의 스택 시사점

1. **즉시 적용**: hallmark(#3)는 스킬 파일 하나라 도입 비용 제로 — frontend-design과 함께 쓰면 디자인 품질 하한선이 올라감.
2. **도입 검토**: Langfuse(#5)를 셀프호스팅하면 데일리 봇·자동화 에이전트의 실패 지점 추적이 가능해짐 — 자동화를 늘리기 전에 관측성부터.
3. **관찰**: Vibe-Trading(#1)의 68-스킬 구조는 '도메인 에이전트 = 스킬 묶음' 설계의 교본 — 직접 쓰지 않더라도 스킬 설계 참고자료로 가치.

## 전일 대비 변화

- **발행 공백**: 7/17, 7/18 미발행 (이번 회차가 7/16 이후 첫 리포트)
- **신규 진입**: 전체 10건 (기존 리포트 2건과 중복 없음 확인)
- **차순위 주목**: OpenCut(트렌딩 1위 상주하나 AI 비중 낮아 제외), needle(⭐2.6k, 웨어러블용 26M 툴콜링 모델), Steinberger의 AI 사용량 한도 메뉴바 트래커, memsearch(⭐2.1k, Markdown+Milvus 코딩에이전트 메모리)

---

## 🔴 라이브 커뮤니티 펄스 (last30days 스킬 · 오늘 도입)

> 오늘부터 조사 도구로 last30days 스킬(v3.16.0)을 도입. Reddit·HN·Digg의 실측 참여도(포인트·댓글 수) 기반 DISCOVERY 스윕 결과 중 본 리포트 범위에 맞는 것만 발췌. 위 TOP 10(웹 리서치 기반)과 상호 보완. 조사 윈도우: 2026-06-18 ~ 2026-07-18.

1. **"처음부터 시작한다면 어떤 도구 쓸래?" 스택 토론** — Reddit·HN 12개 스레드, 상호작용 858회(HN 92pt, Reddit 댓글 302). 도구 선택 담론 자체가 커뮤니티 최상위 관심사 — 본 리포트의 존재 이유와 정확히 겹치는 수요.
2. **1인 기업 AI 에이전트 운영 프레임워크** — "6개월 운영에서 나온 10단계 프레임워크(그리고 깨진 지점들)" 공유 글 확산(상호작용 387회, Reddit 댓글 162). 개인 스택 방법론의 실전 검증 사례.
3. **LLM 캐시 무효화 감지 도구** — 하네스 빌더용 캐시 인밸리데이션 캐처가 HN 737pt·댓글 370. "토큰을 많이 쓴다고만 생각하는데 실은 캐시가 깨진 것" (u/DigitalGuruLabs). 에이전트 비용 최적화의 대표 맹점.
4. **무감독 자동화 실패담** — Slack 자동응답을 에이전트에 맡겼다 사고 난 사례가 화제(상호작용 553회). 개인 자동화에 권한 게이팅·감독이 필요한 이유의 생생한 반면교사.
5. **Gemma 4 챗 템플릿·툴콜링 대수술** — 툴콜링 수정과 Flash Attention 4 지원(상호작용 4,147회, HN 2,057pt). 로컬 스택에서 에이전트 돌리는 유저에게 직결되는 신뢰성 개선.
6. **벤치마크 사기 경계령** — HLE 99.44%를 주장한 신생 랩이 실제로는 타사 모델을 서빙 중인 것으로 드러남(상호작용 828회). 벤치마크 수치만 보고 스택에 모델을 편입하는 위험 환기.

---

*생성: Claude Code 자동 트렌드 리서치 · 조사 기간: 2026-06-19 ~ 2026-07-19 · 커뮤니티 펄스: last30days 스킬 DISCOVERY*
