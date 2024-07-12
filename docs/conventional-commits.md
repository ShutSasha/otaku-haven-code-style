# Conventional commits ⚡

[Return to Table of Contents](../README.md)

## Summary
The Conventional Commits specification is a lightweight convention on top of commit messages. It provides an easy set of rules for creating an explicit commit history; which makes it easier to write automated tools on top of. 

## The commit structure should be smth like this:

```
<type>[optional scope]: <description>
 
[optional body]

[optional footer(s)]
```

### What is `type` how to use it?
The key function of a commit type is to describe the nature of changes made to the codebase, thereby making those changes easier to understand, navigate, and manage.

### List of Commit Types

1. **feat:** A new feature for the user.
    ```plaintext
    feat: add user authentication via social media
    ```

2. **fix:** A bug fix.
    ```plaintext
    fix: resolve login issue on mobile devices
    ```

3. **docs:** Documentation only changes.
    ```plaintext
    docs: update README with new API usage examples
    ```

4. **style:** Changes that do not affect the meaning of the code (white-space, formatting, missing semi-colons, etc).
    ```plaintext
    style: correct indentation in the main.js file
    ```

5. **refactor:** A code change that neither fixes a bug nor adds a feature.
    ```plaintext
    refactor: reorganize user service for better readability
    ```

6. **perf:** A code change that improves performance.
    ```plaintext
    perf: optimize image loading for faster page render
    ```

7. **test:** Adding missing tests or correcting existing tests.
    ```plaintext
    test: add unit tests for the authentication module
    ```

8. **build:** Changes that affect the build system or external dependencies (example scopes: gulp, broccoli, npm).
    ```plaintext
    build: update webpack configuration to improve build speed
    ```

9. **ci:** Changes to our CI configuration files and scripts (example scopes: Travis, Circle, BrowserStack, SauceLabs).
    ```plaintext
    ci: add GitHub Actions workflow for automated testing
    ```

10. **chore:** Other changes that don't modify src or test files.
    ```plaintext
    chore: update dependencies to latest versions
    ```

11. **revert:** Reverts a previous commit.
    ```plaintext
    revert: revert commit 9f6d1a2 due to breaking changes
    ```

12. **merge:** Merging branches.
    ```plaintext
    merge: merge feature/login into main
    ```

13. **hotfix:** A quick fix to address critical issues.
    ```plaintext
    hotfix: fix critical bug in the payment processing module
    ```

14. **config:** Changes in configuration files.
    ```plaintext
    config: update ESLint rules for better code quality
    ```

15. **assets:** Changes in static files (images, fonts, etc).
    ```plaintext
    assets: add new logo assets for the marketing campaign
    ```

16. **i18n:** Changes related to internationalization and localization.
    ```plaintext
    i18n: add support for French language
    ```

17. **security:** Changes that improve security.
    ```plaintext
    security: fix security vulnerability in user authentication
    ```

### Detailed Examples

#### feat:
A new feature for the user.
```plaintext
feat: add user authentication via social media

Implemented OAuth2 for Facebook, Google, and Twitter.
```

#### fix:
A bug fix.
```plaintext
fix: resolve login issue on mobile devices

Fixed a bug where login was not working on iOS devices.
```

#### docs:
Documentation only changes.
```plaintext
docs: update README with new API usage examples

Added examples for the new endpoints introduced in v2.0.
```

#### style:
Changes that do not affect the meaning of the code (white-space, formatting, missing semi-colons, etc).
```plaintext
style: correct indentation in the main.js file

Reformatted the file to follow the project's style guide.
```

#### refactor:
A code change that neither fixes a bug nor adds a feature.
```plaintext
refactor: reorganize user service for better readability

Separated logic into smaller functions for better maintainability.
```

#### perf:
A code change that improves performance.
```plaintext
perf: optimize image loading for faster page render

Reduced the size of images and implemented lazy loading.
```

#### test:
Adding missing tests or correcting existing tests.
```plaintext
test: add unit tests for the authentication module

Covered edge cases and increased code coverage to 95%.
```

#### build:
Changes that affect the build system or external dependencies.
```plaintext
build: update webpack configuration to improve build speed

Enabled caching and parallel processing in webpack.
```

#### ci:
Changes to our CI configuration files and scripts.
```plaintext
ci: add GitHub Actions workflow for automated testing

Configured tests to run on every push to the main branch.
```

#### chore:
Other changes that don't modify src or test files.
```plaintext
chore: update dependencies to latest versions

Updated several npm packages to their latest versions.
```

#### revert:
Reverts a previous commit.
```plaintext
revert: revert commit 9f6d1a2 due to breaking changes

This reverts commit 9f6d1a2 which caused issues in production.
```

#### merge:
Merging branches.
```plaintext
merge: merge feature/login into main

Integrated the login feature branch into the main branch.
```

#### hotfix:
A quick fix to address critical issues.
```plaintext
hotfix: fix critical bug in the payment processing module

Resolved an issue that was causing payments to fail.
```

#### config:
Changes in configuration files.
```plaintext
config: update ESLint rules for better code quality

Adjusted rules to enforce stricter code standards.
```

#### assets:
Changes in static files (images, fonts, etc).
```plaintext
assets: add new logo assets for the marketing campaign

Included new SVG and PNG files for the upcoming marketing campaign.
```

#### i18n:
Changes related to internationalization and localization.
```plaintext
i18n: add support for French language

Translated all user interface strings to French.
```

#### security:
Changes that improve security.
```plaintext
security: fix security vulnerability in user authentication

Addressed an issue where user sessions were not properly invalidated.
```

By following these conventions, we ensure that our commit history is clear, informative, and useful for both human readers and automated tools.
