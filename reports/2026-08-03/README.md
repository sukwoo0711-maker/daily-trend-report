# 🧰 AI Personal Stack 트렌드 리포트 — 2026-08-03 (7건: 보안 1 · 방법론 1 · 채택 S 5)

> **조사 방식**: 하이브리드 5회차. ① 도구 발굴은 GitHub API 직접 관측(`created:>=2026-07-04`, 쿼리 3종) ② 뉴스·논쟁은 last30days v3.16.0 DISCOVERY(윈도우 2026-07-03 ~ 08-02) ③ 정량 인용은 08-01 확정한 **HN Algolia item ID 규칙** 적용 ④ **지목 계정 재스윕**(08-02 확정한 고정 목록).
> **범위**: AI Personal Stack 구축에 유용한 것만 — 사용 방법론, 자동화, Skills, MCP, GitHub Rising Star, 로컬/셀프호스팅, 에이전트 보안.
> **제외**: 일반 뉴스, 모델 출시 소식, 정책/시장 동향, 에이전틱 브라우저, **최근 7일 내(07-27~08-02) 리포트에서 다룬 항목**.
> **정렬 기준**: 보안·방법론 항목(등급 미적용) → 채택 등급 S, 각 그룹 안에서 관측 주목도순.
> **관측 시각**: **2026-08-03 KST**. 별 수·fork 수는 이 시점 단일 스냅샷.
> **출처 범위/누락**: GitHub API(직접) + DISCOVERY + HN Algolia. 누락 = X·YouTube·TikTok, **Reddit 원문**(7판 연속 미해결).

---

## 🚨 먼저 — 우리는 3판 동안 틀린 파일을 추적하고 있었다

상세는 #1. 요약하면 두 가지다.

1. 07-31에 지목한 계정이 **8번째 저장소**(`humanizer-cli`, 08-01 생성, 283★)를 냈다. 재스윕 규칙이 다시 적중했다.
2. 그보다 중요한 것 — **8개 저장소 전부가 실행 파일 하나만 담고 있는 게 아니라 세 파일 한 벌을 담고 있다.** `gup.xml` + `libcurl.dll` + 이름만 바뀌는 `.exe`. 그리고 그 `gup.xml`은 **Notepad++의 업데이터(WinGup) 설정 파일 원문**이다. 07-31·08-02 리포트는 "동일 블롭 `79d0513…`"만 추적했는데, **바이트가 동일한 그 exe는 오히려 제3자 정품일 가능성이 높고, 저장소마다 다른 쪽은 DLL이다**(8개 저장소 = 8개 서로 다른 DLL 블롭).

**게이트를 3차 교정했다** — 판별 단위를 "반복되는 동일 블롭"에서 **"함께 실려온 파일 한 벌"** 로 넓힌다. [ADOPTION-CRITERIA.md](../../ADOPTION-CRITERIA.md)에 반영했다.

## ⚠ 게이트/중복/검증실패로 제외한 항목(투명 처리)

