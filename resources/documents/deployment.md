# Production Deployment & Rollback

## Environment URLs
* **Staging:** `https://staging.myproject.com`
* **Production:** `https://myproject.com`

## Rollback Procedures
If a production release introduces a critical error, run the following workflow in GitHub Actions:
1. Navigate to Actions -> Production Deploy.
2. Select **Run Workflow** and choose the previous stable release tag (e.g., `v1.2.4`).
3. Click Run.