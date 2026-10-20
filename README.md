# grill-into-pr

`grill-into-pr` is a ChatGPT-oriented skill for designing a GitHub repository change before implementation, including redesign of already-implemented behavior.

It uses focused grilling to settle the purpose, requirements, and design, then continuously reflects those decisions in a documentation-only Draft PR.

## Contract

The user specifies a GitHub repository and target branch.

The skill then:

1. grills unresolved decisions that materially affect the purpose, requirements, or design;
2. puts each recommended answer after all choices for its grill question;
3. creates a Draft PR early;
4. changes documentation only, never implementation files;
5. updates the PR after about five newly settled decisions;
6. treats each checkpoint as a full synchronization between the conversation and the PR;
7. distinguishes decided, unresolved, and deferred issues;
8. keeps only the currently effective decisions when earlier statements are corrected or replaced;
9. finishes when no in-scope unresolved decision remains;
10. removes Draft status when the design PR is ready for review;
11. returns directly to grilling if PR review reveals a decision that requires user judgment.

Implementation belongs to a separate phase.

## Checkpoints

A checkpoint is not merely an append operation.

At each checkpoint, the skill compares all currently effective decisions with the PR, updates the PR body and relevant documentation, and removes stale or superseded content.

This keeps long design conversations from accumulating unreflected decisions.

## Scope

For already-implemented behavior, the skill compares authoritative requirements and design with the current implementation, then settles the intended design without treating existing code or tests as requirements. Implementation, testing, replanning, and salvage decisions belong to their respective workflows.

The PR may modify documentation files only.

If no suitable document exists, the skill may create an appropriate design document.

Incidental names such as branch names, PR titles, and document names are chosen autonomously unless the user or repository already constrains them.

## Completion

The final artifact is a review-ready design PR.

Issues explicitly deferred to another chat or phase do not block completion.

If reviewer feedback or self-review introduces a decision that requires user judgment, the skill resumes the normal grill flow and synchronizes the resulting decision back into the PR.

## Origin

This skill follows the grilling approach used by `supersovaa/grill-into-patch`, which in turn was derived from the ideas and structure of Matt Pocock's `grilling` skill from the `mattpocock/skills` repository.
