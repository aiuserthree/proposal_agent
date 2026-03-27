---
name: proposal-assembler
description: 드래프트를 최종 제안서로 조립
---
# proposal-assembler

## 1. 목적과 컨텍스트

`workspace/drafts/`의 에이전트 산출물과 `consensus-*.md`·`critic-review-*.md` 결과를 통합하여 **단일 최종 제안서** Markdown을 생성한다. `proposal-structure` PART 순서와 `output-format` 규칙을 준수한다.

## 2. 입력 명세

| 구분 | 항목 | 필수 |
|------|------|------|
| 필수 | strategist / analyst / planner / designer / developer / pm-agent 산출물 경로 | 예 |
| 필수 | `rfp-analysis.md` | 예 |
| 선택 | marketer 산출물(유형 D/E) | 유형별 |
| 선택 | `consensus-{날짜}.md`, `critic-review-{날짜}.md` | 권장 |
| 선택 | 고객사 표기명·최종 날짜 | 예 |
| 선택 | `workspace/references/*.md` 또는 `@` **참고 제안서 MD** | 패턴 참고 시 |

## 3. 출력 명세

| 항목 | 내용 |
|------|------|
| 경로 | `workspace/final/proposal-{고객사약칭}-{YYYY-MM-DD}.md` |
| 형식 | Markdown, `#` 제목 1회, `##` PART, Mermaid·표 포함 |
| 부가 | 목차, 부록(RFP 매핑), THANK YOU |

## 4. 단계별 실행 절차 (10단계)

1. **수집**: drafts·discussions에서 최신 날짜 파일을 확정한다.
2. **레퍼런스 MD**: `workspace/references/` 또는 사용자 `@`로 제공된 **참고 제안 MD**(KB·F&Co·JAJU 등)가 있으면 목차·절 이름만 스캔하고, **프롤로그·AS-IS 다각도·부록 분리** 필요 여부를 메타에 표시한다(본문 복제 금지).
3. **목차 골격**: proposal-structure PART 1~8 + (선택) 프롤로그 + 부록(APPENDIX) 헤딩을 생성한다.
4. **본문 병합**: 에이전트별 담당 PART를 순서대로 이어붙인다(중복 제목 정리).
5. **용어 통일**: consistency-validator 결과 또는 수동으로 용어·수치를 맞춘다.
6. **시각 요소**: 표·Mermaid 블록이 깨지지 않았는지 검증한다.
7. **매핑 부록**: rfp-compliance-checker 산출 또는 표를 부록에 삽입한다. 시장 통계·긴 표는 **부록 A** 본문, **부록 B** 레퍼런스 출처로 분리 가능(writing-style §15).
8. **발표 Notes**: 사용자·RFP가 PT 제출이면 PART별 하단에 `> **Notes:**` 선택 삽입(writing-style §16).
9. **메타**: 표지에 사업명·제출일·아이뱅크 표기(ibank-identity).
10. **저장**: final 경로에 쓰고 경로를 orchestrator에 반환한다.

## 5. 품질 기준

1. PART 순서와 proposal-structure 일치.
2. 동일 사실의 수치·기간·인원이 본문 전체에서 일관.
3. REQ ID 참조가 부록과 모순 없음.
4. 최소 분량(writing-style **50p**, PART **1~3·5~8: 5p**, **PART4 구축·실행: 10p+**, PART2 벤치마킹 **3p+**) 충족 또는 부족 시 보강 플래그.
5. 이미지 상대 경로가 최종 폴더 기준으로 유효.

## 6. 출력 템플릿 (머리부)

```markdown
# [사업명] 제안서
**발주처**:  | **제출일**:  | **제안사**: 아이뱅크

## 목차
...

## PART 1. 사업 이해 및 제안 개요
...

---

## 부록 A. RFP 요구사항 추적표
...

## THANK YOU
...
```

## 7. 에러 처리 규칙

| 상황 | 처리 |
|------|------|
| 특정 PART 파일 누락 | placeholder에 "추가 필요" 및 orchestrator 알림 |
| Mermaid 렌더 오류 | 노드 ID 영문화·분할 후 재삽입 |
| 중복 헤딩 | `###` 레벨 조정으로 계층 정리 |

## 8. 연계 스킬·에이전트

| 연계 대상 | 용도 |
|-----------|------|
| proposal-factory 규칙 | writing-style, proposal-structure, output-format 준수 |
| Orchestrator | 단계 산출물 승인·재작성 루프 |
| Critic | 일관성·RFP 대응 재검토 |

## 9. 관련 규칙 파일

- `rules/writing-style.mdc` — 분량·톤·금지어
- `rules/benchmarking-research-agent.mdc` — PART 2 벤치마킹 시 research-agent 연동
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

