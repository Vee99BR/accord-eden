# Accord: Eden

This repository contains the automation script to keep the [eden-mirror](https://github.com/Vee99BR/eden-mirror) repository in sync with the upstream [Eden](https://git.eden-emu.dev/eden-emu/eden) repository.

---

## Create a Personal Access Token (PAT)

Since `accord-eden` needs to push to another repository (`eden-mirror`), the default `GITHUB_TOKEN` does **not** have cross-repository permissions. You need to create a **Fine-grained Personal Access Token** with the right permissions:

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

The GitHub Actions workflow in this repository will use the `EDEN_MIRROR_TOKEN` to authenticate and push changes to the `eden-mirror` repository automatically.

The synchronization runs daily at KTT (Kasane Teto Time, or 01:04 UTC), and can also be triggered manually.

---

If you have any questions or want to contribute, feel free to open an issue or PR.
