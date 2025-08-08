# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview
This is a Laravel/PHP project called "spatie-guidelines-parallel-agents" that includes a comprehensive suite of Spatie guideline enforcement agents and slash commands for code quality.

## Initial Setup Commands
When the Laravel project is initialized, use these commands:

```bash
# Install PHP dependencies
composer install

# Install Node.js dependencies (if package.json exists)
npm install

# Copy environment file
cp .env.example .env

# Generate application key
php artisan key:generate

# Run database migrations
php artisan migrate

# Start development server
php artisan serve
```

## Common Development Commands
Once the Laravel project is set up:

```bash
# Run tests
php artisan test
# or
./vendor/bin/phpunit

# Run specific test
php artisan test --filter TestName

# Clear caches
php artisan cache:clear
php artisan config:clear
php artisan route:clear
php artisan view:clear

# Database operations
php artisan migrate:fresh --seed  # Reset database and seed
php artisan db:seed               # Run seeders only

# Asset compilation (if using Laravel Mix/Vite)
npm run dev    # Development build
npm run watch  # Watch for changes
npm run build  # Production build

# Code formatting and linting (if configured)
./vendor/bin/pint  # Laravel Pint for PHP formatting
```

## Expected Architecture
When fully initialized, this Laravel project will follow standard Laravel conventions:

- **MVC Pattern**: Models in `app/Models/`, Controllers in `app/Http/Controllers/`, Views in `resources/views/`
- **Service Layer**: Business logic should be extracted into Service classes in `app/Services/`
- **Database**: Eloquent ORM with migrations in `database/migrations/`
- **Testing**: Feature tests in `tests/Feature/`, Unit tests in `tests/Unit/`
- **API**: If building an API, routes in `routes/api.php` with API resources and controllers

## Development Guidelines
- Follow Laravel naming conventions and best practices
- Use Eloquent relationships for database queries
- Implement form request validation for input validation
- Use Laravel's built-in authentication if needed
- Keep controllers thin, move business logic to services
- Write tests for new features and bug fixes

## Spatie Guidelines Enforcement

This project includes specialized agents and slash commands that enforce Spatie's Laravel & PHP coding guidelines:

### Available Slash Commands
- `/spatie-review` - Run full codebase analysis with all agents in parallel
- `/spatie-quick [file]` - Quick check with critical agents
- `/spatie-fix [path]` - Auto-fix common violations
- `/spatie-controller [name]` - Create or review controllers
- `/spatie-refactor [file]` - Deep refactoring with extended thinking

### Available Agents (in .claude/agents/)
1. **core-laravel** - Laravel principles and patterns
2. **php-standards** - PSR compliance and type declarations
3. **class-structure** - Class design and properties
4. **control-flow** - Early returns and happy path
5. **naming** - Comprehensive naming conventions
6. **laravel-conventions** - Laravel-specific features
7. **code-quality** - Overall code maintainability (PROACTIVE)
8. **spatie-review** - Orchestrator that runs all agents in parallel

### How to Use
- For full analysis: `/spatie-review`
- For quick checks: `/spatie-quick UserController.php`
- For auto-fixes: `/spatie-fix app/Models/`
- To run specific agents: Use Task tool with subagent_type parameter
- Agents can be run in parallel for efficiency

### Key Spatie Guidelines Enforced
- PSR-1, PSR-2, PSR-12 compliance
- Short nullable notation (?Type instead of Type|null)
- Void return types when methods return nothing
- Typed properties over docblocks
- Constructor property promotion when possible
- Early returns (happy path last)
- Avoid else statements
- Controllers use plural names
- Routes use kebab-case URLs, camelCase names
- Config files use kebab-case, keys use snake_case
- No env() calls outside config files
- Array notation for validation rules

See SPATIE-AGENTS-GUIDE.md for complete documentation.

## Important Notes
- The Spatie agents and slash commands are ready to use immediately
- Check for `.env` file configuration before running any artisan commands
- Database connection must be configured in `.env` before running migrations
- Run `/spatie-review` regularly to maintain code quality
- Agents can identify issues but won't modify code unless using `/spatie-fix`