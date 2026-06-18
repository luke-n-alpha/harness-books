# Harness Books

[English README](./README.md) · [中文 README](./README.zh-CN.md)

[![온라인으로 읽기](https://img.shields.io/badge/Read%20Online-Harness%20Books-16a34a?style=flat-square&logo=googlechrome&logoColor=white)](https://harness-books.agentway.dev/en/)
[![AgentWay 소개](https://img.shields.io/badge/About-AgentWay-22c55e?style=flat-square&logo=bookstack&logoColor=white)](https://agentway.dev)

하네스 엔지니어링(harness engineering)을 다루는 두 권의 책입니다. 두 책은 같은 공학적 질문을 좇습니다. 코드를 작성하는 모델을 터미널, 저장소, 권한 시스템, 팀 워크플로(workflow) 안에 놓았을 때, 전체 시스템을 한계 안에 머무르게 하고, 끊기지 않게 하며, 그 결과에 책임지게 만드는 것은 무엇인가?

<table>
  <tr>
    <td align="center" valign="top" width="50%">
      <a href="https://harness-books.agentway.dev/en/book1-claude-code/">
        <img src="./book1-claude-code/assets/cover-wxb-en.svg" alt="Harness Engineering: Claude Code 설계 가이드" width="280">
      </a>
      <br>
      <strong>Harness Engineering: Claude Code 설계 가이드</strong>
      <br>
      <a href="https://harness-books.agentway.dev/en/book1-claude-code/">온라인으로 읽기</a> ·
      <a href="https://harness-books.agentway.dev/en/book1-claude-code/exported/book1-claude-code-en.pdf">PDF 내려받기</a>
    </td>
    <td align="center" valign="top" width="50%">
      <a href="https://harness-books.agentway.dev/en/book2-comparing/">
        <img src="./book2-comparing/assets/cover-wxb-en.svg" alt="Claude Code와 Codex의 하네스 설계 철학" width="280">
      </a>
      <br>
      <strong>Claude Code와 Codex의 하네스 설계 철학</strong>
      <br>
      <a href="https://harness-books.agentway.dev/en/book2-comparing/">온라인으로 읽기</a> ·
      <a href="https://harness-books.agentway.dev/en/book2-comparing/exported/book2-comparing-en.pdf">PDF 내려받기</a>
    </td>
  </tr>
</table>

이 책들은 소스 코드를 한 줄씩 따라가려는 것이 아닙니다. 하네스(harness)가 제약과 실행을 어떻게 조직하는지, 그리고 본질적으로 불안정한 모델을 어떻게 지속 가능한 공학 질서로 접어 넣을 수 있는지에 초점을 맞춥니다. 프롬프트(prompt) 계층화, 질의 루프(query loop), 권한 결정, 컨텍스트 거버넌스(context governance), 실패 복구, 멀티 에이전트(multi-agent) 검증, 로컬 규칙, 그리고 팀 제도(institution)가 함께 하네스의 기관계(organ system)를 이룹니다. 진짜 위험은 모델이 가끔 틀린 말을 한다는 데 있는 것이 아니라, 시스템에 그 결과를 다룰 구조가 없다는 데 있습니다.

## 핵심 주장

- 하네스 엔지니어링은 제약 구조가 실행을 어떻게 조직하는가에 관한 것입니다.
- 코드를 작성하는 모델이 실제 공학 환경에 들어서는 순간, 핵심 문제는 더 이상 답변의 품질이 아니라 행동의 결과입니다.
- 프롬프트, 도구, 권한, 상태, 복구, 검증, 제도는 시스템 주변의 부속품이 아닙니다. 같은 제어 구조 안의 기관(organ)입니다.
- 에이전트 시스템을 비교할 때 핵심 질문은 기능 체크리스트가 아니라, 질서를 실제로 어디에 두는가입니다.
- 팀이 개인의 경험을 재사용 가능한 규칙으로 바꾸지 못하면, 에이전트를 안정적인 시스템으로 만들기 어렵습니다.

## 두 책이 다루는 것

### Book 1: Claude Code 설계 가이드

첫 번째 책은 Claude Code를 관찰 대상으로 삼아 런타임 구조에 집중합니다. 시스템이 왜 결국 제어 평면(control plane), 질의 루프(query loop), 도구 권한(tool permission), 컨텍스트 거버넌스(context governance), 복구 경로(recovery path), 멀티 에이전트(multi-agent) 검증, 팀 규칙 같은 구성 요소를 키울 수밖에 없는지를 묻습니다.

다음 질문이 궁금하다면 Book 1부터 시작하십시오.

- 하네스 엔지니어링이 왜 단지 규모만 키운 프롬프트 엔지니어링(prompt engineering)이 아닌가
- 프롬프트가 왜 채팅 창이 아니라 본질적으로 제어 평면의 일부인가
- 모델의 실수가 왜 예외적 사건이 아니라 런타임의 정상 상태로 다뤄져야 하는가
- 멀티 에이전트 작업과 검증이 왜 하나의 모호한 메커니즘으로 뭉뚱그려지면 안 되는가
- 팀이 어떻게 개인의 경험을 재사용 가능한 공학 제도로 굳힐 수 있는가

### Book 2: Claude Code와 Codex 비교

두 번째 책은 Claude Code와 Codex를 나란히 놓고, 각 하네스가 질서를 어디에 두는지 묻습니다. 한쪽은 런타임 규율에서 출발하고, 다른 쪽은 더 구조화된 제어 계층에서 출발합니다. 두 시스템 모두 작동하지만, 권한을 분배하는 방식이 다릅니다.

시스템 선택, 아키텍처 판단, 또는 직접 하네스를 만들 때 무엇을 배워야 하는지가 더 궁금하다면 Book 2부터 시작하십시오.

- Claude Code와 Codex 사이의 가장 큰 제어 평면(control plane) 차이는 무엇인가
- 질의 루프(query loop), 스레드(thread), 롤아웃(rollout), 상태(state)의 역할을 어떻게 맞춰 볼 것인가
- 권한, 샌드박스(sandbox), 정책 언어(policy language)가 어떤 거버넌스 역할을 하는가
- 스킬(skill), 훅(hook), 로컬 규칙이 어떻게 조직의 습관을 시스템에 새기는가
- 직접 하네스를 만들고 싶다면, 누구에게서 먼저 배우고 어느 계층부터 공부해야 하는가

## 권장 읽기 순서

- 전체 틀을 먼저 잡고 싶다면: Book 1을 읽고 이어서 Book 2를 읽으십시오.
- 코딩 에이전트 도구에 이미 익숙하고 아키텍처의 분기점을 곧바로 보고 싶다면: Book 2부터 시작하십시오.
- 결론만 원한다면: Book 1의 9장과 Book 2의 7장을 읽으십시오.

<details>
<summary><strong>전체 목차</strong></summary>

### Book 1 — Harness Engineering: Claude Code 설계 가이드

- [도입](./book1-claude-code/locales/ko/index.md)
- [서문: 하네스, 터미널, 그리고 엔지니어링 제약](./book1-claude-code/locales/ko/preface.md)
- [1장 왜 하네스 엔지니어링이 필요한가](./book1-claude-code/locales/ko/chapter-01-why-harness-engineering.md)
- [2장 프롬프트는 인격이 아니라 제어 평면입니다](./book1-claude-code/locales/ko/chapter-02-prompt-is-control-plane.md)
- [3장 질의 루프: 에이전트 시스템의 심장박동](./book1-claude-code/locales/ko/chapter-03-query-loop-heartbeat.md)
- [4장 도구, 권한과 인터럽트: 왜 에이전트는 세계를 직접 만지면 안 되는가](./book1-claude-code/locales/ko/chapter-04-tools-permissions-interrupts.md)
- [5장 컨텍스트 거버넌스: 메모리, CLAUDE.md, 그리고 예산 제도로서의 압축](./book1-claude-code/locales/ko/chapter-05-context-memory-compact.md)
- [6장 오류와 복구: 실패 후에도 계속 작동하는 에이전트 시스템](./book1-claude-code/locales/ko/chapter-06-errors-and-recovery.md)
- [7장 멀티 에이전트와 검증: 분업으로 불안정성 관리하기](./book1-claude-code/locales/ko/chapter-07-multi-agent-and-verification.md)
- [8장 팀 도입: 똑똑한 도구를 재사용 가능한 제도로 만들기](./book1-claude-code/locales/ko/chapter-08-team-landing-practices.md)
- [9장 하네스 엔지니어링 10대 원칙](./book1-claude-code/locales/ko/chapter-09-ten-principles.md)
- [부록 A 체크리스트: 원칙을 실행 가능한 제약으로 만들기](./book1-claude-code/locales/ko/appendix-a-checklists.md)
- [부록 B 도표: 런타임 뼈대 그려보기](./book1-claude-code/locales/ko/appendix-b-diagram-notes.md)
- [부록 C 소스 코드 지도: 각 장의 근거가 되는 파일](./book1-claude-code/locales/ko/appendix-c-source-map.md)

### Book 2 — Claude Code와 Codex의 하네스 설계 철학

> Book 2의 한국어판은 아직 준비 중입니다. 아래 링크는 영어 원문으로 연결됩니다.

- [도입](./book2-comparing/locales/en/index.md)
- [읽기 지도: Book 1과 이 비교서를 함께 이해하는 법](./book2-comparing/locales/en/chapter-00-reading-map.md)
- [서문: 같은 말에 얹은 부속품이 아니라, 서로 다른 두 하네스](./book2-comparing/locales/en/preface.md)
- [1장: 왜 Claude Code와 Codex를 비교하는가](./book2-comparing/locales/en/chapter-01-why-this-comparison.md)
- [2장: 두 개의 제어 평면: 프롬프트 조립과 명령 단편](./book2-comparing/locales/en/chapter-02-two-control-planes.md)
- [3장: 심장박동은 어디에 있는가: 질의 루프 대 스레드·롤아웃·상태](./book2-comparing/locales/en/chapter-03-loop-thread-and-rollout.md)
- [4장: 도구, 샌드박스, 정책 언어: 누가 모델의 과속을 막는가](./book2-comparing/locales/en/chapter-04-tools-sandbox-and-exec-policy.md)
- [5장: 스킬, 훅, 로컬 규칙: 시스템이 지역적 규율을 배우는 법](./book2-comparing/locales/en/chapter-05-skills-hooks-and-local-governance.md)
- [6장: 위임, 검증, 영속 상태: 누가 시스템의 자기 채점을 막는가](./book2-comparing/locales/en/chapter-06-delegation-verification-and-state.md)
- [7장: 다른 길을 통한 수렴인가, 갈라지는 분기인가](./book2-comparing/locales/en/chapter-07-convergence-and-divergence.md)
- [8장: 직접 하네스를 만든다면, 무엇부터 공부할 것인가](./book2-comparing/locales/en/chapter-08-how-to-choose-or-build.md)
- [부록 A: 비교의 토대가 되는 소스 코드 지도](./book2-comparing/locales/en/appendix-a-source-map.md)
- [부록 B: 당신의 하네스가 어디에 서 있는지 가늠하는 체크리스트](./book2-comparing/locales/en/appendix-b-checklists.md)

</details>

## 계속 연습하고 싶다면: AgentWay

<table>
<tr>
<td width="180" align="center" valign="middle">
  <a href="https://agentway.dev/">
    <img src="assets/agentway-logo.svg" alt="AgentWay" width="150">
  </a>
</td>
<td valign="middle">
  <b><a href="https://agentway.dev/">AgentWay</a></b>는 관련은 있지만 별개인 실습 플랫폼입니다. Harness Books가 제어 구조, 공학적 판단, 아키텍처의 분기를 설명한다면, AgentWay는 이 아이디어들이 학습 경로, 훈련, 프로젝트 연습, 에이전트 PoC로 이어지는 곳입니다.
</td>
</tr>
</table>

## 로컬 빌드

로케일을 인식하는 Honkit 사이트 두 개를 빌드한 뒤, 통합 Pages 사이트를 조립합니다.

```bash
python3 tools/book-kit/build_honkit.py book1-claude-code
python3 tools/book-kit/build_honkit.py book1-claude-code --locale en
python3 tools/book-kit/build_honkit.py book2-comparing
python3 tools/book-kit/build_honkit.py book2-comparing --locale en
python3 tools/book-kit/build_pages_site.py
```

최종 산출물은 `dist/`에 기록됩니다.

---

<sub>Keywords: Harness Engineering, Claude Code guide, Claude Code vs Codex, AI coding agent, control plane, query loop, agent recovery, agent verification, local governance, approval policy</sub>
