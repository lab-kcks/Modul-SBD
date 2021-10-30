# ALTER, MODIFY, DROP, RENAME (DDL)

Pada modul kali ini, kita akan mempelajari bagaimana cara untuk mengubah struktur tabel dengan mengganti karakteristik atribut-atribut dan dengan menambahkan kolom. Selain itu, kita juga akan belajar bagaimana cara menyalin tabel dan cara menghapus tabel.

Semua perubahan dalam struktur tabel dibuat dengan menggunakan perintah <b>ALTER TABLE</b> diikuti dengan kata kunci yang menghasilkan perubahan spesifik yang ingin dibuat. Tersedia tiga opsi: <b>ADD, MODIFY, dan DROP</b>. kita dapat menggunakan ADD untuk menambahkan kolom, MODIFY untuk mengubah karakteristik kolom, dan DROP untuk menghapus kolom dari tabel. Sebagian besar RDBMS tidak mengizinkan untuk menghapus kolom kecuali kolom tersebut tidak berisi nilai apa pun; karena jika bisa terjadi, tindakan tersebut dapat menghapus data penting yang digunakan oleh tabel lain.



Sintaks dasar untuk menambah atau memodifikasi kolom adalah:
```sql
ALTER TABLE nama_tabel
  {ADD | MODIFY} (nama_kolom tipe_data [ {ADD | MODIFY} nama_kolom tipe_data] );
```
dimana add / modify bisa dipilih salah satu. untuk lebih jelanya akan dijabarkan setelah ini mengenai penggunaan alter table.


## 1. Mengubah kolom tipe data
dengan menggunakan syntax ALTER, kita bisa merubah kolom tipe data dari tabel yang telah di buat sebelumnya. berikut merupakan syntax yang dapat digunakan:
```sql
ALTER TABLE nama_tabel
	MODIFY (nama_kolom tipe_data);
contoh :
ALTER TABLE mahasiswa 
MODIFY (nrp VARCHAR(10));
```

keterangan pada tabel diatas ialah, saya ingin merubah sebuah tipe data pada tabel mahasiswa di kolom nrp yang sebelumnya adalah integer untuk menjadi varchar.

## 2. Menambahkan kolom
kita dapat menambahkan kolom berdasarkan tabel yang telah dibuat sebelumnya. berikut merupakan syntax yang dapat digunakan:
```sql
ALTER TABLE nama_tabel
	ADD (nama_kolom tipe_data);
contoh :
ALTER TABLE mahasiswa
	ADD (alamat VARCHAR(50));
```
*perlu diperhatikan, pada saat menambahkan kolom menggunakan alter, tidak disarankan memasukkan NOT NULL untuk kolom baru, karena hal ini akan berpotensi error. sehingga setiap tabel baru, akan menjadi default null.*

## 3. Menambahkan primary key, foreign key, dan mengecek constraints
- pada saat membuat tabel baru berdasarkan tabel lain, tabel baru tidak menyertakan aturan integritas dari tabel lama. Secara khusus, tidak ada primary key. untuk itu bisa ditambahkan dengan syntax sebagai berikut:

    ```sql
    ALTER TABLE nama_tabel
                    ADD PRIMARY KEY (nama_kolom);
    ```
- kasus yang lain mungkin terjadi ialah ketika lupa untuk menambahkan foreign key dari tabel yang telah diimputkan sebelumnya. 

    ```sql 
    ALTER TABLE nama_tabel 
    ADD FOREIGN KEY (nama_kolom) REFERENCES (nama_tabel2);
    ```
- untuk melakukan check pada constraint juga bisa diterapkan pada tabel. sebagai contoh jika seharusnya terdapat constraint pada sebuah harga yang dimana tidak bisa bernilai negatif. (harus lebih dari 0 atau sama dengan 0), maka dapat diaplikasikan sebagai berikut:
    ```sql
    ALTER TABLE buku
    ADD CHECK (harga_buku >= 0);
    ```

## 4. Menghapus kolom
terkadang, kita ingin mengubah tabel dengan menghapus kolom. dapat menggunakan syntax sebagai berikut:
```sql 
ALTER TABLE nama_tabel
	DROP COLUMN nama_kolom;
```

*perlu diperhatikan dimana beberapa RDBMS tidak bisa melakukan drop untuk semua kolom, terutama jika kolom tersebut ialah foreign key atau primary key, karena akan dapat berdampak pada database itu sendiri.* 

## 5. Menghapus table 
sebuah tabel bia dihapus dengan menggunakan syntax sebagai berikut:
```sql
DROP nama_tabel;
```

## 6. Alter pada constraint
- Perintah ALTER TABLE untuk menambahkan batasan tabel di dalamnya. dengan syntax sebagai berikut :
    ```sql
    ALTER TABLE nama_tabel
    ADD constraint [ ADD constraint ];
    ```
    *jenis-jenis constraint bisa diliat [disini](../Modul-3/README.md)

- Perintah ALTER TABLE untuk menghapus kolom atau tabel
constraint. dengan syntax sebagai berikut :
    ```sql
    ALTER TABLE nama_tabel
    DROP {PRIMARY KEY | COLUMN nama_kolom | CONSTRAINT nama_constraint };
    ```