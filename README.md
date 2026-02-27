# SQL Server via Docker

---

## Prasyarat

Pastikan sudah terinstal di sistem kamu:

- [Docker Desktop](https://www.docker.com/products/docker-desktop/) (Windows/Mac) atau Docker Engine + Compose (Linux)
- [Visual Studio Code](https://code.visualstudio.com/)
- Extension VS Code: **SQL Server (mssql)**

---

## Cara Setup

### 1. Clone Project

```bash
git clone https://github.com/alberdjuniawan/setup-mssql-sql.git
```


---

### 2. Konfigurasi Environment

Salin file `.env.example` menjadi `.env`:

```bash
cp .env.example .env
```

Buka file `.env` dan sesuaikan konfigurasi sesuai kebutuhan:

```env
# Nama container Docker
CONTAINER_NAME=mssql

# Password SA SQL Server
SA_PASSWORD=yourStrongPasswordHere!123

# Port host
HOST_PORT=1433
```

> **Catatan password SQL Server:** SQL Server mewajibkan password minimal 8 karakter dengan kombinasi huruf besar, huruf kecil, angka, dan/atau simbol. Password yang tidak memenuhi syarat akan menyebabkan container gagal start.

---

### 3. Jalankan SQL Server

```bash
docker compose up -d
```

Cek status container:

```bash
docker ps
```

Pastikan container `mssql` berstatus **Up**.

---

## Koneksi via VS Code

1. Buka VS Code
2. Tekan `Ctrl+Shift+P` (atau `Cmd+Shift+P` di Mac)
3. Ketik dan pilih **MS SQL: Connect**
4. Isi detail koneksi berikut:

   | Field         | Value                     |
   |---------------|---------------------------|
   | Server Name   | `localhost,1433`          |
   | Database      | `master` *(bisa dikosongkan)* |
   | Auth Type     | `SQL Login`               |
   | User Name     | `sa`                      |
   | Password      | *(password dari file `.env`)* |

5. Tekan **Enter**, simpan nama profile (opsional), dan mulai query!

---

## 🛠️ Manajemen Container

| Perintah | Fungsi |
|---|---|
| `docker compose up -d` | Jalankan container |
| `docker compose stop` | Hentikan container sementara |
| `docker compose start` | Jalankan kembali container |
| `docker compose down` | Hapus container & network |

---
