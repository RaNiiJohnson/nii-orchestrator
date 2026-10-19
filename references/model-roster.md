# Model roster: platform contract

Open when compiling a new execution prompt or an execution handoff missing its model settings.

## Ask at compilation

- The Lead uses the model and effort with which the implementation session is launched. Do not include it among the three choices.
- Implementers own bounded code changes, their tests and accepted review fixes.
- Researchers own read-only repository exploration, primary-documentation checks and test-gap analysis.
- Reviewers work independently, read-only, on changes they did not author.
- Check the current environment's model catalog and agent controls; list exact identifiers and supported effort levels, not aliases guessed from memory.
- Ask one question per role, preferably bundled in one structured question. Put the user's latest confirmed settings first when still available; otherwise recommend supported settings and label them as recommendations.
- If the current compilation request already specifies all three roles, confirm the parsed settings and proceed. If incomplete, ask only for the missing entries.
- A previous compilation is a recommendation, not authorization for a new one. Offer to remember a preference only when a supported persistence mechanism exists; do not claim it was saved without writing it.
- Keep a pending roster question open until answered. Do not silently choose a model or effort.

## Codex

- Use exact model and effort overrides supported by the available sub-agent tool.
- Where spawn_agent rejects overrides with full-history forks, use a fresh or partial context and supply a complete task brief.
- Avoid specialized agent roles with fixed models that would override the chosen settings.
- Model availability on the current host does not establish availability in another session. Require the execution Lead to check again and disclose limitations before substitution.
- Respect the host's actual concurrent-agent capacity; queue additional independent work rather than inventing unlimited slots.

## Other agent environments

- Translate the user's choices to native supported controls; never invent unsupported flags.
- In Claude Code or another client, inspect the available model aliases and effort controls rather than reusing Codex model identifiers.
- If a chosen per-agent setting is unavailable, explain the limitation and obtain a replacement choice; never substitute silently or create persistent global configuration as an unrequested workaround.
- If the user accepts a sequential fallback without sub-agents, state that review was not independently performed.

## Review independence

- Give Reviewers fresh contexts, the specification, acceptance criteria and the actual diff, not the authors' persuasive rationale.
- Use distinct risk lenses, such as scope coverage, authorization, data consistency or failure recovery.
- A different model family may add useful independence when supported; it is optional. Preserve the user's confirmed roster even when all roles use one family.
- Copy exact settings and any confirmed limitation into the execution prompt. Settings describe roles, not headcounts.
