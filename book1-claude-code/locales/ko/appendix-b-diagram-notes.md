# 부록 B 도표: 런타임 뼈대 그려보기

앞선 장들에서는 런타임 구조를 글로 설명했습니다. 글로도 충분히 설명할 수 있지만, 어떤 것들은 그림으로 나타내면 독자들이 훨씬 빠르게 깨닫게 됩니다. Claude Code는 단순히 "프롬프트 뭉치에 도구 몇 개를 더한 것"이 아니라, 매우 명확한 상태 머신(state machine) 시스템이라는 사실 말입니다.

## B.1 도표 1: Claude Code 전체 제어 평면

![Claude Code 전체 제어 평면](diagrams/diag-01-claude-code-control-plane.png)

이 그림을 "사용자 -> 모델 -> 도구 -> 출력"과 같은 아동용 그림책 수준의 순서도로 그려서는 안 됩니다. 그런 방식은 시스템의 진짜 핵심 기관들을 숨겨버리기 때문입니다. 더 합리적인 이해 방식은 Claude Code를 다음 다섯 계층으로 나누는 것입니다.

1. 사용자 상호작용 계층(user interaction layer)
2. 제어 평면 계층(control plane layer)
3. 실행 루프 계층(execution loop layer)
4. 외부 능력 계층(external capability layer)
5. 영속성 및 관측 계층(persistence and observability layer)

이 도표의 핵심은 모든 모듈을 나열하는 것이 아니라, 다음 사항들을 강조합니다.

- 모델은 최상위 계층에도, 최하위 계층에도 없습니다.
- 모델은 질의 루프(query loop) 내의 한 단계일 뿐입니다.
- 시스템을 하나로 묶어주는 진짜 주체는 제어 평면과 복구 평면(recovery plane)입니다.

## B.2 도표 2: 질의 루프 주 순환 및 복구 분기

![질의 루프 주 순환](diagrams/diag-b02-01-query-loop-main.png)

![질의 루프 복구 분기](diagrams/diag-b02-02-query-loop-recovery-branches.png)

## B.3 도표 3: 도구 배치 순서와 StreamingToolExecutor

![도구 배치 순서](diagrams/diag-b03-01-tool-batch-ordering.png)

![StreamingToolExecutor 생명주기](diagrams/diag-b03-02-streaming-tool-executor.png)

## B.4 도표 4: 컨텍스트 소스와 압축 재구축

![컨텍스트 소스와 예산](diagrams/diag-b04-01-context-sources-and-budget.png)

![압축 재구축 파이프라인](diagrams/diag-b04-02-compact-rebuild-pipeline.png)

## B.5 도표 5: 코디네이터-워커 흐름과 검증 분리

![코디네이터와 워커 흐름](diagrams/diag-b05-01-coordinator-worker-flow.png)

![검증 분리](diagrams/diag-b05-02-verification-separation.png)

## B.6 도표 6: 팀 거버넌스 맵

![팀 거버넌스 맵](diagrams/diag-06-team-governance-map.png)
