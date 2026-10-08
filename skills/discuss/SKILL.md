---
name: discuss
description: Collaborative discussion workflow where Agent and User exchange questions and answers inside a single Markdown document. Use when the user wants document-based cross-questioning, adds comments or answers to planning docs, or asks to continue this planning method. This is a discussion-first workflow, not authorization to implement application code.
---

# Discuss

Help the user reason through a problem by exchanging questions and answers inside the same document. The user may challenge assumptions, request first-principles explanations, make decisions, or reserve topics for themselves. Progress toward a coherent soultion without treating every question as a request to build.

## One primary document — a second only when needed

The primary and always-present document is:

- `<topic>-discussion.md`: active open points and their conversations.

Do not create a second document upfront. Create a second document — `<topic>-decisions.md` — only when the user explicitly asks for agreed decisions to be recorded, or when enough points have closed that a decisions record is clearly useful. That document captures only closed decisions. It is never a skeleton, never a plan for open items, and never a duplicate of the discussion.

When a second document exists, keep both linked. Follow existing folder conventions rather than assuming a particular repository or stack.

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

Messages such as "updated," "answered," and "done" mean read the document again, not infer approval from the chat message. Also read inline diff comments and answers inserted into status lines. Anchor comments by their meaning and surrounding text because line numbers can move.

For each new answer:

- **Question or challenge:** append a direct answer and keep the point open. Do not keep restating already-settled choices.
- **Explicit agreement:** remove the closed section from the discussion. If a decisions doc exists, add the agreed decision there. If not, note it is ready to move whenever the user asks. Approval of one paragraph does not approve every proposal in the section.
- **Partial agreement:** remove the settled part from the discussion and record it if a decisions doc exists; append what remains unresolved and keep that part open. Do not label an entire topic closed prematurely.
- **Closed:** consolidate the decision, then remove the closed section from the discussion. Do not create a decisions doc proactively — only do so if the user has asked for it.
- **Deferred / "backlog":** mark as deferred in the discussion. If a decisions doc exists, record it under a deferred section there; remove from active discussion.
- **"I will decide" / "not for agent":** stop investigating or proposing on that topic. Leave it user-owned; if asked to move it to the decisions doc, supply a structure with clearly unfilled values and remove the discussion section.

If a user closes a topic without answering every subquestion, honor the closure. Record only the explicit decision; put genuinely necessary remaining details into a clearly labeled user-owned placeholder rather than silently choosing them or reopening the discussion.

Preserve point numbers where prior replies refer to them. If all points are closed, leave a short notice; do not manufacture more questions to keep planning active.

## Maintain the decisions doc (only when it exists)

Write closed decisions only — no open items, no skeletons, no placeholders for undecided things. Scale structure to what has actually been agreed; no predefined sections.

When promoting a decision, write only what was explicitly agreed. Remove conflicting pending text. Avoid accumulating "latest decisions" appendices that contradict earlier entries.

Do not invent values the user reserved for themselves. A closed discussion does not mean implementation readiness: if remaining details are user-owned, leave them blank and clearly labeled.

## Scope and finishing

Document planning and agreed solution only unless the user separately requests implementation. Do not edit application code, migrations, dependencies, or deploy resources as a consequence of final approval.

Do not delete historical documents merely because this skill is active. When explicitly asked to clean docs, preserve unique useful material first and repair references after removing redundant files.

Prefer direct, focused Markdown edits. Use scripts only when their benefit justifies them; do not mechanically rewrite an open conversation. Before writing, reread affected content so new user edits are not overwritten. Verify that user messages remain intact in open sections, promoted decisions are consistent, and links resolve.

Finish briefly: name the updated documents, summarize the decisions moved, and state what remains open. Do not repeat the entire discussion in chat.
