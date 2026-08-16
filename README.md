# 🛠️ Lavender Kernel Builder

A GitHub Actions workflow designed to automate the process of building custom Linux kernels for the **Redmi Note 7 (lavender)**. It offers multi-source repository selection, automated Clang toolchain fetching, performance profile tweaks, KernelSU injection, and automatic AnyKernel3 zip packaging.

---

## 📌 Features

* **Multi-Source Support:** Choose between public kernel repositories (`predator-strombreaker`, `rave`, `san`), custom sources, or private sources (`snx`).
* **KernelSU Integration:** Automated setup for `xxKSU` or `KernelSU Next`.
* **Performance Tweaks:** Built-in profiles for EAS/HMP schedulers and performance-oriented config toggles (including 1000Hz extreme frequency setups).
* **Compiler Caching:** Integrated `ccache` to speed up subsequent workflow runs.
* **Auto-Packaging:** Dynamically packages the compiled kernel into a flashable AnyKernel3 `.zip` file.
* **Automatic Releases:** Publishes the final flashable zip directly to GitHub Releases upon build completion.

---

## 🚨 Important Notes & Requirements

### 1. KernelSU Injection Requirement

> **Note:** To enable KernelSU (`xxKSU` or `KernelSU Next`), your chosen kernel source **must already have the necessary hooks applied manually**. Applying KernelSU on an unhooked source will cause compilation errors or boot loops.

### 2. Accessing the Private Source (`snx`)

> **Notice:** The `snx` kernel source is hosted in a **private repository**. Access requires a one-time payment of **IDR 5,000 (Rp 5.000)**.

* **How to buy access:** Contact via Telegram at **[@exxyrou](https://www.google.com/search?q=https://t.me/exxyrou)** and provide proof of payment.
* **Usage:** Once approved, you will receive a personal access token (`GH_TOKEN`). Pass this token into the `GH_TOKEN` input field when triggering the workflow.

---

## 🚀 How to Run the Workflow

1. Go to the **Actions** tab in your repository.
2. Select **🛠️ Lavender Kernel Builder** from the left sidebar.
3. Click **Run workflow** and fill in the required parameters:

| Input Parameter | Description |
| --- | --- |
| `KERNEL_SOURCE` | Select preset source (`predator-strombreaker`, `rave`, `san`, `snx`) or `custom`. |
| `CUSTOM_KERNEL_URL` | URL of the repository (required if `custom` is selected). |
| `GH_TOKEN` | GitHub Personal Access Token (required for private repos like `snx` or private `custom` links). |
| `KERNEL_BRANCH` | Select preset branch (`oldcam`, `snx 1` to `snx 6`) or `custom`. |
| `CUSTOM_KERNEL_BRANCH` | Specific branch name (required if `custom` branch is selected). |
| `KERNEL_DEFCONFIG` | Name of your kernel defconfig file (e.g., `lavender_defconfig`). |
| `LOCALVERSION` | Custom suffix added to the kernel version (e.g., `-MyKernel-v1.0`). |
| `DEFAULT_HOSTNAME` | Hostname compiled into the kernel. |
| `BUILD_USER` | Username string for build info. |
| `BUILD_HOST` | Host string for build info. |
| `KERNEL_TWEAK` | Select performance profile (`none`, `eas`, `eas-extreme`, `hmp`, `hmp-extreme`). |
| `INJECT_KSU` | Select KernelSU variant (`none`, `xxKSU`, `KernelSU Next`). |
| `UBUNTU_VERSION` | Select the GitHub runner OS version. |
| `CLANG_SOURCE` | Select toolchain (`custom` URL or `neutron`). |
| `CUSTOM_CLANG_URL` | Direct download link for a custom Clang toolchain tarball. |

4. Click **Run workflow**. Once finished, the flashable `.zip` file will be uploaded to the **Releases** section of your GitHub repository.
