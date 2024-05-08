# Tugas-teori-1-Pemograman-Jaringan

Nama: Anggita Rachmadinda Putri

Kelas: IF 02 - 01

NIM: 1203220086

## Soal
1. Membuat sebuah program server yang dapat menerima koneksi dari klien menggunakan protokol TCP. Server ini akan menerima pesan dari klien dan mengirimkan pesan balasan berisi jumlah karakter pada pesan tersebut. Gunakan port 12345 untuk server. Membuat analisa dari hasil program tersebut 

**Source Code:**

Bagian ini untuk menginisialisasi server menggunakan protokol TCP/IP. Pernyataan import socket mengimpor modul socket, yang menyediakan fungsi-fungsi untuk berkomunikasi melalui jaringan. Dengan menggunakan socket.socket(socket.AF_INET, socket.SOCK_STREAM), kita membuat objek socket yang menggunakan alamat IPv4 (socket.AF_INET) dan protokol TCP (socket.SOCK_STREAM). Langkah selanjutnya adalah mengikat socket ke alamat dan port tertentu menggunakan server_socket.bind(('localhost', 12345)). Di sini, localhost merujuk pada komputer tempat server berjalan dan 12345 adalah nomor port yang dipilih untuk server. Dengan server_socket.listen(5), server diinstruksikan untuk mendengarkan koneksi masuk. Argumen 5 menunjukkan bahwa server akan menerima hingga lima koneksi masuk yang tertunda. Pesan "Server telah siap menerima koneksi..." dicetak untuk memberi tahu operator server bahwa server telah dimulai dan siap menerima koneksi. Dengan langkah-langkah ini, server siap untuk menerima koneksi dari klien dan menanggapi pesan yang diterima.
```sh
import socket

def main():
    # Inisialisasi socket TCP/IP
    server_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)

    # Bind socket ke alamat dan port tertentu
    server_socket.bind(('localhost', 12345))

    # Listen untuk koneksi masuk
    server_socket.listen(5)

    print("Server telah siap menerima koneksi...")
```

Bagian ini untuk menjalankan server dalam loop tak terbatas (while True). Setiap iterasi dari loop ini, server akan menunggu dan menerima koneksi dari klien yang ingin berkomunikasi. Ketika koneksi diterima, server akan mencetak pesan yang memberitahu bahwa koneksi berhasil dibuat dengan klien dan mencantumkan alamat IP dan nomor port klien. Setelah koneksi terbentuk, server akan menerima pesan dari klien menggunakan metode recv() dengan ukuran buffer 1024 byte. Pesan yang diterima akan di-decode dari format byte menjadi string dan kemudian dicetak untuk keperluan pemantauan dan debugging. Selanjutnya, server akan menghitung jumlah karakter dalam pesan yang diterima menggunakan fungsi len(). Setelah jumlah karakter pesan dihitung, server akan mengirimkan balasan kepada klien. Balasan ini berisi jumlah karakter pesan yang telah dihitung, yang dikonversi menjadi string, kemudian diencode menjadi format byte menggunakan metode encode() sebelum dikirimkan ke klien. Setelah server mengirim balasan, koneksi dengan klien ditutup menggunakan metode close() untuk membersihkan sumber daya dan membebaskan port untuk koneksi berikutnya. Proses ini akan berulang terus-menerus, memungkinkan server untuk terus menerima koneksi dan menanggapi pesan dari klien.
```sh
    while True:
        # Terima koneksi dari klien
        client_socket, client_address = server_socket.accept()
        print(f"Terhubung dengan {client_address}")
        
        # Terima pesan dari klien
        message = client_socket.recv(1024).decode()
        print(f"Pesan dari klien: {message}")
        
        # Hitung jumlah karakter pesan
        num_chars = len(message)
        
        # Kirim balasan berupa jumlah karakter ke klien
        client_socket.send(str(num_chars).encode())
        
        # Tutup koneksi dengan klien
        client_socket.close()

if __name__ == "__main__":
    main()
```
## Output
Server
![reference image](/images/5.png)

2. Membuat sebuah program klien yang dapat terhubung ke server yang telah dibuat pada soal nomor 1. Klien ini akan mengirimkan pesan ke server berupa inputan dari pengguna dan menampilkan pesan balasan jumlah karakter yang diterima dari server. Membuat analisa dari hasil program tersebut
