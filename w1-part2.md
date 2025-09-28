# MODUL 2: FUNCTIONS DAN CONTROL FLOW
**Programming Logic dan User Interaction**

---

## CHAPTER 1: FUNCTIONS DAN MODULARITAS

### 1.1 Pengenalan Functions

Function adalah blok kode yang dapat dipanggil berulang kali:

```python
# Function sederhana
def salam():
    """Function untuk menyapa"""
    print("Halo, selamat datang!")

# Memanggil function
salam()
salam()  # Bisa dipanggil berkali-kali

# Function dengan parameter
def salam_personal(nama):
    """Function dengan parameter"""
    print(f"Halo {nama}, selamat datang!")

salam_personal("Ahmad")
salam_personal("Siti")
```

Catatan konseptual (fungsi dan modularitas, dari bahan ajar):
- Fungsi adalah blok kode yang bisa dipanggil berulang untuk mengurangi pengulangan (reusability) dan membuat program terstruktur.
- Penamaan yang jelas meningkatkan keterbacaan: gunakan snake_case dan nama yang bermakna.
- Jika sebuah fungsi tidak memiliki `return`, maka nilai kembalian default-nya adalah `None`.

### 1.2 Function dengan Return Value

```python
# Function yang mengembalikan nilai
def hitung_luas_persegi(sisi):
    """Menghitung luas persegi"""
    luas = sisi * sisi
    return luas

# Menggunakan return value
luas = hitung_luas_persegi(5)
print(f"Luas persegi: {luas}")

# Function dengan multiple parameters
def hitung_luas_persegi_panjang(panjang, lebar):
    """Menghitung luas persegi panjang"""
    return panjang * lebar

hasil = hitung_luas_persegi_panjang(10, 5)
print(f"Luas persegi panjang: {hasil}")

# Function dengan multiple return values
def hitung_lingkaran(radius):
    """Menghitung luas dan keliling lingkaran"""
    import math
    luas = math.pi * radius * radius
    keliling = 2 * math.pi * radius
    return luas, keliling

luas, keliling = hitung_lingkaran(7)
print(f"Luas: {luas:.2f}, Keliling: {keliling:.2f}")
```

Catatan konseptual (nilai kembalian):
- Tanpa `return`, Python mengembalikan `None` (berguna untuk fungsi yang hanya memiliki efek samping seperti print/logging).
- Fungsi bisa mengembalikan lebih dari satu nilai dengan mengembalikan tuple, lalu di-unpack ke beberapa variabel.

### 1.3 Parameter Types

```python
# Default parameters
def perkenalan(nama, umur=20, kota="Jakarta"):
    """Function dengan default parameter"""
    return f"Nama: {nama}, Umur: {umur}, Kota: {kota}"

print(perkenalan("Ahmad"))  # Menggunakan default
print(perkenalan("Budi", 25))  # Override umur
print(perkenalan("Citra", 22, "Bandung"))  # Override semua

# Keyword arguments
def buat_profil(nama, umur, pekerjaan, hobi):
    return f"{nama} ({umur} tahun) - {pekerjaan}, hobi: {hobi}"

# Bisa dipanggil dengan berbagai urutan
profile1 = buat_profil("Ahmad", 25, "Developer", "Gaming")
profile2 = buat_profil(hobi="Membaca", nama="Siti", pekerjaan="Designer", umur=23)
print(profile1)
print(profile2)

# *args dan **kwargs
def hitung_rata_rata(*angka):
    """Function dengan variable arguments"""
    if len(angka) == 0:
        return 0
    return sum(angka) / len(angka)

print(f"Rata-rata: {hitung_rata_rata(10, 20, 30, 40, 50)}")

def tampilkan_info(**kwargs):
    """Function dengan keyword arguments"""
    for key, value in kwargs.items():
        print(f"{key}: {value}")

tampilkan_info(nama="Ahmad", umur=25, kota="Jakarta", pekerjaan="Developer")
```

Catatan konseptual (parameter):
- Positional vs keyword arguments: keyword arguments memungkinkan urutan argumen fleksibel dan meningkatkan kejelasan.
- Default parameter memberi nilai bawaan jika argumen tidak diberikan.
- `*args` menampung sejumlah argumen posisi yang variatif; `**kwargs` menampung pasangan key-value yang variatif.

