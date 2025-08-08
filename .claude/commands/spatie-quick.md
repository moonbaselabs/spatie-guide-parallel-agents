---
description: Quick Spatie check on current file or specified files
argument-hint: [file path or pattern]
---

Run a quick Spatie guidelines check on specific files.

Target files: $ARGUMENTS (or currently open file if no arguments)

Use the Task tool to run these critical agents in parallel:
1. **naming** - Check naming conventions
2. **control-flow** - Check control flow patterns  
3. **php-standards** - Check PHP standards

Provide a concise summary of:
- Violations found (with file:line references)
- Quick fixes that can be applied immediately
- Any critical issues

Keep the output brief and actionable.