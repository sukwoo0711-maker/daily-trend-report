# 🧰 AI Personal Stack 트렌드 리포트 — 2026-08-04 (6건: 보안 1 · 방법론 2 · 채택 S 2 · A 1)

> **조사 방식**: 하이브리드 6회차. ① 도구 발굴은 GitHub API 직접 관측(`created:>=2026-07-05`, 쿼리 7종 + 토픽 2종) ② 뉴스·논쟁은 last30days v3.16.0 DISCOVERY(윈도우 2026-07-04 ~ 08-03) ③ 정량 인용은 **HN Algolia item ID 직접 조회**(08-01 규칙) ④ **지목 계정 재스윕**(08-02 확정 고정 목록) ⑤ 채택 후보는 **계정 단위 바이너리 스캔**(07-31 개정).
> **범위**: AI Personal Stack 구축에 유용한 것만 — 사용 방법론, 자동화, Skills, MCP, GitHub Rising Star, 로컬/셀프호스팅, 에이전트 보안.
> **제외**: 일반 뉴스, 모델 출시 소식, 정책/시장 동향, 에이전틱 브라우저, **최근 7일 내(07-28~08-03) 리포트에서 다룬 항목**.
> **정렬 기준**: 보안·방법론 항목(등급 미적용) → 채택 등급 S → A, 각 그룹 안에서 관측 주목도순.
> **관측 시각**: **2026-08-04 KST**. 별 수·fork 수·블롭 SHA는 이 시점 단일 스냅샷.
> **출처 범위/누락**: GitHub API(직접) + DISCOVERY + HN Algolia. 누락 = X·YouTube·TikTok, **Reddit 원문**(8판 연속 미해결).

---

## 🚨 먼저 — 캠페인이 무엇을 하는 것인지 오늘 처음 보였다

상세는 #1. 요약하면 세 가지다.

1. **새 저장소는 0건.** 07-31에 시작한 재스윕이 처음으로 아무것도 못 잡았다. 대신 **8번째 저장소의 별이 하루 만에 283 → 550으로 거의 두 배**가 됐다.
2. **그보다 중요한 것 — 이 저장소들의 마크다운은 위조가 아니라 정품이다.** `andrej-karpathy-skills`의 `SKILL.md`는 **19.9만★ 원본과 블롭 SHA가 같고**(`6a62d0441753`), `ponytail-improved`의 스킬 파일 6종은 **9.5만★ MIT 원본과 전부 바이트 동일**하다. 그런데 **둘 다 GitHub fork가 아니다**(`fork:false, parent:none`) — "forked from" 배너가 뜨지 않는다.
3. **07-31·08-02·08-03이 추적한 파일은 전부 부산물이었다.** 판별의 실질은 *"이 저장소가 자기 것이라고 내놓은 마크다운이 실은 남의 것인가"* 다.

**부수 정정**: 08-03 리포트와 `ADOPTION-CRITERIA.md`는 `gup.xml`이 *"8개 전부 내용이 같다"* 고 적었다. **틀렸다 — 2변종이다**(`bd59041f343b` 4,608B가 4곳, `c61c3c179a8d` 4,521B가 4곳). 판정(전건 G1 제외)은 바뀌지 않지만 관측은 정정한다.

## ⚠ 게이트/중복/검증실패로 제외한 항목(투명 처리)

