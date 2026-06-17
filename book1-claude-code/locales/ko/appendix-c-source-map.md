# 부록 C 소스 코드 지도: 본서 각 장의 주요 근거 파일

이 책은 소스 코드 가이드북은 아니지만, 근본적으로 소스 코드를 바탕으로 작성되었습니다. 이 부록에서는 각 장의 내용을 뒷받침하는 가장 핵심적인 파일들을 지도로 구성했습니다.

이 지도는 전체 색인이 아니며, 본서의 논점과 직접적으로 관련된 주요 파일들만을 나열합니다.

저작권 경계에 대해 한마디 덧붙입니다. 이 소스 코드 지도의 역할은 분석 근거가 어떤 파일에서 비롯되었는지를 밝히는 것이지, 내용과 함께 이 파일들의 원문 내용을 제공하겠다고 약속하는 것이 아닙니다. 여기에는 필요한 공학적 참조, 모듈 위치 및 구조 분석을 위한 정보만 남겼으며, 소스 코드 사본을 첨부하거나 구현 코드를 길게 전재하지 않습니다.

## C.1 1장 왜 하네스 엔지니어링(harness engineering)이 필요한가

핵심 파일:

- `src/constants/prompts.ts`
- `src/utils/systemPrompt.ts`
- `src/query.ts`
- `src/services/tools/toolOrchestration.ts`
- `src/tools/BashTool/prompt.ts`

본 장의 주요 논점 근거:

- 프롬프트(prompt)는 인격 포장이 아니라 제어 평면(control plane) 구성 요소입니다
- 질의 루프(query loop)야말로 에이전트 시스템의 뼈대입니다
- 도구와 Bash의 위험성에 대한 설명이 하네스(harness)의 필요성을 입증합니다

## C.2 2장 프롬프트는 제어 평면이며, 인격 꾸미기가 아닙니다

핵심 파일:

- `src/constants/prompts.ts`
- `src/utils/systemPrompt.ts`
- `src/utils/claudemd.ts`
- `src/memdir/memdir.ts`
- `src/constants/systemPromptSections.ts`
- `src/main.tsx`

본 장의 주요 논점 근거:

- 시스템 프롬프트의 계층적 조립
- `CLAUDE.md`와 메모리(memory)를 제어 평면 입력으로 활용합니다
- 동적 시스템 알림과 컨텍스트(context) 주입

## C.3 3장 질의 루프: 에이전트 시스템의 심장박동

핵심 파일:

- `src/query.ts`
- `src/QueryEngine.ts`

본 장의 주요 논점 근거:

- 질의 루프의 상태 기계(state machine)적 특성
- 모델 호출 이전에 수행되는 입력 거버넌스(governance)
- 스트리밍 이벤트 소비와 복구(recovery) 분기
- 대화 수명 주기(conversation lifecycle)에 대한 QueryEngine의 소유권

## C.4 4장 도구, 권한과 인터럽트

핵심 파일:

- `src/services/tools/toolOrchestration.ts`
- `src/services/tools/toolExecution.ts`
- `src/services/tools/StreamingToolExecutor.ts`
- `src/hooks/useCanUseTool.tsx`
- `src/utils/permissions/PermissionResult.ts`
- `src/tools/BashTool/prompt.ts`
- `src/tools/BashTool/bashPermissions.ts`

본 장의 주요 논점 근거:

- 동시성 안전과 컨텍스트 순차 재생(ordered context replay)
- 도구 실행 래퍼(wrapped tool execution) 스택
- `allow / deny / ask` 권한 의미론(authorization semantics)
- 스트리밍 도구 인터럽트(interrupt)와 합성 종료(synthetic closure)
- Bash에 대한 특수한 고압 거버넌스

## C.5 5장 컨텍스트 거버넌스: 메모리, CLAUDE.md와 압축

핵심 파일:

- `src/utils/claudemd.ts`
- `src/memdir/memdir.ts`
- `src/services/SessionMemory/prompts.ts`
- `src/services/compact/autoCompact.ts`
- `src/services/compact/compact.ts`
- `src/query.ts`

본 장의 주요 논점 근거:

- `CLAUDE.md`의 계층적 발견과 로딩
- `MEMORY.md`는 본문 저장소가 아닌 진입 색인(entry index)으로 활용합니다
- 세션 메모리의 구조적 연속성
- 자동 압축(autocompact) 임계값, 버퍼와 서킷 브레이커(circuit breaker)
- 압축 후 작업 의미론의 재구축

## C.6 6장 오류와 복구

핵심 파일:

- `src/query.ts`
- `src/services/compact/autoCompact.ts`
- `src/services/compact/compact.ts`
- `src/services/api/withRetry.ts`

본 장의 주요 논점 근거:

- 보류 가능한 복구 가능 오류(withheld recoverable errors)
- 프롬프트 초과(prompt-too-long) 시 붕괴 처리(collapse drain)와 반응형 압축
- `max_output_tokens`의 확대(escalation)와 계속 전략(continuation strategy)
- 자동 압축 실패 시 서킷 브레이커 작동
- 압축 과정 자체의 PTL 하에서의 복구(self-recovery under PTL)

## C.7 7장 멀티 에이전트와 검증

핵심 파일:

- `src/utils/forkedAgent.ts`
- `src/coordinator/coordinatorMode.ts`
- `src/tasks/LocalAgentTask/LocalAgentTask.tsx`
- `src/utils/hooks/hooksConfigManager.ts`
- `src/skills/bundled/verify.ts`
- `src/memdir/memoryTypes.ts`

본 장의 주요 논점 근거:

- 포크된 에이전트(forked agent)의 캐시 안전 파라미터와 상태 격리(state isolation)
- 코디네이터(coordinator)의 합성(synthesis) 책임
- 검증(verification)의 독립적 단계화
- 서브에이전트(subagent) 수명 주기 훅(lifecycle hook)
- 작업 정리와 부모-자식 간 중단(abort) 전파
- 오래된 메모리(stale memory)에 대한 검증 규율(verify discipline)

## C.8 8장 팀 도입

핵심 파일:

- `src/utils/claudemd.ts`
- `src/tools/SkillTool/prompt.ts`
- `src/tools/SkillTool/SkillTool.ts`
- `src/utils/forkedAgent.ts`
- `src/utils/hooks/hooksConfigManager.ts`
- `src/main.tsx`

본 장의 주요 논점 근거:

- 팀 `CLAUDE.md`의 계층적 안정성
- 스킬(skill)을 단순 프롬프트 모음이 아닌 제도적 파편(institutional slice)으로 정의합니다
- 승인(approval) 경계와 허용 규칙의 범위 지정
- 훅을 통한 수명 주기 거버넌스(lifecycle governance)
- 세션 시작 시 지침(instructions) 및 스킬 로딩 동작

## C.9 9장 열 가지 원칙

9장은 단일 파일에서 직접 도출된 것이 아닙니다. 앞선 모든 장을 압축한 내용입니다. 이 장의 근거는 전서에서 사용된 핵심 모듈들이 공동으로 보여주는 시스템 구조입니다:

- 프롬프트 조립(prompt assembly)
- 질의 루프
- 도구 조정(tool orchestration)
- 권한 모델(permission model)
- 컨텍스트 거버넌스
- 복구 시스템
- 멀티 에이전트 조정(multi-agent orchestration)
- 팀 거버넌스 훅
