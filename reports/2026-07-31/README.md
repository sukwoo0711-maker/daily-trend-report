# 🧰 AI Personal Stack 트렌드 리포트 — 2026-07-31 (채택 4건 + 보안 1건)

> **조사 방식**: 하이브리드 **2회차** — 뉴스·논쟁은 last30days 스킬(v3.16.0) DISCOVERY 스윕(2026-06-30 ~ 2026-07-30), 도구 발굴은 GitHub Search/Repos/Trees API 직접 관측(`created:>=2026-07-01`, 쿼리 4종). 파이프라인 전환 자체는 **07-30 1부에서 이미 시행**했고, 이번 판은 그 위에서 ① 07-30 #5의 보안 사안을 계정 단위로 확대 추적하고 ② 07-30이 "내용 검증 미완"으로 이월한 S등급 후보들을 판정한다.
> **범위**: AI Personal Stack 구축에 유용한 것만 — 사용 방법론, 자동화, Skills, MCP, GitHub Rising Star, 로컬/셀프호스팅, 에이전트 보안.
> **제외**: 일반 뉴스, 모델 출시 소식, 정책/시장 동향, 에이전틱 브라우저, **최근 7일 내(07-24~07-30) 리포트에서 다룬 항목**.
> **정렬 기준**: 보안·방법론 항목(등급 미적용) → 채택 등급 S → A, 각 그룹 안에서 관측 주목도순.
> **관측 시각**: **2026-07-31 00:07~00:40 KST (2026-07-30 15:07~15:40 UTC)**. 별 수·파일 크기·블롭 SHA는 이 시점 GitHub API 단일 스냅샷이며, **두 시점 스냅샷이 없으므로 증가율은 주장하지 않는다.**
> **출처 범위/누락**: 조회 = GitHub Search/Repos/Trees/Users API(직접, 인증됨) + last30days DISCOVERY(Reddit·HN·Digg) + 공개 웹 검색. 누락 = X·YouTube·TikTok(이번 런 미수집), Reddit 원문 permalink(DISCOVERY 요약 단계 유실 지속).

## 🚨 이번 판의 핵심 — 07-30 #5는 단발 사고가 아니라 계정 단위 캠페인이었다

07-30 1부 #5는 `0xwilliamortiz/andrej-karpathy-skills`(마크다운 가이드라인 저장소)에 Windows 바이너리가 동봉된 것을 G1 제외 사유로 기록했다. **이번 판은 같은 계정의 나머지 저장소 전체로 스캔을 넓혔고, 그 결과 단발 사고가 아니라는 것이 확인됐다.**

**동일한 블롭 하나(`79d051352df6…`, 804,688바이트)가 저장소 6개에 4개의 서로 다른 파일명으로 들어가 있다.**

| 저장소 | ★ | fork | 생성 | 그 블롭이 쓰는 이름 | 동봉 DLL |
|---|---|---|---|---|---|
| `openclaude-improved` | 559 | 80 | 07-26 | `bin/vibecodecalc.exe` | `bin/libcurl.dll` |
| `ponytail-improved` | 558 | 125 | 07-28 | `skills/ponytail/vibecodecalc.exe` | `skills/ponytail/libcurl.dll` |
| `andrej-karpathy-skills` | 545 | 94 | 07-21 | **`fastsetup.exe`** | `libcurl.dll` |
| `FlashKDA` | 192 | 27 | 07-29 | `csrc/smxx/vibecodecalc.exe` | `csrc/smxx/libcurl.dll` |
| `agents-council` | 173 | 19 | 07-20 | **`council-worker.exe`** | `.../scripts/libcurl.dll` |
| `yoinks` | 52 | 11 | 07-21 | **`yoinks.exe`** | `libcurl.dll` |
| **합계** | **≈2,079** | **356** | **10일 이내** | **전부 SHA `79d051352df6`** | (DLL은 SHA 제각각) |

읽어야 할 지점은 세 가지다.

**① 같은 파일이 저장소마다 이름만 바꿔 달린다.** `fastsetup.exe`·`council-worker.exe`·`yoinks.exe`·`vibecodecalc.exe`는 **바이트 단위로 같은 파일**이다(블롭 SHA 동일). 각 저장소의 맥락에 맞는 이름을 입혀 "여기 있을 법한 파일"처럼 보이게 한 것이다.

**② 주제가 서로 무관하다.** Claude Code 스킬팩, 에이전트 하네스 "개선판", 멀티 에이전트 플러그인, 동영상 다운로더, 그리고 **`FlashKDA`(CUDA 학습·디코드 커널)**. 마지막이 결정적이다 — **메모리 효율 CUDA 커널 저장소에 `vibecodecalc.exe`가 들어갈 이유는 없다.** 즉 저장소의 목적에서 파생된 파일이 아니라, 목적과 무관하게 주입되는 페이로드다.

