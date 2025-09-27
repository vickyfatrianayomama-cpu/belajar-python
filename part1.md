# Materi Python 3 - Bagian 1: Program Python Pertama Anda

Selamat datang di bab pertama perjalanan belajar Python! Di sini, kita akan belajar cara menulis program Python pertama Anda. Kita akan mulai dari dasar-dasar, seperti menjalankan kode di IDLE, membuat variabel, menangani error, dan menambahkan komentar. Semua langkah akan dijelaskan dengan sederhana dan mudah diikuti.

## 1. Menulis Script Python

Python bisa dijalankan di dua tempat utama di IDLE: **jendela interaktif** (interactive window) dan **jendela script** (script window). Mari kita pelajari cara kerjanya.

### Jendela Interaktif (Interactive Window)
- Ini adalah shell Python tempat Anda bisa mengetik kode satu baris per satu.
- Ketika Anda membuka IDLE, Anda akan melihat prompt `>>>` di bagian bawah.
- Coba ketik `1 + 1` dan tekan Enter. Python akan menampilkan hasil `2`.
- Ini disebut **REPL** (Read-Evaluate-Print Loop): Baca kode, Evaluasi, Cetak hasil, dan ulangi.

**Contoh sederhana:**
- Ketik: `print("Hello, world")`
- Tekan Enter, dan Anda akan melihat: `Hello, world`

Ini adalah program "Hello, world" pertama Anda! Fungsi `print()` digunakan untuk menampilkan teks ke layar.

### Jendela Script (Script Window)
- Untuk menulis program yang lebih panjang, gunakan jendela script.
- Buka dengan: File > New File.
- Ketik kode Anda di sini, tanpa prompt `>>>`.
- Simpan file dengan ekstensi `.py`, misalnya `hello_world.py`.
- Jalankan dengan: Run > Run Module (atau tekan F5).
- Output akan muncul di jendela interaktif.

**Langkah-langkah mudah:**
1. Buka IDLE.
2. Pilih File > New File.
3. Ketik: `print("Hello, world")`
4. Simpan sebagai `hello_world.py`.
5. Jalankan dengan F5.
6. Lihat hasil di jendela interaktif.

## 2. Mengalami Error (Mess Things Up)

Semua programmer pernah membuat kesalahan. Mari kita lihat jenis error yang umum dan cara memperbaikinya.

### Error Sintaks (Syntax Errors)
- Terjadi ketika kode Anda tidak sesuai aturan Python.
- Contoh: Hapus tanda kutip di akhir string.
  - Kode salah: `print("Hello, world)`
  - IDLE akan menampilkan pesan error: "EOL while scanning string literal."
- IDLE akan menyoroti baris yang bermasalah.

### Error Waktu Jalankan (Run-time Errors)
- Terjadi saat program sudah berjalan.
- Contoh: Hapus semua tanda kutip.
  - Kode salah: `print(Hello, world)`
  - Error: `NameError: name 'Hello' is not defined`
- Python akan menampilkan **traceback** yang menjelaskan di mana error terjadi.

**Tips:** Jangan takut error! Mereka membantu Anda belajar. Coba buat error sengaja untuk latihan.

## 3. Membuat Variabel

Variabel adalah nama yang menyimpan nilai. Ini membuat kode lebih mudah dibaca dan digunakan ulang.

### Operator Penugasan (=)
- Gunakan `=` untuk memberi nilai ke variabel.
- Contoh:
  ```
  phrase = "Hello, world"
  print(phrase)
  ```
  - Output: `Hello, world`

### Aturan Nama Variabel
- Hanya huruf (A-Z, a-z), angka (0-9), dan garis bawah (_).
- Tidak boleh dimulai dengan angka.
- Contoh valid: `phrase`, `string1`, `_a1p4a`, `list_of_names`.
- Contoh tidak valid: `9lives`.

### Tips Memilih Nama Variabel
- Gunakan nama deskriptif, bukan singkatan.
- Lebih baik: `seconds_per_hour = 3600` daripada `s = 3600`.
- Ikuti gaya **snake_case**: huruf kecil, kata dipisah garis bawah (sesuai PEP 8).

**Latihan:**
1. Buat variabel `nama = "Anda"`
2. Cetak dengan `print(nama)`

## 4. Memeriksa Nilai di Jendela Interaktif

Ada dua cara melihat nilai variabel:
- **Print:** `print(variabel)` - untuk tampilan manusiawi.
- **Inspect:** Ketik nama variabel saja dan tekan Enter - untuk info detail.

Contoh:
```
x = 2
y = "2"
print(x)  # Output: 2
print(y)  # Output: 2
x         # Output: 2
y         # Output: '2' (dengan kutip, menunjukkan string)
```

