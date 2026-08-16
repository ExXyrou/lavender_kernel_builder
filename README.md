<div align="center">

# 🛠️ Lavender Kernel Builder

### 🚀 Automated Custom Linux Kernel CI for Xiaomi Redmi Note 7 (`lavender`)
*Powered by GitHub Actions & AnyKernel3*

</div>

---

## 📖 About
**Lavender Kernel Builder** is an automated GitHub Actions workflow designed to compile custom kernels for the **Xiaomi Redmi Note 7 (`lavender`)**. 

Whether you are a developer testing a new feature or a user wanting to build a custom kernel, this tool handles everything automatically—from setting up the compiler and fixing compatibility issues to packing the final result into a flashable ZIP file and publishing a release.

---

## ⚙️ Workflow Inputs & Parameters

When you trigger this workflow manually via the **Actions** tab, you can customize the following settings:

| Parameter | Type | Required? | Description & Example |
| :--- | :--- | :---: | :--- |
| `KERNEL_SOURCE` | String | **Yes** | Your kernel repository URL (e.g., `https://github.com/user/kernel_xiaomi_lavender`) |
| `KERNEL_BRANCH` | String | **Yes** | The branch name to clone (Default: `main`) |
| `KERNEL_DEFCONFIG` | String | **Yes** | The target defconfig name (e.g., `lavender_defconfig`) |
| `LOCALVERSION` | String | No | Custom kernel suffix name (e.g., `-MyKernel-v1.0`) |
| `DEFAULT_HOSTNAME` | String | **Yes** | Default kernel hostname (e.g., `xiaomi@redmi`) |
| `BUILD_USER` | String | **Yes** | Build username (e.g., `xiaomi`) |
| `BUILD_HOST` | String | **Yes** | Build hostname (e.g., `redmi`) |
| `UBUNTU_VERSION` | Choice | **Yes** | Ubuntu runner version (`ubuntu-latest`, `ubuntu-24.04`, `ubuntu-22.04`, `ubuntu-20.04`) |
| `CLANG_SOURCE` | Choice | **Yes** | Clang toolchain source (`custom` or `neutron`) |
| `CUSTOM_CLANG_URL` | String | Conditional | Download link or Git URL for your custom Clang (Required if `CLANG_SOURCE` is set to `custom`) |

---

## 🚀 Key Features

*   **⚡ Lightning Fast Caching:** Uses `ccache` and toolchain caching to drastically reduce compilation times on subsequent builds.
*   **🛠️ Automatic Error Fixes:** Automatically patches common modern compiler errors (like DTC and Lexer errors) found in older kernel sources.
*   **📦 Ready-to-Flash ZIP:** Automatically packs the compiled kernel image into a flashable ZIP package using **AnyKernel3**.
*   **📢 Telegram Alerts:** Sends real-time notification messages to Telegram (Build Started, Success, Failed) complete with direct links to logs and downloads.
*   **🏷️ Auto-Publish Releases:** Automatically uploads your final flashable ZIP file to GitHub **Releases** upon a successful build.

---

## 💡 How to Use

1. Go to the **Actions** tab in your GitHub repository.
2. Select the **🛠️ Lavender Kernel Builder** workflow from the left sidebar.
3. Click the **Run workflow** dropdown button on the right.
4. Fill in your preferred configuration parameters (Source URL, Branch, Defconfig, Toolchain, etc.).
5. Click **Run workflow** and watch the compilation progress in real time!
6. Once finished, download your flashable kernel ZIP from the repository's **Releases** page.

---

> [!NOTE]
> Make sure your repository has **Read and write permissions** enabled under *Settings > Actions > General > Workflow permissions* so the script can successfully publish releases.
