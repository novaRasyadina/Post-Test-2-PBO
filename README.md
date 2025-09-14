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

**# Penjelasan Alur Program #**

<img width="767" height="162" alt="image" src="https://github.com/user-attachments/assets/a9f87123-20b5-44ea-8f3b-346228d6963d" />

Class PreOrder dideklarasikan sebagai public agar dapat diakses dari package lain. Di dalamnya terdapat empat atribut private yaitu id, namaPelanggan, jenisKain, dan jumlah. Modifier private memastikan bahwa atribut ini tidak bisa diakses secara langsung dari luar class sehingga menjaga prinsip enkapsulasi. Atribut id digunakan sebagai identitas unik setiap pesanan, namaPelanggan menyimpan nama pelanggan yang melakukan pre-order, jenisKain menyimpan jenis kain songket yang dipesan, dan jumlah menyimpan banyaknya kain yang dipesan.

<img width="968" height="158" alt="image" src="https://github.com/user-attachments/assets/3122b656-898d-4e20-86ca-c87bbfe9d8cb" />

Constructor ini dipakai untuk membuat objek baru PreOrder. Setiap kali objek dibuat, nilai id, namaPelanggan, jenisKain, dan jumlah diinisialisasi sesuai input. Kata kunci this digunakan untuk membedakan antara atribut class dan parameter constructor yang memiliki nama sama.

<img width="788" height="640" alt="image" src="https://github.com/user-attachments/assets/8446bd9a-14cb-43ce-87e2-b923d8578950" />
<img width="802" height="119" alt="image" src="https://github.com/user-attachments/assets/04103e08-94a2-40c0-abb2-fe341f2e8585" />

getter digunakan untuk membaca nilai dari atribut. misalnya getNamaPelanggan() mengembalikan nilai namaPelanggan sehingga class lain, misalnya PreOrderService, dapat menampilkan atau memproses data pelanggan tanpa mengakses atribut langsung.
sedangkan setter digunaiakn untuk mengubah nilai pada atribut. misalnya ketika user melakukan update pre-order, method setJumlah() dapat dipanggil untuk emgganti jumlah kain sesuai input baru.

Selanjutnya adalah package servive dengan Class PreOrderService

<img width="412" height="81" alt="image" src="https://github.com/user-attachments/assets/ffafa39a-6bf0-488b-bf62-c00b8e79a690" />

kode di atas yaitu class PreOrderService mengimpor PreOrder dari package model sehingga dapat membuat dan memanipulasi objek pre-order. ArrayList digunakan untuk menyimpan semua pre-order sementara di memory dan Scanner digunakan untuk membaca input.

<img width="909" height="118" alt="image" src="https://github.com/user-attachments/assets/3e358b0a-9823-4064-97f8-2c981bc7f73a" />

di sini dibuat list listPreOrder untuk menyimpan semua data, nextId untuk memberikan ID unik setiap pre-order baru, dan objek scanner untuk membaca input dari user. setiap operasi CRUD nanti memanipulasi list ini.

<img width="872" height="647" alt="image" src="https://github.com/user-attachments/assets/a6461a8a-b27d-4cfe-8378-feb1b790d0ae" />
<img width="860" height="204" alt="image" src="https://github.com/user-attachments/assets/efcfa7e6-3ec4-4597-97b2-23336396ec5f" />

method tambahPreOrder() meminta input nama pelanggan, jenis kain, dan jumlah. validasi dilakukan untuk memastikan nama dan jenis kain tidak kosong, serta jumlah merupakan angka lebih besar dari nol dan harsu berupa angka. Jika input valid, dibuat objek PreOrder baru dengan ID otomatis dan dimasukkan ke list. 

<img width="796" height="257" alt="image" src="https://github.com/user-attachments/assets/36792ae0-801a-4606-990b-256626ea16db" />

Method tampilkanPreOrder() menampilkan semua pre-order. Jika list kosong, method berhenti. Jika ada data, looping setiap objek dan mencetak atributnya. Alurnya membaca data dari model dan menampilkannya ke terminal atau output.

