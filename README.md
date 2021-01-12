<p align="center"><img src="https://cdn.svarun.dev/gh/actions-small.png" width="150px"/></p>

# Github Workflow Sync - ***Github Action***
Github Action To Sync Github Action's Workflow Files Across Repositories 

## 🛠 Installation
1. Add Fastlane to the destination repository by copying the `example` folder from [this repository](https://github.com/levin-riegner/fastlane) and configure the .env files and code signing accordingly.
1. Add the new repository to keep in sync inside the `REPOSITORIES` variable on the [WorkflowSync](.github/workflows/workflow-sync.yml) file.
2. Copy the example [.env file](example/.env) to the destination repository inside the `.github/workflows/` folder. Update it to match your project setings.
3. Ensure the account `levinriegner-qa` has write access to the repository.
4. Push the changes to master.
5. Approve the auto-generated Pull Request in the destination repository.
6. Enjoy ☕️
> Follow [this guide](https://www.notion.so/CI-Continuous-Integration-006651de6c39478394ce13866ce1df21) for the complete process.

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

### IMPORTANT
Please do not push new commits directly to the release or internal branches, otherwise we might end up with conflicting version codes later on.<br>
If you need to upload a new build for the same release, always **push the changes to master first** and then rebase them on top of the release or internal branch.

## ⚙️ Updating Workflows
1. Update the workflows inside the `workflows` folder as needed.
2. Push the changes to master.
3. Approve the auto-generated Pull Request in the destination repositories.
4. Enjoy ☕️