**③ 유통 규모와 속도.** 6개 저장소가 **07-20 ~ 07-29 열흘 안에** 생성됐고 합계 약 2,079★·356fork다. `openclaude-improved`·`ponytail-improved`는 GitHub 기준 fork가 아니라 **인기 프로젝트 이름에 "-improved"를 붙인 별도 저장소**이며, 계정은 2024-01-07 생성인데 팔로워는 7명이고 나머지는 빈 저장소(`dfhdfh` 같은 설명)다. 별 2,000개와 팔로워 7명의 조합 자체가 신호다.

**단정하지 않는 것**: 이 실행 파일을 **다운로드·실행·역공학하지 않았다.** 따라서 악성 여부는 이 리포트의 주장이 아니다. 다만 채택 판정에는 그 단정이 필요 없다 — **무엇을 하는지 확인할 수 없는 서명 없는 실행 파일**이고, 그중 하나(`andrej-karpathy-skills`)는 README가 그것을 **권장 설치 경로**로 안내한다. G1 제외로 충분하다.

**실무 조치**: 위 6개 저장소는 별 수와 무관하게 신뢰하지 말 것. 이미 클론했다면 해당 `.exe`/`.dll`을 실행한 적이 있는지 확인할 것. 스킬만 필요하다면 마크다운 파일만 골라 복사하고 바이너리는 가져오지 말 것.

**게이트 개정(즉시 적용)**: 바이너리 스캔을 **저장소 단위에서 계정 단위로 승격**한다. 07-30 시점의 저장소 단위 스캔은 `andrej-karpathy-skills` 한 건만 잡았고, 나머지 5개(합계 1,534★)는 놓쳤다. 아래 시사점 1에 명령을 남긴다.

## ⚠ 게이트/중복으로 제외한 항목(투명 처리)

별 수는 모두 2026-07-31 00:07~00:40 KST 관측.

| 반환 항목 | 처리 | 사유 |
|---|---|---|
| `Sahir619/fable-method` (1,972★, MIT) | **제외** | **07-30 1부 #1 중복.** 이번 스윕에서도 최상위로 올라왔으나 7일 중복 규칙 적용 |
| `Kulaxyz/self-learning-skills` | **제외** | **07-30 1부 #2 중복** |
| `xai-org/grok-build` (23,532★, Apache-2.0, 07-14) — 이번 창 최대 신규 저장소 | **제외** | **G4 설치 필요**(코딩 에이전트 하네스 본체 + TUI). B등급 예외 요건("쓰던 게 EOL") 미해당 |
| `lopopolo/harness-engineering` (2,407★, 07-18) | **제외(판정 보류)** | **G3** — CC-BY-4.0은 통과 목록(MIT·Apache-2.0·BSD·ISC) 밖. 다만 이것이 규칙의 허점일 수 있어 아래 open query 1로 올린다 |
| `QoderAI/better-harness` (1,193★, MIT) | **제외** | **G4** — 호스트별 플러그인 설치 + Node ≥ 22.20.0 (07-30도 동일 사유로 제외) |
| `Intuition-Lab/personal-model` (1,267★, Apache-2.0) — **07-30 이월분** | **제외(판정 완료)** | **G4** — 43 MB 파이썬 애플리케이션(`clients/`·`connectors/`), macOS 중심. 07-30이 "검증 미완"으로 남긴 건을 이번 판에서 닫는다 |
| `VictorTaelin/OptMem` (906★, 07-25) — "426토큰 프롬프트 + 스크립트" | **제외** | **G3 라이선스 파일 없음.** 형태는 A등급감이지만 확인 못 한 것은 추천하지 않는다 |
| `Kulaxyz/token-diet` (513★, 07-03) — "평균 31% 청구 절감" | **제외** | **G3 라이선스 파일 없음.** 토큰 절감은 이 스택의 최우선 관심사지만 동일 원칙 적용(같은 소유자의 `self-learning-skills`는 MIT라 07-30에 채택됐다 — 저장소별로 다르다) |
| `KinetiNode/claude-fable-5-system-prompt-clean` (431★) | **제외** | 유출된 벤더 시스템 프롬프트 재배포물. 재배포자의 MIT 표기는 **원저작물에 미치지 않음** → 라이선스 상태 불명(G3) |
| `vshulcz/deja-vu` (498★, MIT) | **제외** | **G4** 바이너리 설치. (단 "LLM·임베딩 없이 hit@1 84.9%" 주장은 BM25 우선 노선과 같은 방향이라 관찰 대상으로 기록) |
| DISCOVERY #2 — OpenAI/HuggingFace 브리치 | **제외** | **07-23 #1 계열 중복 — 6판 연속**(07-30은 침입 기술 타임라인이라는 새 각도로만 게재) |
| DISCOVERY #1·#3 — "정치인용 LLM 증류 설명"(HN 1,818pt), Kimi K3 로컬 압축 | **제외** | **범위 외** — 각각 유머 스레드, 모델 출시 |
| DISCOVERY #5 — "다들 첫날 소감만 올린다, 한 달 뒤에도 남은 건?" | **제외** | **클러스터 오염.** 엔진 로그상 `r/BodyHackGuide` 결과 7건이 같은 클러스터에 섞였고 대표 코멘트도 그쪽이다 → 539댓글 집계를 주제 근거로 인용할 수 없음(open query 4) |
| DISCOVERY #6 — Agent-Manager (tmux TUI) | **제외** | **G4 설치 필요**, 참여도도 얕음(HN 92pt) |

