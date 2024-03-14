# Create SBOM

This action uses [Syft](https://github.com/anchore/syft) to create a SBOM ([Software Bill of Materials](https://en.wikipedia.org/wiki/Software_supply_chain)). It archive the result as an output of the Github Action run.

## How to use

```yaml
env:
  IMAGE_NAME: ${{ github.repository }}

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - name: Build Docker image
        run: |
          docker build -t ${{ env.IMAGE_NAME }}:${{ github.sha }} . --build-arg COMMIT_SHA=${{ github.sha }}
      - name: Create SBOM
        uses: digitalservicebund/github-actions/create-sbom@c6b78c632c4b017802d3e3ce9706a43b9380f804
        with:
          image_name: ${{ env.IMAGE_NAME }}:${{ github.sha }}
```

**Inputs:**
- `image_name`: **required**. Target image for which the SBOM should be created.
- `output_format`: optional. Output format of the SBOM. Available formats [listed here](https://github.com/anchore/syft?tab=readme-ov-file#output-formats).

## Updating this action

After merging a dependabot PR or pushing changes, you need to [cut a new release](https://docs.github.com/en/repositories/releasing-projects-on-github/managing-releases-in-a-repository).
