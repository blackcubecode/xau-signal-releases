📘 Panduan Admin — XAU Signal Bot Telegram
> **Dokumen internal rahasia — jangan dibagikan kepada pembeli atau dipublikasikan.**
Informasi	Detail
Versi dokumen	1.0
Terakhir diperbarui	26 Oktober 2026
Admin	`blackcubecode`
⚠️ Kerahasiaan dan Penyimpanan
Dokumen ini memuat prosedur internal dan informasi sensitif. Jangan:
Commit dokumen ini ke repositori Git mana pun.
Mengirim dokumen ini kepada pembeli.
Menyimpannya di folder yang dapat diakses publik.
Mengunggahnya ke cloud publik.
Simpan di password manager (Bitwarden, 1Password, atau KeePass) dan folder lokal terenkripsi.
> **Peringatan keamanan:** secret lisensi pernah tercantum dalam dokumen sumber yang dibagikan ke percakapan ini. Demi keamanan, anggap secret tersebut sudah terekspos dan rotasi secret sebelum digunakan untuk menerbitkan lisensi baru. Jangan menyalin secret lama ke dokumentasi publik.

1. INFORMASI KRITIS

1.1 Secret License
```text
LICENSE_SECRET = [REDACTED — AMBIL DARI PASSWORD MANAGER]
```
Fungsi: Kunci utama untuk generate license key. Semua key di-generate dari (chat_id + secret).
Kalau hilang: Tidak bisa generate key baru → pembeli lama tidak bisa di-reset → harus generate secret baru → semua key lama tidak valid.
Simpan di: password manager, minimal 2 tempat (Bitwarden + KeePass).

1.2 Lokasi Project
```text
E:\Applications\EA\xau_signal\bots\xau_signal
File penting:

license_check.py — verifikasi lisensi (secret obfuscated)

telegram_bot.py — bot utama

.env — konfigurasi (JANGAN commit)

.env.example — template untuk pembeli
```

1.3 Repo GitHub
Repo	Fungsi	Visibility
xau_signal-bot-telegram	Source code utama	Private
xau-signal-releases	Distribusi paket .tar.gz	Private

1.4 Kontak Penjual
```text
Telegram : @blackcubecodeadmin
Email    : blackcubecodex@gmail.com
GitHub   : @blackcubecode
```

2. PERSIAPAN AWAL (SEKALI SAJA)

2.1 Install Python
Download Python 3.10+ dari https://www.python.org/downloads/
Saat install, centang "Add Python to PATH"
Verifikasi: python --version

2.2 Install dependencies
```powershell
cd "E:\Applications\EA\xau_signal\bots\xau_signal"
pip install -r requirements.txt
```

2.3 Set secret di password manager
Buat entri:
```text
Nama     : XAU Signal Bot - LICENSE_SECRET
Username : blackcubecode
Password : [REDACTED — AMBIL DARI PASSWORD MANAGER]
Catatan  : Secret untuk generate license key pembeli
```

3. ALUR JUAL KE PEMBELI BARU

3.1 Pembeli menghubungi via Telegram
Template balasan pertama:
```text
Halo 👋

Terima kasih sudah tertarik dengan XAU Signal Bot Telegram.

📦 Paket: XAU Signal Bot v1.1
💰 Harga: [HARGA]
💳 Pembayaran: QRIS / Transfer Bank

Untuk pembelian:
```

1. Transfer ke [REKENING/QRIS]

2. Kirim bukti transfer

3. Kirim Chat ID Telegram Anda (dari @userinfobot)

Setelah pembayaran dikonfirmasi, saya kirim:
File paket (.tar.gz)
License key
Panduan instalasi
🆘 Bantuan: @blackcubecodeadmin
3.2 Pembeli transfer & kirim bukti
Konfirmasi pembayaran diterima.

3.3 Minta Chat ID pembeli
Template:
```text
Terima kasih, pembayaran sudah diterima ✅

Sekarang saya butuh Chat ID Telegram Anda:
```

1. Buka Telegram, cari @userinfobot

2. Kirim /start

3. Bot akan balas dengan ID Anda (angka)

4. Copy & kirim ke saya

