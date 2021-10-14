# Pengenalan MySQL dan DDL

## Daftar Isi
- [1. Pengenalan MySQL](#1-pengenalan-mysql)
  - [1.1 Kelebihan MySQL](#11-kelebihan-mysql)
  - [1.2 Kekurangan MySQL](#12-kekurangan-mysql)
- [2. Instalasi MySQL](#2-instalasi-mysql)
- [3. Client MySQL Menggunakan XAMPP](#3-client-mysql-menggunakan-xampp)
  - [3.1 Cara Menginstall XAMPP](#31-cara-menginstall-xampp)
  - [3.2 Cara Menjalankan XAMPP](#32-cara-menjalankan-xampp)
- [4. Cara mengakses MySQL](#4-cara-mengakses-mysql)
- [5. Tipe data di MySQL](#5-tipe-data-di-mysql)
- [6. Pengenalan DDL](#6-pengenalan-ddl)
- [7. Membuat Database](#7-membuat-database-melalui-console-dan-ui)
  - [7.1 Membuat Database melalui Console](#71-membuat-database-melalui-console)
  - [7.2 Membuat Database melalui UI](72-membuat-database-melalui-ui)

## 1. Pengenalan MySQL
Setiap bahasa pemrograman memiliki fungsi yang berbeda. Begitu pula dengan structured query language (SQL). SQL adalah bahasa query yang dirancang untuk pengambilan informasi tertentu dari database. Meskipun saat ini sudah ada berbagai jenis database, seperti MySQL, Microsoft SQL Server, dan PostgreSQL, mayoritas database tersebut tetap menggunakan dasar SQL.

<br>
<img legth="500" src="images" />
<br>

Lalu, apakah SQL tetap berguna jika digunakan bersamaan dengan bahasa pemrograman yang lain? Jawabannya iya. Sebagai contoh, jika menggunakan bahasa pemrograman Python, biasanya tetap membutuhkan SQL untuk mengambil data dari database. Maka, dapat disimpulkan bahwa SQL adalah salah satu bahasa query dasar dalam pengelolaan database.

MySQL masuk ke dalam jenis RDBMS (Relational Database Management System). Maka dari itu, istilah semacam baris, kolom, tabel, dipakai pada MySQL. Contohnya di dalam MySQL sebuah database terdapat satu atau beberapa tabel.

### 1.1 Kelebihan MySQL
MySQL mempunyai beberapa kelebihan yang bisa dimanfaatkan untuk mengembangkan perangkat lunak yang handal seperti:

**1. Mendukung Integrasi Dengan Bahasa Pemrograman Lain**

Website atau perangkat lunak terkadang dikembangkan dengan menggunakan berbagai macam bahasa pemrograman, jadi kita tidak perlu khawatir jika menggunakan MySQL. Maka dari itu, MySQL bisa membantu kita untuk mengembangkan perangkat lunak yang lebih efektif dan tentu saja lebih mudah dengan integrasi antara bahasa pemrograman.

**2. Tidak Membutuhkan RAM Besar**

MySQL dapat dipasang pada server dengan spesifikasi  kecil. Jadi tidak perlu khawatir jika hanya mempunyai server dengan kapasitas 1 GB karena kita masih bisa menggunakan MySQL sebagai database.

**3. Mendukung Multi User**

MySQL dapat dipakai oleh beberapa user dalam waktu  bersamaan tanpa membuatnya crash atau berhenti bekerja. Ini dapat dimanfaatkan ketika mengerjakan proyek yang sifatnya tim  sehingga seluruh tim dapat bekerja dalam waktu bersamaan tanpa harus menunggu user lain selesai.

**4. Bersifat Open Source**

MySQL adalah sistem manajemen database gratis. Meskipun gratis, bukan berarti database ini mempunyai kinerja buruk. Apalagi lisensi gratis yang dipakai adalah GPL di bawah pengelolaan Oracle sehingga kualitasnya termasuk baik. Selain itu, kita juga tidak perlu khawatir jika terjadi masalah karena banyak komunitas dan dokumentasi yang membahas soal MySQL.

**5. Struktur Tabel yang Fleksibel**

MySQL mempunyai struktur tabel yang mudah dipakai dan fleksibel. Contohnya saat MySQL memproses ALTER TABLE dan lain sebagainya. Jika dibandingkan dengan database lain seperti Oracle dan PostgreSQL, MySQL tergolong lebih mudah.

**6. Tipe Data yang Bervariasi**

Kelebihan lain dari MySQL adalah mendukung berbagai macam data yang bisa digunakan di MySQL. Contohnya float, integer, date, char, text, timestamp, double, dan lain sebagainya. Jadi manajemen database sistem ini sangat membantu untuk mengembangkan perangkat lunak yang berguna untuk pengelolaan database di server.

**7. Keamanan yang Terjamin**

Open source bukan berarti MySQL menyediakan keamanan yang buruk. Malah sebaliknya, MySQL mempunyai fitur keamanan yang cukup apik. Ada beberapa lapisan keamanan yang diterapkan oleh MySQL, seperti level nama host, dan subnetmask. Selain itu MySQL juga dapat mengatur hak akses user dengan enkripsi password tingkat tinggi.

### 1.2 Kekurangan MySQL

Sayangnya, meskipun memiliki segudang kelebihan, masih ada beberapa kelemahan yang dimiliki oleh MySQL sehingga Anda perlu mempertimbangkannya juga sebelum memakainya.

**1. Kurang Cocok untuk Aplikasi Game dan Mobile**

Bagi yang ingin mengembangkan aplikasi game atau perangkat mobile ada baiknya jika mempertimbangkan lagi jika ingin menggunakan MySQL. Kebanyakan pengembang game maupun aplikasi mobile tidak menggunakannya karena memang database manajemen sistem ini masih kurang bagus dipakai untuk sistem aplikasi tersebut.

**2. Sulit Mengelola Database yang Besar**

Jika ingin mengembangkan aplikasi atau sistem di perusahaan dengan database yang cukup besar, ada baiknya jika menggunakan database manajemen sistem selain MySQL. MySQL dikembangkan supaya ramah dengan perangkat yang mempunyai spesifikasi rendah, itulah mengapa MySQL tidak memiliki fitur yang lengkap seperti aplikasi lainnya

**3. Technical Support yang Kurang Bagus**

Sifatnya yang open source terkadang membuat aplikasi tidak menyediakan technical support yang memadai. Technical support MySQL diklaim kurang bagus. Hal ini membuat pengguna kesulitan. Apalagi jika pengguna mengalami masalah yang berhubungan dengan pengoperasian perangkat lunak tersebut dan membutuhkan bantuan technical support.

## 2. Instalasi MySQL
Berikut ini merupakan langkah-langkah yang dilakukan untuk melakukan download dan instalasi sebuah aplikasi MySQL. Aplikasi MySQL yang satu ini bersifat stand alone, di mana MySQL yang disediakan oleh developer MySQL ini dapat dibuka secara implisit di terminal/command prompt OS. Instalasi MySQLi versi ini **bersifat opsional**, karena nantinya kita akan lebih sering menggunakan aplikasi XAMPP (Aplikasi AMP yang menggabungkan Apache, MySQL, dan PHPMyAdmin). Namun, apabila ingin coba menginstall, berikut merupakan langkah-langkahnya:

1.  Mendownload aplikasi MySQL Community Server di http://dev.mysql.com/downloads/mysql/ dan kemudian pilih package yang ingin diinstall sesuai dengan OS (Windows, MacOS, Ubuntu, dll) yang digunakan.

<br>
<img legth="500" src="" />
<br>

2.  Setelah package berhasil didownload, maka aplikasi MySQL siap untuk diinstal. Klik dua kali pada file penginstal MySQL. Lalu, OS akan mengonfigurasi Penginstal MySQL:

<br>
<img legth="500" src="" />
<br>

3. Layar Selamat Datang: Welcome Screen menyediakan beberapa opsi. Pilih opsi pertama: 'Install MySQL Products'

<br>
<img legth="500" src="3" />
<br>

4. Unduh produk MySQL terbaru: Penginstal MySQL memeriksa dan mengunduh produk MySQL terbaru termasuk server MySQL, MySQL Workbench, dll.

<br>
<img legth="500" src="" />
<br>

5. Klik tombol 'next' untuk melanjutkan

<br>
<img legth="500" src="" />
<br>

6. Memilih Jenis Pengaturan: ada beberapa jenis pengaturan yang tersedia. Pilih opsi 'Full' untuk menginstal semua produk dan fitur MySQL.

<br>
<img legth="500" src="" />
<br>

7. Kemudian, kita dapat melakukan Checking Requirements.

<br>
<img legth="500" src="" />
<br>

8. Installation Progress: Penginstal MySQL akan mengunduh semua produk yang dipilih:

<br>
<img legth="500" src="" />
<br>

9. Installation Progress, ditunjukkan progress pengunduhan produk:

<br>
<img legth="500" src="" />
<br>

10. Setelah progress instalasi selesai, klik tombol 'next' untuk melanjutkan:

<br>
<img legth="500" src="" />
<br>

11. Klik tombol 'Next' untuk mengkonfigurasi Server Database MySQL:

<br>
<img legth="500" src="" />
<br>

12. Pilih Config Type dan MySQL port (3006 secara default) dan klik tombol 'Next' untuk melanjutkan.

<br>
<img legth="500" src="" />
<br>

13. Konfigurasi Server MySQL: pilih kata sandi untuk akun root. Harap perhatikan unduhan kata sandi dan simpan dengan aman jika Anda menginstal server database MySQL di server produksi. Jika Anda ingin menambahkan lebih banyak pengguna MySQL, Anda dapat melakukannya di langkah ini.

<br>
<img legth="500" src="" />
<br>

14. Konfigurasi Server MySQL: pilih detail layanan Windows termasuk Nama Layanan Windows dan jenis akun, lalu klik tombol 'Next' untuk melanjutkan.

<br>
<img legth="500" src="" />
<br>

15. Konfigurasi Server MySQL – Sedang Berlangsung: Penginstal MySQL sedang mengonfigurasi server database MySQL. Tunggu sampai selesai dan klik tombol 'Next' untuk melanjutkan.

<br>
<img legth="500" src="" />
<br>

16. Konfigurasi Server MySQL – Selesai. Klik tombol 'Next' untuk melanjutkan.

<br>
<img legth="500" src="" />
<br>

17. Ikhtisar Konfigurasi: Penginstal MySQL menginstal database sampel dan model sampel.

<br>
<img legth="500" src="" />
<br>

18. Instalasi Selesai: Klik tombol 'Finish' untuk menutup installation wizard dan meluncurkan MySQL Workbench.

<br>
<img legth="500" src="" />
<br>

Aplikasi MySQL ini terbilang cukup mudah untuk menjalankannya. Salah satu caranya adalah dengan menggunakan Command Line mySQL yang terinstall pada OS yang digunakan. Selain itu, aplikasi ini juga dapat digunakan pada aplikasi lain seperti DbForge Studio, MySQL Workbench, dll.

## 3. Client MySQL Menggunakan XAMPP
Seperti yang telah dijelaskan sebelumnya, XAMPP berguna untuk menjalankan MySQL pada localhost atau komputer tanpa harus ada koneksi internet. Tujuannya untuk menjalankan atau melakukan pengetesan sebuah database supaya lebih cepat ketika diakses jika dibandingkan dengan cara online. XAMPP merupakan aplikasi cross platform: Apache, MySQL, PHP dan Perl. XAMPP juga memberikan solusi sederhana dan cukup ringan dijalankan, memungkinkan Anda membuat web server lokal untuk melakukan pengetesan website.

### 3.1 Cara Menginstall XAMPP
Berikut adalah langkah-langkah untuk menginstall sekaligus mendownload XAMPP:

**Langkah 1:** Download XAMPP melalui website Apache Friends pada https://www.apachefriends.org/index.html. Pilih salah satu OS yang sesuai dengan perangkat yang dimiliki:

<br>
<img legth="500" src="" />
<br>

**Langkah 2:** Lakukan instalasi setelah Anda selesai mengunduh. Selama proses instalasi mungkin Anda akan melihat pesan yang menanyakan apakah Anda yakin akan menginstalnya. Silakan tekan 'Yes' untuk melanjutkan instalasi. Kemudian klik tombol 'Next':

<br>
<img legth="500" src="" />
<br>

**Langkah 3:** Pada tampilan selanjutnya akan muncul pilihan mengenai komponen mana dari XAMPP yang ingin dan tidak ingin Anda instal. Beberapa pilihan seperti Apache dan PHP adalah bagian penting untuk menjalankan website dan akan otomatis diinstal. Silakan centang MySQL dan phpMyAdmin, untuk pilihan lainnya biarkan saja.

<br>
<img legth="500" src="" />
<br>

**Langkah 4:** Berikutnya silakan pilih folder tujuan dimana XAMPP ingin Anda instal, pada tutorial ini pada direktori C:\xampp.

<br>
<img legth="500" src="" />
<br>

**Langkah 5:** Pada halaman selanjutnya, akan ada pilihan apakah Anda ingin menginstal Bitnami untuk XAMPP, dimana nantinya dapat Anda gunakan untuk install WordPress, Drupal, dan Joomla seccara otomatis.

<br>
<img legth="500" src="" />
<br>

**Langkah 6:** Pada langkah ini proses instalasi XAMPP akan dimulai. Silakan klik tombol 'Next'.

<br>
<img legth="500" src="" />
<br>

**Langkah 7:** Setelah berhasil diinstal, akan muncul notifikasi untuk langsung menjalankan control panel. Silakan klik 'Finish'.

<br>
<img legth="500" src="" />
<br>

### 3.2 Cara Menjalankan XAMPP
Setelah instalasi XAMPP selesai, maka aplikasi XAMPP dapat segera digunakan dan dijalankan. Silakan buka aplikasi XAMPP kemudian klik tombol Start pada Apache dan MySQL. Jika berhasil dijalankan, Apache dan MySQL akan berwarna hijau seperti gambar di bawah ini. Untuk melakukan pengecekan, silakan akses link http://localhost atau 127.0.0.1 melalui browser.

<br>
<img legth="500" src="" />
<br>

## 4. Cara mengakses MySQL
Setelah XAMPP berhasil diakses, maka Anda bisa mengakses tabel SQL pada phpMyAdmin. phpMyAdmin adalah aplikasi berbasis web yang digunakan untuk melakukan pengelolaan database MySQL dan atau tool yang paling populer untuk mengelola database MySQL.

Untuk mengakses phpMyAdmin, Anda hanya perlu mengetik link http://localhost/phpmyadmin, maka akan muncul tampilan seperti ini:

<br>
<img legth="500" src="" />
<br>

## 5. Tipe data di MySQL
Apa sih tipe data itu? Tipe data di MySQL merupakan jenis nilai yang ditampung pada variabel yang berupa numerik, (angka), teks, ataupun gambar. Tipe data dalam database digunakan untuk mendefinisikan suatu kolom atau field. Jenis-jenis tipe data bermacam-macam dan secara umum tipe data pada mysql ada empat kelompok yaitu Numeric, String, Date dan Tipe Data Blob.

Penggunaan typedata pada database memiliki beberapa fungsi yaitu:
- Untuk memberikan batasan atau format pada kolom table suatu database.
- Untuk membatasi data yang di-insert pada suatu kolom.
- Memberikan dampak hasil yang konsisten pada suatu kolom.

Pada database tipe data akan terlihat seperti fungsi/function pada umumnya di pemrograman, oleh karena itu terdapat tipe data pada database yang wajib Anda set/menentukan nilai parameter, dan ada juga tipe data yang tidak memerlukan parameter.

Parameter pada tipe data ini digunakan untuk menentukan jumlah character berapa batas maksimal dari jumlah character. Ada juga parameter yang digunakan untuk mem-fix-kan jumlah character misal 5, maka tidak boleh kurang dan tidak boleh lebih. Untuk tipe data boolean parameter nya digunakan utnuk mendefinisakan option atau pilihan dari suatu kasus yang logik.

**Contoh tipe data yang perlu ditentukan parameter nya:**

– Attibut `id` dengan maksimal penggunaan 2 digit bilangan bulat.
`id INT(2)`
– Attibut `username` dengan maksimal penggunaan 20 digit string.
`username VARCHAR (20)`

**Contoh tipedata yang tidak perlu ditentukan parameter nya:**


– Attibut `birthday` dengan tipe data `Date`.
`birthday DATE`


– Attribut `address` dengan tipe data `Text`.
`address TEXT`


Pada database  terdapat 5 jenis tipe data itu di kelompokan berdasarkan fungsinya, yaitu String, numeric, Date, Boolean, dan Binary. Berikut masing-masing penjelasan dari tipe data, dan contoh dari tipe data pada DBMS MYSQL:


**1. Tipe Data String**

String adalah tipe data yang digunakan pada kolom yang menyimpan data dalam bentuk huruf atau karakter, kalimat, text, dan semacamnya. Kolom yang diinisialisaikan tipe datanya berupa string maka dapat juga menyimpan data dalam bentuk source code, HTML, XML, JSON dan semacamnya dengan format text tertentu misal UTF8. Berikut ini beberapa contoh tipe data string yang dapat anda guanakan di DBMS MYSQL:

| No. | Tipe Data | Fungsi |
| ------ | ------ | ------ |
| 1. | CHAR | Menyimpan data string (huruf, angka, spesial karakter) ukuran panjang karakter atau digit huruf yang tetap. memiliki kapasitas jangkauan 0 s/d 255 karakter. |
| 2. | VARCHAR | Menyimpan String dengan digit huruf yang dinamis dan jumlah maksimal yang telah ditentukan. Dengan kapasitas jangkauan 0 s/d 65535 karakter. |
| 3. | TEXT | Menyimpan String dengan panjang maksimal  65.535 bytes |
| 4. | TINYTEXT | Menyimpan String dengan panjang maksimal 255 karakter |
| 5. | MEDIUMTEXT | Menyimpan data berupa String dengan panjang maksimal 16,777,215 karakter |
| 6. | LONGTEXT | Menyimpan data berupa String dengan panjang maksimal 4,294,967,295 karakter |


**2. Tipe Data Numeric/Angka**

Numeric, dari namanya sudah pasti numeric berarti digunakan pada kolom yang menyimpan data berupa angka. Tipe Data numeric memiliki beberpa format penulisan mislakan bilangan desimal, bilangan bulat, dll. Berikut ini beberapa contoh format dari tipe data numeric:

Tabel Tipe Data Numeric (Angka)
| No. | Tipe Data | Fungsi | Jangkauan/Range | Ukuran |
| ------ | ------ | ------ | ------ | ----- |
| 1. | TINYINT | Bilangan bulat (Positif/Negatif) | -128 s/d 127 | 1 Byte |
| 2. | SMALLINT| Bilangan bulat (Positif/Negatif) | -32.768 s/d 32.767 | 2 Byte |
| 3. | MEDIUMINT | Bilangan bulat (Positif/Negatif) | -8.388.608 s/d 8.388.607 | 3 Byte |
| 4. | INT | Bilangan bulat (Positif/Negatif) | -2.147.483.648 s/d 2.147.483.647 | 4 Byte |
| 5. | BIGINT | Bilangan bulat (Positif/Negatif) | -9.223.372.036.854.775.808 s/d 9.223.372.036.854.775.807 | 8 Byte |
| 6. | FLOAT | Bilangan pecahan presisi tunggal | 3.402823466E+38 s/d -1.175494351E-38, 0, dan 1.175494351E-38 s/d 3.402823466E+38 | 4 Byte |
| 7. | DOUBLE | Bilangan pecahan presisi ganda | -1.79…E+308 s/d -2.22…E-308, 0, dan 2.22…E-308 s/d 1.79…E+308 | 8 Byte |
| 8. | DECIMAL / NUMERIC | Bilangan pecahan (Positif/Negatif) Bilangan desimal dengan nilai tergantung besaran M dan D | -1.79…E+308 s/d -2.22…E-308, 0, dan 2.22…E-308 s/d 1.79…E+308 | M Byte |

Untuk membua tipe data bilangan bulat menjadi positif, hanya perlu ditambahkan kata `UNSIGNED`. Misal, `UNSIGNED INT` memiliki nilai 0 sampai 4.294.967.295.


**3. Tipe data Date (Waktu)**

Date adalah tipe data untuk kolom yang digunakan untuk menyimpan data yang memiliki format waktu bisa berupa tanggal atau pun jam.

Tabel Tipe Data Date (Waktu)
| No. | Tipe Data | Fungsi | Jangkauan/Range |
| ------ | ------ | ------ | ------ |
| 1. | DATE | Menyimpan data tanggal dengan Format (YYYY-MM-DD), Tahun-Bulan-Hari. | 1000-01-01 s/d 9999-12-31 |
| 2. | TIME | Menyimpan String dengan digit huruf yang dinamis dan jumlah maksimal yang telah ditentukan. Dengan kapasitas jangkauan 0 s/d 65535 karakter. | -838:59:59 s/d +838:59:59 |
| 3. | DATETIME | Menyimpan String dengan panjang maksimal  65.535 bytes | 	1000-01-01 00:00:00 s/d 9999-12-31 23:59:59 |
| 4. | YEAR | Menyimpan String dengan panjang maksimal 255 karakter | 1900 s/d 2155 |


**4. Tipe Data Binary**

Binary adalah tipe data yang memungkinkan suatu kolom database dapat menyimpan suatu binary file, Misalkan :
Document: Text Document(.doc, .odf), sparesheet (.xls, .ods)
Multi Media: Gambar (.jpg, .png, .gif), video (.mp4, .mkv), music (.mp3, .acc)

Berikut tabel beberapa contoh tipe data binary yang dapat digunakan pada DBMS MYSQL:
| No. | Tipe Data | Fungsi | Ukuran |
| ------ | ------ | ------ | ------ |
| 1. | BIT | Menyimpan data biner | 64 digit biner |
| 2. | TINYBLOB | Menyimpan gambar ukuran kecil | 255 bytes |
| 3. | BLOB | Menyimpan gambar ukuran standar | 65.535 bytes |
| 4. | MEDIUMBLOB | Menyimpan gambar ukuran cukup besar | 16.777.215 bytes |
| 5. | LONGBLOB | Menyimpan gambar ukuran sangat besar | 4.294.967.295 bytes |


**5. Tipe Data Boolean**

Tipe Data Boolean adalah suatu tipe data yang sifatnya seperti if-else atau if-else-if menungkinkan suatu kolom untuk memiliki pilihan data untuk disimpan. Jadi dengan penerapan tipe data boolean ini memungkinkan untuk menolak insert data yang nilainya diluar pilihan.

Tabel Type Data Boolean
| No. | Tipe Data | Fungsi |
| ------ | ------ | ------ |
| 1. | BOOLEAN | Membadingkan tipe data numberic 0 = False, dan 1 = True |
| 2. | ENUM | Menyimpan data dalam bentuk String tertentu yang telah tersedia pada parameter-nya |

Contoh Pengaplikasian Tipe Data pada Console MySQL

<br>
<img legth="500" src="" />
<br>

## 6. Pengenalan DDL
DDL adalah salah satu bentuk SQL yang bisa digunakan untuk menciptakan atau membuat database, tabel, struktur tabel, merubah struktur database, menghapus tabel, menghapus database serta membuat relasi antar tabel. Oleh sebab itu, DDL ini mempunyai sejumlah perintah dasar yang terdiri atas Create, Alter serta Drop.
 
**1. Create**

`Create` adalah bahasa pemrograman yang digunakan saat kita akan membuat sebuah objek. Dalam perintah ini dapat diklasifikasikan kembali sebagai berikut:

- CREATE DATABASE 
- CREATE FUNCTION
- CREATE INDEX
- CREATE PROCEDURE
- CREATE TABLE
- CREATE TRIGGER
- CREATE VIEW

**2. Alter**

`Alter` adalah perintah yang dipakai manakala hendak mengubah struktur suatu tabel atau memodifikasi bentuk kolom, mengganti ataupun sekedar menambah tabel yang sebelumnya sudah ada.

- ALTER DATABASE
- ALTER FUNCTION
- ALTER PROCEDURE
- ALTER TABLE
- ALTER VIEW
- RENAME TABLE

**3. Rename**

`RENAME TABLE` merupakan perintah yang dibuat untuk mengganti/mengubah nama dari sebuah table.

**4. Drop**

`Drop` adalah perintah yang bisa digunakan terkait dengan penghapusan objek yang terdapat dalam database. `Drop` dapat diklasifikasikan menjadi beberapa macam, yaitu:
- DROP DATABASE
- DROP FUNCTION
- DROP INDEX
- DROP PROCEDURE
- DROP TABLE
- DROP TRIGGER
- DROP VIEW

Penerapannya pada query MySQL akan dibahas pada modul-modul selanjutnya.

## 7. Membuat Database (melalui console dan UI)

Pembuatan sebuah database pada aplikasi XAMPP dapat melalui 2 metode, yaitu menggunakan console dan User Interface (UI). Dengan menggunakan console, maka kita perlu untuk memasukkan query pda SQL yang disediakan. Sedangkan untuk metode UI, kita hanya perlu menggunakan UI yang tersedia dari membuat nama database, sampai membuat atribut yang diinginkan. Untuk membuat database, pastikan bahwa aplikasi XAMPP telah berjalan dan Apache dan MySQL sudah running (status: hijau).

### 7.1 Membuat Database melalui Console
Langkah-langkahnya adalah sebagai berikut:

1. Membuka link http://localhost/phpmyadmin pada web browser

<br>
<img legth="500" src="" />
<br>

2. Pilih menu **SQL** pada toolbar di bagian atas

<br>
<img legth="500" src="" />
<br>

3. Buat sebuah database kosong, misalnya sebuah database bernama `bioskop` maka diketikkan query `CREATE DATABASE bioskop;` seperti berikut:

<br>
<img legth="500" src="" />
<br>

4. Maka akan muncul sebuah database baru bernama `bioskop` pada sebelah kiri tampilan seperti ini.

<br>
<img legth="500" src="" />
<br>

5. Setelah itu, klik database tersebut. Masuk ke dalam menu `SQL` kembali seperti ini:

<br>
<img legth="500" src="" />
<br>

6. Sekarang kita akan memmasukkan beberapa table kedalamnya, misalnya seperti sebuah program berikut:

```sql
CREATE TABLE operator(
    id VARCHAR (20) NOT NULL,
    nama VARCHAR (50) NOT NULL,
    password VARCHAR(100) NOT NULL,
    created_at DATETIME NOT NULL,
    updated_at TIMESTAMP,
    PRIMARY KEY (id)
);

CREATE TABLE film (
    id VARCHAR (20) NOT NULL,
    judul VARCHAR (50) NOT NULL,
    deskripsi TEXT,
    rating VARCHAR (50) NOT NULL,
    produksi VARCHAR(100) NOT NULL,
    distributor VARCHAR(100) NOT NULL,
    durasi INT NOT NULL,
    country VARCHAR(50) NOT NULL,
    created_at DATETIME NOT NULL,
    updated_at TIMESTAMP,
    PRIMARY KEY (id)
);

CREATE TABLE teater (
    id VARCHAR (20) NOT NULL,
    nama VARCHAR (50) NOT NULL,
    created_at DATETIME NOT NULL,
    updated_at TIMESTAMP,
    PRIMARY KEY (id)
);

-- foreign key: teater_id
CREATE TABLE kursi (
    id VARCHAR (20) NOT NULL,
    nama VARCHAR (50) NOT NULL,
    teater_id VARCHAR(20) NOT NULL,
    created_at DATETIME NOT NULL,
    updated_at TIMESTAMP,
    PRIMARY KEY (id)
);

-- foreign key: film_id, teater_id
CREATE TABLE jadwal (
    id VARCHAR (20) NOT NULL,
    hari VARCHAR (50) NOT NULL,
    jam VARCHAR(20) NOT NULL,
    harga INT NOT NULL,
    film_id VARCHAR(20) NOT NULL,
    teater_id VARCHAR(20) NOT NULL,
    created_at DATETIME NOT NULL,
    updated_at TIMESTAMP,
    PRIMARY KEY (id)
);

-- foreign key: operator_id, jadwal_id, kursi_id, 
CREATE TABLE transaksi (
    id VARCHAR(20) NOT NULL,
    operator_id VARCHAR(20) NOT NULL,
    jadwal_id VARCHAR(20) NOT NULL,
    kursi_id VARCHAR(20) NOT NULL,
    jumlah_dibayar INT NOT NULL,
    kembalian INT NOT NULL,
    created_at DATETIME NOT NULL,
    PRIMARY KEY (id)
);
```

7. Setelah itu, maka akan muncul tampilan seperti ini menandakan bahwa tabel-tabel yang dimasukkan telah berhasil dibuat:

<br>
<img legth="500" src="" />
<br>

### 7.2 Membuat Database melalui UI
Langkah-langkahnya adalah sebagai berikut:

1. Pada bagian kiri localhost/phpMyAdmin, silahkan klik New untuk membuat database baru.

<br>
<img legth="500" src="" />
<br>

2. Masukkan nama database pada kolom yang tersedia. Pada tutorial ini, kita menggunakan nama `database_baru` sebagai nama database yang akan dibuat. Jika sudah diberi nama, klik Create.

<br>
<img legth="500" src="" />
<br>

3. Kali ini, mari membuat tabel dengan empat kolom untuk data pengguna dengan nama tabel `users`.  Kemudian, klik tombol **Go**.

<br>
<img legth="500" src="" />
<br>

4. Di bagian ini, Anda harus memasukkan nama kolom dan tipe datanya. Untuk tabel `users`, kita akan membuat kolom `id`, `name`, `email`, dan `address`. Jika sudah terisi seperti gambar di bawah ini, klik tombol `Save`.

<br>
<img legth="500" src="" />
<br>

5. Sekarang, kita sudah memiliki database dengan tabel users yang diinginkan.

<br>
<img legth="500" src="" />
<br>

## Referensi
+ https://www.mysqltutorial.org/install-mysql/
+ https://blog.devart.com/how-to-connect-to-mysql-server.html#dbforge-studio-for-mysql
+ https://docs.oracle.com/en/java/java-components/advanced-management-console/2.21/install-guide/mysql-database-installation-and-configuration-advanced-management-console.html#GUID-00D8401C-C5EF-4F7C-B211-8B268BA0DB91
+ https://www.sinauo.com/2020/04/macam-macam-type-data-database-mysql.html
+ https://www.niagahoster.co.id/blog/cara-membuat-database-di-mysql/#4_Membuat_Database_di_phpMyAdmin
