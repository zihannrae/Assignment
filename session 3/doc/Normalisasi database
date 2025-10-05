# Pemanfaatan AI untuk Normalisasi Database 
---
Normalisasi *database* atau basis data merupakan sebuah proses pengorganisasian data dengan tujuan meminimalkan redudansi data dan meningkatkan integritas data. 

Perkembangan Akal Imitasi (AI) juga dimanfaatkan dalam lingkup ini lantaran dapat membuat alur kerja lebih efisien. Langkah-langkah pemanfaatan AI dalam normalisassi *database* di antaranya sebagai berikut :

## 1. Buka browser dan cari website perangkat ai 
        Perangkat AI yang dimaksud dapat berupa [chat.gpt](https://www.chatgpt.com), [Perplexity](https://www.perplexity.ai), ataupun perangkat AI lainnya. 
## 2. Masukkan perintah atau *prompt* ke dalam menu pencarian
        Contoh prompt : `Buatlah langkah-langkah pemanfaatan AI untuk normalisasi database n1,n2,n3 menggunakan linus mint melalui MariaDB dengan database perpustakaan`
## 3. Buka MAriadb
        Pastikan Mariadb telah terinstall 
        `sudo systemctl start mariadb`
         `sudo systemctl enable mariadb`  
        login ke Mariadb
        `sudo mysql -u root`
## 3. Masukkan query ke dalam terminal 
### I. Buat database dan tabel awal (belum normalisasi)
CREATE DATABASE perpustakaan;
USE perpustakaan;

CREATE TABLE buku_awal (
  id_buku INT PRIMARY KEY,
  judul VARCHAR(100),
  penulis VARCHAR(50),
  kategori VARCHAR(50),
  penerbit VARCHAR(50),
  tahun_terbit YEAR,
  nama_anggota VARCHAR(50),
  alamat_anggota VARCHAR(100),
  buku_dipinjam INT
);
### II. Isi tabel dengan contoh data 
INSERT INTO buku_awal VALUES
(1, 'Pemrograman Python', 'Budi Santoso', 'Teknologi', 'Gramedia', 2020, 'Ani', 'Jl. Melati No 5', 1),
(2, 'Belajar AI', 'Sari Wulandari', 'Teknologi', 'Erlangga', 2021, 'Budi', 'Jl. Mawar No 10', 2),
(3, 'Sejarah Indonesia', 'Agus Santoso', 'Sejarah', 'Kompas', 2018, 'Ani', 'Jl. Melati No 5', 3);
### III. Gunakan AI untuk normalisasi data
Copy skema dan data, lalu tanyakan ke AI dengan prompt : 
`Tolong bantu saya normalisasi tabel database perpustakaan ini yang masih belum terstruktur. Tabel memiliki kolom: id_buku, judul, penulis, kategori, penerbit, tahun_terbit, nama_anggota, alamat_anggota, buku_dipinjam. Jelaskan langkah normalisasi sampai 3NF dan buatkan skema tabel hasil normalisasi beserta contoh SQL untuk MariaDB.`
AI akan menjawab untuk memisahkan tabel menjadi :
`- Buku (id_buku, judul, penulis, kategori_id, penerbit_id, tahun_terbit)`
`- Kategori (kategori_id, nama_kategori)`
`- Penerbit (penerbit_id, nama_penerbit)`
`- Anggota (id_anggota, nama_anggota, alamat_anggota)`
`- Peminjaman (id_peminjaman, id_anggota, id_buku, tanggal_pinjam, tanggal_kembali)`
### IV. Buat tabel normalisasi 
masukkan ke dalamm terminal: 
-- Kategori
CREATE TABLE kategori (
  kategori_id INT PRIMARY KEY AUTO_INCREMENT,
  nama_kategori VARCHAR(50) NOT NULL
);

-- Penerbit
CREATE TABLE penerbit (
  penerbit_id INT PRIMARY KEY AUTO_INCREMENT,
  nama_penerbit VARCHAR(50) NOT NULL
);

-- Buku
CREATE TABLE buku (
  id_buku INT PRIMARY KEY,
  judul VARCHAR(100),
  penulis VARCHAR(50),
  kategori_id INT,
  penerbit_id INT,
  tahun_terbit YEAR,
  FOREIGN KEY (kategori_id) REFERENCES kategori(kategori_id),
  FOREIGN KEY (penerbit_id) REFERENCES penerbit(penerbit_id)
);

-- Anggota
CREATE TABLE anggota (
  id_anggota INT PRIMARY KEY AUTO_INCREMENT,
  nama_anggota VARCHAR(50),
  alamat_anggota VARCHAR(100)
);

-- Peminjaman
CREATE TABLE peminjaman (
  id_peminjaman INT PRIMARY KEY AUTO_INCREMENT,
  id_anggota INT,
  id_buku INT,
  tanggal_pinjam DATE,
  tanggal_kembali DATE,
  FOREIGN KEY (id_anggota) REFERENCES anggota(id_anggota),
  FOREIGN KEY (id_buku) REFERENCES buku(id_buku)
);
### V. Isi data kategori dan penerbit 
INSERT INTO kategori (nama_kategori) VALUES ('Teknologi'), ('Sejarah');
INSERT INTO penerbit (nama_penerbit) VALUES ('Gramedia'), ('Erlangga'), ('Kompas');
### VI. Isi data buku (sesuaikan dengan kategori_id dan penerbit_id)
INSERT INTO buku (id_buku, judul, penulis, kategori_id, penerbit_id, tahun_terbit) VALUES
(1, 'Pemrograman Python', 'Budi Santoso', 1, 1, 2020),
(2, 'Belajar AI', 'Sari Wulandari', 1, 2, 2021),
(3, 'Sejarah Indonesia', 'Agus Santoso', 2, 3, 2018);
### VII. Isi data anggota
INSERT INTO anggota (nama_anggota, alamat_anggota) VALUES
('Ani', 'Jl. Melati No 5'),
('Budi', 'Jl. Mawar No 10');
## 4. Ssimulasi peminjaman buku 
INSERT INTO peminjaman (id_anggota, id_buku, tanggal_pinjam, tanggal_kembali) VALUES
(1, 1, '2023-09-01', '2023-09-10'),
(2, 2, '2023-09-03', '2023-09-12'),
(1, 3, '2023-09-05', '2023-09-15');
## 5. Verifikasi 
SELECT a.nama_anggota, b.judul, p.tanggal_pinjam, p.tanggal_kembali
FROM peminjaman p
JOIN anggota a ON p.id_anggota = a.id_anggota
JOIN buku b ON p.id_buku = b.id_buku;


> Foto penulis di seminar sebagai syarat absen 
![absen](/session%203/img/buat%20absen.jpeg)
