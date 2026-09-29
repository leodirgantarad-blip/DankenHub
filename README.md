DANKEN APP HUB v3.0

<p align="center">██████╗  █████╗ ███╗   ██╗██╗  ██╗███████╗███╗   ██╗
 ██╔══██╗██╔══██╗████╗  ██║██║ ██╔╝██╔════╝████╗  ██║
 ██║  ██║███████║██╔██╗ ██║█████╔╝ █████╗  ██╔██╗ ██║
 ██║  ██║██╔══██║██║╚██╗██║██╔═██╗ ██╔══╝  ██║╚██╗██║
 ██████╔╝██║  ██║██║ ╚████║██║  ██╗███████╗██║ ╚████║
 ╚═════╝ ╚═╝  ╚═╝╚═╝  ╚═══╝╚═╝  ╚═╝╚══════╝╚═╝  ╚═══╝

"DANKEN APP HUB"

ANDROID TERMINAL APPLICATION LAUNCHER

"Termux • Android • Python • Cyber UI"

</p>---

[*] About

DANKEN APP HUB adalah application launcher berbasis Python + Termux yang dirancang untuk memberikan pengalaman seperti mini application center langsung dari terminal Android.

Dengan satu dashboard, kamu dapat membuka aplikasi Android, browser, mencari package, melakukan scanning aplikasi, melihat informasi perangkat, dan menjalankan package secara manual.

«DANKEN APP HUB bukan emulator Android.
Aplikasi tetap dijalankan oleh sistem Android melalui Android Intent/command yang dipanggil dari Termux.»

---

[+] Features

Feature| Status
Application Launcher| "[+]"
Browser Launcher| "[+]"
Smart App Search| "[+]"
Favorite Applications| "[+]"
Android Package Scanner| "[+]"
Custom Package Launcher| "[+]"
Device Information| "[+]"
Cyber Terminal Dashboard| "[+]"
Boot Animation| "[+]"
JSON Configuration| "[+]"
External Python Dependencies| "NONE"

---

[>] Dashboard

╔══════════════════════════════════════════════════════════════════════════╗
║ D A N K E N   A P P   H U B                                             ║
╠══════════════════════════════════════════════════════════════════════════╣
║ DASHBOARD                                                                ║
╚══════════════════════════════════════════════════════════════════════════╝

  ● SYSTEM ONLINE    Android launcher ready

  [ 1] APPLICATIONS        Launch apps
  [ 2] BROWSER             Open any website
  [ 3] FAVORITES            Quick launch
  [ 4] APP SCANNER          Detect installed packages
  [ 5] SMART SEARCH         Find app/package
  [ 6] CUSTOM LAUNCH        Launch package manually
  [ 7] DEVICE STATUS        Android information
  [ 8] REFRESH              Reload config
  [ 0] EXIT                 Close launcher

  DANKEN@HUB >

---

[!] Requirements

Android

- Android device
- Termux
- Python 3
- Permission/availability untuk menjalankan Android commands

Python

Tidak membutuhkan:

numpy
requests
rich
colorama

atau library Python eksternal lainnya.

Project menggunakan Python standard library sehingga instalasinya tetap ringan.

---

[+] Installation

1. Install Python

Di Termux:

pkg update
pkg install python

---

2. Clone Repository

git clone https://github.com/leodirgantarad-blip/DankenHub

Masuk ke folder:

cd DANKEN-APP-HUB

---

3. Run

python danken_app_hub.py

Atau menggunakan launcher:

chmod +x start.sh
./start.sh

---

[>] Quick Start

Setelah menjalankan:

python danken_app_hub.py

kamu akan melihat boot sequence DANKEN.

DANKEN APP HUB
      ↓
SYSTEM INITIALIZING
      ↓
ANDROID TERMINAL INTERFACE
      ↓
DASHBOARD

Kemudian pilih menu menggunakan nomor.

Contoh:

DANKEN@HUB > 1

untuk membuka Application Launcher.

---

[*] Application Launcher

Menu:

[1] APPLICATIONS

menampilkan daftar aplikasi yang tersimpan pada konfigurasi.

Contoh:

[ 1] Chrome                  com.android.chrome
[ 2] Firefox                 org.mozilla.firefox
[ 3] YouTube                 com.google.android.youtube
[ 4] Termux                  com.termux
[ 5] Settings                com.android.settings

Pilih nomor aplikasi:

DANKEN@HUB > 1

Android kemudian akan menerima perintah launcher.

---

[*] Browser

Gunakan:

[2] BROWSER

Kemudian masukkan:

google.com

atau:

https://github.com

DANKEN APP HUB akan menggunakan Android Intent untuk membuka URL melalui browser yang tersedia.

---

[*] Smart Search

Gunakan:

[5] SMART SEARCH

Pencarian dapat dilakukan berdasarkan:

Application Name
Package Name

Contoh:

Search > chrome

Hasil:

[ 1] Chrome
     com.android.chrome

---

[*] App Scanner

Gunakan:

