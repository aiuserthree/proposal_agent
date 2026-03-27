---
name: start-proposal
displayName: "Start Proposal"
description: "RFP 분석부터 최종 제안서까지 전체 자동 실행"
---
# /start-proposal

## PRE-CHECK
### CHECK 1: RFP 확인
1. workspace/rfp/ 파일 확인
2. 없으면 채팅 이전 메시지에서 탐색
3. 둘 다 없으면 등록 안내 후 멈춤:
⚠️ RFP가 없습니다. workspace/rfp/에 파일을 넣거나 채팅에 직접 입력 후 /start-proposal 재실행.

### CHECK 2: 레퍼런스 확인
- 샘플 있음 → 정상 진행
- 없음 → 디폴트 템플릿 기반 진행 (멈추지 않음)

### CHECK 2b: 참고 제안서(선택)
- `workspace/references/*.md` 또는 `*.txt`가 있으면 목차·절 구조에 **반영**한다(PPT/PDF는 텍스트 추출본 필요, `input-flexibility` §17).

### CHECK 3: workspace 폴더 없으면 자동 생성

### CHECK 4: MCP 비정상 시 web_search 대체 (멈추지 않음)

## 자동 실행 (중단 없이)
STEP 1: RFP 분석 → rfp-analysis.md
STEP 2: 레퍼런스 매칭 (샘플 있을때만)
STEP 3: 전략 수립 → strategist-전략-{날짜}.md
STEP 4: 환경 분석 → analyst-환경분석-{날짜}.md — **벤치마킹은 Cursor `research-agent` 플러그인 필수**(`rules/benchmarking-research-agent.mdc`): `run-benchmark` 또는 multi-search→site-scrape→screenshot(+traffic 등), **3~5 상세·URL·비교표**, PART2 **5p+·벤치 단독 3p+**, `competitor-analysis` 스킬(research-agent 절차 포함)
STEP 5: 기획 설계 → planner-기획-{날짜}.md
STEP 6: 디자인 전략 → designer-디자인-{날짜}.md
STEP 7: 기술 설계 → developer-기술-{날짜}.md
STEP 8: 마케팅 (D/E만) → marketer-마케팅-{날짜}.md
STEP 9: 수행 계획 → pm-agent-수행계획-{날짜}.md
STEP 10: 교차 검토 → critic-review-{날짜}.md
STEP 11: MUST 자동 수정 + 재검토 (최대 3회)
STEP 12: 합의 도출 → consensus-{날짜}.md
STEP 13: 최종 조립 → proposal-{고객사}-{날짜}.md (**최소 50p·PART4 구축·실행 10p+·그 외 PART 5p+**, 부족 시 보강 후 재조립)
STEP 14: 완료 보고

## 규칙
- RFP 없으면 멈추고 등록 안내
- 레퍼런스/MCP 없어도 대체 수단으로 자동 진행
- 각 STEP: ⏳ 진행중... / ✅ 완료
- 중간 사용자 입력 요청 금지
- 오류 시 건너뛰고 최종 보고에 누락 명시
