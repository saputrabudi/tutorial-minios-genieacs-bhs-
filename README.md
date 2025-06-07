# 🚀 Tutorial Instalasi MiniOS dan GenieACS

<div align="center">

![MiniOS Logo](https://img.shields.io/badge/MiniOS-Live-blue?style=for-the-badge&logo=linux)
![GenieACS Badge](https://img.shields.io/badge/GenieACS-ACS%20Server-green?style=for-the-badge&logo=server)
![License](https://img.shields.io/badge/License-Free-brightgreen?style=for-the-badge)
![Language](https://img.shields.io/badge/Language-Bahasa%20Indonesia-red?style=for-the-badge)

</div>

---

<div align="center">

### 📖 Panduan lengkap untuk menginstall MiniOS di USB Flash Drive dan menginstall GenieACS di sistem MiniOS

[![GitHub](https://img.shields.io/badge/GitHub-MiniOS-black?style=flat&logo=github)](https://github.com/minios-linux/minios-live)
[![Documentation](https://img.shields.io/badge/Docs-GenieACS-blue?style=flat&logo=gitbook)](https://docs.genieacs.com)

</div>

---

## 📑 Daftar Isi

- [🖥️ Instalasi MiniOS di USB Flash Drive](#️-instalasi-minios-di-usb-flash-drive)
- [⚙️ Instalasi GenieACS di MiniOS](#️-instalasi-genieacs-di-minios)
- [🛠️ Troubleshooting](#️-troubleshooting)
- [📚 Referensi](#-referensi)

---

## 🖥️ Instalasi MiniOS di USB Flash Drive

<div align="center">

```ascii
    ┌─────────────────────────────────────┐
    │  🖥️  MiniOS Installation Guide  💿  │
    └─────────────────────────────────────┘
```

</div>

### 1️⃣ Download File ISO MiniOS

<img src="https://img.shields.io/badge/Step-1-blue?style=flat-square" alt="Step 1"> **Download Requirements**

* Download file ISO MiniOS dari website resmi MiniOS.

### 2️⃣ Membuat USB Drive yang Bootable

<img src="https://img.shields.io/badge/Step-2-orange?style=flat-square" alt="Step 2"> **Pilihan Metode Instalasi**

#### 🥇 Metode Utama (Windows/Linux/MacOS)

> ⭐ **Rekomendasi:** Metode ini mendukung fitur persistence

1. Copy folder `/minios/` ke root directory disk Anda (contoh: `E:\minios\`).
2. Navigasi ke directory `/minios/boot/` di USB device atau hard disk Anda.
3. Cari file `bootinst.bat` (untuk Windows) atau `bootinst.sh` (untuk Linux dan MacOS).
4. Jalankan file tersebut dengan double-click untuk melakukan perubahan yang diperlukan pada master boot record device Anda.

#### 🔸 Menggunakan Rufus (Windows)

![Windows](https://img.shields.io/badge/Windows-0078D4?style=flat&logo=windows&logoColor=white)

Rufus adalah utility yang membantu format dan membuat USB flash drive yang bootable.

1. 📥 Buka Rufus.
2. 🖱️ Pilih USB drive Anda.
3. 📁 Pilih file ISO MiniOS.
4. ▶️ Mulai proses.

#### 🔸 Menggunakan UNetbootin (Windows/Linux/MacOS)

![Cross Platform](https://img.shields.io/badge/Cross--Platform-Multi-brightgreen?style=flat&logo=atom)

UNetbootin dapat membuat bootable Live USB drive.

1. 📥 Buka UNetbootin.
2. 📁 Pilih file ISO MiniOS.
3. 🖱️ Pilih USB drive Anda.
4. ✅ Klik 'OK'.

#### 🔸 Menggunakan Ventoy (Windows/Linux)

![Ventoy](https://img.shields.io/badge/Ventoy-Multi--Boot-blue?style=flat&logo=debian)

Ventoy adalah tool open-source yang memungkinkan Anda membuat bootable USB drive dengan hanya menyalin file ISO ke dalamnya.

1. ⬇️ Install Ventoy ke USB drive Anda.
2. 📋 Copy file ISO MiniOS langsung ke USB.

#### 🔸 Menggunakan Balena Etcher (Windows/Linux/MacOS)

![Balena Etcher](https://img.shields.io/badge/Balena--Etcher-Cross--Platform-yellow?style=flat&logo=raspberry-pi)

Balena Etcher adalah utility cross-platform yang menulis images ke drives.

1. 📁 Pilih file ISO MiniOS.
2. 🖱️ Pilih USB drive Anda.
3. ⚡ Klik "Flash!".

#### 🔸 Menggunakan `dd` (Linux)

![Linux](https://img.shields.io/badge/Linux-FCC624?style=flat&logo=linux&logoColor=black)

1. Identifikasi USB drive Anda dengan `lsblk`.
2. Unmount disk dengan `umount /dev/sdX`.
3. Jalankan:
```bash
sudo dd if=/path/to/minios.iso of=/dev/sdX bs=4M; sync
```

#### 🔸 Menggunakan `dd` (MacOS)

![macOS](https://img.shields.io/badge/macOS-000000?style=flat&logo=apple&logoColor=white)

1. 🔍 Identifikasi USB drive Anda dengan `diskutil list`.
2. 📤 Unmount disk dengan `diskutil unmountDisk /dev/diskX`.
3. ⚡ Jalankan:
```bash
sudo dd if=/path/to/minios.iso of=/dev/rdiskX bs=1m
```

### 3️⃣ Booting dari USB Drive

<img src="https://img.shields.io/badge/Step-3-green?style=flat-square" alt="Step 3"> **Boot Process**

1. 🔄 Restart komputer Anda.
2. ⌨️ Pilih USB drive di boot menu komputer Anda untuk boot dari USB tersebut.

### 4️⃣ Catatan Penting

<img src="https://img.shields.io/badge/Important-Notes-red?style=flat-square" alt="Important"> **Requirements & Limitations**

* 🚫 Boot installer tidak mendukung multiboot; hanya MiniOS yang akan bootable dari drive tersebut.
* 🔧 Disk Anda harus menggunakan partition scheme `msdos` (gunakan MBR, bukan GPT).
* 💾 Drive harus diformat dengan salah satu file system yang didukung: FAT32, NTFS, ext2, ext3, ext4, btrfs.

> 💡 **Pengingat:** Metode instalasi utama adalah rekomendasi utama, tetapi Anda juga bisa menggunakan Rufus, UNetbootin, Ventoy, Balena Etcher, atau `dd` sebagai alternatif di Windows, Linux, dan MacOS. Namun, perlu diingat bahwa fitur persistence tidak akan berfungsi ketika menggunakan Ventoy, Balena Etcher, atau `dd`.

---

## ⚙️ Instalasi GenieACS di MiniOS

<div align="center">

```ascii
    ┌───────────────────────────────────────┐
    │  ⚙️  GenieACS Installation Guide  🖥️  │
    └───────────────────────────────────────┘
```

![GenieACS](https://img.shields.io/badge/GenieACS-v1.2.13-green?style=for-the-badge&logo=server)
![Node.js](https://img.shields.io/badge/Node.js-v12.13+-brightgreen?style=for-the-badge&logo=node.js)
![MongoDB](https://img.shields.io/badge/MongoDB-v3.6+-green?style=for-the-badge&logo=mongodb)

</div>

### 📋 Prerequisites

#### 🟢 Node.js

![Node.js](https://img.shields.io/badge/Node.js-339933?style=flat&logo=node.js&logoColor=white)

GenieACS memerlukan Node.js 12.13 ke atas. Untuk instalasi di MiniOS:

```bash
# Update package manager
sudo apt update

# Install Node.js
sudo apt install nodejs npm

# Verifikasi instalasi
node --version
npm --version
```

#### 🟢 MongoDB

![MongoDB](https://img.shields.io/badge/MongoDB-47A248?style=flat&logo=mongodb&logoColor=white)

GenieACS memerlukan MongoDB 3.6 ke atas:

```bash
# Install MongoDB
sudo apt install mongodb

# Start dan enable MongoDB service
sudo systemctl start mongodb
sudo systemctl enable mongodb

# Verifikasi status MongoDB
sudo systemctl status mongodb
```

### 📦 Install GenieACS

#### 🚀 Instalasi dari NPM:

![NPM](https://img.shields.io/badge/NPM-CB3837?style=flat&logo=npm&logoColor=white)

```bash
sudo npm install -g genieacs@1.2.13
```

### 🔧 Konfigurasi systemd

#### 👤 Buat system user untuk menjalankan GenieACS daemons

![System User](https://img.shields.io/badge/System-User-blue?style=flat&logo=linux)

```bash
sudo useradd --system --no-create-home --user-group genieacs
```

#### 📁 Buat directory untuk menyimpan extensions dan environment file

![Directory](https://img.shields.io/badge/Directory-Setup-yellow?style=flat&logo=folder)

```bash
mkdir /opt/genieacs
mkdir /opt/genieacs/ext
chown genieacs:genieacs /opt/genieacs/ext
```

#### 📝 Buat file konfigurasi

![Config](https://img.shields.io/badge/Config-File-orange?style=flat&logo=gear)

Buat file `/opt/genieacs/genieacs.env` untuk menyimpan opsi konfigurasi:

```bash
sudo tee /opt/genieacs/genieacs.env > /dev/null <<EOF
GENIEACS_CWMP_ACCESS_LOG_FILE=/var/log/genieacs/genieacs-cwmp-access.log
GENIEACS_NBI_ACCESS_LOG_FILE=/var/log/genieacs/genieacs-nbi-access.log
GENIEACS_FS_ACCESS_LOG_FILE=/var/log/genieacs/genieacs-fs-access.log
GENIEACS_UI_ACCESS_LOG_FILE=/var/log/genieacs/genieacs-ui-access.log
GENIEACS_DEBUG_FILE=/var/log/genieacs/genieacs-debug.yaml
NODE_OPTIONS=--enable-source-maps
GENIEACS_EXT_DIR=/opt/genieacs/ext
EOF
```

#### Generate JWT secret yang aman:

```bash
node -e "console.log(\"GENIEACS_UI_JWT_SECRET=\" + require('crypto').randomBytes(128).toString('hex'))" >> /opt/genieacs/genieacs.env
```

#### Set file ownership dan permissions:

```bash
sudo chown genieacs:genieacs /opt/genieacs/genieacs.env
sudo chmod 600 /opt/genieacs/genieacs.env
```

#### Buat logs directory

```bash
mkdir /var/log/genieacs
chown genieacs:genieacs /var/log/genieacs
```

### Buat systemd unit files

#### Service genieacs-cwmp:

```bash
sudo systemctl edit --force --full genieacs-cwmp
```

Masukkan konfigurasi berikut:

```ini
[Unit]
Description=GenieACS CWMP
After=network.target

[Service]
User=genieacs
EnvironmentFile=/opt/genieacs/genieacs.env
ExecStart=/usr/bin/genieacs-cwmp

[Install]
WantedBy=default.target
```

#### Service genieacs-nbi:

```bash
sudo systemctl edit --force --full genieacs-nbi
```

Masukkan konfigurasi berikut:

```ini
[Unit]
Description=GenieACS NBI
After=network.target

[Service]
User=genieacs
EnvironmentFile=/opt/genieacs/genieacs.env
ExecStart=/usr/bin/genieacs-nbi

[Install]
WantedBy=default.target
```

#### Service genieacs-fs:

```bash
sudo systemctl edit --force --full genieacs-fs
```

Masukkan konfigurasi berikut:

```ini
[Unit]
Description=GenieACS FS
After=network.target

[Service]
User=genieacs
EnvironmentFile=/opt/genieacs/genieacs.env
ExecStart=/usr/bin/genieacs-fs

[Install]
WantedBy=default.target
```

#### Service genieacs-ui:

```bash
sudo systemctl edit --force --full genieacs-ui
```

Masukkan konfigurasi berikut:

```ini
[Unit]
Description=GenieACS UI
After=network.target

[Service]
User=genieacs
EnvironmentFile=/opt/genieacs/genieacs.env
ExecStart=/usr/bin/genieacs-ui

[Install]
WantedBy=default.target
```

### Konfigurasi log rotation

Simpan konfigurasi berikut sebagai `/etc/logrotate.d/genieacs`:

```bash
sudo tee /etc/logrotate.d/genieacs > /dev/null <<EOF
/var/log/genieacs/*.log /var/log/genieacs/*.yaml {
    daily
    rotate 30
    compress
    delaycompress
    dateext
}
EOF
```

### Enable dan start services

```bash
# Enable dan start genieacs-cwmp
sudo systemctl enable genieacs-cwmp
sudo systemctl start genieacs-cwmp
sudo systemctl status genieacs-cwmp

# Enable dan start genieacs-nbi
sudo systemctl enable genieacs-nbi
sudo systemctl start genieacs-nbi
sudo systemctl status genieacs-nbi

# Enable dan start genieacs-fs
sudo systemctl enable genieacs-fs
sudo systemctl start genieacs-fs
sudo systemctl status genieacs-fs

# Enable dan start genieacs-ui
sudo systemctl enable genieacs-ui
sudo systemctl start genieacs-ui
sudo systemctl status genieacs-ui
```

### Verifikasi Instalasi

Setelah semua service berjalan, Anda dapat mengakses GenieACS UI melalui web browser di:

```
http://localhost:3000
```

### Catatan Keamanan

⚠️ **Penting untuk deployment production:**
- Pastikan untuk mengkonfigurasi TLS/HTTPS
- Ubah `UI_JWT_SECRET` ke string yang unik dan aman
- Rujuk ke dokumentasi HTTPS untuk mengaktifkan TLS untuk enkripsi traffic

---

## 🛠️ Troubleshooting

<div align="center">

```ascii
    ┌─────────────────────────────────────┐
    │  🛠️  Troubleshooting Guide  🔍  │
    └─────────────────────────────────────┘
```

</div>

### 🖥️ Masalah Umum MiniOS

| 🚨 Masalah | 💡 Solusi |
|------------|-----------|
| 🚫 **USB tidak bootable** | Pastikan menggunakan MBR (bukan GPT) dan format yang didukung |
| 💾 **Persistence tidak bekerja** | Gunakan metode instalasi utama, bukan Ventoy/Etcher/dd |

### ⚙️ Masalah Umum GenieACS

| 🚨 Masalah | 💡 Solusi |
|------------|-----------|
| 🔴 **Service tidak start** | Periksa logs dengan `journalctl -u <service-name>` |
| 🔒 **Permission denied** | Pastikan ownership file/directory sudah benar untuk user genieacs |
| 🗄️ **MongoDB connection error** | Pastikan MongoDB service berjalan |

### 📊 Melihat Logs

![Logs](https://img.shields.io/badge/Monitoring-Logs-blue?style=flat&logo=file-text)

```bash
# Logs GenieACS services
journalctl -u genieacs-cwmp -f
journalctl -u genieacs-nbi -f
journalctl -u genieacs-fs -f
journalctl -u genieacs-ui -f

# Access logs
tail -f /var/log/genieacs/genieacs-*.log
```

---

## 📚 Referensi

<div align="center">

| 📖 Resource | 🔗 Link | 📝 Description |
|-------------|---------|----------------|
| ![MiniOS](https://img.shields.io/badge/MiniOS-Wiki-blue?style=flat&logo=github) | [Installing MiniOS on a USB Flash Drive](https://github.com/minios-linux/minios-live/wiki/Installing-MiniOS-on-a-USB-Flash-Drive) | Tutorial resmi instalasi MiniOS |
| ![GenieACS](https://img.shields.io/badge/GenieACS-Docs-green?style=flat&logo=gitbook) | [GenieACS Installation Guide](https://docs.genieacs.com/en/latest/installation-guide.html) | Panduan instalasi GenieACS |
| ![MiniOS](https://img.shields.io/badge/MiniOS-Website-orange?style=flat&logo=linux) | [MiniOS Official Website](https://minios.dev/) | Website resmi MiniOS |
| ![GenieACS](https://img.shields.io/badge/GenieACS-Website-red?style=flat&logo=server) | [GenieACS Official Website](https://genieacs.com/) | Website resmi GenieACS |

</div>

---

<div align="center">

## 🤝 Kontribusi

![Contributions Welcome](https://img.shields.io/badge/Contributions-Welcome-brightgreen?style=for-the-badge)

Jika Anda menemukan kesalahan atau ingin menambahkan informasi, silakan buat issue atau pull request.

## 📄 Lisensi

![License](https://img.shields.io/badge/License-Free%20to%20Use-green?style=for-the-badge)

Tutorial ini tersedia secara bebas untuk digunakan dan dimodifikasi.

---

<div align="center">

**⭐ Jika tutorial ini membantu, berikan star pada repository ini! ⭐**

Made with ❤️ for the Indonesian tech community

</div>

</div>