# 부록 A 체크리스트: 원칙을 실행 가능한 제약으로 만들기

앞선 장들에서는 원칙에 대해 다루었습니다. 원칙을 체크리스트로 만들지 못하면, 결국 듣기에는 좋지만 실행할 수 없는 판단들만 남게 됩니다. 이 부록의 임무는 말하기는 쉽지만 지키기는 어려운 판단들을 즉시 사용할 수 있는 몇 개의 리스트로 압축하는 것입니다.

이 리스트들이 시스템을 자동으로 더 좋게 만들어 준다는 보장은 없습니다. 이들은 단지 가장 흔하고 지루한 실수가 반복되는 것을 방지할 뿐입니다. 엔지니어링에서의 많은 발전은 단순히 영감에 의존하는 것이 아니라, 같은 실수를 줄여나가는 과정에서 이루어집니다.

## A.1 에이전트 런타임(agent runtime) 설계 체크리스트

AI 코딩 에이전트가 실제 엔지니어링 워크플로우에 진입하려면 최소한 다음 질문들에 명확히 답할 수 있어야 합니다.

- 매 회차 호출을 독립적인 문답으로 처리하는 것이 아니라, 명확한 질의 루프(query loop)가 존재하는가?
- 복구(recovery), 예산, 압축(compaction), 훅(hook), 턴(turn) 카운트 등의 정보를 명확히 기록하는 회차 간 상태 객체(cross-turn state object)가 있는가?
- 모델 출력을 단순한 최종 문안이 아니라 이벤트 스트림(event stream)으로 처리하는가?
- 인터럽트(interrupt) 발생 시 완료되지 않은 도구 결과(tool result)를 보충하여 실행 원장(execution ledger)을 닫힌 루프(closed loop)로 유지할 수 있는가?
- 완료, 실패, 복구, 계속과 같은 서로 다른 종료 의미론(stop semantics)을 구분하는가?
- 초장기 대화 시 용량 부족을 임기응변으로 때우는 것이 아니라, 긴 세션을 위한 컨텍스트 예산(context budget)을 설계했는가?

이 질문들 중 두세 개 이상 답할 수 없다면, 해당 시스템은 "데모는 할 줄 아는" 단계에 머물러 있을 가능성이 크며 "엔지니어링 프로세스를 운영할 수 있는" 단계와는 거리가 멉니다.

## A.2 프롬프트(prompt) 설계 체크리스트

시스템 프롬프트는 단순히 길기만 해서는 안 되며, 계층과 역할이 분명해야 합니다.

검토 시 최소한 다음을 확인합니다.

- 신원 기술, 행동 규칙, 도구 제약, 출력 규율이 별도로 조직되어 있는가?
- 프롬프트의 우선순위 출처(예: 기본, 프로젝트, 사용자 정의, 추가, 에이전트 전용 프롬프트)가 명확한가?
- 위험한 동작, 권한을 넘는 동작, 검증 규율을 암시하는 정도가 아니라 명확한 규칙으로 작성했는가?
- 프롬프트가 런타임(runtime)이 처리해야 할 책임을 대신 짊어지게 하지는 않았는가?
- 버그를 수정할 때마다 프롬프트에 문장을 덧붙이는 것이 아니라, 팀이 안정적으로 유지보수할 수 있는가?

매우 실용적인 판단 기준은 다음과 같습니다. 특정 프롬프트 섹션을 삭제했을 때 시스템 행동에 구조적인 변화가 생기는가? 그렇다면 그것은 진정한 제어 평면(control plane)입니다. 그렇지 않다면 단순한 장식일 가능성이 높습니다.

## A.3 도구(tool) 및 권한(permission) 설계 체크리스트

모델이 현실 세계를 접하게 하는 모든 시스템은 먼저 다음을 자문해야 합니다.

- 도구 호출이 모델에 의한 직접적인 노출이 아닌, 통합된 스케줄링을 거치는가?
- 동시성(concurrency)은 기본적으로 허용하는 것이 아니라 명시적으로 안전함이 증명되는가?
- `allow / deny / ask`와 같은 권한(permission) 의미론의 분기가 존재하는가?
- 고위험 도구를 일반 도구와 동일하게 취급하지 않고 특례로 관리하는가?
- 인터럽트(interrupt), 폴백(fallback), 형제 노드 실패(sibling failure)에 대해 명확한 마무리 의미론을 생성할 수 있는가?
- 도구 실행의 인과 관계 체인을 기록하여 공중에 뜬 `tool_use`가 나타나지 않게 하는가?

Bash와 ReadTool이 관리 방식에 있어 거의 차이가 없다면, 이는 보통 위험에 대한 이해가 충분하지 않다는 것을 의미합니다.

