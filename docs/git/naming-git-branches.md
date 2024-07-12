# Overview 

Apart from having good Git Branching Strategies, it is important to follow some naming conventions to ensure proper maintenance of the repository and a clear, structured way of separating tasks. To avoid confusions and have an organised overview of every feature that is being worked on

# Structure of branch name

> < > - MUST
> 
> [ ] - optional 

```
<type>/[optional scope]/[optional subscope]/<description>
```

## 1. Use Separators

When writing a branch name, using separators such as hyphen `-` or slash `/` helps to increase readability of the name. But remember to be consistent with the chosen separator for all branches names.

> We are using this one separator `/`, because we believe it helps to clearly distinguish between different names.

### Example

```
feat/server/notification-crud
```

## 2. Start Name with Category Word

It is recommended to begin the name of a branch with a category word, which indicates the type of task that is being solved with that branch. Some of the most used category words are:

### List of Branch Types

1. **feat**: Feature development
    ```plaintext
    feat/user-authentication
    ```

2. **fix**: Bug fixes
    ```plaintext
    fix/login-issue
    ```

3. **docs**: Documentation updates
    ```plaintext
    docs/update-readme
    ```

4. **style**: Code style changes (formatting, whitespace, etc.)
    ```plaintext
    style/refactor-indentation
    ```

5. **refactor**: Code refactoring (non-functional changes)
    ```plaintext
    refactor/improve-data-processing
    ```

6. **perf**: Performance improvements
    ```plaintext
    perf/optimize-image-loading
    ```

7. **test**: Adding or updating tests
    ```plaintext
    test/add-auth-tests
    ```

8. **build**: Changes that affect the build system or external dependencies
    ```plaintext
    build/update-webpack-config
    ```

9. **ci**: Changes to CI/CD configuration
    ```plaintext
    ci/add-github-actions
    ```

10. **chore**: Routine tasks and other changes that do not modify src or test files significantly (e.g., small changes, removing logs, correcting typos, updating dependencies).
    ```plaintext
    chore/update-dependencies
    ```

11. **revert**: Reverting changes
    ```plaintext
    revert/revert-login-feature
    ```

12. **merge**: Merging branches
    ```plaintext
    merge/feature-login-to-main
    ```

13. **hotfix**: Critical hotfixes
    ```plaintext
    hotfix/fix-payment-bug
    ```

14. **config**: Configuration changes
    ```plaintext
    config/update-eslint-rules
    ```

15. **assets**: Changes to static files (images, fonts, etc.)
    ```plaintext
    assets/add-new-logo
    ```

16. **i18n**: Internationalization and localization changes
    ```plaintext
    i18n/add-french-language
    ```

17. **security**: Security improvements
    ```plaintext
    security/fix-auth-vulnerability
    ```

### Detailed Examples

#### feat:
```plaintext
feat/add-user-authentication
```

#### fix:
```plaintext
fix/login-page-crash
```

#### wip:
```plaintext
wip/451/optimize-data-analysis
```

#### docs:
```plaintext
docs/update-installation-guide
```

#### style:
```plaintext
style/fix-code-formatting
```

#### refactor:
```plaintext
refactor/restructure-user-service
```

#### perf:
```plaintext
perf/optimize-loading-speed
```

#### test:
```plaintext
test/coverage-improvements
```

#### build:
```plaintext
build/webpack-upgrade
```

#### ci:
```plaintext
ci/travis-setup
```

#### chore:
```plaintext
chore/clean-up-dependencies
```

#### revert:
```plaintext
revert/revert-feature-x
```

#### merge:
```plaintext
merge/feature-x-into-main
```

#### hotfix:
```plaintext
hotfix/fix-critical-issue
```

#### config:
```plaintext
config/update-build-settings
```

#### assets:
```plaintext
assets/add-new-icons
```

#### i18n:
```plaintext
i18n/translate-to-spanish
```

#### security:
```plaintext
security/update-auth-mechanism
```

By using these category words to name your branches, you can clearly communicate the purpose of each branch and make your project more organized and manageable.

## 3. Use the ID of the issue

Using the ID of the related issue in the branch name makes it easy to identify the task and keep track of its progress.

### Example

```plaintext
wip/451/optimize-data-analysis
```

## 4. Avoid Using Numbers Only

It’s not a good practice to name a branch by only using numbers, because it creates confusion and increases chances of making mistakes. Instead, combine ID of issues with key words for the respective task.

## 5. Avoid Long Branch Names

As much as the branch name needs to be informative, it also needs to be precise and short. Detailed and long names can affect readability and efficiency.

## 6. Be Consistent

Consistency is key. After choosing one or more conventions, stick to them throughout the project.

## Summary 

- Keep it short and concise, but make sure to include relevant key words.
- Use category words to easily identify the type of the task.
- Include ID of related issues to help tracking of progress.
- Adding the name of the author helps to keep track of shared work. `[optional]`
- Keep the same name conventions for the whole project.
