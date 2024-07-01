![image](https://github.com/nurulaisyah14/praktikumUAS2/assets/148174512/d473e93d-1af8-408d-b8a2-c048ce256738)
# Tugas Praktikum { UAS } <img src=https://logos-download.com/wp-content/uploads/2016/05/MySQL_logo_logotype.png width="130px" >


|**Nama**|**NIM**|**Kelas**|**Matkul**|
|----|---|-----|------|
|Nurul Aisyah|312310476|TI.23.A.5|Basis Data|

## Soal Praktikum UAS
![image](https://github.com/nurulaisyah14/praktikumUAS2/assets/148174512/8d4524f8-5847-4fd5-8fa2-d1c30cb464bf)
> **Keterangan** : Terdapat 5 tabel yang terdiri dari tabel Perusahaan, Departemen, Karyawan, Project dan Project Detail.



## Latihan Praktikum UAS

### 1. Menampilkan Nama Karyawan yang Berada di Departemen yang Dipimpin oleh Manajer dengan Nama 'Rika'
**Script :**

```sql
SELECT Karyawan.nik, Karyawan.nama
FROM Karyawan
JOIN Departemen ON Karyawan.id_dept = Departemen.id_dept
WHERE Departemen.manajer_nik = (
    SELECT nik FROM Karyawan WHERE nama = 'Rika'
);
```

**Output :**

![image](https://github.com/nurulaisyah14/praktikumUAS2/assets/148174512/94609d06-cbd1-4c0b-b696-91fac1569fdd)




### 2. Menampilkan Nama Proyek yang dikerjakan oleh Karyawan dari Departemen 'RnD'
**Script :**

```sql
SELECT DISTINCT Project.nama
FROM Project
JOIN Project_detail ON Project.id_proj = Project_detail.id_proj
JOIN Karyawan ON Project_detail.nik = Karyawan.nik
JOIN Departemen ON Karyawan.id_dept = Departemen.id_dept
WHERE Departemen.nama = 'RnD';
```

**Output :**

![image](https://github.com/nurulaisyah14/praktikumUAS2/assets/148174512/33a81ad3-1aaa-4d90-b846-0b22b83b0f08)



### 3. Menampilkan Nama Karyawan yang Terlibat dalam Lebih dari Satu Proyek
**Script :**

```sql
SELECT Karyawan.nik, Karyawan.nama, COUNT(Project_detail.id_proj) AS jumlah_proyek
FROM Karyawan
JOIN Project_detail ON Karyawan.nik = Project_detail.nik
GROUP BY Karyawan.nik, Karyawan.nama
HAVING COUNT(Project_detail.id_proj) > 1;
```

**Output :**

![image](https://github.com/nurulaisyah14/praktikumUAS2/assets/148174512/b60c025a-4a81-4e86-9ac4-f4a323f8c949)



### 4. Menampilkan Nama Proyek yang melibatkan Karyawan terbanyak.
**Script :**

```sql
SELECT Project.nama, COUNT(Project_detail.nik) AS jumlah_karyawan
FROM Project
JOIN Project_detail ON Project.id_proj = Project_detail.id_proj
GROUP BY Project.nama
ORDER BY jumlah_karyawan DESC
LIMIT 1;
```

**Output :**

![image](https://github.com/nurulaisyah14/praktikumUAS2/assets/148174512/a94dffd7-3a58-497f-8b94-332a2e97baf2)



### 5. Menampilkan Nama Proyek yang Diikuti oleh Karyawan dengan Gaji Pokok Kurang dari 3 Juta
**Script :**

```sql
SELECT DISTINCT P.nama
FROM Project P
JOIN Project_detail PD ON P.id_proj = PD.id_proj
JOIN Karyawan K ON PD.nik = K.nik
WHERE K.gaji_pokok < 3000000;
```

**Output :**

![image](https://github.com/nurulaisyah14/praktikumUAS2/assets/148174512/ff406b5a-2461-4835-adc4-96d52efeea00)

