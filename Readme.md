## Argo CD – Multi-Stage Application Structure

Argo CD
└── app-of-apps
    ├── dev
    │   └── nginx app (replicas=1)
    ├── staging
    │   └── nginx app (replicas=2)
    └── prod
        └── nginx app (replicas=3)


### Overview
This repository demonstrates a **multi-stage deployment** using **Argo CD App-of-Apps pattern**.

### Environments
- **dev**
  - Used for development and testing
  - Single replica for fast iteration

- **staging**
  - Pre-production environment
  - Two replicas for validation and stability testing

- **prod**
  - Production environment
  - Three replicas for high availability

### Deployment Flow
1. Argo CD manages a root **app-of-apps**
2. Each environment is deployed as a child application
3. Changes are automatically synchronized from Git
4. Environments are fully isolated using Kubernetes namespaces

kubectl apply -f app-of-apps.yaml
Then open:

Argo CD → Applications
You will see:

✅ dev-app

✅ staging-app

✅ prod-app

Each auto-syncing 🎉
