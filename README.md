# 🖥️ Pure Windows RDP via Tailscale on GitHub Actions ☁️

This repository provides a GitHub Actions workflow to create a clean, unmodified Windows Remote Desktop (RDP) session that is accessible securely over a [Tailscale](https://tailscale.com/) network.

This workflow is intentionally minimal. It does **not** apply any performance tweaks, debloating scripts, or system modifications. You get a pure, standard Windows environment, giving you a blank canvas to customize as you see fit. 🎨

---

## ✨ Features

*   ✅ **Pure Windows Environment**: Runs on the latest standard `windows-latest` image. No components, services, or apps are removed or disabled.
*   ✅ **Full Admin Access**: Get full administrator privileges to install software, change settings, or perform any task.
*   ✅ **Secure & Easy Access**: By leveraging Tailscale, the RDP port is never exposed to the public internet. 🛡️
*   ✅ **On-Demand**: Spin up a fresh Windows machine whenever you need it, directly from your GitHub repository.
*   ✅ **Zero Configuration**: The workflow is ready to go. Just provide your Tailscale authentication key and you're all set!

---

## 🚀 How to Use

### 📋 Prerequisites
*   A **GitHub Account**.
*   A **Tailscale Account** (the free personal plan is perfect).

### Step 1: Get Your Tailscale Auth Key 🔑

1.  Go to the **[Keys page](https://login.tailscale.com/admin/settings/keys)** in your Tailscale Admin Console.
2.  Click **Generate auth key**.
3.  Configure the key. For best results, you may want to make it **Reusable** and disable **Ephemeral**.
4.  Copy the generated key (it will look like `tskey-auth-...`).

### Step 2: Add the Key to GitHub Secrets 🔒

1.  In your GitHub repository, go to `Settings` > `Secrets and variables` > `Actions`.
2.  Click **New repository secret**.
3.  Name the secret `TAILSCALE_AUTH_KEY`.
4.  Paste your Tailscale auth key into the "Secret" field.
5.  Click **Add secret**.

### Step 3: Run the Workflow ▶️

1.  Go to the **Actions** tab in your repository.
2.  Select the **Pure RDP via Tailscale** workflow from the sidebar.
3.  Click the **Run workflow** dropdown, and then click the green **Run workflow** button.

### Step 4: Get Connection Details 🔎

1.  Wait for the job to start. Click on the running workflow to view its progress.
2.  Open the logs for the `Display Connection Details and Keep Alive` step.
3.  You will find the **Tailscale IP Address**, **Username**, and **Password** printed in the log.

    ```sh
    ================ RDP IS READY ================
    IP Address: 100.XX.XX.XX
    Username  : runneradmin
    Password  : WindowsRDP#2025
    ==============================================
    ```

### Step 5: Connect via RDP 💻

1.  Open your favorite Remote Desktop client (e.g., Microsoft Remote Desktop).
2.  Use the **Tailscale IP address** as the computer name/PC name.
3.  Connect using the username (`runneradmin`) and password from the logs.

You are now connected! The session will remain active for up to 6 hours or until you manually cancel the workflow on GitHub. ⏰