### 1.4 Scope dan Local vs Global Variables

```python
# Global variable
nama_aplikasi = "Sistem Akademik"
versi = "1.0"

def tampilkan_header():
    """Function mengakses global variable"""
    print(f"=== {nama_aplikasi} v{versi} ===")

def hitung_nilai(tugas, uts, uas):
    """Function dengan local variables"""
    # Local variables
    bobot_tugas = 0.3
    bobot_uts = 0.3
    bobot_uas = 0.4
    
    nilai_akhir = (tugas * bobot_tugas) + (uts * bobot_uts) + (uas * bobot_uas)
    return nilai_akhir

tampilkan_header()
nilai = hitung_nilai(85, 90, 88)
print(f"Nilai akhir: {nilai:.2f}")

# Global keyword
counter = 0

def increment_counter():
    global counter  # Akses global variable
    counter += 1
    print(f"Counter: {counter}")

increment_counter()
increment_counter()
```

Catatan konseptual (scope dan variabel):
- Variabel lokal hidup di dalam fungsi; variabel global dapat diakses di seluruh modul, namun penggunaannya sebaiknya dibatasi untuk menghindari efek samping tak terduga.
- Python bertipe dinamis: tipe variabel ditentukan saat runtime oleh nilai yang diberikan.

### 🧠 Mini Quiz - Chapter 1

**Soal 1:** Apa yang dikembalikan function ini?
```python
def test():
    x = 5
    y = 10
    # Tidak ada return statement
result = test()
```
a) 15  b) None  c) Error  d) 0

**Soal 2:** Bagaimana cara membuat parameter dengan nilai default?
a) def func(x=5):  b) def func(x default 5):  c) def func(x := 5):  d) def func(default x=5):

**Soal 3:** Apa kegunaan *args dalam function?
a) Untuk error handling  b) Untuk variable arguments  c) Untuk default values  d) Untuk return multiple values

### 💪 Mini Exercise - Chapter 1

**Latihan 1:** Kalkulator sederhana:
```python
# Buat function untuk operasi: +, -, *, /
# Function harus menangani pembagian dengan nol
# Test dengan berbagai input
```

**Latihan 2:** Sistem penilaian:
```python
def hitung_grade(nilai):
    # Return grade berdasarkan nilai:
    # >= 90: A, >= 80: B, >= 70: C, >= 60: D, < 60: E
    pass

def statistik_kelas(*nilai):
    # Hitung rata-rata, nilai tertinggi, terendah
    # Return sebagai dictionary
    pass
```

**Latihan 3:** Function dengan **kwargs:
```python
def buat_laporan(**data):
    # Terima berbagai parameter untuk laporan
    # Format output yang rapi
    pass

# Test: buat_laporan(nama="Ahmad", nilai=85, kelas="XII")
```

**Jawaban Mini Quiz:**
1. b) None
2. a) def func(x=5):
3. b) Untuk variable arguments

---

## CHAPTER 2: INPUT/OUTPUT DAN USER INTERACTION

### 2.1 Input dari User

```python
# Input dasar
nama = input("Masukkan nama Anda: ")
print(f"Halo {nama}!")

# Konversi input ke tipe data lain
try:
    umur = int(input("Masukkan umur: "))
    tinggi = float(input("Masukkan tinggi (cm): "))
    print(f"Data: {nama}, {umur} tahun, {tinggi} cm")
except ValueError:
    print("Input tidak valid!")

# Input dengan validasi
def input_angka(prompt):
    """Input angka dengan validasi"""
    while True:
        try:
            return float(input(prompt))
        except ValueError:
            print("Masukkan angka yang valid!")

nilai = input_angka("Masukkan nilai (0-100): ")
print(f"Nilai yang dimasukkan: {nilai}")
```

Catatan konseptual (input dan validasi):
- `input()` selalu mengembalikan string; gunakan konversi `int()`/`float()` sebelum perhitungan numerik.
- Validasi input dan penanganan kesalahan (`try/except`) penting untuk pengalaman pengguna yang baik.

### 2.2 Format Output

