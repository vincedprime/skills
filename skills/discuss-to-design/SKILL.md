---
name: discuss-to-design
description: Plan collaboratively through a shared Markdown discussion with per-point Agent/User replies, then consolidate agreed decisions into one technical design document. Use when the user wants document-based cross-questioning, adds comments or answers to planning docs, or asks to continue this planning method. This is a planning workflow, not authorization to implement application code.
---

# Discuss to design

Help the user reason through a design by exchanging questions and answers inside the same document. The user may challenge assumptions, request first-principles explanations, make decisions, or reserve topics for themselves. Progress toward a coherent design without treating every question as a request to build.

## Two documents, two roles

Use existing documents when available. Otherwise create:

- `<topic>-discussion.md`: active open points and their conversations.
- `<topic>-tdd.md`: the single technical design document containing agreed decisions, explicit user-owned placeholders, and deferred work.

TDD means **Technical Design Document** here, not automatically test-driven development. Include acceptance criteria when useful, but do not introduce a testing methodology or framework solely because the user says TDD.

Do not create a second TDD disguised as a discussion document, or duplicate the same decisions across several planning files. Keep both documents linked. Follow existing folder conventions rather than assuming a particular repository or stack.

## Begin with evidence

Read relevant project docs and inspect only the code needed to establish current facts. Cross-check older specs against the user's latest decisions. Distinguish current requirements, obsolete plans, agent proposals, and verified implementation. Do not resurrect superseded requirements because an old file calls them final.

Collect concrete unresolved problems. Explain the problem first, then offer a reasoned approach and the exact decision needed. Avoid turning routine implementation details into repeated product approval questions. Preserve useful existing data structures and constraints when consolidating docs.

## Discussion format

Use numbered headings and a conversation within each point:

```markdown
## 3. Descriptive decision title

**Problem:** What remains unresolved and why it matters.

**Agent:** Proposed approach, reasoning, and a concrete example. End with the specific question if an answer is needed.

**User:**

Status: Open.
```

The user fills in their reply. Append an `**Agent:**` reply directly after their latest message, before the status or next section. Repeat the labels for subsequent turns. Never invent a user reply or approval.

While a point is open, preserve earlier messages verbatim: do not paraphrase, compress, reorder, or replace the conversation. A new reply can explicitly supersede an older proposal. Metadata such as status may be maintained, but do not edit a status line containing the user's answer as if it were disposable metadata.

Use plain language, short connected explanations, and concrete examples. When the user asks why, explain the mechanism and tradeoff before recommending a solution. Define unfamiliar terms; use backend/Java comparisons only when relevant to the user. Avoid tables unless requested. For cost, performance, or library claims, verify the needed evidence and distinguish estimates from measurements.

## Process updates

Messages such as “updated,” “answered,” and “done” mean read the document again, not infer approval from the chat message. Also read inline diff comments and answers inserted into status lines. Anchor comments by their meaning and surrounding text because line numbers can move.

For each new answer:

- **Question or challenge:** append a direct answer and keep the point open. Do not keep restating already-settled choices.
- **Explicit agreement:** carry the agreed decision into the TDD. Approval of one paragraph does not approve every proposal in the section.
- **Partial agreement:** move the settled requirement into the TDD, append what remains unresolved, and preserve the open conversation. Do not label an entire topic closed prematurely.
- **Closed:** consolidate the decision or requested handoff first, then remove the closed discussion section. Append-only applies to open conversations, not closed sections.
- **Deferred / “backlog”:** record the issue under deferred engineering work in the TDD without treating its proposed solution as approved; remove it from active discussion.
- **“I will decide” / “not for agent”:** stop investigating or proposing on that topic. Leave it user-owned; if asked to move it to the TDD, supply a structure with clearly unfilled values and remove the discussion section.

If a user closes a topic without answering every subquestion, honor the closure. Record only the explicit decision; put genuinely necessary remaining details into a clearly labeled user-owned placeholder rather than silently choosing them or reopening the discussion.

Preserve point numbers where prior replies refer to them. If all points are closed, leave a short notice linking to the TDD; do not manufacture more questions to keep planning active.

## Maintain the single TDD

Write a design specification, not a transcript. Scale structure to the project; typical sections are purpose, scope, architecture, data model, operations, invariants, acceptance criteria, and deferred/user-owned details.

When promoting a decision, update its actual section, schema, and relevant acceptance criteria. Remove conflicting pending text. Avoid accumulating “latest decisions” appendices that contradict earlier sections. The conversation's append-only rule does not prohibit maintaining the TDD as a coherent specification.

Separate confirmed behaviour from placeholders. Retain exact field types, units, nullability, ownership rules, and state transitions when they are settled. Do not invent values the user reserved for themselves. A closed discussion does not prove implementation readiness: clearly identify remaining user-owned details and deferred behaviour without treating them as active agent questions.

## Scope and finishing

Document planning and agreed design only unless the user separately requests implementation. Do not edit application code, migrations, dependencies, or deploy resources as a consequence of design approval.

Do not delete historical documents merely because this skill is active. When explicitly asked to clean docs, preserve unique useful material first and repair references after removing redundant files.

Prefer direct, focused Markdown edits. Use scripts only when their benefit justifies them; do not mechanically rewrite an open conversation. Before writing, reread affected content so new user edits are not overwritten. Verify that user messages remain intact in open sections, promoted decisions are consistent, and links resolve.

Finish briefly: name the updated documents, summarize the decisions moved, and state what remains open. Do not repeat the entire discussion in chat.