Chat ID ini akan didaftarkan untuk license key Anda.
3.4 Generate license key
```powershell
cd "E:\Applications\EA\xau_signal\bots\xau_signal"
python license_check.py <CHAT_ID_PEMBELI>
```
Contoh:
```powershell
python license_check.py 987654321
```
Output:
```text
Chat ID : 987654321
Key     : a1b2c3d4e5f6g7h8i9j0k1l2m3n4o5p6
```
Copy key itu.

3.5 Catat di tracking
Buka Excel/Google Sheets/Notion, tambahkan baris:
Tanggal	Nama	Telegram	Chat ID	License Key	Versi	Status	Catatan
2026-10-26	Budi	@budi	987654321	a1b2c3d4e5f6...	v1.1	✅ Active	-

3.6 Kirim paket + key ke pembeli
Attach file xau_signal-bot-v1.1.tar.gz ke chat Telegram, lalu kirim pesan:
```text
Halo [Nama] 👋

Terima kasih sudah membeli *XAU Signal Bot Telegram v1.1*!

📦 *Paket*: xau_signal-bot-v1.1.tar.gz (terlampir)
🔑 *License Key*: a1b2c3d4e5f6g7h8i9j0k1l2m3n4o5p6
🆔 *Chat ID terdaftar*: 987654321

📖 Panduan lengkap ada di README.md di dalam paket.

⚠️ *Penting*:
• Jangan bagikan license key ke orang lain
• License terikat ke Chat ID Anda — tidak bisa dipindah
• Simpan key ini di tempat aman

🆘 Bantuan: @blackcubecodeadmin
```

4. CARA PEMBELI INSTALL
Kirim juga panduan ini (atau cukup arahkan ke README di paket):

4.1 Extract paket
Windows (PowerShell):
```powershell
tar -xzf xau_signal-bot-v1.1.tar.gz
cd xau_signal
```

4.2 Buat virtual environment
```powershell
python -m venv .venv
.\.venv\Scripts\Activate.ps1
```

4.3 Install dependencies
```powershell
pip install -r requirements.txt
```

4.4 Buat bot Telegram sendiri
Buka Telegram, cari @BotFather
Kirim /newbot
Kasih nama bot (bebas)
Kasih username bot (harus diakhiri bot)
BotFather kasih token (format 123456789:ABCdef...)
Copy token

4.5 Isi .env
```powershell
Copy-Item .env.example .env
notepad .env
```
Isi:
```ini
TELEGRAM_BOT_TOKEN=<token_dari_botfather>
TELEGRAM_CHAT_ID=<chat_id_pembeli>
XAU_LICENSE_KEY=<key_dari_admin>
```

4.6 Jalankan bot
```powershell
python telegram_bot.py
```
Ekspektasi:
```text
✅ Lisensi valid. Bot siap dijalankan.
...
Telegram connected: @bot_pembeli
```

5. TROUBLESHOOTING PEMBELI

5.1 ❌ LISENSI TIDAK DITEMUKAN
Penyebab: `.env` tidak ada / kosong / format salah.
Solusi:
Cek `.env` ada di folder yang sama dengan telegram_bot.py
Cek isi `.env`:
```powershell
Get-Content .env
Pastikan 3 baris:

text
TELEGRAM_BOT_TOKEN=...
TELEGRAM_CHAT_ID=...
XAU_LICENSE_KEY=...
```
Tidak ada spasi di sekitar =
Tidak pakai tanda kutip

5.2 ❌ LISENSI TIDAK VALID
Penyebab: key tidak cocok dengan chat ID.
Solusi:
Cek chat ID di `.env` = chat ID yang didaftarkan
Cek key di `.env` = key yang dikirim admin
Cek tidak ada spasi / karakter nyasar
Kalau masih gagal: minta pembeli kirim screenshot `.env` (sensor token), lalu verifikasi:
```powershell
# Di komputer admin
python license_check.py <chat_id_pembeli>
# Bandingkan output dengan key yang dikirim
```

5.3 Telegram connection failed: Unauthorized
Penyebab: token bot salah / sudah di-revoke.
Solusi:
Buka @BotFather → /mybots → pilih bot → API Token
Kalau token beda dengan `.env` → update `.env`
Kalau token sudah di-revoke → generate baru