```python
# String formatting methods
nama = "Ahmad"
nilai = 87.5
ranking = 1

# f-string (modern)
print(f"Siswa: {nama}, Nilai: {nilai:.1f}, Ranking: #{ranking}")

# format() method
print("Siswa: {}, Nilai: {:.1f}, Ranking: #{}".format(nama, nilai, ranking))

# % formatting (legacy)
print("Siswa: %s, Nilai: %.1f, Ranking: #%d" % (nama, nilai, ranking))

# Advanced formatting
harga = 1500000
print(f"Harga: Rp {harga:,}")  # Dengan pemisah ribuan
print(f"Harga: Rp {harga:>15,}")  # Right align dalam 15 karakter

# Format tanggal dan waktu
from datetime import datetime
sekarang = datetime.now()
print(f"Sekarang: {sekarang:%Y-%m-%d %H:%M:%S}")
```

Catatan konseptual (string formatting dari bahan ajar):
- F-string menggunakan placeholder dalam kurung kurawal `{}` untuk menyisipkan variabel/ekspresi.
- Perhatikan spasi saat menggabungkan string (concatenation) agar hasil tampilan sesuai harapan.

### 2.3 File I/O

```python
# Menulis ke file
def simpan_data_mahasiswa(data):
    """Simpan data mahasiswa ke file"""
    with open("mahasiswa.txt", "w") as file:
        file.write("=== DATA MAHASISWA ===\n")
        for mhs in data:
            file.write(f"Nama: {mhs['nama']}, NIM: {mhs['nim']}, IPK: {mhs['ipk']}\n")
    print("Data berhasil disimpan!")

# Membaca dari file
def baca_data_mahasiswa():
    """Baca data mahasiswa dari file"""
    try:
        with open("mahasiswa.txt", "r") as file:
            content = file.read()
            return content
    except FileNotFoundError:
        return "File tidak ditemukan!"

# Contoh penggunaan
data_mhs = [
    {"nama": "Ahmad", "nim": "12345", "ipk": 3.75},
    {"nama": "Siti", "nim": "12346", "ipk": 3.85}
]

simpan_data_mahasiswa(data_mhs)
print(baca_data_mahasiswa())
```

Catatan konseptual (mode file singkat):
- "r" untuk membaca, "w" untuk menulis (overwrite), "a" untuk menambah di akhir (append), dan "x" untuk membuat file baru (gagal jika sudah ada).

### 2.4 Interactive Menu System

```python
def tampilkan_menu():
    """Tampilkan menu pilihan"""
    print("\n=== SISTEM MANAJEMEN MAHASISWA ===")
    print("1. Tambah Data Mahasiswa")
    print("2. Lihat Semua Data")
    print("3. Cari Mahasiswa")
    print("4. Keluar")
    print("=" * 35)

def tambah_mahasiswa(data_list):
    """Tambah data mahasiswa baru"""
    print("\n--- Tambah Data Mahasiswa ---")
    nama = input("Nama: ")
    nim = input("NIM: ")
    
    while True:
        try:
            ipk = float(input("IPK (0.00-4.00): "))
            if 0 <= ipk <= 4:
                break
            else:
                print("IPK harus antara 0.00 - 4.00")
        except ValueError:
            print("Masukkan angka yang valid!")
    
    mahasiswa_baru = {"nama": nama, "nim": nim, "ipk": ipk}
    data_list.append(mahasiswa_baru)
    print(f"Data {nama} berhasil ditambahkan!")

def sistem_manajemen():
    """Sistem manajemen mahasiswa"""
    data_mahasiswa = []
    
    while True:
        tampilkan_menu()
        pilihan = input("Pilih menu (1-4): ")
        
        if pilihan == "1":
            tambah_mahasiswa(data_mahasiswa)
        elif pilihan == "2":
            if data_mahasiswa:
                print("\n=== DATA MAHASISWA ===")
                for i, mhs in enumerate(data_mahasiswa, 1):
                    print(f"{i}. {mhs['nama']} ({mhs['nim']}) - IPK: {mhs['ipk']}")
            else:
                print("Belum ada data mahasiswa.")
        elif pilihan == "3":
            if data_mahasiswa:
                cari = input("Masukkan nama atau NIM yang dicari: ").lower()
                hasil = [mhs for mhs in data_mahasiswa 
                        if cari in mhs['nama'].lower() or cari in mhs['nim']]
                if hasil:
                    print("\n=== HASIL PENCARIAN ===")
                    for mhs in hasil:
                        print(f"{mhs['nama']} ({mhs['nim']}) - IPK: {mhs['ipk']}")
                else:
                    print("Data tidak ditemukan.")
            else:
                print("Belum ada data mahasiswa.")
        elif pilihan == "4":
            print("Terima kasih!")
            break
        else:
            print("Pilihan tidak valid!")

# Jalankan sistem (uncomment untuk test)
# sistem_manajemen()
```

