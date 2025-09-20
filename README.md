# 🖥️ Windows Environment on Demand

Proyek ini menyediakan cara sederhana untuk men-deploy lingkungan Windows yang bersih dan sementara, langsung dari GitHub Actions. Dapatkan akses ke antarmuka grafis Windows lengkap sesuai permintaan, sempurna untuk pengujian, pengembangan, atau menjalankan aplikasi spesifik Windows tanpa perlu mesin virtual lokal.

## ✨ Fitur Utama

*   🚀 **Deployment Sesuai Permintaan**: Jalankan alur kerja kapan pun Anda membutuhkan lingkungan Windows yang baru.
*   🔧 **Setup yang Dapat Disesuaikan**: Gunakan skrip PowerShell Anda sendiri dari Gist untuk menginstal perangkat lunak atau konfigurasi yang Anda butuhkan secara otomatis.
*   🔒 **Koneksi Terowongan Aman**: Menggunakan Ngrok untuk membuat koneksi yang aman dan dapat diakses ke lingkungan Anda dari mana saja.
*   ☁️ **Berbasis Cloud Penuh**: Tidak memerlukan instalasi atau konfigurasi di komputer lokal Anda. Semuanya berjalan di infrastruktur GitHub.

## ⚙️ Cara Kerjanya

Alur kerja ini mengotomatiskan seluruh proses untuk Anda:

1.  **📥 Unduh Skrip**: Alur kerja mengambil skrip setup PowerShell kustom Anda dari URL Gist yang Anda sediakan.
2.  **⚙️ Eksekusi**: Skrip tersebut dijalankan di dalam sebuah runner Windows, mempersiapkan lingkungan, menginstal aplikasi, dan mengatur pengguna.
3.  **🔗 Buat Terowongan**: Sebuah terowongan (tunnel) yang aman dibuat menggunakan Ngrok, yang memaparkan port koneksi lingkungan ke internet publik.
4.  **📊 Tampilkan Detail**: Alamat dan port unik untuk koneksi Anda akan ditampilkan di log alur kerja, siap untuk Anda gunakan.

## 🚀 Panduan Memulai

Ikuti langkah-langkah ini untuk menjalankan lingkungan Windows pertama Anda.

### 1. Prasyarat

*   Akun GitHub.
*   Akun [Ngrok](https://ngrok.com/) (akun gratis sudah cukup).

### 2. Konfigurasi: Atur Token Ngrok Anda

Alur kerja ini memerlukan token autentikasi Ngrok Anda untuk membuat terowongan yang aman. Anda harus menyimpannya sebagai *secret* di repositori Anda.

1.  Salin **Auth Token** Anda dari [dashboard Ngrok Anda](https://dashboard.ngrok.com/get-started/your-authtoken).
2.  Di repositori GitHub Anda, buka **Settings** > **Secrets and variables** > **Actions**.
3.  Klik **New repository secret**.
4.  Beri nama secret `NGROK_AUTH_TOKEN`.
5.  Tempelkan Auth Token Anda ke dalam kolom **Secret**.
6.  Klik **Add secret**.

### 3. Jalankan Alur Kerja

1.  Buka tab **Actions** di repositori Anda.
2.  Di bawah daftar alur kerja di sebelah kiri, pilih **"🖥️ Deploy Windows Environment 🚀"**.
3.  Klik tombol **Run workflow** di sebelah kanan.
4.  (Opsional) Anda dapat mengubah **URL Gist** jika Anda ingin menggunakan skrip setup kustom Anda sendiri.
5.  Klik tombol hijau **Run workflow**.

### 4. Hubungkan ke Lingkungan Anda

Setelah alur kerja dimulai, navigasikan ke halaman ringkasan proses yang sedang berjalan.

1.  Tunggu hingga tugas eksekusi utama berjalan.
2.  Klik tugas tersebut untuk melihat output log secara langsung.
3.  Di akhir log, Anda akan melihat sebuah kotak yang dicetak dengan jelas berisi detail koneksi.

    ```text
    +-----------------------------------------------------------------+
    |                                                                 |
    |   ✅💻 LINGKUNGAN WINDOWS ANDA TELAH SIAP! 💻✅                 |
    |                                                                 |
    +-----------------------------------------------------------------+
    |   Gunakan detail di bawah ini untuk memulai sesi grafis Anda:     |
    |                                                                 |
    |   🖥️  Alamat (IP/Hostname) : 0.tcp.ngrok.io:12345               |
    |   👤  Username             : (Sesuai skrip Anda)                |
    |   🔑  Password             : (Sesuai skrip Anda)                |
    |                                                                 |
    +-----------------------------------------------------------------+
    ```
4.  Gunakan alamat dan kredensial tersebut dengan klien koneksi desktop jarak jauh pilihan Anda untuk mengakses antarmuka grafis Windows.

Lingkungan akan tetap aktif hingga alur kerja mencapai batas waktu (timeout) 360 menit atau Anda membatalkannya secara manual.

## 🔧 Kustomisasi

Anda dapat dengan mudah menyesuaikan lingkungan dengan memodifikasi skrip PowerShell. Cukup buat Gist publik Anda sendiri dengan file `setup.ps1` dan masukkan URL mentahnya saat menjalankan alur kerja. Ini memungkinkan Anda untuk:

*   Menginstal perangkat lunak spesifik (misalnya, `winget install vscode`).
*   Mengatur variabel lingkungan.
*   Mengunduh dan mengonfigurasi file proyek.

## 📄 Lisensi

Proyek ini dilisensikan di bawah [Lisensi MIT](LICENSE).
