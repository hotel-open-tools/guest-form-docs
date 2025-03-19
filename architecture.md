# 📌 Project Architecture

This document describes the architecture of the Guest Registration System, including its key components and their interactions.

## 🔹 System Architecture Diagram

```mermaid
graph TD
    Developer --> |Develops code| DevContainer
    DevContainer -->|Pushes code| GitHubRepository
    GitHubRepository -->|Triggers| GitHubActions
    GitHubActions -->|Builds & Deploys| AzureContainerApps
    GitHubActions -->|Publishes| GitHubPackages
    AzureContainerApps -->|Stores data| AzureCosmosDB[(AzureCosmosDB)]
    User -->|Uses app| AzureContainerApps
    DevContainer o-.-o |Pulls images| GitHubPackagesf
    AzureContainerApps o-.-o |Pulls images| GitHubPackages
    GitHubActions --> |Gitops| Azure-Resources

    subgraph Local Environment
        Developer
        DevContainer
    end

    subgraph GitHub
        GitHubRepository
        GitHubActions
        GitHubPackages
    end

    subgraph Azure-Resources
        AzureContainerApps
        AzureCosmosDB
    end

    User
```

## 🏗️ Architecture Components

- **Frontend:** A Vue.js-based application hosted on **Azure Static Web Apps**, allowing guests to register their details.
- **Backend:** An API deployed on **Azure Container Apps**, handling form submissions and retrieving guest data.
- **Database:** **Azure Cosmos DB** is used to store guest information in a scalable, serverless manner.
- **CI/CD Pipeline:** GitHub Actions automates testing, linting, and deployment of the application.