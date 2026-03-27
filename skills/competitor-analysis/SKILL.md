---
name: competitor-analysis
description: 경쟁사 벤치마킹 (MCP)
---
# competitor-analysis

## 1. 목적과 컨텍스트

동종·동경쟁 서비스 **3~5개**를 선정해 기능·UX·콘텐츠를 비교한다. `analyst`의 PART 2 핵심 입력이며, 출처 URL·스크린샷 경로를 필수로 남긴다.

**research-agent 필수**: 본 스킬은 Cursor에 설치된 **research-agent** 플러그인 절차를 따른다. `proposal-factory/rules/benchmarking-research-agent.mdc` 및 research-agent의 **`run-benchmark`**, **`multi-search`**, **`site-scrape`**, **`screenshot-capture`**, (선택) **`traffic-verify`**, **`branding-extract`** 스킬과 **`exclusion-criteria`**, **`search-principles`** 룰을 실행·준수한 뒤, 그 결과를 `workspace/drafts/competitor-*.md` 형식으로 정리한다. 전체 파이프라인은 research-agent **`/run-benchmark`**(또는 **`/start`**)로 RFP를 넣어 돌린 뒤 산출물을 인용해도 된다.

**분량(필수)**: `writing-style` **1.1b·1.1c**에 따라 PART 2 중 **벤치마킹·비교만 최소 3페이지 분량**(인쇄 기준 환산)을 채운다. 최종 제안서 전체는 **50p+**, PART 2는 **5p+**가 되도록 본 스킬 산출이 **충분한 표·사이트별 소절**을 포함한다.

## 2. 입력 명세

| 구분 | 항목 | 필수 |
|------|------|------|
| 필수 | 산업·서비스 범위 | 예 |
| 선택 | 후보 URL 목록 | 아니오 |
| 선택 | `workspace/references/*.md` (참고 제안서에서 추출한 목차·키워드) | 권장 |

## 3. 출력 명세

| 항목 | 내용 |
|------|------|
| 경로 | `workspace/drafts/competitor-{YYYY-MM-DD}.md`, `drafts/screenshots/{사이트명}/` |
| 형식 | 비교 표 + 사이트별 반페이지 요약 |

## 4. 단계별 실행 절차 (research-agent 정렬)

1. **`search-principles`**·**`exclusion-criteria`** 를 연다. 후보 탐색은 research-agent **`multi-search`** 절차(한·영 병렬 등)를 따른다.
2. 후보 URL마다 **`site-scrape`** 으로 구조·기능·제외 여부를 검증한다.
3. **`screenshot-capture`** 로 데스크톱/모바일 캡처 경로를 남긴다(Firecrawl 실패 시 Playwright 폴백은 research-agent 스킬과 동일).
4. (권장) **`traffic-verify`** 로 규모 검증; Inspire·비주얼 분석 시 **`branding-extract`**.
5. 비교 항목(IA, 기능, 콘텐츠, 비주얼)을 표준화하고 장단점·시사점을 도출한다.
6. analyst 보고서 형식으로 요약하고, research-agent **`run-benchmark`** 전체를 돌렸다면 `output/reports/` 등 **산출 경로**를 메타에 기록한다.

**단축 경로**: 동일 RFP로 research-agent **`/run-benchmark`** 를 먼저 실행한 뒤, 리포트·스크린샷을 본 스킬 출력 템플릿에 맞게 압축한다.

## 5. 품질 기준

1. 최소 **3개**, 최대 **5개** 사이트.
2. 각 사이트 **출처 URL** 필수.
3. 표 **2개 이상**(비교 매트릭스 + 갭/시사점 또는 기능×사이트 표).
4. 사이트별 **최소 3~6문단**(또는 소제목+표)으로 **반페이지 이상** 분량 확보.
5. writing-style 금지 표현 사용 안 함.
6. MCP 실패 시 한계를 명시하고 **web_search**로 공개 정보 보강.
7. 참고 제안서 md가 있으면 **비교 항목 목록**(목차에서)을 매트릭스 열로 반영.

## 6. 출력 템플릿

```markdown
# 경쟁사 벤치마킹
## 비교 대상
| 사이트 | URL | 선정 이유 |
## 비교 매트릭스
| 항목 | A | B | C |
## 시사점
```

## 7. 에러 처리 규칙

| 상황 | 처리 |
|------|------|
| 사이트 차단 | 공개 검색·캐시만으로 요약 |
| 후보 부족 | 간접 경쟁 포함 + 근거 |

## 8. 연계 스킬·에이전트

| 연계 대상 | 용도 |
|-----------|------|
| **research-agent** | `run-benchmark`, `multi-search`, `site-scrape`, `screenshot-capture`, `traffic-verify`, `branding-extract`; 에이전트 `context-builder`, `orchestrator`, `market-researcher`, `site-auditor` 등 |
| proposal-factory 규칙 | `benchmarking-research-agent.mdc`, writing-style, proposal-structure, output-format |
| Orchestrator | 단계 산출물 승인·재작성 루프 |
| Critic | 일관성·RFP 대응 재검토 |

## 9. 관련 규칙 파일

- `rules/writing-style.mdc` — 분량·톤·금지어
- `rules/proposal-structure.mdc` — PART 배치
- `rules/collaboration-protocol.mdc` — 저장 경로·합의
- `rules/output-format.mdc` — Markdown·Mermaid

## 10. 품질 자가점검 체크리스트

- [ ] 입력 명세의 필수 항목이 모두 충족되었는가?
- [ ] 출력 경로·파일명이 collaboration-protocol과 일치하는가?
- [ ] 표·절 번호가 최종 제안서에서 참조 가능한가?
- [ ] 금지 표현(writing-style)이 제거되었는가?
- [ ] 에러/예외 시나리오가 문서화되었는가?

## 11. 산출물 보존·재실행

- 동일 날짜 재실행 시 파일명에 `_v2` 또는 시각 접미를 붙인다.
- 중간 산출물은 삭제하지 않고 보관하여 critic 재검토에 대비한다.
- MCP 실패 시 대체 경로(web_search 등)를 보고서에 명시한다.

## 12. 용어·메타데이터

- 문서 상단에 `generated_for`, `rfp_ref`, `skill_version: 1` 메타를 주석으로 남길 수 있다.
- 고객사 고유명사는 RFP 표기를 그대로 사용한다.


## 13. 상세 실행 노트 (공통)

1. 스킬 실행 전 `workspace/discussions/rfp-analysis.md` 존재 여부를 확인한다.
2. 산출물은 UTF-8(LF)로 저장하고, 표·코드블록 들여쓰기를 유지한다.
3. 수치·날짜는 writing-style의 숫자 표기 규칙을 따른다.
4. 본 스킬 산출물을 인용하는 최종 PART는 proposal-structure의 해당 절을 명시한다.
5. 재현성을 위해 사용한 검색어·URL·도구명을 부록 또는 각주에 남긴다.

## 14. 한계 및 면책

- 공개되지 않은 정보는 추론·가정으로 표시하며, 계약·법적 효력이 있는 수치는 발주처 확인을 전제로 한다.
- MCP·외부 API 장애 시 결과 파일 상단에 장애 요약을 기록한다.

## 15. 승인·게이트
- 본 산출물은 해당 담당 에이전트 초안으로 간주하며, critic 통과 후 최종본에 편입한다.
- MUST 이슈가 남아 있으면 동일 스킬 재실행 또는 연계 스킬 보완을 명시한다.

<!-- skill_doc_end -->