<img width="1054" height="749" alt="image" src="https://github.com/user-attachments/assets/ae0f4fec-d3ac-4b80-9099-10e143d36c2c" />

Method updatePreOrder() meminta ID pre-order yang akan diperbarui. Objek ditemukan dengan findById(). jika objek ada, user dapat mengubah nama, jenis kain, atau jumlah. Input kosong berarti field tidak berubah. program membaca input dari user menggunakan scanner.nextLine() dan mencoba mengubah input menjadi integer menggunakan Integer.parseInt(). Jika input berupa angka dan lebih besar dari 0, maka method setJumlah(jumlah) dipanggil untuk memperbarui atribut jumlah dari objek PreOrder. Jika user memasukkan sesuatu yang bukan angka, misalnya huruf atau simbol, maka Integer.parseInt() akan memunculkan exception NumberFormatException. Exception ini ditangani oleh blok catch, sehingga program tidak crash. Dalam blok catch, ditampilkan pesan ke user bahwa jumlah tidak valid dan data lama tetap digunakan.

<img width="846" height="324" alt="image" src="https://github.com/user-attachments/assets/1f31774a-da0c-4fcc-9453-15681ba82a44" />

Method hapusPreOrder() meminta ID, mencari objek di list, dan menghapusnya jika ditemukan.

<img width="944" height="418" alt="image" src="https://github.com/user-attachments/assets/c0a39e1f-3bcb-49a0-83a7-05f7df227fa4" />

Method cariPreOrder() dideklarasikan public agar bisa dipanggil dari package lain, misalnya dari class MainApp. Method ini tidak mengembalikan nilai (void) karena tujuannya adalah menampilkan hasil pencarian langsung kr console. menampilkan pesan ke user untuk memasukkan nama pelanggan yang ingin dicari. Input dibaca menggunakan scanner.nextLine(). Method toLowerCase() diterapkan agar pencarian tidak sensitif terhadap huruf kapital atau kecil, sehingga misalnya input Nova dan nova tetap bisa cocok.
kemudian ada Looping yang menelusuri semua objek PreOrder di list listPreOrder. Untuk setiap objek, program mengambil nama pelanggan menggunakan po.getNamaPelanggan(), mengubahnya ke huruf kecil dengan toLowerCase(), lalu mengecek apakah mengandung keyword yang dimasukkan user dengan method contains(). Jika ada yang cocok, objek po dicetak ke console dan variabel ditemukan diubah menjadi true.
Setelah semua data diperiksa, jika tidak ada satu pun yang cocok (ditemukan tetap false), program menampilkan pesan bahwa tidak ada data yang sesuai.

<img width="661" height="278" alt="image" src="https://github.com/user-attachments/assets/7c9a8f2d-1c11-4a81-a6ac-b23fcc1149e3" />

mtthod cariById(int id) bersifat private karena hanya dipakai dalam class PreOrderService, misalnya untuk update atau delete. method ini menerima parameter id dan melakukan looping semua objek PreOrder di list. Jika ditemukan objek dengan po.getId() == id, objek tersebut dikembalikan (return po).

<img width="593" height="100" alt="image" src="https://github.com/user-attachments/assets/6401d66d-2cc8-4530-a8a4-2c5d0d22c842" />

kode di atas menandakan lass MainApp berada dalam package Main. Dengan ini, package lain harus melakukan import untuk bisa mengakses MainApp. Package Main berfungsi sebagai View dalam arsitektur MVC, tempat menampilkan menu dan menerima input user.
kemudian impor class Scanner dari java.util untuk membaca input dari consol, lalu PreOrderService dari package Service agar bisa memanggil semua method CRUD dan search yang sudah didefinisikan sebelumnya.

<img width="865" height="157" alt="image" src="https://github.com/user-attachments/assets/1bdc9944-4543-410d-a651-f8908252bcde" />

