# MODUL 4: MERANCANG ALGORITMA DENGAN PSEUDOCODE DAN MENERJEMAHKANNYA KE PYTHON

## Pendahuluan

Algoritma adalah urutan langkah logis dan terstruktur untuk memecahkan masalah. Dalam praktik pemrograman, penulisan algoritma sering diawali dalam bentuk pseudocode (kode semu) yang independen dari bahasa pemrograman. Pseudocode membantu kita fokus pada logika sebelum menerjemahkannya ke dalam kode Python yang berjalan.

---

## Tujuan Pembelajaran

Setelah menyelesaikan modul ini, mahasiswa diharapkan mampu:
- Memahami konsep algoritma dan alur logika (sequence, selection, iteration)
- Menuliskan algoritma dalam bentuk pseudocode yang jelas dan konsisten
- Menerjemahkan pseudocode menjadi program Python yang benar dan dapat dijalankan
- Menguji dan memverifikasi program terhadap berbagai skenario input (termasuk edge cases)

---

## Materi Utama

### 1. Konsep Algoritma & Alur Logika

- Sequence (urutan): Langkah dieksekusi satu per satu dari atas ke bawah.
- Selection (pemilihan): Menggunakan kondisi (if/elif/else) untuk memilih jalur eksekusi.
- Iteration (pengulangan): Mengulang langkah (for/while) hingga kondisi terpenuhi.
- Abstraksi: Pecah masalah besar menjadi sub-masalah (fungsi/prosedur).

Contoh alur sederhana (narasi):
1) Baca tiga angka a, b, c
2) Hitung rata-rata = (a+b+c)/3
3) Tampilkan hasil

### 2. Pseudocode: Format, Notasi, Contoh

Tidak ada standar baku tunggal, namun konsistensi penting. Contoh notasi yang dipakai di modul ini:
- Assignment: SET total ← 0
- Input/Output: READ n, PRINT "Hasil"
- Seleksi: IF … THEN … ELSE … ENDIF
- Perulangan: FOR i FROM 1 TO n DO … ENDFOR, WHILE kondisi DO … ENDWHILE
- Fungsi/Prosedur: FUNCTION nama(param) … RETURN nilai, PROCEDURE nama(param) … ENDPROC

Contoh pseudocode menghitung jumlah bilangan genap dari 1..n:

```
READ n
SET sum_even ← 0
FOR i FROM 1 TO n DO
    IF i MOD 2 = 0 THEN
        sum_even ← sum_even + i
    ENDIF
ENDFOR
PRINT sum_even
```

### 3. Studi Kasus: Pseudocode untuk Masalah Nyata

Kasus A: Rata-rata nilai dan kategori grade

Deskripsi: Diberikan daftar nilai 0–100, hitung rata-rata dan tentukan grade (A/B/C/D/E).

Pseudocode:
```
READ k (jumlah nilai)
SET total ← 0
FOR i FROM 1 TO k DO
    READ nilai
    total ← total + nilai
ENDFOR
SET avg ← total / k
IF avg ≥ 90 THEN grade ← "A"
ELSEIF avg ≥ 80 THEN grade ← "B"
ELSEIF avg ≥ 70 THEN grade ← "C"
ELSEIF avg ≥ 60 THEN grade ← "D"
ELSE grade ← "E"
PRINT avg, grade
```

Kasus B: Validasi password sederhana

Aturan: minimal 8 karakter, mengandung huruf dan angka.

Pseudocode:
```
READ password
IF LENGTH(password) < 8 THEN
    PRINT "invalid"
ELSEIF NOT (containsLetter(password) AND containsDigit(password)) THEN
    PRINT "invalid"
ELSE
    PRINT "valid"
ENDIF
```

### 4. Translasi Pseudocode ke Python (Dengan Contoh)

Contoh 1: Jumlah bilangan genap 1..n

Pseudocode (ringkas): 
```
READ n
SET sum_even ← 0
FOR i FROM 1 TO n DO
    IF i MOD 2 = 0 THEN
        sum_even ← sum_even + i
    ENDIF
ENDFOR
PRINT sum_even
```

Python:
```python
def sum_even(n: int) -> int:
    total = 0
    for i in range(1, n + 1):
        if i % 2 == 0:
            total += i
    return total

print(sum_even(10))  # 2+4+6+8+10 = 30
```

Contoh 2: Rata-rata nilai dan grade

Pseudocode:
```
READ k (jumlah nilai)
SET total ← 0
FOR i FROM 1 TO k DO
    READ nilai
    total ← total + nilai
ENDFOR
SET avg ← total / k
IF avg ≥ 90 THEN grade ← "A"
ELSEIF avg ≥ 80 THEN grade ← "B"
ELSEIF avg ≥ 70 THEN grade ← "C"
ELSEIF avg ≥ 60 THEN grade ← "D"
ELSE grade ← "E"
PRINT avg, grade
```

