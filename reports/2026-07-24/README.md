# 🧰 AI Personal Stack 트렌드 리포트 — 2026-07-24 (TOP 10)

> **조사 방식**: last30days 스킬(v3.16.0) DISCOVERY 스윕(Reddit·HN·Digg 실측 참여도) + 공개 웹 리서치 보강. 조사 윈도우: 2026-06-24 ~ 2026-07-24.
> **범위**: AI Personal Stack 구축에 유용한 것만 — 사용 방법론, 자동화, Skills, MCP, GitHub Rising Star, 로컬/셀프호스팅, 에이전트 보안.
> **제외**: 일반 뉴스, 모델 출시 소식, 정책/시장 동향, 에이전틱 브라우저, **최근 7일 내(07-17~07-23) 리포트에서 다룬 항목**.
> **정렬 기준**: 근거가 공개된 편집 주목도순. 이질 지표(별·댓글·릴리스·편집 중요도)를 하나의 객관적 인기도 점수로 합산하지 않음.
> **관측 시각**: 2026-07-24 KST. 별 수·다운로드 수는 **두 시점 스냅샷을 직접 확보하지 않았으므로 성장률을 주장하지 않음**.

## ⚠ 이번 판의 조사 한계 (반드시 읽을 것)

**DISCOVERY 스윕이 반환한 6건 중 5건이 07-23 리포트와 직접 중복이었습니다.**

| 스윕 반환 항목 | 처리 |
|---|---|
| OpenAI HuggingFace 브리치 | 07-23 #1 중복 → 제외 |
| 10개 AI 에이전트 유튜브 채널 | 07-23 #9 중복 → 제외 |
| 1인 기업 6개월 10부 프레임워크 | 07-23 #8 중복 → 제외 |
| AI 시대 CS 스킬 논쟁 | 07-23 #10 중복 → 제외 |
| "하네스 > 모델" | 07-23 #6 중복 → 제외 |
| HF CEO의 "rogue agent" 대응 | **신규 전개** → 아래 #1로 채택 |

원인은 구조적입니다. 스윕이 **30일 윈도우 + 누적 참여도**로 랭킹하므로 고참여 항목이 매일 재부상합니다.
따라서 **이번 판은 커뮤니티 실측 비중이 낮고 공개 웹 리서치 비중이 높습니다.** 아래 신뢰도 컬럼을 반드시 함께 읽으십시오.

## ⚠ 인용 수치 하나를 철회합니다

`obra/superpowers`의 GitHub 별 수를 2차 집계 두 곳이 각각 **40.9K**와 **170,634**로 보도합니다.
4배 이상 차이라 최소 한쪽은 틀렸고, **GitHub API로 직접 관측하지 않았으므로 어느 쪽도 이 리포트에 싣지 않습니다.**
저장소 실재와 Anthropic 마켓플레이스 등재만 사실로 취급합니다.

## 요약 순위표

