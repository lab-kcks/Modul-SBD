# Data Manipulation Language (DML) Part 4

## Daftar Isi
- [1. Trigger]()
     - [1.1 Pengenalan]()
     - [1.2 Syntax]()
     - [1.3 Contoh Implementasi]()
     - [1.4 Pengujian Trigger]()
- [2. View]()
     - [2.1 Pengenalan]()
     - [2.2 Syntax]()
     - [2.3 Contoh Implementasi]()
     - [2.4 Pengujian View]()
## 1. Trigger

### 1.1 Pengenalan
![image!](gambar 1)

TRIGGER adalah kumpulan kode SQL yang berjalan secara otomatis untuk mengeksekusi perintah INSERT, UPDATE, DELETE. Biasanya, TRIGGER akan dijalankan sebelum atau sesudah proses INSERT, UPDATE, DELETE (Perintah DML). Atau dalam kata lain, TRIGGER suatu objek database yang merupakan aksi atau prosedur yang terjadi jika terjadi perubahan pada suatu row.

fungsi TRIGGER dalam database sebenarnya merupakan kode prosedural yang secara otomatis dijalankan untuk menanggapi perubahan tertentu pada table tertentu atau tampilan dalam database. Trigger biasanya banyak digunakan untuk menjaga integritas informasi pada database.

Idealnya, Trigger harus dipertimbangkan ketika kode ini digunakan untuk mengotomatisasi perubahan yang spesifik untuk database atau pengelolaan data. Log audit adalah contoh penerapan dari Trigger. Misalnya sebuah sistem CMS WordPress dengan table ‘blog’ yang berisi judul dan isi artikel. Kemudian sebuah table ‘audit’ yang bisa merekam tanggal dan waktu sebuah artikel ketika ditambahkan, diedit atau dihapus. Sistem web Anda mungkin tidak pernah menyajikan informasi yang atau bahkan tahu setiap perubahan database itu dicatat.

#### Karakteristik Trigger:
1) Sebuah nama yang unik. Misalnya blog_before_insert atau blog_after_update.
2) Sebuah Trigger hanya dapat memonitor satu table.
3) Ketika Trigger dijalankan, ini terjadi ‘before’ atau ‘after’ INSERT, UPDATE atau DELETE. Trigger ‘before’ harus digunakan jika Anda perlu untuk memodifikasi data yang masuk. 4. Sebuah Trigger ‘after’ harus digunakan jika Anda ingin referensi record baru, berubah sebagai foreign key untuk catatan di table lain.
5) Blok kode Trigger: satu set perintah SQL untuk menjalankan. Perhatikan bahwa Anda dapat merujuk ke suatu kolom dalam tabel menggunakan OLD.col_name (nilai sebelumnya) atau NEW.col_name (nilai baru). Nilai untuk NEW.col_name dapat diubah dalam Trigger SEBELUM INSERT dan UPDATE.

### 1.2 Syntax
Cara penulisan TRIGGER dapat menggunakan syntax sebagai berikut:
```sql
DELIMITER $$
CREATE TRIGGER nama_trigger
{BEFORE | AFTER} {INSERT | UPDATE| DELETE }
    ON nama_table 
    FOR EACH ROW
BEGIN
    KODE SQL
END$$
DELIMITER ;
```

Untuk memulai menggunakan TRIGGER kita gunakan CREATE TRIGGER dilanjutkan nama TRIGGER yang ingin dibuat. `{BEFORE | AFTER}` adalah waktu TRIGGER akan dijalankan, apakah sebelum atau sesudah database dimodifikasi oleh perintah DML. `{INSERT | UPDATE | DELETE}` adalah perintah DML yang mengaktifkan TRIGGER

Lebih detail waktu TRIGGER akan dijelaskan di tabel berikut:

| No | Waktu TRIGGER | Keterangan TRIGGER |
| ------ | ------ | ------ |
| 1 | BEFORE INSERT	| TRIGGER dijalankan sebelum record dimasukkan ke database |
| 2 | AFTER INSERT |	TRIGGER dijalankan sesudah record dimasukkan ke database |
| 3 | BEFORE UPDATE	| TRIGGER dijalankan sebelum record dirubah di database |
| 4 | AFTER UPDATE |	TRIGGER dijalankan sesudah record dirubah database |
| 5 | BEFORE DELETE |	TRIGGER dijalankan sebelum record dihapus di database |
| 6 | AFTER DELETE |	TRIGGER dijalankan sesudah record dihapus di database |

