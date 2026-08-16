# 🛠️ Lavender Kernel Builder

An automated GitHub Actions workflow to build, tweak, package, and release custom Android kernels for the **Xiaomi Redmi Note 7 (`lavender`)** right inside GitHub. No local Linux PC or complex setup required!

---

## ✨ Key Features

* **Multiple Kernel Sources:** Choose from pre-configured popular sources (like *Predator-Strombreaker*, *San*, *SNX*) or link any **Custom Repository**.
* **Built-in KernelSU Integration:** Easily inject **KernelSU** or **KernelSU Next** with a single click.
* **Performance Profiles:** Toggle between **EAS** (Energy Aware Scheduling) or **HMP** architectures, with **Extreme** modes for maximum speed and responsiveness.
* **Automatic Toolchain Handling:** Supports custom Clang downloads or **Neutron Clang** via Antman.
* **Flashable Zip Packaging:** Automatically packs your compiled kernel image into an **AnyKernel3** flashable zip ready to flash via TWRP/OrangeFox.
* **Auto-Release:** Instantly publishes the build as a GitHub Release complete with upload artifacts and custom release tags.

---

## 📌 Important Notes Before You Build

* **KernelSU Next Requirement:** If you choose **KernelSU Next** in the injection options, you **must** use a kernel source that has already been manually hooked/prepared for KernelSU Next.
* **Accessing the `snx` Source:** Because the `snx` repository is private, you need to request access or make a small support donation of **5,000 IDR** to the developer tools. To donate and get access, contact the developer on Telegram at **@exxyrou**.

---

## 🚀 How to Use

1. Fork or upload this workflow file into your GitHub repository under `.github/workflows/kernel-builder.yml`.
2. Go to your repository's **Actions** tab on GitHub.
3. Select the **Lavender Kernel Builder** workflow from the left sidebar.
4. Click **Run workflow** and configure your preferred inputs:
* **Kernel Source & Branch:** Choose your desired source and branch. *(Note: If using a private repository like `snx`, make sure you have access and provide your personal access token in `GH_TOKEN`).*
* **Defconfig Name:** Enter your kernel's config file name (e.g., `lavender_defconfig`).
* **Performance Profile:** Pick between standard or extreme EAS/HMP tweaks.
* **KernelSU:** Select whether to include KernelSU variants or leave it as `none`.


5. Click the green **Run workflow** button and watch the compilation live! Once finished, grab your flashable zip from the **Releases** page.

---

## 📋 Inputs Configuration Reference

| Input Parameter | Description | Default |
| --- | --- | --- |
| `KERNEL_SOURCE` | Select your kernel repository source. | `custom` |
| `CUSTOM_KERNEL_URL` | Git repository URL when using the `custom` source. | *None* |
| `GH_TOKEN` | GitHub Access Token for private source access (required for `snx`). | *None* |
| `KERNEL_BRANCH` | Branch to clone from the kernel repository. | `custom` |
| `KERNEL_DEFCONFIG` | Target defconfig file name for compilation. | *Required* |
| `LOCALVERSION` | Custom suffix added to your kernel version name. | *None* |
| `DEFAULT_HOSTNAME` | Hostname set inside the kernel configuration. | *Required* |
| `BUILD_USER` & `BUILD_HOST` | Custom builder username and machine name tags. | *Required* |
| `KERNEL_TWEAK` | Select a pre-configured performance profile. | `none` |
| `INJECT_KSU` | Choose a KernelSU integration option. | `none` |
| `UBUNTU_VERSION` | GitHub runner Ubuntu environment version. | `ubuntu-latest` |
| `CLANG_SOURCE` | Choose between `neutron` toolchain or a `custom` URL. | `custom` |