Python:
```python
from typing import List, Tuple

def hitung_rerata_dan_grade(nilai: List[float]) -> Tuple[float, str]:
    k = len(nilai)
    if k == 0:
        return 0.0, "E"
    avg = sum(nilai) / k
    if avg >= 90: grade = "A"
    elif avg >= 80: grade = "B"
    elif avg >= 70: grade = "C"
    elif avg >= 60: grade = "D"
    else: grade = "E"
    return avg, grade

print(hitung_rerata_dan_grade([80, 90, 100]))  # (90.0, 'A')
```

Contoh 3: Validasi password sederhana

Pseudocode:
```
READ password
IF LENGTH(password) < 8 THEN
    PRINT "invalid"
ELSEIF NOT (containsLetter(password) AND containsDigit(password)) THEN
    PRINT "invalid"
ELSE
    PRINT "valid"
ENDIF
```

Python:
```python
def is_valid_password(pw: str) -> bool:
    if len(pw) < 8:
        return False
    has_letter = any(ch.isalpha() for ch in pw)
    has_digit = any(ch.isdigit() for ch in pw)
    return has_letter and has_digit

print(is_valid_password("abc12345"))  # True
print(is_valid_password("abcdefg"))   # False
```

---

## LOTS (Remember–Understand–Apply)

### Ringkasan Singkat
- Algoritma: urutan langkah logis (sequence, selection, iteration)
- Pseudocode: media mengekspresikan algoritma secara bahasa natural-teknis sebelum koding
- Translasi ke Python: fokus mapping struktur (IF/ELSE → if/elif/else, FOR/WHILE → for/while)

### Contoh Singkat
Pseudocode menghitung faktorial n:
```
READ n
SET result ← 1
FOR i FROM 1 TO n DO
    result ← result * i
ENDFOR
PRINT result
```
Python:
```python
def faktorial(n: int) -> int:
    result = 1
    for i in range(1, n + 1):
        result *= i
    return result
```

### 🧠 Mini Quiz (LOTS)
1) Pseudocode digunakan untuk…
   a) Mengoptimalkan kompilasi  b) Mendeskripsikan logika sebelum koding  c) Menulis komentar saja  d) Menguji performa

2) Struktur kontrol yang TIDAK termasuk iteration adalah…
   a) for  b) while  c) if  d) do-while

3) Translasi yang tepat: `IF x MOD 2 = 0 THEN PRINT "Genap"` →
   a) `if x % 2 == 0: print("Genap")`  b) `if x / 2 = 0: print("Genap")`  c) `if x % 2 = 0: print("Genap")`  d) `if x == 2 % 0: print("Genap")`

Kunci: 1) b, 2) c, 3) a

### 💪 Mini Exercise (LOTS)
1) Tulis pseudocode dan Python untuk menghitung jumlah bilangan kelipatan 3 atau 5 dari 1..n.
2) Tulis pseudocode dan Python untuk menghitung jumlah kata pada sebuah kalimat (dipisah spasi).
3) Tulis pseudocode dan Python untuk menentukan apakah sebuah angka adalah bilangan prima.

---

## HOTS (Analyze–Evaluate–Create)

### Studi Kasus Terpadu: Ringkasan Transaksi Harian

Masalah: Diberikan daftar transaksi penjualan (tanggal, kategori, jumlah, harga_satuan). Buat ringkasan per kategori: total_item, total_pendapatan, rata_rata_harga, serta temukan kategori terlaris. Tangani input kosong/invalid.

Langkah:
1) Tulis pseudocode terstruktur (fungsi-prosedur) untuk pipeline: validasi → agregasi → ringkasan → laporan.
2) Terjemahkan ke Python modular (fungsi kecil, docstring, type hints).
3) Uji dengan data: variasi kategori, data kosong, dan nilai negatif (tolak/skip dengan pesan).

Skeleton Pseudocode:
```
FUNCTION validate(tx)
    RETURN isValid(tx)

FUNCTION aggregate(transactions)
    INIT map kategori → {total_item, total_pendapatan, count}
    FOR setiap tx IN transactions DO
        IF validate(tx) THEN
            UPDATE agregat kategori
        ENDIF
    ENDFOR
    RETURN agregat

FUNCTION summarize(agregat)
    HITUNG rata_rata_harga per kategori
    TEMUKAN kategori terlaris berdasarkan total_item
    RETURN ringkasan
```

Pertimbangan Evaluasi:
- Kompleksitas waktu (O(n)) dan memori
- Keterbacaan dan modularitas
- Penanganan edge cases

---

## Kesimpulan

Pseudocode menjembatani ide ke implementasi. Dengan menguasai struktur dasar algoritma dan translasi yang konsisten ke Python, Anda dapat membangun solusi yang benar, teruji, dan mudah dirawat. Latihan terarah (LOTS → HOTS) memperkuat pemahaman sekaligus kemampuan analitis dan kreatif.
