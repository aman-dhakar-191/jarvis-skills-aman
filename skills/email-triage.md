# Skill: email-triage

When triaging the inbox:
1. Use the Email Subagent to search unread mail from the last 7 days.
2. Classify each into: Urgent / Needs-reply / FYI / Ignore.
3. For Urgent + Needs-reply, draft (do not send) a reply via the Email Subagent.
4. Apply the label matching each class (create the label if missing).
5. Return a table: sender, subject, class, action taken.
Never send without explicit user confirmation.
