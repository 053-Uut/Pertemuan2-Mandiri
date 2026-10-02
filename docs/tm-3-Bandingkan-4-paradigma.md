# TM-3 — Perbandingan 4 Paradigma

## Kasus

Dashboard membutuhkan tiga data, yaitu total jadwal, daftar jadwal, dan tagihan.

## Perbandingan 4 Paradigma

| Paradigma | Cara Kerja | Jumlah Request | Kelebihan | Kekurangan |
|---|---|---:|---|---|
| REST | Memanggil endpoint total jadwal, daftar jadwal, dan tagihan secara terpisah | N request | Sederhana dan mudah digunakan | Membutuhkan beberapa request |
| GraphQL | Mengambil total jadwal, daftar, dan tagihan melalui query `dashboardTrend` | 1 request | Data dapat diambil sekaligus sesuai kebutuhan | Implementasi lebih kompleks |
| gRPC | Komunikasi antar-service, misalnya service Dashboard meminta data dari service Jadwal dan Tagihan | Hipotetik | Cepat untuk komunikasi antar-service | Kurang cocok untuk komunikasi langsung dengan browser |
| WS/Polling | Mengirim pembaruan data secara berkala atau real-time | Berulang | Cocok untuk angka yang harus selalu diperbarui | Dapat menambah beban server |

## Pilihan

**Pemenang: GraphQL.**

Untuk kasus dashboard ini, GraphQL dipilih karena total jadwal, daftar jadwal, dan tagihan dapat diminta dalam **1 request** menggunakan query `dashboardTrend`. Hal ini membuat pengambilan data dashboard lebih terpusat dibandingkan REST yang membutuhkan beberapa request.

## Kapan Pilihan Diganti?

Pilihan dapat diganti jika kebutuhan sistem berubah.

- **REST** dapat digunakan jika data yang dibutuhkan sederhana dan hanya berasal dari satu endpoint.
- **gRPC** dapat digunakan jika komunikasi dilakukan antar-service dalam arsitektur microservices.
- **WebSocket** dapat digunakan jika dashboard membutuhkan pembaruan data secara real-time.
- **Polling** dapat digunakan jika pembaruan data cukup dilakukan secara berkala.

## Kesimpulan

Keempat paradigma memiliki penggunaan yang berbeda. REST cocok untuk API sederhana, GraphQL cocok untuk mengambil beberapa data sekaligus, gRPC cocok untuk komunikasi antar-service, sedangkan WebSocket/Polling cocok untuk kebutuhan pembaruan data secara berkala atau real-time. Untuk kasus dashboard yang membutuhkan total jadwal, daftar jadwal, dan tagihan, pilihan yang digunakan adalah **GraphQL** karena dapat mengambil data tersebut melalui satu request.