`ON` mendefinisikan table yang mengaktifkan TRIGGER. `BEGIN END  adalah pernyataan yang membungkus kode TRIGGER. Pastikan diawal gunakan `DELIMITER $$` dan diakhir dikembalikan ke `DELIMITER;`

### 1.3 Contoh Implementasi
Untuk praktek TRIGGER kali ini, kita akan database yang bernama `data_alamat` yang berisi 2 tabel, bernama table `mahasiswa` dan table `log_mahasiswa`. Fungsi dari kedua tabel adalah sebagai berikut:

```
Table mahasiswa -> menyimpan data mahasiswa
Table log_mahasiswa -> menyimpan perubahan data mahasiswa
```

Jadi setiap ada perubahan data (UPDATE) alamat mahasiswa pada table mahasiswa maka akan disimpan di table log_mahasiwa tentang histori perubahan data alamat tersebut. Dengan adanya log perubahan data mahasiswa maka akan memudahkan dalam melihat histori data mahasiswa yang pernah berubah dalam sistem.

Syntax pembuatan tabel `mahasiswa` adalah sebagai berikut:

```sql
CREATE TABLE mahasiswa
(
    nim INT(10),
    nama VARCHAR(100),
    alamat VARCHAR(100),
    PRIMARY KEY(nim)
);

INSERT INTO mahasiswa 
VALUES 
(21400200,"faqih","bandung"),
(21400201,"ina","jakarta"),
(21400202,"anto","semarang"),
(21400203,"dani","padang"),
(21400204,"jaka","bandung"),
(21400205,"nara","bandung"),
(21400206,"senta","semarang");
```

Lalu, untuk syntax pembuatan tabel `log_mahasiswa` adalah sebagai berikut:
```sql
CREATE TABLE log_mahasiswa
(
    id_log INT(10) AUTO_INCREMENT,
    nim INT(10),
    alamat_lama VARCHAR(100),
    alamat_baru VARCHAR(100),
    waktu DATE,
    PRIMARY KEY(id_log)
);
```

Setelah itu, akan kita aplikasikan penggunaan TRIGGER pada kedua tabel. Kita akan menyimpan data perubahan alamat sebelum perintah UPDATE dijalankan. Syntax nya adalah sebagai berikut:

```sql
DELIMITER $$
CREATE TRIGGER update_alamat_mahasiswa 
    BEFORE UPDATE 
    ON mahasiswa
    FOR EACH ROW 
BEGIN
    INSERT INTO log_mahasiswa
    set nim = OLD.nim,
    alamat_lama=OLD.alamat,
    alamat_baru=NEW.alamat,
    waktu = NOW(); 
END$$
DELIMITER ;
```

Syntax ini dijalankan pada sql database yang digunakan. Keyword `OLD` digunakan untuk mengambil data kolom di table yang lama sedangkan keyword `NEW` digunakan untuk mengambil data kolom di table yang baru. Sekarang kita akan coba update alamat mahasiswa dengan NIM 21400200. Sebelum di-update alamat mahasiswa dengan NIM 21400200 adalah “bandung”.

Operasi TRIGGER yang tersimpan dapat dilihat pada menu "Trigger":

![image!](2)

### 1.4 Pengujian Trigger

Dari tabel dan TRIGGER yang sudah kita inputkan sebelumnya, kita akan mencoba melakukan pengujian TRIGGER tersebut dengan mengganti alamat yang bernilai “bandung” menjadi “surabaya” pada tabel `mahasiswa`:

```sql
UPDATE mahasiswa 
SET alamat = 'surabaya'
WHERE nim = 21400200;
```

Sekarang coba lakukan perintah SELECT untuk melihat/mengecek isi table `log_mahasiswa`:
```sql
SELECT *
FROM log_mahasiswa;
```

Jadi record baru secara otomatis telah ditambahkan ke table `log_mahasiswa  untuk mahasiswa dengan `NIM 21400200` yang telah diubah alamat awal “bandung” menjadi “surabaya”. Sedangkan pada table mahasiswa alamat yang tercantum adalah alamat yang baru seperti tampilan berikut:

![image!](3)

## 2. View

### 2.1 Pengenalan
Dalam SQL, VIEW merupakan tabel virtual yang dibuat berdasarkan kumpulan hasil dari pernyataan SQL. Tampilan terdiri atas baris dan kolom seperti tabel pada umumnya. Field dalam VIEW adalah field dari satu atau beberapa tabel nyata dalam database. Nah dengan menggunakan VIEW, kita dapat menambahkan pernyataan dan fungsi SQL ke tampilan dan menyajikan data seolah-olah data berasal dari satu tabel tunggal.

#### Keuntungan Menggunakan VIEW
1) Menyederhanakan kueri kompleks
VIEW membantu menyederhanakan kueri kompleks. Jika kita memiliki kueri kompleks yang sering digunakan, kita dapat membuat tampilan berdasarkan kueri tersebut sehingga kita dapat merujuk ke tampilan tersebut dengan menggunakan pernyataan SELECT sederhana alih-alih mengetik kueri lagi.

2) Membuat logika bisnis yang konsisten
Misalkan kita harus berulang kali menulis rumus yang sama di setiap kueri memiliki kueri yang memiliki logika bisnis yang kompleks. Untuk membuat logika ini konsisten di seluruh kueri, Akita bisa menggunakan VIEW untuk menyimpan penghitungan dan menyembunyikan kerumitannya.

