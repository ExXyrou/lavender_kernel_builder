<div align="center">

# 🛠️ Lavender Kernel Builder

### 🚀 Automated Custom Linux Kernel CI for Xiaomi Redmi Note 7 (lavender)
*Powered by GitHub Actions & AnyKernel3*

</div>

---

## 📖 About
**Lavender Kernel Builder** adalah workflow GitHub Actions otomatis yang dirancang khusus untuk mengkompilasi kernel custom perangkat **Xiaomi Redmi Note 7 (`lavender`)**. Workflow ini mendukung berbagai pilihan versi Ubuntu, sistem cache kompilasi (`ccache`), fleksibilitas pemilihan toolchain Clang (Custom atau Neutron), serta integrasi notifikasi real-time via Telegram.

---

## ⚙️ Workflow Inputs & Parameters

Saat Anda menjalankan workflow ini secara manual (*workflow_dispatch*), Anda dapat mengatur parameter berikut:

| Parameter | Tipe | Wajib? | Deskripsi / Contoh |
| :--- | :--- | :---: | :--- |
| `KERNEL_SOURCE` | String | **Ya** | URL Repository Kernel (Contoh: `https://github.com/user/kernel_xiaomi_lavender`) |
| `KERNEL_BRANCH` | String | **Ya** | Nama Branch Kernel (Default: `main`) |
| `KERNEL_DEFCONFIG` | String | **Ya** | Nama Defconfig target (Contoh: `lavender_defconfig`) |
| `LOCALVERSION` | String | Tidak | Nama Suffix Kernel (Contoh: `-MyKernel-v1.0`) |
| `DEFAULT_HOSTNAME` | String | **Ya** | Hostname bawaan kernel (Contoh: `xiaomi@redmi`) |
| `BUILD_USER` | String | **Ya** | Usernamepembuat build (Contoh: `xiaomi`) |
| `BUILD_HOST` | String | **Ya** | Hostname mesin build (Contoh: `redmi`) |
| `UBUNTU_VERSION` | Choice | **Ya** | Versi Runner Ubuntu (`ubuntu-latest`, `ubuntu-24.04`, `ubuntu-22.04`, `ubuntu-20.04`) |
| `CLANG_SOURCE` | Choice | **Ya** | Sumber Toolchain Clang (`custom` atau `neutron`) |
| `CUSTOM_CLANG_URL` | String | Kondisional | URL Unduhan / Git Clang kustom (Wajib diisi jika `CLANG_SOURCE` dipilih `custom`) |

---

## 🚀 Key Features

*   **⚡ Smart Caching:** Menggunakan `ccache` dan caching folder Clang untuk mempercepat waktu kompilasi pada build berikutnya.
*   **🛠️ Error Patches:** Otomatis memperbaiki error umum pada kompiler modern seperti *DTC & Lexer Compilation Errors* pada kernel versi lama.
*   **📦 Flashable ZIP Integration:** Otomatis membungkus hasil kompilasi (`Image.gz-dtb` / `Image`) ke dalam format ZIP siap-flash menggunakan **AnyKernel3**.
*   **📢 Telegram Notifications:** Mengirimkan pesan status (Build Started, Success, Failed) lengkap dengan durasi build, tombol log, dan tautan unduhan rilis.
*   **🏷️ Automatic Release:** Berhasil mempublikasikan file ZIP ke *GitHub Releases* secara otomatis setelah build sukses.

---

## 💡 How to Use

1. Masuk ke tab **Actions** di repository GitHub Anda.
2. Pilih workflow **🛠️ Lavender Kernel Builder** pada panel sebelah kiri.
3. Klik tombol **Run workflow** di sebelah kanan atas.
4. Isi parameter yang diperlukan (URL Source, Branch, Defconfig, Toolchain, dll).
5. Klik **Run workflow** dan pantau proses kompilasi secara *real-time*.
6. Unduh file ZIP melalui menu **Releases** atau *Artifacts* setelah build selesai.

---

> [!NOTE]
> Pastikan repository Anda memiliki izin akses *Actions* (`Read and write permissions`) agar script dapat mempublikasikan rilis secara otomatis.
