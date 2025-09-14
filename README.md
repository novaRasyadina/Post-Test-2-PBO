# Post Test 2 PBO
# **Manajemen Pre-Order Kain Songket**
Program ini dibuat dengan aplikasi Java untuk mengelola data pre-order
kain songket. fitur yang tersedia meliputi menambah pesanan, melihat daftar pesanan, mengubah dan menghapus data. Sedangkan semua data disimpan dalam ArrayList. program ini berjalan berulang dan akan berakhir hingga pengguna memilih menu keluar. 

**# Penjelasan Package #**
<img width="611" height="241" alt="image" src="https://github.com/user-attachments/assets/13adfa79-ea82-48c9-91e2-0719c71431f4" />
Program ini dibuat dengan menggunakan struktur MVC (Model View Controller), yang mana setiap package memiliki peran tanggung jawab spesifik.
* package Model

  package ini berisi class PreOrder yang mendefinisikan strukturdaata
  pemesanan kain songket. di sini disimpan semua atribut yang diperlukan,
  yaitu id, nama pelanggan, jenis kain, dan jumlah. package Model beeperan
  sebagai Model dlam pola MVC, artinya bertanggung jawab hanya untukmenyimpan
  data, menyediakan constructor untuk membuat objek baru, serta getter dan
  setter untuk mengakses atau mengubah data. Tidak ada logika pemrosesan data
  di sini, sehingga menjaga pemisahan fungsi.
  
* Package Service

  Package ini berisi kelas PreOrderService, yang merupakan Controller dalam MVC. fungsi utamanya adalah mengolah logika CRUD yang antara lain menambah, menampilkan, memperbarui, menghapus, dan mencari data pre-order. di sini juga diterapkan validasi input, misalnya memastikan jumlah yang dimasukkan adalah angka lebih dari nol, dan memastikan nama serta jenis kain tidak kosong. semua metode CRUD memanipulasi data yang berasal dari ArrayList<PreOrder> yang berada di dalam kelas ini.
* package Main
  
  Pckage ini berisi class MainApp, yang berperan sebagai view dalam MVC. kelas ini menampilkan menu interaktif ke pengguna, menerima inpit pilihan menu, dan memanggil metode yang sesuai dari PreOrderService. semua interaksi langsung denganuser terjadi di sini, sedangkan pengolahan data, sehingga tetap menjaga pemisah tanggung jawab atau perannya.
