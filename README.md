# grill-into-pr

`grill-into-pr` is a ChatGPT-oriented skill for designing a GitHub repository change before implementation.

It uses focused grilling to settle the purpose, requirements, and design, then continuously reflects those decisions in a documentation-only Draft PR.

## Contract

The user specifies a GitHub repository and target branch.

The skill then:

1. grills unresolved decisions that materially affect the purpose, requirements, or design;
2. creates a Draft PR early;
3. changes documentation only, never implementation files;
4. updates the PR after about five newly settled decisions;
5. treats each checkpoint as a full synchronization between the conversation and the PR;
6. distinguishes decided, unresolved, and deferred issues;
7. keeps only the currently effective decisions when earlier statements are corrected or replaced;
8. finishes when no in-scope unresolved decision remains;
9. removes Draft status when the design PR is ready for review.

Implementation belongs to a separate phase.

## Checkpoints

A checkpoint is not merely an append operation.

At each checkpoint, the skill compares all currently effective decisions with the PR, updates the PR body and relevant documentation, and removes stale or superseded content.

This keeps long design conversations from accumulating unreflected decisions.

## Scope

The PR may modify documentation files only.

If no suitable document exists, the skill may create an appropriate design document.

Incidental names such as branch names, PR titles, and document names are chosen autonomously unless the user or repository already constrains them.

## Completion

The final artifact is a review-ready design PR.

Issues explicitly deferred to another chat or phase do not block completion.

## Origin

This skill follows the grilling approach used by `supersovaa/grill-into-patch`, which in turn was derived from the ideas and structure of Matt Pocock's `grilling` skill from the `mattpocock/skills` repository.
