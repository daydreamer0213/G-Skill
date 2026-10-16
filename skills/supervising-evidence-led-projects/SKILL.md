---
name: supervising-evidence-led-projects
description: Use when supervising a long-running multi-stage software project with architecture documents, delegated execution, exact-SHA gates, external actions, or recurring risks of over-engineering, under-design, repeated approvals, and unverified blocker claims.
---

# Supervising Evidence-Led Projects

## Core principle

Build the smallest **sufficient** system justified by current evidence and the
project's authoritative design. “Minimal” does not mean leaving the next
failure unknowable; “complete” does not mean building every imaginable future
capability.

## Working method

1. Read current architecture, specs, plans, and handoffs before proposing a
   stage. History is evidence, not authority over newer design.
2. When mining long conversations for lessons, reconstruct complete decision
   cases rather than producing a keyword or incident checklist. Preserve the
   observed problem, the user's reasoning in their own words, the mistaken
   assumption, alternatives considered, the selected solution and evidence,
   the transferable method, and its applicability boundary. A list of past
   mistakes can prevent repetition but does not demonstrate transferable
   understanding.
3. Derive the solution from the project's current canonical concepts,
   invariants, ownership boundaries, and product flow before mapping it onto
   available interfaces. Existing APIs describe implementation capability;
   they do not automatically define product semantics. Record inherited
   decisions, the proven design-to-code gap, genuinely new decisions, and
   explicit deferrals. If verified code or operational evidence supersedes a
   document, resolve or update the canonical source instead of following it
   mechanically.
4. Treat a load-bearing design as a falsifiable hypothesis before treating it
   as a specification. State the problem without assuming a mechanism; inspect
   mainstream and upstream solutions; compare realistic alternatives; name
   both the risk reduced and the normal capability lost; and choose the
   cheapest evidence that could disprove the design. Correct code does not
   rescue an unreasonable specification.
5. Trace one normal story, one counterexample that should not trigger the
   mechanism, and one failure story across components. For every important
   fact, identify its source, decision owner, destination, and durable evidence.
   If a realistic story does not fit, revisit component relationships before
   adding fields.
6. State the product boundary and stage outcome. Separate the main path from
   experiments, legacy assets, and later-stage ideas.
7. Before designing ordinary Agent or Runtime machinery, inspect current
   upstream/mainstream capabilities and assign ownership in this order:
   **reuse → configure or thinly adapt → self-build only for a proven
   project-specific responsibility**. A design being strict, deterministic,
   or easy to test is not evidence that the project should own it. Use the
   normal Agent loop only as an end-to-end equivalence check for the adapter,
   not as a subsystem to recreate.
8. Classify each alleged gap before acting:
   - **Proven blocker:** reproduced on a reachable current path or contradicts
     an existing contract. Fix or explicitly stop that path.
   - **Probable risk:** supported but not reproduced. Add a proportionate check,
     not a subsystem.
   - **Theoretical edge:** requires contrived or unavailable conditions. Record
     it only if useful; it is not a release blocker.
9. Preserve facts needed for the next real decision. Defer pricing engines,
   polling, schedulers, generic stores, and future lifecycle machinery until
   the main path needs them.
10. Execute stages as: approved design → written plan → TDD implementation →
   focused and regression gates → correctness/architecture/simplicity review →
   exact feature SHA → controlled main integration → exact-main CI → separately
   authorized external action.
11. Report exact SHA, behavior, test/CI result, resource/cost facts, uncertainty,
   and next entry point. A controller reports proactively at success, stop, or
   blocker; the supervisor should not busy-poll it.

## Realistic interpretation and stage completion

- Interpret omissions in their normal context and use the precision needed for
  the current decision. A complete resume listing a completed bachelor's degree
  normally supports screening at that level; an adjacent major plus relevant work
  can support a related role. An omitted study format need not block exploratory
  screening. Keep these judgments distinct from verified facts; do not invent
  degrees, personal circumstances, or qualifications.
