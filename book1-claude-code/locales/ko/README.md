# Harness Engineering: Claude Code 설계 가이드

![표지: Harness Engineering — Claude Code 설계 가이드](assets/cover-wxb-en.svg)

부제: 소스 수준 런타임 설계에서 추출한, 통제 가능한 AI 코딩 시스템을 위한 공학 원칙

> 이 책은 모델이 코드를 작성할 수 있는지를 묻지 않습니다. 코드를 작성하는 모델이 터미널, 저장소, 팀 워크플로(workflow)에 연결된 뒤에도 공학 시스템을 잘못된 방향으로 끌고 가지 않게 하려면 어떻게 해야 하는지를 묻습니다.

이 책은 소스 코드 주석을 짜깁기한 것도, 기능 둘러보기도 아닙니다. Claude Code가 불안정한 모델을 어떻게 지속 가능한 공학 질서로 수렴시키는지에 초점을 맞춥니다. 제어 평면(control plane), 메인 루프(main loop), 도구 권한(tool permission), 컨텍스트 거버넌스(context governance), 복구 경로(recovery path), 멀티 에이전트(multi-agent) 검증, 그리고 팀 실천이 하나의 일관된 뼈대를 이룹니다.

이 책은 세 가지 독서 전제에서 출발합니다.

- 무게 중심은 모델의 능력이 아니라, 하네스(harness)가 제약과 실행을 어떻게 조직하는가에 있습니다
- 목표는 함수를 한 줄씩 설명하는 것이 아니라, 런타임이 왜 이렇게 성장할 수밖에 없었는가입니다
- 가치는 개인의 기교 모음이 아니라, 구조를 재사용 가능한 팀 실천으로 바꾸는 데 있습니다

권장 읽기 순서:

1. [서문: 하네스(harness), 터미널, 그리고 엔지니어링 제약](preface.md)
2. [1장 왜 하네스 엔지니어링(harness engineering)이 필요한가](chapter-01-why-harness-engineering.md)
3. [2장 프롬프트(prompt)는 인격이 아니라 제어 평면(control plane)입니다](chapter-02-prompt-is-control-plane.md)
4. [3장 질의 루프(query loop): 에이전트 시스템의 심장박동](chapter-03-query-loop-heartbeat.md)
5. [4장 도구, 권한과 인터럽트: 왜 에이전트는 세계를 직접 만지면 안 되는가](chapter-04-tools-permissions-interrupts.md)
6. [5장 컨텍스트 거버넌스: 메모리, CLAUDE.md 및 압축은 예산 제도입니다](chapter-05-context-memory-compact.md)
7. [6장 오류와 복구: 오류 발생 후에도 계속해서 작동하는 에이전트 시스템](chapter-06-errors-and-recovery.md)
8. [7장 멀티 에이전트와 검증: 분업과 검증으로 불안정성 관리하기](chapter-07-multi-agent-and-verification.md)
9. [8장 팀 도입: 똑똑한 도구를 지속 가능한 워크플로로 만들기](chapter-08-team-landing-practices.md)
10. [9장 하네스 엔지니어링(harness engineering) 10대 원칙](chapter-09-ten-principles.md)
11. [부록 A 체크리스트: 원칙을 실행 가능한 제약으로 만들기](appendix-a-checklists.md)
12. [부록 B 도표: 런타임 뼈대 그려보기](appendix-b-diagram-notes.md)
13. [부록 C 소스 코드 지도: 본서 각 장의 주요 근거 파일](appendix-c-source-map.md)

통합된 결론부터 먼저 보고 싶다면 [9장](chapter-09-ten-principles.md)으로 바로 가십시오.
