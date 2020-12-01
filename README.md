<p align="center"><img src="https://cdn.svarun.dev/gh/actions-small.png" width="150px"/></p>

# Github Workflow Sync - ***Github Action***
Github Action To Sync Github Action's Workflow Files Across Repositories 

## ⚙️ Configuration
1. Update the workflows inside the `workflows` folder as needed.
2. Add new repositories to keep in sync inside the file `.github/workflows/workflow-sync.yml`.
3. Ensure the account `levinriegner-qa` has write access to all repositories.
4. Push the changes to master.
5. Approve the auto-generated Pull Request in the destination repositories.
6. Enjoy ☕️
---
## 🚀 Workflows Usage

### Internal Workflow

To create a new *internal* release use the GitHub Actions `Internal` Flow:

1. Checkout from `master` to a new branch named `internal/a.b.c` and push to origin.
    - Android: Build is uploaded to Firebase App Tester.
    - iOS: Build is uploaded to Testflight.

### Release Workflow

To create a new release use the GitHub Actions `Release` Flow:

1. Checkout from `master` to a new branch named `release/a.b.c` and push to origin.
2. Once both platforms are finished, visit their store portals to submit the builds.
    - Android: Build is uploaded to Production track as Draft.
    - iOS: Build is uploaded to Testflight.

### Test Workflow

Commits to `master` will execute all Flutter Unit Tests.

## IMPORTANT
Please do not push new commits directly to the release or internal branch, otherwise we might end up with conflicting version codes later on.<br><br>
If you need to upload a new build for the same release, always **push the changes to master first** and then rebase them on top of the release branch.