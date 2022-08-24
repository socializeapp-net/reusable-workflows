# reusable-workflows
GitHub Actions Workflows


## Set up a new caller repository
The following steps are required to do just once for a corresponding repository:

1. create a workflow yaml file in .github folder
   - only adjust the service name for the corresponding repository/service

    ```yaml
    name: Build and Deploy to Cloud Run
    
    # do not change
    on:
      push:
        branches:
          - "main"
          - "dev"
          - "experimental/*"
    
    # adjust the service name
    jobs:
      call-reusable-deploy:
        uses: socializeapp-net/reusable-workflows/.github/workflows/reusable-deploy.yaml@main
        with:
          service_name: backend-auth-service
        secrets: inherit
    ```
2. Open the caller repository in GitHub>Settings>Secrets
   - prove that the following secrets are set:
     - `GAR_JSON_KEY`
       - for the GCP service account
       - with the following permissions:
         - roles/run.admin
         - roles/iam.serviceAccountUser
         - roles/artifactregistry.admin
     - `SOCIALIZE_PACKAGE_PAT`
       - for private GitHub package access
      
## Development of Workflows
- install Nektos/Act for local GitHub Actions development
  - https://github.com/nektos/act
  - create a .secrets file with the following content:
    ```
    GAR_JSON_KEY=<same as GCP service account key>
    SOCIALIZE_PACKAGE_PAT=<same as GITHUB_TOKEN>
    ```
  - https://cloud.google.com/artifact-registry/docs/docker/authentication