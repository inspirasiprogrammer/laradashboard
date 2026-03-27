```markdown
# laradashboard Development Patterns

> Auto-generated skill from repository analysis

## Overview
This skill teaches the core development patterns and workflows used in the `laradashboard` project, a JavaScript codebase built with the Vite framework. You'll learn about the project's coding conventions, how to manage translations and releases, update dependencies, handle module statuses, and implement features with proper testing. This guide also provides step-by-step instructions for each workflow and the recommended commands to streamline your development process.

## Coding Conventions

- **File Naming:**  
  Use camelCase for file names.  
  _Example:_  
  ```
  userProfile.js
  dashboardView.jsx
  ```

- **Import Style:**  
  Use relative imports for modules within the project.  
  _Example:_  
  ```js
  import { getUser } from './userService';
  import Dashboard from '../components/dashboardView';
  ```

- **Export Style:**  
  Use named exports.  
  _Example:_  
  ```js
  // In userService.js
  export function getUser(id) { ... }
  export function updateUser(data) { ... }
  ```

- **Commit Messages:**  
  Follow the Conventional Commits format with prefixes: `fix`, `feat`, `refactor`, `chore`.  
  _Example:_  
  ```
  feat: add user profile editing modal
  fix: correct dashboard stats calculation
  ```

## Workflows

### Update Translations and Rebuild Assets
**Trigger:** When translations are added or updated, or new features require translation keys  
**Command:** `/update-translations`

1. Edit or add translation keys in all `resources/lang/*.json` files.
2. Rebuild frontend assets, updating `public/build/assets/*.css` and `public/build/manifest.json`.
3. Optionally update `README.md` and `version.json` if related to a release.

_Example:_  
```json
// resources/lang/en.json
{
  "welcome": "Welcome",
  "logout": "Log out"
}
```
```bash
npm run build
```

---

### Release Version Bump
**Trigger:** When a new release is ready to be published  
**Command:** `/release`

1. Update `README.md` with new release notes or changelog.
2. Update `version.json` with the new version number.
3. Update `package.json` and `package-lock.json` if npm dependencies or version changed.

_Example:_  
```json
// version.json
{
  "version": "1.2.0"
}
```

---

### Dependency Update via Dependabot
**Trigger:** When Dependabot detects an outdated dependency  
**Command:** `/update-dependency`

1. Update `package-lock.json` or `composer.lock` with the new dependency version.
2. Merge the automated pull request.

_Example:_  
```diff
- "vite": "^3.0.0"
+ "vite": "^4.0.0"
```

---

### Fix or Update Module Statuses
**Trigger:** When a module's status needs to be changed or a bug is found in module loading  
**Command:** `/update-module-status`

1. Edit `modules_statuses.json` to reflect new statuses.
2. Optionally update translations if related to module status messages.
3. Optionally rebuild frontend assets.

_Example:_  
```json
// modules_statuses.json
{
  "userModule": "active",
  "analyticsModule": "inactive"
}
```

---

### Feature Development with Tests and Views
**Trigger:** When developing a new feature, refactoring, or fixing a bug that affects multiple layers  
**Command:** `/feature`

1. Update or add PHP backend files (Controllers, Services, Models, etc).
2. Update or add Blade views in `resources/views`.
3. Update or add frontend JS/CSS if needed.
4. Update or add tests in `tests/Feature` or `tests/Unit`.

_Example:_  
```js
// resources/js/components/userProfile.js
export function UserProfile({ user }) { ... }
```
```php
// tests/Feature/UserProfileTest.php
public function test_user_profile_shows_correct_data() { ... }
```

## Testing Patterns

- **Test File Pattern:**  
  Test files follow the `*.test.ts` pattern for JavaScript/TypeScript tests.

- **Location:**  
  Tests are typically placed alongside source files or in dedicated test directories.

- **Example:**  
  ```ts
  // userService.test.ts
  import { getUser } from './userService';

  test('should fetch user by ID', () => {
    expect(getUser(1)).toEqual({ id: 1, name: 'Alice' });
  });
  ```

## Commands

| Command                | Purpose                                                      |
|------------------------|--------------------------------------------------------------|
| /update-translations   | Update translation files and rebuild frontend assets          |
| /release               | Prepare and release a new version                            |
| /update-dependency     | Update npm/composer dependencies (typically via Dependabot)   |
| /update-module-status  | Update or fix module loading statuses                        |
| /feature               | Implement a new feature, refactor, or fix with tests/views   |
```