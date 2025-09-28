# MODUL 1: DASAR-DASAR PYTHON
**Tipe Data dan Struktur Data Fundamental**

---

## CHAPTER 1: TIPE DATA DASAR PYTHON

### 1.1 Pengenalan Tipe Data

Python memiliki beberapa tipe data built-in yang fundamental:
- **Integer (int)**: Bilangan bulat
- **Float**: Bilangan desimal
- **String (str)**: Teks
- **Boolean (bool)**: True/False

Catatan konseptual (ringkas dari bahan ajar):
- Setiap program bekerja dengan data—teks, angka, atau kombinasi lain. Tipe data adalah “roda gigi” yang memungkinkan bagian program lainnya saling terhubung dan berjalan.
- Python tidak mengejar jumlah tipe data yang sangat banyak; justru sederhana namun efektif sehingga kita bisa lebih fokus ke pemecahan masalah daripada detail teknis yang berlebihan.

### 1.2 Integer (Bilangan Bulat)

```python
# Contoh integer
umur = 25
jumlah_siswa = 30
tahun = 2024

# Operasi matematika dengan integer
a = 10
b = 3
print(f"Penjumlahan: {a + b}")
print(f"Pengurangan: {a - b}")
print(f"Perkalian: {a * b}")
print(f"Pembagian: {a / b}")    # Hasil: float
print(f"Pembagian bulat: {a // b}")  # Hasil: int
print(f"Modulo: {a % b}")
```

Catatan konseptual (int vs float):
- `100` (int) berbeda dengan `100.00` (float). Int cocok untuk bilangan bulat seperti jumlah nyawa atau item, sedangkan float dipakai untuk presisi desimal (misalnya pengurangan nyawa 1.5 poin per hit). Pilih tipe sesuai kebutuhan presisi perhitungan.

### 1.3 Float (Bilangan Desimal)

```python
# Contoh float
tinggi = 175.5
berat = 65.2
pi = 3.14159

# Operasi dengan float
suhu_celsius = 25.5
suhu_fahrenheit = (suhu_celsius * 9/5) + 32
print(f"{suhu_celsius}°C = {suhu_fahrenheit}°F")

# Precision dan rounding
import math
nilai = 3.14159
print(f"Dibulatkan: {round(nilai, 2)}")
print(f"Floor: {math.floor(nilai)}")
print(f"Ceiling: {math.ceil(nilai)}")
```

### 1.4 String (Teks)

```python
# Membuat string
nama = "Ahmad Fauzi"
kota = 'Jakarta'
alamat = """Jl. Merdeka No. 123
Jakarta Pusat
Indonesia"""

# String methods
print(nama.upper())
print(nama.lower())
print(nama.title())
print(len(nama))

# String formatting
umur = 25
print(f"Nama saya {nama}, umur {umur} tahun")
print("Nama saya {}, umur {} tahun".format(nama, umur))
```

Catatan konseptual (apa itu string dan cara menampilkan):
- String adalah kumpulan karakter yang dibatasi tanda kutip tunggal atau ganda.
- Untuk menampilkan string, gunakan `print("teks")` atau variabel berisi teks. Spasi juga bagian dari string, jadi jika menggabungkan string, perhatikan penempatan spasi.

### 1.5 Boolean (Benar/Salah)

```python
# Boolean values
is_student = True
is_working = False
has_license = True

# Boolean operations
print(is_student and has_license)  # AND
print(is_student or is_working)    # OR
print(not is_working)              # NOT

# Comparison menghasilkan boolean
a = 5
b = 3
print(a > b)   # True
print(a == b)  # False
print(a != b)  # True
```

Catatan konseptual (peran boolean):
- Boolean hanya memiliki dua nilai: `True` atau `False`. Tipe ini sangat penting untuk pengambilan keputusan (percabangan). Misal analogi: jika cuaca dingin maka bawa jaket, jika hangat maka bawa pakaian tipis—itulah logika True/False yang menuntun alur program.

### 1.6 Konversi Tipe Data

