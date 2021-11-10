# Data Manipulation Language (DML)

## Daftar Isi
- [1. Insert](#1-insert)
- [2. Update](#2-update)
- [3. Delete](#3-delete)
- [4. Select](#4-select)
  - [4.1 Menampilkan data secara keseluruhan](#41-menampilkan-data-secara-keseluruhan)
  - [4.2 Menampilkan kolom tertentu](#42-menampilkan-kolom-tertentu)
  - [4.3 Menampilkan baris data tertentu](#43-menampilkan-baris-data-tertentu)
  - [4.3 Query dengan kondisi](#44-query-dengan-kondisi)


Pada modul kali ini kita akan membahas tentang cara mengoperasikan struktur Data Manipulation Language (DML). Seperti yang telah disebutkan pada modul sebelumnya, DML adalah sebuah bahasa dalam SQL yang digunakan untuk mengambil  dan memanipulasi data dalam database relasional. Topik bahasan dalam modul ini adalah:

## 1. Insert
Insert table digunakan untuk menyisipkan sebuah baris baru ke dalam sebuah tabel. Berikut adalah basic syntax dari insert table:

```sql
INSERT INTO table_name (column1, column2, column3, ...)
VALUES (value1, value2, value3, ...);
```
dengan contoh
```sql
INSERT INTO mahasiswa (id_mahasiswa, NamaDepan, NamaBelakang, Alamat, NRP)
VALUES ('1', 'Ratna', 'Puji', 'Jl. Cendrawasih No.9', '0531653527');
```
![image](https://user-images.githubusercontent.com/73152464/141041968-0187ffa5-3d2c-458a-afe8-b0551e6b91c7.png)

atau ketika kita ingin memasukkan data pada semua kolom, tidak perlu menspesifikkan kolom tertentu sebagai berikut:
```sql
INSERT INTO mahasiswa 
VALUES ('2', 'Liana', 'Steffi', 'Jl. Tumpel Agung', '0531862773');
```

![image](https://user-images.githubusercontent.com/73152464/141042013-27faab8e-dd2e-448f-8ef3-9939ababd36c.png)

ketika kita ingin mengisi beberapa kolom saja, maka syntax yang digunakan adalah sebagai contoh berikut:
```sql
INSERT INTO mahasiswa (NamaDepan, NamaBelakang) 
VALUES ('Dewa', '19');
```

![image](https://user-images.githubusercontent.com/73152464/141042088-32068fea-1748-470c-bb3b-6970a26b6f04.png)

<br> 

## 2. Update
Update table digunakan untuk memodifikasi data pada tabel. Berikut adalah syntax dari update table:
```sql
UPDATE table_name
SET column1 = value1, column2 = value2, ...
WHERE condition;
```
dengan contoh
```sql
UPDATE mahasiswa
SET NamaDepan = 'Nifa', NRP= '0531485624'
WHERE id_mahasiswa = 1;
```

![image](https://user-images.githubusercontent.com/73152464/141042372-164ee798-7c99-46c3-bf33-0561609a1e52.png)

Harap berhati-hati ketika menggunakan syntax UPDATE tanpa WHERE, karena akan memperbarui semua data pada kolom yang diupdate. 

<br>

## 3. Delete
Delete syntax digunakan untuk menghapus data yang terdapat pada tabel. 
```sql
DELETE FROM table_name 
WHERE condition;
```
sebagai contoh
```sql
DELETE FROM mahasiswa 
WHERE id_mahasiswa='2';
```

![image](https://user-images.githubusercontent.com/73152464/141042626-6b26e8f8-a863-4169-9ea0-8b5951b424b2.png)

Kita juga bisa menghapus semua baris pada tabel tanpa menghapus tabel tersebut. Hal tersebut menyebabkan struktur tabel yang telah dibuat di awal tidak terhapus namun semua data pada tabel tersebut akan dihapus.
```sql
DELETE FROM table_name;
```
sebagai contoh:
```sql
DELETE FROM mahasiswa;
```

![image](https://user-images.githubusercontent.com/73152464/141042689-9cbbdce4-9fb9-485f-bbfa-47080dd79db4.png)

<br>

## 4. Select
Select syntax digunakan untuk menampilkan data yang terdapat pada tabel.
### <b>4.1 Menampilkan data secara keseluruhan</b>
Untuk menampilkan data secara keseluruhan dapat menggunakan syntax sebagai berikut:
```sql
SELECT * FROM table_name;
```
sebagai contoh
```sql
SELECT * FROM mahasiswa;
```

![image](https://user-images.githubusercontent.com/73152464/141043230-9811fdfd-b96b-49c9-983f-ca16c68f55f1.png)

### <b>4.2 Menampilkan kolom tertentu</b>
Untuk menampilkan data pada kolom tertentu, dapat menggunakan syntax sebagai berikut:
```sql
SELECT column1, column2, ...
FROM table_name;
```
sebagai contoh:
```sql
SELECT NamaDepan, NamaBelakang
FROM mahasiswa;
```

![image](https://user-images.githubusercontent.com/73152464/141043425-98676838-b7e4-4157-a644-39cab0561f58.png)


### <b>4.3 Menampilkan baris data tertentu</b>
Untuk menampilkan data pada baris tertentu, dapat menggunakan syntax sebagai berikut:
```sql
SELECT * FROM table_name WHERE condition;
```
sebagai contoh:
```sql
SELECT * FROM mahasiswa WHERE id_mahasiswa='1';
```

![image](https://user-images.githubusercontent.com/73152464/141043623-51aa535c-84fa-4ba6-a903-a33b99a368a2.png)

### <b>4.4 Query dengan kondisi</b>
Untuk menampilkan data dengan suatu kondisi, dapat menggunakan syntax sebagai berikut:
```sql
SELECT * FROM table_name WHERE condition;
```
sebagai contoh:
```sql
SELECT * FROM mahasiswa WHERE Alamat='Jl. Tumpel Agung';
```

![image](https://user-images.githubusercontent.com/73152464/141043698-1fd23fc4-8ffa-4685-8454-eae440e7422e.png)