5.4 Chat not found
Penyebab: bot belum di-/start di chat pembeli, atau chat ID salah.
Solusi:
Pembeli kirim /start ke bot mereka
Cek chat ID via @userinfobot
Kalau kirim ke grup/channel: tambahkan bot sebagai admin

5.5 ModuleNotFoundError
Penyebab: dependencies belum ter-install.
Solusi:
```powershell
pip install -r requirements.txt
```

5.6 Error lain
Minta pembeli kirim:
Screenshot error
Output python telegram_bot.py
Versi Python: python --version

6. RESET LICENSE (GANTI CHAT ID)

6.1 Kapan perlu reset?
Pembeli ganti HP / akun Telegram → Chat ID berubah
Pembeli pindah dari chat pribadi ke channel
Pembeli minta reset (alasan wajar)

6.2 Prosedur reset
Step 1 — Konfirmasi ke pembeli:
```text
Halo [Nama],

Untuk reset license, konfirmasi:
1️⃣ Chat ID lama: [CHAT_ID_LAMA]
2️⃣ Chat ID baru: [CHAT_ID_BARU]
3️⃣ Alasan: [ALASAN]

```
Setelah dikonfirmasi, saya kirim key baru dalam 1×24 jam.
Step 2 — Generate key baru:
```powershell
cd "E:\Applications\EA\xau_signal\bots\xau_signal"
python license_check.py <CHAT_ID_BARU>
```
Step 3 — Kirim key baru:
```text
Halo [Nama],

License key baru untuk Chat ID [CHAT_ID_BARU]:

🔑 [KEY_BARU]

Update `.env` Anda:
TELEGRAM_CHAT_ID=[CHAT_ID_BARU]
XAU_LICENSE_KEY=[KEY_BARU]

Key lama tidak berlaku lagi. 🙏
```
Step 4 — Update tracking:
Baris lama: status → Revoked (reset)
Tambah baris baru: chat ID baru, key baru, status Active
Catatan: Key lama secara teknis masih valid untuk chat ID lama. Tapi secara sosial, kamu bilang "tidak berlaku". Kalau curiga disalahgunakan, blokir di Telegram.

7. UPDATE VERSI BOT

7.1 Kapan update?
Ada bug fix
Ada fitur baru
Ada perubahan strategi

7.2 Prosedur update
Step 1 — Edit source code di folder asli:
```powershell
cd "E:\Applications\EA\xau_signal\bots\xau_signal"
```
Step 2 — Test lokal:
```powershell
python telegram_bot.py
# Pastikan ✅ Lisensi valid + bot jalan
```
Step 3 — Buat paket baru:
```powershell
cd "E:\Applications\EA\xau_signal\bots"
tar -czf "E:\Applications\EA\xau_signal-bot-v1.2.tar.gz" `
    --exclude="xau_signal/.env" `
    --exclude="xau_signal/.git" `
    --exclude="xau_signal/__pycache__" `
    --exclude="xau_signal/*.db" `
    --exclude="xau_signal/*.bak-*" `
    --exclude="xau_signal/*.backup_*" `
    --exclude="xau_signal/backups" `
    --exclude="xau_signal/backup_*" `
    --exclude="xau_signal/server" `
    xau_signal
```
Step 4 — Upload ke GitHub Release:
Buka https://github.com/blackcubecode/xau-signal-releases/releases/new
Tag: v1.2
Title: v1.2 — [Deskripsi update]
Attach: xau_signal-bot-v1.2.tar.gz
Publish
Step 5 — Beri tahu pembeli lama (opsional):
```text
Halo [Nama],

Update XAU Signal Bot v1.2 sudah tersedia!

📦 Download: [LINK]
📝 Yang baru: [DESKRIPSI]

License key Anda tetap berlaku — tidak perlu generate baru.
```

8. TRACKING PEMBELI

8.1 Template Excel/Google Sheets
Kolom	Keterangan
Tanggal	Tanggal transaksi
Nama	Nama pembeli
Telegram	Username Telegram
Email	Email (opsional)
Chat ID	ID terdaftar
License Key	Key yang dikirim
Versi	v1.0 / v1.1 / dst
Harga	Nominal
Metode Bayar	QRIS / Transfer
Status	Active / Refund / Revoked
Catatan	Reset, ganti chat ID, dll

