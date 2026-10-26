# XAU Signal Bot Telegram — Releases

Repositori ini menyediakan rilis resmi **XAU Signal Bot Telegram** yang siap diunduh oleh pembeli dengan akses dan lisensi resmi.

## 📥 Download Versi Terbaru

1. Buka tab **Releases** pada repositori GitHub ini.
2. Pilih versi terbaru yang tersedia.
3. Unduh file paket rilis, misalnya `xau_signal-bot-v1.0.tar.gz`.
4. Simpan file di komputer atau server yang akan digunakan untuk menjalankan bot.

Pastikan Anda mengunduh paket dari rilis resmi repositori ini.

## 🔑 Instalasi dan Aktivasi

### 1. Extract Paket

Buka terminal pada direktori tempat file rilis diunduh, lalu jalankan:

```bash
tar -xzf xau_signal-bot-v1.0.tar.gz
cd xau_signal
```

Sesuaikan nama file arsip dengan versi yang Anda unduh.

### 2. Baca Panduan Instalasi

Buka file `README.md` yang tersedia di dalam paket dan ikuti petunjuk instalasi sesuai lingkungan sistem Anda.

Pastikan Python dan seluruh dependensi yang diperlukan telah terpasang.

### 3. Konfigurasi File `.env`

Buat atau edit file `.env` sesuai petunjuk instalasi, kemudian isi variabel berikut:

```dotenv
TELEGRAM_BOT_TOKEN=isi_token_bot_anda
TELEGRAM_CHAT_ID=isi_chat_id_anda
XAU_LICENSE_KEY=isi_kunci_lisensi_anda
```

**Keterangan konfigurasi:**

- `TELEGRAM_BOT_TOKEN` — token bot Telegram yang diperoleh melalui [@BotFather](https://t.me/BotFather).
- `TELEGRAM_CHAT_ID` — ID chat atau grup Telegram tujuan pengiriman sinyal. Pastikan bot memiliki akses yang diperlukan.
- `XAU_LICENSE_KEY` — kunci lisensi resmi yang diberikan penjual secara terpisah.

**Penting:** Ganti seluruh nilai contoh dengan nilai yang benar. Jangan membagikan token bot atau kunci lisensi kepada pihak lain. Jangan mengunggah file `.env` ke repositori publik.

### 4. Jalankan Bot

Setelah konfigurasi selesai dan dependensi terpasang, jalankan:

```bash
python telegram_bot.py
```

Jika sistem menggunakan perintah `python3`, gunakan:

```bash
python3 telegram_bot.py
```

Periksa keluaran terminal untuk memastikan bot berjalan tanpa kesalahan. Jika diperlukan, ikuti petunjuk aktivasi lisensi yang tersedia di dalam paket.

## 💝 Donasi dan Dukungan Pengembangan

Dukung pengembangan, pemeliharaan, dan peningkatan **XAU Signal Bot Telegram** melalui donasi QRIS.

<p align="center">
  <img
    src="qris.jpg"
    width="300"
    alt="QRIS Donasi Black Cube Code"
  >
</p>

<p align="center">
  <strong>Black Cube Code</strong><br>
  Terima kasih atas dukungan dan kontribusi Anda!
</p>

Donasi bersifat sukarela dan digunakan untuk mendukung pengembangan serta pemeliharaan proyek.

Pastikan file `qris.jpg` berada di direktori yang sama dengan file `README.md` agar gambar QRIS dapat ditampilkan dengan benar di GitHub.

## 🆘 Bantuan dan Dukungan Teknis

Jika mengalami kendala instalasi, konfigurasi, atau aktivasi lisensi, silakan hubungi dukungan resmi:

- **Telegram:** [@blackcubecodeadmin](https://t.me/blackcubecodeadmin)
- **Email:** [blackcubecodex@gmail.com](mailto:blackcubecodex@gmail.com)

Saat menghubungi dukungan, sertakan informasi versi rilis, sistem operasi, dan pesan kesalahan yang relevan.

Jangan mengirimkan token bot, kata sandi, atau kunci lisensi melalui pesan publik.

## 📄 Lisensi dan Hak Penggunaan

Perangkat lunak ini merupakan perangkat lunak proprietary yang dilindungi oleh hak kekayaan intelektual pemiliknya.

Dilarang menyalin, memodifikasi, menjual kembali, mendistribusikan ulang, atau membagikan paket perangkat lunak maupun kunci lisensi tanpa izin tertulis dari pemilik hak, kecuali jika secara tegas diizinkan oleh perjanjian lisensi yang berlaku.

Pembelian produk memberikan hak penggunaan sesuai ketentuan lisensi yang diberikan oleh penjual. Pembelian tidak secara otomatis mengalihkan kepemilikan hak cipta perangkat lunak.

## ⚠️ Penafian Risiko Trading

Jika perangkat lunak digunakan untuk menghasilkan sinyal trading emas (XAU/USD), harap perhatikan hal-hal berikut:

- Sinyal yang dihasilkan bukan jaminan keuntungan.
- Aktivitas trading memiliki risiko kerugian finansial.
- Pengguna bertanggung jawab atas keputusan trading yang diambil.
- Hasil historis tidak menjamin hasil pada masa mendatang.

Gunakan perangkat lunak secara bijak dan sesuaikan keputusan trading dengan toleransi risiko masing-masing.

---

<p align="center">
  <strong>XAU Signal Bot Telegram</strong><br>
  Developed by Black Cube Code<br>
  © All Rights Reserved.
</p>