### 🧠 Mini Quiz - Chapter 2

**Soal 1:** Function input() di Python selalu mengembalikan tipe data:
a) int  b) float  c) str  d) bool

**Soal 2:** Cara yang benar untuk format angka dengan 2 desimal menggunakan f-string:
a) f"{nilai:.2}"  b) f"{nilai:.2f}"  c) f"{nilai:2f}"  d) f"{nilai:2.f}"

**Soal 3:** Mode file yang digunakan untuk menulis ke file (overwrite jika ada):
a) "r"  b) "w"  c) "a"  d) "x"

### 💪 Mini Exercise - Chapter 2

**Latihan 1:** Program kalkulator interaktif:
```python
# Buat program yang terus meminta input
# User bisa pilih operasi (+, -, *, /)
# Validasi input angka
# Opsi untuk keluar dari program
```

**Latihan 2:** Sistem inventori sederhana:
```python
# Menu: tambah barang, lihat barang, update stok, keluar
# Simpan data ke file
# Baca data dari file saat program dimulai
# Validasi input untuk stok dan harga
```

**Latihan 3:** Log aktivitas:
```python
def log_aktivitas(aktivitas):
    # Simpan aktivitas dengan timestamp ke file log
    # Format: [YYYY-MM-DD HH:MM:SS] Aktivitas
    pass

# Test dengan berbagai aktivitas
```

**Jawaban Mini Quiz:**
1. c) str
2. b) f"{nilai:.2f}"
3. b) "w"

---

## CHAPTER 3: LOOPS DAN ITERASI

### 3.1 For Loop

```python
# Loop dengan range
print("=== Counting 1-10 ===")
for i in range(1, 11):
    print(f"Angka: {i}")

# Loop dengan step
print("\n=== Angka Genap 2-20 ===")
for i in range(2, 21, 2):
    print(f"Genap: {i}")

# Loop mundur
print("\n=== Countdown ===")
for i in range(10, 0, -1):
    print(f"Countdown: {i}")
print("Blast off! 🚀")

# Loop pada list
buah = ["apel", "pisang", "jeruk", "mangga"]
print("\n=== Daftar Buah ===")
for buah_item in buah:
    print(f"- {buah_item.capitalize()}")

# Loop dengan enumerate (index dan value)
print("\n=== Daftar dengan Index ===")
for index, buah_item in enumerate(buah, 1):
    print(f"{index}. {buah_item.capitalize()}")
```

### 3.2 While Loop

```python
# While loop sederhana
print("=== While Loop Basic ===")
counter = 1
while counter <= 5:
    print(f"Counter: {counter}")
    counter += 1

# While loop untuk validasi input
def input_valid_angka():
    """Input angka dengan validasi menggunakan while loop"""
    while True:
        try:
            angka = float(input("Masukkan angka (1-100): "))
            if 1 <= angka <= 100:
                return angka
            else:
                print("Angka harus antara 1-100!")
        except ValueError:
            print("Input harus berupa angka!")

# Game tebak angka
import random

def game_tebak_angka():
    """Game tebak angka menggunakan while loop"""
    target = random.randint(1, 100)
    percobaan = 0
    max_percobaan = 7
    
    print("=== GAME TEBAK ANGKA ===")
    print(f"Tebak angka antara 1-100 dalam {max_percobaan} percobaan!")
    
    while percobaan < max_percobaan:
        try:
            tebakan = int(input(f"Percobaan {percobaan + 1}: "))
            percobaan += 1
            
            if tebakan == target:
                print(f"🎉 BENAR! Angka {target} dalam {percobaan} percobaan!")
                return
            elif tebakan < target:
                print("Terlalu kecil! ⬆️")
            else:
                print("Terlalu besar! ⬇️")
                
        except ValueError:
            print("Masukkan angka yang valid!")
    
    print(f"😞 Game Over! Angka yang benar: {target}")

# Test game (uncomment untuk bermain)
# game_tebak_angka()
```

### 3.3 Nested Loops

