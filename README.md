# 1. Membuat database latihan1

Dalam studi kasus Data Barang, mahasiswa diminta membuat sebuah database baru dengan nama latihan1 menggunakan perintah:
```
CREATE DATABASE latihan1;
```

Pembuatan database ini merupakan langkah konseptual untuk memisahkan dan mengorganisasi data ke dalam satu ruang logis tersendiri. Dengan adanya database `latihan1`, seluruh objek data seperti tabel dan relasinya akan terkelola dalam satu skema yang terpisah dari database lain, sehingga memudahkan pemeliharaan dan mencegah konflik data.

# 2. Membuat tabel data_barang
<img width="1077" height="200" alt="image" src="https://github.com/user-attachments/assets/f33a4fbb-59e8-4f2b-bfc6-6339ddf901ab" />
Setelah database dibuat, mahasiswa diminta mendefinisikan struktur penyimpanan data dengan membuat tabel `data_barang`. Tabel ini memiliki sejumlah kolom, antara lain id_barang (sebagai primary key dan auto_increment), kategori, nama, gambar, harga_beli, harga_jual, dan stok. 
Secara akademik, langkah ini menanamkan pemahaman mengenai perancangan skema database:

  1. id_barang digunakan untuk mengidentifikasi setiap baris data secara unik.
  2. Kolom bertipe varchar menyimpan data teks seperti nama dan kategori.
  3. Kolom bertipe decimal digunakan untuk nilai moneter agar perhitungan keuangan presisi.
  4. Kolom stok bertipe integer untuk merepresentasikan jumlah persediaan barang.

Dengan demikian, mahasiswa tidak hanya menyalin perintah, tetapi juga memahami fungsi dan tipe data yang tepat untuk setiap atribut.