```python
# Konversi antar tipe data
angka_str = "123"
angka_int = int(angka_str)  # String ke integer
angka_float = float(angka_str)  # String ke float

nilai = 95.7
nilai_int = int(nilai)          # Float ke integer (95)
nilai_str = str(nilai)          # Float ke string

# Konversi boolean
print(bool(1))    # True
print(bool(0))    # False
print(bool(""))   # False
print(bool("text"))  # True

# Contoh konversi dalam konteks
def konversi_suhu(celsius_str):
    """Konversi string celsius ke fahrenheit"""
    celsius = float(celsius_str)
    fahrenheit = (celsius * 9/5) + 32
    return fahrenheit

hasil_konversi = konversi_suhu("25.5")
print(f"Hasil konversi: {hasil_konversi}")
print(f"Tipe data: {type(hasil_konversi)}")
```

Catatan konseptual (cek tipe dan konversi):
- Python menentukan tipe variabel saat runtime (dinamis). Anda dapat memeriksa tipe dengan `type(x)` dan mengonversi antar tipe menggunakan konstruktor seperti `int()`, `float()`, `str()`, dan `bool()`.

### 1.7 Variabel: Konsep, Penamaan, dan Penugasan (dari bahan ajar)

Variabel adalah “wadah” untuk menyimpan data agar bisa dipanggil, diubah, atau dihapus saat dibutuhkan. Python bersifat dinamis—Anda tidak perlu mendeklarasikan tipe di awal; tipe ditentukan dari nilai yang diberikan.

Contoh pembuatan variabel beragam tipe:

```python
name = "John"      # string
age = 33            # integer
weight = 131.50     # float
is_married = True   # boolean (perhatikan huruf besar-kecil: True/False)
```

Mengecek tipe variabel:

```python
print(type(age))   # <class 'int'>
```

Multiple assignment (satu nilai ke beberapa variabel sekaligus):

```python
Age = Number = Point = 20
print(Age, Number, Point)  # 20 20 20
```

Menampilkan beberapa variabel sekaligus (gunakan koma sebagai pemisah, bukan disambung tanpa pemisah):

```python
name = "Jonah"
age = 47
height_in_cm = 170
occupation = "Programmer"

print(name, age, height_in_cm, occupation)  # Jonah 47 170 Programmer

# Hindari menulis seperti ini karena salah sintaks:
# print(name age height_in_cm occupation)  # SyntaxError
```

Konkatenasi string dan perhatian spasi:

```python
first_name = "John"
last_name = "Wick"

print(first_name + last_name)       # JohnWick (tanpa spasi)
print(first_name + " " + last_name) # John Wick (dengan spasi)
```

Menggabungkan string dengan angka: konversi dulu ke string menggunakan `str()` atau gunakan f-string:

```python
text1 = "Zero is equal to "
text2 = 0
print(text1 + str(text2))  # Zero is equal to 0

# Alternatif yang lebih rapi: f-string (string formatting modern)
show = "GOT"
name1 = "Daenerys"; name2 = "Jon"; name3 = "Tyrion"; seasons = 8
print(f"The show called {show} had characters like {name1}, {name2} and {name3} in all {seasons} seasons.")
```

Aturan penamaan variabel (ringkas):
- Case-sensitive (`number` dan `Number` berbeda).
- Tidak boleh diawali angka; karakter yang diizinkan: huruf, angka, dan underscore `_` (tanpa spasi).
- Hindari memakai kata kunci Python sebagai nama variabel.
- Gunakan nama yang bermakna untuk meningkatkan keterbacaan (misal `height_in_cm` daripada `hcm`).

### 🧠 Mini Quiz - Chapter 1

**Soal 1:** Apa output dari kode berikut?
```python
x = "123"
y = int(x) + 7
print(y)
```
a) "1237"  b) 130  c) Error  d) "130"

**Soal 2:** Tipe data apa yang dihasilkan dari operasi `5 / 2`?
a) int  b) float  c) str  d) bool

**Soal 3:** Manakah yang TIDAK termasuk tipe data primitif di Python?
a) int  b) float  c) list  d) bool

### 💪 Mini Exercise - Chapter 1

**Latihan 1:** Buatlah program yang:
- Berisi Variable nama (string)
- Berisi Variable umur (integer) 
- Berisi Variable tinggi badan (float)
- Tampilkan informasi dengan format yang rapi. Misal "Nama saya adalah X umur saya Y tinggi badan saya Z"

