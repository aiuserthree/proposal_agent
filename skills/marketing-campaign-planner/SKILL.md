---
name: marketing-campaign-planner
description: 캠페인/SNS 전략 기획
---
# marketing-campaign-planner

## 1. 목적과 컨텍스트

유형 **D/E**에서 **디지털 마케팅·캠페인·SNS**를 제안한다. `strategist`의 KPI·`marketer` 본문과 정합하며, 정량 KPI와 운영 리듬을 명시한다.

## 2. 입력 명세

| 구분 | 항목 | 필수 |
|------|------|------|
| 필수 | 마케팅 목표·예산감(또는 규모) | 예 |
| 필수 | 타겟·채널 제약 | 예 |
| 선택 | 캠페인 기간·시즌 | 아니오 |

## 3. 출력 명세

| 항목 | 내용 |
|------|------|
| 경로 | `workspace/drafts/marketing-campaign-{YYYY-MM-DD}.md` |
| 형식 | 페르소나 + 채널 + 캘린더 + 미디어믹스 + KPI 표 |

## 4. 단계별 실행 절차 (7단계)

**IMC·캠페인형**(레퍼런스: JAJU 등)일 때 출력 순서를 **Task → Analysis → Direction → 채널·캘린더 → 운영**으로 맞춘다(`marketer` 에이전트와 동일).

1. **목표**: 인지·전환·리텐션 중 우선순위를 정한다.
2. **페르소나**: 메시지·채널을 연결한다.
3. **채널**: Owned/Paid/Earned를 구분한다.
4. **캠페인**: 컨셉·크리에이티브 방향·랜딩을 정의한다.
5. **캘린더**: 주차별 콘텐츠·이벤트를 배치한다.
6. **KPI**: 노출·클릭·전환 등 측정 지표와 목표치를 적는다.
7. **운영**: 리포트 주기·A/B·크리시스 대응을 적는다.

## 5. 품질 기준

1. KPI가 **측정 가능**해야 함.
2. 예산·인력이 pm-agent와 모순 없음.
3. RFP 마케팅 요구 100% 반영.
4. 표 2개 이상(캘린더·KPI).
5. writing-style 금지 표현 배제.

## 6. 출력 템플릿

```markdown
# 마케팅·캠페인
## TASK(과제·브랜딩 목표)
## Analysis(시장·타깃·경쟁)
## Direction(크리에이티브·미디어)
## 목표·KPI
## 페르소나
## 채널 전략
## 캠페인 컨셉
## 콘텐츠 캘린더
| 주차 | 채널 | 콘텐츠 | 목표 |
## 미디어믹스
## 운영·리포트
```

## 7. 에러 처리 규칙

| 상황 | 처리 |
|------|------|
| 예산 미제공 | 시나리오 A/B로 분기 |
| 채널 제한 | RFP 우선, 제약 표에 명시 |

## 8. 연계 스킬·에이전트

| 연계 대상 | 용도 |
|-----------|------|
| proposal-factory 규칙 | writing-style, proposal-structure, output-format 준수 |
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

