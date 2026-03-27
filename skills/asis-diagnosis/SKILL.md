---
name: asis-diagnosis
description: AS-IS 현황 진단 (MCP)
---
# asis-diagnosis

## 1. 목적과 컨텍스트

**현재 서비스·사이트**의 정보 구조, 콘텐츠, 성능·접근성 이슈를 진단한다. Firecrawl/Playwright MCP가 있으면 크롤링·스크린샷을, 없으면 `web_search`·문서 기반으로 대체한다.

## 2. 입력 명세

| 구분 | 항목 | 필수 |
|------|------|------|
| 필수 | AS-IS URL 또는 시스템 설명 | 예 |
| 선택 | 모바일/데스크톱 뷰 | 아니오 |

## 3. 출력 명세

| 항목 | 내용 |
|------|------|
| 경로 | `workspace/drafts/asis-{YYYY-MM-DD}.md`, 스크린샷 `workspace/drafts/screenshots/` |
| 형식 | 갭 분석 표 + 스크린샷 링크 + 개선 방향 |

## 4. 단계별 실행 절차 (6단계)

1. URL 접속 또는 문서에서 기능 목록을 파악한다.
2. IA·주요 화면을 캡처한다.
3. 문제점(UX·기술·콘텐츠)을 분류한다.
4. 우선순위(P0/P1)를 부여한다.
5. TO-BE와의 갭을 표로 정리한다.
6. analyst 본문에 인용 가능한 요약을 만든다.

## 5. 품질 기준

1. 스크린샷·경로 또는 **출처** 명시.
2. 추론 시 **reference-matcher**와 유사 근거 병기.
3. 개인정보·민감 화면은 마스킹.
4. 최소 3개 이상 이슈 또는 "이슈 없음" 근거.
5. RFP AS-IS 요구와 항목 정렬.

## 6. 출력 템플릿

```markdown
# AS-IS 진단
## 대상
## 화면·구조
## 이슈 목록
| ID | 영역 | 현상 | 영향 | 우선순위 |
## 갭(TO-BE 대비)
```

## 7. 에러 처리 규칙

| 상황 | 처리 |
|------|------|
| URL 없음 | 유사 사례 + 전제 명시 |
| MCP 실패 | 공개 자료·스크린샷 생략 + 한계 명시 |

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