- Define what this stage decides, the costs of missing a suitable option versus
  advancing a borderline one, and any real later verification. Assign checks to
  the stage that needs them. Explore relevant opportunities when the agreed
  threshold permits it; do not let an upstream filter remove the very cases a
  downstream decision is meant to consider.
- Before executing a stage, state its acceptable outcome, necessary evidence and
  finish condition. Once those are met, close the stage and move to the next
  unmet goal. Reopen a passed item for a changed requirement, demonstrated
  failure or decision-relevant uncertainty; cosmetic consistency and further
  hypothetical edge cases alone do not require another test round.

For the user's reasoning, contrasting examples and scope, read
[recent decision cases](references/recent-decision-cases.md) when these judgments
are relevant. Existing milestone reviews still apply; use actual progress and
remaining acceptance gaps rather than counting debug rounds as advancement.

## Decision rules

| Situation | Required response |
|---|---|
| User sets direction but delegates details | Decide implementation details from the documents; do not request approval item by item. |
| A real run fails with privacy-safe output too coarse to diagnose | Add the narrowest structured fact at the source boundary; neither expose raw data nor build a general logging platform. |
| Synthetic tests pass | Claim mechanism proof only. Do not claim natural efficacy, production readiness, or user validation. |
| An agent proposes a useful task and the real runtime/provider/verifier executes it | Count it as natural project evidence only when it serves a real backlog need, the task and acceptance criteria were frozen before the answer, the result was unknown, and there was one formal attempt without answer-fitting or cherry-picking. Otherwise label it controlled or synthetic. |
| A controller is evaluating an Agent or product | Freeze and launch the work, collect evidence, verify, and reveal identities; never write the product output, repair the evaluated result, or manually manufacture the candidate being judged. |
| A secondary concern could delay the main goal | Defer it unless it protects a current safety, correctness, privacy, or authorization boundary. |
| A gate fails outside the approved scope | Preserve the scene, prove the cause, continue independent work, and request only the narrow authority actually needed. |
| External action is within standing authorization | Proceed without repeated confirmation; never reinterpret development budget as permission for unrelated effects. |

## Resource discipline

Reuse worktrees, caches, dependency stores, and test environments; prefer the
designated data drive. Do not duplicate them for convenience. Distinguish
measured incremental usage from a shared cache's total size. During an active
run preserve the scene; after review, retain receipts, summaries, hashes,
necessary durable records, and committed sources, then retire reproducible
worktrees and generated environments through their supported mechanisms.

## Red flags

- Treating an unlikely hypothetical as an Important blocker without a reachable
  path.
- Rebuilding generic Agent/Runtime behavior because a local implementation is
  controllable, instead of reusing the upstream mechanism and keeping only the
  project's distinct governance seam.
- Reducing historical decisions to keywords, prohibitions, or a bug list while
  dropping the user's reasoning, the rejected assumptions, and the evidence
  that made the final choice appropriate.
- Letting a convenient current API redefine project concepts or flow instead
  of first identifying whether the interface is reusable, needs a thin adapter,
  or exposes a real design-to-code gap.
- Treating a user's architectural correction as a writing preference or a
  one-off prohibition instead of checking whether the direction, ownership,
  or solution fitness has drifted.
- Counting failed patch rounds as a universal threshold instead of using
  changing symptoms and broken producer-consumer evidence to revisit the
  abstraction owner.
- Invoking YAGNI to omit evidence required for the next real decision.
- Building price polling, budget accounting, telemetry, or lifecycle machinery
  before the main feature needs it.
- Re-running a real task to obtain a nicer result instead of diagnosing first.
- Calling a scripted fixture “natural evidence.”
- Claiming green after only a second run hid a clean-build failure.
- Letting an execution task finish without an unsolicited structured report.

When a red flag appears, return to the current documents and observable facts;
do not compensate by swinging to the opposite extreme.
