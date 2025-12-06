# SwapLab: Cordova & Construct Game Templates (Monorepo)

![SwapLab Certified](https://img.shields.io/badge/SwapLab-Certified-success)
![License](https://img.shields.io/badge/license-MIT-blue.svg)
![Structure](https://img.shields.io/badge/Structure-Monorepo-orange)

This repository hosts a collection of starter templates for building **Standard Cordova** applications and **HTML5 Games** (Construct 2 & 3).

These templates are versatile. While designed for Cordova, they are fully compatible with **all SwapLab Build Services**, allowing you to build them using either the classic Cordova engine or the modern Capacitor engine.

---

## ⚠️ CRITICAL: Privacy & Billing Guide

Before using these templates, please read these rules to ensure your code is safe and your billing is managed correctly.

### 🔒 1. Privacy Rule: Make Your Fork PRIVATE
When you fork this repository to your account, **you must change the visibility to PRIVATE** immediately to protect your source code.
* **Why?** To prevent leaking your App ID, API Keys, or proprietary game assets to the internet.
* **Compatibility:** You **do not** need a public repo to use SwapLab. Our public build images can be pulled into your **Private Repository** without any limits.

### 💰 2. Billing & Service Model
It is important to distinguish between **GitHub Costs** and **SwapLab Service Costs**.

**A. GitHub Actions Quota (Compute)**
The build process runs inside *your* GitHub account.
* **Free Accounts:** GitHub typically provides **2,000 free minutes/month**.
* **Capacity:** ~300-400 builds/month.
* **Upgrade:** If you exceed this, you pay GitHub directly via [GitHub Actions Billing](https://docs.github.com/en/billing/concepts/product-billing/github-actions).

**B. SwapLab Subscription (Orchestration)**
We offer a **Free Tier** (Unlimited Debug builds) and **Paid Tiers** (Release builds).
* **Philosophy:** Our fees are **not** for reselling GitHub minutes. They cover our physical resources (vCPU, RAM, NVMe, Storage) and security infrastructure.
* **How to Upgrade:** You can view plans and upgrade your account directly within the **SwapLab Dashboard** after signing in.
👉 **[View Pricing & Plans](https://pricing.swaplab.net)**

## 🚀 Build Support & Pricing

| Build Type | Availability |
| :--- | :--- |
| **Debug APK** | ✅ **Free Forever** (Unlimited, No Subscription) |
| **Release APK / AAB** | 🎁 **Free PROMO** (Ends Jan 1, 2026) |
| **Export Android Studio/Xcode** | 🎁 **Free PROMO** (Ends Jan 1, 2026) |


> [!TIP]
> **🛡️ Security & Trial Options (Zero-Trust)**
>
> If you are hesitant about uploading your **Keystore/Signing Keys** to a cloud service, you have a safe alternative:
> * **Local Signing:** Choose **`Export Android Studio`** or **`Export Xcode`** as your build type. We will compile the native project structure for you, and you can sign the final app locally on your own machine.
> * **Plugin Devs & Testing:** Use **`Debug APK`** (Unlimited/Free). It requires no keys and is perfect for testing **Capacitor/Cordova plugins** or evaluating the service without a subscription.




---

## 📂 Available Templates

Choose your preferred project type below. Each folder represents a complete, isolated application.

| Folder Name | Description | Type |
| :--- | :--- | :--- |
| [`/cordova-app-hello-world`](./cordova-app-hello-world) | Standard Apache Cordova "Hello World" | **Cordova** |
| [`/c3-ghost-racer-android`](./c3-ghost-racer-android) | Construct 3 Export (Android) | **Game** |
| [`/c3-fruit-slicing-ios`](./c3-fruit-slicing-ios) | Construct 3 Export (iOS) | **Game** |
| [`/c2-space-blaster`](./c2-space-blaster) | Construct 2 Export (Space Shooter) | **Game** |
| [`/c2-flapping-bird`](./c2-flapping-bird) | Construct 2 Export (Flappy Clone) | **Game** |



> [!WARNING]
> **⛔️ CRITICAL: DO NOT DELETE THE `.github/workflows` DIRECTORY**
>
> This directory is the **digital bridge** connecting your repository to the SwapLab Service.
> * **How it works:** SwapLab acts as the **Trigger**, but the build runs on **YOUR GitHub Account** using your Action Minutes.
> * **Consequence:** Removing these files will **sever the connection**, and the Service will be **unable to trigger** the build process.


---

## 🎮 Special Notes for Construct Users

If you are using Scirra Construct game engines, please note the following requirements:

### Construct 3
To export your game for Mobile (Cordova/Android/iOS), you must have a valid subscription.
* **Check Pricing:** [Buy Construct 3](https://www.construct.net/en/make-games/buy-construct)
* **Export Guide:** Select "Cordova" as your export target in the Construct 3 editor.

### Construct 2 (Legacy)
Construct 2 is officially discontinued.
* **Final Release:** r280 (July 1, 2021).

---

## 🌐 Service Compatibility

These templates are unique because they can be built on **ANY** of our platforms. Choose the engine that fits your needs:

| Builder Service | Engine Used | Best For |
| :--- | :--- | :--- |
| **[cordova.swaplab.net](https://cordova.swaplab.net)** | **Pure Cordova** | Dedicated build workflows for the classic Apache Cordova ecosystem. |
| **[capacitor.swaplab.net](https://capacitor.swaplab.net)** | **Capacitor** | Modernizing your Cordova app. Uses the newer Capacitor runtime to build standard Cordova projects. |
| **[repository.swaplab.net](https://repository.swaplab.net)** | **Both** | CI/CD automation. Supports both engines depending on the workflow file you choose. |

---

## ⚙️ Build Configuration Guide

SwapLab offers advanced build settings to customize your security and performance.

### 1. 🛠️ Build Provider
Select the CI/CD infrastructure to run your build process.
* **GitHub (Default):** Uses standard GitHub Actions runners.
* *CircleCI / GitLab:* (Coming Soon).

### 2. 🛡️ Vulnerability Scan (NPM Audit)
**Status:** <span style="color:red">MANDATORY</span>
Checks your project's dependencies against the CVE database. Even legacy games often use npm packages that may have critical flaws.

### 3. 🔍 Semgrep (SAST)
**Status:** <span style="color:red">MANDATORY</span>
Static Application Security Testing. Scans your source code for insecure patterns.

### 4. 📦 Trivy (SCA)
**Status:** <span style="color:red">MANDATORY</span>
Scans third-party libraries for deep supply chain vulnerabilities.

### 5. 🔒 NPM Script Security
**Status:** Optional (Default: Off)
* **Enabled:** Adds `--ignore-scripts`.
* **Warning:** Many Cordova plugins **REQUIRE** scripts to install properly. **We recommend keeping this OFF for Cordova/Construct projects.**

### 6. 💊 Auto-Heal Vulnerabilities
**Status:** Optional (Default: Off)
* **Function:** Runs `npm audit fix` automatically.
* **Benefit:** Can fix minor dependency issues in `package.json` automatically.

### 7. 🔬 Final Artifact Scan
**Status:** Optional (Default: Off)
* **Enabled:** Runs `clamscan` (Anti-virus) on the final APK/AAB file.

---

## ⚡ How to Build

Choose the method that suits your workflow. Both options utilize **your GitHub Action minutes** for the build execution.

### Option A: Repository Builder (CI/CD Automation)
*Best for automated builds directly from your GitHub repository.*

> **Requirement:** Since this repository is a **Monorepo** (containing multiple templates), you **must** specify which folder you want to build (e.g., `cordova-app-hello-world` or `c3-ghost-racer-android`) to ensure the `.github` bridge is excluded from the artifact.

1.  **Create Repository:** Click **Use this template** (top right) > **Create a new repository** (Select **Private**).
2.  **Access Service:** Log in to **[repository.swaplab.net](https://repository.swaplab.net)**.
3.  **Start Build:**
    * Select your newly created repository.
    * Select **Cordova** as the Framework Type.
    * **Project Folder Name:** ✍️ **ENTER FOLDER NAME** (e.g., `cordova-app-hello-world`).
    * *Critical:* **DO NOT** leave this empty. You must specify the specific project folder you want to build.
    * Click **Build from Repository**.

### Option B: Cordova Builder (Manual Upload)
*Best for quick builds via Zip upload. Also uses your GitHub Action minutes.*

1.  **Download:** Click **<> Code** > **Download ZIP**.
2.  **Extract & Prepare:**
    * Unzip the downloaded file.
    * Open the folder and choose your desired template (e.g., open the `cordova-app-hello-world` folder).
    * **Zip** the contents of that specific folder (e.g., create `hello-world.zip`).
    * *Note:* Do not zip the entire monorepo; only zip the specific project folder you want to build.
3.  **Build:** Go to **[cordova.swaplab.net](https://cordova.swaplab.net)**.
4.  **Configure:**
    * Select **Cordova** as the Framework Type.
    * Upload your specific project zip file.
    * Click **Build**.

---



## 📺 Video Tutorials

Visual learner? Watch our step-by-step guides directly on YouTube.

* **🎥 [SwapLab GitHub Sign In Steps](https://youtu.be/km8ljUfL6Dc)**
* **🚀 [Construct 3 Cordova to Capacitor: Automated APK Release Build](https://youtu.be/GXM38MdL-fs)**
* **🚀 [Construct 3 Cordova to Capacitor: Automated AAB Release Build (Mobile Ads Ready)](https://youtu.be/5dDqSHt_d60)**
* **🍎 [Construct 3 Cordova to Capacitor: No CLI, Drag & Drop to Android Studio](https://youtu.be/RTapxQgyOm4)**



## 🔐 Signing Production Builds (Repository Builder Only)

> **Important:** This section applies **ONLY** to users using **Option A (Repository Builder)**.
> If you are using Option B (Manual Upload), you do not need to configure these secrets.

To generate signed **Release APKs** or **AAB (Android App Bundle)** automatically via GitHub Actions, you **MUST** configure the following Secrets in your GitHub Repository settings.

### 1. Add Secrets to GitHub
Go to **Settings** > **Secrets and variables** > **Actions** > **New repository secret**.

**🛠️ Workflow Implementation Details:**
If you inspect the workflow file ([`both-workflow-repo-no-cache.yml`](https://github.com/swaplab-engine/template-cordova/blob/main/.github/workflows/both-workflow-repo-no-cache.yml)), you will see exactly how these credentials are passed to the container:

| Secret Name | Description |
| :--- | :--- |
| `KEYSTORE_BASE64` | Your `.jks` or `.keystore` file converted to a Base64 string. |
| `KEYSTORE_PASSWORD` | The password for your Keystore. |
| `KEY_ALIAS` | The alias name of your key. |
| `KEY_PASSWORD` | The password for your specific key alias. |

### 2. How to generate KEYSTORE_BASE64
You cannot upload the binary keystore file directly to GitHub Secrets. You must convert it to a text string first.

**Mac/Linux:**
```bash
base64 -i your-keystore.jks > base64-keystore.txt
# Open base64-keystore.txt, copy the content, and paste it into the Secret value.
```

**Windows (PowerShell):**
```bash
[Convert]::ToBase64String([IO.File]::ReadAllBytes("your-keystore.jks")) | Out-File base64-keystore.txt
```

### 3. 🔍 Transparency: How Secrets are Used (Secure & Ephemeral)
We prioritize security by using **Just-In-Time (JIT) Processing**.

Your signing keys and passwords are handled with strict isolation rules to ensure they cannot be leaked or retrieved:

1.  **Memory-Only:** Your secrets are processed entirely in **Volatile Memory (RAM)**.
2.  **No Disk IO:** We strictly **do not** write your passwords to any persistent configuration files or logs on the server.
3.  **Zero Trace:** The build environment is ephemeral. Once the build process finishes, the isolated container is immediately destroyed, wiping all data from memory.

```yaml
# From the .yml workflow (Inputs):
-e INPUT_KEYSTORE_BASE64=${{ secrets.KEYSTORE_BASE64 }} \
-e INPUT_KEYSTORE_PASSWORD=${{ secrets.KEYSTORE_PASSWORD }} \
-e INPUT_KEY_ALIAS=${{ secrets.KEY_ALIAS }} \
-e INPUT_KEY_PASSWORD=${{ secrets.KEY_PASSWORD }} \
```
* **Security Note (Silent Mode):** To guarantee zero leakage, the GitHub Actions log output is intentionally **restricted**.
    * **Where to watch:** A secure, sanitized log stream is transmitted exclusively to your **SwapLab Live Dashboard**.



---


## 🏗️ Infrastructure & Ecosystem

The build engine used to process these templates is part of the SwapLab Open Ecosystem. Our architecture prioritizes **Zero-Knowledge Storage** and **Just-In-Time (JIT) Security**.

![SwapLab Security Architecture](https://github.com/user-attachments/assets/fc878e6c-b39c-44d0-836f-328c05452163)

You can audit our infrastructure components here:

* **🐳 Cordova Core:** [View Public Base Image](https://github.com/swaplab-engine/cordova-core)
* **🐳 Capacitor Core:** [View Public Base Image](https://github.com/swaplab-engine/capacitor-core)
* **📦 Build Packages:** [View Engine Images Registry](https://github.com/orgs/swaplab-engine/packages)
* **⚙️ Workflow Templates:** [View Integration .yml Files](https://github.com/swaplab-engine/workflow-templates)

---






<br>

<details>
<summary><strong>🔍 Transparency: GitHub Permissions & API Usage (Click to expand)</strong></summary>

<br>


<img width="431" height="741" alt="GitHub-Permissions" src="https://github.com/user-attachments/assets/cfdc1b35-517a-4b9e-9c29-300fd7b93aac" />


In this workflow, SwapLab acts as a **Digital Bridge (Trigger)**. It connects your SwapLab dashboard to your private GitHub Workspace, allowing you to trigger builds that run *inside* your own repository using standard GitHub Actions.

We believe in radical transparency. Here is the exact technical breakdown of why we request specific permissions and which GitHub APIs are triggered:

### 1. 🔑 Authentication
We use **Firebase Authentication (GitHub OAuth)** to verify your identity. We never see, store, or access your GitHub password.
* **Ref:** [Firebase GitHub Auth Documentation](https://firebase.google.com/docs/auth/web/github-auth)

### 2. ⚡ Workflows (Actions: Write)
**Why it's required:**
To act as a "Remote Control" for your build button. This allows the SwapLab Dashboard to start a build or cancel a hanging process.

**API Endpoints Used:**
* **Trigger Build:** `POST /repos/{owner}/{repo}/actions/workflows/{workflow_id}/dispatches`
* **Cancel Build:** `POST /repos/{owner}/{repo}/actions/runs/{run_id}/cancel`
* **Ref:** [GitHub: Manually run a workflow](https://docs.github.com/en/actions/how-tos/manage-workflow-runs/manually-run-a-workflow)

### 3. 📂 Contents (Read & Write)
**Why it's required:** `repository.swaplab.net`

* **(Read) To Check Out Code:**
    This allows the GitHub Actions runner to securely `checkout` your source code into the temporary, isolated build environment so it can be compiled.
* **(Write) To Upload Build Artifacts:**
    This permission supports our **Artifact Storage** feature. If you select the *"GitHub Repository (Releases)"* option, we use this permission to automatically create a new GitHub Release and upload your finished build file (e.g., `.apk` or `.aab`) as an asset to that release.

> **⚠️ Note:** We only use this permission to **Create** releases. We **do not** automate the deletion of your files. Full control to delete old releases or assets remains manually in your hands via:
> `https://github.com/{owner}/{repo}/releases`

**API Tool Used:**
We utilize the official GitHub CLI (`gh api`) within the workflow:
```bash
gh api \
  -H "Accept: application/vnd.github+json" \
  -H "X-GitHub-Api-Version: 2022-11-28" \
  /repos/OWNER/REPO/releases

```
**🛠️ Workflow Implementation Details:**
If you inspect the workflow file ([`both-workflow-repo-no-cache.yml`](https://github.com/swaplab-engine/template-cordova/blob/main/.github/workflows/both-workflow-repo-no-cache.yml)), you will see exactly how these credentials are passed to the container:

* `-e GITHUB_SHA=${{ github.sha }}`: **Unique Release Code.**
    We use the unique Commit ID to tag the release version. This ensures you can trace every APK/AAB back to the exact code change that generated it.
* `-e GITHUB_TOKEN=${{ secrets.GITHUB_TOKEN }}`: **Automatic Token.**
    This is a temporary, auto-generated token provided by GitHub Actions. It is strictly used to authenticate the upload of the artifact back to your repository and expires immediately after the job finishes.



### 4. ℹ️ Metadata (Read-only)
**Why it's required:**
This is a default permission. We use it to read basic information about your repository (like its name and visibility) to display it correctly in your Dashboard list.

</details>

<br>





---

## 🔗 Legal & Support

By using this service, you agree to our policies regarding repository access and data handling.

* **Repository Access:** [Permissions Explained](https://swaplab.net/privacy-policy/repository-permissions.html)
* **Terms & Conditions:** [Read Terms](https://swaplab.net/privacy-policy/terms-and-conditions.html)
* **Privacy Policy:** [Read Policy](https://swaplab.net/privacy-policy/privacy-policy.html)

---

## 🙏 Credits & Acknowledgements

These templates are adapted from open-source examples provided by the Scirra Construct community and the Apache Cordova project.

| Project | Original Source / Inspiration |
| :--- | :--- |
| **Space Blaster** | [Scirra Construct 2 Templates](https://www.construct.net/en) |
| **Ghost Racer** | [Scirra Construct 3 Templates](https://editor.construct.net/) |
| **Hello World** | [Apache Cordova](https://cordova.apache.org/) |



## 👨‍💻 About the Creator

SwapLab is built and maintained by **EMI (EMI-INDO)**, a dedicated developer in the Hybrid Mobile App ecosystem.

This service was built to solve the real-world build problems I faced while developing plugins and games.

* **Cordova Plugins:** I maintain various open-source [Cordova Plugins on GitHub](https://github.com/EMI-INDO?tab=repositories).
* **Game Assets:** Verified seller of [Construct 3 Addons](https://www.construct.net/en/game-assets/users/emiindo-378213).
* **Community:** Active member of the [Construct Community Forums](https://www.construct.net/en/forum).

---
<p align="center">
  Maintained by <b>SwapLab Engineering Team</b>
</p>