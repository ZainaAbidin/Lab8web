# 1. Membuat database latihan1

Dalam studi kasus Data Barang, mahasiswa diminta membuat sebuah database baru dengan nama latihan1 menggunakan perintah:
```
CREATE DATABASE latihan1;
```

Pembuatan database ini merupakan langkah konseptual untuk memisahkan dan mengorganisasi data ke dalam satu ruang logis tersendiri. Dengan adanya database `latihan1`, seluruh objek data seperti tabel dan relasinya akan terkelola dalam satu skema yang terpisah dari database lain, sehingga memudahkan pemeliharaan dan mencegah konflik data.

# 2. Membuat tabel data_barang
Setelah database dibuat, mahasiswa diminta mendefinisikan struktur penyimpanan data dengan membuat tabel `data_barang`. Tabel ini memiliki sejumlah kolom, antara lain id_barang (sebagai primary key dan auto_increment), kategori, nama, gambar, harga_beli, harga_jual, dan stok. 
Secara akademik, langkah ini menanamkan pemahaman mengenai perancangan skema database:

  1. id_barang digunakan untuk mengidentifikasi setiap baris data secara unik.
  2. Kolom bertipe varchar menyimpan data teks seperti nama dan kategori.
  3. Kolom bertipe decimal digunakan untuk nilai moneter agar perhitungan keuangan presisi.
  4. Kolom stok bertipe integer untuk merepresentasikan jumlah persediaan barang.

Dengan demikian, mahasiswa tidak hanya menyalin perintah, tetapi juga memahami fungsi dan tipe data yang tepat untuk setiap atribut.

# 3. Menambahkan data awal ke tabel
<img width="1007" height="164" alt="image" src="https://github.com/user-attachments/assets/d1b9d192-797b-4e01-b892-6e8dc04d1bd5" />

Langkah selanjutnya adalah mengisi tabel `data_barang` dengan beberapa data awal menggunakan perintah `INSERT INTO`. Praktikum memberikan contoh tiga baris data yang mewakili beberapa merek telepon seluler Android, lengkap dengan kategori, nama, nama berkas gambar, harga beli, harga jual, dan stok. 

Tujuannya adalah agar mahasiswa dapat mengamati hasil operasi Create dalam konteks `CRUD` secara langsung. Data awal ini akan menjadi bahan uji saat membuat fitur Read, Update, dan Delete pada aplikasi PHP yang dibangun. Selain itu, mahasiswa belajar mengelola data berbentuk batch insert untuk menghemat waktu dan mengefisiensikan proses pengisian database.

# 4. Membuat folder proyek dan mengaksesnya melalui browser
Praktikum kemudian menginstruksikan pembuatan folder lab8_php_database di dalam `htdocs`, dan mengaksesnya melalui URL `http://localhost/lab8_php_database/`. 
Langkah ini memperkenalkan hubungan antara struktur direktori di sisi server dan URL di sisi klien. Dengan mengakses folder tersebut melalui browser, mahasiswa memahami bahwa setiap berkas PHP/HTML di dalamnya dapat dipanggil sebagai bagian dari aplikasi web, selama berada di bawah kontrol web server Apache.

# 5. Membuat berkas koneksi.php (konfigurasi koneksi database)
<img width="1920" height="1080" alt="Screenshot (127)" src="https://github.com/user-attachments/assets/7d76317f-37b0-43b9-9b88-0be053d26f35" />

Berkas `koneksi.php` dibuat untuk menyimpan konfigurasi koneksi ke database, mencakup nama host `(localhost)`, nama pengguna `(root)`, kata sandi `(kosong)`, dan nama database `(latihan1)`. Di dalamnya digunakan fungsi `mysqli_connect()` untuk membuka koneksi dan blok pengecekan guna memastikan koneksi berhasil atau gagal. 
Secara akademik, langkah ini menunjukkan prinsip pemisahan tanggung jawab (separation of concerns) dalam pemrograman: logika koneksi database ditempatkan dalam satu berkas yang dapat di-include oleh berkas lain. Hal ini meningkatkan keteraturan kode, memudahkan pemeliharaan, dan mengurangi duplikasi konfigurasi.

# 6. Membuat index.php sebagai tampilan Read data
<img width="1920" height="1080" alt="Screenshot (128)" src="https://github.com/user-attachments/assets/721edf89-1e46-4b54-a105-3dac3716ea2e" />

