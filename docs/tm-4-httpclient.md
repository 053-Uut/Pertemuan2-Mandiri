# TM-4 — HTTP Client + DevTools

**Entity:** Pengajuan Judul

## Base API

BASE=https://silab.ft.unira.ac.id/api/v1

---

## A. Postman GET $BASE

### Request

**Method:** GET

**URL:** https://silab.ft.unira.ac.id/api/v1

Request dilakukan menggunakan method GET ke endpoint `$BASE`.

### Hasil Pengujian

**Status Code:** 200 OK

**Content-Type:** text/html; charset=UTF-8

**Server:** nginx

**Framework:** Express

Response yang diterima berupa halaman HTML yang memberikan informasi bahwa layanan SILAB telah berpindah ke ATLAS.

Isi response menjelaskan bahwa layanan pada `silab.ft.unira.ac.id` telah dialihkan ke alamat `atlas.unira.ac.id`.

### Screenshot

- Screenshot Postman GET `$BASE` dengan Body dan status `200 OK`.
- Screenshot Postman Headers yang menunjukkan `:status 200` dan `content-type: text/html; charset=UTF-8`.

---

## B. DevTools Network

### Request

Halaman yang dibuka:

https://silab.ft.unira.ac.id/jadwal

Pada Chrome DevTools digunakan tab **Network** dengan filter `api/v1`.

### Hasil Pengujian

Ditemukan request:

**Request URL:** https://silab.ft.unira.ac.id/api/v1/graphql

**Request Method:** POST

**Status Code:** 200 OK

**Type:** XHR

Request tersebut menunjukkan bahwa halaman melakukan komunikasi dengan endpoint API yang menggunakan prefix `/api/v1`.

### Screenshot

Screenshot menunjukkan:

- DevTools pada tab Network.
- Filter `api/v1`.
- Request `graphql`.
- Request URL `https://silab.ft.unira.ac.id/api/v1/graphql`.
- Request Method `POST`.
- Status Code `200 OK`.

---

## C. Curl -i $BASE/salah-ketik

### Request

Pengujian dilakukan menggunakan perintah:

```bash
curl.exe -i https://silab.ft.unira.ac.id/api/v1/salah-ketik
```

### Hasil Pengujian

Response yang diterima:

```text
HTTP/1.1 404 Not Found
Server: nginx
Date: Sat, 03 Oct 2026 03:00:00 GMT
Content-Type: application/json; charset=utf-8
Content-Length: 189
Connection: keep-alive
Vary: Accept-Encoding
X-Powered-By: Express
Vary: Origin
Access-Control-Allow-Credentials: true
ETag: W/"bd-WnupPZu2gyTpiwvrUHJ4L+OdxF0"
```

Response body:

```json
{
  "jsonapi": {
    "version": "1.0"
  },
  "meta": {
    "authors": "Muhammad Umar Mansyur",
    "copyright": "2023 ~ Silab Informatika Universitas Madura"
  },
  "status": false,
  "message": "Api atau berkas tidak ditemukan"
}
```

**Status Code:** 404

**Status:** Not Found

**Message:** Api atau berkas tidak ditemukan

Hasil pengujian menunjukkan bahwa endpoint `/api/v1/salah-ketik` menghasilkan `404 Not Found`, bukan `500 Internal Server Error`. Oleh karena itu, status `500` tidak dibuat-buat atau dituliskan sebagai hasil pengujian.

### Perbedaan curl -s dan curl -i

`curl -s` digunakan untuk menjalankan request dalam mode silent sehingga output tambahan seperti progress meter tidak ditampilkan.

`curl -i` digunakan untuk menampilkan HTTP response header bersama dengan response body.

Dengan demikian, `curl -s` lebih sederhana untuk melihat hasil response, sedangkan `curl -i` lebih berguna untuk melihat status code dan informasi header HTTP.

### Screenshot

Screenshot hasil perintah `curl.exe -i` dilampirkan sebagai bukti pengujian.

---

## Kesimpulan

TM-4 membahas penggunaan HTTP client melalui Postman, curl, dan DevTools.

Pada bagian A, pengujian menggunakan Postman terhadap `GET $BASE` menghasilkan status `200 OK` dengan response berupa halaman HTML yang menginformasikan perpindahan layanan SILAB ke ATLAS.

Pada bagian B, pengujian menggunakan DevTools Network menemukan request `POST https://silab.ft.unira.ac.id/api/v1/graphql` dengan status `200 OK`.

Pada bagian C, pengujian menggunakan `curl -i` terhadap endpoint `/api/v1/salah-ketik` menghasilkan status `404 Not Found` dengan message `Api atau berkas tidak ditemukan`.

Semua hasil pengujian ditulis berdasarkan response aktual yang diterima dari server dan tidak menggunakan response yang dibuat-buat.