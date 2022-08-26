# reusable-workflows

Collection of organization-wide reusable GitHub Action workflows.


## Set up a new caller repository
The following steps are required to do just once for a corresponding repository:

1. create a new repository from the template repository
   - https://github.com/socializeapp-net/template-backend-service
2. Open the caller repository in GitHub>Settings>Secrets
   - prove that the secrets described in the template repository are set up
      
## Development of Workflows
- install Nektos/Act for local GitHub Actions development
  - https://github.com/nektos/act
  - create a .secrets file with the following structure:
    ```
    KEY=VALUE
    KEY2=VALUE2
    ```
  - https://cloud.google.com/artifact-registry/docs/docker/authentication