```python
# Tabel perkalian
print("=== TABEL PERKALIAN ===")
for i in range(1, 11):
    for j in range(1, 11):
        hasil = i * j
        print(f"{hasil:4}", end="")  # Format 4 karakter
    print()  # Newline setelah setiap baris

# Pattern dengan nested loop
def cetak_segitiga(tinggi):
    """Cetak pattern segitiga dengan nested loop"""
    print(f"\n=== Segitiga Tinggi {tinggi} ===")
    for i in range(1, tinggi + 1):
        # Spasi
        for j in range(tinggi - i):
            print(" ", end="")
        # Bintang
        for k in range(2 * i - 1):
            print("*", end="")
        print()

cetak_segitiga(5)

# Matrix operations
def buat_matrix(baris, kolom, nilai_default=0):
    """Buat matrix menggunakan nested loop"""
    matrix = []
    for i in range(baris):
        row = []
        for j in range(kolom):
            row.append(nilai_default)
        matrix.append(row)
    return matrix

def tampilkan_matrix(matrix):
    """Tampilkan matrix"""
    print("\n=== MATRIX ===")
    for baris in matrix:
        for elemen in baris:
            print(f"{elemen:4}", end="")
        print()

# Test matrix
matrix_3x3 = buat_matrix(3, 3, 1)
tampilkan_matrix(matrix_3x3)
```

### 3.4 Loop Control (break, continue, else)

```python
# Break dan continue
def demo_break_continue():
    """Demonstrasi break dan continue"""
    print("=== DEMO BREAK & CONTINUE ===")
    
    # Continue - skip angka genap
    print("Angka ganjil 1-10:")
    for i in range(1, 11):
        if i % 2 == 0:  # Skip angka genap
            continue
        print(i, end=" ")
    print()
    
    # Break - berhenti di angka 7
    print("\nAngka 1-10 tapi berhenti di 7:")
    for i in range(1, 11):
        if i == 7:
            break
        print(i, end=" ")
    print()

demo_break_continue()

# For-else dan while-else
def cari_angka_prima(n):
    """Cari angka prima menggunakan for-else"""
    if n < 2:
        return False
    
    for i in range(2, int(n ** 0.5) + 1):
        if n % i == 0:
            return False  # Break karena ketemu pembagi
    else:  # Dijalankan jika loop selesai tanpa break
        return True

# Test angka prima
print("\n=== TEST ANGKA PRIMA ===")
for angka in [2, 3, 4, 17, 25, 29]:
    status = "Prima" if cari_angka_prima(angka) else "Bukan Prima"
    print(f"{angka}: {status}")

# Menu dengan while-else
def menu_dengan_else():
    """Demo while-else"""
    print("\n=== MENU DEMO ===")
    print("Ketik 'quit' untuk keluar")
    
    while True:
        perintah = input("Masukkan perintah: ").lower()
        if perintah == 'quit':
            break
        elif perintah == 'hello':
            print("Halo!")
        else:
            print("Perintah tidak dikenal")
    else:  # Tidak dijalankan karena ada break
        print("Loop selesai tanpa break")
    
    print("Program selesai!")

# Uncomment untuk test
# menu_dengan_else()
```

### 🧠 Mini Quiz - Chapter 3

**Soal 1:** Apa output dari kode ini?
```python
for i in range(3):
    if i == 1:
        continue
    print(i)
```
a) 0 1 2  b) 0 2  c) 1 2  d) 0 1

**Soal 2:** Kapan blok else dalam for loop dijalankan?
a) Selalu  b) Jika ada break  c) Jika tidak ada break  d) Jika ada error

**Soal 3:** Bagaimana cara membuat loop mundur dari 10 ke 1?
a) range(10, 1)  b) range(10, 0, -1)  c) range(10, 1, -1)  d) range(1, 10, -1)

### 💪 Mini Exercise - Chapter 3

**Latihan 1:** Pattern printing:
```python
# Buat function untuk mencetak berbagai pattern:
# 1. Segitiga siku-siku
# 2. Belah ketupat
# 3. Tabel perkalian custom
```

**Latihan 2:** Sistem quiz:
```python
# Buat quiz dengan loop:
# - Daftar soal dan jawaban
# - Hitung skor
# - Ulangi sampai user mau berhenti
# - Tampilkan statistik
```