Class MainApp dideklarasikan public agar bisa diakses dari luar package, dan method main adalah titik awal program dijalankan oleh Java. Semua alur program dimulai dari sini. kemudian dibuat objek scanner untuk membaca input dari user, dan objek service dari PreOrderService untuk memanggil semua method CRUD dan search. Jadi setiap input dari user nanti diteruskan ke service untuk diproses sesuai fungsinya Variabel pilihan digunakan untuk menyimpan angka yang dimasukkan user untuk memilih menu. ini menjadi kontrol alur program, apakah user ingin menambah, menampilkan, mengubah, menghapus, mencari data, atau keluar.

<img width="844" height="284" alt="image" src="https://github.com/user-attachments/assets/d67a70d9-ea50-43d6-ac67-38426e76c5be" />

kode di atas adalah bagian menu utama ditampilkan ke user. setiap opsi menu diarahkan untuk menjalankan method tertentu di service. User bisa melihat pilihan dan menentukan operasi yang ingin dilakukan.

<img width="795" height="157" alt="image" src="https://github.com/user-attachments/assets/2f27f424-9174-442d-964f-b05ef4776a28" />

pada bagian ini user atau pelanggan diminta untuk memasukan angka untuk memilih menu. jika user salah memasukan input bukan angka, program menangkap error dan menampilkan pesan error kepada penlanggan.

<img width="966" height="345" alt="image" src="https://github.com/user-attachments/assets/62be414e-b436-411c-a9c9-c5396df6d3e1" />

bagian kode ini adalah pengendali menu utama. Switch case mengecek pilihan user dan memanggil method yang sesuai di PreOrderService untuk menambah, menampilkan, mengubah, menghapus, atau mencari pre-order. pilihan 6 menghentikan program, sedangkan input yang tidak valid akan menampilkan pesan error. loop do-while membuat menu terus muncul sampai user memilih keluar, dan scanner.close() menutup input setelah program selesai.

<img width="635" height="305" alt="image" src="https://github.com/user-attachments/assets/f7191318-75e3-4133-bca6-9eca3cbeae88" />

Pengguna diminta untuk memasukan nomor menu yang ingin dituju, pada gambar di atas pengguna memilih menu nomor 1 yaitu membuat pesanan pre order, kemudian pengguna diminta memasukan nama, jenis kain, dan jumlah. 

<img width="859" height="242" alt="image" src="https://github.com/user-attachments/assets/43de551e-05bc-43f5-933f-887b3e1c44ab" />

Apabila pengguna memasukan angka 2, maka informasi pemesanan akan ditampilkan

<img width="893" height="336" alt="image" src="https://github.com/user-attachments/assets/1db3d3c4-ad8e-436f-99d1-02efb643601a" />

jika pengguna memasukan angka 3, pengguna dapat mengupdate pemesanan, dengan syarat pengguna tidak dapat memasukan angka 0. apabila pengguna measukan angka nol, maka informasi pemesnan tidak akan berubah.

<img width="792" height="229" alt="image" src="https://github.com/user-attachments/assets/847ada96-c35c-4286-8617-8c2cc947897b" />

pengguna atau pelanggan dapat melakukan pengecekan kembali dengan menginput angka 2 untuk melihat pesanan yang sudah di ubah.

<img width="840" height="267" alt="image" src="https://github.com/user-attachments/assets/6c44dd02-3117-4c5c-9219-5ffc977a94de" />

fitur ini memungkinkan pengguna untuk melakukan pencarian produk.

<img width="669" height="509" alt="image" src="https://github.com/user-attachments/assets/906a1515-28cb-434c-b6c3-f301db74def0" />

pengguna juga dapat menghapus pre-order dengan memasukan angka 4, apabila sudah memasukan angka 4, maka akan muncul pesan "Data Berhasil Dihapus". setelahnya pengguna dapat mengecek kembali dengan input angka 2 dan menampilkan tidak terdapat data pre-order karena data telah berhasil dihapus.

<img width="861" height="303" alt="image" src="https://github.com/user-attachments/assets/8c9569a8-28c4-4cf8-a2f1-163d9291095a" />

Fitur terakhir dari program ini adalah menu keluar dari program pemesanan dengan menginput angka nomnor 6. akan muncul pesan "Terima Kasih Telah Berkunjung -_-!"
