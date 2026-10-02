# TM-1 — Peta Routing Pribadi

**Entity:** Pengajuan Judul

## Base API

BASE=https://silab.ft.unira.ac.id/api/v1

## Peta Routing

| METHOD + API | SvelteKit File | ATLAS SPA | Flutter name + args | US |
|---|---|---|---|---|
| GET `/api/v1/pengajuan-judul` | `routes/pengajuan-judul/+page.svelte` | `/pengajuan-judul` | `getPengajuanJudul()` | US-01 |
| GET `/api/v1/pengajuan-judul/:id` | `routes/pengajuan-judul/[id]/+page.svelte` | `/pengajuan-judul/:id` | `getPengajuanJudulDetail(id)` | US-02 |
| POST `/api/v1/pengajuan-judul` | `routes/pengajuan-judul/baru/+page.svelte` | `/pengajuan-judul/baru` | `createPengajuanJudul(data)` | US-03 |
| PUT `/api/v1/pengajuan-judul/:id` | `routes/pengajuan-judul/[id]/edit/+page.svelte` | `/pengajuan-judul/:id/edit` | `updatePengajuanJudul(id, data)` | US-04 |
| DELETE `/api/v1/pengajuan-judul/:id` | `routes/pengajuan-judul/[id]/+page.svelte` | `/pengajuan-judul/:id` | `deletePengajuanJudul(id)` | US-05 |

## Authorization

- **US-01:** `authorize(Mahasiswa, Kaprodi, Tendik)`
- **US-02:** `canAccess()`
- **US-03:** `authorize(Mahasiswa)`
- **US-04:** `authorize(Kaprodi, Tendik)`
- **US-05:** `authorize(Tendik)`

## Keterangan

- `[id]` digunakan untuk mengakses data pengajuan judul berdasarkan ID.
- `baru` digunakan untuk route pengajuan judul baru.
- `GET` digunakan untuk mengambil daftar dan detail pengajuan judul.
- `POST` digunakan untuk membuat pengajuan judul baru.
- `PUT` digunakan untuk mengubah data pengajuan judul.
- `DELETE` digunakan untuk menghapus pengajuan judul.
- Semua endpoint menggunakan prefix `/api/v1`.
- `authorize()` digunakan untuk membatasi akses berdasarkan role.
- `canAccess()` digunakan untuk memastikan pengguna dapat mengakses data pengajuan judul tertentu.
- `:id` pada URL merupakan parameter ID pengajuan judul.