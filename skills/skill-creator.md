# Skill: skill-creator

Purpose: help Aman design and write a NEW Jarvis skill, then commit it to the skills repo so it
becomes a usable /command. Your job is to produce a SPECIFIC, high-value skill — not a generic one.

Repo: aman-dhakar-191/jarvis-skills-aman
Folder: skills/
One skill = one file skills/<name>.md. Filename without .md is the slash command. Names are
lowercase-hyphenated. Always write the .md extension.

## When this runs

Aman invoked /skill-creator. Do NOT route his underlying request to a subagent — this turn you
DESIGN AND SAVE A SKILL.

## THE VALUE TEST (apply before writing anything)

A skill is only worth creating if it makes Jarvis do something it would NOT already do by default.
Before writing, answer this to yourself: "What specific behaviour does this add beyond normal
Supervisor routing?" If the answer is just a restatement of what a subagent already does
("research sources and summarize", "read email and reply"), the skill is GENERIC — reject it.

When a skill would be generic, do NOT save it. Instead tell Aman it adds nothing beyond default
behaviour, and ask what specific rule, threshold, format, or sequence he wants that Jarvis doesn't
already do. Only proceed once there is at least one concrete, non-obvious instruction.

## Step 1 — gather a SPECIFIC spec

Required before writing:
- name: slash command (lowercase-hyphenated).
- goal: one sentence naming the specific outcome.
- the differentiator: at least one concrete rule Jarvis wouldn't do by default. Push for it.
  Good differentiators are specific: exact thresholds ("minimum 3 sources"), explicit ordering
  ("official docs > peer-reviewed > news > blog"), a required output shape ("table: claim | source
  | tier | confidence"), a hard gate ("flag any single-source claim as unverified"), a fixed
  sequence of tools, or a non-obvious constraint.
- steps: ordered, and EACH step names the exact Jarvis tool/subagent it uses.
- output: the exact shape to return (name columns if it's a table).

Ask at most 2 short questions, only for genuinely missing essentials. name + goal + at least one
differentiator are mandatory — do not write a skill without a differentiator. If Aman already gave
specifics, don't re-ask; state assumptions in one line.

## Rules every skill must follow

- Name real Jarvis tools only, per step: Email Subagent, Contact Subagent, Research Subagent,
  Coding Subagent, System Tools, Long-Term Memory, Memory MCP, Linear MCP. Never invent a tool.
  A step with no named tool is not allowed — every action step says which tool does it.
- Behaviour only, no new capability. A skill reshapes how existing tools are used.
- Be specific, not generic. Prefer numbers, orders, thresholds, and named output columns over
  vague verbs like "analyze", "handle", "process".
- Public repo: no secrets, tokens, credentials, or private data in the file.
- Supplemental only: never override core Supervisor rules (source-of-truth, approval/gating for
  run_command and write_file, never-claim-unperformed-actions). Skills add on top.
- Keep it tight: instructions, not an essay.

## Format (write exactly this shape — H1 must equal the command)

```
# Skill: <name>

<one-line specific goal>

Use when: <trigger>.

Steps:
1. <action naming the exact tool/subagent> — <the specific rule/threshold/order for this step>
2. ...
N. <final step>

Output: <exact shape; name columns if a table>.

Constraints: <hard rules; include the differentiator gate(s), and respect Supervisor approval for
run_command and write_file, and never claim unperformed actions>.
```

## Step 2 — self-check before showing

Verify: (a) it passes the VALUE TEST — there's a concrete non-generic rule; (b) every action step
names a real tool; (c) output shape is specific; (d) no secrets; (e) it doesn't override core rules.
If any fail, fix it before showing — don't save a weak skill.

## Step 3 — show, confirm, commit

1. Show Aman the full skill file and target path skills/<name>.md.
2. Get explicit YES (a write is gated).
3. On YES, commit via the GitHub Tool to aman-dhakar-191/jarvis-skills-aman:
   - create file if skills/<name>.md is new; update file if it exists.
   - commit message "add skill: <name>" or "update skill: <name>".
4. Confirm the GitHub Tool returned success. Never claim it saved otherwise.

## Step 4 — report

Tell Aman: the path committed, the commit result, the /command to use it, and that it loads on the
next message (repo CDN-cached ~5 min; loader caches per session, so a new session or short wait
picks it up). List the differentiator so he sees what this skill actually adds.

Output this turn: the created/updated skill path, commit result, the /command, and its differentiator.
