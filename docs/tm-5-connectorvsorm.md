## 1. Kode Asli

Kode asli yang digunakan untuk mengambil data jadwal:

```js
const { jadwal } = require('../data/mock');

router.get('/', (req, res) => {
  const { status } = req.query;

  const data = status
    ? jadwal.filter((item) => item.status === status)
    : jadwal;

  res.status(200).json({
    status: true,
    message: 'Daftar jadwal berhasil diambil',
    data,
  });
});

## 2. Penulisan Ulang dengan Raw MySQL2

Kode di atas menggunakan data `mock`. Jika data jadwal disimpan dalam database MySQL, pengambilan data dapat ditulis menggunakan connector `mysql2` sebagai berikut:

```js
const mysql = require('mysql2/promise');

const db = mysql.createPool({
  host: 'localhost',
  user: 'root',
  password: '',
  database: 'nama_database',
});

router.get('/', async (req, res) => {
  try {
    const { status } = req.query;

    let sql = 'SELECT * FROM jadwal';
    const params = [];

    if (status) {
      sql += ' WHERE status = ?';
      params.push(status);
    }

    const [data] = await db.execute(sql, params);

    res.status(200).json({
      status: true,
      message: 'Daftar jadwal berhasil diambil',
      data,
    });
  } catch (error) {
    res.status(500).json({
      status: false,
      message: 'Gagal mengambil data jadwal',
    });
  }
});

## 3. Penulisan Ulang dengan Prisma

Dengan Prisma, pengambilan data jadwal dapat menggunakan method `findMany()`.

```js
router.get('/', async (req, res) => {
  try {
    const { status } = req.query;

    const data = await prisma.jadwal.findMany({
      where: status ? { status: status } : {},
    });

    res.status(200).json({
      status: true,
      message: 'Daftar jadwal berhasil diambil',
      data,
    });
  } catch (error) {
    res.status(500).json({
      status: false,
      message: 'Gagal mengambil data jadwal',
    });
  }
});

## 4. Risiko SQL Injection

Pada penggunaan raw SQL, SQL Injection dapat terjadi jika input dari pengguna langsung digabungkan ke dalam query SQL.

Contoh yang berisiko:

```js
const sql = `SELECT * FROM jadwal WHERE status = '${status}'`;


```markdown
## 5. Kesimpulan

Kode asli menggunakan data `mock` dan mengambil data dengan `filter()`. Pada versi raw `mysql2`, data diambil menggunakan query SQL secara langsung. Sedangkan pada Prisma, data diambil menggunakan method `findMany()`.

Raw `mysql2` memberikan kontrol langsung terhadap query SQL, sedangkan Prisma menyediakan cara pengambilan data melalui ORM yang lebih terstruktur. Penggunaan parameterized query pada `mysql2` serta mekanisme ORM pada Prisma dan Sequelize membantu mengurangi risiko SQL Injection.