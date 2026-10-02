# TM-2 — Kartu HTTP Method + Code

Entity: Pengajuan Judul

## Base API

BASE=https://silab.ft.unira.ac.id/api/v1

## Kartu HTTP

| METHOD + API | Code | Status | Message | Siapa Salah | Aksi Perbaikan |
|---|---:|---|---|---|---|
| GET `/api/v1` | 301 | Moved Permanently | Redirecting to /api/v1/ | URL request perlu diperiksa | Gunakan `/api/v1/` atau ikuti redirect |
| GET `/jadwal/jumlah-jadwal` | 302 | Found | Found. Redirecting to / | URL atau routing perlu diperiksa | Periksa kembali endpoint dan route |
| POST `/jadwal` | 302 | Found | Found. Redirecting to / | URL atau routing perlu diperiksa | Periksa kembali endpoint dan route |
| GET `/api/v1/xxx` | 404 | Not Found | Api atau berkas tidak ditemukan | Endpoint tidak tersedia | Gunakan endpoint yang benar |
| POST `https://api.unira.ac.id/graphql` | 200 | OK | API mengembalikan data hello | Tidak ada | Request berhasil |
| GET `/api/v1/` | 200 | OK | SILAB telah berpindah ke ATLAS | Tidak ada | Gunakan alamat ATLAS yang diberikan |
| POST `/api/v1/jadwal` `{}` | 401 | Unauthorized | Akses tidak diizinkan! | Client belum memiliki autentikasi | Gunakan autentikasi/token yang valid |
| POST `/api/v1/jadwal` `{` | 400 | Bad Request | Unexpected end of JSON input | Client mengirim JSON tidak valid | Perbaiki format JSON |

## Kategori HTTP

| Code | Kategori | Hasil Pengujian |
|---:|---|---|
| 200 | OK | Ada |
| 201 | Created | Belum diuji |
| 400 | Bad Request | Ada |
| 401–403 | Unauthorized / Forbidden | 401 Ada, 403 Belum diuji |
| 500 | Internal Server Error | Belum diuji |

## Authorization

- GET `/api/v1`: dapat diakses dan menghasilkan redirect.
- GET `/api/v1/`: dapat diakses dan menghasilkan informasi perpindahan SILAB ke ATLAS.
- GET `/api/v1/xxx`: endpoint tidak ditemukan.
- POST `/api/v1/jadwal`: membutuhkan autentikasi.
- POST `/api/v1/jadwal` dengan JSON tidak valid: request ditolak karena format JSON salah.
- POST `https://api.unira.ac.id/graphql`: request berhasil dengan status 200.

## Keterangan

- Code `200` menunjukkan request berhasil diproses.
- Code `201` menunjukkan resource berhasil dibuat dan akan diuji pada pengujian berikutnya.
- Code `301` menunjukkan resource diarahkan secara permanen ke URL lain.
- Code `302` menunjukkan request diarahkan sementara ke URL lain.
- Code `400` menunjukkan request yang dikirim tidak valid.
- Code `401` menunjukkan request membutuhkan autentikasi.
- Code `403` menunjukkan akses ditolak dan belum diuji pada TM-2.
- Code `404` menunjukkan endpoint atau resource tidak ditemukan.
- Code `500` menunjukkan kesalahan pada sisi server dan belum diuji pada TM-2.
- Pengujian dilakukan berdasarkan response yang diterima dari server.
- Tidak membuat response fiktif untuk status code yang belum diuji.