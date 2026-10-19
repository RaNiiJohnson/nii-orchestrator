# Progressive execution prompt contract

Open before drafting an implementation prompt. Adapt this schema to the actual product; omit irrelevant sections and resolve placeholders before returning the prompt.

The prompt is a complete scope brief, not a binding file-by-file technical plan. The fresh Lead inspects current evidence and chooses the implementation plan. All future scope remains visible for architecture decisions; only the active batch is authorized for implementation.

## Required prompt fields

Include the destination and last observed repository state; current user instructions; accepted product behavior, corrections and exclusions; chosen stack; public interfaces and data ownership when relevant; exact model roster; workflow below; verification and acceptance evidence; external prerequisites; and delivery expectations.

Label recommendations and unverified facts. Ask about unsettled material product choices before compilation. Do not convert an unanswered question into a requirement.

Do not embed project-specific examples from prior unrelated projects. Preserve the current user's naming, paths, platforms, budget and release order. Never include secrets in prompts or records.

## Execution mandate

Encode these rules without conflicting continuous-execution instructions elsewhere in the prompt:

1. Inspect repository instructions, branch/worktrees, dirty files, current dependencies, tests and project records. Preserve pre-existing work. Verify unfamiliar APIs against installed types or current primary documentation.
2. Present the complete roadmap, then start only the first unfinished, dependency-ready batch unless the user identifies another batch whose prerequisites are met.
3. Announce the batch's goal, visible outcome, boundaries and verification. Decide routine technical details and proceed within that batch without per-edit approvals.
4. Inform the user at meaningful milestones, significant discoveries and blockers. Respect the host's progress-update cadence; status updates do not replace the final delivery checkpoint.
5. Implement, integrate, verify, independently review and remediate the active batch. Continue necessary corrections within the batch rather than stopping merely after writing code.
6. Update the durable records and deliver the batch report. End the turn and wait for explicit user continuation before starting another batch. Corrections belong to the current batch until resolved.

If the host is in planning-only mode, prepare the plan without implementation; a prompt never overrides mode restrictions.

## Roadmap and PR boundaries

- Define ordered outcomes and known dependencies, not a fixed universal list of phases or a required number of PRs.
- Make each batch reviewable and locally testable; keep tests with the behavior they prove. Refine the provisional split against the actual change graph before starting.
- Distinguish a batch, an agent workstream, a commit and a GitHub PR. A batch may warrant more than one PR; do not force an unsafe split or create one PR per agent.
- Future batches may inform architecture but must not be implemented speculatively by the Lead or sub-agents.
- A completed but unmerged batch is not automatically available to a new branch. Inspect the actual dependency state; prepare a documented local stack or wait for the prerequisite as appropriate. Never assume that user continuation authorizes a merge.
- A roadmap is not proof of implementation. A blocked or partially verified batch must be reported as such and must not be marked done to advance the roadmap.

## Role routing and briefs

- Lead: owns the plan, decomposition, sequencing, integration, findings triage and final verification; runs as launched.
- Researchers: use the confirmed settings for independent read-only questions in parallel when useful; report evidence rather than file dumps.
- Implementers: use the confirmed settings for independent slices of the active batch and accepted fixes. Own disjoint files/modules; sequence shared interfaces before dependent slices.
- Reviewers: use the confirmed settings in fresh, read-only contexts after integrated verification; never review changes they authored.
- Use multiple agents when independent work supports it, within platform limits. Implement directly when delegation would add no value.
- Every brief supplies goal and reason, settled invariants, owned files/modules, neighboring interfaces, done-condition, focused checks and expected report. Implementers must preserve others' and the user's changes.
- Detect unsupported settings before dispatch. Apply the explicit model/fallback agreement from the roster; disclose the actual roster in the report.

## Durable project state

Create or extend concise project records instead of duplicating existing conventions:
- agreed scope and decisions;
- dependency-ordered roadmap and batch status;
- current batch, actual changes, checks and blockers;
- branch/worktree/commit and PR state;
- one next mission and relevant context pointers.

Keep transient logs in an ignored task-owned scratch location. Keep the durable, non-secret handoff in repository documentation, so another chat can reconstruct progress without access to scratch files or old conversation history.

Update records at milestones and before each delivery. Preserve dirty files and unfinished work accurately; a handoff does not require inventing a clean state.

## UI development loop

For any browser-observable work, require each UI Implementer and the Lead to run the app early and use the provided browser continuously: write a small piece, look, interact, fix and look again.

Observe loading, empty, failure, permission-denied, long-content, narrow-width and theme/language states applicable to the feature. Inspect console/network issues and retain concise observations or captures as evidence.

Types and builds do not establish visual correctness. State precisely which native/mobile checks ran; browser previews are not evidence of native-device execution.

## Verification and independent review

1. Run focused checks during implementation and integrated checks for the active batch before review. Include relevant regression coverage of completed prerequisites, not unfinished future functionality.
2. Prove meaningful success, authorization, concurrency and recovery behavior where relevant. Use fakes for paid or external actions unless real calls are authorized; never claim an unconfigured integration works.
3. Launch independent Reviewers with distinct risk lenses selected for this batch. Request concrete file/line evidence, reproduction and severity.
4. Confirm each finding by reproduction or code/documentation evidence before fixing. Explain dismissals with evidence.
5. Delegate confirmed fixes to Implementers and rerun affected checks. Allow at most two complete review/remediation cycles per batch; disclose unresolved findings rather than looping or claiming success.
6. Separate verified, unverified, blocked and deferred outcomes in the final report. Missing credentials cannot be replaced by fake success.

## External-action boundaries

- Necessary local branches, worktrees and commits are normal implementation mechanics unless repository rules or the user limit them. Protect unrelated work.
- Pushing, opening PRs, merging, production deployment, purchases and creating external repositories require explicit applicable user authorization; respect any narrower host permission requirement.
- A request such as "continue" authorizes the next batch only. Authorization to open one PR does not authorize merging it, deploying it or starting another batch.
- Without a remote or GitHub access, deliver locally with a concrete PR proposal. Do not invent a PR URL or create an external repository to remove the blocker.
- If PR creation is authorized, create only the authorized PRs, attach their URLs using the host's artifact tool when available, inspect available CI status and report actual results. An open PR is not a completed merge.
- Creating, navigating to or messaging another chat is separate from preparing its handoff; do it only at the user's request.

## Required delivery checkpoint

End every batch with:
- implemented outcome and scope left for later;
- steps to run and try the result;
- checks actually run, results and UI/native evidence;
- independent review findings, fixes and remaining risks;
- secrets-free setup requirements, blockers and manual checks;
- actual Git state and any real PR/CI state;
- proposed PR title(s), contents, dependencies and count when no PR exists yet;
- next batch and a copy-ready next-chat handoff.

Stop at this report. State that the active batch has been delivered or is blocked, accurately, and that the next batch awaits user continuation. Do not include a question authorizing all remaining PRs or an instruction to finish the complete roadmap autonomously.

## Next-chat handoff schema

Return a compact brief with:
- repository and precise branch/worktree/commit state, including dirty files;
- sources of applicable instructions and scope/roadmap records;
- completed batches with evidence and the current batch's true status;
- accepted decisions and exclusions relevant to the next mission;
- exact confirmed role roster, with availability recheck required;
- blockers, prerequisites and external actions already authorized, without broadening them;
- exactly one next mission: complete the current batch if unfinished, otherwise the next batch once the user requests it;
- the same verify/review/report/stop checkpoint and external-action boundaries.

Do not claim to have inspected inaccessible files or to have saved a chat-only handoff. Preserve the option to continue in the same chat or a new one.
