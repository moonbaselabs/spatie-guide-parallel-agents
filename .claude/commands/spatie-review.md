---
description: Run all Spatie guideline agents in parallel to review the entire codebase
argument-hint: [optional: specific directory or file pattern]
---

Perform a comprehensive Spatie guidelines review of the codebase.

First, identify all PHP files in the project:
- If arguments provided: analyze files matching `$ARGUMENTS`
- Otherwise: find all PHP files in the project (excluding vendor/, node_modules/, storage/, bootstrap/cache/)

Then run ALL of these agents IN PARALLEL using the Task tool (all in one message with multiple tool calls):

1. **core-laravel** - Review for Laravel principles and patterns
2. **php-standards** - Check PSR compliance and type declarations  
3. **class-structure** - Analyze class design and properties
4. **control-flow** - Evaluate control flow and early returns
5. **naming** - Verify naming conventions
6. **laravel-conventions** - Check Laravel-specific features
7. **code-quality** - Assess overall code quality

IMPORTANT: You must launch all agents simultaneously in a single message using multiple Task tool invocations for parallel execution.

After all agents complete, compile a comprehensive markdown report with:

# Spatie Guidelines Compliance Report

## Executive Summary
- Overall Compliance Score (0-100)
- Total Files Analyzed
- Critical Issues Count
- Warnings Count
- Suggestions Count

## Critical Violations
List any blocking issues that MUST be fixed immediately

## File-by-File Analysis
Group findings by file with line numbers

## Category Breakdown
### Core Laravel Principles
[Aggregated findings]

### PHP Standards
[Aggregated findings]

### Class Structure
[Aggregated findings]

### Control Flow
[Aggregated findings]

### Naming Conventions
[Aggregated findings]

### Laravel Conventions
[Aggregated findings]

### Code Quality
[Aggregated findings]

## Top 10 Priority Fixes
Numbered list of the most important issues to address

## Positive Highlights
What the codebase is doing well

## Recommendations
Strategic improvements for long-term code health

Save the full report as `spatie-review-report.md` in the project root.