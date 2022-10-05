# Binus University
This repository includes my personal homework for the course Introduction to Database Systems on week 7 and session 11.

## Number 1
Here I demonstrate how to create a database on the console, you guys must have the installation MySQL first and can run it by this command.
```bash
mysql -u username -p password
```
To create the database you can run this query and also don't forget to use the database to create the table inside the database.
```mysql
CREATE DATABASE AplikasiKaryawanTerbaik;
USE AplikasiKaryawanTerbaik;
```
## Number 2
The query below is used to create the table.
```mysql
CREATE TABLE karyawan
(
    id_karyawan   INT NOT NULL PRIMARY KEY,
    nama_karyawan VARCHAR(255),
    nik           VARCHAR(10),
    alamat        VARCHAR(255),
    no_hp         VARCHAR(15),
    pendidikan    VARCHAR(10),
    status        VARCHAR(10),
    username      VARCHAR(255),
    password      VARCHAR(255),
    id_level      INT,
    proses        INT
);

CREATE TABLE kriteria
(
    id_kriteria   INT PRIMARY KEY NOT NULL,
    nama_kriteria VARCHAR(255),
    bobot         VARCHAR(10),
    keterangan    VARCHAR(255),
    jenis         VARCHAR(10)
);

CREATE TABLE level
(
    id_level   INT PRIMARY KEY NOT NULL,
    nama_level VARCHAR(255),
    keterangan VARCHAR(255)
);

CREATE TABLE penilaian
(
    `id_penilaian` INT          NOT NULL PRIMARY KEY,
    `id_kriteria`  INT          NOT NULL,
    `id_karyawan`  INT          NOT NULL,
    `nilai`        INT          NOT NULL,
    `penilai`      VARCHAR(255) NOT NULL
);
```
## Number 3
The query below is used to insert the data into the related table.
```mysql
INSERT INTO `karyawan` (`id_karyawan`, `nama_karyawan`, `nik`, `alamat`, `no_hp`, `pendidikan`, `status`, `username`,
                        `password`, `id_level`, `proses`)
VALUES (1, 'Is Suryani', '1-01-2017', 'semarang', '81326632236', 'Strata 1', ' Tetap', 'admin', 'admin', 1, 1),
       (2, 'Elizabeth Drimiorda Primasari', '08-08-1998', 'semarang', '0812345678', 'Strata 1', 'Tetap', 'manager',
        'manager', 2, 0),
       (3, 'Sigit Yulianto ', '09-09-1988', 'semarang', '0812345679', 'Strata 1', 'Tetap', 'supervisor', 'supervisor',
        3, 0),
       (4, 'Dewanto', '09-09-1988', 'semarang', '08123456710', 'Strata 1', 'Tetap', 'supervisor2', 'supervisor2', 3, 0),
       (5, 'Bambang Broto', '09-09-1988', 'semarang', '08123456711', 'Strata 1', 'Tetap', 'supervisor3', 'supervisor3',
        3, 0),
       (6, 'lsmediYuliarso', '09-09-1988', 'semarang', '08123456712', 'Strata 1', 'Tetap', 'supervisor4', 'supervisor4',
        3, 0),
       (7, 'Henox Claudian', '10-10-1995', 'semarang', '082345678911', 'SMA', 'Kontrak', '', '', 4, 1),
       (8, 'Sumanto', '10-10-1995', 'semarang', '082345678912', 'SMK', 'Kontrak', '', '', 4, 1),
       (9, 'Triyanti', '10-10-1995', 'semarang', '082345678913', 'SMA', 'Outsource', '', '', 4, 1),
       (10, 'Pasiran', '10-10-1995', 'semarang', '082345678914', 'SMK', 'Kontrak', '', '', 4, 1),
       (11, 'Elda Yunita Sari', '10-10-1995', 'semarang', '082345678915', 'SMK', 'Kontrak', '', '', 4, 1),
       (14, 'test', '10-10-1995', 'palembang', '081326632236', 'SMA', 'Outsource', '', '', 4, 0),
       (15, 'rian', '08-08-1998', 'semarang', '086554688', 'SMA', 'Outsource', '', '', 4, 0);

INSERT INTO `level` (`id_level`, `nama_level`, `keterangan`)
VALUES ('1', 'admin', 'Pengelola Sistem'),
       ('2', 'store manager', 'Melihat hasil penilaian'),
       ('3', 'supervisor', 'kepala pramuniaga dan pemberi nilai pramuniaga'),
       ('4', 'pramuniaga', 'pelayan toko buku gramediaem'),
       ('8', 'testing', 'testing data');

INSERT INTO `kriteria` (`id_kriteria`, `nama_kriteria`, `bobot`, `keterangan`, `jenis`)
VALUES ('1', 'karakter', '0.2', 'karakter yang dimiliki oleh pramuniaga', 'benefit'),
       ('2', 'kedisipilinan', '0.25', 'kedisiplinan pramuniaga dalam bekerja', 'benefit'),
       ('3', 'tanggung jawab', '0.25', 'tanggung jawab pramuniaga dengan pekerjaannya', 'benefit'),
       ('4', 'etika', '0.3', 'etika dan perilaku pramuniaga', 'benefit');

INSERT INTO `penilaian` (`id_penilaian`, `id_kriteria`, `id_karyawan`, `nilai`, `penilai`)
VALUES (13, 1, 10, 50, ' Bernadus Adi Dewanto'),
       (14, 2, 10, 60, 'Bernadus Adi Dewanto'),
       (15, 3, 10, 70, 'Bernadus Adi Dewanto'),
       (16, 4, 10, 80, 'Bernadus Adi Dewanto'),
       (17, 1, 11, 80, 'Bambang Broto'),
       (18, 2, 11, 80, 'Bambang Broto'),
       (19, 3, 11, 85, 'Bambang Broto'),
       (20, 4, 11, 85, 'Bambang Broto');
```
## Number 4
The query below is used to retrieve karyawan data which has supervisor level.
```mysql
SELECT karyawan.nama_karyawan, level.nama_level
FROM karyawan
         INNER JOIN level ON karyawan.id_level = level.id_level
WHERE level.id_level = 3;
```
## Number 5
The query below is used to update the data.
```mysql
UPDATE `karyawan` SET `status` = 'Kontrak' WHERE `karyawan`.`id_karyawan` = 9;
```
## Number 6
The query below is used to update the data.
```mysql
# alternative 1
UPDATE `karyawan`
SET `status` = 'Tetap'
WHERE `karyawan`.`id_karyawan` = 7 AND `karyawan`.`id_karyawan` = 11;

# alternative 2
UPDATE `karyawan` SET `status` = 'Tetap' WHERE `karyawan`.`id_karyawan` = 7;
UPDATE `karyawan` SET `status` = 'Tetap' WHERE `karyawan`.`id_karyawan` = 11;
```
## Number 7
The query below is used to update the data.
```mysql
UPDATE `karyawan`
SET `username` = 'Manager1',
    `password` = 'Manager1',
    `id_level` = '2'
WHERE `karyawan`.`id_karyawan` = 3;
```
Created by Rochman Ramadhani Chiefto Irawan ❤.
