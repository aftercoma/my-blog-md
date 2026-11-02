---
title: "Cara Install OBS Studio di Linux (Distro-Distro Utama)"
date: 2026-11-02T22:30:00+07:00
draft: false
author: "Agung"
tags: ["linux", "obs-studio", "streaming", "tutorial"]
categories: ["Linux", "Tools"]
description: "Panduan lengkap cara install OBS Studio di berbagai distro Linux menggunakan Flatpak, PPA, maupun package manager bawaan."
---

OBS Studio (*Open Broadcaster Software*) adalah salah satu software open-source terbaik dan paling populer untuk kebutuhan *live streaming* dan *screen recording*. Bagi kamu pengguna Linux, proses instalasinya kini sangat mudah berkat adanya dukungan Flatpak dan *package manager* resmi dari masing-masing distro.

Berikut adalah panduan lengkap cara install OBS Studio di berbagai distro Linux.

---

## 1. Menggunakan Flatpak (Rekomendasi Utama)

Cara paling aman, universal, dan direkomendasikan untuk hampir semua distro Linux (seperti Fedora, Arch Linux, Debian, dll) adalah menggunakan **Flatpak**. Dengan Flatpak, kamu akan selalu mendapatkan versi OBS Studio terbaru tanpa khawatir masalah dependensi sistem.

### Pastikan Flatpak Terinstal
Jika distro kamu belum memiliki Flatpak, install terlebih dahulu:

* **Ubuntu / Debian / Linux Mint:**
  ```bash
  sudo apt install flatpak
  ```
* **Fedora:**
  ```bash
  sudo dnf install flatpak
  ```
* **Arch Linux:**
  ```bash
  sudo pacman -S flatpak
  ```

### Tambahkan Repository Flathub & Install OBS Studio
Setelah Flatpak terpasang, tambahkan repository Flathub dan install OBS dengan perintah berikut:

```bash
flatpak remote-add --if-not-exists flathub https://dl.flathub.org/repo/flathub.flatpakrepo
flatpak install flathub com.obsproject.Studio
```

Untuk menjalankan OBS Studio via Flatpak, kamu bisa mengetikkan perintah ini di terminal:
```bash
flatpak run com.obsproject.Studio
```
*(Atau langsung cari "OBS Studio" melalui Application Launcher / App Menu di desktop environment kamu).*

---

## 2. Cara Install Berdasarkan Distro Tertentu

Jika kamu lebih menyukai *native package* daripada Flatpak, berikut adalah cara instalasi berdasarkan distro yang kamu gunakan:

### A. Ubuntu & Linux Mint (Menggunakan PPA Resmi)
Tim OBS Studio menyediakan PPA resmi agar pengguna Ubuntu mendapatkan update versi terbaru dengan cepat.

```bash
sudo add-apt-repository ppa:obsproject/obs-studio
sudo apt update
sudo apt install obs-studio
```

### B. Fedora Linux
Fedora menyediakan OBS Studio langsung melalui repository resmi mereka atau RPM Fusion. Cara paling mudah di Fedora adalah menggunakan DNF:

```bash
sudo dnf install obs-studio
```

### C. Arch Linux & Distro Turunannya (Manjaro, EndeavourOS)
Untuk pengguna Arch Linux, OBS Studio tersedia di repository resmi `extra`. Kamu bisa menginstalnya menggunakan Pacman:

```bash
sudo pacman -S obs-studio
```

---

## Catatan Penting untuk Pengguna Linux (Wayland & NVIDIA)

Jika kamu menggunakan Linux dengan *Display Server* **Wayland** (seperti GNOME Wayland atau *window manager* seperti Hyprland/Niri):
* **Screen Capture:** Fitur *Window Capture* dan *Screen Capture* mungkin memerlukan plugin tambahan seperti `pipewire` dan `xdg-desktop-portal` agar berjalan mulus.
* **GPU NVIDIA:** Pastikan driver proprietary NVIDIA dan `libva` / `vdpau` terkonfigurasi dengan benar agar *hardware encoding* (NVENC) dapat digunakan untuk meringankan performa CPU saat *recording* atau *streaming*.

---

## Kesimpulan

Sekarang OBS Studio sudah terinstal di sistem Linux kamu. Kamu bisa langsung mengatur *Audio/Video settings*, menambahkan *Scenes* dan *Sources*, lalu mulai merekam layar atau melakukan *live streaming*. 

Jika ada kendala saat proses instalasi, silakan tanyakan di kolom komentar ya!