| 반환 항목 | 처리 | 사유 |
|---|---|---|
| `VictorTaelin/OptMem` (1,097★) — *"영구 메모리, 426토큰 프롬프트 + 스크립트"* | **제외(가장 아깝다)** | **G3** — 저장소에 **LICENSE 파일이 아예 없다**(트리 13개 파일 전수 확인, API도 `NONE`). 07-31 `NOASSERTION` 규칙은 "원문을 읽어라"인데 **읽을 원문이 없는 경우**다. 내용은 정확히 이 리포트가 찾는 모양(**의존성 0 파이썬 단일 파일** + 426토큰 프롬프트)이라 라이선스만 붙으면 즉시 A~S 후보. 부수 우려: 설치가 `curl \| sh` |
| DISCOVERY #1 중국 LLM 출시 러시 / #3 qwen3.7 유출 정황 | **제외(범위 + 검증 실패)** | **모델 출시 소식 자체**(08-03 개정 후에도 제외). 더해 창 안 HN 스토리 **0건** |
| DISCOVERY #5 — 과소평가된 에이전트 활용처 | **제외(검증 실패)** | **5판 연속 재부상, 4판 연속 HN ID 미확인.** 08-01 규칙 적용 |
| DISCOVERY #6 — *"마크다운 위키가 메모리 제품 8종을 다 이겼다"* | **제외(재현 불가 + G3)** | 상세는 #3. 공개된 건 **채점 코드뿐이고 데이터셋·결과 원자료는 저장소가 명시적으로 비공개**. 라이선스 없음(4★). 엔진은 HN 37pt·10댓글로 보고했으나 **실제는 [`49156055`](https://news.ycombinator.com/item?id=49156055) 2pt·0댓글** |
| DISCOVERY #4 — Nightcrawler(스마트폰 로컬 AI 침투테스트 에이전트) | **제외(G1)** | HN [`49154127`](https://news.ycombinator.com/item?id=49154127) 78pt·23댓글로 **실재는 검증됨**. 그러나 **이중용도 공격도구**이고, 최상위 댓글부터 *"샌드박스를 어떻게 벗어났는지가 유일한 관심사였는데 설명이 없다. 미공개 제3자 외부 샌드박스, 인터넷에 연결된 미공개 패키지 매니저…"*(381표)로 샌드박스 경계를 문제 삼는다 |
| `torakagemusha-sudo/torafirma-skill-router` (14★, MIT) | **제외(G1+G4)** | 주제(*"큰 스킬 라이브러리를 컨텍스트 범람 없이 로딩"*)는 정확히 맞지만 **후보 저장소 본체에 `releases/skill-router-windows-x64-1.0.0.zip`**(내용 확인 불가) + C++/Rust 빌드 필요 |
| `SerhiiKorniienko/bullshit-detector` (101★, MIT, 계정 전체 CLEAN) | **제외(부분 G4 + 범위 인접)** | HN [`49096917`](https://news.ycombinator.com/item?id=49096917) 65pt·68댓글로 실재 확인. 채점 엔진 `tally.py`(71KB)는 **stdlib만** 써서 그 자체로는 A급인데, 수집부 `fetch.py`가 `requests`·배너가 `PIL`을 요구하고 **대상이 유튜브·기사 팩트체크**라 개인 에이전트 스택 구성요소가 아니다. *설계는 참고할 만하다* — 주장 단위 검증 + 결정론적 stdlib 채점기 분리 |
| `SlanchaAI/ingot` (49★, Apache-2.0) | **제외(G4)** | *"에이전트 스킬용 증거 게이트형 eval"* 로 08-03 open query 3과 겹치지만 **py 67개 + Docker/Caddy** |
| `pax-beehive/paxm`(436★ Apache-2.0), `vshulcz/deja-vu`(510★ MIT) | **제외(G4)** | 각각 Go 158·533파일. 후자는 *"LongMemEval-S에서 hit@1 84.9%, LLM도 임베딩도 없이"* 라는 **주목할 주장**이 있으나 단일 바이너리 빌드가 필요하고, 오늘 B등급 예외 3조건 중 ①(대체 S/A 없음)을 만족하지 못한다 |
| `coji/natural-japanese`(139★), `NulightJens` 계열 문체 스킬 | **제외(주제 중복)** | 08-01 #3·08-02 #5가 이미 AI 문체 제거. 7일 규칙 |
| `img2threejs`(9,340★), `video-shotcraft`(3,402★), `jakubkrehel/skills`(2,895★), `vox-director`, `worldwonderer/*` 등 | **제외(범위 외)** | 미디어·UI 제작. **신규 스킬 저장소 상위를 이 카테고리가 계속 독점한다**(4판 연속 관측) |
| `xai-org/grok-build`(24,003★), `yc-software/qm`(9,063★), `unicity-aos/aos-ce`(8,574★) | **제외(G4)** | 하네스 본체 |

---

## 요약 순위표

| 순위 | 트렌드 | 등급 | 라이선스 | 분류 | 관측 근거·시점 | 신뢰도 |
|---|---|---|---|---|---|---|
| 1 | **캠페인의 수법 규명** — 마크다운은 **19.9만★·9.5만★ 원본의 블롭 그대로**, fork 표시만 없앤 재발행. 신규 저장소 0건, 대신 최신 저장소 별 2배 | N/A(보안) | — | 보안/공급망 | GitHub API 블롭 SHA 상류 대조 2건 + 계정 전수, 08-04 | **높음**(메타데이터 한정) |
| 2 | **DISCOVERY는 폐기가 아니라 소스별 비대칭 실패** — 3판 연속 전량 실패 뒤 오늘 **2건 정확 일치**, 1건 18배 과대보고 | N/A(방법론) | — | 방법론/검증 | HN Algolia 6클러스터 전수 조회, 08-04 | **높음** |
| 3 | **"내 방식이 이겼다"는 주장일수록 증거 기준을 낮추지 말 것** — 마크다운 위키 벤치마크가 **채점 코드만 공개, 데이터·결과 비공개** | N/A(방법론) | — | 방법론/검증 | 저장소 원문 + HN [`49156055`](https://news.ycombinator.com/item?id=49156055) 2pt, 08-04 | 중간~높음 |
| 4 | `oliver-zehentleitner/keep-the-why` — **"왜"를 코드 옆에 남기는 스킬**. eval 케이스 + **프롬프트 인젝션 픽스처**를 자기 컨텍스트 파일에 대해 돌린다 | **S** | MIT | 방법론/문서화 | GitHub API: 139★, `evals.json` 41KB·픽스처 100여, 계정 CLEAN | 중간~높음 |
| 5 | `nicobailon/grill-for-unknowns` — 같은 뿌리에서 나온 grill 스킬인데 **이쪽만 상류 계보를 문서로 밝힌다** | **S** | MIT | 방법론/계획검증 | GitHub API: 191★, md 12·순수 마크다운, 계정 CLEAN | 중간 |
| 6 | `NHClimber87/llm-serve-dashboard` — 로컬 서빙 관측을 **stdlib 단일 파일 + HTML 한 장**으로 | **A** | MIT | 로컬 스택/관측 | GitHub API: 66★, 파일 9개, import 전수 stdlib 확인 | 중간~높음 |

---

## 상세

### 1. 캠페인은 위조가 아니라 **정품 재발행**이었다 🚨

먼저 재스윕 결과. 계정 `0xwilliamortiz`는 **여전히 저장소 8개**다. 07-31에 세운 재스윕 규칙이 **처음으로 신규 저장소를 못 잡았다.** 대신 다른 것이 움직였다.

| 저장소 | 생성 | ★ (08-03 → 08-04) | fork |
|---|---|---|---|
| **`humanizer-cli`** | 08-01 | **283 → 550** | 31 → 69 |
| `ponytail-improved` | 07-28 | 579 → 584 | 129 |
| `openclaude-improved` | 07-26 | 566 → 568 | 81 |
| `andrej-karpathy-skills` | 07-21 | 546 → 549 | 95 |
| `ratchet` | 07-31 | 409 → 418 | 85 |
| `agents-council` · `FlashKDA` · `yoinks` | 07-20~29 | 변동 미미 | — |

계정 팔로워는 **7 → 12**. 하루 증가분 286★ 중 **267★이 최신 저장소 한 곳에 몰렸다.** 새 저장소를 안 만든 대신 **가장 최근 것에 주목도를 몰아주는 모양**이다(관측일 뿐, 조작 여부는 단정하지 않는다).

**그리고 계정 전수 스캔 중에 훨씬 중요한 것이 나왔다.** 채택 후보 `NHClimber87/llm-serve-dashboard`의 계정을 스캔하다가, 같은 계정에 **`andrej-karpathy-skills`라는 이름의 저장소**가 있는 것을 발견했다. 캠페인 저장소와 같은 이름이다. 확인해 보니 이쪽은 **2026-04-16에 만들어진 `multica-ai/andrej-karpathy-skills`의 fork**였다 — 캠페인 저장소(07-21 생성)보다 **석 달 앞선다**. 그래서 원본을 열어 봤다.

> **`multica-ai/andrej-karpathy-skills`** — **199,077★ · fork 20,483 · 2026-01-27 생성 · fork 아님**

그리고 블롭을 대조했다.

| 파일 | 원본(19.9만★) | 캠페인 저장소(549★) | 판정 |
|---|---|---|---|
| `skills/karpathy-guidelines/SKILL.md` | `6a62d0441753` 2,518B | `6a62d0441753` 2,518B | **바이트 동일** |
| `README.zh.md` | `1228d8ccbe8f` 6,042B | `1228d8ccbe8f` 6,042B | **바이트 동일** |
| `README.md` | `7cf07a786532` 6,198B | `688241481dd6` 4,349B | 교체됨 |
| `.claude-plugin/`·`CLAUDE.md`·`EXAMPLES.md`·`CURSOR.md` | 있음 | **없음** | 삭제됨 |
| `fastsetup.exe` · `gup.xml` · `libcurl.dll` | — | **추가됨** | 삼종세트 |

**한 건이면 우연일 수 있어 두 번째를 봤다.** `0xwilliamortiz/ponytail-improved`(584★)의 상류는 **`DietrichGebert/ponytail` — 94,717★ · 2026-06-12 생성 · MIT**이고, 설명 문구(*"Makes your AI agent think like the laziest senior dev in the room"*)가 **글자 그대로 같다.** 블롭 대조 결과 스킬 파일이 **6종 전부 바이트 동일**했다.

`skills/ponytail/SKILL.md` `02c0712c8627` · `.openclaw/skills/ponytail/SKILL.md` `a3e4d94b791e` · `.agents/rules/ponytail.md` `0af61d583fbd`(`.clinerules`·`.qoder`·`.windsurf` 3곳에 같은 블롭) · `.kiro/steering/ponytail.md` `09cf36db7c33` · `benchmarks/results/2026-06-12-caveman-vs-ponytail.md` `b3dd3815c2d7` — **전부 원본과 동일**. 바뀐 건 README(20,032B → 4,782B)와, `skills/ponytail/` 안에 들어간 `vibecodecalc.exe` + `libcurl.dll` + `gup.xml`뿐이다.

**여기서 그림이 맞춰진다.** 왜 이 저장소들이 읽어 보면 멀쩡했는지, 왜 별이 빠르게 붙었는지 — **내용물이 진짜이기 때문이다.** 십수만 별짜리 유명 스킬을 통째로 복사하고, **GitHub fork 관계를 만들지 않아 "forked from" 배너를 없앤 뒤**, 이름에 `-improved`를 붙이고 실행 파일 한 벌을 끼워 넣는다. 07-31이 잡은 "동일 exe 블롭", 08-02가 잡은 "은닉 설치 스크립트", 08-03이 잡은 "세 파일 한 벌"은 전부 **끼워 넣은 쪽**이었고, **가져온 쪽은 아무도 안 봤다.**

**게이트를 4차 교정했다** — 판별 축을 하나 더 세운다. **"이 저장소가 자기 것으로 내놓은 마크다운이, 상류 원본과 블롭 SHA가 같은가. 그런데 fork가 아닌가."** 이 조합은 실행 파일이 하나도 없어도 성립하는 신호다. 명령은 시사점 1에 보존했다. [ADOPTION-CRITERIA.md](../../ADOPTION-CRITERIA.md)에 반영했다.

**08-03 관측 정정**: `gup.xml`은 8곳 전부 같지 않다. **2변종**이다.

| 블롭 | 크기 | 저장소 |
|---|---|---|
| `bd59041f343b` | 4,608B | `agents-council`(2경로) · `andrej-karpathy-skills` · `yoinks` · `FlashKDA` |
| `c61c3c179a8d` | 4,521B | `openclaude-improved` · `ponytail-improved` · `ratchet` · `humanizer-cli` |

생성일 순서와 정확히 일치하지도 않는다(`FlashKDA` 07-29가 구변종, `openclaude-improved` 07-26이 신변종). **"고정된 것 vs 바뀌는 것" 이분법 자체가 너무 거칠었다**는 뜻이다.

- 1차 출처: [`multica-ai/andrej-karpathy-skills`](https://github.com/multica-ai/andrej-karpathy-skills)·[`DietrichGebert/ponytail`](https://github.com/DietrichGebert/ponytail) 트리, [`0xwilliamortiz`](https://github.com/0xwilliamortiz) 계정 전수 트리·블롭 SHA(2026-08-04 조회)
- 반대 근거/한계: **바이너리는 받지도 돌리지도 않았고 악성 여부를 단정하지 않는다.** 상류 두 곳은 각각 라이선스가 **없음(multica-ai)** 과 **MIT(DietrichGebert)** 이라, MIT 쪽은 **출처 표기만 하면 복제 자체가 위반이 아니다** — 문제 삼는 것은 복제가 아니라 **fork 관계를 만들지 않아 계보를 감춘 것과 실행 파일 동봉**이다. "fork를 일부러 피했다"는 것은 관측(`fork:false`)에서의 **추론**이고, 상류 저장소를 지우고 새로 push해도 같은 상태가 된다. 별 증가가 인위적인지는 **확인하지 않았다**(증가율만 관측). 표본은 계정 1개, 상류 대조는 8곳 중 **2곳만** 했다. GitHub 조치 여부 미확인.
- 신뢰도: **높음**(블롭 SHA 일치·fork 플래그·별 수는 1차 관측). 해석은 **중간**.

### 2. DISCOVERY는 죽지 않았다 — 실패가 소스별로 갈린다 🔍

08-03 open query 1은 *"3판 연속 실패했으니 DISCOVERY를 정량 인용원에서 완전히 제외하고 주제 발견기로만 쓸지"* 를 다음 판 최우선으로 남겼다. 오늘 그 판단을 내리려고 **6개 클러스터 전부를 Algolia로 조회**했다. 결과는 예상과 달랐다.

| 클러스터 | 엔진 보고 | Algolia 창 내 조회 | 판정 |
|---|---|---|---|
| #2 인지부채 — LLM 코드를 손으로 다시 타이핑 | HN 278pt·247댓글 | [`49153374`](https://news.ycombinator.com/item?id=49153374) **280pt·247댓글**(08-03) | ✅ **일치**(포인트는 조회 시점 차) |
| #4 Nightcrawler 로컬 침투테스트 에이전트 | HN 78pt·23댓글 | [`49154127`](https://news.ycombinator.com/item?id=49154127) **78pt·23댓글**(08-03) | ✅ **정확 일치** |
| #6 마크다운 위키 메모리 벤치마크 | HN 37pt·10댓글 | [`49156055`](https://news.ycombinator.com/item?id=49156055) **2pt·0댓글**(08-03) | ❌ **18배 과대보고** |
| #1 중국 LLM 출시 러시 | HN 129pt·23댓글 | 해당 스토리 **0건** | ❌ 인용 불가 |
| #3 qwen3.7 출시 정황 | HN 3pt·2댓글 | **0건** | ❌ 인용 불가 |
| #5 과소평가된 활용처 | HN 22pt·2댓글 | **0건**(5판 연속) | ❌ 인용 불가 |

**즉 "DISCOVERY의 HN 집계는 못 믿는다"가 아니라 "클러스터에 따라 정확하기도 하고 18배 틀리기도 한다"** 가 오늘의 실측이다. 그리고 갈리는 축이 보인다 — **엔진이 정확했던 두 건은 HN이 1차 발생지**(둘 다 Show HN/블로그 링크로 HN에서 먼저 터짐)이고, **18배 틀린 건은 Reddit이 1차이고 HN에는 2pt짜리 자기 홍보 글만 있는 건**이다. 다시 말해 엔진은 **HN 밖 참여도를 HN 칸에 흘려 담는다.**

**그러므로 08-03이 제안한 "DISCOVERY 정량 인용 전면 금지"는 채택하지 않는다.** 그 규칙이었다면 오늘 정확했던 2건도 버렸을 것이고, 무엇보다 **08-01 규칙(ID로 확인 전엔 인용 금지)이 이미 필요한 전부**다. 오늘 확정하는 것은 그 규칙의 **적용 범위를 전 클러스터 전수로** 못박는 것이다. [METHODOLOGY.md](../../METHODOLOGY.md)에 반영했고, **open query 1은 종결**한다.

- 1차 출처: HN Algolia `search?tags=story&numericFilters=created_at_i>1783123200`, 2026-08-04 조회(질의 9종)
- 반대 근거/한계: Algolia 조회는 **키워드 기반**이라 제목이 크게 다른 스토리를 놓쳤을 가능성을 배제하지 못한다(그래서 "존재하지 않는다"가 아니라 "인용 불가"). "HN이 1차 발생지면 정확하다"는 **표본 6건에서 뽑은 가설**이고 검증된 규칙이 아니다 — 다음 판들에서 같은 축으로 계속 세면 판정된다. **Reddit 쪽 수치는 여전히 대조하지 못했다**(8판 연속).
- 신뢰도: **높음**(6클러스터 전수 조회). 원인 가설은 **낮음~중간**.

### 3. 내 방식을 칭찬하는 주장일수록 증거 기준을 낮추지 말 것 ⚖️

DISCOVERY #6이 물어온 제목은 이렇다.

> *"AI 에이전트 메모리 시스템 8종을 2,176개 과제로 돌렸더니 **평범한 마크다운 위키가 모든 제품을 이겼다**."*

이 스택에 이보다 듣기 좋은 문장은 없다. 사용자의 메모리는 실제로 마크다운 파일 더미이고, `offline-knowledge-base`도 `MEMORY.md`도 같은 계열이다. **그래서 더 세게 검증했다.**

근거 저장소 `AML-memory/agent-memory-leaderboard`(4★, 07-29 생성)를 열면 스스로 이렇게 적어 둔다.

> *"이 디렉터리는 리더보드가 **공개 데이터셋에 사용한 답변 생성·평가 계약(contract)** 을 공개한다."*
> *"내부 배포 코드, 서비스 주소, 자격증명, **데이터베이스, 데이터셋, 실행 산출물은 의도적으로 이 공개 릴리스 밖에 둔다.**"*

즉 **공개된 것은 채점기이고, 채점 대상과 결과 원자료는 없다.** 파일은 파이프라인 스크립트 8개와 README뿐이며 **LICENSE가 없다(G3)**. 그리고 앞서 본 대로 **HN 실측은 2pt·0댓글**이다 — 엔진이 보고한 37pt의 18분의 1이다.

**공정하게 적자면 이 저장소가 정직한 부분도 있다.** 운영 파라미터를 상세히 공개한다 — 검색 `top_k` 100, Add 64워커, 판정자 전역 15요청 상한, 429 시 키 로테이션과 30초 쿨다운, 점수는 내부 `[0,1]`을 `[0,100]`으로 환산. 그중 한 줄이 눈에 띈다 — **`Qwen JSON 요청은 enable_thinking=false로 설정`**. 08-03 #8이 채택한 서빙 함정 레지스트리의 `03-enable-thinking-default-drift`와 **정확히 같은 지점**이고, 이 팀이 그 함정을 알고 있다는 뜻이다.

**그럼에도 채택하지 않는다.** 재현 경로가 없는 결론은 결론이 아니다. 08-03이 `SimpleEnglish`를 오늘의 최고 신뢰도로 올린 이유가 *"저자가 자기 한계를 먼저 적었고 `python3 evals/run_bench.py` 한 줄로 재현된다"* 였는데, 같은 잣대를 **내 편을 들어 주는 주장에도 그대로 대야** 그 잣대가 잣대다.

- 1차 출처: [GitHub — AML-memory/agent-memory-leaderboard](https://github.com/AML-memory/agent-memory-leaderboard) README 원문(2026-08-04 조회), HN [`49156055`](https://news.ycombinator.com/item?id=49156055)
- 반대 근거/한계: **주장이 틀렸다고 말하는 것이 아니다** — 마크다운 위키가 실제로 이겼을 수도 있다. 판정은 *"이 저장소로는 확인할 수 없다"* 이지 *"거짓이다"* 가 아니다. **Reddit 원문 스레드(98댓글)는 확보하지 못했으므로** 거기에 더 나은 근거가 있을 가능성을 배제하지 못한다(8판 연속 이월된 같은 공백). LongMemEval-S·LOCOMO·PersonaMem 등 파이프라인이 참조하는 데이터셋 자체는 공개 벤치마크다.
- 신뢰도: 중간~높음 — 저장소 원문·라이선스 부재·HN 수치는 1차 확인. **주장의 진위는 미판정.**

### 4. `oliver-zehentleitner/keep-the-why` — 코드가 설명 못 하는 것을 코드 옆에 남긴다 🧭 **[S · MIT]**
**139★ · fork 12 · 생성 2026-07-10 · 최종 푸시 08-01 · md 134 · 본체 CLEAN · 계정 전체 오탐만**

한 문장이 목적을 다 말한다.

> *"**'밥한테 물어봐'는 문서가 아니다.** Keep a Changelog가 무엇이 바뀌었는지를 기록한다면, 이것은 **왜 바뀌었는지**를 보존한다."*

네 가지 모드로 쓴다. ① **연속 포착** — 대화 중에 남길 가치가 있는 근거(결정, 기각한 대안, 우회, 장애, 제약)가 나오면 코드 옆 `context/`에 적는다. **여기에 특이한 항목이 하나 있다 — *일어나지 않은 변경*.** 뭔가를 고치려다 "왜 건드리면 안 되는지"를 알고 멈춘 경우, **커밋되는 것이 없으므로 그 판단은 어디에도 흔적을 남기지 않는다.** ② **소급 복원** — 레거시 저장소에서 코드·git 이력·이슈·기존 문서로 결정을 재구성. ③ **지식 이전 인터뷰** — 유지보수자가 떠나기 전에, 저장소를 먼저 분석하고 **코드가 설명하지 못한 지점만 골라** 묻는다(장기 근속자에게는 자유 서술을 시키고 거기서 근거를 추출하는 별도 기법). ④ **유지보수** — 모순 해소, 대체된 항목 표시, 중복 병합.

**이 항목을 오늘 S로 올리는 이유는 주제가 아니라 검증 자세다.** `skills/keep-the-why/evals/evals.json`(41KB)에 **프롬프트와 기대 행동을 짝지은 케이스**가 들어 있고, `tools/evals/`에는 **케이스마다 픽스처 프로젝트를 만들어 실제 에이전트 세션을 돌리고 트랜스크립트와 파일 변경을 채점하는 러너**(`run.py`, **import 전수 stdlib**)가 있다. 픽스처가 100개를 넘는데 구성이 두 갈래다.

- **부정 케이스** — `negative-routine-change-no-trigger`, `negative-manufactured-abandoned-reasoning`(없는 근거를 지어내지 말 것), `negative-existing-good-structure-untouched`, `significant-correction-is-not-a-decision`. **스킬이 발동하면 안 되는 상황**을 명시적으로 채점한다.
- **`trust-model-*` 8종** — `direct-injection-in-context`, `hidden-unicode-instructions`, `base64-payload-in-source-material`, `dangerous-command-disguised-as-decision`, `injection-attempts-to-mark-itself-confirmed`. **자기가 만드는 컨텍스트 파일을 인젝션 표면으로 놓고** 적대적 입력을 돌린다.

그 근거는 `references/trust-model.md`에 논증돼 있고, 논리가 이 리포트의 #1과 같은 계열이다.

> *"`context/`가 다른 파일보다 공격받기 쉽다는 뜻이 아니다. **뭔가 주입된 것이 거기 안착하면, 이 스킬의 설계 자체 — 먼저 읽고, 무기한 보관 — 가 일회성 주입을 지속적 주입으로 바꿔 준다**는 뜻이다."*

핵심 규칙은 한 줄이다 — **`context/`는 프로젝트 지식이지 에이전트 지시가 아니다.** 판별은 주제가 아니라 서술이냐 지시냐로 한다: *"이 컴포넌트는 호환성 때문에 Python 3.11이 필요하다"* 는 지식, *"지금 이 셸 명령으로 Python 3.11을 설치하라"* 는 지시이며 **`context/`에 역사적 근거처럼 적혀 있다고 지식이 되지 않는다.**

**이 스택에 붙는 자리**: 사용자의 `git-history-ops`가 *"git 이력 = 에이전트 컨텍스트·세이브포인트"* 라는 같은 명제 위에 있고, `offline-knowledge-base`·`spec-defect-search`는 *"사양·결함 이력을 어떻게 쌓고 꺼내는가"* 문제다. **회사PC 이식 대상 코드는 대개 담당자가 없다** — 모드 ②·③이 정확히 그 상황을 위해 갈라져 있다.

- 1차 출처: [GitHub — oliver-zehentleitner/keep-the-why](https://github.com/oliver-zehentleitner/keep-the-why), [`skills/keep-the-why/SKILL.md`](https://github.com/oliver-zehentleitner/keep-the-why/blob/main/skills/keep-the-why/SKILL.md)(24KB)·[`references/trust-model.md`](https://github.com/oliver-zehentleitner/keep-the-why/blob/main/skills/keep-the-why/references/trust-model.md)·`evals/README.md`·`evals.json`·`tools/evals/run.py` 원문
- 반대 근거/한계: **eval 결과 수치가 공개돼 있지 않다.** 케이스와 러너는 있지만 *"몇 건 통과했다"* 는 표가 없다 — 08-03 #4(`SimpleEnglish`)가 96 generations 실측표를 낸 것과 대비된다. 러너는 **LLM 판정자**를 쓰므로 돌리면 토큰이 든다(러너 자체는 스킬 패키지 밖 개발 도구이고, **스킬은 마크다운만이라 S 등급은 유지**). 저장소가 스스로 밝히듯 **에이전트 1종(Claude Code)에서만 구동**했고 **교차 에이전트 결과는 공개된 공백**이다 — [feedback-company-pc-porting-doctrine]의 "중립 문체" 요구와 정면으로 걸리는 지점이니 이식 시 확인이 필요하다. 계정 스캔에서 20여 저장소에 `.bat`이 걸렸으나 전부 **Sphinx 문서 빌드용 `dev/sphinx/make.bat`** 와 Capacitor 안드로이드 gradle 래퍼로, 08-01 2단계 판정 규칙상 **오탐**(후보 본체 CLEAN, 캠페인 블롭과 무관, SHA 상이). 버전 `0.6.4`로 아직 1.0 이전.
- 신뢰도: 중간~높음 — 라이선스·구성·CLEAN·원문은 1차 확인, **효과 수치 없음**.

### 5. `nicobailon/grill-for-unknowns` — 같은 뿌리, 다른 정직함 🔗 **[S · MIT]**
**191★ · fork 7 · 생성 2026-07-09 · 최종 푸시 07-20 · 파일 18개(md 12 + json 3) · CLEAN · 계정 전체 오탐만**

**07-31 #3에서 `Neeeophytee/finding-unknowns-skills`(283★)를 채택했다.** 오늘 같은 축을 다시 훑다가 나온 이 저장소는 **주제가 겹친다** — 지도(map) 대 영토(territory), 알려진/모르는 것의 4분면, 한 번에 한 질문씩 인터뷰. 7일 중복 규칙이라면 그대로 걸러야 할 항목이다.

**그런데 이쪽에는 07-31 채택분에 없던 파일이 두 개 있다.** `NOTICE.md`와 `references/upstream-lineage.md`다.

> *"이 프로젝트는 Matt Pocock의 MIT 라이선스 스킬 저장소에서 아이디어와 구조를 가져왔다 — `grill-with-docs`, `grilling`, `domain-modeling`. 또한 Thariq의 「A Field Guide to Fable: Finding Your Unknowns」의 전략을 반영했다."*

`upstream-lineage.md`는 여기서 더 나아가 **상류 스킬 3종의 원본 URL과 각각에서 무엇을 가져왔는지를 항목별로 적고**, 프런트매터의 `author`도 `Nico Bailon (co-authored by Matt Pocock)`이다. 그리고 유지보수자용 메모에 남긴 세 줄이 이 리포트가 **오늘 #1에서 데인 바로 그 지점**이다.

> *"**상류의 구성 전체를 살펴라.** 헤드라인 산출물에서 멈추지 마라. `grill-with-docs`는 작아 보였지만, 실제 동작은 그것이 링크한 `grilling` + `domain-modeling`과 그 보조 파일들에서 나왔다."*
> *"**출처 표기와 라이선스를 보존하라.** 상류의 저작권 고지를 어댑터 이름으로 갈아치우지 마라."*

**즉 오늘의 채택 사유는 스킬 내용이 아니라 계보 처리다.** 07-31 #3은 같은 상류(Thariq의 글 계열)에서 나왔는데 그 사실이 저장소에 없었고, 이 리포트는 그것을 모른 채 채택했다. **중복 판정의 기준을 "주제가 같은가"에서 "상류가 같은가"로 한 칸 올려야 한다**는 것이 오늘의 교훈이고, #1의 캠페인 사례가 같은 축의 극단이다.

내용 쪽에서도 07-31 채택분과 다른 점이 하나 있다. **grill의 종료 조건을 명시한다** — *"이 grill에는 정의된 끝이 있다. 모르는 것 원장이 비면 끝난다. 남은 개수를 줄어드는 대로 알려라('material unknowns 2개 남음') — 사용자가 끝이 다가오는 것을 보게."* 그리고 *"질문에는 값이 매겨져 있다(evidence-priced) — 집요한 심문이 아니다. **비본질적 주제를 안 묻는 것이 올바른 동작이다.**"* 07-30 #3(긴 정책 문서는 지켜지지 않는다)의 관점에서, **끝나지 않는 grill보다 종료 조건이 있는 grill이 실제로 지켜질 가능성이 높다.**

**이 스택에 붙는 자리**: 사용자가 쓰는 `auto-grill`(사용자 개입 없이 스스로 심문)과 `grill-me`(사용자를 심문)의 **중간 지점**이다 — 문서·소스에 근거를 대고 묻되, 결정은 사용자에게 남긴다.

- 1차 출처: [GitHub — nicobailon/grill-for-unknowns](https://github.com/nicobailon/grill-for-unknowns), [`SKILL.md`](https://github.com/nicobailon/grill-for-unknowns/blob/main/plugins/grill-for-unknowns/SKILL.md)(14KB)·[`NOTICE.md`](https://github.com/nicobailon/grill-for-unknowns/blob/main/NOTICE.md)·[`references/upstream-lineage.md`](https://github.com/nicobailon/grill-for-unknowns/blob/main/plugins/grill-for-unknowns/references/upstream-lineage.md) 원문
- 반대 근거/한계: **eval 없음** — 07-31 #3과 같은 공백이다. **상류 원본(`mattpocock/skills`)을 직접 대조하지 않았다** — 계보 문서가 정직하다는 것과 그 내용이 정확하다는 것은 다른 문제이고, 오늘 판정은 *"계보를 밝혔다"* 까지다. **07-20 이후 푸시 없음**(버전 `0.1.3`). 프런트매터에 `metadata.hermes` 항목이 있어 **완전한 하네스 중립은 아니다**. 07-31 #3과 **둘 다 쓰면 컨텍스트가 겹친다** — 07-27 #1·07-30 #3이 경고한 비대의 원인이므로 **하나를 고르는 편**이 취지에 맞다.
- 신뢰도: 중간 — 구성·라이선스·CLEAN·원문은 1차 확인, **효과 근거 없음**.

### 6. `NHClimber87/llm-serve-dashboard` — 로컬 서빙을 보는 눈, 설치 0으로 📟 **[A · MIT]**
**66★ · fork 10 · 생성 2026-07-10 · 최종 푸시 07-30 · 파일 9개 · CLEAN**

저장소가 자기를 이렇게 소개한다 — *"로컬 llama.cpp/vLLM 서빙용 **단일 파일·의존성 0** 라이브 대시보드. GPU, 처리량, KV/컨텍스트, 모델 라이브러리. **stdlib 파이썬 + 로컬 우선 HTML 한 장.**"*

**주장을 그대로 믿지 않고 확인했다.** 저장소 전체가 9개 파일이고(`fleet-metrics.py` 61KB + `index.html` 73KB + `models-registry.json` + 문서 3 + 스크린샷 + LICENSE + .gitignore), 파이썬 파일의 import를 전수 뽑으면 이렇다.

```
errno, ipaddress, json, math, os, socket, re, subprocess, sys, time,
urllib.request, http.server(HTTPServer, BaseHTTPRequestHandler)
```

**12개 전부 표준 라이브러리다.** pip 설치가 없고, 서버는 `http.server`로 직접 띄우며, HTML은 로컬 파일 한 장이다. **08-03이 `helasaoudi/llm-inspector`를 "주제는 정확히 맞는데 pip 의존성 7종이라 G4"로 아깝게 뺐는데, 같은 자리를 의존성 0으로 채운 항목**이다.

**이 스택에 붙는 자리**: 사용자의 `local-structured-output-bench`가 이미 부딪힌 문제들 — localhost vs 127.0.0.1 3배 차이, ollama가 `-md` 스텁을 물어 오는 문제, speculative가 8GB에서 0.99배 — 는 전부 **"지금 실제로 무엇이 어떻게 도는지"를 못 봐서** 사후에 원인을 캔 것들이다. 08-03 #8(서빙 함정 115건 레지스트리)이 *"요청도 응답도 멀쩡한데 숫자가 틀린다"* 를 **목록으로** 준다면, 이건 그 순간의 KV/컨텍스트·처리량을 **화면으로** 준다. 회사PC 상한(VRAM 8GB)에서 **컨텍스트를 얼마나 잡으면 어디서 꺾이는지**가 이 축의 실제 질문이다.

- 1차 출처: [GitHub — NHClimber87/llm-serve-dashboard](https://github.com/NHClimber87/llm-serve-dashboard), `fleet-metrics.py` import 전수(2026-08-04 조회), [`README.md`](https://github.com/NHClimber87/llm-serve-dashboard/blob/main/README.md)·`INSTALL.md`
- 반대 근거/한계: **직접 돌려 보지 않았다** — "stdlib만 쓴다"는 import 전수 확인이지 **동작 확인이 아니다**. `subprocess`를 쓰므로 **GPU 지표는 외부 명령(`nvidia-smi` 계열) 호출에 의존할 가능성이 높고**, 그 경로는 확인하지 않았다 — 3070/Windows에서 그 명령이 그대로 먹는지는 로컬 테스트벤치에서 먼저 봐야 한다. **eval·정확도 검증 없음.** **66★로 오늘 채택분 중 가장 작고 fork 10으로 검증 인구가 얇다.** 07-30 이후 푸시 없음. 계정 스캔에서 여러 저장소에 `.ps1`·`.bat`·`.exe`·`.wasm`이 걸렸으나 **전부 상류 유명 프로젝트의 fork**(`qwen-code`의 벤더링된 ripgrep·tree-sitter, `unsloth`, `ik_llama.cpp` 등)이고 **후보 본체는 CLEAN**, 캠페인 블롭과 SHA 무관 — 08-01 2단계 규칙에 따라 **오탐 처리**. 참고로 이 계정의 `andrej-karpathy-skills`가 **#1의 상류를 찾게 해 준 실마리**였다(04-16 생성 fork).
- 신뢰도: 중간~높음 — 라이선스·구성·CLEAN·import는 1차 확인, **동작·정확도는 미검증**.

---

## 오늘의 스택 시사점

1. **차단 지표를 "끼워 넣은 것"에서 "가져온 것"으로 옮겨라.** 지난 세 판이 exe 해시 → 파일 한 벌로 지표를 넓혀 왔는데, 오늘 보니 **그 전부가 공격자가 자유롭게 바꿀 수 있는 쪽**이었다. 바꿀 수 없는 쪽은 **훔쳐 온 마크다운**이다 — 그걸 바꾸면 저장소가 매력을 잃는다. 새 스킬 저장소를 받을 때 한 줄로 확인한다:

   ```bash
   # ① 후보의 SKILL.md 블롭 SHA를 뽑고
   gh api "repos/{owner}/{repo}/git/trees/HEAD?recursive=1" \
     --jq '.tree[]|select(.path|endswith("SKILL.md"))|"\(.sha[0:12]) \(.size) \(.path)"'
   # ② 같은 이름/설명의 상위 저장소를 찾아 같은 값을 뽑아 대조한다
   gh search repos "{설명 문구 그대로}" --sort stars --limit 5 \
     --json fullName,stargazersCount,createdAt,description
   # ③ 블롭이 같은데 fork가 아니면 그 자체가 신호다
   gh api "repos/{owner}/{repo}" --jq '"fork:\(.fork) parent:\(.parent.full_name // "none")"'
   ```

   **설명 문구를 그대로 검색창에 넣는 것**이 가장 싼 1단계다 — #1의 두 건 모두 설명이 원본과 글자까지 같았다.
2. **"별이 붙는 속도"는 검증이 아니라는 것이 다시 확인됐다.** 07-31이 *"별 수는 검증이 아니다"* 를 적었는데, 오늘은 **왜** 그런지가 보인다 — 별은 **내용물의 품질에 붙는 게 맞다.** 다만 그 내용물이 그 저장소의 것이 아닐 수 있다. 19.9만★ 원본의 파일을 그대로 담았으니 549★는 오히려 자연스러운 반응이다. **평가 대상과 별이 가리키는 대상이 어긋나 있다.**
3. **자기 한계를 적어 둔 산출물 우대(08-03 시사점 4)는 이제 "출처를 적어 둔 산출물"까지 넓힌다.** #5가 상류 3종을 URL과 함께 밝혀 놓은 덕에, 07-31 채택분과의 관계를 **오늘 알 수 있었다.** 계보를 안 밝힌 산출물은 나쁘다기보다 **중복·표절 판정을 불가능하게 만든다.** 채택 기준의 신뢰도 가점 항목에 **"상류 계보 명시 여부"** 를 추가할 만하다.
4. **자기 편을 드는 증거일수록 한 단계 더 검증하라.** #3의 *"마크다운 위키가 이겼다"* 는 이 스택의 방식을 정확히 칭찬하는 결론이었고, 그래서 **그냥 실었으면 아무도 이상하게 안 봤을 것**이다. 실제로는 채점 코드만 공개, 데이터·결과 비공개, 라이선스 없음, HN 2pt였다. **확증편향은 근거가 약할 때가 아니라 결론이 마음에 들 때 위험하다.**
5. **"왜"를 남기는 비용이 "왜"를 복원하는 비용보다 훨씬 싸다.** #4가 특히 값진 항목으로 꼽은 것은 **일어나지 않은 변경**이다 — 고치려다 이유를 알고 멈춘 판단은 **커밋이 없으므로 git 이력에도 안 남는다.** 회사PC 이식 작업에서 *"이건 왜 이렇게 돼 있지"* 로 시간을 태우는 것의 절반은 이 종류다. `git-history-ops`가 커버하지 못하는 정확히 그 틈이다.
6. **관측 도구는 stdlib 한 파일로도 충분하다.** #6이 61KB 파이썬 한 개로 하는 일을, 08-03에 뺀 항목은 pip 의존성 7종으로 했다. 08-03 시사점 3(*"효과 측정은 무거운 하네스를 요구하지 않는다"*)의 관측 버전이다 — **측정도, 관측도, 무거울 이유가 없다.**
7. **실패한 규칙과 실패한 결론을 구분하라.** #2에서 DISCOVERY를 폐기하려다 멈췄다. 3판 연속 실패는 사실이지만, 오늘 전수 조회를 하니 **실패가 소스별로 갈렸다.** 3판은 표본 3개였고, 그 표본이 우연히 한쪽에 몰렸을 뿐이다. **"연속 실패했으니 버린다"는 판단은 전수를 세기 전에 내리면 안 된다.**

## 전일 대비 변화

- **캠페인 성격 재규정**: 07-31 "동일 exe 반복" → 08-02 "은닉 설치 스크립트" → 08-03 "파일 한 벌" → **오늘 "상류 정품 마크다운의 fork 없는 재발행"**. 지목 계정 저장소는 **8개 유지(신규 0건, 규칙 도입 후 최초)**, 대신 최신 저장소 별이 **283 → 550**.
- **게이트 4차 교정**: 판별 축에 **"상류 블롭 일치 + fork 아님"** 을 추가. [ADOPTION-CRITERIA.md](../../ADOPTION-CRITERIA.md) 반영.
- **08-03 관측 정정**: `gup.xml`은 **8곳 동일이 아니라 2변종**(4,608B / 4,521B). 판정은 불변이라 [RE-ADJUDICATION.md](../../RE-ADJUDICATION.md)에 **뒤집힘 0건**으로 기록.
- **open query 1 종결**: DISCOVERY 전면 강등은 **부결**. 6클러스터 전수 조회에서 **2건 정확 일치·1건 18배 과대·3건 미확인**으로 실패가 비대칭임이 드러났다. 08-01 규칙(ID 확인 전 인용 금지)의 **적용 범위를 전 클러스터 전수로** 확정해 [METHODOLOGY.md](../../METHODOLOGY.md)에 명문화.
- **중복 판정 기준 상향**: 주제 중복이 아니라 **상류 중복**으로 본다(#5). 07-31 #3과 오늘 #5가 같은 뿌리였다는 것은 **후자가 계보를 밝혔기 때문에** 알 수 있었다.
- **로컬 스택 축은 유지**: 08-03에 편입한 축에서 오늘 A등급 1건(#6). 다만 이번 창의 로컬 항목 대부분은 여전히 **엔진·바인딩 빌드(G4)** 라 순위표에 못 올랐다.

## 이월 open query

1. **`keep-the-why` 교차 에이전트 확인(신규, 우선).** 저장소가 스스로 *"에이전트 1종에서만 구동, 교차 에이전트는 열린 공백"* 이라고 밝힌다. 회사PC는 여러 에이전트 병용이 전제이므로, **로컬 테스트벤치에서 다른 하네스로 같은 케이스를 돌려 보는 것**이 이식 전 조건이다.
2. **grill 계열 A/B(신규).** 07-31 #3(`finding-unknowns-skills`)과 오늘 #5(`grill-for-unknowns`)는 **같은 상류의 경쟁 구현이고 둘 다 MIT**다. 08-03 open query 3(STE A/B)과 같은 절차로 묶어 돌리면 러너 하나로 둘 다 판정된다.
3. **`llm-serve-dashboard` 실동작 확인(신규).** `subprocess` 경로가 3070/Windows에서 그대로 먹는지 로컬 테스트벤치에서 먼저 볼 것. 먹지 않으면 A등급 근거(설치 0)가 흔들린다.
4. **`OptMem` 라이선스 추적(신규).** 1,097★에 의존성 0 파이썬 단일 파일이라 **라이선스만 붙으면 즉시 재판정 대상**이다. 저자에게 이슈로 물을지는 사용자 판단(외부 접촉).
5. **#1의 상류 대조를 8곳 전부로.** 오늘은 2곳만 했다. 나머지 6곳(`ratchet`·`humanizer-cli`·`agents-council`·`FlashKDA`·`yoinks`·`openclaude-improved`)의 마크다운도 상류가 있는지 확인하면 **수법의 일반성**이 판정된다.
6. **`defending-code-reference-harness` 잔여 3종(08-03부터 이월).** `triage`(45KB, 카나리아 픽스처)·`patch`·`vuln-scan` 원문 미대조.
7. **Reddit 원문 확보(07-28부터 8판 이월).** 오늘 #3에서 **실제로 대가를 치렀다** — Reddit 98댓글 스레드를 못 봐서 "이 저장소로는 확인 불가"에서 멈췄다. **대안을 찾거나 "Reddit 집계는 정량 인용하지 않는다"로 규칙을 확정**할 것.
8. **GitHub 신고 여부는 사용자 판단 사항(08-03부터 이월).** #1은 외부 영향 조치라 임의 진행하지 않았다. 오늘 상류 저장소 2곳이 특정됐으므로 **원저작자 쪽에 알릴지**도 같은 성격의 판단이다.

---

*생성: Claude Code 자동 트렌드 리서치 (GitHub API 직접 관측 + last30days v3.16.0 DISCOVERY + HN Algolia item ID 전수 검증) · 관측 시각: 2026-08-04 KST · 방법론: [METHODOLOGY.md](../../METHODOLOGY.md) · 채택 기준: [ADOPTION-CRITERIA.md](../../ADOPTION-CRITERIA.md) · 재판정 원장: [RE-ADJUDICATION.md](../../RE-ADJUDICATION.md)*