**Latihan 2:** Konversi tipe data berikut dan tampilkan hasilnya:
```python
a = "3.14"
b = 42
c = True
# Konversi a ke float, b ke string, c ke integer
```

**Jawaban Mini Quiz:**
1. b) 130
2. b) float  
3. c) list

---

## CHAPTER 2: STRUKTUR DATA - LISTS

### 2.1 Pengenalan List

List adalah struktur data berurutan yang bisa menyimpan berbagai tipe data:

```python
# Membuat list
buah = ["apel", "pisang", "jeruk"]
angka = [1, 2, 3, 4, 5]
campuran = ["Ahmad", 25, 175.5, True]

# List kosong
keranjang = []
belanja = list()

print(f"Buah: {buah}")
print(f"Panjang list: {len(buah)}")
```

### 2.2 Mengakses Elemen List

```python
makanan = ["nasi", "ayam", "sayur", "buah"]

# Akses dengan index (dimulai dari 0)
print(f"Makanan pertama: {makanan[0]}")
print(f"Makanan terakhir: {makanan[-1]}")

# Slicing
print(f"2 makanan pertama: {makanan[:2]}")
print(f"2 makanan terakhir: {makanan[-2:]}")
print(f"Makanan tengah: {makanan[1:3]}")
```

### 2.3 Operasi pada List

```python
# Menambah elemen
hobi = ["membaca", "menulis"]
hobi.append("coding")        # Tambah di akhir
hobi.insert(1, "traveling")  # Tambah di posisi tertentu

print(f"Hobi: {hobi}")

# Menghapus elemen
hobi.remove("menulis")       # Hapus berdasarkan nilai
deleted = hobi.pop()         # Hapus elemen terakhir
deleted_index = hobi.pop(0)  # Hapus berdasarkan index

print(f"Hobi setelah dihapus: {hobi}")

# Mengubah elemen
warna = ["merah", "hijau", "biru"]
warna[0] = "kuning"
print(f"Warna: {warna}")
```

### 2.4 Operasi List Lanjutan

```python
angka = [3, 1, 4, 1, 5, 9, 2, 6]

# Sorting
angka_sorted = sorted(angka)      # Buat list baru yang sorted
print(f"Sorted (baru): {angka_sorted}")

angka.sort()                      # Sort list asli
print(f"Sorted (asli): {angka}")

# Reverse
angka.reverse()
print(f"Reversed: {angka}")

# Pencarian
print(f"Index of 5: {angka.index(5)}")
print(f"Count of 1: {angka.count(1)}")

# Copy list
backup_angka = angka.copy()
angka_lain = angka[:]  # Alternatif copy
```

### 2.5 List Comprehension

```python
# List comprehension - cara ringkas membuat list
angka = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]

# Kuadrat dari setiap angka
kuadrat = [x**2 for x in angka]
print(f"Kuadrat: {kuadrat}")

# Bilangan genap saja
genap = [x for x in angka if x % 2 == 0]
print(f"Genap: {genap}")

# Kombinasi kondisi dan transformasi
kuadrat_ganjil = [x**2 for x in angka if x % 2 == 1]
print(f"Kuadrat ganjil: {kuadrat_ganjil}")

# List comprehension dengan string
nama = ["ahmad", "budi", "citra"]
nama_kapital = [n.capitalize() for n in nama]
print(f"Nama kapital: {nama_kapital}")
```

### 🧠 Mini Quiz - Chapter 2

**Soal 1:** Apa output dari `fruits = ['apel', 'pisang']; print(fruits[1])`?
a) apel  b) pisang  c) 1  d) Error

**Soal 2:** Method apa yang digunakan untuk menambah elemen di akhir list?
a) add()  b) append()  c) insert()  d) push()

**Soal 3:** Hasil dari `[x**2 for x in [1,2,3]]` adalah:
a) [1,2,3]  b) [1,4,9]  c) [2,4,6]  d) Error

### 💪 Mini Exercise - Chapter 2

**Latihan 1:** Buat program manajemen daftar belanja:
```python
belanja = []
# Tambahkan 5 item
# Hapus 1 item  
# Tampilkan jumlah item
# Cek apakah "susu" ada dalam daftar
```

**Latihan 2:** Analisis nilai siswa:
```python
nilai = [85, 92, 78, 96, 88, 75, 90]
# Hitung rata-rata
# Cari nilai tertinggi dan terendah
# Hitung jumlah siswa yang lulus (>= 80)
```

