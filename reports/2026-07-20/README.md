# 🧰 AI Personal Stack 트렌드 리포트 — 2026-07-20 (TOP 10)

> **조사 방식**: last30days 스킬(v3.16.0) DISCOVERY 스윕(Reddit·HN·Digg 실측 참여도) + 웹 리서치 보강. 조사 윈도우: 2026-06-20 ~ 2026-07-20.
> **범위**: AI Personal Stack 구축에 유용한 것만 — 사용 방법론, 자동화, Skills, MCP, GitHub Rising Star.
> **제외**: 일반 뉴스, 모델 출시 소식, 정책/시장 동향, 에이전틱 브라우저, **최근 7일 내 리포트에서 다룬 항목**.
> **정렬 기준**: 인기도(스타 수·성장 속도·실측 참여도) 내림차순.

## 요약 순위표

| 순위 | 트렌드 | 분류 | 인기도 근거 |
|---|---|---|---|
| 1 | 에이전트 메모리 설계 논쟁 ("저장+RAG는 잘못된 기본값") | 방법론 | HN 868pt·댓글 663 (실측) |
| 2 | Strix — AI 침투테스트 에이전트 | 보안/Rising Star | 주당 +7,000 스타 |
| 3 | Orca · herdr — 병렬 에이전트 코디네이션 신작 | 자동화 | 주간 트렌딩 리더 |
| 4 | OmniRoute — 로컬 AI 게이트웨이 | 인프라 | 주간 트렌딩 리더 |
| 5 | CubeSandbox — 하드웨어 격리 샌드박스 | 보안/인프라 | 주간 트렌딩 리더 (Tencent) |
| 6 | Impeccable — AI 코딩 디자인 안티패턴 라이브러리 | Skills | 주간 트렌딩 리더 |
| 7 | Destructive Command Guard — 위험 명령 차단 훅 | 보안 | 데일리 무버 |
| 8 | Marketing Skills — 비개발 직군 스킬팩 | Skills | 데일리 무버 |
| 9 | Agent Skill Ninja — 스킬 검색·설치 MCP | MCP/Skills | 140+ 스킬 인덱스 |
| 10 | 문서→구조화 추출 스택 (Hyper-Extract 외) | 인프라 | 클러스터 합산 ⭐7k+ |

---

## 상세