8.2 Contoh baris
Tanggal	Nama	Telegram	Chat ID	License Key	Versi	Harga	Status	Catatan
2026-10-26	Budi	@budi	987654321	a1b2c3d4...	v1.1	150k	✅ Active	-
2026-10-27	Siti	@siti	123456789	e5f6g7h8...	v1.1	350k	✅ Active	Pro

8.3 Backup tracking
Simpan di Google Sheets (auto-backup)
Export ke Excel setiap minggu
Simpan di folder lokal terenkripsi

9. KEAMANAN

9.1 Yang HARUS dilakukan
✅ Simpan LICENSE_SECRET di password manager
✅ Ganti token bot jika bocor
✅ Repo GitHub: private
✅ File .env: jangan commit
✅ Tracking: simpan di tempat aman
✅ Backup secret minimal 2 tempat

9.2 Yang TIDAK boleh dilakukan
❌ Kirim LICENSE_SECRET ke pembeli
❌ Commit .env ke Git
❌ Upload ADMIN_GUIDE.md ke repo publik
❌ Share link download publik (tanpa kontrol)
❌ Pakai token bot yang sudah bocor

9.3 Kalau secret bocor
Segera generate secret baru:
```powershell
$secret = -join ((48..57) + (65..90) + (97..122) | Get-Random -Count 32 | ForEach-Object {[char]$_})
"Secret baru: $secret"
```
Update license_check.py dengan secret baru (obfuscated)
Generate key baru untuk semua pembeli
Kirim key baru ke semua pembeli
Update tracking

9.4 Kalau token bot bocor
Buka @BotFather → /mybots → pilih bot → API Token → Revoke current token
Generate token baru
Update `.env` admin
(Pembeli pakai token bot masing-masing — tidak terpengaruh)

10. DAFTAR PERINTAH CEPAT

10.1 Generate license key
```powershell
cd "E:\Applications\EA\xau_signal\bots\xau_signal"
python license_check.py <CHAT_ID>
```

10.2 Test bot lokal
```powershell
cd "E:\Applications\EA\xau_signal\bots\xau_signal"
python telegram_bot.py
```

10.3 Buat paket baru
```powershell
cd "E:\Applications\EA\xau_signal\bots"
tar -czf "E:\Applications\EA\xau_signal-bot-v1.X.tar.gz" `
    --exclude="xau_signal/.env" `
    --exclude="xau_signal/.git" `
    --exclude="xau_signal/__pycache__" `
    --exclude="xau_signal/*.db" `
    --exclude="xau_signal/*.bak-*" `
    --exclude="xau_signal/*.backup_*" `
    --exclude="xau_signal/backups" `
    --exclude="xau_signal/backup_*" `
    --exclude="xau_signal/server" `
    xau_signal
```

10.4 Verifikasi paket
```powershell
tar -tzf "E:\Applications\EA\xau_signal-bot-v1.X.tar.gz"
```

10.5 Cek secret (untuk verifikasi)
```powershell
# JANGAN jalankan di tempat publik
cd "E:\Applications\EA\xau_signal\bots\xau_signal"
python -c "from license_check import _get_secret; print('Secret length:', len(_get_secret()))"
```
Ekspektasi: Secret length: 32

11. KONTAK DARURAT
Keperluan	Kontak
Bantuan teknis	@blackcubecodeadmin
Email	blackcubecodex@gmail.com
GitHub	https://github.com/blackcubecode

12. CATATAN PENTING
Secret [REDACTED — AMBIL DARI PASSWORD MANAGER] — simpan di password manager. Kalau hilang, tidak bisa generate key baru.
Token bot — jangan pernah share. Kalau bocor, revoke via @BotFather.
Tracking pembeli — simpan di tempat aman, jangan di repo publik.
Test dulu sebelum kirim ke pembeli — pastikan ✅ Lisensi valid muncul.
Backup folder project setiap minggu ke Google Drive / external drive.
© 2026 blackcubecode. All rights reserved.
Dokumen internal — jangan disebarkan.
</parameter>
