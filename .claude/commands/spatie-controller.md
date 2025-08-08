---
description: Review or create a controller following Spatie guidelines
argument-hint: [controller name or file path]
---

Review an existing controller or create a new one following Spatie guidelines.

If file exists at $ARGUMENTS:
- Run **laravel-conventions** agent to check controller structure
- Run **naming** agent to verify naming
- Run **control-flow** agent for method optimization
- Suggest improvements

If creating new controller named $ARGUMENTS:
- Generate a resource controller with proper:
  - Plural naming (e.g., PostsController)
  - CRUD methods (index, create, store, show, edit, update, destroy)
  - Type hints and return types
  - Form request validation
  - Early return patterns
  - Proper dependency injection

Example structure following Spatie guidelines with:
- Constructor property promotion
- Typed properties
- Array validation notation
- Resource responses
- Proper error handling