**Latihan 3:** List comprehension challenge:
```python
angka = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
# Buat list bilangan genap saja
# Buat list kuadrat dari bilangan ganjil
# Buat list string "genap" atau "ganjil" untuk setiap angka
```

**Jawaban Mini Quiz:**
1. b) pisang
2. b) append()
3. b) [1,4,9]

---

## CHAPTER 3: STRUKTUR DATA - DICTIONARIES

### 3.1 Pengenalan Dictionary

Dictionary adalah struktur data key-value yang sangat berguna:

```python
# Membuat dictionary
mahasiswa = {
    "nama": "Ahmad Fauzi",
    "nim": "12345",
    "jurusan": "Teknik Informatika",
    "ipk": 3.75
}

# Dictionary kosong
data = {}
info = dict()

print(f"Data mahasiswa: {mahasiswa}")
print(f"Nama: {mahasiswa['nama']}")
```

### 3.2 Mengakses dan Memodifikasi Dictionary

```python
produk = {
    "nama": "Laptop Gaming",
    "harga": 15000000,
    "brand": "ASUS",
    "stok": 5
}

# Akses nilai
print(f"Harga: Rp {produk['harga']:,}")
print(f"Brand: {produk.get('brand', 'Unknown')}")

# Menambah/mengubah
produk["kategori"] = "Elektronik"
produk["harga"] = 14500000  # Update harga

# Menghapus
del produk["stok"]
removed = produk.pop("kategori", "Tidak ada")

print(f"Produk: {produk}")
```

### 3.3 Operasi Dictionary Lanjutan

```python
inventory = {
    "laptop": 10,
    "mouse": 25,
    "keyboard": 15,
    "monitor": 8
}

# Iterasi
print("=== Inventory ===")
for item, jumlah in inventory.items():
    print(f"{item.capitalize()}: {jumlah} unit")

# Keys dan values
print(f"Items: {list(inventory.keys())}")
print(f"Quantities: {list(inventory.values())}")

# Merge dictionaries
inventory_tambahan = {"webcam": 12, "speaker": 20}
inventory.update(inventory_tambahan)

print(f"Inventory lengkap: {inventory}")
```

### 3.4 Dictionary Comprehension

```python
# Dictionary comprehension
angka = [1, 2, 3, 4, 5]

# Angka dan kuadratnya
kuadrat_dict = {x: x**2 for x in angka}
print(f"Kuadrat: {kuadrat_dict}")

# Dengan kondisi
genap_kuadrat = {x: x**2 for x in angka if x % 2 == 0}
print(f"Kuadrat genap: {genap_kuadrat}")

# Dari list ke dictionary
nama_list = ["Ahmad", "Budi", "Citra"]
panjang_nama = {nama: len(nama) for nama in nama_list}
print(f"Panjang nama: {panjang_nama}")

# Nested dictionary
mahasiswa_data = {
    f"mhs_{i}": {"nama": f"Mahasiswa {i}", "nilai": i * 20}
    for i in range(1, 6)
}
print(f"Data mahasiswa: {mahasiswa_data}")
```

### 🧠 Mini Quiz - Chapter 3

**Soal 1:** Bagaimana cara mengakses nilai dengan key "nama" dari dict `data`?
a) data.nama  b) data["nama"]  c) data(nama)  d) data->nama

**Soal 2:** Method apa yang mengembalikan semua keys dari dictionary?
a) keys()  b) getkeys()  c) allkeys()  d) listkeys()

**Soal 3:** Apa yang terjadi jika mengakses key yang tidak ada tanpa default?
a) Mengembalikan None  b) Mengembalikan ""  c) KeyError  d) Mengembalikan 0

### 💪 Mini Exercise - Chapter 3

**Latihan 1:** Sistem informasi mahasiswa:
```python
mahasiswa = {
    "nama": "Andi",
    "nim": "12345",
    "jurusan": "Informatika",
    "ipk": 3.75
}
# Tambahkan field "semester"
# Ubah IPK menjadi 3.80
# Tampilkan semua informasi
```