## 요약 순위표

| 순위 | 트렌드 | 등급 | 라이선스 | 분류 | 관측 근거·시점 | 신뢰도 |
|---|---|---|---|---|---|---|
| 1 | 스킬·에이전트 저장소 공급망 — **동일 실행파일이 한 계정 6개 저장소에 4개 이름으로 재배포**(≈2,079★) | N/A(보안) | — | 보안/공급망 | GitHub Trees/Users API 직접 관측(블롭 SHA·크기·생성일·fork 수), 07-31 00:07~00:40 KST | **높음**(메타데이터 한정) |
| 2 | `Nanako0129/pilotfish` — 프런티어가 계획, 싼 모델이 실행 (설정 3파일, 런타임 코드 0) | **S** | MIT | 자동화/비용 | GitHub API: 547★, 생성 07-08, 최종 푸시 07-29, 바이너리 스캔 CLEAN | 중간~높음 |
| 3 | `Neeeophytee/finding-unknowns-skills` — `context-audit`·`progressive-disclosure` 등 11종 | **S** | MIT(LICENSE 원문 확인) | Skills/컨텍스트 | GitHub API: 283★, 생성 07-05, md 18, 하네스 3종 매니페스트, CLEAN | 중간 |
| 4 | `anthropics/code-migration-kit-with-claude-code` — 6단계 게이트형 대규모 이식 킷 | **S** | Apache-2.0(LICENSE 원문 확인) | 이식/방법론 | GitHub API: 253★, 생성 07-08, 프롬프트 8종 + SKILL.md, CLEAN | 중간~높음 |
| 5 | `sunflower-of-parchman/codex-hygiene` — 읽기 전용 컨텍스트·텔레메트리 감사 (**07-30 이월분 판정 완료**) | **A** | MIT | 컨텍스트/진단 | GitHub API: 250★, import 전수 확인 = **stdlib only**, CLEAN | 중간 |

---

## 상세

### 1. 동일 실행파일이 6개 저장소에 이름만 바꿔 배포됐다 🚨

관측 내용과 게이트 판정은 위 핵심 절에 표로 정리했다. 여기서는 **이 사례가 채택 절차에 남기는 교훈**만 적는다.

**교훈 1 — 저장소 단위 검사는 부족하다.** 07-30 시점에 저장소 하나만 스캔해서 한 건을 걸렀지만, 같은 계정의 나머지 5개(합계 1,534★)는 그대로 남아 있었다. **소유자를 축으로 한 번 더 훑는 비용은 API 호출 몇 번**이고, 이번엔 그 한 단계가 5건을 추가로 잡았다.

**교훈 2 — 별 수는 검증이 아니다.** 6개 저장소 합계 약 2,079★·356fork다. 별이 500개 넘는 저장소가 세 개 있고, 그중 둘은 인기 프로젝트 이름에 `-improved`를 붙인 것이다. **이름의 친숙함과 별 수는 신뢰의 근거가 될 수 없다**는 것이 이 사례의 실증이다.

**교훈 3 — 도메인이 다른 저장소일수록 오히려 티가 난다.** `FlashKDA`는 CUDA 커널 저장소다. 스킬팩에 있는 `.exe`는 "설치 도우미인가 보다" 하고 넘어갈 수 있지만, **커널 저장소의 `csrc/smxx/vibecodecalc.exe`는 설명이 되지 않는다.** 계정 단위로 훑으면 이런 불일치가 드러난다.

