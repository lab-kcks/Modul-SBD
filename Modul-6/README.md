# Data Manipulation Language (DML) Part 2

## Daftar Isi
- [1. Pengurutan Data](#1-pengurutan-data)
  - [1.1 Asc (Ascending)](##11-asc-(ascending))
  - [1.2 Desc (Descending)](##11-desc-(descending))
- [2. Fungsi Agregasi](#2-fungsi-agregasi)
- [3. Operator Between, IN, LIKE](#3-operator-between,-in,-like)
  - [3.1 Operator Between](#31-operator-between)
  - [3.2 Operator IN](#32-operator-in)
  - [3.3 Operator LIKE](#31-operator-like)
- [4. Ekspresi Query](#4-select)
- [5. Fungsi Waktu](#5-fungsi-waktu)

Pada modul kali ini kita akan membahas lebih lanjut terkait fungsi-fungsi pada DML. Tanpa capcipcup mari kita langsung eksekusi.

## 1. Pengurutan data
Untuk mengurutkan tampilan data dari suatu table, digunakan klausa Order By. Klausa Order By, dapat digunakan untuk mengurutkan data :  
  ### <b> 1.1 Asc (Ascending) <b>
  Untuk mengurutkan data dari kecil ke besar 
  ### <b> 1.2 Desc (Descending) <b>
  Untuk mengurutkan data dari besar ke kecil
  
Syntax dan contoh dari Order By adalah sebagai berikut.
  ```sql
  SELECT column1, column2, ...
  FROM table_name
  ORDER BY column1, column2, ... ASC|DESC;
  ```
Contoh:
  ```sql
  SELECT NamaDepan, NamaBelakang 
  FROM mahasiswa 
  ORDER BY NamaDepan ASC;
  ```

![image](https://user-images.githubusercontent.com/73152464/142403455-984a298d-12bc-44c8-8531-2e7b5cfe4e94.png

## 2. Fungsi Agregasi
Fungsi agregasi dapat digunakan untuk mencari jumlah, rata-rata, nilai maksimal dan nilai minimal dalam field yang terdapat pada table.
Beberapa fungsi agregasi

| Agregasi | Keterangan |
| COUNT | Menghitung cacah data |
| SUM | Menjumlahkan data |
| AVG | Mencari Rata-rata data |
| MAX | Mencari nilai maksimal |
| MIN | Mencari nilai minimal |
  
Syntax dan contoh dari Fungsi Agregasi adalah sebagai berikut.
  ```sql
  SELECT COUNT|SUM|AVG|MAX|MIN(column_name)
  FROM table_name
  WHERE condition;
  ```
Contoh:
  Karena pada tabel kemarin yang punya data angka hanya kolom id_mahasiswa, jadi kita aplikasikan fungsi agregasi ini pada kolom id_mahasiswa :D
  
  ![image](https://user-images.githubusercontent.com/73152464/142405603-2a7dadf1-2295-4577-a19d-59ab2b25dc2e.png)
  
  ```sql
  SELECT MIN(id_mahasiswa) FROM mahasiswa;
  ```
  
  ![image](https://user-images.githubusercontent.com/73152464/142404781-49d68fce-da2e-4a0b-97ab-7e2eab90944f.png)

  ```sql
  SELECT MAX(id_mahasiswa) FROM mahasiswa;
  ```
  
  ![image](https://user-images.githubusercontent.com/73152464/142404920-cac77ff2-4eec-4d89-93de-c8b6d204eb80.png)

  ```sql
  SELECT COUNT(id_mahasiswa) FROM mahasiswa;
  ```
  
  ![image](https://user-images.githubusercontent.com/73152464/142405051-4b310484-6d8c-4ead-9ceb-41574878fffe.png)
  
  ```sql
  SELECT SUM(id_mahasiswa) FROM mahasiswa;
  ```
  
  ![image](https://user-images.githubusercontent.com/73152464/142405205-8e5779db-316e-409d-a54a-d947cc039ba7.png)

  ```sql
  SELECT AVG(id_mahasiswa) FROM mahasiswa;
  ```
  ![image](https://user-images.githubusercontent.com/73152464/142405354-de25964b-d9a2-46b1-99dd-4419dc2cbc24.png)

  
## 3. Operator Between, IN, LIKE
  ### <b> 3.1 Operator Between <b>
  Operator Between merupakan operator yang digunakan untuk menangani operasi memilih nilai dalam rentang tertentu. Nilai dapat berupa angka, teks, atau   tanggal. Syntax dari Operator Between adalah sebagai berikut.
  
  ```sql
  SELECT column_name(s)
  FROM table_name
  WHERE column_name BETWEEN value1 AND value2;
  ```
  
  Contoh:
  ```sql
  SELECT * FROM mahasiswa 
  WHERE id_mahasiswa BETWEEN 2 AND 4;
  ```
  
  ![image](https://user-images.githubusercontent.com/73152464/142406612-efdc10b5-2059-4992-87a9-2511a4197c83.png)

  ```sql
  SELECT * FROM mahasiswa 
  WHERE NamaDepan BETWEEN 'Anugrah' AND 'Liani';
  ```
  
  ![image](https://user-images.githubusercontent.com/73152464/142407025-214ffdb2-e10d-4f4b-bbc3-86974ecc6c6c.png)

  
  ### <b> 3.2 Operator IN <b>
  Operator IN digunakan untuk menentukan beberapa nilai dalam klausa  WHERE. Operator IN biasanya digunakan untuk mencocokkan nilai. Syntax yang digunakan adalah sebagai berikut.
  
  ```sql
  SELECT column_name(s)
  FROM table_name
  WHERE column_name IN (value1, value2, ...);
  ```
  Contoh:
  
  ```sql
  SELECT * FROM mahasiswa 
  WHERE Alamat IN ('Jl. Tumpel Agung');
  ```
  
  ![image](https://user-images.githubusercontent.com/73152464/142407703-a0b0342b-8998-4234-82db-4fc72927af86.png)
  
  ```sql
  SELECT * FROM mahasiswa 
  WHERE Alamat NOT IN ('Jl. Tumpel Agung');
  ```
  
  ![image](https://user-images.githubusercontent.com/73152464/142407846-c64efb39-439b-4767-a6bb-e23e5b327a28.png)

  
  ### <b> 3.3 Operator LIKE <b>
  Operator Like merupakan operator yang digunakan untuk mencari suatu data (search).  Terdapat beberapa simbol yang sering digunakan pada operator ini yaitu:
  - Tanda persen (%) mewakili nol, satu, atau beberapa karakter
  - Tanda garis bawah (_) mewakili satu karakter tunggal
  Syntaxnya sebagai berikut.
  
  ```sql
  SELECT column1, column2, ...
  FROM table_name
  WHERE column LIKE pattern;
  ```
  | No | Pattern | Keterangan |
  | 1. | WHERE table_name LIKE 'a%' | Mencari semua data yang dimulai dengan huruf “a” |
  | 2. | WHERE table_name LIKE '%i' | Mencari semua data yang diakhiri dengan huruf “i” |
  | 3. | WHERE table_name LIKE '%an%' | Mencari semua data yang memiliki huruf “an” di semua posisi |
  | 4. | WHERE table_name LIKE '_i%' | Mencari semua data yang memiliki huruf “i” di posisi kedua |
  | 5. | WHERE table_name LIKE 'a_%' | Mencari semua data yang dimulai dengan huruf “a” dan memiliki setidaknya panjang 2 huruf |
  | 6. | WHERE table_name LIKE 'a__%' | Mencari semua data yang dimulai dengan huruf “a” dan memiliki setidaknya panjang 3 huruf |
  | 7. | WHERE table_name LIKE 'n%a’ | Mencari semua data yang dimulai dengan huruf “a” dan diakhiri dengan huruf “h” |

  Contoh:
  1. `SELECT * FROM mahasiswa WHERE NamaDepan LIKE 'a%'`
  
  ![image](https://user-images.githubusercontent.com/73152464/142408495-7818d1c5-199a-4b3e-99cb-0a2c4038b7e3.png)
  
  2. `SELECT * FROM mahasiswa WHERE NamaBelakang LIKE '%i'`
  
  ![image](https://user-images.githubusercontent.com/73152464/142408854-099fb26f-e035-4c20-9fd1-7bed0bdb3ea0.png)

  3. `SELECT * FROM mahasiswa WHERE NamaDepan LIKE '%an%'`

  ![image](https://user-images.githubusercontent.com/73152464/142409097-1f2c368b-40b3-4dd2-b9fe-ccaa4202fe7c.png)

  4. `SELECT * FROM mahasiswa WHERE NamaDepan LIKE '_i%'`
  
  ![image](https://user-images.githubusercontent.com/73152464/142409206-a9056c32-077a-4fb5-a9b3-05111a4ac08c.png)

  5. `SELECT * FROM mahasiswa WHERE NamaDepan LIKE 'a_%'`

  ![image](https://user-images.githubusercontent.com/73152464/142409334-67e7518a-c15a-48b1-b04c-0a0641d12afa.png)

  6. `SELECT * FROM mahasiswa WHERE NamaDepan LIKE 'a__%'`
  
  ![image](https://user-images.githubusercontent.com/73152464/142409434-2135e2e0-eeeb-47a4-bf3a-3fc359282b56.png)

  7. `SELECT * FROM mahasiswa WHERE NamaDepan LIKE 'n%a'`
  
  ![image](https://user-images.githubusercontent.com/73152464/142409565-e87fa322-2a3a-4c94-8293-1b947ef3f14e.png)

## 4. Ekspresi Query
  Ekspresi Query dapat digunakan untuk melakukan perubahan terhadap field kolom keluaran, menambah baris teks field keluaran.
    
  ### <b> 4.1 Mengganti Nama Field keluaran <b>
  Syntax yang digunakan untuk mengganti nama field keluaran:
  
    ```sql  
    SELECT column_name AS alias_name
    FROM table_name;
    ```
    Contoh:
    
    ```sql
    SELECT NamaDepan AS ini_nama_depan 
    FROM mahasiswa;
    ```
  
    ![image](https://user-images.githubusercontent.com/73152464/142411117-6641a0d4-b1d6-4537-a627-a8de970e3af0.png)

    ```sql
    SELECT NamaDepan AS 'ini_nama_depan', NamaBelakang AS 'ini_nama_belakang' 
    FROM mahasiswa;
    ```
    
    ![image](https://user-images.githubusercontent.com/73152464/142411599-2eec5a55-1fa6-43a0-8969-e6f223e1346d.png)
    
    ### <b> 4.2 Menambahkan Baris Teks Field Keluaran <b>
  
  
## 5. Fungsi Waktu
  
  Kita dapat mengetahui waktu dengan menggunakan syntax SQL. Beberapa Fungsi waktu dalam MySQL antara lain:  
    - Current_Date : Untuk menampilkan tanggal saat ini
    ```sql  
    SELECT CURRENT_DATE 
    ```
  
    ![image](https://user-images.githubusercontent.com/73152464/142410005-2cf01c7b-2879-46c0-8676-3cd66151ad04.png)

    - Current_Time : Untuk menampilkan waktu saat ini
    ``` sql
    SELECT CURRENT_TIME
    ```
  
    ![image](https://user-images.githubusercontent.com/73152464/142410106-78233a30-6258-49e1-87c6-4af48dd23011.png)

    - Current_Timestamp: Untuk menampilkan tanggal dan waktu saat ini
  
    ![image](https://user-images.githubusercontent.com/73152464/142410280-a44bf8a7-d8dc-4462-819e-9bd301b3aa6e.png) 
