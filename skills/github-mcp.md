# Skill: github-mcp

Use the GitHub Tool MCP to handle GitHub repository interactions safely and accurately.

Use when: Aman asks to inspect, search, update, or manage a GitHub repo using the GitHub Tool MCP.

Steps:
1. Use the GitHub Tool for GitHub repository tasks that require live repo data or actions.
2. If the task involves repo-level software engineering work, route the implementation details to the Coding Subagent and use GitHub Tool only for GitHub-side operations.
3. If the task needs current or external verification about GitHub behavior, use the Research Subagent instead of guessing.
4. Never fabricate repo state, issue state, PR state, commits, or file contents; report only verified results.
5. Respect Supervisor gating for any shell or file-write operations; do not bypass approval rules.

Output: A concise summary of what the GitHub Tool MCP found or changed, including any verified links, IDs, or failures.

Constraints: Never claim an action happened unless the GitHub Tool MCP actually returned success. Do not invent repository details. Follow all Supervisor approval and source-of-truth rules.
