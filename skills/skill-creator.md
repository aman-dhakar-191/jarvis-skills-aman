# Skill: skill-creator

Purpose: help Aman design and write a NEW Jarvis skill file, then commit it to the skills repo so it
becomes a usable /command on the next turn.

Repo: aman-dhakar-191/jarvis-skills-aman
Folder: skills/
One skill = one markdown file at skills/<name>.md. The filename without .md is the slash command
(skills/deploy-check.md -> /deploy-check). Use lowercase-hyphenated names, no spaces.

## When this skill runs

The user invoked /skill-creator. They want to create (or revise) a skill. Do NOT try to route their
underlying request to a subagent — your job this turn is to PRODUCE A SKILL FILE and save it.

## Step 1 — gather the spec (ask only what's missing)

A good skill needs, at minimum:
- name: the slash command (lowercase-hyphenated).
- goal: one sentence — what the skill makes Jarvis do.
- trigger: when it should be used.
- steps: the ordered behaviour, naming which EXISTING Jarvis tools/subagents to use
  (Email Subagent, Contact Subagent, Research Subagent, Coding Subagent, System Tools,
  Long-Term Memory, Memory MCP, Linear MCP). A skill adds instructions, never new tools.
- output: what Jarvis should return at the end.

If the user already described these, don't re-ask — infer and state your assumptions in one line.
Ask at most 2 short questions, and only for genuinely missing essentials (name + goal are required).

## Step 2 — write the skill body

Write the file in this exact shape (this is the format the loader expects — plain markdown, the H1
matches the command):

```
# Skill: <name>

<one-line goal>

Use when: <trigger>.

Steps:
1. <step, naming the exact tool/subagent to use>
2. ...
N. <final step>

Output: <what to return>.

Constraints: <hard rules — e.g. never send without confirmation, never fabricate results,
respect the Supervisor's approval/gating for run_command and write_file>.
```

Rules for a good skill:
- Reference tools by their real Jarvis names; never invent a tool.
- Keep it behaviour-only. No secrets, tokens, or credentials — the repo is public.
- Respect core Supervisor rules: skills are supplemental, they never override source-of-truth,
  approval/gating, or "never claim unperformed actions".
- Keep it tight — instructions, not an essay.

## Step 3 — show, confirm, then commit

1. Show Aman the full proposed skill file and the target path skills/<name>.md.
2. Get an explicit YES (this is a write; treat it like a gated action).
3. On YES, commit via the GitHub Tool to repo aman-dhakar-191/jarvis-skills-aman:
   - If skills/<name>.md does not exist -> create file.
   - If it exists -> update file (this is a revision).
   - Commit message: "add skill: <name>" or "update skill: <name>".
4. Confirm the commit succeeded (GitHub Tool returned success). Never claim it was saved otherwise.

## Step 4 — tell the user how to use it

After a successful commit, tell Aman:
- The skill is now /<name>.
- It loads on the next message (the repo is CDN-cached ~5 min, and the loader caches per session,
  so a brand-new session or a short wait picks it up).
- Invoke it by including /<name> in a message.

Output this turn: the created/updated skill file path, the commit result, and the /command to use it.