Berkas index.php berfungsi sebagai halaman utama yang menampilkan seluruh data dari tabel data_barang. File ini meng-include koneksi.php, menjalankan perintah `SELECT * FROM data_barang`, lalu menampilkan hasilnya dalam bentuk tabel HTML lengkap dengan kolom gambar, nama barang, kategori, harga, stok, dan aksi. 
Langkah ini merealisasikan operasi Read pada konsep CRUD. Di sini mahasiswa belajar:
  1. Mengirim query ke MySQL menggunakan `mysqli_query()`.
  2. Mengambil hasil query baris demi baris dengan `mysqli_fetch_array()`.
  3. Mengintegrasikan data dinamis ke dalam struktur HTML menggunakan sintaks PHP singkat `(<?= ... ?>)`.

# 7. Membuat tambah.php untuk operasi Create
<img width="1920" height="1080" alt="Screenshot (129)" src="https://github.com/user-attachments/assets/5867069d-aca3-4d83-91c4-b1eb19af5c0f" />

Berkas tambah.php dibangun untuk mengimplementasikan operasi Create, yaitu menambahkan data baru ke tabel data_barang. Pada bagian atas skrip, dilakukan pembacaan data dari formulir `($_POST)` serta pengelolaan berkas gambar yang diunggah melalui `$_FILES`. Jika proses unggah berhasil, path gambar disimpan ke dalam kolom gambar. Selanjutnya, dijalankan perintah `INSERT INTO` untuk memasukkan data baru ke database, dan pengguna diarahkan kembali ke index.php setelah proses selesai. 
Dari sudut pandang akademik, langkah ini mengajarkan beberapa konsep penting:
  1. Validasi dan pemrosesan input form di sisi server.
  2. Penanganan upload berkas dan penyimpanan path berkas, bukan file itu sendiri, di database.
  3. Penerapan prinsip `post/redirect/get`, di mana setelah proses penyimpanan, pengguna diarahkan kembali ke halaman lain untuk mencegah pengulangan pengiriman data saat halaman di-refresh.

# 8. Membuat ubah.php untuk operasi Update
<img width="1920" height="1080" alt="Screenshot (130)" src="https://github.com/user-attachments/assets/75a89ab9-0491-46fb-9768-bf93dad2c9de" />

Langkah berikutnya adalah pembuatan berkas ubah.php yang menangani operasi Update terhadap data yang sudah ada. Skrip ini memiliki dua peran:
  1. Ketika dipanggil dengan parameter id melalui `$_GET, skrip` mengambil data barang yang bersangkutan dan menampilkannya dalam formulir sehingga dapat diedit.
  2. Ketika formulir disubmit, skrip membaca data baru dari `$_POST`, menangani kemungkinan unggah gambar baru, lalu menjalankan perintah UPDATE data_barang `SET ... WHERE id_barang = ....` 

Melalui langkah ini, mahasiswa memahami bagaimana data eksisting dapat dimodifikasi secara selektif. Penggunaan fungsi pembantu `is_select()` juga memperlihatkan cara mempertahankan nilai pilihan pada elemen`<select>` agar sesuai dengan kategori yang tersimpan di database. Di samping itu, mahasiswa belajar membedakan alur logika antara permintaan GET (menampilkan form) dan POST (memproses perubahan data).

# 9. Membuat hapus.php untuk operasi Delete
<img width="1920" height="1080" alt="Screenshot (134)" src="https://github.com/user-attachments/assets/6871ac99-f765-4685-913c-28b99a8ee7c8" />

Untuk melengkapi implementasi CRUD, praktikum mengarahkan pembuatan berkas hapus.php. Berkas ini menerima parameter `id melalui $_GET`, lalu menjalankan perintah:
```
DELETE FROM data_barang WHERE id_barang = '{$id}'
```
Setelah eksekusi, pengguna diarahkan kembali ke index.php. 
Langkah ini menegaskan pemahaman mengenai operasi Delete, yaitu penghapusan baris data secara permanen dari tabel. Mahasiswa diajak menyadari pentingnya kehati-hatian pada operasi ini karena bersifat irreversible, serta pentingnya memastikan bahwa `id` yang diterima benar-benar mengacu pada data yang dimaksud.
