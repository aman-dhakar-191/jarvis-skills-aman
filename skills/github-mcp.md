# Skill: github-mcp

Use the GitHub Tool MCP strictly for GitHub repository interactions requiring live data or direct GitHub API operations.

Use when: Aman requests repository, branch, or file inspection, updates, issue and PR management, or verification of GitHub state.

Steps:
1. Always verify repository, branch, and file existence through the GitHub Tool prior to making any write operations.
2. Prefer the GitHub Tool over the Coding Subagent exclusively for GitHub-side operations such as repository metadata queries and issue/PR state checks.
3. Never fabricate or guess about repository state, PR states, commit contents, issue statuses, or file contents; report only data verified by the GitHub Tool.
4. Explicitly list all changed paths and indicate success or failure of each action clearly.
5. Defer software engineering or implementation tasks to the Coding Subagent.
6. Adhere strictly to Supervisor gating for shell commands and file I/O operations; bypassing approval is forbidden.

Output: A concise summary of GitHub-side operation results, including verified links, IDs, and changes.

Constraints: No claim of action should be made without GitHub Tool validation. Do not invent repository or issue details. All Supervisor approval and source-of-truth rules must be followed.

---

Slash Command: /github-mcp