## A.4 컨텍스트 거버넌스(context governance) 체크리스트

모든 장기 세션 에이전트는 언젠가 컨텍스트 제한에 직면하게 됩니다. 일찍 관리할수록 비용이 적게 듭니다.

검토 시 최소한 다음을 확인합니다.

- 장기 규칙, 장기 기억(memory), 세션 연속성, 임시 대화가 계층화되어 있는가?
- 인덱스형 파일이 끊임없이 팽창하는 것을 방지하기 위해 명확한 입구 파일과 본문 파일의 구분이 있는가?
- 메모리, 세션 메모리, 스킬(skill) 첨부 파일에 대한 토큰(token) 예산이 설정되어 있는가?
- 윈도우가 가득 찬 후에야 수습하는 것이 아니라, 미리 압축(compaction) 출력 공간을 확보하고 있는가?
- 압축 후 계획, 스킬, 핵심 파일, 도구 상태와 같은 작업 의미론이 복구되는가?
- 압축 자체가 실패할 경우에 대비한 복구 전략이 준비되어 있는가?

컨텍스트 관리를 잘하는 시스템은 종종 다소 인색해 보입니다. 그 인색함은 보통 단점이 아니라 장점입니다.

## A.5 오류 복구(error recovery) 설계 체크리스트

오류 복구에서 가장 두려운 것은 설계 자체가 없거나, 무한 루프에 빠지도록 설계되는 것입니다.

최소한 다음을 확인합니다.

- 복구 가능한 오류는 사용자에게 즉시 노출되기 전에 먼저 복구 분기로 진입하는가?
- 복구 경로는 파괴성이 낮은 것에서 높은 것으로 계층화되어 있는가?
- 반응형 압축(reactive compact), 정지 훅(stop hooks), 재시도(retry)가 서로 엉키지 않도록 보호 장치가 있는가?
- `max_output_tokens` 이후에 요약(recap)보다 이어 쓰기가 우선시되는가?
- 자동 복구에 횟수 제한, 재시도 제한, 서킷 브레이커(circuit breaker)가 포함되어 있는가?
- 인터럽트(interrupt) 또한 의미 있는 마무리가 필요한 실패 상태로 간주되는가?

멈추지 않는 복구 시스템은 복구하지 않는 시스템만큼이나 위험합니다. 단지 더 부지런히 위험할 뿐입니다.

## A.6 멀티 에이전트(multi-agent) 설계 체크리스트

멀티 에이전트 설계의 핵심은 불확실성을 조직하는 것입니다. 검토 시 다음을 확인합니다.

- 포크(fork) 시 프롬프트 캐시(prompt cache) 공유와 캐시 안전(cache-safe) 매개변수의 일관성을 고려하는가?
- 서브에이전트(subagent)는 기본적으로 가변 상태(mutable state)가 격리되어 있는가?
- 연구(research), 구현(implementation), 검증(verification), 합성(synthesis) 역할이 명확히 구분되어 있는가?
- 코디네이터(coordinator)가 단순히 워커(worker)의 결과를 전달하는 것이 아니라 실제로 종합적인 이해를 담당하는가?
- 검증(verification)이 구현과 독립적인가?
- 에이전트 수명 주기(lifecycle)가 관측 가능하고, 중단 가능하며, 정리 가능한가?
- 부모 에이전트의 중단(abort)이 자식 에이전트에게 전파되어 고아 작업이 남지 않게 하는가?

어떤 시스템이 멀티 에이전트를 표방하지만 모든 에이전트가 비슷한 일을 하고 있고, 아무도 합성이나 검증을 책임지지 않는다면, 그것은 보통 혼란을 병렬 처리로 확장하고 있을 뿐입니다.

## A.7 팀 도입(team adoption) 체크리스트

팀에 에이전트를 도입할 때 가장 흔한 오판은 개인의 숙련도를 제도적 성숙도로 착각하는 것입니다.

도입 전 다음을 확인하는 것이 좋습니다.

- 계층화된 `CLAUDE.md`가 마련되어 있으며, 팀이 무엇을 작성하고 무엇을 작성하지 말아야 할지 알고 있는가?
- 스킬(skill)을 대량으로 만들기 전에 먼저 검증(verification) 정의가 표준화되어 있는가?
- 결과의 심각도와 환경 민감도에 따라 승인 정책(approval policy)의 경계가 나뉘어 있는가?
- 핵심 제도가 정적 문서에 몰려 있지 않고 적절한 훅(hook) 시점에 연결되어 있는가?
- 트랜스크립트(transcript), 작업 결과물, 훅 이벤트 등을 검토를 위한 증거로 유지하고 있는가?
- 오래된 메모리, 만료된 규칙, 효력을 잃은 스킬에 대한 유지보수 메커니즘이 있는가?

