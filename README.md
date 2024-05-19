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
('DS001', 'Arif'),
('DS002', 'Bagus'),
('DS003', 'Iqbal'),
('DS004', 'Radit'),
('DS005', 'Uyun');
```
GAMBAR

***Output :***

GAMBAR

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

GAMBAR

4. Lakukan perubahan data pada tabel dosen (kd_ds)

Berikut adalah contoh perintah untuk melakukan perubahan data pada tabel "dosen" dengan kolom "kd_ds":
```
UPDATE dosen SET kd_ds = 'DS005' WHERE nama = 'Radit';
```
Perintah di atas akan mengubah nilai kolom `"kd_ds" "Radit" menjadi "DS005" pada tabel "dosen"`. Anda dapat menyesuaikan nilai yang ingin Anda ubah dan kondisi WHERE sesuai dengan kebutuhan Anda.

Pastikan untuk menjalankan perintah dengan hati-hati dan memastikan bahwa perubahan data yang Anda lakukan sesuai dengan kebutuhan dan kebijakan yang berlaku dalam basis data Anda.

***Output :***

GAMBAR

5. Lakukan penghapusan data pada tabel dosen

Untuk menghapus data dari tabel "dosen" dengan kondisi "kd_ds = 'DS006'", Anda dapat menggunakan perintah DELETE dengan sintaks yang benar. Berikut adalah contoh perintah yang dapat Anda gunakan:
```
DELETE FROM Dosen WHERE kd_ds = 'DS006';
```

***Output :***

GABAR

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

GAMBAR

Dengan perubahan di atas, ketika Anda menghapus record dari tabel "dosen" yang memiliki referensi di tabel "mahasiswa", nilai kolom "kd_ds" dalam tabel "mahasiswa" yang mengacu pada record yang dihapus akan diatur menjadi NULL.

Setelah menjalankan perintah di atas, Anda dapat kembali mencoba menghapus record dengan menggunakan perintah berikut:

7. Lakukan penghapusan data pada tabel dosen
```
DELETE FROM dosen WHERE kd_ds = 'DS003';
```
***0utput :***

GAMBAR

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
SET kd_ds = 'DS006' WHERE nama = 'Haha Hihi';
```

- Menghapus data
```
DELETE FROM dosen WHERE nim = 'DS003';
```

### Apa bedanya penggunaan RESTRICT dan penggunaan CASCADE
