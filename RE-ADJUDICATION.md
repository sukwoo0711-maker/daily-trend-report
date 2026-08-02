# 소급 재판정 원장

[ADOPTION-CRITERIA.md](ADOPTION-CRITERIA.md)가 개정될 때, **개정 전 기준으로 제외했던 과거 항목을 다시 판정한 기록**이다.

과거 리포트는 **날짜 스냅샷이므로 수정하지 않는다**([METHODOLOGY.md](METHODOLOGY.md)의 정정 원칙). 판정이 뒤집힌 경우 원문은 그대로 두고 이 원장에 결과를 남긴다.

---

## 2026-07-31 개정에 따른 재판정

**개정 내용**: ① G3 통과 목록을 산출물 유형별로 분리(문서형에 CC0-1.0·CC-BY-4.0 추가, NC·ND·SA는 제외 유지) ② `NOASSERTION`은 자동 탈락이 아니라 LICENSE 원문 확인 신호 ③ G1 바이너리 스캔을 계정 단위로 승격.

**재판정 범위**: 채택 기준은 2026-07-24에 확정됐으므로 **07-24 이후 리포트에서 라이선스(G3) 사유로 제외한 항목 전부**. 그 이전 리포트(07-15~07-23)에는 라이선스 게이트가 없었으므로 대상이 아니다.

**관측 시각**: 2026-07-31 KST. 별 수는 이 시점 GitHub API 단일 스냅샷.

### 결과 요약

| 원 판정 | 항목 | 재판정 | 사유 |
|---|---|---|---|
| 07-31 제외(G3) | `lopopolo/harness-engineering` (2,408★) | **→ 채택(문서형 S)** | CC-BY-4.0이 문서형 통과 목록에 신설 |
| 07-28·29·30 제외(G3+G2) | **Anthropic Claude Security 플러그인** | **→ 채택(S)** | 라이선스·비용이 모두 확인됨 (Apache-2.0 / 무료) |
| 07-27 제외(G3) | Rapid7 MCP 서버 + Agent Skill | **제외 유지(사유 교체)** | 라이선스는 MIT로 확인 → **G3 아님**. 실제 사유는 **G1+G2+G4** |
| 07-31 제외(G3) | `VictorTaelin/OptMem` (926★) | **제외 유지** | LICENSE 파일 여전히 없음(재확인) |
| 07-31 제외(G3) | `Kulaxyz/token-diet` (513★) | **제외 유지** | LICENSE 파일 여전히 없음(재확인) |
| 07-30 제외(G3) | `0xwilliamortiz/openclaude-improved` (559★) | **제외 유지(사유 강화)** | LICENSE는 "독점 파생물" NOTICE → 불명이 아니라 더 강한 제외 근거. 07-31 #1의 그 블롭도 포함 |
| 07-31 제외(G3) | `KinetiNode/claude-fable-5-system-prompt-clean` (431★) | **제외 유지** | 유출된 벤더 원저작물에 재배포자의 라이선스 표기가 미치지 않음. 개정과 무관 |

**뒤집힌 판정 2건, 사유 교체 2건, 유지 3건.**

---

### 1. Anthropic Claude Security 플러그인 — 3판 이월된 open query 해소 **[제외 → 채택 S]**

**원 판정**: 07-28 *"G3 라이선스 불명 + G2 비용 미확인. 오픈소스 여부·과금 조건 미확인"* → 07-29·07-30에도 같은 사유로 이월(3판 연속).

**재판정 근거 (2026-07-31 실측)**

두 가지가 모두 확인됐다.