- 1차 출처: GitHub API 직접 관측 — [`users/0xwilliamortiz/repos`](https://github.com/0xwilliamortiz?tab=repositories), 각 저장소의 `git/trees/HEAD?recursive=1`(블롭 SHA·크기), `repos/{owner}/{repo}`(생성일·별·fork), `andrej-karpathy-skills`의 README·`gup.xml` 원문. 관측 2026-07-31 00:07~00:40 KST.
- 보조 관측: `andrej-karpathy-skills`의 `gup.xml`은 Notepad++ 업데이터(WinGup)의 설정 파일 원문이며 LGPL-3.0 헤더를 포함한다 — MIT를 표방하는 저장소의 라이선스 표기와도 일치하지 않는다(G3 추가 위반). 바이너리 3종은 최초 커밋 6일 뒤 웹 UI `Add files via upload`로 추가됐다.
- 반대 근거/한계: **실행 파일을 다운로드·실행·분석하지 않았다.** 악성 판정은 하지 않으며, 편의용 인스톨러를 반복 커밋했을 가능성도 배제하지 않는다. 다만 그 가능성이 참이더라도 `FlashKDA`에 들어간 이유는 설명되지 않는다. 동봉 `libcurl.dll`은 저장소마다 SHA가 달라(802~806 KB) 동일 파일이 아니다 — **이름만 같고 빌드가 다르다.** 계정 1개·표본 6개이므로 "생태계 전반의 추세"로 일반화하지 말 것.
- 신뢰도: **높음(메타데이터에 한해)** — 블롭 SHA 동일성, 파일명, 크기, 생성일, 별·fork 수는 전부 1차 API로 직접 확인. 실행 동작에 대한 주장은 없음.

### 2. `Nanako0129/pilotfish` — 프런티어가 계획하고 싼 모델이 실행한다, 설정 파일 3개로 🐟
**MIT · 547★ · 생성 2026-07-08 · 최종 푸시 07-29(이번 채택분 중 가장 활발) · 바이너리 스캔 CLEAN**

이름 그대로 "큰 놈 옆에서 잔일을 하는 작은 물고기" 구조다. **비싼 모델은 계획·판정만 하고, 검색·기계적 편집·테스트 실행·문서 갱신 같은 물량 작업은 싼 모델 서브에이전트가 처리하며, 수용 경계 리뷰만 새 컨텍스트의 상위 모델이 다시 본다.** 설치되는 실체는 세 층뿐이다 — 머신 설정(`settings.json`: 누가 오케스트레이션하고 폴백 체인은 무엇인지), 역할(`agents/*.md`: 8개 역할을 각각 적정 등급과 권한 표면에 프런트매터로 고정), 정책(`CLAUDE.md`: **모델 이름이 아니라 역할 언어로** 위임 방법을 기술). 저장소 표현으로 **"설정 파일 세 개 분량, 런타임 코드 없음"** 이고, 실제로 트리의 `.js`·`.py` 22개가 전부 `benchmarks/` 픽스처임을 직접 확인했다.

근거 측면에서 특이한 점은 **자기 벤치가 아니라 벤더 공식 수치를 인용**한다는 것이다: 오케스트레이터를 상위 모델로 두고 워커를 한 단계 낮춘 구성이 **전량 상위 모델 대비 성능 96%를 비용 46%에** 낸다(BrowseComp 86.8% vs 90.8%, 문제당 $18.53 vs $40.56). 구독제에서는 이점이 하나 더 붙는데, 주간 한도가 "전체 모델 버킷 + 중급 모델 전용 추가 버킷" 2중 구조라 실행을 중급 모델로 내리면 **단가와 별개로 전용 여유분을 더 쓰게 된다.** 실무 함정도 적혀 있다 — 특정 버전 이후 내장 탐색 서브에이전트가 **메인 세션 모델을 상속**해서, 메인이 최상위 모델이면 백그라운드 검색마다 최상위 등급 토큰을 태운다는 것.

**이 스택에 붙는 자리**: `frugal-agent-stack`(3-도구 저비용 전략)과 `model-downgrade-eval`(다운그레이드 가부 판정)의 **구현체 레퍼런스**다. 07-30 #1(fable-method)이 "왜 낮은 등급 모델이 절차를 따를 수 있는가"를 다뤘다면, 이건 **그 절차를 어느 등급에 어떻게 배치하는가**다 — 같은 문제의 다른 층이라 중복이 아니다. 설치물이 설정·마크다운뿐이라 회사 PC 이식 부담이 사실상 없고, "역할 언어로만 쓰고 모델 이름은 설정에 격리"는 하네스가 바뀌어도 옮겨지는 규칙이다.
- 1차 출처: [GitHub — Nanako0129/pilotfish](https://github.com/Nanako0129/pilotfish), [`install/AGENT-INSTALL.md`](https://github.com/Nanako0129/pilotfish/blob/main/install/AGENT-INSTALL.md), [`templates/`](https://github.com/Nanako0129/pilotfish/tree/main/templates)
- 반대 근거/한계: **특정 하네스 종속이다** — `~/.claude/`에 쓰고 하네스 버전 하한(2.1.219+)이 있으며, 낮으면 설치 프로그램이 변경 전에 멈춘다. 인용된 96%/46%는 **벤더 자기 측정**이고 워크로드가 다르면 재현되지 않는다. 저장소가 **널 결과도 공개**했다 — 어떤 구독 환경에서는 상위 도구 계약이 위임을 막아 **명시 지시 없이는 디스패치가 0**이었고 압축판·대조군 모두 같았다. 원격 문서를 읽혀 설치하는 편의 경로는 프롬프트 인젝션 표면이므로 **핀 고정 로컬 체크아웃 경로**를 쓸 것(저장소도 그렇게 권한다).
- 신뢰도: 중간~높음 — 구조·라이선스·설치물 형태·바이너리 부재는 1차 확인. **성능·비용 수치는 벤더 자기주장 인용.**

### 3. `Neeeophytee/finding-unknowns-skills` — 컨텍스트 감사·점진 공개를 스킬로 고정 🔍
**MIT(LICENSE 원문 직접 확인) · 283★ · 생성 2026-07-05 · 최종 푸시 07-28 · md 18 · 바이너리 스캔 CLEAN**

"비용이 커지기 전에 모르는 것을 찾아낸다"는 목표로 묶인 스킬 11종이다: `blindspot-pass`, `brainstorm-prototypes`, `interview-me`, `reference-hunt`, `implementation-plan`, `implementation-notes`, `pitch-packager`, `change-quiz`, 그리고 **`context-audit`·`progressive-disclosure`·`agent-interface-design`**. 뒤 세 개가 이 스택에 직접 걸린다 — **07-27 #1의 컨텍스트 엔지니어링 새 규칙(전부 앞단에 싣지 말고 점진 공개, 예시 대신 인터페이스 설계)을 원리 설명이 아니라 실행 가능한 스킬로 고정한 형태**이기 때문이다. 07-27 #1이 "무엇을 해야 하는가"였다면 이건 "그걸 매번 어떻게 돌리는가"다.

07-30 #3(HANDBOOK.md 벤치마크: 긴 정책문서를 준 에이전트가 엄격 채점에서 최고 36.2%)과 함께 읽으면 쓰임이 분명해진다. **긴 규칙 문서가 안 지켜진다면, 규칙을 더 쓰는 게 아니라 컨텍스트에 무엇이 올라가는지를 감사해야 한다.** `context-audit`이 정확히 그 자리다. 매니페스트가 `.claude-plugin`·`.codex-plugin`·`.agents` 세 벌로 들어 있어 **하네스 3종을 같은 마크다운으로 커버**한다.

**이 스택에 붙는 자리**: `instruction-hygiene`(context rot 대응)과 정면으로 겹친다. 겹침은 배제 사유가 아니라 **대조군으로서의 가치**다 — `instruction-hygiene`는 T0 결정론 검사 우선이고 이쪽은 스킬 기반 감사이므로, 같은 문제를 다른 방법으로 푼 결과를 비교할 수 있다.
- 1차 출처: [GitHub — Neeeophytee/finding-unknowns-skills](https://github.com/Neeeophytee/finding-unknowns-skills), [`skills/`](https://github.com/Neeeophytee/finding-unknowns-skills/tree/main/skills), LICENSE 원문
- 반대 근거/한계: **GitHub API는 라이선스를 `NOASSERTION`으로 반환한다.** LICENSE 파일 본문을 직접 읽어 표준 MIT임을 확인하고 통과시켰다(open query 2). 스킬 11종의 **실효성 근거·eval이 저장소에 없다** — 07-30 #1(fable-method)과 달리 검증 로그가 없고, 개수는 품질이 아니다. 스킬을 무더기로 얹는 것 자체가 07-27 #1과 07-30 #3이 경고한 컨텍스트 비대의 원인이 되므로 **`context-audit`·`progressive-disclosure` 2개만 골라 쓰는 편**이 취지에 맞다. 저장소도 스스로 "커뮤니티 증류물이며 벤더 공식이 아님"을 명시한다.
- 신뢰도: 중간 — 저장소·라이선스·구성·바이너리 부재는 1차 확인, **효과 근거 없음.**

### 4. `anthropics/code-migration-kit-with-claude-code` — "판정자가 없으면 종료 조건도 없다" 🔀
**Apache-2.0(LICENSE 원문 확인, Copyright 2026 Anthropic, PBC) · 253★ · 생성 2026-07-08 · 바이너리 스캔 CLEAN**

대규모 언어 이식(같은 아키텍처·같은 자료구조, 새 언어)을 **6단계 게이트**로 진행하는 프롬프트 8종 + `SKILL.md` + 템플릿 모음이다. 이 스택의 이식 작업과 겹치는 지점이 셋이다.

첫째, **0번 단계가 "이식하지 마라"를 유효한 결과로 인정한다.** `prompts/00-feasibility.md`는 읽기 전용 보고서를 만들어 "남는 쪽의 논거", 검증 비용, 기존 테스트의 생존 여부를 committed call로 적게 한 뒤 판정한다.

둘째, **판정자를 먼저 세우게 강제한다.** *"No judge, no exit condition."* 기존 테스트가 공개 표면을 때리면 그게 판정자이고, 옛 언어의 내부 구현에 의존해 함께 죽는다면 **이식 가능한 parity harness를 먼저 만들어 원본과 '일부러 망가뜨린 코드' 양쪽에 대해 검증**한 뒤에야 번역을 시작한다. 통과만 보는 게 아니라 **실패를 잡아내는지까지 확인**하는 구조다.

셋째, **하드 게이트를 프롬프트에 박아뒀다.** 번역 팬아웃 전에 `templates/settings.json`(거부 규칙)을 대상 저장소에 깔아야 하고, **프롬프트 03·04는 그 파일의 존재를 확인하고 없으면 중단한다.** README는 이유까지 적었다 — *"초기 테스트에서 이 단계가 조용히 건너뛰어졌고 아무것도 잡아내지 못했다."*

**이 스택에 붙는 자리**: 회사 PC 이식 작업과 `arch-boundary-lint`(C/C++ 계층 경계 린터)의 상위 절차에 해당한다. "게이트를 통과 못 하면 다음 단계로 못 감"은 `auto-grill`의 하드 게이트, `instruction-hygiene`의 결정론 검사와 같은 설계다. 스크립트(`depmap_c.py` 등)는 선택 사항이고 **핵심 산출물은 프롬프트·템플릿 마크다운**이라 이식 부담이 없다.
- 1차 출처: [GitHub — anthropics/code-migration-kit-with-claude-code](https://github.com/anthropics/code-migration-kit-with-claude-code), [`prompts/`](https://github.com/anthropics/code-migration-kit-with-claude-code/tree/main/prompts), [`templates/settings.README.md`](https://github.com/anthropics/code-migration-kit-with-claude-code/blob/main/templates/settings.README.md)
- 반대 근거/한계: 저장소가 스스로 **"참조용 코드이며 적극적으로 유지보수하지 않음, 이슈·PR 미확인"** 이라고 명시한다(07-08 이후 푸시 없음). 프롬프트는 실제 전사물이 아니라 **재구성물**이라는 것도 저장소가 밝혔다 — 실제 산출물은 "더 지저분하고 더 구체적"이었으며 참조 사례로 든 대규모 포트의 실제 "프롬프트"는 576줄 룰북이었다고 한다. **성공률·소요시간 같은 효과 수치는 없다.** GitHub API는 라이선스를 `NOASSERTION`으로 반환하지만 LICENSE 파일은 표준 Apache-2.0이다.
- 신뢰도: 중간~높음 — 1차 저장소(벤더 공식 계정), 라이선스·구성·게이트 설계 직접 확인. **효과에 대한 정량 근거 없음.**

### 5. `sunflower-of-parchman/codex-hygiene` — 표준 라이브러리만 쓰는 읽기 전용 컨텍스트 감사 🧹
**MIT · 250★ · 생성 2026-07-07 · SKILL.md 1 + `.py` 2 + `.sh` 2 · 바이너리 스캔 CLEAN · 07-30 이월분 판정 완료**

07-30이 "게이트 위반은 확인되지 않았으나 내용 검증을 완료하지 못했다"며 이월한 후보다. **이번 판에서 검증을 끝내고 A등급으로 채택한다.**

특정 하네스의 **현재 컨텍스트·도구 표면을 측정하고 1~90일 활동을 되돌아보는 읽기 전용 스킬**이다. 산출물이 관측·해석·미상을 분리해 적고, 근거가 어디서 끊기는지 명시하며, **측정 후에야 되돌릴 수 있는 정리 단계를 제안**한다. 도구 목록·스레드별 토큰 텔레메트리, 설치된 플러그인·MCP 상태, 명시적 컴팩션 횟수, 관측된 `SKILL.md` 읽기 횟수까지 집계한다.

**A등급 판정 근거는 직접 확인했다.** `scripts/codex_activity_review.py`의 import를 전수 확인한 결과 `argparse`·`collections`·`datetime`·`hashlib`·`json`·`os`·`pathlib`·`re`·`shutil`·`sqlite3`·`statistics`·`subprocess`·`sys`·`typing`·`urllib.parse` — **전부 파이썬 표준 라이브러리, 서드파티 의존 0**이다. 이미 있는 런타임으로 돌고 새 프로그램 설치가 없다(G4 통과). 설치는 스킬 디렉터리에 클론하는 것이 전부다.

**이 스택에 붙는 자리**: 07-27 #1의 "컨텍스트를 덜어내라"와 07-30 #3의 "긴 규칙은 안 지켜진다"를 **측정 가능하게** 만든다. `instruction-hygiene`가 규칙 문서의 군살을 잡는다면, 이건 **런타임에서 실제로 무엇이 얼마나 로드됐는지**를 잰다 — 재고 나서 덜어내는 순서가 맞다.
- 1차 출처: [GitHub — sunflower-of-parchman/codex-hygiene](https://github.com/sunflower-of-parchman/codex-hygiene), [`SKILL.md`](https://github.com/sunflower-of-parchman/codex-hygiene/blob/main/SKILL.md), `scripts/codex_activity_review.py` import 전수 확인
- 반대 근거/한계: **특정 하네스 전용이다** — 그 하네스의 로컬 텔레메트리 파일 구조를 읽으므로 다른 하네스로 그대로 옮겨지지 않는다(원리는 이식 가능, 구현은 아님). 프라이버시 주장("로그·설정·도구 스키마·시크릿·환경값은 비공개 유지")은 **저장소 자기주장**이며 스크립트 전체를 라인 단위로 감사하지는 않았다 — **회사 PC 반입 전 `scripts/` 2개 파일(약 90 KB)을 직접 읽을 것.** 이번 채택분 중 가장 작고(250★) 07-19 이후 푸시가 없다.
- 신뢰도: 중간 — 라이선스·의존성·읽기 전용 설계는 1차 확인. **개인정보 취급 주장은 미검증.**

---

## 오늘의 스택 시사점

1. **바이너리 스캔을 계정 단위로 올려라.** #1이 실증했다 — 저장소 단위 스캔은 6건 중 1건만 잡았다. 다운로드 없이 메타데이터만 읽으므로 비용이 거의 없다.

   ```bash
   # 1단계: 대상 저장소 스캔
   gh api "repos/{owner}/{repo}/git/trees/HEAD?recursive=1" \
     --jq '[.tree[]|select(.type=="blob")|.path]
           | map(select(test("[.](exe|dll|so|dylib|bin|msi|jar|pyd|wasm|zip|7z|gz|ps1|bat|cmd)$";"i")))
           | if length==0 then "CLEAN" else "BINARIES: "+join(", ") end'

   # 2단계(이번 판에서 추가): 같은 소유자의 다른 저장소도 전부
   for n in $(gh api "users/{owner}/repos?per_page=100&type=owner" --jq '.[].name'); do
     printf "%-40s " "$n"
     gh api "repos/{owner}/$n/git/trees/HEAD?recursive=1" \
       --jq '[.tree[]|select(.type=="blob")|.path]
             | map(select(test("[.](exe|dll|msi|scr|bat|cmd|ps1)$";"i")))
             | if length==0 then "clean" else "*** "+join(", ") end' 2>/dev/null
   done
   ```

   추가로 **README의 "recommended" 설치 경로를 그대로 믿지 말 것** — #1의 사례는 권장 경로가 바로 위험한 쪽이었고, 안전한 대안(마크다운 직접 복사)이 Option B로 밀려 있었다.

2. **"싼 모델로 내려도 되는가"가 어제와 오늘로 한 쌍이 됐다.** 07-30 #1(fable-method)은 **왜 되는가**를 줬다 — 지침을 "무엇을 중시하라"가 아니라 "무엇을, 어떤 순서로, 어떤 임계값으로"로 쓰면 낮은 등급 모델이 문자 그대로 따를 수 있다. 오늘 #2(pilotfish)는 **어디에 배치하는가**를 준다 — 계획·판정은 위, 물량은 아래, 수용 경계만 다시 위. 둘 다 설치물이 설정·마크다운뿐이다. 다만 인용 수치가 각각 프로젝트·벤더 자기 측정이므로, `model-downgrade-eval`의 판정 규칙 사전 등록 → A/B → 프로그램 채점 절차를 건너뛰는 근거로 쓰지 말 것.

3. **컨텍스트는 "덜어내라"에서 "재고 나서 덜어내라"로 넘어간다.** 07-30 #3이 긴 정책문서의 실패를 실측했다면, 오늘 #5(codex-hygiene)는 **계측**을, #3(finding-unknowns)은 **절차**를 준다. 순서는 계측이 먼저다 — 무엇이 얼마나 로드되는지 재지 않고 덜어내면 무엇이 좋아졌는지도 모른다. 단 #3을 통째로 얹는 것 자체가 컨텍스트 비대이므로 **2개만** 취할 것.

4. **이식은 "판정자부터"다.** #4는 벤더 공식 킷인데도 1단계가 "이식하지 마라도 유효한 답"이고, 번역 시작 전에 **일부러 망가뜨린 코드까지 잡아내는지 검증한 판정자**를 요구하며, 거부 규칙 파일이 없으면 프롬프트가 스스로 멈춘다. 회사 PC 이식 작업에 그대로 옮길 수 있는 순서다 — 대상을 고르기 전에 "무엇으로 성공을 판정할 것인가"를 먼저 고정할 것.

## 전일 대비 변화

- **07-30이 연 하이브리드 파이프라인의 2회차다.** 전환 자체는 어제 시행됐고, 오늘은 그 위에서 **미완 항목을 닫는 판**이다: 07-30 #5(보안)를 계정 단위로 확대해 1건 → 6건으로 확정했고, 07-30이 "검증 미완"으로 이월한 S등급 후보 3건 중 `codex-hygiene`을 채택(A), `personal-model`을 G4 제외로 판정했다.
- **테마 이동**: 07-27~07-29의 "덜고 조인다" → 07-30의 "긴 규칙은 안 지켜진다(HANDBOOK.md)" → 오늘 **"그러면 무엇을 신뢰할 것인가"**. 채택 4건 중 3건(#3·#4·#5)이 계측·게이트·판정자 계열이고, #1은 신뢰의 근거로 별 수를 쓰면 안 된다는 실증이다.
- **신규 진입**: 보안 1건(#1, 07-30 #5의 확대) + S 3건(#2~#4) + A 1건(#5).
- **이탈(중복/게이트)**: `fable-method`·`self-learning-skills`는 07-30 채택분과 7일 중복. HF/OpenAI 브리치는 6판 연속 중복. `grok-build`·`better-harness`·`personal-model`·`deja-vu`는 G4, `OptMem`·`token-diet`·`harness-engineering`·유출 프롬프트 재배포물은 G3.

## 이월 open query

1. **G3 통과 목록에 문서형 라이선스를 넣을지 결정 필요(신규, 우선).** `harness-engineering`(2,407★)이 **CC-BY-4.0이라는 이유만으로** 탈락했다. CC-BY-4.0은 불명 라이선스도 카피레프트 전염 라이선스도 아니며, 문서·지식 배포물의 흔한 선택이다. 이 리포트가 다루는 S등급(마크다운·프롬프트)의 상당수가 여기 해당할 수 있다. **문서형 산출물에 한해 CC-BY-4.0·CC0-1.0을 통과로 둘지**를 [ADOPTION-CRITERIA.md](../../ADOPTION-CRITERIA.md) 개정으로 결정할 것. 현행 규칙은 코드용 라이선스 목록을 문서에 그대로 적용하고 있다.
2. **`NOASSERTION`은 판정이 아니라 "LICENSE 원문을 읽으라"는 신호다(신규, 우선).** 이번 판 채택 4건 중 2건(`finding-unknowns-skills`·`code-migration-kit`)이 API상 `NOASSERTION`이었지만 파일 본문은 **표준 MIT / 표준 Apache-2.0**이었다 — API 필드만 보고 걸렀다면 벤더 공식 킷을 "라이선스 불명"으로 버렸을 것이다. 반대 방향도 확인됐다: 07-30이 `NOASSERTION`으로 제외한 `openclaude-improved`의 LICENSE 파일은 **"Anthropic Claude Code CLI에서 파생됐으며 원본은 독점 소프트웨어"라는 NOTICE**였다 — 제외는 옳았고 사유는 "불명"이 아니라 **"독점 파생물"이라는 더 강한 근거**였다(덧붙여 이 저장소도 #1의 그 블롭을 담고 있다). **양방향 모두 LICENSE 원문 확인을 요구하므로, 이를 게이트 절차에 명문화할 것.**
3. **하이브리드 쿼리 세트 고정(07-30 이월).** 이번에도 GitHub 쿼리 4개를 수동 구성했다. **재현 가능한 형태로 고정**할 것 — `created:>=D-30` × (stars 구간) × (키워드/토픽 축) + **소유자 단위 2차 스캔**(이번 판에서 필요성이 입증됨).
4. **DISCOVERY 클러스터 오염 필터(신규).** 이번에 제외한 항목은 `r/BodyHackGuide` 결과가 주제 클러스터에 섞인 사례다. 엔진 로그에 `Discovered subreddits`가 남으므로 **주제와 무관한 서브레딧이 섞인 클러스터는 정량치를 인용하지 않는다**는 규칙을 명문화할 것.
5. **Reddit 원문 permalink(07-28~07-30 이월, 지속).** 07-30이 HN Algolia로 HN 쪽은 해결했다. Reddit은 미해결이나, 도구 발굴이 GitHub API로 이관되면서 **우선순위는 낮다.**
6. **Claude Security 플러그인 재판정(07-28~07-30 이월, 지속).** 라이선스·과금이 공개되면 게이트 재적용.

---

*생성: Claude Code 자동 트렌드 리서치 (GitHub Search/Repos/Trees/Users API 직접 관측 + last30days v3.16.0 DISCOVERY) · 관측 시각: 2026-07-31 00:07~00:40 KST (2026-07-30 15:07~15:40 UTC) · 방법론: [METHODOLOGY.md](../../METHODOLOGY.md) · 채택 기준: [ADOPTION-CRITERIA.md](../../ADOPTION-CRITERIA.md)*
