# UAS Pengembangan Web – Debug REST API CI4
Nama : Dimas Yogi Frediansyah
Nim  : 231080200046
Kelas : 4b1 Informatika

## Tugas:
- Perbaiki minimal 5 bug dari aplikasi
- Catat bug dan solusinya dalam tabel laporan

### Laporan Bug
| No | File                     | Baris | Bug                        | Solusi                                                               |
|----|--------------------------|-------|----------------------------|----------------------------------------------------------------------|
| 1  |app/Models/UserModel.php  |  22   | Weak password hashing (MD5)| TGanti dengan password_hash() dengan cost yang sesuai.   |

| 2  |app/Config/Routes.php     |  7    | Missing auth filter pada refresh endpoint| Tambahkan filter auth pada route refresh.  |

| 3  |AuthController.php        |  18   | Password tidak di-hash     | Gunakan password_hash() untuk meng-hash password sebelum disimpan.|

| 4  |AuthController.php        |  4    |Plain text password comparison|Hash password input dengan password_verify() sebelum membandingkan.|

| 5  |app/Config/JWTLibrary.php |  33   |Hardcoded secret key        | Pindahkan secret key ke file .env dan load menggunakan get          ('JWT_SECRET').|

| 6	 |app/Controllers/AuthController.php	|39–40|	Data email dan password tidak dicek saat login	|Tambahkan pengecekan, misalnya `if (!$email|

| 7	 |UserModel.php	| 18 | 	Password masih di-hash dengan MD5 (kurang aman) |	Ganti dengan password_hash(..., PASSWORD_DEFAULT) supaya lebih aman|

| 8	 |ProjectController.php	| 22 | 	user_id tidak diambil dari token JWT |	Ambil user_id dari token dan simpan ke data request |

| 9	 |JWTLibrary.php	| 12| 	Secret key JWT ditulis langsung di dalam kode |	Pindahkan secret key ke file .env, contoh: JWT_SECRET=your_secure_key_here|

| 10 | 	Database.php	| 8	| Program tidak cek apakah koneksi ke database berhasil | 	Tambahkan pengecekan koneksi dan penanganan error agar aplikasi tidak langsung error| 
## Uji dengan Postman:
- POST /login
- POST /register
- GET /users (token diperlukan)