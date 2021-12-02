# Stored Procedure & Function

## Daftar Isi
- [1. Pendahuluan](#1-pendahuluan)
- [2. Keuntungan](#2-keuntungan)
- [3. Terminologi](#3-terminologi)
     - [3.1 Parameter](#31-parameter)
     - [3.2 RETURN](#32-return)
- [4. Syntax](#4-syntax)
     - [4.1 Create](#41-untuk-membuat)
     - [4.2 Drop](#42-untuk-menghapus)
     - [4.3 Call](#43-untuk-memanggil)
     - [4.2 Show](#44-untuk-melihat-listnya)
- [5. Uji coba](#5-uji-coba)
     - [5.1 Procedure](#51-uji-coba-procedure)
     - [5.1.1 Parameter IN](#511-procedure-parameter-in)
     - [5.1.2 Parameter OUT](#512-procedure-parameter-out)
     - [5.1.3 Parameter INOUT](#513-procedure-parameter-inout)
     - [5.1.4 Parameter IN dan OUT](#514-procedure-parameter-in-dan-out)
     - [5.1.5 Compound Statement](#515-procedure-compound-statement)
     - [5.2 Function](#52-uji-coba-function)
- [6. Perbedaan](#6-perbedaan)

## 1. Pendahuluan
Procedure & Function adalah subprogram yang dapat dibuat dan disimpan dalam database sebagai objek database. Mereka dapat dipanggil program lain atau melalui SQL.
Terdapat 2 function pada MYSQL:
  1) Function yang sudah ada pada sistem (built-in) contoh:

    TO_NUMBER(text, format), LOWER(text), ADD_MONTHS(date, no.of months), dll

  2) Function yang dibuat oleh user

## 2. Keuntungan
  - Cepat, kompilasi dilakukan di Database (kadang disebut “pre -compilation”) sehingga mengurangi traffic data
  - Adanya pemisahan antara database access logic dengan application logic sehingga program aplikasi menjadi lebih sederhana dan lebih ringkas (thin client concept)
  - Berupa obyek dalam database, sehingga menghilangkan ketergantungan terhadap bahasa program yang digunakan
  - Bersifat Portable, jika bisa berjalan di database tsb maka dipastikan jika database bisa terinstall di manapun maka store procedure/function pasti bisa dijalankan

## 3. Terminologi

### 3.1 Parameter
Parameter merupakan variabel memori yang digunakan untuk menerima suatu nilai dari pemangilnya.

Terdapat 3 mode parameter yaitu : IN, OUT, dan INOUT
- IN 

  Parameter ini digunakan untuk memberikan input ke subprogram. Nilainya konstan. Dalam pernyataan pemanggilan, parameter ini dapat berupa variabel atau nilai literal   atau ekspresi. Secara default, parameternya adalah tipe IN.

- OUT

  Parameter ini digunakan untuk mendapatkan output dari subprogram. Nilainya dapat diubah di dalam subprogram. Dalam pernyataan pemanggilan, parameter ini harus         selalu berupa variabel untuk menampung nilai dari subprogram. 

- IN OUT 

  Parameter ini digunakan baik untuk memberikan input maupun untuk mendapatkan output dari subprogram. Nilainya dapat diubah di dalam subprogram. Dalam pernyataan       pemanggilan, parameter ini harus selalu berupa variabel untuk menampung nilai dari subprogram. 
  
### 3.2 RETURN
RETURN adalah kata kunci yang menginstruksikan kompiler untuk mengalihkan kontrol dari subprogram ke pernyataan panggilan. Di Function RETURN juga mengembalikan nilai.

## 4. Syntax

### 4.1 Untuk membuat

Procedure
```sql
CREATE PROCEDURE sp_name ([proc_arameter [,…]])
routine_body
```

Function
```sql
CREATE FUNCTION sp_name ([func_parameter [,…]])
RETURNS type
routine_body
```

Keterangan: 
- proc_arameter:

  [IN | OUT | INOUT] param_name type
  
- func_parameter:

  param_name type
  
- Type :
  Semua type data yang valid di SQL.

- Routine_body:

  Statement SQL procedure yang valid.
  
Jika tidak ada parameter maka empty parameter digunakan dengan menggunakan (). Setiap parameter memiliki IN parameter sebagai default. IN, OUT, INOUT parameter hanya valid untuk procedure, sedangkan untuk function hanya IN parameter saja.

RETURN type hanya berlaku untuk function.

ROUTINE_BODY berisi statement SQL yang valid. Dapat berisi statement sederhana seperti SELECT atau INSERT atau berisi gabungan beberapa statement yang dapat ditulis dengan menggunakan BEGIN .. END. Compound statement dapat berisi deklarasi, loop dan struktur kontrol yang lain

### 4.2 Untuk menghapus

```
sql DROP {PROCEDURE|FUNCTION} [IF EXIST] name
```

contoh: 
```
sql DROP PORCEDURE spDafGaji;
```

### 4.3 Untuk memanggil

```sql 
CALL name
```

contoh: 
```sql 
CALL spDafGaji();
```

### 4.4 Untuk melihat listnya

```sql 
SHOW {PROCEDURE|FUNCTION} statu s;
```

contoh: 
```sql 
Show PROCEDURE status;
```


## 5. Uji Coba

Tabel dan record yang akan digunakan:
```sql
CREATE TABLE `jurusan` (
  `id` int(11) NOT NULL,
  `kode_jurusan` varchar(2) NOT NULL,
  `nama_jurusan` varchar(50) NOT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4;

INSERT INTO `jurusan` (`id`, `kode_jurusan`, `nama_jurusan`) VALUES
(1, '01', 'Informatika'),
(2, '02', 'Kimia'),
(3, '03', 'Biologi');

CREATE TABLE `mahasiswa` (
  `id` int(11) NOT NULL,
  `nama` varchar(30) NOT NULL,
  `kode_jurusan` varchar(2) NOT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4;

INSERT INTO `mahasiswa` (`id`, `nama`, `kode_jurusan`) VALUES
(1, 'Andi', '01'),
(2, 'Bob', '01'),
(3, 'Caca', '02'),
(4, 'David', '02'),
(5, 'Erika', '03');
```

Hasil akhir struktur database

![image](https://github.com/Kota-Cerdas-dan-Keamanan-Siber/Modul-SBD/blob/main/Modul-9/img/modul9-0.jpg)

### 5.1 Uji Coba Procedure

#### 5.1.1 Procedure Parameter IN

Menambahkan Procedure
```sql
CREATE PROCEDURE sp_jurusan_mhs(kdjurusan char(2))
SELECT m.nama, m.kode_jurusan, j.nama_jurusan
FROM mahasiswa m 
LEFT JOIN jurusan j
ON j.kode_jurusan = m.kode_jurusan
WHERE m.kode_jurusan = kdjurusan;
```

Memanggil Procedure
```sql
CALL sp_jurusan_mhs('01')
```

Hasil

![image](https://github.com/Kota-Cerdas-dan-Keamanan-Siber/Modul-SBD/blob/main/Modul-9/img/modul9-1.jpg)

#### 5.1.2 Procedure Parameter OUT

Menambahkan Procedure
```sql
CREATE PROCEDURE sp_sum_mhs (OUT sum int(11))
SELECT count(*) INTO sum FROM mahasiswa;
```

Memanggil Procedure
```sql
CALL sp_sum_mhs(@n);
SELECT @n;
```

Hasil

![image](https://github.com/Kota-Cerdas-dan-Keamanan-Siber/Modul-SBD/blob/main/Modul-9/img/modul9-2.jpg)

#### 5.1.3 Procedure Parameter INOUT

Menambahkan Procedure
```sql
CREATE PROCEDURE sp_telp (INOUT telp varchar(20))
SELECT CONCAT("(",left(telp,3),") ",substring(telp,4,3),"-",substring(telp,7))
INTO telp
```

Memanggil Procedure
```sql
SET @telp = '0211234567';
CALL sp_telp(@telp);
SELECT @telp;
```

Hasil

![image](https://github.com/Kota-Cerdas-dan-Keamanan-Siber/Modul-SBD/blob/main/Modul-9/img/modul9-3.jpg)

#### 5.1.4 Procedure Parameter IN dan OUT

Menambahkan Procedure
```sql
CREATE PROCEDURE sp_sum_jurusan(IN kdjurusan char(2), OUT sum int)
SELECT count(*) INTO sum FROM mahasiswa
WHERE kode_jurusan = kdjurusan;
```

Memanggil Procedure
```sql
CALL sp_sum_jurusan('01', @n);
SELECT @n;
```

Hasil

![image](https://github.com/Kota-Cerdas-dan-Keamanan-Siber/Modul-SBD/blob/main/Modul-9/img/modul9-4.jpg)

#### 5.1.5 Procedure Compound Statement

Menambahkan Procedure
```sql
DELIMITER $$
CREATE PROCEDURE sp_ganti_jurusan (kd varchar(2), nm varchar(20))
BEGIN
    IF(EXISTS(SELECT kode_jurusan FROM jurusan WHERE kode_jurusan = kd))
    THEN
    	UPDATE jurusan SET nama_jurusan = nm WHERE kode_jurusan = kd;
    ELSE
    	INSERT INTO jurusan (kode_jurusan,nama_jurusan) VALUES (kd,nm);
    END IF;
END;
$$
DELIMITER ;
```

Memanggil Procedure
```sql
CALL sp_ganti_jurusan('01', 'Statistika')
```

Hasil

![image](https://github.com/Kota-Cerdas-dan-Keamanan-Siber/Modul-SBD/blob/main/Modul-9/img/modul9-5.jpg)

### 5.2 Uji Coba Function

Menambahkan Function
```sql
DELIMITER $$
CREATE FUNCTION f_sum_mhs (kdjurusan char(2))
RETURNS int
BEGIN
    DECLARE sum int;
    SELECT COUNT(*) INTO sum FROM mahasiswa
    	where kode_jurusan = kdjurusan;
    RETURN sum;
END;
$$
DELIMITER ;
```

Memanggil Function
```sql
SELECT kode_jurusan, nama_jurusan, f_sum_mhs(kode_jurusan) FROM jurusan
```

Hasil

![image](https://github.com/Kota-Cerdas-dan-Keamanan-Siber/Modul-SBD/blob/main/Modul-9/img/modul9-6.jpg)

## 6. Perbedaan

| PROCEDURE | FUNCTION |
| ------ | ------ |
| Digunakan terutama untuk menjalankan proses tertentu | Digunakan terutama untuk melakukan beberapa perhitungan |
| Tidak dapat dipanggil dalam pernyataan SELECT | Fungsi yang tidak berisi pernyataan DML dapat dipanggil dalam pernyataan SELECT |
| Gunakan parameter OUT untuk mengembalikan nilai | Gunakan RETURN untuk mengembalikan nilai |
| Tidak wajib mengembalikan nilainya | Wajib mengembalikan nilainya |
| RETURN hanya akan keluar dari kontrol dari subprogram | RETURN akan keluar dari kontrol dari subprogram dan juga mengembalikan value |
| Tipe data yang dikembalikan tidak akan ditentukan pada saat pembuatan | Mengembalikan tipe data wajib pada saat pembuatan |
