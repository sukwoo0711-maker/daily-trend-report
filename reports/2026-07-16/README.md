# 🧰 AI Personal Stack 트렌드 리포트 — 2026-07-16 (TOP 10)

> **검증 상태: `LEGACY_UNVERIFIED`** — 이 보고서는 현재의 [근거 계약](../../METHODOLOGY.md) 도입 전 작성됐습니다. 수치·링크·“인기도” 순위는 재사용 전에 원문과 관측 시점을 다시 확인하십시오.

> **조사 방식**: last30days 방식 — 최근 30일(2026-06-16 ~ 2026-07-16) 웹 리서치 기반.
> **범위**: AI Personal Stack 구축에 유용한 것만 — 사용 방법론, 자동화, Skills, MCP, GitHub Rising Star.
> **제외**: 일반 뉴스, 모델 출시 소식, 정책/시장 동향, 에이전틱 브라우저, **이전 리포트에서 이미 다룬 항목**.
> **정렬 기준**: 인기도(스타 수·성장 속도·언급량 추정) 내림차순.

## 요약 순위표

| 순위 | 트렌드 | 분류 | 인기도 근거 |
|---|---|---|---|
| 1 | 에이전트 메모리 레이어 (Mem0·Zep·Letta) | 방법론/인프라 | Mem0 ⭐51k+, 개발자 10만+ |
| 2 | Claude Code 플러그인 마켓플레이스 생태계 | Skills/생태계 | 월 방문 30만+, 설치 수십만 단위 |
| 3 | Nanobot — 셀프호스팅 개인 에이전트 런타임 | Rising Star | ⭐44.2k |
| 4 | Chatterbox 등 로컬 보이스 스택 | 로컬 스택 | ⭐25.1k + 보이스 클러스터 급성장 |
| 5 | DeepTutor — 에이전트 네이티브 학습 플랫폼 | Rising Star | ⭐24.8k |
| 6 | ai-job-search — Claude Code 구직 자동화 | 자동화 | ⭐19k, 월 +5.6k 최고 성장세 |
| 7 | OpenFang — 32MB Rust 에이전트 OS | Rising Star | ⭐17.8k |
| 8 | oMLX 등 Apple Silicon 로컬 추론 붐 | 로컬 스택 | ⭐16.6k + 클러스터 9종 |
| 9 | LEANN·turbovec — 벡터 스토리지 경량화 | 인프라 | ⭐11.9k / ⭐11.5k |
| 10 | 에이전트 샌드박스·자격증명 보안 | 보안 | OpenSandbox ⭐11.5k 외 클러스터 |

---

## 상세