**Latihan 3:** Data processing:
```python
# Proses list data mahasiswa
# - Hitung rata-rata nilai per mata kuliah
# - Cari mahasiswa dengan IPK tertinggi
# - Kelompokkan berdasarkan status kelulusan
```

**Jawaban Mini Quiz:**
1. b) 0 2
2. c) Jika tidak ada break
3. b) range(10, 0, -1)

---

## CHAPTER 4: CONDITIONAL STATEMENTS LANJUTAN

### 4.1 If-Elif-Else Advanced

```python
# Grading system yang kompleks
def hitung_grade(nilai, kehadiran, tugas):
    """System grading dengan multiple conditions"""
    
    # Validasi input
    if not (0 <= nilai <= 100 and 0 <= kehadiran <= 100 and 0 <= tugas <= 100):
        return "Input tidak valid"
    
    # Syarat kelulusan minimum
    if kehadiran < 75:
        return "E (Kehadiran tidak memenuhi)"
    
    if tugas < 60:
        return "E (Tugas tidak memenuhi)"
    
    # Grading berdasarkan nilai
    if nilai >= 90:
        grade = "A"
    elif nilai >= 80:
        grade = "B"
    elif nilai >= 70:
        grade = "C"
    elif nilai >= 60:
        grade = "D"
    else:
        grade = "E"
    
    # Bonus untuk kehadiran sempurna
    if kehadiran == 100 and grade in ["B", "C", "D"]:
        grade_levels = {"B": "A-", "C": "B-", "D": "C-"}
        grade = grade_levels.get(grade, grade)
    
    return grade

# Test grading system
print("=== SISTEM GRADING ===")
test_cases = [
    (95, 100, 90),  # A
    (85, 100, 80),  # A- (bonus kehadiran)
    (75, 70, 80),   # E (kehadiran kurang)
    (80, 90, 50),   # E (tugas kurang)
]

for nilai, hadir, tugas in test_cases:
    grade = hitung_grade(nilai, hadir, tugas)
    print(f"Nilai: {nilai}, Kehadiran: {hadir}%, Tugas: {tugas} → Grade: {grade}")
```

### 4.2 Logical Operators dan Short-Circuit

```python
# Short-circuit evaluation
def demo_short_circuit():
    """Demonstrasi short-circuit evaluation"""
    
    def check_positive(x):
        print(f"Checking if {x} is positive")
        return x > 0
    
    def check_even(x):
        print(f"Checking if {x} is even")
        return x % 2 == 0
    
    print("=== AND Short-Circuit ===")
    # Jika kondisi pertama False, kondisi kedua tidak dievaluasi
    result = check_positive(-5) and check_even(-5)
    print(f"Result: {result}\n")
    
    print("=== AND Normal ===")
    result = check_positive(10) and check_even(10)
    print(f"Result: {result}\n")
    
    print("=== OR Short-Circuit ===")
    # Jika kondisi pertama True, kondisi kedua tidak dievaluasi
    result = check_positive(5) or check_even(5)
    print(f"Result: {result}\n")

demo_short_circuit()

# Complex logical conditions
def validasi_login(username, password, age, is_active):
    """Validasi login dengan multiple conditions"""
    
    # Check basic requirements
    if not username or not password:
        return False, "Username dan password wajib diisi"
    
    # Check age and account status
    if not (18 <= age <= 100) or not is_active:
        return False, "Akun tidak memenuhi syarat"
    
    # Check password strength (simplified)
    if len(password) < 8:
        return False, "Password minimal 8 karakter"
    
    # All conditions met
    return True, "Login berhasil"

# Test validation
login_tests = [
    ("", "pass123", 20, True),           # Username kosong
    ("user1", "123", 20, True),          # Password pendek
    ("user2", "password123", 17, True),  # Umur tidak memenuhi
    ("user3", "password123", 25, False), # Akun tidak aktif
    ("user4", "password123", 25, True),  # Valid
]

print("=== VALIDASI LOGIN ===")
for username, password, age, is_active in login_tests:
    valid, message = validasi_login(username, password, age, is_active)
    print(f"User: {username} → {message}")
```

### 4.3 Match-Case (Python 3.10+)

