---
name: init
description: Initialize a new CLAUDE.md file with codebase documentation, then split into rule files
---

Please analyze this codebase and create a `.claude/CLAUDE.md` file, which will be given to future instances of Claude Code to operate in this repository.

What to add:
1. Commands that will be commonly used, such as how to build, lint, and run tests. Include the necessary commands to develop in this codebase, such as how to run a single test.
2. High-level code architecture and structure so that future instances can be productive more quickly. Focus on the "big picture" architecture that requires reading multiple files to understand.

Usage notes:
- Write CLAUDE.md to `.claude/CLAUDE.md`, NOT to the project root. Claude Code automatically discovers it there.
- Do NOT create or modify CLAUDE.md in the project root directory. All documentation goes to `.claude/`.
- If there's already a CLAUDE.md (at project root or `.claude/CLAUDE.md`), suggest improvements to it.
- If CLAUDE.md exists in both locations (project root and `.claude/`), delete the one in the project root directory and keep only `.claude/CLAUDE.md`.
- When you make the initial CLAUDE.md, do not repeat yourself and do not include obvious instructions like "Provide helpful error messages to users", "Write unit tests for all new utilities", "Never include sensitive information (API keys, tokens) in code or commits".
- Avoid listing every component or file structure that can be easily discovered.
- Don't include generic development practices.
- If there are Cursor rules (in .cursor/rules/ or .cursorrules) or Copilot rules (in .github/copilot-instructions.md), make sure to include the important parts.
- If there is a README.md, make sure to include the important parts.
- Do not make up information such as "Common Development Tasks", "Tips for Development", "Support and Documentation" unless this is expressly included in other files that you read.
- Be sure to prefix the file with the following text:

```
# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.
```

After creating CLAUDE.md, split it into focused rule files under `.claude/rules/` (one topic per file). Then rewrite CLAUDE.md as overview + `@rules/xxx.md` imports.

Rule file format:
- Rules are plain Markdown files with optional YAML frontmatter.
- The ONLY supported frontmatter field is `paths` (an array of glob patterns).
- Do NOT use `description`, `globs`, or any other frontmatter fields — those are not valid for rules.
- Rules WITHOUT `paths` load unconditionally at session start (use for project-wide knowledge like architecture overview).
- Rules WITH `paths` load only when Claude works with matching files (use for language/framework-specific conventions).
- Example of a file-type-specific rule:
  ```markdown
  ---
  paths:
    - "**/*.java"
  ---
  # content here
  ```
- Example of a global rule (no frontmatter at all, or empty frontmatter):
  ```markdown
  # content here
  ```
