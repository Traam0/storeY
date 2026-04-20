Here is your **improved Markdown** with the content from the Conventional Commits guide integrated cleanly into your workflow rules (without making it messy or redundant). I also aligned terminology so everything is consistent across branches, PRs, and commits.

---

# Git Workflow and Contribution Rules

---

## 1. Feature Branch Workflow (Manually Enforced)

GitHub does not enforce feature branch usage automatically. This workflow is enforced through team discipline and code review practices.

---

### Step 1: Create a Feature Branch from `dev`

All new work must originate from the `dev` branch.

```bash
git checkout dev
git checkout -b feature/<feature-name>
```

**Example:**

```bash
git checkout -b feature/auth-login
```

---

### Step 2: Work Only Inside the Feature Branch

* All commits must be made within the feature branch
* Commits must follow **Conventional Commits style (required)**
* Commits should be small, atomic, and meaningful
* Direct commits to `dev` or `main` are not allowed

---

## 2. Commit Message Convention (Required)

This project follows **Conventional Commits** as defined in:
[https://gist.github.com/qoomon/5dfcdf8eec66a051ecd85625518cfd13](https://gist.github.com/qoomon/5dfcdf8eec66a051ecd85625518cfd13) ([Gist][1])

---

### Commit Format

```bash
<type>(<optional scope>): <description>
```

Optional body and footer allowed:

```bash
<type>(<scope>): <description>

<body>

<footer>
```

---

### Allowed Commit Types

| Type       | Purpose                                     |
| ---------- | ------------------------------------------- |
| `feat`     | New feature                                 |
| `fix`      | Bug fix                                     |
| `refactor` | Code restructuring without behavior change  |
| `perf`     | Performance improvement                     |
| `style`    | Formatting / style only (no logic change)   |
| `test`     | Adding or updating tests                    |
| `docs`     | Documentation only                          |
| `build`    | Build system / dependencies                 |
| `chore`    | Maintenance tasks (config, gitignore, etc.) |
| `ops`      | CI/CD, infrastructure, deployment           |

---

### Rules for Commit Messages

* Use **imperative present tense**: “add” not “added”
* Do not capitalize the first letter of the description
* No trailing period in the subject line
* Keep commits focused on a single change
* Do not mix unrelated changes in one commit

---

### Breaking Changes

If a commit introduces a breaking change:

```bash
feat(api)!: remove legacy auth endpoint

BREAKING CHANGE: legacy authentication endpoint has been removed
```

---

### Examples

```bash
feat(auth): add login with email and password
fix(cart): prevent duplicate item addition
refactor(api): simplify user service logic
docs: update installation instructions
```

---

## 3. Push Feature Branch

```bash
git push origin feature/<feature-name>
```

---

## 4. Pull Request Workflow

All changes must go through a pull request:

```text
feature/* → dev
```

---

### PR Requirements

Before review:

* Clear PR description is required
* Testing steps must be included
* Related issue must be referenced (if applicable)

---

## 5. Pull Request Review Rules

### Step 1: Code Review

* Provide clear, constructive feedback
* Identify bugs, edge cases, and design issues
* Request changes when necessary

---

### Step 2: Approval Criteria

A PR can only be approved if:

* Functionality works as expected
* Code is clean and maintainable
* Requirements are fully met
* No critical issues remain

---

### Step 3: Merge Process

Once approved:

* Feature branches are merged into `dev`
* `dev` is the integration branch
* `main` is updated only for stable releases

---

## 6. Branch Merge Strategy

### Feature Flow

```text
feature/* → PR → dev
```

### Release Flow

```text
dev → PR → main
```

---

## 7. Summary of Workflow Rules

* All development happens in feature branches
* All commits follow Conventional Commits
* All changes require pull requests
* All PRs require review and approval
* `dev` = integration branch
* `main` = production-ready branch
* No direct commits to `dev` or `main`