**Latihan 2:** Kamus Bahasa Inggris-Indonesia:
```python
kamus = {
    "hello": "halo",
    "world": "dunia", 
    "python": "python"
}
# Tambahkan 3 kata baru
# Buat function untuk translate
# Test dengan beberapa kata
```

**Latihan 3:** Analisis data penjualan:
```python
penjualan = {
    "januari": 1500000,
    "februari": 1800000,
    "maret": 1650000
}
# Hitung total penjualan
# Cari bulan dengan penjualan tertinggi
# Hitung rata-rata penjualan
```

**Jawaban Mini Quiz:**
1. b) data["nama"]
2. a) keys()
3. c) KeyError

---

## CHAPTER 4: STRUKTUR DATA - TUPLES

### 4.1 Pengenalan Tuple

Tuple adalah struktur data yang immutable (tidak bisa diubah):

```python
# Membuat tuple
koordinat = (3, 4)
warna_rgb = (255, 128, 0)
data_siswa = ("Ahmad", 17, "XII-A", True)

# Tuple dengan satu elemen (perlu koma)
single_tuple = (42,)
not_tuple = (42)  # Ini integer, bukan tuple

print(f"Koordinat: {koordinat}")
print(f"Type: {type(koordinat)}")
print(f"Single tuple: {single_tuple}, Type: {type(single_tuple)}")
```

### 4.2 Operasi pada Tuple

```python
point = (10, 20, 30)

# Akses elemen (sama seperti list)
print(f"X: {point[0]}, Y: {point[1]}, Z: {point[2]}")

# Slicing
print(f"XY: {point[:2]}")
print(f"YZ: {point[1:]}")

# Tuple methods (terbatas)
angka_tuple = (1, 2, 3, 2, 4, 2, 5)
print(f"Count of 2: {angka_tuple.count(2)}")
print(f"Index of 3: {angka_tuple.index(3)}")

# Panjang tuple
print(f"Length: {len(point)}")
```

### 4.3 Unpacking Tuple

```python
# Tuple unpacking
person = ("Alice", 25, "Engineer")
nama, umur, pekerjaan = person

print(f"Nama: {nama}")
print(f"Umur: {umur}")
print(f"Pekerjaan: {pekerjaan}")

# Swap variables menggunakan tuple
a = 10
b = 20
print(f"Sebelum: a={a}, b={b}")

a, b = b, a  # Swap
print(f"Sesudah: a={a}, b={b}")

# Multiple return values
def get_name_age():
    return "Bob", 30

nama, umur = get_name_age()
print(f"Dari function: {nama}, {umur}")
```

### 4.4 Tuple sebagai Key Dictionary

```python
# Tuple bisa digunakan sebagai key (karena immutable)
lokasi_suhu = {
    (0, 0): 25.5,
    (10, 10): 23.2,
    (20, 20): 27.8
}

print("=== Data Suhu Berdasarkan Koordinat ===")
for koordinat, suhu in lokasi_suhu.items():
    x, y = koordinat
    print(f"Lokasi ({x}, {y}): {suhu}°C")

# Menambah data baru
lokasi_suhu[(5, 5)] = 24.1
lokasi_suhu[(15, 15)] = 26.3

# Tidak bisa pakai list sebagai key (error)
# data = {[1, 2]: "value"}  # TypeError!
```

### 🧠 Mini Quiz - Chapter 4

**Soal 1:** Perbedaan utama tuple dengan list adalah:
a) Tuple bisa diubah  b) Tuple tidak bisa diubah  c) Tuple hanya untuk angka  d) Tidak ada perbedaan

**Soal 2:** Bagaimana cara membuat tuple dengan satu elemen?
a) (5)  b) (5,)  c) [5]  d) {5}

**Soal 3:** Operasi apa yang TIDAK bisa dilakukan pada tuple?
a) Indexing  b) Slicing  c) append()  d) len()

### 💪 Mini Exercise - Chapter 4

**Latihan 1:** Koordinat dan jarak:
```python
# Buat tuple untuk menyimpan koordinat (x, y)
titik_a = (3, 4)
titik_b = (6, 8)
# Hitung jarak antara kedua titik
# Tampilkan koordinat dengan format yang rapi
```

