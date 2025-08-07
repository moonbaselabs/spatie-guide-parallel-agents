# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview
This is a Laravel/PHP project called "spatieguideagents". The repository is currently empty and awaiting Laravel project initialization.

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

## Important Notes
- This repository is currently empty. Initialize a Laravel project first before development
- Check for `.env` file configuration before running any artisan commands
- Database connection must be configured in `.env` before running migrations