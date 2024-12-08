# Frontend Design Strategy: IE Bank CI/CD Implementation

---

## Table of Contents

1. [Git Feature Branch Strategy](#git-feature-branch-strategy)
2. [Continuous Integration Workflow](#continuous-integration-workflow)
3. [References](#references)

---

## Git Feature Branch Strategy

### Overview

The frontend development workflow for IE Bank adheres to a Git Feature Branch strategy, designed to ensure collaboration, maintain quality, and enable efficient deployments. Key aspects include:

- **Branching Strategy**: Developers create short-lived branches for features, bug fixes, or CI/CD updates.
- **Pull Requests**: All code changes are merged into the `main` branch only after a thorough review.
- **Branch Protection Rules**:
  - Pull requests require approvals before merging.
  - Status checks must pass to ensure code quality.
- **Deployment Workflow**:
  - Push to the `ci-cd-rework` branch triggers deployment to the **Development** environment.
  - Pull requests to the `main` branch trigger deployment to **Development** and **UAT** environments.
  - Push to the `main` branch triggers deployment to **Development**, **UAT**, and **Production** environments.

### GitHub Configuration

1. **Branch Protection Rules**:
   - Navigate to `Settings > Branches > Branch Protection Rules`.
   - Add rules for the `main` branch to enforce pull request approvals and passing CI checks.

2. **Feature Branch Workflow**:
   - Create feature branches with the naming conventions:
     - Features: `feature/<description>`
     - Bug fixes: `bugfix/<description>`
     - CI/CD updates: `ci-cd-rework`
   - Merge branches into `main` only after successful review and CI runs.

---

## Continuous Integration Workflow

### Overview

The frontend CI workflow automates the build, test, and deployment process for the Vue.js application. It ensures consistent, high-quality code and deployment across environments.

### Build Steps

1. **Set Up Node.js**:
   - Configures Node.js version `18.x` using the `actions/setup-node@v4` action.
   - Caches npm dependencies to speed up builds.
   - **Purpose**: Ensures consistent environments for frontend builds.

2. **Install Dependencies**:
   - Runs `npm install` to fetch all required project dependencies.
   - **Purpose**: Prepares the application for build and test processes.

3. **Build Application**:
   - Executes `npm run build -- --mode development --dest dist-dev` to build the Vue.js application.
   - **Purpose**: Produces a deployable version of the frontend application.

4. **Upload Artifact**:
   - Uses `actions/upload-artifact@v4` to store build artifacts for deployment.
   - **Purpose**: Ensures consistent builds across all environments.

### Workflow Triggers

- Triggered by pushes to the `ci-cd-rework` branch.
- Triggered by pull requests to the `main` branch.
- Manually triggered via workflow dispatch.

---

## References

- [DevOps Checklist - Azure Architecture Center | Microsoft Learn](https://learn.microsoft.com/en-us/azure/architecture/checklist/dev-ops)
- [GitHub Actions Documentation](https://docs.github.com/en/actions)
- [Vue.js Deployment Guide](https://cli.vuejs.org/guide/deployment)
