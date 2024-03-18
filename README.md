# Create SBOM

This action uses [Syft](https://github.com/anchore/syft) to create a SBOM ([Software Bill of Materials](https://en.wikipedia.org/wiki/Software_supply_chain)). It archive the result as an output of the Github Action run.

## How to use

Add this step after building and pushing your container image to GitHub's registry:

```yaml
- name: Create SBOM
  uses: digitalservicebund/create-sbom@LATEST_HASH
  with:
    image_name: ${{ github.repository }}:${{ github.sha }}
```

**Inputs:**
- `image_name`: **required**. Target image for which the SBOM should be created.
- `output_format`: optional. Output format of the SBOM. Available formats [listed here](https://github.com/anchore/syft?tab=readme-ov-file#output-formats).

## Updating this action

After merging a dependabot PR or pushing changes, you need to [cut a new release](https://docs.github.com/en/repositories/releasing-projects-on-github/managing-releases-in-a-repository).
