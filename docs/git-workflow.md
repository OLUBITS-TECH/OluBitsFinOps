# Git Workflow

## Branching Strategy

OluBitsFinOps uses a lightweight feature-branch workflow.

The `main` branch represents the stable integration branch. Normal development work should not be committed directly to `main`.

Development work should be performed in short-lived branches created from `main`.

## Branch Naming Convention

Branches should follow this pattern:

feature/<work-item-id>-<short-description>

fix/<work-item-id>-<short-description>

docs/<work-item-id>-<short-description>

Examples:

feature/17-create-solution-structure

feature/24-add-customer-endpoint

fix/38-correct-transfer-validation

docs/12-update-architecture

Branch names should be:

- lowercase
- hyphen-separated
- concise
- traceable to an Azure DevOps work item

## Pull Request Strategy

Changes should be integrated into `main` through Pull Requests.

Pull Requests should:

- have a clear title
- reference the related Azure DevOps work item
- describe the purpose of the change
- include only related changes
- pass required build and test checks when CI is available
- be reviewed before merging

## Pull Request Naming

Pull Request titles should include the Azure DevOps work-item ID.

Example:

[17] Create solution structure

## Merge Strategy

After approval and successful checks, the Pull Request can be merged into `main`.

Merged feature branches should be deleted after the work is completed.

## Repository Bootstrap Exception

The initial repository bootstrap commit was committed directly to `main` because the repository was empty and did not yet have a baseline commit.

After the initial bootstrap, normal development should follow the feature-branch and Pull Request workflow.