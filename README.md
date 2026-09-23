# 🚀 TypeScript Workflow Template

Welcome to the ultimate **TypeScript Template** repository! This repository comes pre-configured with a modern, high-performance tooling ecosystem designed to automate code quality, dependency management, commit standards, and seamless continuous integration.

## 🛠️ Built-In Tooling & Plugins

This template integrates a suite of automated workflows and git hooks categorized by their function:

### Code Quality & Formatting

- **[Ultracite](https://www.ultracite.ai/docs)**: Orchestrates ultra-fast linting and formatting powered internally by [**oxlint**](https://oxc.rs/docs/guide/usage/linter.html) and [**oxfmt**](https://oxc.rs/docs/guide/usage/formatter.html).
- **[Autofix](https://autofix.ci/setup)**: Automatically fixes linting and formatting issues directly on your Pull Requests via GitHub Actions.

### Commit & Git Workflow

- **[Lefthook](https://lefthook.dev/)**: A lightning-fast Git hooks manager that runs linters and commit checks locally before pushing.
- **[Commitlint](https://commitlint.js.org/guides/getting-started.html)**: Enforces the Conventional Commits specification on your commit messages.
- **[Commitizen](https://github.com/commitizen/cz-cli)**: Provides a command-line wizard to help you write formatted commit messages.

### Project & Automation

- **[Semantic Release](https://semantic-release.org/intro/)**: Fully automates the package release workflow, determining version numbers and generating changelogs based on commit history.
- **[Renovate](https://docs.renovatebot.com/getting-started/installing-onboarding/)**: Keeps your `npm` packages and GitHub Actions automatically updated via automated PRs.

### Issue & Label Management

- **[Label Sync](https://github.com/marketplace/actions/label-sync)**: Ensures standard issue labels are identical across your repositories.
- **[Advanced Issue Labeler](https://github.com/marketplace/actions/advanced-issue-labeler)**: Dynamically assigns labels to new issues based on body content or template selection.
- **[Issue Templates](.github/ISSUE_TEMPLATE/)**: Pre-configured issue templates located in `.github/ISSUE_TEMPLATE/` for streamlined **Bug Reports** and **Feature Requests**.

### Security & CI/CD

- **[CodeQL](https://docs.github.com/en/code-security/concepts/code-scanning/codeql/codeql-code-scanning)**: Industry-grade static analysis engine by GitHub to discover vulnerabilities in your codebase.
- **Node.js Build And Test Pipeline**: Automatically validates type safety, runs unit tests, and verifies production builds on every PR.

## 🚀 Getting Started

### 1. Generate Your Repository

Click the **"Use this template"** button at the top right of this page to spin up a new repository.

### 2. Setup Repository

- **Add Renovate:** [Install the Hosted GitHub App](https://docs.renovatebot.com/getting-started/installing-onboarding/#hosted-githubcom-app) for your new repo.
- **Sync Labels:**
  - Navigate to your repository and click on **Actions** in the navigation bar.
  - Select **Sync Labels** from the left sidebar, click the **Run workflow** dropdown, and trigger it manually.

### 3. Local Setup

Clone your new repository and install dependencies to automatically initialize git hooks:

```bash
npm install
```

## ⚓ Git Hooks (Lefthook Ecosystem)

This template uses **Lefthook** to automate checks locally before code ever leaves your machine. The following hooks are pre-configured:

- **`prepare-commit-msg` (Commit Wizard):** Intercepts standard `git commit` commands to automatically launch the interactive **Commitizen** wizard in your terminal.
- **`commit-msg` (Message Linting):** Runs **Commitlint** against your commit message to guarantee it follows the Conventional Commits specification.
- **`pre-commit` (Automated Fixes):** Runs `ultracite fix` on your staged files to handle formatting, linting, and type-aware diagnostics. Any automatically fixed files are re-staged before the commit completes.

## 📋 Available Scripts

- `npm run fix` — Run both `oxlint` and `oxfmt` with Ultracite to auto-fix errors and format code.
- `npm run check` — Audit format and lint rules across all files without modifying them.
- `npm run prepare` — Syncs Lefthook hooks automatically on `npm install`.
- `npm run build` — Compile the project for production. _(Referenced by CI workflow)_
- `npm test` — Run the local test suite. _(Referenced by CI workflow)_

**Note** Define test and build commands in `package.json`. The CI pipeline runs these automatically if they are present, so you don't need to modify the workflow files.

## 📁 Repository Structure

```text
│   .gitignore
│   .releaserc
│   commitlint.config.ts
│   lefthook.yml
│   oxfmt.config.ts
│   oxlint.config.ts
│   package-lock.json
│   package.json
│   README.md
│   renovate.json
│   tsconfig.json
│
├───.github
│   │   advanced-issue-labeler.yml
│   │   labels.yml
│   │
│   ├───ISSUE_TEMPLATE
│   │       bug_report.yml
│   │       config.yml
│   │       feature_request.yml
│   │
│   └───workflows
│           autofix.yml
│           codeql.yml
│           issue-labeler.yml
│           label-sync.yml
│           node.js.yml
│           release.yml
│
└───.vscode
        extensions.json
        labels-schema.json
        settings.json
```