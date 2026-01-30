# stale-demo

A test repository to experiment with the GitHub Stale Action. This repo is used for testing how stale issues and pull requests are automatically marked and closed after periods of inactivity.

## Overview

This repository uses a custom stale action (`chiranjib-swain/stale@feature/rate-limit-retry`) to manage inactive issues and pull requests. The workflow automatically marks issues and PRs as stale after a period of inactivity and eventually closes them if they remain inactive.

## Workflow Configuration

The stale workflow is configured in `.github/workflows/stale.yml` with the following settings:

### Trigger
- **Manual Trigger**: The workflow can be manually triggered using `workflow_dispatch`

### Permissions
- `issues: write` - Allows marking and closing issues
- `pull-requests: write` - Allows marking and closing pull requests
- `actions: write` - Allows workflow management

### Stale Behavior

#### Issues
- **Days before stale**: 15 days
- **Stale message**: "This issue is stale because it has been open for 30 days with no activity."
  - *Note: The message mentions 30 days, but the actual threshold is configured to 15 days*
- **Days before close**: 7 days (after being marked stale)

#### Pull Requests
- **Days before stale**: 20 days
- **Stale message**: "This pull request is stale because it has been open for 30 days with no activity."
  - *Note: The message mentions 30 days, but the actual threshold is configured to 20 days*
- **Days before close**: 7 days (after being marked stale)

### Additional Settings
- **Remove stale when updated**: `true` - The stale label will be removed if there's new activity

## Usage

1. Issues or PRs that remain inactive for the specified period will automatically be marked as stale
2. If an issue or PR receives new activity after being marked stale, the stale label will be removed
3. Items that remain stale for 7 additional days will be automatically closed

## Testing

This repository is specifically designed for testing the stale action behavior. You can:
- Create test issues to observe stale marking after 15 days of inactivity
- Create test pull requests to observe stale marking after 20 days of inactivity
- Manually trigger the workflow to test the stale action immediately
