---
name: llm-handoff
description: 
  Creates structured Obsidian notes from LLM conversations — decisions, insights, actions,
  references, prompts/workflows, and full handoff summaries. Use this skill whenever Jason says
  "create a handoff", "make a note", "save this", "capture this decision", "log this insight",
  "write this up for Obsidian", or any variation of wanting to preserve LLM conversation output
  as a durable note. Always use this skill — do not improvise a format — when the intent is to
  produce a markdown file for Jason's Obsidian vault. This includes mid-conversation captures
  ("save this insight") and end-of-conversation summaries ("wrap this up").
---

# LLM → Handoff Skill

## Core Principle

Chat, projects, and cowork/coding are places where work happens. Obsidian is the durable memory and accountability layer.
This skill bridges the two by producing structured markdown files Jason can drop into his vault.

**Never save full transcripts.** Produce structured artifacts only.

## Vault Filing Locations

| Note Type        | Vault Location                    | Tag                |
|------------------|-----------------------------------|--------------------|
| Decision         | `00.05 LLM work and summaries`    | `llm_decision`     |
| Insight          | `00.05 LLM work and summaries`    | `llm_insight`      |
| Action           | `00.05 LLM work and summaries`    | `llm_action`       |
| Reference        | `00.05 LLM work and summaries`    | `llm_reference`    |
| Prompt/Workflow  | `00.05 LLM work and summaries`    | `llm_prompt`       |
| Handoff Summary  | `02.01 Inbox`                     | `llm_summaries`    |

---

## Workflow

### Step 1 — Identify the note type

When Jason says "create a handoff" or "make a note" without specifying a type, ask:

> "What type of note? Decision, Insight, Action, Reference, Prompt/Workflow, or full Handoff Summary?"

If the type is already clear from context (e.g., "save this decision"), skip the question.

### Step 2 — Gather missing fields

Before generating the note, check what information is available from the conversation.
Ask only for fields that are genuinely missing and that Jason can't easily fill in later.
Ask Jason if this is a follow-up to an existing project, note, or decision. If it is, ask for the relevant project name or note or a copy of the previous handoff note to link to and reference.
Do not ask for everything upfront — prefer a complete draft with [placeholder] over an interrogation.

**Always infer from conversation context:**
- Title (from the main topic)
- Date (today's date)
- LLM model (from system context if available)
- Project link (ask if not obvious — "Is this connected to a specific project note?")

### Step 3 — Generate the note

Use the appropriate template from the `assets/` folder (see below).
Fill in all fields you can from the conversation. Use `[add]` for fields Jason should complete.
If the note is a follow-up to an existing project or note, include a link to that project/note in the "Project Link" field and reference it in the body of the note. Include a timeline indicating major changes from the previous note if relevant.
Output the note as a markdown code block so it's easy to copy.

### Step 4 — Offer the file

After displaying the note inline, offer to save it as a `.md` file Jason can download.

---

## Templates

See `assets/` for all templates:

- `decision.md` — Strategic choice, commitment, or prioritization
- `insight.md` — Durable realization or conceptual connection
- `action.md` — Next steps to take outside of chat
- `reference.md` — Source summaries, citations, factual background
- `prompt.md` — Reusable prompts or workflows that reliably produce good results
- `handoff.md` — Full end-of-conversation summary (use when wrapping up a substantial session)

**Which template to use:**

| User says...                                      | Template       |
|---------------------------------------------------|----------------|
| "I decided to..." / "capture this decision"       | decision.md    |
| "save this insight" / "I realized..."             | insight.md     |
| "log these actions" / "what do I need to do"      | action.md      |
| "save this source" / "reference note"             | reference.md   |
| "save this prompt" / "this workflow works"        | prompt.md      |
| "wrap this up" / "create a handoff" (no type)     | handoff.md     |

---

## Quality Checks

Before outputting the note:
- [ ] All frontmatter fields filled or marked `[add]`
- [ ] No full transcript pasted — only structured extraction
- [ ] A project link is included or explicitly noted as N/A
- [ ] The Risks / Warnings / Verification flags section is filled if relevant
- [ ] The note would be useful in 6 months without reading the original chat