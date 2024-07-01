![image](https://github.com/nurulaisyah14/praktikumUAS2/assets/148174512/d473e93d-1af8-408d-b8a2-c048ce256738)
# Tugas Praktikum { UAS } <img src=https://logos-download.com/wp-content/uploads/2016/05/MySQL_logo_logotype.png width="130px" >


|**Nama**|**NIM**|**Kelas**|**Matkul**|
|----|---|-----|------|
|Nurul Aisyah|312310476|TI.23.A.5|Basis Data|

# Studi Kasus : Sub Query

## Soal Praktikum UAS
![image](https://github.com/nurulaisyah14/praktikumUAS2/assets/148174512/ed69fe80-dab7-4ecb-a74f-6ddd6e4e0531)
> **Keterangan** : Terdapat 5 tabel yang terdiri dari tabel Perusahaan, Departemen, Karyawan, Project dan Project Detail.

### *Script SQL berdasarkan Tabel Perusahaan*
```sql
CREATE TABLE Perusahaan(
id_p VARCHAR(10) PRIMARY KEY,
nama VARCHAR(45) NOT NULL,
alamat VARCHAR(45) DEFAULT NULL
);

INSERT INTO Perusahaan (id_p, nama, alamat) VALUES
('P01', 'Kantor Pusat', NULL),
('P02', 'Cabang Bekasi', NULL);
SELECT * FROM Perusahaan;
```
#### *Output Tabel Perusahaan :*
![image](https://github.com/nurulaisyah14/praktikumUAS2/assets/148174512/d54f5efc-fd80-4c0f-86aa-bbc3550430b9)



### *Script SQL berdasarkan Tabel Departemen*
```sql
CREATE TABLE Departemen(
id_dept VARCHAR(10) PRIMARY KEY,
nama VARCHAR(45) NOT NULL,
id_p VARCHAR(10) NOT NULL,
manajer_nik VARCHAR(10) DEFAULT NULL
);

INSERT INTO Departemen (id_dept, nama, id_p, manajer_nik) VALUES
('D01', 'Produksi', 'P02', 'N01'),
('D02', 'Marketing', 'P01', 'N03'),
('D03', 'RnD', 'P02', NULL),
('D04', 'Logistik', 'P02', NULL);
SELECT * FROM Departemen;
```
#### *Output Tabel Departemen :*
![image](https://github.com/nurulaisyah14/praktikumUAS2/assets/148174512/37a362ec-fbee-4221-a368-1fe4c6c1cb15)



### *Script SQL berdasarkan Tabel Karyawan*
```sql
CREATE TABLE Karyawan(
nik VARCHAR(10) PRIMARY KEY,
nama VARCHAR(45) NOT NULL,
id_dept VARCHAR(10) NOT NULL,
sup_nik VARCHAR(10) DEFAULT NULL,
gaji_pokok INT
);

INSERT INTO Karyawan (nik, nama, id_dept, sup_nik, gaji_pokok) VALUES
('N01', 'Ari', 'D01', NULL, 2000000),
('N02', 'Dina', 'D01', NULL, 2500000),
('N03', 'Rika', 'D03', NULL, 2400000),
('N04', 'Ratih', 'D01', 'N01', 3000000),
('N05', 'Riko', 'D01', 'N01', 2800000),
('N06', 'Dani', 'D02', NULL, 2100000),
('N07', 'Anis', 'D02', 'N06', 5000000),
('N08', 'Dika', 'D02', 'N06', 4000000),
('N09', 'Raka', 'D03', 'N06', 2000000);
SELECT * FROM Karyawan;
```
#### *Output Tabel Karyawan :*
![image](https://github.com/nurulaisyah14/praktikumUAS2/assets/148174512/e554edbb-4813-4f94-a9bd-5433cda88394)





### *Script SQL berdasarkan Tabel Project*
```sql
CREATE TABLE Project(
id_proj VARCHAR(10) PRIMARY KEY,
nama VARCHAR(45) NOT NULL,
tgl_mulai DATETIME,
tgl_selesai DATETIME,
status TINYINT(1)
);

INSERT INTO Project (id_proj, nama, tgl_mulai, tgl_selesai, status) VALUES
('PJ01', 'A', '2019-01-10', '2019-03-10', '1'),
('PJ02', 'B', '2019-02-15', '2019-04-10', '1'),
('PJ03', 'C', '2019-03-21', '2019-05-10', '1');
SELECT * FROM Project;
```
#### *Output Tabel Project :*
![image](https://github.com/nurulaisyah14/praktikumUAS2/assets/148174512/1f911e2e-42b7-46b0-b0cd-def686f97394)




### *Script SQL berdasarkan Tabel Project Detail*
```sql
CREATE TABLE Project_detail(
id_proj VARCHAR(10) NOT NULL,
nik VARCHAR(10) NOT NULL
);

INSERT INTO Project_detail (id_proj, nik) VALUES
('PJ01', 'N01'),
('PJ01', 'N02'),
('PJ01', 'N03'),
('PJ01', 'N04'),
('PJ01', 'N05'),
('PJ01', 'N07'),
('PJ01', 'N08'),
('PJ02', 'N01'),
('PJ02', 'N03'),
('PJ02', 'N05'),
('PJ03', 'N03'),
('PJ03', 'N07'),
('PJ03', 'N08');
SELECT * FROM Project_detail;
```
#### *Output Tabel Project Detail :*






## Latihan Praktikum UAS

### 1. Menampilkan Nama Karyawan yang Berada di Departemen yang Dipimpinoleh Manajer dengan Nama 'Rika'
**Script :**

```sql
SELECT nik, nama, id_dept FROM Karyawan WHERE id_dept = (SELECT id_dept FROM Karyawan WHERE nama = 'Dika');
```

**Output :**

![image](https://github.com/nurulaisyah14/praktikumUAS2/assets/148174512/94609d06-cbd1-4c0b-b696-91fac1569fdd)




### 2. Menampilkan Nama Proyek yang dikerjakan oleh Karyawan dari Departemen 'RnD'
**Script :**

```sql
SELECT nik, nama, id_dept, gaji_pokok FROM karyawan WHERE gaji_pokok > (SELECT AVG(gaji_pokok) FROM Karyawan) ORDER BY gaji_pokok DESC;
```

**Output :**

![image](https://github.com/nurulaisyah14/praktikumUAS2/assets/148174512/33a81ad3-1aaa-4d90-b846-0b22b83b0f08)



### 3. Menampilkan Nama Karyawan yang Terlibat dalam Lebih dari Satu Proyek
**Script :**

```sql
SELECT nik, nama FROM Karyawan WHERE id_dept IN (SELECT id_dept FROM Karyawan WHERE nama LIKE '%K%');
```

**Output :**

![image](https://github.com/nurulaisyah14/praktikumUAS2/assets/148174512/b60c025a-4a81-4e86-9ac4-f4a323f8c949)



### 4. Menampilkan Nama Proyek yang melibatkan Karyawan terbanyak.
**Script :**

```sql
SELECT karyawan.nik, karyawan.nama, karyawan.id_dept FROM karyawan JOIN departemen ON karyawan.id_dept = departemen.id_dept WHERE departemen.id_p = 'P01';
```

**Output :**

![image](https://github.com/nurulaisyah14/praktikumUAS2/assets/148174512/a94dffd7-3a58-497f-8b94-332a2e97baf2)



### 5. Menampilkan Nama Proyek yang Diikuti oleh Karyawan dengan Gaji Pokok Kurang dari 3 Juta
**Script :**

```sql
SELECT DISTINCT k1.nik, k1.nama FROM karyawan k1 JOIN karyawan k2 ON k1.id_dept = k2.id_dept WHERE k1.gaji_pokok > (SELECT AVG(gaji_pokok) FROM karyawan WHERE nama LIKE '%K%');
```

**Output :**

![image](https://github.com/nurulaisyah14/praktikumUAS2/assets/148174512/ff406b5a-2461-4835-adc4-96d52efeea00)

