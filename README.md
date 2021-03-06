# JARKOM20_modul1_C07

Laporan Resmi Praktikum Modul 1 Jaringan Komputer 2020

Kelompok C07 (0099 &amp; 0157)

# Pembahasan Jawaban

### No 1 Sebutkan webserver yang digunakan pada "testing.mekanis.me"!

`http.host contains "testing.mekanis.me" lalu follow tcp stream`

Artinya menampilkan semua paket dengan protokol http baik menuju ke atau berasal dari host yang mengandung string testing.mekanis.me.

![alt text](https://github.com/marsellaeve/JARKOM20_modul1_C07/blob/main/img/1.png)

### No 2 Simpan gambar "Tim_Kunjungan_Kerja_BAKN_DPR_RI_ke_Sukabumi141436.jpg"!

`File -> export object -> http ->filter->Tim_Kunjungan_Kerja_BAKN_DPR_RI_ke_Sukabumi141436.jpg`

merupakan cara untuk melakukan export data hasil paket capture.

`http contains Tim_Kunjungan_Kerja_BAKN_DPR_RI_ke_Sukabumi141436.jpg`

Artinya menampilkan semua paket dengan protokol http yang mengandung string "Tim_Kunjungan_Kerja_BAKN_DPR_RI_ke_Sukabumi141436.jpg" dan untuk mengecek keberadaan file  "Tim_Kunjungan_Kerja_BAKN_DPR_RI_ke_Sukabumi141436.jpg".

![alt text](https://github.com/marsellaeve/JARKOM20_modul1_C07/blob/main/img/2.png)

![alt text](https://github.com/marsellaeve/JARKOM20_modul1_C07/blob/main/img/2b.png)

### No 3 Cari username dan password ketika login di "ppid.dpr.go.id"!

`http.host contains "ppid.dpr.go.id" && http.request.method == POST`

Artinya menampilkan semua paket dengan protokol http baik menuju ke atau berasal dari host yang mengandung string "ppid.dpr.go.id" dan  memiliki method "POST".

![alt text](https://github.com/marsellaeve/JARKOM20_modul1_C07/blob/main/img/3.png)

### No 4 Temukan paket dari web-web yang menggunakan basic authentication method!

`Http.authbasic`

Artinya menampilkan semua paket dengan protokol http yang menggunakan basic authentication method.

![alt text](https://github.com/marsellaeve/JARKOM20_modul1_C07/blob/main/img/4.png)

### No 5 Ikuti perintah di aku.pengen.pw! Username dan password bisa didapatkan dari file .pcapng!

`http.authbasic && http.host contains aku.pengen.pw`

Artinya menampilkan semua paket dengan protokol http yang menggunakan basic authentication method dan menuju ke atau berasal dari host yang mengandung string "aku.pengen.pw".

![alt text](https://github.com/marsellaeve/JARKOM20_modul1_C07/blob/main/img/5a.png)

![alt text](https://github.com/marsellaeve/JARKOM20_modul1_C07/blob/main/img/5b.png)

### No 6 Seseorang menyimpan file zip melalui FTP dengan nama "Answer.zip". Simpan dan Buka file "Open This.pdf" di Answer.zip. Untuk mendapatkan password zipnya, temukan dalam file zipkey.txt (passwordnya adalah isi dari file txt tersebut).

`ftp-data.command=="STOR Answer.zip"`

Artinya menampilkan semua paket dengan protokol ftp yang dalam datanya mengandung command "STOR Answer.zip", ambil paket yang response untuk melakukan export file raw (karena datanya diberikan disini). Untuk STOR sendiri fungsinya untuk mengupload file ke FTP Server.

Cara export file raw :

Klik data yang diinginkan -> klik kanan -> TCP Stream -> ganti ascii menjadi raw -> save as dengan ekstensi sesuai bentuk file

![alt text](https://github.com/marsellaeve/JARKOM20_modul1_C07/blob/main/img/6a.png)

`ftp-data.command=="STOR zipkey.txt"`

Artinya menampilkan semua paket dengan protokol ftp yang dalam datanya mengandung command "STOR zipkey.txt". Setelah dibuka, copy isi data dan dijadikan password untuk extract file zip yang telah diextract sebelumnya.

![alt text](https://github.com/marsellaeve/JARKOM20_modul1_C07/blob/main/img/6b.png)

Isi "Open This.pdf":

![alt text](https://github.com/marsellaeve/JARKOM20_modul1_C07/blob/main/img/6c.png)

### No 7 Ada 500 file zip yang disimpan ke FTP Server dengan nama 1.zip, 2.zip, ..., 500.zip. Salah satunya berisi pdf yang berisi puisi. Simpan dan Buka file pdf tersebut. Your Super Mega Ultra Rare Hint = nama pdf-nya "Yes.pdf"

`frame contains "Yes.pdf"`

Artinya menampilkan semua paket dengan frame yang mengandung string "Yes.pdf". Kemudian extract pdf dengan TCP Stream, Ascii code diganti dengan raw. Save as dengan nama Yes.pdf.

![alt text](https://github.com/marsellaeve/JARKOM20_modul1_C07/blob/main/img/7a.png)

Isi Yes.pdf:

![alt text](https://github.com/marsellaeve/JARKOM20_modul1_C07/blob/main/img/7b.png)

### No 8 Cari objek apa saja yang didownload (RETR) dari koneksi FTP dengan Microsoft FTP Service!

`ftp.request.command=="RETR"`

Artinya menampilkan semua paket dengan protokol ftp yang melakukan request yang mengandung command "RETR". RETR sendiri digunakan untuk mendownload suatu file dari FTP Server. Setelah itu, terdapat 2 file yang didownload yaitu readme dan license.txt.

![alt text](https://github.com/marsellaeve/JARKOM20_modul1_C07/blob/main/img/8a.png)

Untuk melihat file yang didownload dari koneksi FTP dengan Microsoft FTP Service, yaitu dengan klik kanan pada file -> TCP Stream. Kemudian lihat pada baris pertama.

Isi TCP Stream dari file Readme:

![alt text](https://github.com/marsellaeve/JARKOM20_modul1_C07/blob/main/img/8b.png)

Isi TCP Stream dari license.txt:

![alt text](https://github.com/marsellaeve/JARKOM20_modul1_C07/blob/main/img/8c.png)

Karena Follow -> TCP Stream melihatkan Microsoft FTP Service pada RETR Readme maka objek yang didownload (RETR) dari koneksi FTP dengan Microsoft FTP Service adalah Readme

### No 9 Cari username dan password ketika login FTP pada localhost!

`ftp.request.command=="PASS"`

Artinya menampilkan semua paket dengan protokol ftp yang melakukan request yang mengandung command "PASS". PASS digunakan untuk authentication password. Kemudian dapat dilihat password yang direquest adalah dhana123.

![alt text](https://github.com/marsellaeve/JARKOM20_modul1_C07/blob/main/img/9a.png)

`ftp.request.command=="USER"`

Artinya menampilkan semua paket dengan protokol ftp yang melakukan request yang mengandung command "USER". USER digunakan untuk authentication username. Kemudian dapat dilihat username yang direquest adalah dhana.

![alt text](https://github.com/marsellaeve/JARKOM20_modul1_C07/blob/main/img/9b.png)

### No 10 Cari file .pdf di wireshark lalu download dan buka file tersebut! clue: "25 50 44 46"

`frame contains "application/pdf"`

Artinya menampilkan semua paket dengan frame yang berbentuk pdf.

Kemudian ctrl+f -> ubah menjadi find by hex code -> ketik hex code 25504446 -> extract pdf dengan TCP Stream -> Ascii code diganti dengan raw -> Save as dengan nama Yes.pdf.

![alt text](https://github.com/marsellaeve/JARKOM20_modul1_C07/blob/main/img/10a.png)

Potongan isi dari file .pdf dengan hex code 25504446 sebagai berikut:

![alt text](https://github.com/marsellaeve/JARKOM20_modul1_C07/blob/main/img/10b.png)

### No 11 Filter sehingga wireshark hanya mengambil paket yang mengandung port 21!

`port 21`

Port 21 artinya menampilkan semua paket yang spesifik menuju ke atau berasal dari port 21.

![alt text](https://github.com/marsellaeve/JARKOM20_modul1_C07/blob/main/img/11.png)

### No 12 Filter sehingga wireshark hanya mengambil paket yang berasal dari port 80!

`Src port 80`

Src port 80 artinya menampilkan semua paket yang spesifik berasal dari port 80.

![alt text](https://github.com/marsellaeve/JARKOM20_modul1_C07/blob/main/img/12.png)

### No 13 Filter sehingga wireshark hanya menampilkan paket yang menuju port 443!

`dst port 443`

dst port 443 artinya menampilkan semua paket yang spesifik menuju ke port 443.

![alt text](https://github.com/marsellaeve/JARKOM20_modul1_C07/blob/main/img/13.png)

### No 14 Filter sehingga wireshark hanya mengambil paket yang berasal dari ip kalian!

Ip addr: 192.168.0.9

Pertama cari terlebih dahulu ip addr masing-masing dengan buka cmd -> ipconfig

![alt text](https://github.com/marsellaeve/JARKOM20_modul1_C07/blob/main/img/14a.png)

`Src net 192.168.0.9`

Menangkap semua paket yang berasal dari subnet 192.168.0.9

![alt text](https://github.com/marsellaeve/JARKOM20_modul1_C07/blob/main/img/14b.png)

### No 15 Filter sehingga wireshark hanya mengambil paket yang tujuannya ke monta.if.its.ac.id!

`dst "monta.if.its.ac.id"`

dst "monta.if.its.ac.id" artinya menampilkan semua paket yang spesifik menuju ke monta.if.its.ac.id.

![alt text](https://github.com/marsellaeve/JARKOM20_modul1_C07/blob/main/img/15.png)


## Authors

Created by:

[Evelyn Tjitrodjojo 99](https://github.com/marsellaeve)

[Naufal Rafi Akbar Harahap 157](https://github.com/NaufalRafi-hub)
