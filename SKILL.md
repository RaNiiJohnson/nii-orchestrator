---
name: nii-orchestrator
description: Shape projects into staged implementation prompts and evidence-backed handoffs. Use when asked to scope a project, prepare a full prompt with a stop after each PR-ready batch, or brief the next chat.
disable-model-invocation: true
license: MIT
---

# Nii Orchestrator

Turn a settled product discussion into a complete brief for progressive delivery. Derived from Feature Orchestrator; its continuous-execution contract is replaced by one verified batch per user continuation.

## Inspect

1. Identify the requested branch: discuss scope, compile an implementation prompt, or prepare a handoff. An invocation alone starts discussion, not implementation.
2. Inspect applicable repository instructions, Git state, existing code and project records before asking discoverable questions. If no repository exists, record that fact and the intended destination.
3. During discussion and prompt preparation, keep application source, configuration, dependencies and tests unchanged. Keep drafts in chat unless the user asks to save them.

## Discuss

4. Establish users, desired outcomes, journeys, scope, exclusions, constraints, ownership, failure behavior and acceptance evidence. Ask about product choices that materially change scope; distinguish facts, decisions, recommendations and assumptions.
5. Preserve later corrections in a decision ledger. Suggest missing essentials without treating suggestions as accepted scope. Research only when it changes a decision; delegate independent read-only questions when useful, with evidence-focused briefs.
6. Summarize when requested. Compile only after the user requests the prompt or declares the scope settled; scope discussion is not a reason to request sub-agent models early.

## Compile

7. Read [references/model-roster.md](references/model-roster.md) when preparing a handoff prompt: confirm exact Implementer, Researcher and Reviewer settings for this compilation and check platform support. A complete roster in the current compile request is sufficient; ask only for missing entries.
8. Read [references/execution-prompt-contract.md](references/execution-prompt-contract.md) before drafting. Produce a self-contained execution prompt carrying the complete agreed scope, exact roster, acceptance evidence and all batch boundaries below. The fresh Lead inspects the repository and decides the technical plan.
9. Include a provisional dependency-ordered roadmap of coherent, PR-ready outcomes. Treat workstreams, batches and actual PRs as different concepts; have the Lead refine unsafe boundaries before starting a batch.
10. Instruct the Lead to deliver only the first unfinished, dependency-ready batch, including focused checks, integrated verification and independent review. Require meaningful progress updates within the batch and a final user-facing delivery report.
11. Require an explicit user continuation before the next batch. A user may continue in the same chat or take the handoff to a fresh chat; sub-agents and an open PR never bypass this checkpoint.
12. Keep external actions separate: pushing, opening PRs, merging and production deployment each require explicit applicable authorization. A request to continue to the next batch grants none of these actions.

## Handoff

13. For a next-chat handoff, inspect the latest project records, Git state, checks and PR evidence available. If inspection is unavailable, label supplied information as unverified; never infer completion from an old plan.
14. Return a copy-ready brief naming repository, branch/worktree, completed and active batches, decisions, relevant documents, actual checks, dirty files, blockers and exactly one next mission. Preserve unfinished work rather than starting the next batch to make the handoff look complete.
15. Carry the one-batch checkpoint, exact confirmed roster and external-action boundaries into every handoff. Ask only for missing or newly requested settings; a status-only handoff does not need a new roster.

## Return and stop

16. Return a short introduction and one copy-ready prompt for compilation or handoff; answer discussion questions at their natural level. Save artifacts only when requested.
17. Check that the prompt preserves every accepted correction, leaves no material product choice disguised as a technical default, and contains no instruction to finish the entire roadmap autonomously or create all PRs together.
18. End after the requested discussion, prompt or handoff. Implementation belongs to a separately requested implementation mission, which executes only its active batch.
