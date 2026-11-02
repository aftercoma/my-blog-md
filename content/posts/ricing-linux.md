---
title: "Panduan Ricing Hyprland: Terminal-Centric & Estetik di Linux"
date: 2026-11-02T23:00:00+07:00
draft: false
tags: ["linux", "hyprland", "ricing", "wayland", "dotfiles"]
categories: ["Linux", "Ricing"]
description: "Panduan dasar ricing Hyprland di Linux Wayland: mengatur blur, transparansi, animasi mulus, hingga integrasi bar dan launcher."
---

Jika kamu pengguna Linux yang suka tampilan minimalis, kencang, dan estetik, **Hyprland** adalah salah satu *dynamic tiling Wayland compositor* terbaik saat ini. Dibandingkan dengan i3wm atau Sway, Hyprland menawarkan animasi bawaan yang sangat mulus, efek blur yang cantik, serta konfigurasi yang mudah dibaca.

Di artikel ini, kita akan membahas dasar-dasar *ricing* Hyprland agar tampilan desktop Linux kamu makin keren dan nyaman digunakan sehari-hari.

---

## 1. Persiapan Komponen Utama

Untuk membangun ekosistem desktop yang utuh di Hyprland, kamu membutuhkan beberapa *tools* pendukung:

| Komponen | Aplikasi Rekomendasi | Fungsi |
| :--- | :--- | :--- |
| **Status Bar** | `Waybar` / `AGS` | Menampilkan workspace, indikator RAM/CPU, jam, dan tray |
| **Application Launcher** | `Rofi-wayland` / `Wofi` | Menjalankan aplikasi dengan cepat via keyboard |
| **Wallpaper Engine** | `hyprpaper` / `swww` | Menampilkan wallpaper (mendukung GIF/transisi) |
| **Notification Center** | `Dunst` / `Swaync` | Menampilkan notifikasi sistem yang minimalis |
| **Terminal Emulator** | `Kitty` / `Alacritty` | Terminal utama dengan dukungan transparansi |

---

## 2. Struktur File Konfigurasi

File konfigurasi utama Hyprland terletak di:
`~/.config/hypr/hyprland.conf`

Bagi file konfigurasi kamu menjadi beberapa bagian agar lebih rapi:
* `monitors.conf` (Atur resolusi & refresh rate)
* `keybindings.conf` (Shortcut keyboard)
* `windowrules.conf` (Atur transparansi & floating window)
* `animations.conf` (Kustomisasi efek gerakan)

---

## 3. Menambahkan Efek Transparansi & Blur

Salah satu daya tarik utama Hyprland adalah efek *glassmorphism* (blur) yang sangat halus.

Buka file `hyprland.conf` kamu dan tambahkan konfigurasi pada bagian `decoration`:

```ini
decoration {
    rounding = 10                  # Sudut jendela melengkung (rounded corners)
    active_opacity = 0.95
    inactive_opacity = 0.80

    blur {
        enabled = true
        size = 6
        passes = 3
        new_optimizations = true
        ignore_opacity = true
    }

    drop_shadow = yes
    shadow_range = 15
    shadow_render_power = 3
    col.shadow = rgba(1a1a1aee)
}
```

---

## 4. Kustomisasi Animasi agar Lebih Smooth

Animasi di Hyprland menggunakan kurva *Bezier*. Kamu bisa mengatur seberapa kenyal atau cepat gerakan window saat dibuka, ditutup, atau dipindah workspace:

```ini
animations {
    enabled = yes

    # Definisi Kurva Bezier
    bezier = myBezier, 0.05, 0.9, 0.1, 1.05
    bezier = smoothOut, 0.36, 0, 0.66, -0.56

    # Penerapan Animasi
    animation = windows, 1, 6, myBezier
    animation = windowsOut, 1, 6, smoothOut, popin 80%
    animation = border, 1, 10, default
    animation = fade, 1, 7, default
    animation = workspaces, 1, 5, myBezier
}
```

---

## 5. Mengatur Window Rules

Kadang ada aplikasi tertentu yang jalannya kurang maksimal kalau dalam posisi *tiling* (ubin), atau membutuhkan transparansi khusus. Kamu bisa menggunakan `windowrulev2`:

```ini
# Membuat aplikasi tertentu selalu floating
windowrulev2 = float, class:^(pavucontrol)$
windowrulev2 = float, title:^(Volume Control)$

# Contoh rule transparansi spesifik aplikasi
windowrulev2 = opacity 0.90 0.90, class:^(kitty)$
windowrulev2 = opacity 1.00 1.00, class:^(firefox)$
```

---

## 6. Integrasi Auto-Start Aplikasi

Agar Waybar, Wallpaper, dan Notification Daemon berjalan otomatis saat masuk ke Hyprland, tambahkan baris `exec-once` di konfigurasi kamu:

```ini
exec-once = waybar
exec-once = swww-daemon
exec-once = dunst
```

---

## Kesimpulan

Ricing di Hyprland itu sangat fleksibel. Kunci utama mendapatkan tampilan yang ciamik adalah konsistensi **Skema Warna** (misalnya menggunakan *Catppuccin*, *Gruvbox*, atau *Tokyo Night*) pada semua komponen dari Waybar, Terminal, Neovim, hingga Rofi.

Jangan lupa simpan seluruh folder `~/.config/hypr/` kamu ke repository Git (*Dotfiles*) agar aman dan bisa di-restore!⏎