### 1. 에이전트 메모리 레이어: Mem0 · Zep · Letta 🧠
2026년 메모리는 자체 벤치마크와 연구 문헌을 가진 1급 아키텍처 컴포넌트로 승격. Mem0(⭐51k+, 개발자 10만+)의 4월 신규 알고리즘이 LongMemEval 시간축 검색을 49.0% → 93.4%로 끌어올리며 Zep(Graphiti 시간 지식그래프)과의 격차를 해소. Letta(구 MemGPT)는 ⭐13k+. 신흥주자 MemOS(⭐9.9k)·memU(⭐13.9k)도 급성장 — 개인 에이전트에 "나를 기억하는 능력"을 붙이는 표준 계층.
- 출처: [Mem0 — State of AI Agent Memory 2026](https://mem0.ai/blog/state-of-ai-agent-memory-2026), [Atlan](https://atlan.com/know/best-ai-agent-memory-frameworks-2026/), [Developers Digest](https://www.developersdigest.tech/blog/best-ai-agent-memory-providers-2026)

### 2. Claude Code 플러그인 마켓플레이스 생태계 📦
스킬·서브에이전트·훅·MCP 서버를 하나로 묶는 플러그인이 배포 단위로 정착. Anthropic 공식 마켓 + 커뮤니티 마켓 + 독립 디렉터리(월 방문 30만+)가 공존하고, 최다 설치 플러그인은 수십만 설치 단위. `marketplace.json` 든 git repo 하나면 팀 전용 프라이빗 마켓도 구축 가능. wshobson/agents는 Claude Code·Codex CLI·Cursor·Gemini CLI를 아우르는 멀티하네스 마켓으로 확장.
- 출처: [DesignRevision — Claude Code Plugins Guide](https://designrevision.com/blog/claude-code-plugins), [claudemarketplaces.com](https://claudemarketplaces.com/), [wshobson/agents](https://github.com/wshobson/agents)

### 3. Nanobot — 셀프호스팅 개인 에이전트 런타임 🤖
HKUDS의 ⭐44.2k 프로젝트. Telegram·Discord·Slack 멀티채널 연동을 갖춘 자체 호스팅 개인 에이전트 런타임. 대형 프레임워크 없이 개인 서버에서 상시 구동되는 에이전트를 만드는 진입점으로 급부상.
- 출처: [AI Tool Radar — July 2026](https://aitoolradar.io/blog/open-source-ai-radar-july-2026)

### 4. Chatterbox 등 로컬 보이스 스택 🎙️
Resemble AI의 Chatterbox(⭐25.1k)가 23개+ 언어 크로스랭귀지 보이스 클로닝으로 로컬 TTS 표준 자리를 굳히는 중. Higgs Audio(⭐8.2k, 100개+ 언어), NeuTTS Air(⭐6.0k, 온디바이스 360M), MOSS-TTS 패밀리 등 7월 레이더에서 보이스가 독립 클러스터로 분류될 만큼 성장. 개인 스택의 음성 입출력을 구독 없이 로컬로 해결하는 흐름.
- 출처: [AI Tool Radar — July 2026](https://aitoolradar.io/blog/open-source-ai-radar-july-2026)

### 5. DeepTutor — 에이전트 네이티브 학습 플랫폼 🎓
HKUDS의 ⭐24.8k 프로젝트. 튜터링·퀴즈·지식베이스를 에이전트 중심으로 통합한 학습 플랫폼. '에이전트로 배우는' 개인 학습 스택이라는 새 카테고리를 열었다는 평가.
- 출처: [AI Tool Radar — July 2026](https://aitoolradar.io/blog/open-source-ai-radar-july-2026)

### 6. ai-job-search — Claude Code 구직 자동화 💼
Claude Code 위에 구축된 AI 구직 지원 프레임워크. ⭐19k에 이번 달 +5.6k로 추적 대상 중 최고 성장세. 코딩 도구인 Claude Code가 '삶의 워크플로 자동화' 기반으로 쓰이는 대표 사례 — 개인 스택 확장 방향의 시그널.
- 출처: [findarepo Trending](https://findarepo.com/trending/), [OrangeBot.AI](https://orangebot.ai/github-trending-today)

### 7. OpenFang — 32MB Rust 에이전트 OS ⚙️
⭐17.8k. 약 32MB 단일 바이너리에 WASM 샌드박스를 내장한 Rust 자율 에이전트 OS. 무거운 Python 스택 없이 저사양 머신·서버에 개인 에이전트를 올리는 초경량 대안.
- 출처: [AI Tool Radar — July 2026](https://aitoolradar.io/blog/open-source-ai-radar-july-2026)

### 8. oMLX 등 Apple Silicon 로컬 추론 붐 🍎
oMLX(⭐16.6k, 계층형 KV 캐시·멀티모델 서빙)를 필두로 7월 레이더에 Apple Silicon 특화 프로젝트만 9종 등장 — claude-code-local(Claude Code 워크플로 오프라인 구동), DreamServer(llama.cpp+Open WebUI+Whisper+ComfyUI 원커맨드 번들), vllm-mlx 등. 맥 한 대로 완결되는 로컬 스택이 하나의 장르로 성립.
- 출처: [AI Tool Radar — July 2026](https://aitoolradar.io/blog/open-source-ai-radar-july-2026)

### 9. LEANN · turbovec — 벡터 스토리지 경량화 🗜️
LEANN(⭐11.9k)은 임베딩을 선택적으로 재계산해 스토리지 97% 절감을 주장하는 벡터 DB, turbovec(⭐11.5k)은 TurboQuant 압축의 Rust SIMD 구현. 개인 노트북에서 대규모 RAG를 돌리는 비용 장벽을 낮추는 인프라 흐름.
- 출처: [AI Tool Radar — July 2026](https://aitoolradar.io/blog/open-source-ai-radar-july-2026)

### 10. 에이전트 샌드박스·자격증명 보안 🔐
에이전트에게 실행 권한을 주는 시대의 방어 계층이 클러스터로 성장: OpenSandbox(⭐11.5k, K8s 멀티언어 샌드박스), forkd(Firecracker 마이크로VM 스냅숏), nono(OS 수준 최소권한), Agent Vault(프롬프트 인젝션 경유 자격증명 유출 차단 브로커). 스킬·MCP를 늘릴수록 필수가 되는 안전장치.
- 출처: [AI Tool Radar — July 2026](https://aitoolradar.io/blog/open-source-ai-radar-july-2026)

---

## 오늘의 스택 시사점

1. **즉시 적용**: 메모리 레이어(#1)는 Claude Code 파일 메모리와 별개로 개인 에이전트 프로젝트에 Mem0/memU를 붙여볼 가치 — 데일리 봇류(filmmakers-monitor 등)와 궁합이 좋음.
2. **도입 검토**: 플러그인 마켓플레이스(#2)로 흩어진 스킬·훅을 번들화하면 `.claude/` 수동 복사가 사라짐.
3. **주의**: 에이전트에 실행 권한·자격증명을 주는 구성이 늘면 #10의 샌드박스/크리덴셜 브로커가 선택이 아닌 전제가 됨.

## 전일 대비 변화

- **신규 진입**: 전체 10건 (오늘부터 이전 리포트 기수록 항목 제외 규칙 적용 — 어제 TOP 20과 중복 없음)
- **규칙 변경**: 에이전틱 브라우저 카테고리 영구 제외
- **차순위 주목**: claude-obsidian(⭐7.9k, Obsidian 볼트 자동 정리), omnigent(⭐5.0k, 멀티 코딩에이전트 오케스트레이터), OpenWiki(에이전트 문서 자동 유지), OpenKB(⭐2.7k, 문서→위키 지식베이스)

---

*생성: Claude Code 자동 트렌드 리서치 · 조사 기간: 2026-06-16 ~ 2026-07-16*
