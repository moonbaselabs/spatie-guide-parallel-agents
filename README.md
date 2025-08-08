# Spatie Guidelines Agents for Claude Code

A comprehensive suite of AI agents and slash commands that enforce [Spatie's Laravel & PHP coding guidelines](https://spatie.be/guidelines/laravel-php) in your codebase.

## 🚀 Quick Start

Run a full codebase review with a single command:
```
/spatie-review
```

## 📋 Overview

This project provides 7 specialized agents and 5 slash commands that work together to ensure your Laravel/PHP code follows Spatie's industry-leading coding standards. The agents can run in parallel for maximum efficiency and provide detailed, actionable feedback.

## 🤖 Available Agents

### Core Agents

#### 1. `core-laravel`
- **Purpose**: Ensures code follows core Laravel principles and conventions
- **Checks**: Service container usage, facades, Eloquent patterns, middleware
- **When to use**: Reviewing Laravel-specific code patterns

#### 2. `php-standards`
- **Purpose**: Enforces PHP standards including PSR compliance
- **Checks**: PSR-1/2/12, type declarations, nullable syntax, docblocks
- **When to use**: Reviewing PHP code quality and standards

#### 3. `class-structure`
- **Purpose**: Analyzes class design and structure
- **Checks**: Typed properties, constructor promotion, trait usage
- **When to use**: Creating or refactoring classes

#### 4. `control-flow`
- **Purpose**: Optimizes control flow patterns
- **Checks**: Early returns, happy path, avoiding else statements
- **When to use**: Refactoring complex conditionals

#### 5. `naming`
- **Purpose**: Ensures correct naming conventions
- **Checks**: Classes, methods, variables, routes, files, database
- **When to use**: Creating new files or reviewing naming consistency

#### 6. `laravel-conventions`
- **Purpose**: Enforces Laravel-specific conventions
- **Checks**: Routes, controllers, commands, configuration, validation
- **When to use**: Implementing Laravel features

#### 7. `code-quality`
- **Purpose**: Overall code quality and maintainability (PROACTIVE)
- **Checks**: Readability, duplications, comments, formatting
- **When to use**: After writing code or reviewing existing code

### Orchestrator Agent

#### `spatie-review`
- **Purpose**: Runs all agents in parallel and produces comprehensive report
- **Output**: Structured markdown report with compliance scores
- **When to use**: Full codebase reviews or major refactoring

## ⚡ Slash Commands

### `/spatie-review` - Full Codebase Analysis
```
/spatie-review [optional: directory or pattern]
```
- Runs all 7 agents in parallel
- Analyzes entire codebase (excludes vendor/, node_modules/)
- Generates comprehensive compliance report
- Saves report as `spatie-review-report.md`

**Example outputs:**
- Executive summary with compliance score
- Critical violations requiring immediate attention
- File-by-file analysis with line numbers
- Prioritized recommendations

### `/spatie-quick` - Quick Check
```
/spatie-quick [file or pattern]
```
- Runs 3 critical agents (naming, control-flow, php-standards)
- Fast feedback for rapid development
- Concise, actionable output

**Best for:**
- Pre-commit checks
- Quick validation during development
- Focused file reviews

### `/spatie-fix` - Auto-fix Violations
```
/spatie-fix [file or directory]
```
- Automatically fixes common violations
- Safe refactoring only
- Shows summary of changes

**Automatic fixes include:**
- Convert `Type|null` to `?Type` notation
- Add missing `void` return types
- Fix method naming (PascalCase to camelCase)
- Convert string concatenation to interpolation
- Remove unnecessary else statements
- Fix controller names to plural
- Update config files to kebab-case

### `/spatie-controller` - Controller Helper
```
/spatie-controller [controller name or path]
```
- Reviews existing controllers
- Creates new controllers with proper structure
- Ensures CRUD compliance

**Features:**
- Proper plural naming
- Standard CRUD methods
- Type hints and return types
- Form request validation
- Early return patterns

### `/spatie-refactor` - Deep Refactoring
```
/spatie-refactor [file or class]
```
- Uses extended thinking for complex refactoring
- Creates step-by-step refactoring plan
- Shows before/after comparisons

**Refactoring includes:**
- Extract complex methods
- Implement early returns
- Add type declarations
- Constructor property promotion
- Extract to service classes
- Improve error handling

## 🎯 Usage Examples

### Example 1: Review Entire Project
```
/spatie-review
```
Analyzes all PHP files and generates a full compliance report.

### Example 2: Quick Check Before Commit
```
/spatie-quick app/Http/Controllers/UserController.php
```
Fast validation of specific file with immediate feedback.

### Example 3: Auto-fix a Directory
```
/spatie-fix app/Models/
```
Automatically fixes common issues in all model files.

### Example 4: Create New Controller
```
/spatie-controller PostsController
```
Generates a new controller following all guidelines.

### Example 5: Refactor Complex Class
```
/spatie-refactor app/Services/PaymentService.php
```
Deep analysis and refactoring with detailed plan.

## 🔄 Running Agents in Parallel

You can manually run multiple agents in parallel using Claude Code's Task tool:

```
Please run these agents in parallel on UserController.php:
- core-laravel
- php-standards
- naming
- control-flow
```

Claude Code will execute all agents simultaneously and aggregate results.

## 📊 Report Structure

The comprehensive report includes:

```markdown
# Spatie Guidelines Compliance Report

## Executive Summary
- Overall Compliance: 85/100
- Critical Issues: 3
- Warnings: 12
- Suggestions: 8

## Critical Violations
1. Using env() outside config files (UserController.php:15)
2. Missing validation (UserController.php:37)
3. Method using PascalCase (UserController.php:35)

## Category Breakdown
[Detailed findings by category]

## Top Priority Fixes
[Numbered list of most important issues]

## Recommendations
[Strategic improvements]
```

## 🛠️ Installation

The agents and commands are already configured in this project:

```
.claude/
├── agents/
│   ├── class-structure.md
│   ├── code-quality.md
│   ├── control-flow.md
│   ├── core-laravel.md
│   ├── laravel-conventions.md
│   ├── naming.md
│   ├── php-standards.md
│   └── spatie-review.md
└── commands/
    ├── spatie-controller.md
    ├── spatie-fix.md
    ├── spatie-quick.md
    ├── spatie-refactor.md
    └── spatie-review.md
```

## 📚 Guidelines Coverage

These agents enforce the following Spatie guidelines:

### PHP Standards
- PSR-1, PSR-2, PSR-12 compliance
- Type declarations and nullable syntax
- Constructor property promotion
- Trait usage patterns

### Laravel Conventions
- Resource controller patterns
- Route naming and structure
- Configuration management
- Validation patterns
- Artisan commands

### Code Quality
- Early returns and happy path
- Avoiding else statements
- String interpolation over concatenation
- Expressive code over comments
- Proper whitespace and formatting

### Naming Conventions
- Controllers: Plural + Controller
- Models: Singular PascalCase
- Methods/Variables: camelCase
- Routes: kebab-case URLs, camelCase names
- Config: kebab-case files, snake_case keys
- Database: snake_case tables and columns

## 🔍 Customization

### Adding Custom Agents

Create a new agent in `.claude/agents/`:

```markdown
---
name: custom-agent
description: Description of when to use
tools: Read, Edit, Grep
---

Agent prompt and instructions...
```

### Adding Custom Commands

Create a new command in `.claude/commands/`:

```markdown
---
description: Command description
argument-hint: [expected arguments]
---

Command instructions...
```

## 📈 Best Practices

1. **Regular Reviews**: Run `/spatie-review` weekly or before major releases
2. **Pre-commit Checks**: Use `/spatie-quick` before committing code
3. **Incremental Fixes**: Use `/spatie-fix` to clean up technical debt gradually
4. **New Development**: Use `/spatie-controller` when creating new controllers
5. **Refactoring**: Use `/spatie-refactor` for complex refactoring tasks

## 🤝 Contributing

These agents are based on [Spatie's Laravel & PHP Guidelines](https://spatie.be/guidelines/laravel-php). To update or improve them:

1. Review the latest Spatie guidelines
2. Update agent definitions in `.claude/agents/`
3. Test with sample code
4. Document changes

## 📖 Resources

- [Spatie Guidelines](https://spatie.be/guidelines/laravel-php)
- [Claude Code Documentation](https://docs.anthropic.com/en/docs/claude-code)
- [Laravel Best Practices](https://laravel.com/docs)

## 🎉 Getting Started

1. Open your Laravel project in Claude Code
2. Run `/spatie-review` for a full analysis
3. Review the generated report
4. Use `/spatie-fix` to auto-fix simple issues
5. Address critical violations manually
6. Use specific agents for focused improvements

---

*These agents help maintain consistent, high-quality code following Spatie's battle-tested guidelines for Laravel and PHP development.*