Berikut adalah **panduan lengkap & mudah** untuk menginstal dan menjalankan **t3rn executor** di Linux, berdasarkan dokumentasi resmi tetapi disusun ulang agar **lebih ramah pemula** dan **terstruktur**:

---

## ✅ **Panduan Instalasi t3rn Executor (Testnet) untuk Pemula**

> ⚠️ Persyaratan awal:
>
> * Sudah install Linux (Ubuntu/Debian/AlmaLinux, dll)
> * Sudah install `wget`, `tar`, dan `tmux`
> * Sudah punya **Private Key** (jangan pernah bocorkan ke siapa pun!)

---

### 🧩 Langkah 1: Bersihkan folder executor lama (jika ada)

```bash
cd ~
rm -rf executor*
```

---

### 🌐 Langkah 2: Unduh file executor binary terbaru

```bash
wget https://github.com/t3rn/executor-release/releases/download/v0.69.0/executor-linux-v0.69.0.tar.gz
```

---

### 📦 Langkah 3: Ekstrak file yang sudah diunduh

```bash
tar -xvzf executor-linux-v0.69.0.tar.gz
```

---

### 🛠️ Langkah 4: Pindah ke folder executor & beri izin eksekusi

```bash
cd executor/executor/bin
chmod +x executor
```

---

### 📁 Langkah 5: Buat file konfigurasi `.env`

Buat file `.env` di folder `executor/executor/bin/`:

```bash
nano .env
```

Isi dengan:

```bash
export ENVIRONMENT=testnet
export LOG_LEVEL=debug
export LOG_PRETTY=false

export EXECUTOR_PROCESS_BIDS_ENABLED=true
export EXECUTOR_PROCESS_ORDERS_ENABLED=true
export EXECUTOR_PROCESS_CLAIMS_ENABLED=true
export EXECUTOR_ENABLE_BATCH_BIDDING=true
export EXECUTOR_PROCESS_PENDING_ORDERS_FROM_API=false
export EXECUTOR_PROCESS_ORDERS_API_ENABLED=false

export EXECUTOR_MAX_L3_GAS_PRICE=25000
export EXECUTOR_ENABLED_NETWORKS="arbitrum-sepolia,base-sepolia,optimism-sepolia,l2rn,unichain-sepolia,sei-testnet"
export EXECUTOR_ENABLED_ASSETS="eth,t3eth,t3mon,t3sei,mon,sei"
export NETWORKS_DISABLED="blast-sepolia,monad-testnet,arbitrum,optimism,base"

export PRIVATE_KEY_LOCAL=ISI_PRIVATE_KEY_KAMU

export RPC_ENDPOINTS='{
  "l2rn": ["https://b2n.rpc.caldera.xyz/http"],
  "arbt": ["https://arbitrum-sepolia.drpc.org/"],
  "bast": ["https://base-sepolia-rpc.publicnode.com/"],
  "opst": ["https://sepolia.optimism.io/"],
  "seit": ["https://evm-rpc-testnet.sei-apis.com"],
  "unit": ["https://unichain-sepolia.drpc.org"]
}'
```

> 📌 Ganti `ISI_PRIVATE_KEY_KAMU` dengan private key kamu **(tanpa 0x)**.

Setelah selesai, tekan:

* `Ctrl + X` → `Y` → `Enter` untuk menyimpan.

---

### 📟 Langkah 6: Jalankan session tmux agar proses terus jalan

```bash
tmux new -s t3rn-executor
```

---

### ☑️ Langkah 7: Aktifkan konfigurasi `.env`

```bash
source .env
```

---

### 🚀 Langkah 8: Jalankan executor

```bash
./executor
```

Jika berhasil, akan muncul log berwarna abu-abu atau biru yang menandakan executor sedang aktif dan memproses tugas.

---

### 🔄 Tips Tambahan:

* Untuk keluar sementara dari `tmux`, tekan: `Ctrl + B`, lalu `D`
* Untuk kembali masuk ke tmux: `tmux attach -t t3rn-executor`
* Untuk menjalankan executor otomatis saat boot, bisa tambahkan ke systemd (bisa saya bantu jika perlu)

---

Lanjut...
