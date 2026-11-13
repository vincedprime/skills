---
name: discuss
description: Collaborative discussion workflow where Agent and User exchange questions and answers in a discussion doc, with a decisions doc always present. Use when the user wants document-based cross-questioning, adds comments or answers to planning docs, or asks to continue this planning method. This is a discussion-first workflow, not authorization to implement application code.
---

# Discuss to design

Help the user reason through a design by exchanging questions and answers in the discussion document. The user may challenge assumptions, request first-principles explanations, make decisions, or reserve topics for themselves. Progress toward a coherent design without treating every question as a request to build.

## Two documents, always

Always create both at the start of a discussion, in the same folder, and keep them linked:

- `<topic>-discussion.md`: active open points and their conversations.
- `<topic>-decisions.md`: closed decisions only.

Create the decisions file even if nothing is agreed yet. Until the first close, it is a short header plus a link to the discussion and a line that no decisions are closed. It is never a plan for open items and never a duplicate of the discussion.

Follow existing folder conventions rather than assuming a particular repository or stack.

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
- **Explicit agreement:** remove the closed section from the discussion and add the agreed decision to the decisions doc. Approval of one paragraph does not approve every proposal in the section.
- **Partial agreement:** remove the settled part from the discussion, record it in the decisions doc, and keep the unresolved remainder open. Do not label an entire topic closed prematurely.
- **Closed:** consolidate the decision into the decisions doc, then remove the closed section from the discussion.
- **Deferred / "backlog":** record it under a deferred section in the decisions doc; remove it from active discussion.
- **"I will decide" / "not for agent":** stop investigating or proposing on that topic. Move it to the decisions doc with a clearly labeled unfilled placeholder, and remove the discussion section.

If a user closes a topic without answering every subquestion, honor the closure. Record only the explicit decision; put genuinely necessary remaining details into a clearly labeled user-owned placeholder rather than silently choosing them or reopening the discussion.

Preserve point numbers where prior replies refer to them. If all points are closed, leave a short notice; do not manufacture more questions to keep planning active.

## Maintain the decisions doc

Write closed decisions only — no open items and no outline of topics still in discussion. Scale structure to what has actually been agreed; no predefined sections. An empty starter (header, link to the discussion, "No closed decisions yet.") is required until the first close. User-owned blanks are allowed only after an explicit "I will decide".

When promoting a decision, write only what was explicitly agreed. Remove conflicting pending text. Avoid accumulating "latest decisions" appendices that contradict earlier entries.

Do not invent values the user reserved for themselves. A closed discussion does not mean implementation readiness: if remaining details are user-owned, leave them blank and clearly labeled.

## Scope and finishing

Document planning and agreed design only unless the user separately requests implementation. Do not edit application code, migrations, dependencies, or deploy resources as a consequence of design approval.

Do not delete historical documents merely because this skill is active. When explicitly asked to clean docs, preserve unique useful material first and repair references after removing redundant files.

Prefer direct, focused Markdown edits. Use scripts only when their benefit justifies them; do not mechanically rewrite an open conversation. Before writing, reread affected content so new user edits are not overwritten. Verify that user messages remain intact in open sections, promoted decisions are consistent, and links resolve.

Finish briefly: name the updated documents, summarize the decisions moved, and state what remains open. Do not repeat the entire discussion in chat.
