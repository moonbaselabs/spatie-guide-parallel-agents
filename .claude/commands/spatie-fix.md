---
description: Automatically fix common Spatie guideline violations
argument-hint: [file path or directory]
---

Automatically fix common Spatie guideline violations in the specified files.

Target: $ARGUMENTS (or current directory if not specified)

Steps:
1. First run a quick analysis using the **code-quality** and **naming** agents
2. Automatically fix these issues:
   - Convert `Type|null` to `?Type` notation
   - Add missing void return types
   - Fix method naming from PascalCase to camelCase
   - Convert string concatenation to interpolation
   - Remove unnecessary else statements (convert to early returns)
   - Fix controller names to plural
   - Update config file names to kebab-case
   - Add type declarations where obvious

3. Show a summary of:
   - Files modified
   - Fixes applied
   - Issues that require manual intervention

IMPORTANT: Only make safe, automated fixes. Flag complex refactoring for manual review.