# 🧰 AI Personal Stack — Daily Trend Report

최근 30일 웹 리서치(last30days 방식)를 기반으로, **AI Personal Stack 구축에 유용한 트렌드만** 골라 매일 TOP 10을 인기도 순으로 정리하는 아카이브.

## 다루는 것 / 다루지 않는 것

| ✅ 다룸 | ❌ 제외 |
|---|---|
| AI 사용 방법론 (Context Engineering, SDD 등) | 일반 뉴스 (스포츠·엔터·정치) |
| 자동화 (워크플로, 에이전트 오케스트레이션) | 모델 출시 소식 자체 |
| Skills (Claude Code 스킬, 에이전트 스킬 생태계) | AI 기업 시장/투자 동향 |
| MCP 서버 | 정책·규제 뉴스 |
| GitHub Rising Star (급성장 AI 저장소) | 에이전틱 브라우저 |
| 로컬/셀프호스팅 스택, 에이전트 보안 | 이전 리포트에서 이미 다룬 항목 (중복 금지) |

## 구조

```
daily-trend-report/
├── README.md                     ← 이 파일 (인덱스)
├── templates/
│   └── daily-report-template.md  ← 데일리 리포트 템플릿
└── reports/
    └── YYYY-MM-DD/               ← 하루 1폴더
        └── README.md             ← 그날의 트렌드 리포트
```

## 운영 규칙

- **주기**: 매일 1회
- **분량**: 트렌드 TOP 10 (최초 등록판인 2026-07-15만 TOP 20)
- **정렬**: 인기도(스타 수·성장 속도·언급량 추정) 내림차순
- **조사 범위**: 리포트 날짜 기준 최근 30일
- **형식**: 요약 순위표 + 트렌드별 상세(설명, 인기도 근거, 출처 링크) + 스택 시사점

## 리포트 인덱스

| 날짜 | 리포트 | 비고 |
|---|---|---|
| 2026-07-16 | [TOP 10](reports/2026-07-16/README.md) | 중복 제외 규칙 적용 시작 |
| 2026-07-15 | [TOP 20](reports/2026-07-15/README.md) | 최초 확대판 |

---

*Powered by Claude Code — 자동 웹 리서치 기반*
