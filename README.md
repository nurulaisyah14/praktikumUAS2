![image](https://github.com/nurulaisyah14/praktikumUAS2/assets/148174512/d473e93d-1af8-408d-b8a2-c048ce256738)
# Tugas Praktikum { UAS } <img src=https://logos-download.com/wp-content/uploads/2016/05/MySQL_logo_logotype.png width="130px" >


|**Nama**|**NIM**|**Kelas**|**Matkul**|
|----|---|-----|------|
|Nurul Aisyah|312310476|TI.23.A.5|Basis Data|

# Studi Kasus : Sub Query

## Soal Praktikum UAS
![image](https://github.com/nurulaisyah14/praktikumUAS2/assets/148174512/8d4524f8-5847-4fd5-8fa2-d1c30cb464bf)
> **Keterangan** : Terdapat 5 tabel yang terdiri dari tabel Perusahaan, Departemen, Karyawan, Project dan Project Detail.



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