3) Menambahkan lapisan keamanan ekstra
Sebuah tabel dapat mengekspos banyak data termasuk data sensitif seperti informasi pribadi dan perbankan. Dengan menggunakan VIEW dan priviledge setting, kita dapat membatasi data mana yang dapat diakses pengguna dengan hanya memaparkan data yang diperlukan kepada mereka. Misalnya, tabel karyawan mungkin berisi SSN dan informasi alamat, yang seharusnya hanya dapat diakses oleh departemen SDM.

### 2.2 Syntax
VIEW dibuat dengan pernyataan `CREATE VIEW`. Untuk syntax nya sendiri adalah sebagai berikut:

```sql
CREATE VIEW view_name AS
SELECT column1, column2, ...
FROM table_name
WHERE condition;
```

**Catatan: VIEW selalu menampilkan data terkini dikarenakan mesin database membuat ulang tampilan, setiap kali user memasukkan query-nya.**

Saat kita mengeksekusi CREATE VIEW maka akan terbentuk table virtual yang menyimpan kode SQL. Contohnya, kita akan membuat kode SQL yang menghubungkan table mahasiswa dan table transaksi secara INNER JOIN dan menyimpannya ke view.

Kita juga bisa melakukan perintah `DELETE VIEW` pada VIEW yang kita miliki dengan syntax sebaga berikut:

```sql
DROP VIEW view_name; 
```

### 2.3 Contoh Implementasi
Di sini, kita akan mengimplementasikan operasi VIEW yang kita gabungkan dengan perintah `JOIN` untuk menggabungkan value antara dua tabel. Mula-mula, kita akan membuat database bernama `perpustakaan` yang berisi 2 tabel bernama `mahasiswa` dan `transaksi` dengan syntax sebagai berikut:

```sql
CREATE TABLE mahasiswa
(
    nim INT(10),
    nama VARCHAR(100),
    alamat VARCHAR(100),
    PRIMARY KEY(nim)
);

CREATE TABLE transaksi
(
    id INT(10),
    nim VARCHAR(100),
    nama_buku VARCHAR(100),
    PRIMARY KEY(id)
);

INSERT INTO mahasiswa 
VALUES 
(21400200,"faqih","bandung"),
(21400201,"ina","jakarta"),
(21400202,"anto","semarang"),
(21400203,"dani","padang"),
(21400204,"jaka","bandung"),
(21400205,"nara","bandung"),
(21400206,"senta","semarang");

INSERT INTO transaksi 
VALUES 
(1,21400200,"Buku Informatika"),
(2,21400202,"Buku Teknik Elektro"),
(3,21400203,"Buku Matematika"),
(4,21400206,"Buku Fisika"),
(5,21400207,"Buku Bahasa Indonesia"),
(6,21400210,"Buku Bahasa Daerah"),
(7,21400211,"Buku Kimia");
```

Berikut merupakan syntax operasi table `mahasiswa` dan table `transaksi` berdasarkan field `NIM` secara `INNER JOIN` tanpa menggunakan VIEW:
```sql
SELECT mahasiswa.nim, nama, alamat, nama_buku
FROM mahasiswa
INNER JOIN transaksi
ON mahasiswa.nim = transaksi.nim;
```

Sehingga diperoleh hasil output sebagai berikut:

![image!](4)

Dengan view kita bisa membuat table virtual yang menyimpan query join di atas dengan syntax berikut:
```sql
CREATE VIEW transaksiMhs AS 
SELECT mahasiswa.nim, nama, alamat, nama_buku
FROM mahasiswa
INNER JOIN transaksi
ON mahasiswa.nim = transaksi.nim
```

### 2.4 Pengujian View

Jadi kita telah membuat table virtual dengan operasi VIEW dengan nama transaksiMhs. Untuk cara menggunakannya adalah sama seperti melakukan query table biasa. Di MySql browser, kita dapat melihat munculnya table hasil operasi VIEW di bawah table utama dalam database, seperti pada gambar di bawah ini:

![image!](5)

Untuk menampilkan table hasil operasi VIEW dari database utama, maka dapat dijalankan syntax `SELECT`seperti biasa sebagai berikut:

```sql
SELECT *
FROM transaksiMhs;
```

Setelah itu, kita juga bisa melakukan operasi dengan menggunakan tabel VIEW tersebut. Misal kita ingin meng-query nama mahasiswa yang meminjam buku matematika:

```sql
SELECT nama, nama_buku
FROM transaksiMhs
WHERE nama_buku = "Buku Matematika";
```

Nanti akan muncul table output seperti berikut:

![image!](6)

Nah kemudian sudah lelah belajar VIEW dan ingin menghapus operasi VIEW `transaksiMhs`, tinggal menuliskan syntax sebagai berikut:

```sql
DROP VIEW transaksiMhs;
```
