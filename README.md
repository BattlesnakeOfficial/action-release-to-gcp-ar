# action-release-to-gcp-ar

GitHub Action to build a Docker image and push it to GCP Artifact Registry.

## Usage

```yaml
name: Release
on:
  release:
    types: [published]
    branches: [main]
jobs:
  release:
    name: Release
    runs-on: ubuntu-latest
    steps:
    - name: Release to GCP Artifact Registry
      uses: BattlesnakeOfficial/action-release-to-gcp-ar@main
      with:
        # Required
        image_tag: ${{ github.event.release.tag_name }}  # GitHub Release Tag
        gcp_artifact_registry: ${{ secrets.GCP_ARTIFACT_REGISTRY }}
        gcp_project_id: ${{ secrets.GCP_PROJECT_ID }}
        gcp_region: ${{ secrets.GCP_REGION }}
        gcp_service_account_email: ${{ secrets.GCP_SERVICE_ACCOUNT_EMAIL }}
        gcp_workload_identity_provider: ${{ secrets.GCP_WORKLOAD_IDENTITY_PROVIDER }}
        # Optional
        slack_webhook_url: "${{ secrets.SLACK_WEBHOOK_URL" }}
```