```python
# Match-case statement (Python 3.10+)
def kalkulator_match(operator, a, b):
    """Kalkulator menggunakan match-case"""
    match operator:
        case "+":
            return a + b
        case "-":
            return a - b
        case "*":
            return a * b
        case "/":
            if b != 0:
                return a / b
            else:
                return "Error: Pembagian dengan nol"
        case "**" | "^":  # Multiple patterns
            return a ** b
        case _:  # Default case
            return "Operator tidak dikenal"

# Grade interpretation dengan match
def interpretasi_grade(grade):
    """Interpretasi grade menggunakan match-case"""
    match grade.upper():
        case "A":
            return "Excellent (90-100)"
        case "B":
            return "Good (80-89)"
        case "C":
            return "Average (70-79)"
        case "D":
            return "Below Average (60-69)"
        case "E" | "F":
            return "Fail (< 60)"
        case _:
            return "Grade tidak valid"

# Test match-case
print("=== KALKULATOR MATCH-CASE ===")
operasi = [
    ("+", 10, 5),
    ("-", 10, 3),
    ("*", 4, 6),
    ("/", 20, 4),
    ("^", 2, 3),
    ("%", 10, 3)  # Operator tidak dikenal
]

for op, x, y in operasi:
    hasil = kalkulator_match(op, x, y)
    print(f"{x} {op} {y} = {hasil}")

print("\n=== INTERPRETASI GRADE ===")
grades = ["A", "B", "C", "D", "E", "X"]
for g in grades:
    print(f"Grade {g}: {interpretasi_grade(g)}")
```

Tips membaca error (troubleshooting singkat dari bahan ajar):
- Baca pesan error dari baris terbawah—sering kali memberi tahu jenis dan lokasi kesalahan (misal `SyntaxError: invalid syntax`).
- Kesalahan umum: lupa pemisah koma saat mencetak banyak variabel (`print(a, b, c)` bukan `print(a b c)`), atau kurangnya tanda kurung/tanda kutip pada string.

### 4.4 Nested Conditions dan Optimization

```python
# Sistem rekomendasi film
def rekomendasi_film(umur, genre_favorit, rating_minimum, durasi_max):
    """Sistem rekomendasi film dengan nested conditions"""
    
    # Database film sederhana
    film_database = [
        {"judul": "Avengers", "genre": "action", "rating": 8.5, "durasi": 150, "umur_min": 13},
        {"judul": "Frozen", "genre": "animation", "rating": 8.0, "durasi": 102, "umur_min": 3},
        {"judul": "The Godfather", "genre": "drama", "rating": 9.2, "durasi": 175, "umur_min": 17},
        {"judul": "Toy Story", "genre": "animation", "rating": 8.3, "durasi": 81, "umur_min": 3},
        {"judul": "John Wick", "genre": "action", "rating": 7.4, "durasi": 101, "umur_min": 18},
    ]
    
    rekomendasi = []
    
    for film in film_database:
        # Nested conditions untuk filtering
        if umur >= film["umur_min"]:  # Cek umur
            if genre_favorit.lower() == film["genre"]:  # Cek genre
                if film["rating"] >= rating_minimum:  # Cek rating
                    if film["durasi"] <= durasi_max:  # Cek durasi
                        rekomendasi.append(film)
    
    return rekomendasi

# Optimized version dengan all()
def rekomendasi_film_optimized(umur, genre_favorit, rating_minimum, durasi_max):
    """Versi optimized dari sistem rekomendasi"""
    
    film_database = [
        {"judul": "Avengers", "genre": "action", "rating": 8.5, "durasi": 150, "umur_min": 13},
        {"judul": "Frozen", "genre": "animation", "rating": 8.0, "durasi": 102, "umur_min": 3},
        {"judul": "The Godfather", "genre": "drama", "rating": 9.2, "durasi": 175, "umur_min": 17},
        {"judul": "Toy Story", "genre": "animation", "rating": 8.3, "durasi": 81, "umur_min": 3},
        {"judul": "John Wick", "genre": "action", "rating": 7.4, "durasi": 101, "umur_min": 18},
    ]
    
    def cocok_kriteria(film):
        return all([
            umur >= film["umur_min"],
            genre_favorit.lower() == film["genre"],
            film["rating"] >= rating_minimum,
            film["durasi"] <= durasi_max
        ])
    
    return [film for film in film_database if cocok_kriteria(film)]

# Test sistem rekomendasi
print("=== SISTEM REKOMENDASI FILM ===")
rekomendasi = rekomendasi_film(
    umur=16,
    genre_favorit="action",
    rating_minimum=7.0,
    durasi_max=120
)

print("Rekomendasi untuk Anda:")
for film in rekomendasi:
    print(f"- {film['judul']} ({film['rating']}/10, {film['durasi']} menit)")

if not rekomendasi:
    print("Tidak ada film yang cocok dengan kriteria Anda.")
```