### 1. 에이전트 메모리 설계 논쟁: "저장 + RAG는 잘못된 기본값" 🧠
"1년간 에이전트 메모리를 만들고 내린 결론 — save everything + RAG it은 잘못된 기본값"이라는 스레드가 HN 868pt·댓글 663, 총 상호작용 1,781회(last30days 실측, velocity 903)로 이번 주 방법론 담론 1위. 7/16 리포트의 메모리 프레임워크(Mem0 등)가 '무엇을 쓸까'였다면, 이번엔 '어떻게 설계할까'(선별 저장·계층화·시간축)로 논점 이동. magic-context("코딩 에이전트의 해마"), memanto 등 계층형 메모리 신작들이 이 노선의 제품화 사례.
- 출처: last30days DISCOVERY 실측 (r/AI_Agents·r/Rag·HN), [AI Tool Radar — July 2026](https://aitoolradar.io/blog/open-source-ai-radar-july-2026)

### 2. Strix — AI 침투테스트 에이전트 🦉
정적 스캐너가 아니라 실제 보안 연구자처럼 동작하는 오픈소스 침투테스트 에이전트 — 애플리케이션을 동적으로 테스트하고 PoC 익스플로잇으로 취약점을 검증. **주당 약 +7,000 스타**로 이번 주 최고 성장 속도. 개인 프로젝트의 보안 점검을 에이전트에 맡기는 흐름의 선두.
- 출처: [GeekFence — Top 10 Trending AI Repos July 2026](https://geekfence.com/top-10-trending-ai-github-repositories-in-july-2026/)

### 3. Orca · herdr — 병렬 에이전트 코디네이션 신작 듀오 🎛️
Orca(stablyai)는 병렬 코딩 에이전트·워크트리·터미널·디자인 리뷰·핸드오프를 한 화면에 모은 데스크톱/모바일 워크스페이스, herdr는 여러 에이전트를 띄우고 관리하는 터미널 멀티플렉서. 7/19에 다룬 오케스트레이션 흐름이 '프레임워크'에서 '일상 운용 UI'로 내려온 단계 — 개인이 에이전트 여러 개를 굴리는 게 전제가 된 도구들.
- 출처: [GitHub Trending Radar — Weekly](https://www.ai.joaoqueiros.com/blog/github-trending-weekly-daily-ai-builder-repositories-july-2026)

### 4. OmniRoute — 로컬 AI 게이트웨이 🔀
프로바이더 라우팅·폴백·쿼터·텔레메트리를 로컬에서 처리하는 AI 게이트웨이. 모델 여러 개를 쓰는 개인 스택에서 "어떤 요청을 어떤 모델로, 실패하면 어디로"를 코드 밖에서 선언하는 계층 — 비용 관리와 신뢰성을 동시에 잡는 신규 카테고리.
- 출처: [GitHub Trending Radar — Weekly](https://www.ai.joaoqueiros.com/blog/github-trending-weekly-daily-ai-builder-repositories-july-2026)

### 5. CubeSandbox — 하드웨어 격리 에이전트 샌드박스 📦
Tencent Cloud의 동시 다발 에이전트 코드 실행용 하드웨어 격리 샌드박스. 7/16의 샌드박스 클러스터(OpenSandbox 등)에 이어 대형 클라우드 사업자가 직접 참전 — 에이전트 격리 실행이 니치가 아니라 표준 인프라로 굳는 신호.
- 출처: [GitHub Trending Radar — Weekly](https://www.ai.joaoqueiros.com/blog/github-trending-weekly-daily-ai-builder-repositories-july-2026)

### 6. Impeccable — AI 코딩 디자인 언어·안티패턴 라이브러리 🎨
pbakaus(구글 출신)의 디자인 스킬 — 7/19에 다룬 hallmark가 '컴팩트한 교정 스킬'이라면 Impeccable은 디자인 언어 + 커맨드셋 + 안티패턴 라이브러리를 갖춘 확장판. 디자인 스킬 장르가 단일 파일 → 체계화된 라이브러리로 진화 중.
- 출처: [GitHub Trending Radar — Weekly](https://www.ai.joaoqueiros.com/blog/github-trending-weekly-daily-ai-builder-repositories-july-2026)

### 7. Destructive Command Guard — 위험 명령 사전 차단 훅 🛑
에이전트가 실행하려는 셸 명령을 실행 전에 검사해 파괴적 명령(rm -rf류)을 차단하는 훅. 데일리 무버 진입. 7/19 펄스의 "Slack 자동응답 사고" 같은 무감독 자동화 리스크에 대한 가장 저비용 방어 — 훅 하나로 끝나 개인 스택 도입 장벽이 사실상 0.
- 출처: [GitHub Trending Radar — Daily Movers](https://www.ai.joaoqueiros.com/blog/github-trending-weekly-daily-ai-builder-repositories-july-2026)

### 8. Marketing Skills — 비개발 직군 스킬팩 📣
CRO·카피라이팅·SEO·그로스 워크플로를 재사용 가능한 스킬로 묶은 팩(coreyhaines31)이 데일리 무버 진입. 7/15의 claude-skills(337종)가 보여준 '코딩 어시스턴트 → 업무 전반 어시스턴트' 흐름이 마케팅 단일 도메인 전문 팩으로 분화.
- 출처: [GitHub Trending Radar — Daily Movers](https://www.ai.joaoqueiros.com/blog/github-trending-weekly-daily-ai-builder-repositories-july-2026)

### 9. Agent Skill Ninja — 스킬 검색·설치 MCP 🥷
GitHub의 SKILL.md들을 검색·설치·관리하는 MCP — 140+ 스킬 사전 인덱스, 워크스페이스 분석 기반 추천까지. 스킬이 2만 3천 개를 넘어선 생태계에서 '스킬을 찾는 도구'가 자체 카테고리로 등장.
- 출처: [ScriptByAI — Claude Code Resource List](https://www.scriptbyai.com/claude-code-resource-list/)

### 10. 문서→구조화 추출 스택 (Hyper-Extract · knowhere · MDFlux · PDF Oxide) 📄
텍스트를 그래프·표·하이퍼그래프로 변환하는 Hyper-Extract(⭐2.5k), 출처 인용 딸린 셀프호스팅 추출 레이어 knowhere(⭐1.8k), PDF·오피스→Markdown 데스크톱 앱 MDFlux, Rust PDF 라이브러리 PDF Oxide. 개인 지식베이스의 입구인 '문서 인제스천'이 독립 도구군으로 성숙.
- 출처: [AI Tool Radar — July 2026](https://aitoolradar.io/blog/open-source-ai-radar-july-2026)

---

## 오늘의 스택 시사점

1. **즉시 적용**: Destructive Command Guard(#7)는 훅 하나 추가로 끝 — 자동화 늘리기 전에 먼저 거는 안전벨트로 최적.
2. **도입 검토**: 모델을 2개 이상 쓰고 있다면 OmniRoute(#4)로 라우팅·폴백을 선언형으로 옮기는 것이 비용·신뢰성 모두에 이득.
3. **관찰**: 메모리 논쟁(#1)은 우리 파일 기반 메모리 운영에도 시사점 — '다 저장'보다 선별·계층화가 커뮤니티 합의로 수렴 중.

## 전일 대비 변화

- **중복 skip 내역 (신규 7일 규칙 적용)**: last30days DISCOVERY 6건 중 4건(Gemma 4 템플릿, 1인 기업 프레임워크, Slack 자동응답 실패담, "처음부터 시작한다면" 스택 토론)은 7/19 커뮤니티 펄스와 중복되어 제외. OpenCut·OpenWiki·ai-job-search·Vibe-Trading·DeepTutor도 7일 내 기수록으로 제외.
- **차순위 주목**: Codex Plugin CC(Claude Code 안에서 적대적 리뷰·위임), awesome-llm-apps(실행 가능한 예제 모음), SeekDB(⭐2.7k, ACID+벡터 하이브리드 DB), forge(⭐2.1k, 툴콜링 가드레일)

---

*생성: Claude Code 자동 트렌드 리서치 · last30days 스킬 DISCOVERY + 웹 보강 · 조사 기간: 2026-06-20 ~ 2026-07-20*