| 반환 항목 | 처리 | 사유 |
|---|---|---|
| `UiPath/coder_eval` (108★, Apache-2.0) — 08-02 이월 | **B등급 예외 부결(판정 완료)** | 예외 조건 ①"대체 가능한 S/A 수단 없음" **불충족**. 오늘 #4가 **stdlib 3파일**(`run_bench.py`+`ste_lint.py`+`scenarios.json`)로 같은 목적(스킬 효과 A/B 측정)을 달성한다. 655파일·py 361개를 설치할 이유가 사라졌다 |
| DISCOVERY #1 — "빌더가 유저보다 더 흥분해 있다" | **제외(중복)** | **07-29 #1과 동일 논쟁**. 7일 규칙. 참여도는 커졌으나(HN 392pt·232댓글 + Reddit 1,152댓글 집계) 재게재하지 않음 |
| DISCOVERY #2 — 과소평가된 에이전트 활용처 | **제외(검증 실패)** | **4판 연속 재부상, 3판 연속 HN ID 미확인**. 08-01 규칙 적용 |
| DISCOVERY #3 — llama.cpp의 DeepSeek v4 tool calling 수정 | **제외(검증 실패 + 범위)** | 엔진은 **HN 655댓글·1,334pt**로 집계했으나 **30일 창 안에 해당 HN 스토리가 없다**(Algolia 무응답). 게다가 모델 대응 패치 = 출시 소식 계열 |
| DISCOVERY #4·#5·#6 — Qwen 코딩 점검 / LangGraph 법률 RAG / 엔터프라이즈 콜센터 플랫폼 | **제외** | #4는 근거 2건·61 상호작용으로 **박함**, #5는 **쇼케이스 프로젝트**(이식 대상 아님), #6은 **범위 외**(콜센터 상용 플랫폼) |
| `QoderAI/better-harness` (1,431★, MIT) | **제외** | **G4** — js 285개·549파일. 하네스 본체 |
| `jakubkrehel/skills` (2,692★, MIT) | **제외** | **범위 외** — UI 제작용 스킬 모음 |
| `pillar-labs/sail-skill` (136★) | **제외** | **G3** `NOASSERTION` 미확인 + `dist/sail-skill.zip`으로만 배포(내용 확인 불가) |
| `NulightJens/humanizer-stack` (167★) | **제외** | **G3** `NOASSERTION` + **주제 중복**(08-01 #3, 08-02 #5가 이미 AI 문체 제거) |
| `Vincentwei1021/video-shotcraft`(3,220★), `agiwhitelist/auteur`(708★), `worldwonderer/novel-to-game`(509★) 등 영상·드라마·콜라주 스킬 다수 | **제외** | **범위 외** — 미디어 제작. 이 카테고리가 신규 스킬 저장소 상위를 계속 차지한다 |
| `0rangec3t/Black-cat`(175★), `robbin/wechat-exporter`(186★) | **제외** | **G3** 라이선스 없음(후자는 메신저 복호화라 **G1**도 해당) |
| `0xwilliamortiz/humanizer-cli` (283★) | **제외** | **G1** — #1 캠페인 계정 8번째 저장소 |

---

## 요약 순위표

| 순위 | 트렌드 | 등급 | 라이선스 | 분류 | 관측 근거·시점 | 신뢰도 |
|---|---|---|---|---|---|---|
| 1 | **캠페인 재구성** — 8번째 저장소 + **8개 전부가 WinGup 업데이터 한 벌**, 고정된 건 exe이고 **변하는 건 DLL** | N/A(보안) | — | 보안/공급망 | GitHub API 트리·블롭 SHA 8개 계정 전수 + `gup.xml` 원문 판독, 08-03 | **높음**(메타데이터 한정) |
| 2 | **DISCOVERY의 HN 집계는 3판 연속 ID 검증 실패** — 상위 3클러스터 전량 미확인 | N/A(방법론) | — | 방법론/검증 | HN Algolia 창 내 조회 0건 × 3, 08-03 | **높음** |
| 3 | `anthropics/defending-code-reference-harness` — **이월 내용심사 완료**, 스킬 8종은 통짜가 아니라 **낱개로 판정해야** 한다 | **S**(부분) | Apache-2.0 | 보안/방법론 | GitHub API: 6,894★, `threat-model`·`verify` 원문 대조, CLEAN | 중간~높음 |
| 4 | `AminBlg/SimpleEnglish` — ASD-STE100을 스킬로. **96 generations 자체 eval + 정직한 한계 고지** | **S** | MIT | 문서품질/사양서 | GitHub API 1,324★ + **HN [`49114639`](https://news.ycombinator.com/item?id=49114639) 333pt·119댓글(07-30)** | **높음** |
| 5 | `codejunkie99/graph-engineering` — 프롬프트가 아니라 **토폴로지**를 설계한다(지식그래프 9단계 + 태스크그래프) | **S** | MIT | 방법론/지식그래프 | GitHub API: 271★, md 8(순수 마크다운), CLEAN | 중간 |
| 6 | `danyuchn/asd-ste100-skill` — 같은 표준의 **5파일 경량 독립 구현** | **S** | MIT | 문서품질/사양서 | GitHub API: 251★, 파일 5개, 계정 전체 CLEAN | 중간 |
| 7 | `T-Zevin/SkillGuardrail` **문서부** — 스킬 설치 전 검사 **규칙 카탈로그**(스캐너 본체는 제외) | **S**(문서) | Apache-2.0 | 보안/체크리스트 | GitHub API: 142★, `docs/rules.md`·`threat-model.md`, 계정 전체 CLEAN | 중간~높음 |

---

## 상세

### 1. 캠페인 재구성 — 고정된 exe가 아니라 변하는 DLL을 보라 🚨

먼저 재스윕 결과. 계정 `0xwilliamortiz`에 **8번째 저장소**가 생겼다.

> `humanizer-cli` — *"33 ways to spot AI-written text, right in your terminal. Before/after examples, draft checker, **zero dependencies**."*
> **283★ · fork 31 · 생성 2026-08-01** · MIT · `sources/humanizer.exe` = **SHA `79d051352df6`**

07-31 리포트가 "규칙 준수 검사"(`ratchet`)를 표방했듯, 이번엔 **08-01 #3·08-02 #5가 다룬 "AI 문체 제거"** 를 정확히 표방한다. 이 리포트가 추천한 주제를 따라오는 패턴이 세 번째다.

**그런데 계정 전수 스캔에서 훨씬 중요한 것이 나왔다.** 8개 저장소를 파일 단위로 펼치자 전부 같은 **세 파일 한 벌**이었다.

| 저장소 | 생성 | ★ | exe(이름만 다름) | `libcurl.dll` SHA·크기 | `gup.xml` |
|---|---|---|---|---|---|
| `agents-council` | 07-20 | 295 | `council-worker.exe` | `44a8f7793a6f` · 816,128 | ✔(2곳) |
| `andrej-karpathy-skills` | 07-21 | 546 | `fastsetup.exe` | `e2dd51550a7c` · 803,840 | ✔ |
| `yoinks` | 07-21 | 53 | `yoinks.exe` | `8ec1827cd715` · 802,304 | ✔ |
| `openclaude-improved` | 07-26 | 566 | `vibecodecalc.exe` | `ba43d6846cb0` · 805,888 | ✔ |
| `ponytail-improved` | 07-28 | 579 | `vibecodecalc.exe` | `06a4751af94c` · 797,696 | ✔ |
| `FlashKDA` | 07-29 | 193 | `vibecodecalc.exe` | `08fc92045cdb` · 805,888 | ✔ |
| `ratchet` | 07-31 | 409 | `ratchetui.exe` | `321be5869c01` · 816,640 | ✔ |
| **`humanizer-cli`** | **08-01** | **283** | `humanizer.exe` | `c8ce1b92940d` · 809,984 | ✔ |

**exe는 8개 전부 바이트 동일(`79d051352df6`, 804,688B). DLL은 8개 전부 다르다** — SHA도 크기도(797,696 ~ 816,640B) 제각각이다.

그리고 `gup.xml`을 열어 보면 정체가 드러난다. 8개 전부 **내용이 같고**, 그 내용은 **WinGup(= Notepad++의 범용 업데이터)의 설정 파일 원문**이다. 저작권 헤더는 `Copyright 2007 Don HO`, LGPL 고지가 그대로 있고, 본문에는 이런 값이 들어 있다.

```xml
<InfoUrl>https://notepad-plus-plus.org/update/getDownloadUrl.php</InfoUrl>
<SoftwareName>Notepad++</SoftwareName>
<ClassName2Close>Notepad++</ClassName2Close>
<SilentMode>yes</SilentMode>
```

**"AI 문체 탐지 CLI"나 "복잡도 린터"가 Notepad++ 업데이터 설정을 원문 그대로 담을 이유는 없다.** WinGup은 libcurl로 URL에서 업데이트 정보를 받아 패키지를 내려받아 설치하는 프로그램이고, `SilentMode=yes`는 **네트워크 오류를 사용자에게 알리지 않는다**는 설정이다. 저장소가 `package.json`에 *"No network, no API key, no dependencies"* 라고 적어 둔 것과 정면으로 어긋난다 — libcurl은 네트워크 라이브러리다.

**여기서 추적 대상이 바뀐다(추론임을 명시한다).** 관측된 사실만 다시 적으면 ① exe는 8곳에서 불변 ② DLL은 8곳에서 전부 상이 ③ 설정은 제3자 정품 업데이터의 것. 이 조합에 가장 잘 맞는 설명은 **exe가 정품 제3자 실행 파일이고, 저장소마다 갈아끼우는 쪽이 그 프로그램이 자기 폴더에서 읽어 들이는 DLL** 이라는 것이다. 그렇다면 07-31·08-02가 "페이로드"로 지목해 온 블롭 `79d0513…`은 **페이로드가 아니라 운반 수단**이고, 해시 차단 목록에 exe만 올렸다면 8종의 DLL은 전부 통과한다.

**JS 런처도 07-31과 다른 방식으로 같은 곳에 도착한다.** `ratchet`은 정책 우회·base64·창 숨김 같은 노골적 은닉 신호를 썼는데, `humanizer-cli`의 `sources/launch.mjs`는 반대로 **결백해 보이도록 쓰여 있다**(`windowsHide: false`, 우회 없음, 주석에 *"Does nothing risky"*). 그럼에도 동작은 이렇다.

- `cmd /c start "" cmd /k <binary>` — 실행 파일을 **인자 없이 별도 창에서 띄우고** `stdio:"ignore"` + `unref()`로 **손을 뗀다**.
- 사용자가 보는 패널은 **Node가 `SKILL.md`를 읽어 직접 출력**한다. 주석이 스스로 밝힌다 — *"패널은 이 폴더에 어떤 바이너리가 있든, **그것이 아예 돌지 않든** 똑같이 보인다"*, *"`sources/`에 다른 exe를 떨어뜨려도 그대로 동작한다"*.

즉 **화면에 보이는 것과 실제로 실행되는 것이 설계상 분리돼 있다.** 사용자는 정상 출력을 보고, 바이너리는 다른 창에서 무엇이든 한다.

**조치**: 8개 저장소를 별·fork 수와 무관하게 신뢰하지 말 것. 차단 목록을 만든다면 **exe 해시가 아니라 `gup.xml` 동반 여부**로 잡는 편이 낫다.
- 1차 출처: [`0xwilliamortiz`](https://github.com/0xwilliamortiz) 계정 전수 트리·블롭 SHA(2026-08-03), [`humanizer-cli/sources/gup.xml`](https://github.com/0xwilliamortiz/humanizer-cli/blob/main/sources/gup.xml)·[`launch.mjs`](https://github.com/0xwilliamortiz/humanizer-cli/blob/main/sources/launch.mjs)·`package.json` 원문
- 반대 근거/한계: **바이너리는 내려받지도 분석하지도 않았다 — 악성 단정이 아니다.** "exe가 정품 WinGup"이라는 것은 **동반 설정으로부터의 추론**이며 확정이 아니다. 반증 방법은 있다 — 공식 WinGup 릴리스와 해시를 대조하고, DLL 8종을 정품 libcurl 빌드와 대조하면 판정된다. 이 리포트는 **표본을 받지 않는다는 원칙** 때문에 그 대조를 하지 않았다. `gup.xml`의 `InfoUrl`은 **공격자 서버가 아니라 Notepad++ 기본값 그대로**였다는 점도 함께 적어 둔다. 표본은 계정 1개이고 GitHub 조치 여부는 미확인이다.
- 신뢰도: **높음**(파일 구성·SHA·설정 원문에 한해). 해석은 **중간**.

### 2. DISCOVERY의 HN 집계, 3판 연속으로 ID 검증에 실패했다 🔍

08-01 #1에서 **"HN 수치는 item ID로 확인되기 전엔 인용 금지"** 를 규칙으로 세웠다. 오늘 그 규칙을 상위 클러스터 전부에 적용한 결과가 이렇다.

| 엔진이 보고한 값 | Algolia 창 내 조회(2026-07-03 이후) | 판정 |
|---|---|---|
| #1 빌더↔유저 격차 — HN 232댓글·392pt | 해당 스토리 **0건** | 인용 불가 |
| #2 과소평가된 활용처 — HN 232댓글·450pt | **0건** | 인용 불가 |
| #3 llama.cpp tool calling — HN **655댓글·1,334pt** | **0건** | 인용 불가 |

세 클러스터가 **HN 댓글 수를 232로 똑같이** 보고한 것부터가 집계 오염의 표시다. 08-01(6건 중 3건 미확인), 08-02(2건 중 1건 미확인)에 이어 **3판 연속**이고, 오늘은 **상위 전량**이다.

**그런데 같은 도구가 반대 방향으로는 값을 했다.** 엔진의 집계 수치가 아니라 **키워드 축**을 단서로 삼아 Algolia를 직접 조회하자, 오늘 채택 1건이 그 자리에서 검증됐다 — `agent skills` 질의가 **HN [`49114639`](https://news.ycombinator.com/item?id=49114639), 333pt·119댓글, 2026-07-30, URL이 `github.com/AminBlg/SimpleEnglish`** 를 반환했다(#4).

**제안(다음 판 적용)**: DISCOVERY를 **정량 인용원에서 완전히 제외**하고 **주제 후보 발견기로만** 쓴다. 수치는 언제나 Algolia 직접 조회로만 적는다. 지난 3판의 실측이 같은 결론을 가리킨다.
- 1차 출처: HN Algolia `search?tags=story&numericFilters=created_at_i>1783036000`, 2026-08-03 조회
- 반대 근거/한계: **엔진이 Reddit 쪽에서는 실제 스레드를 정확히 물어온다** — 실패 축은 HN 집계에 한정된다. Algolia 조회는 키워드 기반이라 **제목이 크게 다른 스토리를 놓쳤을 가능성**을 배제하지 못한다(그래서 "존재하지 않는다"가 아니라 "인용 불가"로 적는다).
- 신뢰도: **높음** — 3판에 걸친 반복 관측.

### 3. `anthropics/defending-code-reference-harness` — 스킬 8종은 낱개로 판정해야 한다 🛡️ **[S(부분) · Apache-2.0]**
**6,894★ · 생성 2026-05-22 · 최종 푸시 07-16 · CLEAN · 07-31 발견 → 08-01·08-02 2회 연기 → 오늘 심사 완료**

07-31 재판정 원장이 *"스킬 부분은 이식 가능, S~A 후보"* 로 기록하고 두 판을 미룬 항목이다. 원문을 열어 본 결과 **그 기록은 절반만 맞았다.**

`.claude/skills/` 아래 8종을 실제로 읽으면 두 부류로 갈린다.

| 스킬 | 판정 |
|---|---|
| `threat-model`(SKILL 7.4KB + bootstrap 22KB + interview 9KB + schema 6.8KB) | **이식 가능** — 대상 코드베이스가 무엇이든 성립 |
| `triage`(45KB, 카나리아 픽스처 포함), `patch`(25KB), `vuln-scan`(12KB) | 이식 가능 후보(구성 확인, 원문 미대조) |
| **`verify`(2.3KB)** | **이식 불가** — `harness/agent_image.py`, `harness.auth.resolve_auth_env()`, docker `-e` 주입 등 **이 저장소 내부에 묶여 있다** |
| `quickstart`·`customize` | 저장소 온보딩용 |

`threat-model`이 왜 값어치가 있는지는 자기 문장이 설명한다 — *"위협 모델은 지도이고, 취약점 발견은 금속 탐지기다."* 그리고 **리트머스 시험**을 준다: *"코드 한 줄을 고쳐서 사라지면 그건 위협이 아니라 취약점이다."* 세 모드(`interview` / `bootstrap` / `bootstrap-then-interview`)로 나뉘어, **담당자가 있으면 인터뷰하고 없으면 코드와 과거 CVE·git 이력에서 유도**한다. 담당자가 없는 이식 대상 코드를 다뤄야 하는 상황에 정확히 들어맞는 모드가 이미 있다.

의존은 공유 모듈 `_lib/checkpoint.py` 하나이고, 07-31에 import 전수 확인으로 **표준 라이브러리만** 쓰는 것이 확인됐다.

**교훈은 항목 자체보다 절차 쪽이다.** "저장소가 Apache-2.0이고 스킬 폴더가 마크다운이니 스킬은 다 이식 가능"이라는 07-31의 요약은, **낱개로 열어 보니 8종 중 최소 1종이 반증**됐다. 혼합 저장소를 **라이선스 기준으로만** 쪼개고 **이식성 기준으로는 쪼개지 않은** 것이 원인이다.
- 1차 출처: [GitHub — anthropics/defending-code-reference-harness](https://github.com/anthropics/defending-code-reference-harness), [`threat-model/SKILL.md`](https://github.com/anthropics/defending-code-reference-harness/blob/main/.claude/skills/threat-model/SKILL.md), `verify/SKILL.md` 원문
- 반대 근거/한계: **`triage`·`patch`·`vuln-scan` 3종은 크기·구성만 확인했고 원문 대조는 하지 않았다** — 오늘 판정은 `threat-model`(채택)과 `verify`(제외)에 한정된다. 하네스 본체(`pyproject.toml`·py 66개)는 **G4로 여전히 제외**다. `threat-model`의 `allowed-tools`가 `Bash(gh api:*)`·`Task`를 요구하므로 **하네스가 그 권한 모델을 지원해야** 한다. **eval 없음.** 07-16 이후 푸시 없음.
- 신뢰도: 중간~높음 — 라이선스·CLEAN·구성은 1차 확인, 2종은 원문 대조까지 완료, 3종 미대조.

### 4. `AminBlg/SimpleEnglish` — 자기 효과를 실제로 재 본 첫 채택분 📐 **[S · MIT]**
**1,324★ · fork 43 · 생성 2026-07-21 · CLEAN · HN [`49114639`](https://news.ycombinator.com/item?id=49114639) 333pt·119댓글(2026-07-30)**

항공·방산의 정비 매뉴얼 통제언어인 **ASD-STE100 Simplified Technical English(Issue 9)** 의 53개 규칙을 스킬로 옮긴 것이다. 구성은 `skills/simple-english/SKILL.md`(18KB) + `references/{checklist,use-cases}.md` — **복사만으로 이식된다.** 프런트매터에 `compatibility: claude-code cursor codex gemini-cli opencode`를 명시한 **하네스 중립** 산출물이다.

스킬이 시키는 것은 문체 조언이 아니라 절차다: 모드 선택(pragmatic/strict) → 각 문단을 **절차문/서술문으로 분류**(나머지 규칙이 전부 여기 의존) → **초안 전에 어휘를 고정**(check/verify/confirm/validate 중 **동사 하나만**, config/settings 중 **명사 하나만** 골라 문서 전체에서 그것만 쓴다) → 규칙 적용 → **자가 점검(선택 아님)** → 코드·식별자·인용된 오류 메시지는 **건드리지 않는다**.

**08-02가 남긴 open query("채택 6건 전부 eval이 없다")에 대한 오늘의 답이 이 항목이다.** `evals/`에 측정이 커밋돼 있다.

> **6개 모델 × 8개 과제 = 96 generations 실측, 100단어당 STE 위반 평균 72.9% 감소.**
> 모델별 감소폭 41.0% ~ 82.1%, 평균 문장 길이도 함께 짧아지고(예: 11.1→8.5단어) **출력 토큰은 오히려 줄었다**(196→159 등).

더 중요한 것은 같은 파일의 **`## Honest number warnings`** 절이다. 스스로 이렇게 적어 두었다 — 린터는 **정규식 패스라 수동태·품사를 못 잡아 실제 위반을 과소 집계**한다(다만 양쪽 조건에 동일 적용이라 비교는 공정하다), **스킬 조건은 SKILL.md를 프롬프트에 넣으므로 입력 토큰이 설계상 더 든다**, **셀당 1회 생성이라 분산을 보려면 재실행하라**, 그리고 *"어떤 도구도 ASD-STE100 준수를 보장할 수 없다, 이 도구를 포함해서."* 재현 명령까지 한 줄로 준다(`python3 evals/run_bench.py`).

**이 스택에 특히 맞는 이유**: 사용자의 작업 대상이 **사양서·결함 이력·이식 문서**다. STE는 원래 그런 문서를 위해 만들어진 표준이고, 부수 효과로 **기계 번역 품질과 비원어민 가독성**이 올라간다. 그리고 `ste_lint.py`는 import가 `json`·`re`·`sys`뿐이라 **린터만 떼어 내 A등급으로 따로 쓸 수도 있다**(설치 0).
- 1차 출처: [GitHub — AminBlg/SimpleEnglish](https://github.com/AminBlg/SimpleEnglish), [`evals/results/RESULTS.md`](https://github.com/AminBlg/SimpleEnglish/blob/main/evals/results/RESULTS.md), [`skills/simple-english/SKILL.md`](https://github.com/AminBlg/SimpleEnglish/blob/main/skills/simple-english/SKILL.md)
- 커뮤니티 신호(창 안, ID 검증): HN [`49114639`](https://news.ycombinator.com/item?id=49114639) 333pt·119댓글. 상위 반응은 **더 줄이라는 쪽**이다 — 한 사용자가 산출물을 인용하며 *"'Before you start, make sure that your AWS credentials are correct'보다 'Before start, ensure AWS credentials are correct'가 낫지 않나"* 라고 되묻는다. 반대편 신호도 창 안에 있다 — HN [`49139845`](https://news.ycombinator.com/item?id=49139845) *"Ask HN: 에이전트에 왜 '스킬'이 필요한지 아직 모르겠다"*(13pt, 08-02)에서 `infotainment`가 답한다: *"'잘 정리된 마크다운 문서'가 바로 스킬이다"* — 제목과 설명만 목록으로 보여 주고 **에이전트가 필요한 것만 골라 읽는** 방식이라는 점이 차이라는 것이다.
- 반대 근거/한계: **eval은 저자 자신이 만든 정규식 린터로 채점한다** — 독립 채점도, 사람 평가도 없다. **셀당 1회 생성**이라 분산 미측정. 측정 대상 모델이 한 벤더 계열에 몰려 있다. **입력 토큰 증가는 측정에서 빠져 있다**(저자가 명시함) — 18KB SKILL.md를 매번 주입하는 비용은 직접 재야 한다. 07-21 이후 푸시 없음. **한국어 문서에는 그대로 적용되지 않는다** — 영어 산출물용 규칙이다.
- 신뢰도: **높음** — 구성·라이선스·CLEAN·HN 실재가 1차 확인, 효과는 **자체 측정치가 존재하고 한계가 공개**됨.

### 5. `codejunkie99/graph-engineering` — 프롬프트가 아니라 토폴로지를 설계한다 🕸️ **[S · MIT]**
**271★ · fork 38 · 생성 2026-07-23 · md 8(순수 마크다운) · CLEAN**

*"프롬프트 엔지니어는 모델의 말을 조종했고, 루프 엔지니어는 반복을 조종했다. 그래프 엔지니어는 **위상(topology)** 을 조종한다."* 두 축으로 나뉜다 — **지식 그래프**(에이전트가 *기억하는* 것: 노드는 개체·사실, 엣지는 시간과 출처가 붙은 관계, 온톨로지 → 추출 → 융합 → 서빙)와 **태스크 그래프**(에이전트가 *일하는* 방식: 노드는 작업, 엣지는 실행 의존성, 병렬 팬아웃·별도 검증자·정지 규칙·사람 게이트).

내용의 출처가 특이하다 — **동남대(东南大学)의 대학원 지식그래프 강의**([npubird/KnowledgeGraphCourse](https://github.com/npubird/KnowledgeGraphCourse), 4.4K★, 2019년부터 중국어로 강의)를 번역·증류하고 그 위에 태스크그래프 연구를 얹었다. `references/`가 커리큘럼 맵·모델링·추출·융합/GraphRAG·태스크그래프 5편으로 갈라져 있어 **필요한 단계만 꺼내 읽을 수 있다.**

**이 스택에서의 위치**: 사용자의 `offline-knowledge-base`·`spec-defect-search`가 정확히 "사양·결함 이력을 어떤 구조로 쌓고 어떻게 꺼내는가" 문제다. 그동안의 채택분이 **에이전트를 어떻게 배치할지**(08-02 #6~#9)에 몰려 있었다면, 이건 **데이터를 어떤 모양으로 둘지**를 다루는 첫 항목이다.
- 1차 출처: [GitHub — codejunkie99/graph-engineering](https://github.com/codejunkie99/graph-engineering), [`references/fusion-and-llm.md`](https://github.com/codejunkie99/graph-engineering/blob/main/graph-engineering/references/fusion-and-llm.md)
- 반대 근거/한계: **eval·측정 없음** — 교육 자료의 증류물이지 검증된 파이프라인이 아니다. **번역·요약본**이라 원 강의와의 충실도는 확인하지 않았다. **07-23 이후 푸시 없음**(생성일과 같은 날이 마지막). 계정 스캔에서 다른 저장소 2곳(`hyperclaw-avid`·`omi`)에 실행 파일이 걸렸으나 — 후보 저장소 본체는 CLEAN, 걸린 것은 **해당 저장소 자신의 Electron 커넥터와 펌웨어 도구(iperf)** 이며 **캠페인 블롭과 SHA 불일치** — 08-01 2단계 판정 규칙에 따라 **오탐 처리**했다.
- 신뢰도: 중간 — 구성·라이선스·CLEAN은 1차 확인, **효과 근거 없음**.

### 6. `danyuchn/asd-ste100-skill` — 같은 표준, 5파일짜리 독립 구현 ✂️ **[S · MIT]**
**251★ · fork 6 · 생성 2026-07-20 · 파일 5개 · CLEAN · 계정 전체 CLEAN**

`LICENSE` + `README.md` + `SKILL.md`(6.8KB) + `examples/before-after.md` + `references/writing-rules.md`. 그게 전부다.

**#4와 같은 표준을 서로 다른 저자가 따로 구현했고, 하루 차이로 나왔다**(07-20 / 07-21). 08-02 #5에서 "AI 냄새 제거"가 서로 다른 언어권에서 같은 3단 구성으로 수렴한 것을 관측했는데, 이번엔 **동일 표준에 대한 독립 구현 2건**이다. 표준이 이미 있는 영역에서는 스킬이 빠르게 수렴한다는 신호로 읽힌다.

**둘 중 무엇을 고를지**는 갈린다. **#4**는 규칙 53개를 다 담고(18KB) **자체 eval이 있다** — 근거를 원하면 이쪽. **이 항목**은 6.8KB라 **컨텍스트 예산이 빡빡할 때** 유리하고, 07-30 #3(긴 정책 문서는 지켜지지 않는다)의 관점에서는 **짧은 쪽이 실제로 더 지켜질 수도** 있다. 둘 다 MIT라 **같은 과제셋으로 A/B를 돌려 정하는 것**이 가장 값싸다.
- 1차 출처: [GitHub — danyuchn/asd-ste100-skill](https://github.com/danyuchn/asd-ste100-skill)
- 반대 근거/한계: **eval 없음** — #4와 달리 측정치가 전혀 없다. 53개 규칙 전체를 담았는지 **커버리지를 대조하지 않았다**(4.4KB `writing-rules.md`는 #4의 18KB보다 훨씬 작다 — 축약본일 가능성이 높다). **07-20 이후 푸시 없음.** 별 수가 #4의 1/5이다.
- 신뢰도: 중간 — 구성·라이선스·계정 전체 CLEAN은 1차 확인, **내용 커버리지·효과 미확인**.

### 7. `T-Zevin/SkillGuardrail` — 스킬을 깔기 전에 무엇을 볼 것인가 🧪 **[S(문서) · Apache-2.0]**
**142★ · fork 13 · 생성 2026-07-18 · 최종 푸시 07-31 · 본체 CLEAN · 계정 전체 CLEAN**

스킬 패키지를 **설치 전에 격리·검사**하는 스캐너다. 다만 본체는 **Go 프로그램**(`cmd/skillguardrail/main.go`, `go.mod`, `internal/cli/cli.go`)이라 **G4로 제외**한다. 오늘 채택하는 것은 저장소의 **문서 두 개** — `docs/rules.md`(규칙 카탈로그)와 `docs/threat-model.md`(15.9KB)다. Apache-2.0이 저장소 전체를 덮으므로 **07-31에 정한 혼합 저장소 규칙**대로 문서만 취한다.

**왜 이게 오늘 값이 있나**: #1에서 실측한 패턴이 이 카탈로그에 **이미 규칙 번호로 들어 있다.**

| 규칙 | 내용 | #1과의 대응 |
|---|---|---|
| `SG-FILE-002` | 불투명·네이티브 라이브러리·중첩 아카이브·실행 바이너리 동봉 | exe + `libcurl.dll` |
| `SG-EXEC-001` | 원격에서 받은 내용을 인터프리터에 파이프 | (WinGup의 다운로드-설치 동작) |
| `SG-EXEC-003` | 인코딩·조립된 명령을 동적 평가 | `ratchet`의 base64 `-EncodedCommand` |
| `SG-EXEC-005` | 동적 프로세스·셸 실행 API | `spawn(..., {detached, stdio:'ignore'})` |
| `SG-PI-002` | 사용자로부터 **행위나 지시를 은폐** | 패널과 실제 실행의 분리 |
| `SG-PI-005` | 변경 가능한 **외부 지시를 받아와 따름** | 업데이터 구조 그 자체 |

카탈로그가 스스로 밝히는 전제도 이 리포트의 태도와 같다 — *"규칙 매치는 검토를 위한 증거이지 악의의 증명이 아니다."* 그리고 **경계에 걸리면 열어 주는 게 아니라 닫는다**(*fail closed*) — 파일 수·바이트 예산·심볼릭 링크·경로 이탈·압축률 초과로 **검사를 끝내지 못하면 설치 가능 지문을 아예 내주지 않는다**.

**설치 없이 쓰는 법**: 두 문서를 그대로 에이전트에게 주고 **새 스킬을 받을 때 통과시킬 체크리스트**로 쓰면 된다. Go 바이너리 없이도 규칙 목록 자체가 검토 항목이다.
- 1차 출처: [GitHub — T-Zevin/SkillGuardrail](https://github.com/T-Zevin/SkillGuardrail), [`docs/rules.md`](https://github.com/T-Zevin/SkillGuardrail/blob/main/docs/rules.md), [`docs/threat-model.md`](https://github.com/T-Zevin/SkillGuardrail/blob/main/docs/threat-model.md)
- 반대 근거/한계: **채택 범위는 문서 2개뿐이다** — 스캐너를 돌리려면 Go 툴체인이 필요하고 그건 **G4**다. **eval·오탐률 공개 없음** — `benchmarks/`에 매니페스트(`scientific-100.csv` 등)와 로드맵은 있으나 **결과 수치는 없다**. 규칙 카탈로그는 **`builtin-v1` 초기 팩**이라 저자가 계속 바꿀 수 있다. 저장소 자산의 대부분(약 3MB)이 **스크린샷 PNG**다. **문서만 취하는 판정 자체가 이 리포트의 편의적 해석일 수 있다** — 저자는 스캐너를 쓰라고 배포한 것이다.
- 신뢰도: 중간~높음 — 라이선스·CLEAN·규칙 원문은 1차 확인, **도구 성능은 미검증**(도구를 채택하지 않았으므로 판정에 영향 없음).

---

## 오늘의 스택 시사점

1. **차단은 해시가 아니라 파일 구성으로 하라.** #1의 8개 저장소는 **exe 해시가 동일**했기 때문에 지난 두 판이 그것을 지표로 삼았다. 그런데 저장소마다 갈아끼운 쪽은 **DLL 8종**이었다. 해시 목록은 **바꾸기 쉬운 쪽을 지목했을 때만** 작동한다. 더 안정적인 지표는 *"업데이터 설정 파일이 왜 문서 스킬 저장소에 있는가"* 처럼 **있어야 할 이유가 없는 파일**이다.
2. **"보이는 출력이 멀쩡하다"는 여전히 안전 근거가 아니다.** 08-02 #4가 논문으로 보인 것(출력 기반 평가로는 내부 왜곡이 안 보임)을 #1이 **코드로** 보여 준다 — 패널을 Node가 직접 그려서 바이너리가 무엇을 하든 화면이 같다. 08-02 시사점 3의 연장선이고, 이번엔 근거가 실측이다.
3. **효과 측정은 무거운 하네스를 요구하지 않는다.** #4의 eval은 **파이썬 3파일·표준 라이브러리**다. 이 사실 하나로 08-02가 이월한 `coder_eval`(py 361개)의 B등급 예외가 **부결**됐다. 자기 스킬의 효과를 재고 싶다면 `run_bench.py`·`ste_lint.py` 구조를 그대로 베끼는 게 가장 싸다 — 과제셋 JSON + 결정론적 채점기 + 재개 가능한 러너.
4. **한계를 스스로 적어 둔 산출물을 우대하라.** #4를 오늘의 최고 신뢰도로 올린 것은 72.9%라는 숫자가 아니라 **"이 린터는 과소 집계한다 / 셀당 1회라 분산을 모른다 / 어떤 도구도 준수를 보장 못 한다"** 를 저자가 먼저 적었기 때문이다. 채택 기준에 **"자기 한계 고지 여부"** 를 신뢰도 가점 항목으로 넣을 만하다.
5. **문서 표준은 이식 비용이 가장 낮은 개선이다.** #4·#6은 설치가 0이고 사양서·이식 문서에 바로 붙는다. 사내 문서에 적용할 때는 **어휘 고정 규칙**(한 개념에 한 단어)만 먼저 떼어 써도 효과가 나온다 — 스킬 전체를 도입하지 않아도 된다.

## 전일 대비 변화

- **추적 대상 정정**: 07-31·08-02가 지목한 블롭 `79d0513…`은 **8곳에서 불변**이고, 실제로 저장소마다 다른 것은 **`libcurl.dll` 8종**이었다. 캠페인 저장소는 7개 → **8개**(`humanizer-cli`, 08-01 생성).
- **게이트 3차 교정**: 07-31 계정 단위 → 08-01 오탐(무관 fork) → 08-02 오탐(읽을 수 있는 스크립트) → **오늘 "동반 파일 한 벌"** 로 판별 단위 확대.
- **2판 연속 연기했던 내용 심사 완료**: `defending-code-reference-harness`를 열어 보니 **스킬 8종이 균일하지 않았다**(`threat-model` 채택 / `verify` 이식 불가). `coder_eval`의 B등급 예외도 **부결로 종결**.
- **채택분에 처음으로 자체 측정치가 붙었다**: 08-02 open query 2("채택 6건 전부 eval 없음")에 #4가 답했다 — 96 generations 실측 + 한계 고지.
- **DISCOVERY 신뢰도 하락**: HN 집계가 **3판 연속** ID 검증 실패, 오늘은 **상위 3클러스터 전량**. 반면 Algolia 직접 조회는 채택 1건을 즉석에서 검증했다.
- **소급 재판정**: 오늘의 G1 교정은 **과거 판정을 뒤집지 않는다**(캠페인 저장소는 개정 전후 모두 제외). [RE-ADJUDICATION.md](../../RE-ADJUDICATION.md)에 "뒤집힘 0건"으로 기록했다.

## 이월 open query

1. **DISCOVERY의 지위를 규칙으로 확정할 것(신규, 다음 판 최우선).** 3판 연속 실패는 우연이 아니다. **"DISCOVERY는 주제 후보 발견에만 쓰고, 모든 정량 인용은 HN Algolia 직접 조회로만 한다"** 를 METHODOLOGY에 명문화할지 결정한다.
2. **#1의 반증 실험은 하지 않는다(정책 확인 요청).** exe를 공식 WinGup 릴리스와, DLL 8종을 정품 libcurl과 해시 대조하면 판정이 끝난다. 다만 **표본을 받지 않는다**는 현 원칙과 충돌한다. 원칙을 유지할지 사용자 판단이 필요하다.
3. **STE 스킬 A/B(신규).** #4와 #6은 같은 표준의 경쟁 구현이고 둘 다 MIT다. `model-downgrade-eval` 절차로 **사용자의 실제 사양서 문단**에 A/B를 돌리면, 이 리포트가 **자기 스택 데이터로 채택분을 고른 첫 사례**가 된다. #4의 `run_bench.py`가 그대로 러너로 쓰인다.
4. **`defending-code-reference-harness` 잔여 3종.** `triage`(45KB, 카나리아 픽스처)·`patch`·`vuln-scan`은 오늘 원문 대조를 못 했다. `triage`는 07-31 #4와 같은 "판정자를 일부러 망가뜨린 입력으로 검증" 계열이라 우선순위가 높다.
5. **Reddit 원문 확보(07-28부터 7판 이월).** 공개 JSON이 봇 차단이다. **대안을 찾거나 "Reddit 집계는 정량 인용하지 않는다"로 규칙을 확정**할 것.
6. **하이브리드 쿼리 세트 고정(07-30부터 이월).** 재스윕 대상은 `0xwilliamortiz` 1개로 유지. 오늘 신규 후보 계정은 나오지 않았다.
7. **GitHub 신고 여부는 사용자 판단 사항.** #1은 외부 영향 조치라 임의 진행하지 않았다.

---

*생성: Claude Code 자동 트렌드 리서치 (GitHub API 직접 관측 + last30days v3.16.0 DISCOVERY + HN Algolia item ID 검증) · 관측 시각: 2026-08-03 KST · 방법론: [METHODOLOGY.md](../../METHODOLOGY.md) · 채택 기준: [ADOPTION-CRITERIA.md](../../ADOPTION-CRITERIA.md) · 재판정 원장: [RE-ADJUDICATION.md](../../RE-ADJUDICATION.md)*
