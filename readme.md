# 💳 CashFlow

> Manajemen keuangan pribadi dengan dua antarmuka: **Bot Telegram** untuk input cepat dan **Web Dashboard** untuk melihat riwayat transaksi — bisa diakses dari mana saja, sistem bekerja secara manual di input oleh user.

![Python](https://img.shields.io/badge/Python-3.x-blue?logo=python) ![Flask](https://img.shields.io/badge/Flask-Web%20Framework-black?logo=flask) ![SQLite](https://img.shields.io/badge/Database-SQLite-blue?logo=sqlite) ![License](https://img.shields.io/badge/License-MIT-green)

---

## Cara Kerja

Bot Telegram menerima input transaksi dan menyimpannya ke SQLite. Flask web server membaca database yang sama dan menampilkannya sebagai dashboard yang bisa dibuka dari browser.

```
Telegram → bot.py → finance.db → app.py → Web Dashboard
```

---

## Fitur

- 📥 Input pemasukan & pengeluaran via Telegram
- 💰 Saldo otomatis terupdate setiap transaksi
- 📊 Web dashboard dengan riwayat transaksi lengkap
- ✏️ Edit & hapus transaksi dari web (dilindungi password)
- 🔒 Hanya User ID terdaftar yang bisa akses bot

---

## Cara Setup

**1. Clone & install**
```bash
git clone https://github.com/MrElixir1945/CashFlow.git
cd CashFlow
pip install -r requirements.txt
```

**2. Konfigurasi `.env`**
```bash
cp .env.example .env
```

Isi file `.env`:
```env
TELEGRAM_TOKEN=token_bot_telegram_kamu
ALLOWED_USER_ID=user_id_telegram_kamu
ADMIN_PASSWORD=password_untuk_edit_di_web
PUBLIC_URL=https://domain-kamu.ts.net
```

> Cara dapat `ALLOWED_USER_ID`: chat ke [@userinfobot](https://t.me/userinfobot) di Telegram.

**3. Jalankan**
```bash
# Terminal 1 - Bot
python bot.py

# Terminal 2 - Web Dashboard
python app.py
```

**4. Buka dashboard**
```
http://localhost:5000/dashboard?uid=USER_ID_KAMU
```

---

## Akses Public (Opsional)

Untuk mengakses dashboard dari luar jaringan rumah, gunakan [Tailscale Funnel](https://tailscale.com):
```bash
curl -fsSL https://tailscale.com/install.sh | sh
tailscale up
tailscale funnel 5000
```
Dashboard bisa diakses via `https://nama-mesin.nama-akun.ts.net/dashboard?uid=USER_ID`.

---

## Catatan

- `finance.db` ter-generate otomatis, tidak perlu dibuat manual
- Untuk production, jalankan sebagai systemd service agar auto-start saat server restart
- Jangan upload `finance.db` dan `.env` ke GitHub

---

## Author

**Mr. Elixir** — [@MrElixir1945](https://github.com/MrElixir1945)
