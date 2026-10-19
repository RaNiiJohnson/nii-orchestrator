# Nii Orchestrator

Scope a complete project, then deliver it progressively: **one verified batch at a time, with a delivery report before continuing**.

Nii Orchestrator helps refine product decisions, prepare a complete implementation prompt for a fresh session, and hand work off to the next chat. It is adapted from [Feature Orchestrator](https://github.com/ski043/Skills/tree/main/skills/feature-orchestrator), with a central change: execution stops after each delivered batch instead of continuing through the entire roadmap unattended.

## Installation

Requirements: Node.js with `npx`, a skill-compatible agent, and the development tools required by your project.

Install globally to use the skill across projects:

```bash
npx skills add RaNiiJohnson/nii-orchestrator --skill nii-orchestrator --global
```

Or install only in the current project, from its root directory:

```bash
npx skills add RaNiiJohnson/nii-orchestrator --skill nii-orchestrator
```

Follow the installer's prompts to select your agent. Start a new agent session after installation so it can discover the skill.

To inspect the files before installing:

```bash
git clone https://github.com/RaNiiJohnson/nii-orchestrator.git
```

The complete skill is at the root of the cloned `nii-orchestrator/` directory. For a manual personal installation in Codex, copy that directory to `~/.agents/skills/nii-orchestrator/`, including its references and agent metadata. Preserve any existing installation with personal modifications.

## Using the skill with Codex

### Scope a project

```text
$nii-orchestrator Help me scope my project and prepare staged delivery. Start by clarifying its users, features, and first-version boundaries.
```

The agent discusses the product and inspects existing evidence. It does not modify application code during this phase, and suggestions do not automatically become accepted requirements.

### Prepare the implementation prompt

```text
$nii-orchestrator The product decisions are settled. Prepare the complete implementation prompt with a stop after each PR-ready batch.
```

The skill asks for the model and effort settings for three sub-agent roles. If the compilation request already specifies the complete roster, it confirms those settings without asking for them again.

| Role | Responsibility |
| --- | --- |
| Lead | Main implementation agent; keeps the model used to launch its session. |
| Implementer | Bounded code changes, tests, and confirmed review fixes. |
| Researcher | Documentation checks, read-only exploration, and API verification. |
| Reviewer | Independent, read-only review in a fresh context. |

The skill does not impose model versions. Availability and settings must be checked in the actual environment; substitutions must be disclosed and accepted.

Copy the generated prompt into a fresh session opened on the correct repository. That session prepares the complete roadmap, then implements only the first unfinished batch whose dependencies are satisfied.

### Hand off to the next chat

```text
$nii-orchestrator Prepare the handoff to the next chat, checking the current repository, tasks, test evidence, and Git state.
```

The handoff carries one next mission, accepted decisions, relevant documents, checks actually performed, dirty files, and blockers. You can use it in the same chat or a new one without replaying the whole conversation.

## What happens in each batch

1. Announce the goal, scope, and result you will be able to try.
2. Implement with updates at meaningful milestones.
3. Verify the work; for UI changes, inspect and interact with the running interface throughout development.
4. Run independent review, confirm findings, and fix accepted issues, with at most two complete review/remediation cycles.
5. Update project records and deliver a report.
6. Stop before the next batch and wait for an explicit request to continue.

A blocked or partly verified batch is reported as such. The agent must not mark it complete merely to advance the roadmap.

## Batches and pull requests

A batch is a coherent, verifiable outcome. A sub-agent workstream, a commit, and a pull request are separate concepts; their boundaries depend on the actual project.

The delivery report includes the proposed PR contents, checks, and Git state. Without remote access, a batch can be delivered locally with a concrete PR proposal.

**Saying “continue” authorizes the next batch, not pushing, opening a PR, merging, or deploying.** Those external actions require separate applicable authorization. An open PR does not automatically authorize the next batch.

## Compatibility and limitations

- The repository includes Markdown instructions and explicit-invocation metadata for Codex.
- In Claude Code or another compatible environment, use its native invocation mechanism and verify model names, effort controls, and sub-agent availability. Codex model identifiers are not portable aliases.
- The skill prepares instructions; it is not a service that monitors chats or automatically creates pull requests.
- The host's modes, permissions, and concurrency limits still apply.
- Installing this skill does not create accounts, credentials, subscriptions, or external tools.

## Files

- [SKILL.md](SKILL.md): primary instructions.
- [Model roster](references/model-roster.md): model choices and platform constraints.
- [Progressive execution contract](references/execution-prompt-contract.md): prompt structure, checkpoints, and handoffs.

## Rights and attribution

No license is granted here for original Nii Orchestrator additions. Copyright (c) 2026 RaNiiJohnson. All rights reserved for those additions.

Material derived from Feature Orchestrator retains its original copyright and MIT notice in [THIRD_PARTY_NOTICES.md](THIRD_PARTY_NOTICES.md). That notice applies to the upstream material, not to the original additions in this repository.