Inspect berguna untuk melihat tipe data.

## 5. Meninggalkan Catatan (Komentar)

Komentar membantu menjelaskan kode tanpa mempengaruhi jalannya program.

### Cara Menulis Komentar
- **Komentar blok:** Mulai baris dengan `#`.
  ```
  # Ini komentar
  phrase = "Hello, world"
  ```
- **Komentar inline:** Tambahkan `#` di akhir baris kode.
  ```
  print(phrase)  # Ini juga komentar
  ```

### Konvensi PEP 8
- Tulis dalam kalimat lengkap.
- Satu spasi setelah `#`.
- Untuk inline: Minimal dua spasi sebelum `#`.
- Jangan berlebihan: Hanya komentar yang menjelaskan "mengapa", bukan "apa".

**Contoh:**
```
# Hitung detik per jam
seconds_per_hour = 3600  # Nilai tetap
```

## Quiz Interaktif

Untuk menguji pemahaman Anda tentang materi ini, coba jawab pertanyaan-pertanyaan berikut. Jawaban dan penjelasan ada di bagian bawah. Coba kerjakan sendiri dulu sebelum melihat jawaban!

### Pertanyaan 1: Apa itu REPL?
a) Singkatan dari Read-Evaluate-Print Loop, cara Python menjalankan kode interaktif.  
b) Nama editor untuk Python.  
c) Fungsi untuk mencetak teks.

### Pertanyaan 2: Apa perbedaan antara jendela interaktif dan jendela script di IDLE?
a) Interaktif untuk kode satu baris, script untuk program lengkap.  
b) Script untuk debugging, interaktif untuk menjalankan.  
c) Tidak ada perbedaan.

### Pertanyaan 3: Jenis error apa yang terjadi jika Anda menulis `print("Hello, world)` (tanpa kutip akhir)?
a) Syntax error.  
b) Run-time error.  
c) Logic error.

### Pertanyaan 4: Aturan nama variabel yang benar adalah:
a) Boleh dimulai dengan angka.  
b) Hanya huruf, angka, dan garis bawah, tidak boleh dimulai dengan angka.  
c) Boleh menggunakan spasi.

### Pertanyaan 5: Cara menulis komentar inline yang benar sesuai PEP 8:
a) `print("Hello")#Ini komentar`  
b) `print("Hello")  # Ini komentar`  
c) `print("Hello")# Ini komentar`

### Pertanyaan 6 (Esai): Jelaskan mengapa kita menggunakan variabel dalam kode.

## Jawaban Quiz

### Jawaban 1: a) Singkatan dari Read-Evaluate-Print Loop, cara Python menjalankan kode interaktif.
**Penjelasan:** REPL adalah siklus baca-evaluasi-cetak yang membuat jendela interaktif berguna untuk eksperimen cepat.

### Jawaban 2: a) Interaktif untuk kode satu baris, script untuk program lengkap.
**Penjelasan:** Jendela interaktif cocok untuk testing kecil, sedangkan script untuk menyimpan dan menjalankan program besar.

### Jawaban 3: a) Syntax error.
**Penjelasan:** Syntax error terjadi sebelum program berjalan, karena kode tidak sesuai aturan Python (string tidak lengkap).

### Jawaban 4: b) Hanya huruf, angka, dan garis bawah, tidak boleh dimulai dengan angka.
**Penjelasan:** Nama variabel harus valid agar Python mengenalinya. Contoh valid: `var1`, tidak valid: `1var`.

### Jawaban 5: b) `print("Hello")  # Ini komentar`
**Penjelasan:** PEP 8 merekomendasikan minimal dua spasi sebelum `#` untuk komentar inline.

### Jawaban 6: Variabel menyimpan nilai agar kode lebih mudah dibaca, digunakan ulang, dan memberikan konteks (misalnya, `num_students = 30` lebih jelas daripada `n = 30`).
**Penjelasan:** Variabel mencegah pengulangan perhitungan dan membuat kode lebih maintainable.

Gunakan quiz ini untuk mengulang materi. Jika salah, baca ulang bagian terkait!

## Ringkasan

Dalam bab ini, Anda belajar:
- Menjalankan kode di IDLE (interaktif dan script).
- Menangani error (sintaks dan run-time).
- Membuat dan menggunakan variabel.
- Memeriksa nilai variabel.
- Menambahkan komentar untuk dokumentasi.

Selanjutnya, eksplor lebih dalam Python! Jika ada pertanyaan, coba latihan di buku asli atau quiz online.

**Sumber:** Didasarkan dari "Python Basics" Chapter 3.
