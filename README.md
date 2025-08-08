# Accord: Eden

This repository contains automation scripts that serve three main purposes:

1. **[A]utomatic Accord Synchronization**
   Keeps the `master` branch of the upstream [`Eden`](https://git.eden-emu.dev/eden-emu/eden) repository mirrored to [`eden-mirror`](https://github.com/Vee99BR/eden-mirror) daily at KTT (Kasane Teto Time) via GitHub Actions.

2. **Manual Branch Re[c]ord**
   Allows manually mirroring other branches from the upstream.

3. **[B]uild a Mirror of Eden**
   Standalone Github Action Script to build a binary based on `eden-mirror` for testing purposes.
   **Currently supported only on Windows.**

The `eden-mirror` repository offers an isolated and up-to-date source tree, independent from the upstream infrastructure.

---

## Create a Personal Access Token (PAT)

Since `accord-eden` needs to push to another repository (`eden-mirror`), the default `GITHUB_TOKEN` does **not** have cross-repository permissions. You need to create a **Fine-grained Personal Access Token** with the appropriate permissions:

1. Go to: [https://github.com/settings/tokens](https://github.com/settings/tokens)

2. Click **Generate new token** → **Fine-grained, repo-scoped**.

3. Choose a **Token name**.

4. Select the **Resource owner** (your user or organization).

5. Set an expiration date (recommended).

6. Under **Repository access**, select **Only select repositories**.

7. Select the repository `{OWNER}/eden-mirror` to grant access.

8. Set the following **Repository permissions**:
    - **Contents**: `Read and write`
    - **Workflows**: `Read and write`

9. Generate the token and copy it.

10. Save the token as a secret named `EDEN_MIRROR_TOKEN` in the `accord-eden` repository:

    - Go to:
      `Settings` → `Secrets and variables` → `Actions` → `New repository secret`

---

## Usage

### [A]utomatic Accord Synchronization

- The `master` branch of the upstream Eden repository is mirrored to `eden-mirror` once per day at KTT (Kasane Teto Time, or 01:04 UTC).
- This process is handled by GitHub Actions in the `accord-eden` repository.
- The sync can also be triggered manually via the Actions tab.

### Manual Branch Re[c]ord

- Use it to mirror other branches from upstream as needed.

### [B]uild a Mirror of Eden

- Use the `eden-mirror` repository for building Eden manually.
- **Currently supported build environment: Windows**.

---

If you have any questions or would like to contribute, feel free to open an issue or pull request.
