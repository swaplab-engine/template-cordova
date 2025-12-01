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
* **Compatibility:** [Download Archived Versions](https://www.construct.net/en/construct-2/download).
* **SwapLab Support:** We fully support Construct 2 exports via our `cordova.swaplab.net` builder or by wrapping them in Capacitor.

---

## 🌐 Service Compatibility

These templates are unique because they can be built on **ANY** of our platforms. Choose the engine that fits your needs:

| Builder Service | Engine Used | Best For |
| :--- | :--- | :--- |
| **[cordova.swaplab.net](https://cordova.swaplab.net)** | **Pure Cordova** | Legacy projects, Construct 2, strict backward compatibility. |
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

### Option A: CI/CD Automation (Recommended)
*Best for forking this entire collection (Monorepo) and building a specific game directly from GitHub.*

1.  **Fork Repository:** Click **`Fork`** (top right) to copy this monorepo to your account. **Remember to set it to PRIVATE.**
2.  **Access Service:** Log in to [SwapLab.net](https://swaplab.net). *(Your repo connects automatically upon login).*
3.  **Select Builder:** From the main menu, click **Repository Builder** (Builder Plus).
4.  **Start Build:**
    * Select your forked repository.
    * Select "Cordova" (or Capacitor) as the Framework Type.
    * **Project Folder Name:** Enter the specific folder name you want to build (e.g., `c3-ghost-racer-android` or `cordova-app-hello-world`).
    * Click "Build from Repository".

### Option B: Manual Upload (Quick Start)
*Best for testing a single template via Zip upload.*

1.  **Download:** Click **`<> Code`** > **Download ZIP**.
2.  **Extract:** Unzip the downloaded file.
3.  **Prepare Upload:**
    * Choose the folder you want (e.g., `c3-ghost-racer-android`).
    * **Zip THAT folder** individually.
4.  **Build:** Go to [SwapLab.net](https://swaplab.net).
5.  Select **Cordova Builder** (or Capacitor Builder), upload your zip, and build.

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