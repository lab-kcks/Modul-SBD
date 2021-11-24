# Data Manipulation Language (DML) Part 3

## Daftar Isi
- [1. Select Data dengan Join Table](#1-select-data-dengan-join-table)
- [2. Self Join](#2-self-join)
-	[3. Outer Join Dua Table](#3-outer-join-dua-tabel)
      -	[3.1 Inner Join](#31-inner-join)
      -	[3.2 Left Join](#32-left-join)
      -	[3.3 Right Join](#33-right-join)
      -	[3.4 Full Outer Join](#34-full-outer-join)
-	[4. Outer Join Tiga Table atau Lebih](#4-outer-join-tiga-table-atau-lebih)

## 1. Select Data dengan Join Table

![image](1)

Klausa JOIN pada sebuah sistem basis data digunakan untuk menggabungkan baris dari satu atau lebih tabel, berdasarkan kolom terkait di antara mereka. Atau dalam istilah lain, perintah JOIN dalam SQL digunakan untuk menampilkan data pada table yang saling berelasi atau tanpa berelasi tapi berhubungan. Artinya, kita dapat menampilkan data dalam beberapa table dengan melihat ada kesamaan antar tabel. Walau ada entitas yang berbeda, namun isinya tetap dapat kita hubungkan.

Klausa JOIN dapat dibagi menjadi 2 jenis, yaitu Self Join dan Outer Join.

## 2. Self Join
Self join adalah suatu bentuk kondisi join atau penggabungan yang terdiri hanya dari 1 tabel saja, atau dapat dikatakan bahwa tabel tersebut melakukan operasi JOIN dengan dirinya sendiri.

Syntax nya adalah sebagai berikut:

```sql
SELECT column_name(s)
FROM table1 T1, table1 T2
WHERE condition;
```

Dapat dilihat bahwa tabel yang digunakan dalam operasi ini merupakan tabel yang sama, yaitu `table1`. Misalnya kita memiliki sebuah tabel seperti di bawah ini:

![image](2-1)

Kemudian kita membuat syntax di mana kita ingin melihat daftar pelanggan yang berasal dari kota yang sama seperti berikut:

```sql
SELECT A.CustomerName AS CustomerName1, B.CustomerName AS CustomerName2, A.City
FROM Customers A, Customers B
WHERE A.CustomerID <> B.CustomerID
AND A.City = B.City
ORDER BY A.City;
```

Maka akan diperoleh hasil output sebagai berikut.

![image](2-2)

Apabila ingin melihat dataset secara penuh, referensinya diambil dari https://www.w3schools.com/sql/sql_join_self.asp .

## 3. Outer Join Dua Tabel
![image](3)

Nah untuk outer join, merupakan kondisi join atau penggabungan yang terdiri dari 2 tabel atau lebih. Untuk yang pertama akan kita coba operasi join yang terdiri dari 2 tabel terlebih dahulu biar tidak mumet. Outer join dapat dibagi menjadi 4, yaitu:

- Inner join
- Left join
- Right join
- Full outer join

Untuk memudahkan dalam pemahaman materi, kita akan mencoba praktek dengan menggunakan database bernama `penjualan_buku` dengan diisi syntax sebagai berikut:

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
    id_transaksi INT(10),
    nim INT(10),
    buku VARCHAR(100),
    PRIMARY KEY(id_transaksi)
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

### 3.1 Inner Join
Me-return record yang memiliki nilai yang sama antar kedua tabel. Syntax nya dapat dilihat pada di bawah ini:
```sql
SELECT *
FROM table1
INNER JOIN table2
ON table1.field = table2.field;
```

Dengan menggunakan tabel yang telah dibuat sebelumnya, maka dapat diinputkan syntax seperti ini:
```sql
SELECT *
FROM mahasiswa
INNER JOIN transaksi
ON mahasiswa.nim = transaksi.nim;
```

Table mahasiswa mempunyai 7 record dan table transaksi mempunyai 7 record. Jika menggabungkan kedua data menggunakan INNER JOIN berdasarkan kolom NIM maka hanya tampil 4 data mahasiswa yang meminjam buku di perpustakaan. Hasil outputnya adalah sebagai berikut:

![image](3-1)

### 3.2 Left Join
Me-return semua record dari tabel kiri, baik yang memiliki kecocokan record dengan tabel kanan maupun yang tidak. Syntax nya dapat dilihat pada di bawah ini:
```sql
SELECT *
FROM table1
LEFT JOIN table2
ON table1.field = table2.field;
```

Dengan menggunakan tabel yang telah dibuat sebelumnya, maka dapat diinputkan syntax seperti ini:
```sql
SELECT *
FROM mahasiswa
LEFT JOIN transaksi
ON mahasiswa.nim = transaksi.nim;
```

Table kiri (mahasiswa) akan menjadi table master dan mencari nilai yang sama di table transaksi. Apabila ada mahasiswa yang tidak meminjam buku maka diberi nilai NULL. Hasil outputnya adalah sebagai berikut:

![image](3-2)

### 3.3 Right Join
```sql
SELECT *
FROM table1
RIGHT JOIN table2
ON table1.field = table2.field;
```

Contoh, Mencari data dari table mahasiswa dan tranksaksi berdasarkan kolom NIM. Dengan menggunakan tabel yang telah dibuat sebelumnya, maka dapat diinputkan syntax seperti ini:

```sql
SELECT *
FROM mahasiswa
RIGHT JOIN transaksi
ON mahasiswa.nim = transaksi.nim;
```

Hasil outputnya adalah sebagai berikut:

![image](3-3)

Terdapat 7 transaksi peminjaman buku di perpustakaan. Bagi transaksi yang NIM mahasiswa tidak ada di table mahasiswa akan diberi nilai NULL.

### 3.4 Full Outer Join
Me-return semua record dari tabel kanan dan kiri, baik yang memiliki kecocokan record dengan antar kedua tabel maupun yang tidak. Syntax nya dapat dilihat pada di bawah ini:
```sql
SELECT *
FROM table1
FULL JOIN table2;
```

Dengan menggunakan tabel yang telah dibuat sebelumnya, maka dapat diinputkan syntax seperti ini:

```sql
SELECT *
FROM mahasiswa
FULL JOIN transaksi;
```

Hasil outputnya adalah sebagai berikut:

![image](3-4)

Jika database yang digunakan tidak support `FULL JOIN` (MYSQL tidak support FULL JOIN), maka bisa menggunakan `UNION ALL`.

## 4. Outer Join Tiga Table atau Lebih

Untuk outer join tiga table atau lebih di sini agak sedikit lebih kompleks (tp ttp ez kok, sans). Jadi, kita perlu memahami atribut setiap tabel yang ingin dioperasikan sehingga dapat menghasilkan output berupa penggabungan tabel tersebut. Singkatnya, syntax yang dapat digunakan adalah sebagai berikut:

```sql
SELECT atribut FROM table1

JOIN table2 ON table1.field = table2.field;
JOIN table3 ON table1.field = table3.field;
JOIN table4 ON table1.field = table4.field;
(dst. menyesuaikan jml. tabel yang ingin dioperasikan)

WHERE condition;
```

Contohnya di sini, pada database `pemain_sepakbola`, kita membuat 3 tabel bernama `Pemain`, `Posisi`, dan `Status`. Syntax dari setiap tabelnya adalah sebagai berikut:

Tabel `Pemain`
```sql
CREATE TABLE Pemain
(id_pemain char(5), nama char(20), id_posisi char(20), id_status char(20));

INSERT INTO Pemain
(id_pemain, nama, id_posisi,id_status)
VALUES (1, 'Budi', '3','2');
 
INSERT INTO Pemain
(id_pemain, nama, id_posisi,id_status)
VALUES (2, 'Rindang', '3','1');
 
INSERT INTO Pemain
(id_pemain, nama, id_posisi,id_status)
VALUES (3, 'Bintang', '3','1');
 
INSERT INTO Pemain
(id_pemain, nama, id_posisi,id_status)
VALUES (4, 'Wana', '4','3');
 
INSERT INTO Pemain
(id_pemain, nama, id_posisi,id_status)
VALUES (5, 'Orion', '1','3');
```
Tabel `Posisi`
```sql
CREATE TABLE Posisi
(id_posisi char(5), ket_posisi char(20));

INSERT INTO Posisi
(id_posisi, ket_posisi)
VALUES (1, 'Penyerang');
 
INSERT INTO Posisi
(id_posisi, ket_posisi)
VALUES (2, 'PenyerangLapis2');
 
INSERT INTO Posisi
(id_posisi, ket_posisi)
VALUES (3, 'Gelandang');
 
INSERT INTO Posisi
(id_posisi, ket_posisi)
VALUES (4, 'SayapKanan');
 
INSERT INTO Posisi
(id_posisi, ket_posisi)
VALUES (5, 'SayapKiri');
```

Tabel `Status`
```sql
CREATE TABLE Status
(id_status char(5), ket_status char(20));

INSERT INTO Status
(id_status, ket_status)
VALUES (1, 'Sehat');
 
INSERT INTO Status
(id_status, ket_status)
VALUES (2, 'Cedera');
 
INSERT INTO Status
(id_status, ket_status)
VALUES (3, 'Dipinjam');
```

Kemudian, kita jalankan sebuah syntax outer join berikut:

```sql
SELECT nama, ket_status, ket_posisi FROM pemain
JOIN posisi ON pemain.id_posisi=posisi.id_posisi
JOIN status ON pemain.id_status=status.id_status
WHERE posisi.ket_posisi='Gelandang'
AND status.ket_status='Cedera';
```

Maka diperoleh hasil output seperrti berikut:

![image](4-1)
