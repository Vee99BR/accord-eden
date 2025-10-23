# Accord: Eden

This repository contains automation scripts that serve one main purpose:

1. **[A]ccord Branch Central Management**
   Allows managing branches in the mirror repository (`eden-mirror`) manually or automatically.
   You can choose a method for syncing branches:
   - `copy` — forcibly overwrite the branch in the mirror with the upstream branch.
   - `merge` — replay commits from the upstream branch onto `master` in the mirror.
   - `reset` — forcibly reset the `master` branch in the mirror to the upstream `master` branch.

   **Notes:**
   - The `master` branch is synced automatically daily at KTT (Kasane Teto Time, or 01:04 UTC).
   - `branch_to_sync` is required for `copy` or `merge`.
   - The mirror repository is isolated and up-to-date, independent from the upstream infrastructure.

---

## Create a Personal Access Token (PAT)

Since these workflows need to push to another repository (`eden-mirror`), the default `GITHUB_TOKEN` does **not** have cross-repository permissions. You need to create a **Fine-grained Personal Access Token**:

1. Go to: [https://github.com/settings/tokens](https://github.com/settings/tokens)
2. Click **Generate new token** → **Fine-grained, repo-scoped**.
3. Choose a **Token name** and **Resource owner**.
4. Set an expiration date (recommended).
5. Under **Repository access**, select **Only select repositories**.
6. Select `{OWNER}/eden-mirror`.
7. Set permissions:
    - **Contents**: `Read and write`
    - **Workflows**: `Read and write`
8. Generate the token and copy it.
9. Save the token as a secret named `EDEN_MIRROR_TOKEN` in the `accord-eden` repository:
    - Go to:
      `Settings` → `Secrets and variables` → `Actions` → `New repository secret`

---

## Usage

### [A]ccord Branch Central Management

- The `master` branch of the upstream Eden repository is mirrored to `eden-mirror` once per day at KTT (Kasane Teto Time, or 01:04 UTC).
- This process is handled by GitHub Actions in the `accord-eden` repository.
- The sync can also be triggered manually via the Actions tab.
  - `copy` — overwrite a specific branch in the mirror.
  - `merge` — replay commits from a branch onto `master`.
  - `reset` — reset the mirror `master` to upstream `master`.
- Specify `branch_to_sync` for `copy` or `merge`.

---

If you have any questions or want to contribute, feel free to open an issue or pull request.