**Latihan 2:** Data RGB warna:
```python
warna = {
    "merah": (255, 0, 0),
    "hijau": (0, 255, 0),
    "biru": (0, 0, 255)
}
# Tambahkan warna "kuning", "ungu", "orange"
# Buat function untuk mengecek apakah warna valid (0-255)
```

**Latihan 3:** Unpacking dan packing:
```python
data_siswa = ("Ahmad", 16, "X-1", 85.5)
# Unpack ke variabel terpisah
# Buat tuple baru dengan menambah informasi "hobi"
# Gunakan tuple sebagai return value dari function
```

**Jawaban Mini Quiz:**
1. b) Tuple tidak bisa diubah
2. b) (5,)
3. c) append()

---

## CHAPTER 5: KOMBINASI STRUKTUR DATA

### 5.1 Nested Structures

```python
# List of dictionaries
mahasiswa = [
    {"nama": "Ahmad", "nilai": 85, "mata_kuliah": ["Python", "Java"]},
    {"nama": "Budi", "nilai": 90, "mata_kuliah": ["Python", "C++"]},
    {"nama": "Citra", "nilai": 78, "mata_kuliah": ["Java", "JavaScript"]}
]

print("=== Data Mahasiswa ===")
for mhs in mahasiswa:
    print(f"{mhs['nama']}: {mhs['nilai']} - {', '.join(mhs['mata_kuliah'])}")

# Dictionary of lists
nilai_per_mata_kuliah = {
    "Python": [85, 90, 78, 92],
    "Java": [88, 76, 85, 89],
    "C++": [82, 95, 71, 87]
}

for mk, nilai_list in nilai_per_mata_kuliah.items():
    rata_rata = sum(nilai_list) / len(nilai_list)
    print(f"{mk}: rata-rata {rata_rata:.1f}")
```

### 5.2 Practical Examples

```python
# Sistem manajemen inventori
inventori = {
    "laptop": {
        "stok": 15,
        "harga": 12000000,
        "kategori": "elektronik",
        "supplier": ["PT A", "PT B"]
    },
    "mouse": {
        "stok": 50,
        "harga": 150000,
        "kategori": "aksesoris",
        "supplier": ["PT C"]
    }
}

def tampilkan_inventori(data):
    """Menampilkan inventori dengan format rapi"""
    print("=== INVENTORI TOKO ===")
    total_nilai = 0
    
    for produk, info in data.items():
        nilai_stok = info["stok"] * info["harga"]
        total_nilai += nilai_stok
        
        print(f"\n{produk.upper()}:")
        print(f"  Stok: {info['stok']} unit")
        print(f"  Harga: Rp {info['harga']:,}")
        print(f"  Nilai total: Rp {nilai_stok:,}")
        print(f"  Supplier: {', '.join(info['supplier'])}")
    
    print(f"\nTOTAL NILAI INVENTORI: Rp {total_nilai:,}")

tampilkan_inventori(inventori)
```

### 5.3 Data Processing dengan Struktur Gabungan

```python
# Dataset penjualan
penjualan_data = [
    {"tanggal": "2024-01-01", "produk": "laptop", "jumlah": 2, "harga": 12000000},
    {"tanggal": "2024-01-01", "produk": "mouse", "jumlah": 5, "harga": 150000},
    {"tanggal": "2024-01-02", "produk": "laptop", "jumlah": 1, "harga": 12000000},
    {"tanggal": "2024-01-02", "produk": "keyboard", "jumlah": 3, "harga": 500000},
]

def analisis_penjualan(data):
    """Analisis data penjualan"""
    # Group by produk
    penjualan_per_produk = {}
    total_pendapatan = 0
    
    for transaksi in data:
        produk = transaksi["produk"]
        jumlah = transaksi["jumlah"]
        harga = transaksi["harga"]
        pendapatan = jumlah * harga
        
        if produk not in penjualan_per_produk:
            penjualan_per_produk[produk] = {
                "total_unit": 0,
                "total_pendapatan": 0
            }
        
        penjualan_per_produk[produk]["total_unit"] += jumlah
        penjualan_per_produk[produk]["total_pendapatan"] += pendapatan
        total_pendapatan += pendapatan
    
    # Tampilkan hasil
    print("=== ANALISIS PENJUALAN ===")
    for produk, data in penjualan_per_produk.items():
        print(f"{produk.capitalize()}:")
        print(f"  Total unit terjual: {data['total_unit']}")
        print(f"  Total pendapatan: Rp {data['total_pendapatan']:,}")
    
    print(f"\nTOTAL PENDAPATAN: Rp {total_pendapatan:,}")
    
    # Produk terlaris
    terlaris = max(penjualan_per_produk.items(), 
                   key=lambda x: x[1]['total_unit'])
    print(f"PRODUK TERLARIS: {terlaris[0].capitalize()} ({terlaris[1]['total_unit']} unit)")

analisis_penjualan(penjualan_data)
```

