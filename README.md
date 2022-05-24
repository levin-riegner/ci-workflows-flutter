<p align="center"><img src="https://cdn.svarun.dev/gh/actions-small.png" width="150px"/></p>

# Github Actions Workflow Sync
Sync Github Action's Workflow Files Across Repositories 

## 🛠 Installation
1. Add Fastlane to the destination repository by copying the `example` folder from [the fastlane repository](https://github.com/levin-riegner/fastlane) and configure the .env files and code signing accordingly (*follow [this guide](https://www.notion.so/CI-Continuous-Integration-006651de6c39478394ce13866ce1df21) for the complete process*).
2. Copy the example [.env file](example/.env) to the destination repository inside the `.github/workflows/` folder. Update it to match your project setings.
3. Ensure the account `levinriegner-qa` has write access to the destination repository.
1. Add the destination repository to keep in sync inside the `REPOSITORIES` variable on the [workflow-sync.yml](.github/workflows/workflow-sync.yml) file.
4. Push the file changes to master.
5. Approve the auto-generated Pull Request in the destination repository.

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

### Additional builds for the same release
#### Internal
If you need to upload a new build for the same internal release, first push the changes to **master** and then rebase/merge them on top of the internal branch.

#### Production
Additional builds cannot be sent for the same production release.
Simply create a new release branch increasing the version name.

### Manual Dispatch
Workflows that include the `workflow_dispatch:` trigger can also be dispatched manually on the GitHub website:
- Navigate to the "Actions" tab on the repository.
- Select the "Workflow" you want to trigger.
- Press the "Run workflow" button.
- Select the branch you want to run it from.
- Press "Run workflow".

## ⚙️ Updating Workflows
1. Update the workflows inside the `workflows` folder as needed.
2. (Optional) Test your changes on the `testbed` branch.
3. Push changes to `master` to trigger the sync workflow.
4. Approve the auto-generated Pull Request in the destination repositories.