### 🧠 Mini Quiz - Chapter 4

**Soal 1:** Dalam short-circuit evaluation, kapan kondisi kedua tidak dievaluasi pada operator AND?
a) Jika kondisi pertama True  b) Jika kondisi pertama False  c) Selalu dievaluasi  d) Tidak pernah dievaluasi

**Soal 2:** Apa yang terjadi jika tidak ada case yang cocok dalam match-case dan tidak ada default case?
a) Error  b) None  c) False  d) Tidak ada yang terjadi

**Soal 3:** Function all() mengembalikan True jika:
a) Semua elemen True  b) Ada elemen True  c) Tidak ada elemen  d) A dan C benar

### 💪 Mini Exercise - Chapter 4

**Latihan 1:** Sistem seleksi beasiswa:
```python
def cek_beasiswa(ipk, penghasilan_ortu, prestasi, organisasi):
    # Kriteria beasiswa:
    # - IPK >= 3.5
    # - Penghasilan orang tua < 5 juta
    # - Punya prestasi atau aktif organisasi
    # Return: jenis beasiswa dan alasan
    pass
```

**Latihan 2:** Game RPG status checker:
```python
def cek_status_karakter(level, hp, mp, exp):
    # Tentukan status karakter:
    # - Ready to fight
    # - Need healing
    # - Need rest
    # - Level up available
    # Gunakan nested conditions
    pass
```

**Latihan 3:** Sistem approval kredit:
```python
def approve_kredit(gaji, umur, riwayat_kredit, jumlah_pinjaman):
    # Multi-level approval system
    # - Auto approve
    # - Manual review
    # - Auto reject
    # Dengan detailed reasoning
    pass
```

**Jawaban Mini Quiz:**
1. b) Jika kondisi pertama False
2. a) Error
3. d) A dan C benar

---

## LATIHAN DAN QUIZ

### Quiz Pilihan Ganda

1. Apa yang dikembalikan function tanpa return statement?
   a) 0  b) ""  c) None  d) Error

2. Function input() selalu mengembalikan tipe data:
   a) int  b) float  c) str  d) bool

3. Kapan else dalam for loop dieksekusi?
   a) Selalu  b) Jika ada break  c) Jika tidak ada break  d) Tidak pernah

4. Dalam short-circuit AND, kondisi kedua dievaluasi jika kondisi pertama:
   a) True  b) False  c) None  d) Tidak pernah

5. *args dalam function parameter digunakan untuk:
   a) Default values  b) Keyword arguments  c) Variable arguments  d) Return values

### Latihan Praktik

**Latihan 1: Sistem Manajemen Nilai**
Buat program untuk mengelola nilai siswa dengan fitur:
- Input data siswa dan nilai
- Hitung statistik kelas
- Generate laporan

**Latihan 2: Game Sederhana**
Buat game tebak kata dengan:
- Menu interaktif
- System scoring
- Multiple levels

**Latihan 3: Aplikasi Keuangan Personal**
Buat aplikasi untuk:
- Track income/expense
- Kategorisasi transaksi
- Generate summary report

### Kunci Jawaban Quiz
1. c) None
2. c) str
3. c) Jika tidak ada break
4. a) True
5. c) Variable arguments

---

## RANGKUMAN MODUL 2

### Konsep yang Dipelajari:
1. **Functions**: Parameter, return values, scope
2. **I/O Operations**: Input validation, file handling, formatting
3. **Loops**: For, while, nested loops, control statements
4. **Conditionals**: Complex conditions, logical operators, match-case

### Skills yang Dikuasai:
- Membuat fungsi yang efisien dan reusable
- Menangani input user dengan validasi
- Menggunakan loops untuk data processing
- Membuat logic yang kompleks dengan conditionals
- Error handling dan user experience

### Persiapan Modul 3:
Modul selanjutnya akan membahas file management, web scraping, dan teknik Python lanjutan yang membangun di atas fondasi dari modul ini.