### 🧠 Mini Quiz - Chapter 5

**Soal 1:** Bagaimana cara mengakses elemen kedua dari list pertama dalam nested structure `data = [[1,2,3], [4,5,6]]`?
a) data[0][1]  b) data[1][0]  c) data[0,1]  d) data.get(0,1)

**Soal 2:** Struktur data apa yang paling cocok untuk menyimpan informasi mahasiswa dengan berbagai atribut?
a) List  b) Tuple  c) Dictionary  d) Set

**Soal 3:** Dalam list of dictionaries, bagaimana cara mencari semua item dengan kondisi tertentu?
a) Menggunakan for loop  b) List comprehension  c) Filter function  d) Semua benar

### 💪 Mini Exercise - Chapter 5

**Latihan 1:** Sistem nilai mahasiswa:
```python
# Buat struktur data untuk menyimpan:
# - Nama mahasiswa
# - Mata kuliah yang diambil
# - Nilai per mata kuliah
# Hitung IPK masing-masing mahasiswa
```

**Latihan 2:** Analisis data cuaca:
```python
cuaca_data = [
    {"tanggal": "2024-01-01", "suhu": 28, "kelembaban": 80, "hujan": False},
    {"tanggal": "2024-01-02", "suhu": 30, "kelembaban": 75, "hujan": True},
    # tambahkan data lebih banyak
]
# Hitung rata-rata suhu
# Hitung jumlah hari hujan
# Cari hari dengan suhu tertinggi
```

**Jawaban Mini Quiz:**
1. a) data[0][1]
2. c) Dictionary
3. d) Semua benar

---

## LATIHAN DAN QUIZ

### Quiz Pilihan Ganda

1. Manakah yang bukan tipe data primitif di Python?
   a) int  b) str  c) list  d) bool

2. Apa output dari: `print(type(5/2))`?
   a) <class 'int'>  b) <class 'float'>  c) <class 'str'>  d) Error

3. Bagaimana cara menambah elemen ke akhir list?
   a) list.add()  b) list.append()  c) list.push()  d) list.insert()

4. Method apa yang mengembalikan keys dari dictionary?
   a) getkeys()  b) keys()  c) allkeys()  d) listkeys()

5. Perbedaan utama tuple dan list adalah:
   a) Tuple lebih cepat  b) Tuple immutable  c) Tuple hanya angka  d) Tidak ada bedanya

### Latihan Praktik

**Latihan 1: Program Biodata**
Buat program yang meminta input biodata lengkap dan simpan dalam dictionary.

**Latihan 2: Analisis Data Siswa**
Buat program untuk mengelola data nilai siswa dengan berbagai mata pelajaran.

**Latihan 3: Sistem Inventori Sederhana**
Buat program inventori toko menggunakan kombinasi struktur data.

### Kunci Jawaban Quiz
1. c) list
2. b) <class 'float'>
3. b) list.append()
4. b) keys()
5. b) Tuple immutable

---

## RANGKUMAN MODUL 1

Dalam modul ini kita telah mempelajari:

### Konsep Utama:
1. **Tipe Data Dasar**: int, float, string, boolean
2. **List**: Struktur data berurutan yang mutable
3. **Dictionary**: Struktur data key-value
4. **Tuple**: Struktur data immutable
5. **Kombinasi Struktur**: Nested data structures

### Skill yang Dikuasai:
- Manipulasi berbagai tipe data
- Operasi pada list, dictionary, dan tuple
- List/Dictionary comprehension
- Bekerja dengan nested structures
- Problem solving dengan struktur data yang tepat

### Persiapan untuk Modul 2:
Modul berikutnya akan membahas functions, control flow, dan I/O operations yang akan memanfaatkan pemahaman struktur data dari modul ini.
