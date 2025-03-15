# 📌 Epics and User Stories

## 🟢 Epic 1: GitHub & Project Setup
🎯 **Goal:** Establish a structured GitHub organization with well-organized repositories.

### User Stories:
- #### GH-001: Set Up GitHub Organization & Repositories
    - ✅ Create `hotel-open-tools` organization.
    - Configure basic settings (collaborators, visibility, permissions).

- #### GH-002: Create Repositories for Different Components
    - Repositories:
        - `guest-form-app` (Frontend)
        - `guest-form-api` (Backend)
        - `guest-form-infra` (Infrastructure as Code)
        - `guest-form-docs` (Documentation)
    - The repositories are public for open-source collaboration.

## 🟢 Epic 2: Development Environment
🎯 **Goal:** Ensure a smooth development experience with VS Code, WSL, and DevContainers.

### User Stories:
- #### DEV-001: Set Up Development Environment
    - ✅ Install WSL and configure AlmaLinux 9.
    - Install necessary CLI tools (git, Docker, Azure CLI).

- #### DEV-002: Configure DevContainers for Repositories
    - Add DevContainer support for each repository.
    - Define a `.devcontainer.json` file with dependencies.

## 🟢 Epic 3: Documentation & Project Management
🎯 **Goal:** Provide clear and accessible documentation.

### User Stories:
- #### DOC-001: Set Up a Central Documentation Repository | 🔗 **GitHub Issue:** [#1-document-user-stories](https://github.com/hotel-open-tools/guest-form-docs/issues/1)
    - ✅ Create `guest-docs` repository for project documentation.
    - ✅ Add an initial `README.md`.
    - ✅ Create `user-stories.md`.

- #### DOC-002: Document the Project’s Architecture & Design
    - Create `architecture.md` in `guest-docs`.
    - Add high-level system architecture (Frontend, Backend, Database, Infrastructure).

- #### DOC-003: Track and Manage User Stories in GitHub Issues
    - Create GitHub Issues for each user story.
    - Assign issues to the GitHub Kanban Board.

- #### DOC-004: Implement Forge for Documentation as Code
    - Set up Forge in the Documentation Repository.
    - Configure Forge to generate static documentation.
    - Automate documentation deployment via CI/CD.
    - Define a structure for project-wide documentation.
    - Link documentation across multiple repositories.

## 🟢 Epic 4: Infrastructure & Deployment
🎯 **Goal:** Host the application on Azure while ensuring scalability and cost efficiency.

### User Stories:
- #### INFRA-001: Set Up Azure Resource Group for Deployment
    - Create an Azure Resource Group (`hotel-rg`).
    - Define infrastructure setup using Terraform/Bicep.

- #### INFRA-002: Deploy Azure Container Apps Environment
    - Create Azure Container App for backend (`guest-api`).
    - Set up auto-scaling & networking.

- #### INFRA-003: Deploy Backend Service to Azure
    - Build & push the Docker image for `guest-api` to Azure Container Registry (ACR).
    - Deploy the service to Azure Container Apps.

- #### INFRA-004: Deploy Static Web App for Frontend
    - Deploy `guest-form-app` as an Azure Static Web App.
    - Ensure it can communicate with the `guest-api` backend.

- #### INFRA-005: Configure CORS & Authentication
    - Enable CORS policies to allow the frontend to access the API.
    - Implement Managed Identity for secure API access.

## 🟢 Epic 5: Database & Data Management
🎯 **Goal:** Store and manage guest registrations securely.

### User Stories:
- #### DB-001: Set Up Cosmos DB for Guest Profiles
    - Create a Cosmos DB instance.
    - Define a `guests` container with partition keys.

- #### DB-002: Implement API Endpoints for Guest Profiles
    - Implement CRUD operations for guests (Create, Read, Update, Delete).
    - Validate guest data before saving.
    - Test API integration.

## 🟢 Epic 6: Security & Secrets Management
🎯 **Goal:** Ensure secure storage and access control.

### User Stories:
- #### SEC-001: Store Secrets in Environment Variables & GitHub Secrets
    - Store secrets like Cosmos DB connection strings & API keys as environment variables.
    - Use GitHub Secrets for CI/CD workflows.
    - Integrate Managed Identity to securely fetch secrets.
    - Ensure .env files are never committed to GitHub

- #### SEC-002: Implement Secure Authentication for API
    - Require Managed Identity for API access.
    - Prevent unauthenticated users from accessing guest data.

## 🟢 Epic 7: Monitoring & Logging
🎯 **Goal:** Track system performance and log activity.

### User Stories:
- #### MON-001: Integrate Azure Application Insights for Backend Logging
    - Add Application Insights SDK to guest-api backend.
    - Enable structured logging, request tracking, and performance monitoring.
    - Use Log Analytics for debugging issues.

## 🟢 Epic 8: CI/CD & Automation
🎯 **Goal:** Automate deployment and testing.

### User Stories:
- #### CI-001: Set Up GitHub Actions for CI/CD
    - Define a GitHub Actions workflow to build and deploy `guest-api`.
    - Automate deployment to Azure Container Apps on push to `main`.

- #### CI-002: Implement Linting & Tests in CI Pipeline
    - Add linting & unit tests to GitHub Actions.
    - Fail build if tests don’t pass.
    - Tools:
        - Frontend: ESLint + Prettier
        - Backend: Ruff
        - IaC: tflint

- #### CI-003: Implement Automated Testing in CI/CD Pipeline
    - Run unit tests and integration tests in GitHub Actions.
    - Ensure tests must pass before deployment.
    - Tools:
        - Frontend: Vitest (for Vue)
        - Backend: (Python): Pytest
        - IaC: terraform plan

## 🟢 Epic 9: Frontend & User Experience
🎯 **Goal:** Build a user-friendly guest registration UI.

### User Stories:
- #### FE-001: Set Up a Basic UI for Guest Registration
    - Create a simple web form for guest check-in with Vue.
    - Store submitted data in `guest-api`.

- #### FE-002: Connect Frontend to Backend API
    - Integrate `guest-form-app` with `guest-api`.
    - Display stored guest information.

- #### FE-003: Enable Multi-Language Support (English & Spanish)
    - Provide language selection for users.
    - Translate all UI elements.

## 🟢 Epic 10: Backend API
🎯 **Goal:** Implement backend services for handling guest data.

### User Stories:
- #### API-001: Implement POST /register Endpoint
    - Accept guest name, email, phone, nationality.
    - Validate required fields & email formatting.

- #### API-002: Store Guest Data in Cosmos DB
    - Save registration details securely.

- #### API-003: Retrieve Guest Registrations by Date
    - Allow hosts to view registrations from a specific period.

---