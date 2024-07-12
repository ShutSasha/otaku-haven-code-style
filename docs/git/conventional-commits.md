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

## Specification

> The key words “MUST”, “MUST NOT”, “REQUIRED”, “SHALL”, “SHALL NOT”, “SHOULD”, “SHOULD NOT”, “RECOMMENDED”, “MAY”, and “OPTIONAL” in this document are to be interpreted as described in [*RFC 2119*](https://www.ietf.org/rfc/rfc2119.txt).

1. Commits MUST be prefixed with a type, which consists of a noun, `feat`, `fix`, `chore`, etc., followed by the OPTIONAL scope, OPTIONAL `!`
*Symbol* - `!` *is used in Conventional Commits to indicate breaking changes. This helps developers and users of libraries or applications understand that these changes may require additional actions to adapt existing code to the new version.*, and REQUIRED terminal colon and space.

**Example for symbol `!`**
```
fix!: support for the deprecated authenticate function has been removed

BREAKING CHANGE: the authenticate function is no longer available. Use the new login function instead.
```
2. The type `feat`  MUST be used when a commit adds a new feature to your application or library.
3. The type `fix` MUST be used when a commit represents a bug fix for your application.
4. A scope MAY be provided after a type. A scope MUST consist of a noun describing a section of the codebase surrounded by parenthesis, e.g., `fix(parser): `
5. A summary description **of commit** MUST immediately follow the colon and space after the type/scope prefix. The description is a short summary of the code changes, e.g., *fix: array parsing issue when multiple spaces were contained in string*.
6. A longer commit body MAY be provided after the short description, providing additional contextual information about the code changes. The body MUST begin one blank line after the description.
7. A commit body is free-form and MAY consist of any number of newline separated paragraphs.
8. One or more footers MAY be provided one blank line after the body. Each footer MUST consist of a word token, followed by either a `:<space>` or `<space>#` separator, followed by a string value (this is inspired by the git trailer convention).

**Example below**

```
feat(auth): Added OAuth2 support

This commit adds support for OAuth2, allowing users to authenticate via Google and Facebook.
Added a new module for handling OAuth2 tokens.

BREAKING CHANGE: The old email authorization method is no longer supported.
Closes #456
Fixes #789
```
9. A footer’s token MUST use `-` in place of whitespace characters, e.g., `Acked-by` (this helps differentiate the footer section from a multi-paragraph body). An exception is made for `BREAKING CHANGE`, which MAY also be used as a token.
10. A footer’s value MAY contain spaces and newlines, and parsing MUST terminate when the next valid footer token/separator pair is observed.
11. Breaking changes MUST be indicated in the type/scope prefix of a commit, or as an entry in the footer.
12. If included as a footer, a breaking change MUST consist of the uppercase text BREAKING CHANGE, followed by a colon, space, and description, e.g., *BREAKING CHANGE: environment variables now take precedence over config files*.
13. If included in the type/scope prefix, breaking changes MUST be indicated by a `!` immediately before the `:`. If `!` is used, `BREAKING CHANGE: ` MAY be omitted from the footer section, and the commit description SHALL be used to describe the breaking change.
14. Types other than `feat` and `fix` MAY be used in your commit messages, e.g., *docs: update ref docs*.
15. The units of information that make up Conventional Commits MUST NOT be treated as case sensitive by implementors, with the exception of BREAKING CHANGE which MUST be uppercase.
16. BREAKING-CHANGE MUST be synonymous with BREAKING CHANGE, when used as a token in a footer.








