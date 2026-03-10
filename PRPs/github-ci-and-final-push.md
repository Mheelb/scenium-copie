# GitHub CI and Final Push PRP

## Goal
Set up a minimalist GitHub Actions CI workflow to ensure tests pass before any potential deployment, and push all implemented features to the `main` branch, excluding internal tool directories.

## Why
1.  **Reliability:** Automating tests in CI prevents breaking changes from reaching production.
2.  **Clean Repository:** Keeping `.gemini/` and `PRPs/` out of the remote repository maintains a focused codebase for deployment and collaboration.

## What
-   **Task 1: GitHub Actions CI**
    -   Create `.github/workflows/ci.yml`.
    -   Workflow should run on `push` and `pull_request` to `main`.
    -   Steps: Checkout, Install dependencies, Run tests (`npm test`).
-   **Task 2: Final Push**
    -   Stage all modified/new files.
    -   Explicitly exclude `.gemini/` and `PRPs/` (using `.gitignore` or selective staging).
    -   Commit with a clear summary: "Implement responsive slider, contact form tests, and CI workflow".
    -   Push to the remote `main` branch.

## Technical Context

### Files to Implement/Modify
- `.github/workflows/ci.yml` - [New] CI configuration.
- `.gitignore` - [Modify] Ensure `.gemini/` and `PRPs/` are ignored to prevent accidental future pushes.

### Existing Patterns to Follow
- Standard GitHub Actions YAML syntax.
- Use `npm ci` or `npm install` based on project needs (minimalist approach prefers `npm install` if `package-lock.json` is healthy, but `npm ci` is safer for CI).

## Implementation Details

### CI Workflow (`ci.yml`)
```yaml
name: CI
on:
  push:
    branches: [main]
  pull_request:
    branches: [main]
jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - name: Setup Node
        uses: actions/setup-node@v4
        with:
          node-version: '20'
      - name: Install dependencies
        run: npm install
      - name: Run tests
        run: npm test
```

### Git Strategy
1.  Update `.gitignore` to include `.gemini/` and `PRPs/`.
2.  `git add .` (this will ignore the above due to `.gitignore`).
3.  `git commit -m "..."`.
4.  `git push origin main`.

## Validation Criteria

### Functional Requirements
- [ ] CI file is correctly formatted and located.
- [ ] Tests run successfully in the local environment before pushing.
- [ ] Remote repository on `main` does not contain `.gemini/` or `PRPs/`.

### Technical Requirements
- [ ] GitHub Actions syntax is valid.
- [ ] No sensitive files (like `.env`) are committed.

### Testing Steps
1. Run `npm test` locally.
2. Check `git status` to ensure `PRPs/` and `.gemini/` are untracked/ignored.
3. Push and verify the Actions tab on GitHub.
