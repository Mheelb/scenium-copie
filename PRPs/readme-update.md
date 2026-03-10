# README Update (including Docker) PRP

## Goal
Update the `README.md` to describe the Scenium project and provide clear instructions for local development (npm), testing, and Docker usage.

## Why
A project-specific README helps developers understand the goal and available environments (local vs containerized).

## What
-   **Task 1: Project Description**
    -   Landing page for Scenium: mobile event scenes.
-   **Task 2: Local Development (npm)**
    -   `npm install`
    -   `npm run dev` (http://localhost:3000)
    -   `npm run test` (Vitest)
-   **Task 3: Docker Development**
    -   `docker-compose up --build`
    -   Description: Launches the dev environment in a container on port 3000 with hot-reload via volumes.
-   **Task 4: CI/CD Context**
    -   GitHub Actions CI validation on push.

## Technical Context

### Files to Reference (read-only)
- `docker-compose.yml` - For Docker commands.
- `package.json` - For scripts.

### Files to Implement/Modify
- `README.md` - [Modify] Complete rewrite.

## Implementation Details

### Content Structure
1.  **Scenium - Landing Page**
2.  **Installation Locale**
3.  **Lancement avec Docker**
4.  **Tests automatisés**

## Validation Criteria

### Functional Requirements
- [ ] Docker instructions are correct (`docker-compose up`).
- [ ] Project purpose is clear.
- [ ] Test command is mentioned.

### Testing Steps
1. Verify Docker command syntax in the text.
