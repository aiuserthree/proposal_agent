# Proposal Factory 사용 가이드

> 아이뱅크(ibank) 제안서 자동 생성 v1.0.0

---

## 1. 구성
| 구분 | 수량 |
|------|------|
| Rules | 8+ (`benchmarking-research-agent` 등) |
| Skills | 21 |
| Agents | 9 |
| Commands | 1 (/start-proposal) |
| MCP | 3 |

## 2. 사용법
1. workspace/rfp/에 RFP 배치 또는 채팅에 직접 입력
2. /start-proposal 실행
3. 자동으로 최종 제안서까지 생성
4. workspace/final/ 결과 확인

## 3. 워크플로우
PRE-CHECK → STEP 1~14 자동
Orchestrator → Strategist+Analyst → Planner+Designer+Developer+Marketer → PM-Agent → Critic → 수정 → 조립 → 완료

## 4. 벤치마킹과 research-agent

PART 2 벤치마킹 작성 시 **Cursor에 설치된 `research-agent`(ibank-marketplace)** 플러그인의 룰·스킬·에이전트를 **필수**로 연동한다. 제안서 쪽 규칙은 `rules/benchmarking-research-agent.mdc`를 본다. (`/run-benchmark` 또는 `multi-search`→`site-scrape`→`screenshot-capture` 등)

## 5. 에이전트
| 에이전트 | 역할 |
|----------|------|
| Orchestrator | 총괄 |
| Strategist | 전략 |
| Analyst | 분석/벤치마킹(research-agent 연동) |
| Planner | IA/기능 |
| Designer | 디자인 |
| Developer | 기술 |
| Marketer | 마케팅 |
| PM-Agent | 수행계획 |
| Critic | 검토 |

## 6. 입력 유형
| 레벨 | 입력 | 대응 |
|------|------|------|
| Level 1 | 정식 RFP | 완전 자동 |
| Level 2 | 이메일 | 자동+추론 |
| Level 3 | 메모 | 프레임+추론 |

## 7. FAQ
Q: RFP 없이? → 채팅에 직접 입력
Q: 레퍼런스 없이? → 디폴트 진행
Q: 결과? → Markdown, PPT/PDF 별도

---
v1.0.0 | 2026-03-27
