# ufprog-mingw-builder

This repository hosts a dedicated GitHub Actions workflow to automatically build and release the **ufprog** (from [hackpascal/ufprog](https://github.com/hackpascal/ufprog)) utility for Windows (64-bit) using the **MinGW** toolchain via **MSYS2**.

## 🚀 Usage

This workflow is configured to run manually via `workflow_dispatch`.

1. Navigate to the **Actions** tab in this repository.

2. Select the **"Build and Release ufprog (MinGW)"** workflow.

3. Click the **"Run workflow"** button on the right.

4. The workflow will:

   * Clone the latest source code from `hackpascal/ufprog`.

   * Compile the executables and dynamic libraries (DLLs) using MinGW.

   * Collect all necessary build artifacts and runtime DLLs into a portable folder.

   * Compress the folder into a single `.zip` file.

   * Create or update a GitHub Release using the commit date as the version tag (`build-YYYY-MM-DD`).

The final compressed artifact will be attached to the new release.

## 🛠 Workflow Details

| Action Used | Version | Purpose | 
| ----- | ----- | ----- | 
| `msys2/setup-msys2` | `v2` | Installs the MSYS2 environment and MinGW toolchain. | 
| `actions/checkout` | `v5` | Clones the target repository (`hackpascal/ufprog`). | 
| `actions/github-script` | `v8` | Uses the GitHub API to delete previous releases/tags for clean updates. | 
| `softprops/action-gh-release` | `v2` | Creates the final GitHub Release and uploads the `.zip` artifact. |