[4] APP SCANNER

Scanner akan mencoba membaca package yang tersedia melalui:

pm list packages

Kemudian database aplikasi akan diperbarui.

---

[*] Custom Launch

Jika mengetahui package aplikasi, gunakan:

[6] CUSTOM LAUNCH

Contoh:

Package > com.android.chrome

DANKEN kemudian mencoba menjalankan package tersebut.

---

[*] Device Status

Menu:

[7] DEVICE STATUS

menampilkan informasi dasar Android seperti:

Brand
Model
Android Version
SDK
Installed Packages

---

[>] Project Structure

DANKEN-APP-HUB/
│
├── danken_app_hub.py
├── start.sh
├── README.md
│
├── core/
│   ├── __init__.py
│   ├── ui.py
│   ├── android.py
│   └── apps.py
│
├── config/
│   └── apps.json
│
├── data/
│   └── favorites.json
│
└── assets/
    └── README.txt

---

[*] Core Architecture

                 DANKEN APP HUB
                        │
                        ▼
               ┌─────────────────┐
               │ danken_app_hub  │
               │      .py        │
               └────────┬────────┘
                        │
          ┌─────────────┼─────────────┐
          ▼             ▼             ▼
      UI ENGINE     ANDROID CORE   APP MANAGER
          │             │             │
          ▼             ▼             ▼
       Terminal       am / pm       JSON
       Dashboard      Intent        Config
          │             │             │
          └─────────────┼─────────────┘
                        ▼
                 ANDROID SYSTEM
                        │
             ┌──────────┼──────────┐
             ▼          ▼          ▼
          Browser      Apps      Settings

---

[!] Important

DANKEN APP HUB tidak menjalankan APK menggunakan emulator.

Cara kerjanya adalah:

Termux
   │
   ▼
DANKEN APP HUB
   │
   ▼
Android Command / Intent
   │
   ▼
Android System
   │
   ▼
Application

Jadi APK tetap berjalan sebagai aplikasi Android normal.

---

[!] Troubleshooting

"am" tidak ditemukan

Jika muncul:

Command Android 'am' tidak tersedia

maka environment Termux tidak menyediakan command Android tersebut.

UI DANKEN tetap dapat berjalan, tetapi fungsi launcher Android tidak dapat digunakan.

---

"pm" tidak ditemukan

Jika scanner tidak mendapatkan aplikasi:

APP SCANNER

pastikan command:

which pm

tersedia.

---

Python tidak ditemukan

Install:

pkg install python

Kemudian:

python --version

---

[+] Configuration

Database aplikasi terdapat pada:

config/apps.json

Contoh:

[
  {
    "name": "Chrome",
    "package": "com.android.chrome",
    "favorite": true
  }
]

Kamu dapat menambahkan package aplikasi lain sesuai kebutuhan.

---

[>] Development

Clone repository:

git clone https://github.com/USERNAME/DANKEN-APP-HUB.git
cd DANKEN-APP-HUB

Jalankan:

python danken_app_hub.py

Untuk mengembangkan fitur, bagian utama berada di:

core/

---

[*] Roadmap

v3.0

- [x] Cyber dashboard
- [x] Application launcher
- [x] Browser launcher
- [x] Package scanner
- [x] Smart search
- [x] Favorites
- [x] Device information
- [x] Custom launcher
- [x] JSON configuration

Future

[ ] Dynamic app icons
[ ] App categories
[ ] Recent applications
[ ] Custom themes
[ ] Theme editor
[ ] Terminal animation engine
[ ] Plugin system
[ ] Profile system
[ ] Advanced Android integration
[ ] DANKEN command system

---

[!] Security & Privacy

DANKEN APP HUB dirancang sebagai launcher lokal.

Project ini:

- Tidak membutuhkan database online
- Tidak membutuhkan API key
- Tidak mengirim package list ke server
- Tidak membutuhkan akun
- Tidak melakukan remote control terhadap perangkat lain
- Tidak dirancang untuk menyerang sistem lain

Gunakan project hanya pada perangkat dan lingkungan yang kamu miliki atau memiliki izin untuk mengelolanya.

---

[*] License

Project ini dapat dikembangkan dan dimodifikasi sesuai kebutuhan repository.

Jika kamu melakukan fork atau modifikasi besar, disarankan mencantumkan project asli:

DANKEN APP HUB
Original Project by DANKEN

---

[>] Credits

╔══════════════════════════════════════════╗
║                                          ║
║          D A N K E N   A P P             ║
║              H U B                       ║
║                                          ║
║        ANDROID TERMINAL EDITION          ║
║                                          ║
║             DANKEN PROJECT               ║
║                                          ║
╚══════════════════════════════════════════╝

Built with Python + Termux + Android Intent

---

DANKEN

«"BUILD • TEST • CREATE • UPDATE"»

<p align="center">[ SYSTEM ONLINE ]
[ DANKEN CORE ]
[ ANDROID READY ]
[ TERMINAL READY ]

</p>