팀이 진정으로 에이전트 시스템을 감당할 수 있는 것은 보통 소수의 고수에게 의존하기 때문이 아니라, 일반 구성원들도 제도 안에서 이를 올바르게 운영할 수 있기 때문입니다.

## A.8 리뷰 문제 리스트

AI 코딩 에이전트 솔루션을 리뷰해야 한다면 다음 질문들을 직접 던져보십시오.

- 어떤 행동이 프롬프트에 의해 제약되고, 어떤 행동이 런타임(runtime)에 의해 강제되는가?
- 모델이 도구를 오용할 때 누가 막는가? 어느 계층에서 막는가?
- 컨텍스트는 언제 압축되며, 압축 후 작업 의미론을 어떻게 복구하는가?
- 프롬프트가 너무 긴 경우와 최대 출력 토큰(max output tokens)을 초과한 경우를 각각 어떻게 다르게 복구하는가?
- 인터럽트 후 트랜스크립트와 도구 결과 간의 일관성을 어떻게 유지하는가?
- 멀티 에이전트 흐름에서 누가 합성을 담당하고 누가 검증을 담당하는가?
- 실패 복구에 서킷 브레이커와 무한 루프 방지 장치가 있는가?
- 팀이 에이전트가 무엇을 했고 왜 그렇게 했는지 어떻게 감사(audit)하는가?

솔루션이 이 질문들에 대해 "나중에 추가할 수 있다"는 답변을 반복한다면, 아직 런타임 설계가 제대로 이루어지지 않았으며 단지 낙관적인 시나리오만 설계된 상태일 가능성이 높습니다.

## A.9 마지막 체크리스트

앞의 내용이 너무 길다면 최소한 다음 여섯 가지는 기억하십시오: 능력보다 권한을 먼저 설계하고, 자율성보다 롤백을 우선하며, 인도보다 검증을 앞세우고, 장기 대화보다 컨텍스트 예산을 먼저 잡으며, 멀티 에이전트보다 수명 주기를 우선하고, 팀의 숙련도를 기대하기 전에 제도를 먼저 갖추십시오. 이 여섯 가지를 갖춘다고 해서 당장 훌륭해지는 것은 아니지만, 이를 갖추지 못하면 시스템이 단지 아직 문제가 생기지 않았을 뿐일 확률이 높습니다.

## A.10 구현 씨앗 (의사코드 스텁)

앞선 장들의 뼈대를 즉시 복사하여 사용할 수 있는 출발점으로 압축했습니다. 상세 구현은 각 장을 참조하며, 여기에는 최소한의 핵심 구조만 남겼습니다.

### A.10.1 queryLoop (뼈대, 3장 참조)

```
state = { messages, toolUseContext, autoCompactTracking, turnCount, transition, ... }
while not done(state):
    govern_input(state)                 // memory / snip / collapse / autocompact
    events = stream_model(state)
    for e in events:
        if e.is(tool_use): schedule(e, state.toolUseContext)
        if e.is(api_error): return surface(e)
    if interrupted: drain_tools_with_synthetic_results(state); break
    state = advance(state, recover_if_needed(state))
assert state.turnCount monotonic ∧ every tool_use has tool_result
```

### A.10.2 permission decision (뼈대, 4장 참조)

```
decision = hasPermissionsToUseTool(tool, input, ctx)
match decision:
    allow: exec(tool, input)
    deny:  reject(reason)
    ask:   route_to(coordinator | worker | classifier | interactive)
assert decision ∈ {allow, deny, ask}        # 3중 값, 붕괴되지 않음
assert ask never auto-escalates to allow    # 비인가 권한 상승 불가
```

### A.10.3 forkAgent (뼈대, 7장 참조)

```
params = CacheSafeParams { systemPrompt, userContext, systemContext, toolUseContext, forkContextMessages }
ctx    = createSubagentContext(parent)       // mutable state isolated by default
hooks.fire(SubagentStart, { agent_id, agent_type })
defer hooks.fire(SubagentStop, { agent_transcript_path })
assert parent.abort ⇒ propagate(child.abort)
```

### A.10.4 recoverFromError (뼈대, 6장 참조)

```
on recoverable_error(e):
    if e.is(prompt_too_long):
        if stagedCollapse > 0: recoverFromOverflow()
        elif not hasAttemptedReactiveCompact: tryReactiveCompact()
        else: surface(e); skip_stop_hooks()
    if e.is(max_output_tokens):
        if cap < MAX: raise(maxOutputTokensOverride); retry()
        else: append(meta_continue_msg); retry()
assert consecutiveFailures < MAX_CONSECUTIVE_AUTOCOMPACT_FAILURES
```