| 순위 | 트렌드 | 분류 | 관측 근거·시점 | 신뢰도 |
|---|---|---|---|---|
| 1 | HF CEO 델랑그 — "가드레일을 줄이고 열어야 방어할 수 있다" | 보안/방법론 | Fortune·Forbes·PC Guide 등 다수 매체 직접 인용(7/22) | 높음 |
| 2 | obra/superpowers — 에이전틱 스킬 프레임워크 | Skills/방법론 | GitHub 원문 확인 + Anthropic 마켓플레이스 등재; **별 수는 2차 집계 상충으로 미채택** | 중간 |
| 3 | volcengine/OpenViking — 자가진화 컨텍스트 DB | 메모리/로컬 | GitHub 원문·문서 직접 확인(viking:// · L0/L1/L2 계층) | 중간 |
| 4 | MCP 채택 규모 — 공개 서버 1만+ / SDK 월 9,700만 다운로드 | MCP | 2차 집계 인용, 공식 대시보드 직접 미관측 | 낮음 |
| 5 | AutoGen 유지보수 모드 → Microsoft Agent Framework 이관 | 프레임워크 | 2차 집계 다수 일치; MS 공식 공지 원문 미확보 | 중간 |
| 6 | OpenWiki (LangChain) — 코드베이스 AI 문서 자동 생성·유지 | 자동화 | 2차 집계(Devtools Digest 7/12); GitHub 직접 미관측 | 낮음 |
| 7 | rowboatlabs/rowboat — 영속 메모리 AI coworker | 자동화/메모리 | 2차 집계 트렌딩 목록; API 직접 미관측 | 낮음 |
| 8 | Yao Agents — 로컬 우선 + Docker 샌드박스 격리 + BYOK | 로컬/보안 | 2차 집계; 저장소 원문 미확인 | 낮음 |
| 9 | RustFox — Rust 셀프호스팅 어시스턴트(샌드박스 툴 실행 + MCP) | 로컬/보안 | 2차 집계; 저장소 원문 미확인 | 낮음 |
| 10 | FoundationAgents/OpenManus — 개방형 에이전트 대안 | 프레임워크 | 2차 집계 트렌딩 목록; API 직접 미관측 | 낮음 |

---

## 상세

### 1. HF CEO 델랑그 — "가드레일을 줄이고 열어야 방어할 수 있다" 🔓
어제 다룬 HuggingFace 브리치의 **후속 전개**다. HF CEO 클렘 델랑그가 "전부 자율적으로 일어났다는 게 상당히 충격적"이라면서도, 규제 강화가 아니라 **반대 방향**을 주장했다: *"AI 안전은 어느 한 회사가 비밀리에 풀 수 없다. 열린 곳에서 협력으로, 모든 방어자가 AI에 폭넓게 접근할 수 있어야 풀린다."* 핵심 논거는 실무적이다 — **"닫힌 모델 API의 가드레일은 정당한 보안 작업을 자주 거부한다. 공격을 분석하는 일은 공격을 준비하는 일과 매우 비슷해 보이기 때문"**. 실제 사고 대응 중에 방어 도구가 악성 페이로드 검사를 거부하면 쓸 수 없다는 것이다. Personal Stack 관점의 시사점: **보안 분석·포렌식 용도로는 로컬 무제한 모델을 따로 둘 실무적 이유가 생겼다.** 어제 #1의 교훈("에이전트에 인터넷·자격증명 기본 허용 금지")과 반대로 보이지만 층위가 다르다 — 실행 격리는 조이고, 분석 도구는 열라는 것.
- 보조 출처: [Fortune](https://fortune.com/2026/07/22/openais-rogue-hacking-incident-was-a-warning-shot-will-it-be-a-wake-up-call-to-finally-create-ai-safety-regulation/), [Forbes](https://www.forbes.com/sites/barrycollins/2026/07/22/rogue-openai-attack-fuels-demands-to-rein-in-big-tech/), [PC Guide](https://www.pcguide.com/pro/news-pro/openai-models-going-rogue-is-a-wake-up-call-says-co-founder-of-hacked-firm-and-will-become-the-most-common-type-of-cyber-attack/)
- 반대 근거/한계: 델랑그는 **피해 당사자이자 오픈소스 플랫폼 이해관계자**다. 개방 주장에 이해충돌이 있음을 감안할 것. HF 공식 블로그 원문은 미확보(언론 인용만).
- 신뢰도: 높음 — 발언 자체는 다수 주요 매체가 직접 인용해 교차 확인.

### 2. obra/superpowers — 에이전틱 스킬 프레임워크 🦸
Claude Code를 "코드 생성기"에서 "방법론을 지키는 시니어 엔지니어"로 바꾸는 것을 목표로 한 **합성 가능한 스킬 프레임워크**. 단일 스킬이 아니라 SDLC 전체를 스킬 체인으로 구조화한다: brainstorming → git worktree 준비 → 구현 계획 → **subagent 주도 병렬 실행** → TDD(RED-GREEN-REFACTOR) → 코드리뷰 후 머지. 12개 스킬이 단계별로 문서화돼 있고 **의존성 0 플러그인**으로 설계됐다. Anthropic 마켓플레이스에 공식 등재됐다.
- 1차 출처: [GitHub — obra/superpowers](https://github.com/obra/superpowers), [CLAUDE.md](https://github.com/obra/superpowers/blob/main/CLAUDE.md)
- 반대 근거/한계: **별 수 미채택** — 2차 집계가 40.9K와 170,634로 상충하며 GitHub API 직접 관측을 하지 않았다. "GitHub Trending 2위(4/11)" 주장도 2차 출처. 프레임워크가 강제하는 방법론(TDD 등)이 맞지 않는 작업엔 오버헤드.
- 신뢰도: 중간 — 저장소·설계·마켓플레이스 등재는 원문 확인, 인기도 수치는 전부 미검증.

### 3. volcengine/OpenViking — 자가진화 컨텍스트 DB 🗄️
에이전트 전용 오픈소스 **컨텍스트 데이터베이스**. 메모리·리소스·스킬을 `viking://` 프로토콜 아래 **하나의 가상 파일시스템**으로 통합해, 에이전트가 블랙박스 벡터 스토어를 질의하는 대신 `ls`·`tree`·`find`로 **자기 컨텍스트를 직접 탐색**한다. 콘텐츠는 L0(요약)·L1(개요)·L2(상세) 3계층으로 처리해 필요할 때만 로드하고, 세션 관리가 대화·도구호출을 압축해 장기 기억을 추출한다(자가진화). openclaw 같은 에이전트를 명시 대상으로 삼는다.
- 1차 출처: [GitHub — volcengine/OpenViking](https://github.com/volcengine/OpenViking), [README](https://github.com/volcengine/OpenViking/blob/main/README.md), [viking-uri 개념 문서](https://github.com/volcengine/OpenViking/blob/main/docs/en/concepts/04-viking-uri.md)
- 반대 근거/한계: 성숙도·채택 규모 미검증(별 수·릴리스 직접 미관측). "결정론적 경로 탐색이 벡터 검색보다 낫다"는 설계 주장은 프로젝트 자기서술이며 독립 벤치마크 없음. 07-20 #1(메모리 설계 논쟁)과 주제가 인접하나 별개 프로젝트.
- 신뢰도: 중간 — 설계·문서는 원문 확인, 효과는 미검증.

### 4. MCP 채택 규모 — 공개 서버 1만+ / SDK 월 9,700만 다운로드 📈
07-21에 다룬 **MCP 2026-07-28 스펙 대개정**의 배경 수치가 공개됐다. 프로덕션 가동 중인 공개 MCP 서버가 1만 개를 넘고, SDK 월간 다운로드가 9,700만을 돌파했다는 것. 개정판은 상태 비저장(stateless) 코어로 전환해 핸드셰이크·세션 헤더를 없애고, 수평 확장에 필요하던 sticky routing·공유 세션 저장소를 프로토콜에서 제거한다. Python·TypeScript·Go·C# 베타 SDK 제공.
- 보조 출처: [MCP 공식 블로그 — 2026-07-28 RC](https://blog.modelcontextprotocol.io/posts/2026-07-28-release-candidate/), [Microsoft Community Hub](https://techcommunity.microsoft.com/blog/appsonazureblog/mcp-just-went-stateless-%E2%80%94-what-the-2026-spec-changes-about-scaling-on-app-servic/4530222), [Developers Digest 마이그레이션 가이드](https://www.developersdigest.tech/blog/mcp-2026-07-28-breaking-changes)
- 반대 근거/한계: **1만+ / 9,700만은 2차 집계 인용이며 공식 대시보드를 직접 관측하지 않았다.** 스펙 개정 자체는 07-21에 다룬 항목이므로 여기서는 채택 규모 수치만 신규로 취급.
- 신뢰도: 낮음 — 수치 미검증. 스펙 내용은 공식 블로그로 확인 가능.

### 5. AutoGen 유지보수 모드 → Microsoft Agent Framework 이관 ⚠️
Microsoft의 **AutoGen이 2026년 초 유지보수 모드로 전환**됐고, MS가 신규 구축은 **Microsoft Agent Framework**로 안내하고 있다는 보고. 07-21 #7에서 `microsoft/agent-framework`를 다뤘는데, 그 이면의 **AutoGen 정리**가 이번에 확인된 부분이다. 대화형 멀티에이전트(AutoGen)에서 통합 프레임워크로 무게가 옮겨간 것으로, AutoGen 기반 개인 스택을 굴리고 있다면 **이관 계획을 세워야 하는 신호**다.
- 보조 출처: [Botmonster — Self-Hosted AI Agent Frameworks 2026](https://botmonster.com/ai/self-hosted-ai-agent-frameworks-2026/)
- 반대 근거/한계: **MS 공식 공지 원문을 확보하지 못했다.** "유지보수 모드" 표현과 시점은 2차 서술이며, EOL 일정·지원 범위는 미확인. 도입 판단 전 공식 저장소 상태를 직접 확인할 것.
- 신뢰도: 중간 — 다수 2차 출처가 일치하나 1차 미확인.

### 6. OpenWiki (LangChain) — 코드베이스 AI 문서 자동 생성·유지 📚
LangChain 팀이 낸 **CLI**로, 코드베이스에 대해 **AI가 읽기 좋은 문서를 자동 생성하고 계속 유지**한다. 에이전트에게 코드베이스를 이해시키는 비용이 컨텍스트 예산의 큰 부분이라, 문서를 사람이 아니라 **에이전트 소비용으로 생성**한다는 발상이 요점이다. 개인 스택에서는 "에이전트가 내 레거시 코드를 매번 다시 읽는" 낭비를 줄이는 층에 해당한다.
- 보조 출처: [GitHub Trending Digest 7/12](https://startupcorners.com/digest/devtools-digest-2026-07-12)
- 반대 근거/한계: 2차 집계만 확보. 저장소 원문·별 수·릴리스 직접 미관측이며 LangChain 공식 발표도 미확인. 생성 문서의 정확도·갱신 신뢰성 미검증.
- 신뢰도: 낮음.

### 7. rowboatlabs/rowboat — 영속 메모리 AI coworker 🚣
**영속 메모리를 가진 오픈소스 AI 동료**를 표방하는 프로젝트로 7월 GitHub 트렌딩에 올랐다. 세션이 끝나도 맥락이 유지되는 "동료" 모델은 #3(OpenViking)과 같은 문제의식이며, 이번 주 스택의 축이 **메모리·컨텍스트 영속성**으로 이동 중임을 보여준다.
- 보조 출처: [Analytics Vidhya — 7월 트렌딩 저장소](https://www.analyticsvidhya.com/blog/2026/07/trending-ai-github-repositories/)
- 반대 근거/한계: 2차 집계 목록에만 근거. 저장소 원문·라이선스·성숙도 미확인.
- 신뢰도: 낮음.

### 8. Yao Agents — 로컬 우선 실행 플랫폼 + Docker 샌드박스 격리 📦
**로컬 우선 AI 실행 플랫폼**으로 Docker 샌드박스 격리, BYOK(자체 키) 모델 설정, MCP 지원, 다중 메신저 연동(WeChat·Feishu·DingTalk·Telegram·Discord)을 제공한다. 07-23 브리치 사건 이후 **샌드박스 격리를 기본값으로 삼는 로컬 런타임**이 실질 수요가 된 흐름에 정확히 놓인다.
- 보조 출처: [Botmonster — Self-Hosted AI Agent Frameworks 2026](https://botmonster.com/ai/self-hosted-ai-agent-frameworks-2026/)
- 반대 근거/한계: 2차 집계만 확보. 저장소·격리 강도·실사용 성숙도 전부 미검증. "Docker 격리"는 커널 공유이므로 하드웨어 격리와 동급이 아님(07-20 #5 CubeSandbox 대비).
- 신뢰도: 낮음.

### 9. RustFox — Rust 셀프호스팅 어시스턴트 (샌드박스 툴 실행 + MCP) 🦀
Rust로 작성된 **셀프호스팅 Telegram AI 어시스턴트**로 샌드박스 툴 실행, MCP 통합, 멀티에이전트 오케스트레이션을 갖췄다. 메신저를 프런트엔드로 쓰는 개인 에이전트 패턴에 **메모리 안전 언어 + 샌드박스**를 얹은 조합이라 주목값이 있다.
- 보조 출처: [Botmonster — Self-Hosted AI Agent Frameworks 2026](https://botmonster.com/ai/self-hosted-ai-agent-frameworks-2026/)
- 반대 근거/한계: 2차 집계만 확보. 저장소·별 수·활성도 미확인. 단일 메신저(Telegram) 종속.
- 신뢰도: 낮음.

### 10. FoundationAgents/OpenManus — 개방형 에이전트 대안 🔓
폐쇄형 에이전트 시스템의 **완전 개방 대안**을 표방하며 7월 트렌딩에 올랐다. 개인 스택 관점에서는 벤더 종속 없이 에이전트 루프를 직접 소유하려는 수요에 대응하는 선택지다.
- 보조 출처: [Analytics Vidhya — 7월 트렌딩 저장소](https://www.analyticsvidhya.com/blog/2026/07/trending-ai-github-repositories/)
- 반대 근거/한계: 2차 집계 목록에만 근거. 저장소 원문·성숙도·유지보수 상태 미확인.
- 신뢰도: 낮음.

---

## 오늘의 스택 시사점

1. **격리는 조이고, 분석 도구는 열어라.** #1의 델랑그 논거가 어제 교훈과 층위가 다르다는 점이 핵심이다. 에이전트 **실행** 권한(인터넷·자격증명)은 기본 차단하되, **보안 분석용**으로는 가드레일 없는 로컬 모델을 따로 두는 이중 구성이 실무 해답에 가깝다.
2. **이번 주 축은 "메모리·컨텍스트 영속성"이다.** #3 OpenViking, #7 rowboat이 같은 문제를 서로 다르게 푼다. 특히 OpenViking의 **파일시스템 패러다임**(벡터 검색 대신 `ls`/`tree`로 탐색)은 감사 가능성 면에서 벡터 스토어보다 유리하다 — 무엇이 왜 로드됐는지 경로로 설명된다.
3. **프레임워크 이관 신호를 놓치지 말 것.** #5 AutoGen 유지보수 모드는 개인 스택에 직접 영향이다. 다만 1차 미확인이므로 **공식 저장소 상태를 직접 보고** 판단할 것.
4. **방법론이 도구화되고 있다.** #2 Superpowers는 "스킬"이 단발 기능이 아니라 **SDLC 전체를 강제하는 프레임워크**로 커지는 흐름을 보여준다. 다만 방법론 강제는 작업 성격에 따라 순수 오버헤드가 된다.

## 전일 대비 변화

- **테마 이동**: 보안·아이덴티티(07-23) → **메모리·컨텍스트 영속성 + 로컬 격리 런타임**.
- **07-23 #1(HF 브리치)의 후속**이 정책 논쟁으로 전개됐다(#1). 사건 → 대응 → 규제/개방 논쟁 순으로 축이 옮겨가는 중.
- **조사 품질은 어제보다 낮다.** DISCOVERY 스윕 6건 중 5건이 중복이라 커뮤니티 실측 근거가 거의 남지 않았고, 이번 판 10건 중 **신뢰도 '낮음'이 6건**이다. 어제(낮음 3건)보다 후퇴했다.
- **개선 필요**: 스윕이 30일 누적 참여도로 랭킹해 매일 같은 항목을 반환한다. 윈도우 축소나 GitHub API 직접 관측 경로 추가를 검토해야 한다(아래 open query).

## 이월 open query

1. **DISCOVERY 중복 문제** — 30일 윈도우 + 누적 참여도 랭킹이 구조적으로 같은 항목을 재부상시킨다. 윈도우 축소(`--days=7`) 또는 이전 리포트 항목을 스윕 단계에서 제외하는 방식 중 선택 필요.
2. **GitHub 지표 직접 관측** — 별 수·성장률을 2차 집계로 인용하다 이번에 4배 상충(#2)을 만났다. GitHub API로 두 시점 스냅샷을 남기는 파이프라인이 필요하다.