- **라이선스**: 플러그인 본체가 [`anthropics/claude-plugins-official`](https://github.com/anthropics/claude-plugins-official) (**Apache-2.0**, 32,873★, 최종 푸시 2026-07-30)의 `plugins/claude-security/` 아래에 **공개**돼 있다. 플러그인 디렉터리에 자체 `LICENSE`도 있다. → **G3 통과**
- **비용**: 전체 사용자에게 제공되며, 파일 편집마다 도는 결정론 패턴 검사 계층은 **모델 호출이 없어 사용량 비용이 0**이다. → **G2 통과**

**구성** (바이너리 스캔 CLEAN, `anthropics` 계정 4개 저장소 계정 단위 스캔도 전부 CLEAN)

```
plugins/claude-security/
├── .claude-plugin/plugin.json
├── agents/          claude-security · explore · patch-generator · patch-verifier
│                    scan-inventory · scan-researcher · scan-verifier  (전부 .md)
├── skills/claude-security/SKILL.md  + jobs/{scan-changes,scan-codebase}.md
├── hooks/           banner_hook.sh · banner_notice.py · hooks.json
└── scripts/         patch_artifacts.py · render_report.py · write_scan_meta.py
```

**등급 판정**: 실체가 **마크다운 에이전트·스킬 정의 + 훅/스크립트**이고 별도 바이너리·서버·Docker 설치가 없다. 하네스 자체의 플러그인 기구로 얹힌다. → **G4 통과, S등급.**

**주목할 설계**: 에이전트가 `patch-generator`와 **`patch-verifier`로 분리**돼 있고 `scan-verifier`가 따로 있다. 생성자와 검증자를 다른 에이전트로 두는 구조로, 07-30 #1(fable-method의 `fable-judge`)·07-31 #4(이식 킷의 "판정자 없으면 종료 조건 없다")와 같은 계열이다. 사용자의 `subagent-review-durability` 관심사와 직접 겹친다.

**한계**: 베타이며 위 구성은 저장소 스냅샷 기준이다. **탐지 성능·오탐률에 대한 독립 평가는 확인하지 않았다** — 게이트 통과와 설계 구조만 확인했다. "결정론 계층은 비용 0"은 벤더 설명이며, 모델을 쓰는 심층 리뷰 경로의 비용은 별도다.

- 1차 출처: [`anthropics/claude-plugins-official`](https://github.com/anthropics/claude-plugins-official) — 저장소 트리·LICENSE 직접 관측(2026-07-31)
- 보조 출처: [MarkTechPost](https://www.marktechpost.com/2026/07/22/anthropic-releases-claude-security-plugin-for-claude-code-in-beta-a-multi-agent-vulnerability-scanner-that-runs-in-your-terminal/), [CybersecurityNews](https://cybersecuritynews.com/free-security-plugin-for-claude-code/) — 무료 제공·결정론 계층 비용 0
- 신뢰도: 중간~높음 — 라이선스·구성·바이너리 부재는 1차 확인, 비용은 벤더 설명 + 2차 교차, **성능은 미검증**

### 2. Rapid7 MCP 서버 — 제외는 유지, 사유는 교체 **[G3 → G1+G2+G4]**

**원 판정**: 07-27 *"실재하나 라이선스를 확인하지 못해 G3(라이선스 불명=제외)"*.

**재판정 근거**: 해당 저장소는 [`rapid7/rapid7-bulk-export-mcp`](https://github.com/rapid7/rapid7-bulk-export-mcp)로 확인되며 **라이선스는 MIT**(22★, 최종 푸시 2026-07-28, 바이너리 CLEAN). **즉 G3 제외는 사실과 달랐다.** 개정된 `NOASSERTION`·불명 처리 절차("확인 못 했으면 확인하라")를 적용하면 이 항목은 G3를 통과한다.

다만 **제외 결론 자체는 유지되며, 오히려 사유가 더 분명하다.**

- **G1 보안 — 탈락.** README가 **Platform Admin 권한의 조직 API 키**를 요구한다. 이유도 명시돼 있다 — *"bulk export API는 플랫폼 전체의 모든 취약점 데이터를 반환하므로 관리자급 접근이 필요하다."* 이는 채택 기준의 명시적 제외 항목인 **"광범위 자격증명 요구"** 에 정면으로 해당한다.
- **G2 비용 — 탈락.** Rapid7 Insight Platform 계정이 전제다. 상용 제품이므로 "완전 무료 또는 로컬 실행"을 만족하지 않는다.
- **G4 설치 — 탈락.** MCP 서버 설치가 필요하다(`py` 20개).

**교훈**: "라이선스 불명"이라는 포괄 사유가 **더 정확하고 더 강한 제외 근거를 가리고 있었다.** 확인 안 된 것을 불명으로 처리하는 관행은 안전한 쪽으로 틀리긴 하지만, 그 항목이 왜 위험한지를 기록하지 못한다. 개정된 절차(원문 확인 후 판정)는 이 점에서도 낫다.

### 3. 제외 유지 항목

- **`VictorTaelin/OptMem`** (926★, 2026-07-31 재확인) — 루트 구성이 `README.md`·`WINDOWS.md`·`install.sh`·`memo`·`test.py`·`anim`이며 **LICENSE 파일이 여전히 없다.** 형태는 문서형에 가깝지만, 개정으로 추가된 것은 CC0·CC-BY이지 "라이선스 없음"이 아니다. **제외 유지.**
- **`Kulaxyz/token-diet`** (513★, 2026-07-31 재확인) — `SKILL.md`·`activation.md` 등 사실상 문서형이지만 **LICENSE 파일 없음.** 토큰 절감이라는 주제가 이 스택의 최우선 관심사여도 동일 원칙을 적용한다. **제외 유지.** (같은 소유자의 `self-learning-skills`는 MIT라 07-30에 채택됐다 — 소유자가 아니라 저장소 단위로 본다.)
- **`0xwilliamortiz/openclaude-improved`** (559★) — LICENSE 파일이 *"Anthropic Claude Code CLI에서 파생됐으며 원본은 독점 소프트웨어"* 라는 NOTICE다. **제외 유지, 사유는 "불명"에서 "독점 파생물"로 강화.** 덧붙여 이 저장소는 07-31 #1의 그 블롭(`79d051352df6`)을 `bin/vibecodecalc.exe`로 담고 있어 **G1에도 걸린다.**
- **`KinetiNode/claude-fable-5-system-prompt-clean`** (431★) — 유출된 벤더 시스템 프롬프트의 재배포물. 재배포자가 붙인 표기는 원저작물의 권리에 영향을 주지 않으므로 라이선스 상태가 불명이다. **개정과 무관, 제외 유지.**

---

### 재판정 중 발견한 신규 항목 (재판정 결과 아님)

Claude Security open query를 해소하는 과정에서 나온 것으로, **과거에 제외된 적이 없으므로 재판정 대상이 아니다.** 다음 판 후보로 기록한다.

**[`anthropics/defending-code-reference-harness`](https://github.com/anthropics/defending-code-reference-harness)** — 6,880★, **Apache-2.0**(GitHub API는 `NOASSERTION` 반환 → LICENSE 원문 확인으로 판정), 생성 2026-05-22, 최종 푸시 07-16, 바이너리 CLEAN.

위협 모델링·스캔·트리아지·패치 스킬 8종(`threat-model`·`vuln-scan`·`triage`·`patch`·`verify`·`dnr-hunt`·`dnr-respond`·`customize`)과 자율 스캔 하네스가 함께 있다. **혼합 저장소 규칙 적용 대상**이다.

- **스킬 부분** — `.claude/skills/` 아래 마크다운 + 공유 모듈 `_lib/checkpoint.py`. 그 파이썬의 import를 전수 확인한 결과 `datetime`·`pathlib`·`json`·`os`·`re`·`shutil`·`sys`로 **전부 표준 라이브러리**다. → 이식 가능, S~A 후보
- **하네스 부분** — `pyproject.toml`·`dnr_harness/`·`bin/`·`py` 66개. → **G4 설치 필요, B등급**
- 루트 LICENSE가 Apache-2.0로 저장소 전체를 덮으므로 `harness-engineering`과 달리 **부분별 라이선스 모호성은 없다.** 나누는 기준은 라이선스가 아니라 설치 부담이다.
- `triage/fixtures/canary-findings.json` — **카나리아 픽스처**가 들어 있다. 검증자가 실제로 문제를 잡아내는지를 심어둔 값으로 확인하는 구조로, 07-31 #4(이식 킷의 "일부러 망가뜨린 코드로 판정자를 검증")와 같은 계열이다.

**내용 심사는 하지 않았다** — 게이트 적합성과 구성만 확인했다.

---

## 재판정을 유발한 규칙 변화 기록

| 날짜 | 변경 | 영향 |
|---|---|---|
| 2026-07-24 | 채택 기준(G1~G4) 최초 확정 | 이전 리포트(07-15~07-23)에는 소급 적용하지 않음 |
| 2026-07-31 | G3를 산출물 유형별로 분리(문서형에 CC0·CC-BY 추가) | 제외 → 채택 1건(`harness-engineering`) |
| 2026-07-31 | `NOASSERTION`을 자동 탈락에서 제외, LICENSE 원문 확인 의무화 | 제외 → 채택 1건(Claude Security), 사유 교체 1건(Rapid7) |
| 2026-07-31 | G1 바이너리 스캔을 계정 단위로 승격 | 제외 사유 강화 1건(`openclaude-improved`) |
| 2026-08-02 | G1을 불투명 바이너리 / 읽을 수 있는 스크립트로 분리 | 오탐 교정 1건(`microsoft/skill-recorder`) |
| 2026-08-03 | G1 판별 단위를 "반복되는 동일 블롭"에서 **"함께 실려온 파일 한 벌"** 로 확대 | **뒤집힘 0건**(아래) |

---

## 2026-08-03 재판정 — 뒤집힘 0건

08-03의 G1 3차 교정은 **판별 지표를 넓혔을 뿐 좁히지 않았으므로**, 개정 전 기준으로 제외했던 항목이 되살아날 여지가 구조적으로 없다. 전수 확인 결과는 아래와 같다.

- **캠페인 저장소 8개** — 개정 전에는 "동일 블롭 반복"으로, 개정 후에는 "동반 파일 한 벌(`gup.xml` + 저장소마다 다른 `libcurl.dll`)"로 제외된다. **결론 동일, 근거만 강화.** 다만 실무적 함의는 달라진다 — 차단 목록을 exe 해시로 만들었다면 **DLL 8종은 전부 통과**했을 것이다. 상세는 [2026-08-03 리포트 #1](reports/2026-08-03/README.md#1-캠페인-재구성--고정된-exe가-아니라-변하는-dll을-보라-).
- **08-01·08-02에 오탐으로 판정했던 항목**(`AmazingAng/old-coder`, `microsoft/skill-recorder`) — 새 기준으로 동반 파일 구성을 다시 봐도 이상 없다. **오탐 판정 유지, 채택 유지.**
- **08-03 신규 후보 5건** — 처음부터 새 기준으로 심사했으므로 재판정 대상이 아니다.

이번 개정으로 **채택 상태가 바뀐 과거 항목은 없다.** 규칙 변화를 원장에 남기는 것이 목적이며, 과거 리포트는 날짜 스냅샷이므로 수정하지 않는다.
