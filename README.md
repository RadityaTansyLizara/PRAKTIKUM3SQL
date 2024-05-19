# PRAKTIKUM3SQL
| Variable | Isi |
| -------- | --- |
| Nama | RADITYA TANSY LIZARA  |
| NIM | 312310454 |
| Kelas | TI.23.A5 |
| Mata Kuliah | Basis Data |

1. Lakukan penambahan data pada tabel mahasiswa dengan mengisi kd_ds yang belum ada pada data dosen.
dengan menggunakan kode berikut :
```
INSERT INTO dosen (kd_ds, nama) VALUES
('DS001', 'Tya'),
('DS002', 'Zivi'),
('DS003', 'Arsy'),
('DS004', 'Eva'),
('DS005', 'Opik'),
('DS006', 'Caca');
```

![Screenshot (168)](https://github.com/RadityaTansyLizara/PRAKTIKUM3SQL/assets/147571863/4c256128-68ff-40ab-a5c9-23e66d0b3f4f)

***Output :***

![Screenshot (169)](https://github.com/RadityaTansyLizara/PRAKTIKUM3SQL/assets/147571863/c984b31f-6fef-4873-b63c-101ebca70e45)


2. Hapus satu record data pada tabel dosen yang telah dirujuk pada tabel mahasiswa. 
```
DELETE FROM dosen WHERE kd_ds = 'DS005';
```
***Output :***

![Screenshot (167 2)](https://github.com/RadityaTansyLizara/PRAKTIKUM3SQL/assets/147571863/db3f0aee-92e4-4370-957f-749806b36ea3)

3. Ubah mode menjadi **ON UPDATE CASCADE ON DELETE RESTRICT** 

Untuk mengubah CONSTRAINT FOREIGN KEY menjadi **ON UPDATE CASCADE** dan **ON DELETE RESTRICT**, Anda perlu menambahkan CONSTRAINT dengan opsi yang diinginkan. Berikut adalah langkah-langkahnya:

Tambahkan CONSTRAINT FOREIGN KEY dengan opsi ON UPDATE CASCADE dan ON DELETE RESTRICT:
```
ALTER TABLE mahasiswa
ADD CONSTRAINT fk_dosen
FOREIGN KEY (kd_ds)
REFERENCES dosen (kd_ds)
ON UPDATE CASCADE
ON DELETE RESTRICT;
```
***Output :***

![Screenshot (165)](https://github.com/RadityaTansyLizara/PRAKTIKUM3SQL/assets/147571863/f5d8f20b-09e8-453d-bb86-448009804fa9)


4. Lakukan perubahan data pada tabel dosen (kd_ds)

Berikut adalah contoh perintah untuk melakukan perubahan data pada tabel "dosen" dengan kolom "kd_ds":
```
UPDATE dosen SET kd_ds = 'DS005' WHERE nama = 'Opik';
```
Perintah di atas akan mengubah nilai kolom `"kd_ds" "Opik" menjadi "DS005" pada tabel "dosen"`. Anda dapat menyesuaikan nilai yang ingin Anda ubah dan kondisi WHERE sesuai dengan kebutuhan Anda.

Pastikan untuk menjalankan perintah dengan hati-hati dan memastikan bahwa perubahan data yang Anda lakukan sesuai dengan kebutuhan dan kebijakan yang berlaku dalam basis data Anda.

***Output :***

![Screenshot (165)](https://github.com/RadityaTansyLizara/PRAKTIKUM3SQL/assets/147571863/ccadf860-ec96-4f2b-8b6c-9e30bc37bc20)


5. Lakukan penghapusan data pada tabel dosen

Untuk menghapus data dari tabel "dosen" dengan kondisi "kd_ds = 'DS006'", Anda dapat menggunakan perintah DELETE dengan sintaks yang benar. Berikut adalah contoh perintah yang dapat Anda gunakan:
```
DELETE FROM Dosen WHERE kd_ds = 'DS006';
```

***Output :***

![Screenshot (167)](https://github.com/RadityaTansyLizara/PRAKTIKUM3SQL/assets/147571863/73e2d170-65a3-4c62-a471-6d37c24eee60)


6. Ubah mode menjadi **ON UPDATE CASCADE ON DELETE SET NULL**
```
ALTER TABLE mahasiswa
DROP FOREIGN KEY fk_dosen;
```
```
ALTER TABLE mahasiswa
ADD CONSTRAINT fk_dosen
FOREIGN KEY (kd_ds)
REFERENCES dosen (kd_ds)
ON DELETE SET NULL;
```
***Output :***

![image](https://github.com/RadityaTansyLizara/PRAKTIKUM3SQL/assets/147571863/ccffc3c1-c294-4043-8370-034989621f6b)


Dengan perubahan di atas, ketika Anda menghapus record dari tabel "dosen" yang memiliki referensi di tabel "mahasiswa", nilai kolom "kd_ds" dalam tabel "mahasiswa" yang mengacu pada record yang dihapus akan diatur menjadi NULL.

Setelah menjalankan perintah di atas, Anda dapat kembali mencoba menghapus record dengan menggunakan perintah berikut:

7. Lakukan penghapusan data pada tabel dosen
```
DELETE FROM dosen WHERE kd_ds = 'DS003';
```
Perintah ini akan menghapus record dengan nilai "DS003" dari tabel "dosen", dan karena menggunakan opsi ON DELETE SET NULL, nilai kolom "kd_ds" dalam tabel "mahasiswa" yang mengacu pada record yang dihapus akan diatur menjadi NULL.

# Evaluasi dan Pertanyaan

### Tulis semua perintah-perintah SQL percobaan di atas beserta outputnya!

- Membuat foreign key

Dalam ALTER TABLE:
```
ALTER TABLE mahasiswa
ADD CONSTRAINT fk_dosen
FOREIGN KEY (kd_ds) REFERENCES dosen(kd_ds)
```

Dalam CREATE TABLE:
```
CREATE TABLE mahasiswa(
nim VARCHAR(10) NOT NULL,
nama VARCHAR(100) NOT NULL,
kd_ds VARCHAR(10),
PRIMARY KEY(nim),
CONSTRAINT fk_Dosen FOREIGN KEY (kd_ds)
REFERENCES dosen(kd_ds)
);
```

- Mengubah data
```
UPDATE mahasiswa
SET kd_ds = 'DS001' WHERE nim = 112233445;
```

- Menampilkan CREATE TABLE
```
SHOW CREATE TABLE  mahasiswa;
Mode ON UPDATE CASCADE ON DELETE CASCADE
```
```
ALTER TABLE mahasiswa
DROP FOREIGN KEY fk_mahasiswa_dosen,
ADD CONSTRAINT fk_dosen FOREIGN KEY (kd_ds) REFERENCES dosen(kd_ds) ON UPDATE CASCADE ON DELETE CASCADE;
```

- Menghapus data
```
DELETE FROM dosen WHERE kd_ds = 'DS001';
Mode ON UPDATE CASCADE ON DELETE NOT NULL
```
```
ALTER TABLE <table>
DROP FOREIGN KEY <nama_constraint_lama>,
ADD CONSTRAINT <nama_constraint_baru> FOREIGN KEY (field) REFERENCES <table_references(filed_references)> ON UPDATE CASCADE ON DELETE NOT NULL;
```

- Mengubah data
```
UPDATE dosen
SET kd_ds = 'DS006' WHERE nama = 'Halo';
```

- Menghapus data
```
DELETE FROM dosen WHERE nim = 'DS003';
```

### Apa bedanya penggunaan RESTRICT dan penggunaan CASCADE

Perbedaan utama antara penggunaan RESTRICT dan CASCADE adalah pada cara mereka menangani operasi database yang dapat menyebabkan pelanggaran referensi integritas data.

Penggunaan RESTRICT:

Mencegah operasi database yang akan mengakibatkan pelanggaran referensi integritas data.
Operasi akan dibatalkan dan pesan error akan ditampilkan.
Cocok untuk situasi di mana Anda ingin memastikan bahwa data yang direferensikan tetap valid dan tidak dihapus secara tidak sengaja.
Penggunaan CASCADE:

Secara otomatis menghapus data yang direferensikan jika operasi database menyebabkan pelanggaran referensi integritas data.
Digunakan ketika Anda ingin memastikan konsistensi data dan bersedia menghapus data yang direferensikan jika diperlukan.
Perlu berhati-hati saat menggunakan CASCADE karena dapat menyebabkan hilangnya data yang tidak diinginkan.
Contoh:

Misalkan Anda memiliki dua tabel: Customers dan Orders. Tabel Orders memiliki kolom customer_id yang mereferensikan kolom id pada tabel Customers.

### Berikan Kesimpulan anda !

Constraint atau batasan dalam SQL adalah aturan yang digunakan untuk membatasi nilai data yang dapat disimpan dalam tabel database. Constraint membantu memastikan integritas dan konsistensi data dengan menegakkan aturan bisnis dan mencegah data yang tidak valid masuk ke dalam database.
RESTRICT adalah kata kunci yang digunakan dalam SQL untuk mencegah operasi database yang dapat menyebabkan pelanggaran integritas data referensial. Integritas data referensial memastikan bahwa data dalam tabel yang berbeda saling terkait dengan benar.
Kesimpulan tentang CASCADE
CASCADE adalah kata kunci yang digunakan dalam SQL untuk secara otomatis menghapus data yang direferensikan ketika operasi database menyebabkan pelanggaran integritas data referensial. Integritas data referensial memastikan bahwa data dalam tabel yang berbeda saling terkait dengan benar.
