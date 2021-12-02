# Stored Procedure & Function

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
```
CREATE PROCEDURE sp_name ([proc_arameter [,…]])
[characteristic ..]
routine_body
```

Function
```
CREATE FUNCTION sp_name ([func_parameter [,…]])
RETURNS type
[characteristic ..]
routine_body
```

Keterangan: 
- proc_arameter:

  [IN | OUT | INOUT] param_name type
  
- func_parameter:

  param_name type
  
- Type :
  Semua type data yang valid di SQL.

- Characteristic:

  LANGUAGE SQL
  
  [NOT] DETERMINISTIC

  {CONTAINS SQL | NO SQL | READS SQL DATA | MODIFIES SQL DATA }

  SQL SECURITY {DEFINER | INVOKER }

  COMMENT ‘string’

- Routine_body:

  Statement SQL procedure yang valid.
  
Jika tidak ada parameter maka empty parameter digunakan dengan menggunakan (). Setiap parameter memiliki IN parameter sebagai default. IN, OUT, INOUT parameter hanya valid untuk procedure, sedangkan untuk function hanya IN parameter saja.

RETURN type hanya berlaku untuk function.

ROUTINE_BODY berisi statement SQL yang valid. Dapat berisi statement sederhana seperti SELECT atau INSERT atau berisi gabungan beberapa statement yang dapat ditulis dengan menggunakan BEGIN .. END. Compound statement dapat berisi deklarasi, loop dan struktur kontrol yang lain

### 4.2 Untuk menghapus

`DROP {PROCEDURE|FUNCTION} [IF EXIST] name`

contoh: `DROP PORCEDURE spDafGaji;`

### 4.3 Untuk memanggil

`CALL name`

contoh: `CALL spDafGaji();`


## 5. Stored Procedure

Prosedur dalam SQL adalah unit subprogram yang terdiri dari sekelompok pernyataan SQL yang dapat dipanggil dengan nama. Setiap prosedur dalam SQL memiliki nama uniknya sendiri yang dapat dirujuk dan dipanggil. 

### Uji Coba

#### 5.1 


