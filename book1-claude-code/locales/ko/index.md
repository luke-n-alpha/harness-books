# 도입

![표지: Harness Engineering: Claude Code 설계 가이드](assets/cover-wxb.svg)

> 이 책은 "모델이 코드를 짤 수 있는가"에 대해 고민하지 않습니다. 코드를 작성하는 모델이 터미널, 저장소(repository), 팀의 워크플로우에 도입된 이후, 어떻게 시스템을 잘못된 방향으로 이끌지 않게 할 것인가를 다룹니다.

이 책은 소스 코드 주석을 모아둔 것도, 제품 기능을 소개하는 글도 아닙니다. 이 책은 Claude Code가 어떻게 불안정한 모델을 지속 가능한 엔지니어링 질서 속으로 수렴시키고, 제어 평면(control plane), 질의 루프(query loop), 도구(tool) 권한, 컨텍스트 거버넌스(context governance), 복구 경로(recovery path), 멀티 에이전트(multi-agent) 검증(verification), 팀 제도를 하나의 완전한 골격으로 구성하는지에 집중합니다.

이 책을 읽기 위한 세 가지 전제가 있습니다:

- 핵심은 모델의 능력이 아니라 하네스(harness)가 제약과 실행을 어떻게 조직하는지에 있습니다.
- 핵심은 함수를 한 줄씩 설명하는 것이 아니라, 왜 런타임(runtime) 구조가 반드시 이러한 형태로 나타나야 하는지에 있습니다.
- 핵심은 개인의 기술이 아니라, 이러한 구조를 어떻게 팀이 재사용 가능한 제도(institution)로 변환할 것인지에 있습니다.

권장 독서 순서:

1. [서문 하네스, 터미널, 엔지니어링 제약](preface.md)
2. [1장 하네스 엔지니어링이 필요한 이유](chapter-01-why-harness-engineering.md)
3. [2장 프롬프트는 인격이 아니라 제어 평면입니다](chapter-02-prompt-is-control-plane.md)
4. [3장 질의 루프: 에이전트 시스템의 심장박동](chapter-03-query-loop-heartbeat.md)
5. [4장 도구, 권한, 인터럽트: 왜 에이전트가 세계를 직접 건드리면 안 되는가](chapter-04-tools-permissions-interrupts.md)
6. [5장 컨텍스트 거버넌스: 메모리, CLAUDE.md, 압축은 예산 제도입니다](chapter-05-context-memory-compact.md)
7. [6장 오류와 복구: 오류 발생 후에도 계속 작동할 수 있는 에이전트 시스템](chapter-06-errors-and-recovery.md)
8. [7장 멀티 에이전트와 검증: 분업과 검증으로 불안정성 관리하기](chapter-07-multi-agent-and-verification.md)
9. [8장 팀 도입: 스마트 도구를 재사용 가능한 제도로 만들기](chapter-08-team-landing-practices.md)
10. [9장 하네스 엔지니어링 10가지 원칙](chapter-09-ten-principles.md)
11. [부록 A 체크리스트: 원칙을 실행 가능한 제약으로 만들기](appendix-a-checklists.md)
12. [부록 B 도식: 런타임 골격 그려보기](appendix-b-diagram-notes.md)
13. [부록 C 소스 코드 지도: 본서 각 장의 주요 근거 파일](appendix-c-source-map.md)

전체적인 판단을 먼저 확인하고 싶다면 [9장](chapter-09-ten-principles.md)으로 바로 이동해도 좋습니다.
