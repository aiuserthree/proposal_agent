---
name: design-strategy
description: 디자인 컨셉/가이드 수립
---
# design-strategy

## 1. 목적과 컨텍스트

디자인 에이전트·`designer` 산출과 연동되는 **컨셉·디자인 토큰·그리드·반응형·컴포넌트 원칙**을 한 문서로 정리한다. 시안 이미지가 아닌 **가이드**로서 제안서 PART 6에 삽입한다.

## 2. 입력 명세

| 구분 | 항목 | 필수 |
|------|------|------|
| 필수 | strategist 전략 키워드 3개 | 예 |
| 필수 | `brand-identity-*.md` 또는 RFP CI 요구 | 예 |
| 선택 | 벤치마킹 URL·스크린샷 | 권장 |

## 3. 출력 명세

| 항목 | 내용 |
|------|------|
| 경로 | `workspace/drafts/design-strategy-{YYYY-MM-DD}.md` 또는 designer 본문에 통합 |
| 형식 | Markdown + 컬러/타이포 표 + 레퍼런스 목록 |

## 4. 단계별 실행 절차 (6단계)

1. 키워드와 브랜드 분석을 연결해 **컨셉 한 문장**을 정한다.
2. 컬러 팔레트(Primary/Secondary/Neutral)를 HEX로 제안한다.
3. 타이포 스케일(제목·본문·캡션)을 정의한다.
4. 그리드·거터·최대 폭을 반응형 브레이크포인트와 함께 기술한다.
5. 주요 UI 컴포넌트(버튼·폼·카드·내비) 원칙을 bullet로 정한다.
6. 레퍼런스 URL 3개+와 선정 이유를 기록한다.

## 5. 품질 기준

1. WCAG 방향(AA 목표 등) 명시.
2. RFP 디자인 제약과 충돌 시 RFP 우선.
3. 레퍼런스가 **출처 URL** 포함.
4. writing-style 금지 표현 사용 안 함.
5. PART 6 시각요소 표(writing-style) 충족.

## 6. 출력 템플릿

```markdown
# 디자인 전략
## 컨셉
## 컬러
| 역할 | HEX | 용도 |
## 타이포
## 그리드·반응형
## 컴포넌트 원칙
## 레퍼런스
| 이름 | URL | 이유 |
```

## 7. 에러 처리 규칙

| 상황 | 처리 |
|------|------|
| 브랜드 색 미공개 | 중립 팔레트 + 확정 시 교체 문구 |
| 레퍼런스 접속 불가 | 정적 설명만으로 대체 |

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

