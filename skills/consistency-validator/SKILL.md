---
name: consistency-validator
description: 용어/수치/톤 일관성 검사
---
# consistency-validator

## 1. 목적과 컨텍스트

최종 조립 전 또는 후 **동일 개념의 상이 용어**, **섹션 간 수치 불일치**, **톤 편차**, **중복·모순**을 검출한다. `writing-style`·`rfp-compliance`와 정합한 수정 제안을 산출한다.

## 2. 입력 명세

| 구분 | 항목 | 필수 |
|------|------|------|
| 필수 | 검사 대상 Markdown(단일 파일 또는 drafts 폴더 목록) | 예 |
| 선택 | 마스터 수치 출처(rfp-analysis, pm-agent) | 권장 |
| 선택 | 금지어 목록(writing-style 기반) | 아니오 |

## 3. 출력 명세

| 항목 | 내용 |
|------|------|
| 경로 | `workspace/discussions/consistency-report-{YYYY-MM-DD}.md` |
| 형식 | 문제 목록(심각도 MUST/SHOULD), 위치, 수정 제안 |

## 4. 단계별 실행 절차 (6단계)

1. **용어 스캔**: CMS, 회원, 관리자 등 핵심 명사의 이형태를 수집한다.
2. **수치 스캔**: 기간, 인원, 예산, KPI 수치를 추출해 표로 비교한다.
3. **톤 스캔**: 금지 표현·과장어 검출.
4. **중복**: 동일 단락이 PART 간 반복되는지 확인.
5. **요약**: MUST/SHOULD로 분류하고 수정 우선순위를 부여한다.
6. **저장**: consistency-report에 기록한다.

## 5. 품질 기준

1. MUST 항목은 **위치(파일·절)**까지 특정.
2. 수정 제안은 **한 문장**으로 제시 가능.
3. false positive는 "참고"로 분리.
4. 마스터와 불일치 시 마스터 출처를 명시.
5. 검사 범위가 너무 넓으면 PART 단위로 분할 실행.

## 6. 출력 템플릿

```markdown
# 일관성 검사 보고서
## MUST
| ID | 유형 | 위치 | 내용 | 제안 |

## SHOULD
```

## 7. 에러 처리 규칙

| 상황 | 처리 |
|------|------|
| 파일 파싱 실패 | 수동 절 목록으로 부분 검사 |
| 수치 단위 혼용 | 통일 규칙(writing-style) 제안 |

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

## 15. 승인·게이트
- 본 산출물은 해당 담당 에이전트 초안으로 간주하며, critic 통과 후 최종본에 편입한다.
- MUST 이슈가 남아 있으면 동일 스킬 재실행 또는 연계 스킬 보완을 명시한다.

<!-- skill_doc_end -->
