# Tugas-teori-1-Pemograman-Jaringan

1. 
   A. Server.py
  - Import Library: Mengimpor modul socket untuk menggunakan fungsi-fungsi socket dalam Python.
  - Fungsi hitung_jumlah_karakter: Fungsi ini menerima sebuah string dan mengembalikan jumlah karakternya dalam bentuk string.
  - Inisialisasi Socket Server: Membuat socket server menggunakan socket.socket() dengan parameter socket.AF_INET untuk menentukan domain     alamat (IPv4) dan socket.SOCK_STREAM untuk menentukan jenis socket (TCP).
  - Bind Socket: Mengikat (bind) socket ke alamat localhost dan port 12345 menggunakan metode bind().
  - Listen for Connections: Memulai mendengarkan (listen) koneksi masuk dengan metode listen(). Parameter 5 menentukan jumlah maksimum        koneksi yang diterima oleh server.
  - Loop untuk Menerima Koneksi: Server memasuki loop tak terbatas untuk terus menerima koneksi masuk dari client.
  - Terima Koneksi: Ketika ada koneksi masuk, server menerima koneksi dan mendapatkan objek socket baru untuk berinteraksi dengan client.     Fungsi accept() akan mengembalikan objek socket client dan alamat client.
  - Terima Pesan dari client: Server menerima pesan dari client menggunakan metode recv() dengan buffer size 1024. Pesan tersebut             kemudian di-decode dari byte menjadi string.
  - Proses Pesan: Jika pesan diterima dari client, server akan menghitung jumlah karakter pesan menggunakan fungsi hitung_jumlah_karakter.
  - Kirim Balasan: Server mengirim balasan berupa jumlah karakter pesan kembali ke client menggunakan metode send(). Sebelumnya, jumlah       karakter dikonversi menjadi string dan diencode ke dalam byte.
  - Tutup Koneksi: Setelah mengirim balasan, koneksi dengan client ditutup menggunakan metode close().
    
  B. client.py
  - Import Library: Mengimpor modul socket untuk menggunakan fungsi-fungsi socket dalam Python.
  - Inisialisasi Socket client: Membuat socket client menggunakan socket.socket() dengan parameter socket.AF_INET untuk menentukan domain     alamat (IPv4) dan socket.SOCK_STREAM untuk menentukan jenis socket (TCP).
  - Koneksi ke Server: client melakukan koneksi ke server dengan menggunakan metode connect() dengan alamat localhost dan port 12345.
  - Mengirim Pesan ke Server: client meminta pengguna untuk memasukkan pesan yang akan dikirim ke server, kemudian pesan tersebut dikirim     menggunakan metode send(). Pesan tersebut diencode menjadi byte sebelum dikirim.
  - Terima Balasan dari Server: client menerima balasan dari server menggunakan metode recv() dengan buffer size 1024. Balasan tersebut       kemudian di-decode dari byte menjadi string.
  - Tampilkan Balasan: Balasan dari server, yaitu jumlah karakter pesan, ditampilkan ke pengguna.
  - Tutup Koneksi: Setelah menerima balasan, koneksi dengan server ditutup menggunakan metode close().
    
2. 
  A. Client.py
  - Impor Modul Socket: Kode dimulai dengan mengimpor modul socket, yang merupakan modul bawaan Python yang menyediakan antarmuka untuk       fungsi socket.
  - Fungsi Utama (main): Ini adalah titik masuk utama program. Di dalamnya, koneksi ke server dibuat, pesan dikirim, balasan diterima,        dan kemudian koneksi ditutup.
  - Inisialisasi Socket Klien: Kode membuat objek socket klien dengan menggunakan socket.socket(socket.AF_INET, socket.SOCK_STREAM).
  - AF_INET menandakan bahwa kita akan menggunakan alamat IP versi 4, sedangkan SOCK_STREAM menandakan bahwa ini akan menjadi koneksi TCP.
  - Koneksi ke Server: Klien mencoba untuk terhubung ke server dengan memanggil client_socket.connect(server_address). server_address di      sini adalah tupel yang berisi alamat IP atau nama host server dan nomor port yang akan dikoneksikan (localhost dengan port 12345          dalam contoh ini).
  - Input Pesan: Klien meminta pengguna untuk memasukkan pesan yang akan dikirim ke server dengan menggunakan input().
  - Kirim Pesan ke Server: Pesan yang dimasukkan oleh pengguna dikirim ke server menggunakan client_socket.sendall(pesan.encode()). Pesan     dienkripsi terlebih dahulu ke dalam byte menggunakan encode() agar dapat dikirim melalui koneksi socket.
  - Terima Balasan dari Server: Klien menerima balasan dari server dengan menggunakan client_socket.recv(1024). Angka 1024 menunjukkan        jumlah byte maksimum yang akan diterima dalam satu kali panggilan. Setelah menerima, balasan tersebut di-decode menjadi string            menggunakan decode().
  - Tampilkan Balasan: Balasan dari server ditampilkan ke pengguna.
  - Tutup Koneksi: Koneksi socket ditutup dengan menggunakan client_socket.close().

  Penjelasan:
  Kode tersebut menginisialisasi sebuah koneksi TCP/IP sebagai klien dengan menggunakan modul socket bawaan Python. Setelah menetapkan      koneksi dengan server yang dituju, klien meminta pengguna untuk memasukkan pesan yang akan dikirim. Pesan tersebut dikirim ke server      melalui koneksi socket, kemudian klien menunggu balasan dari server. Setelah menerima balasan dari server, klien mendekode pesan          tersebut dari byte menjadi string dan mencetaknya ke layar. Akhirnya, koneksi socket ditutup untuk membersihkan sumber daya. Dengan       demikian, klien ini berfungsi sebagai antarmuka pengguna sederhana yang memfasilitasi komunikasi dua arah antara pengguna dan server.
