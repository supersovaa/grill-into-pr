---
name: grill-into-pr
description: Grill the user to settle the purpose, requirements, and design for changes to a GitHub repository, continuously reflect the settled design in a documentation-only Draft PR, and finish with a review-ready PR.
---

# Grill into PR

Use this skill when a GitHub repository change should be designed before implementation.

The purpose is to align on intent, requirements, and design.
Do not implement program code.

## Target

The user specifies the target repository and target branch.

If either is already uniquely identified by the conversation, do not ask for it again.
Use the latest relevant state of the target branch as needed.

If naming is not already constrained by the user or repository, choose suitable names autonomously.
Do not grill merely to choose a PR title, branch name, document name, or similar incidental name.

## Grill

Resolve every user decision needed to make the intended design unambiguous.

Map decisions by dependency.
Ask only questions whose prerequisites are already settled.
Do not ask the user for facts that can be determined from the repository, GitHub, available tools, or other accessible sources.

Number grill questions sequentially as `Q1`, `Q2`, and so on.
Restart numbering at `Q1` for each chat.
Give a recommended answer with every question.
Put the recommended answer last, after all answer choices for that question.

Present answer choices for every grill question.
If the decision can be fully answered as yes or no, label the choices `Y` and `N`.
Otherwise, label the choices `A`, `B`, `C`, and so on as needed.

A decision is settled when the conversation leaves only one valid conclusion.
Later corrections, withdrawals, and replacements override earlier statements.
Only the currently effective decisions count.

Keep the grill focused on decisions that materially affect the purpose, requirements, or design.
Handle incidental details autonomously when no instruction requires otherwise.

If the user explicitly says an issue will not be decided in this chat, mark it as deferred rather than unresolved.
Deferred issues do not block completion.

## Draft PR

Create a Draft PR early, once the target repository, target branch, and overall purpose are sufficiently clear.

The PR is a persistent design artifact, not an implementation PR.

Only documentation files may be changed.
Do not modify source code, configuration, build definitions, schemas, or other implementation files.

Reflect only currently effective decisions in the documentation that owns them, following the repository's conventions. State the intended purpose, requirements, behavior, constraints, and material rationale rather than the conversation or workflow that produced them.
Use identifiers that belong to the subject or an authoritative source (such as official Q&A numbers), while keeping grill question numbers, answer-choice labels, and approvals within the conversation.
If no suitable document exists, create an appropriate design document.

Keep the PR body useful as a current design-status summary.
Distinguish at least:

- `Decided`: currently effective decisions;
- `Unresolved`: decisions still required in this chat;
- `Deferred`: issues explicitly left for another chat or phase.

Do not preserve superseded decisions as current decisions.

## Checkpoints

After about five new decisions have been settled, update the PR.

A checkpoint is a full synchronization point, not merely an append operation.

At each checkpoint:

- compare all currently effective decisions with the entire PR;
- update the PR body;
- update all documentation needed to reflect the current design;
- commit and push the documentation changes;
- remove or correct content that was superseded, withdrawn, or contradicted.

Checkpoint earlier when there is a natural design boundary or when a correction makes an earlier PR state materially stale.

The purpose of checkpoints is to prevent omissions.
Do not accumulate a long backlog of settled decisions before updating the PR.

## Repository changes during the grill

Check the target branch's current state when needed.

If newer repository changes do not affect the meaning of settled decisions, adapt autonomously.
If they could change the meaning of a settled decision, continue grilling.

Keep this lightweight.
Do not perform unnecessary repository-wide work merely because the target branch advanced.

## PR review

If PR review, including reviewer feedback or self-review, reveals a decision that requires user judgment, return directly to the Grill and continue the normal question sequence.
Do not resolve that decision silently as part of review handling.

After the resulting decision is settled, synchronize the PR again before completion.

## Completion

The grill is complete when no unresolved decision remains that this chat is responsible for deciding.

Deferred issues do not block completion.

Before finishing:

- compare the complete set of effective decisions with the PR;
- ensure every effective decision is reflected where appropriate;
- ensure withdrawn or superseded decisions are not presented as current;
- ensure unresolved and deferred items are classified correctly;
- ensure the PR contains documentation changes only.

When the design is complete, remove Draft status so the PR is review-ready.

The finished PR is the final artifact.
Implementation belongs to a separate phase.
