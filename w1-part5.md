# MODUL 5: LATIHAN PROBLEM SOLVING DENGAN PYTHON 

## Pendahuluan

Modul ini dirancang untuk mengasah keterampilan problem solving melalui serangkaian latihan bertingkat. Soal-soal disusun mulai dari dasar hingga menantang, menekankan penerapan algoritma dan praktik pemrograman Python yang baik. Setiap level menyertakan deskripsi, spesifikasi input-output, contoh test case, dan solusi Python yang idiomatik.

---

## Tujuan Pembelajaran

Setelah menyelesaikan modul ini, mahasiswa diharapkan mampu:
- Menganalisis dan memformalkan masalah menjadi spesifikasi yang jelas
- Merancang solusi algoritmik yang efektif dan efisien
- Mengimplementasikan solusi Python yang bersih, teruji, dan terukur
- Mengevaluasi kompleksitas dan melakukan optimisasi sederhana

---

## Level 1: Basic Problems

### Soal 1: FizzBuzz Variasi
Deskripsi: Cetak daftar string dari 1..n. Ganti kelipatan 3 dengan "Fizz", kelipatan 5 dengan "Buzz", dan kelipatan 3 dan 5 dengan "FizzBuzz". Selain itu, untuk bilangan genap yang bukan kelipatan 2 dan 5, tambahkan akhiran "!".

Spesifikasi:
- Input: integer n (1 ≤ n ≤ 10_000)
- Output: list of strings

Contoh:
- Input: 6 → ["1", "2!", "Fizz", "4!", "Buzz", "Fizz!"]

Solusi:
```python
def fizzbuzz_var(n: int) -> list[str]:
    out = []
    for i in range(1, n + 1):
        s = ""
        if i % 3 == 0: s += "Fizz"
        if i % 5 == 0: s += "Buzz"
        if not s:
            s = str(i)
        if i % 2 == 0 and i % 5 != 0:
            s += "!"
        out.append(s)
    return out

# Tests
assert fizzbuzz_var(6) == ["1", "2!", "Fizz", "4!", "Buzz", "Fizz!"]
```

### Soal 2: Hitung Huruf dan Angka
Deskripsi: Diberikan string s, hitung jumlah karakter alfabet (a-z, A-Z) dan digit (0-9).

Spesifikasi:
- Input: string s
- Output: tuple (jumlah_huruf, jumlah_digit)

Contoh: "abc123!" → (3, 3)

Solusi:
```python
def count_alpha_digit(s: str) -> tuple[int, int]:
    letters = sum(ch.isalpha() for ch in s)
    digits = sum(ch.isdigit() for ch in s)
    return letters, digits

assert count_alpha_digit("abc123!") == (3, 3)
```

---

## Level 2: Intermediate

### Soal 1: Kompresi Run-Length Encoding (RLE)
Deskripsi: Implementasikan RLE sederhana. Misal: "aaabbc" → "a3b2c1".

Spesifikasi:
- Input: string s (non-empty)
- Output: string terkompresi

Solusi:
```python
def rle_encode(s: str) -> str:
    if not s:
        return ""
    out = []
    prev = s[0]
    cnt = 1
    for ch in s[1:]:
        if ch == prev:
            cnt += 1
        else:
            out.append(f"{prev}{cnt}")
            prev, cnt = ch, 1
    out.append(f"{prev}{cnt}")
    return "".join(out)

assert rle_encode("aaabbc") == "a3b2c1"
```

### Soal 2: Normalisasi Kalimat (Title Case dengan Aturan)
Deskripsi: Ubah kalimat ke Title Case, tetapi abaikan kata hubung (di, ke, dari, dan) kecuali jika di awal.

Solusi:
```python
def smart_title(s: str) -> str:
    stop = {"di", "ke", "dari", "dan"}
    words = s.lower().split()
    out = []
    for i, w in enumerate(words):
        if i > 0 and w in stop:
            out.append(w)
        else:
            out.append(w.capitalize())
    return " ".join(out)

assert smart_title("belajar python di kampus dan rumah") == "Belajar Python di Kampus dan Rumah"
```

---

## Level 3: Algorithmic Challenge

### Soal 1: Binary Search
Deskripsi: Implementasikan binary search pada list terurut. Kembalikan index jika ditemukan, -1 jika tidak.

Solusi:
```python
def binary_search(arr: list[int], target: int) -> int:
    l, r = 0, len(arr) - 1
    while l <= r:
        m = (l + r) // 2
        if arr[m] == target:
            return m
        if arr[m] < target:
            l = m + 1
        else:
            r = m - 1
    return -1

assert binary_search([1,3,5,7,9], 7) == 3
assert binary_search([1,3,5,7,9], 2) == -1
```

### Soal 2: Sorting Stabil Sederhana (Insertion Sort)
Deskripsi: Urutkan list angka menggunakan insertion sort (stabil). Kembalikan list baru.

Solusi:
```python
def insertion_sort(a: list[int]) -> list[int]:
    arr = a[:]  # copy
    for i in range(1, len(arr)):
        key = arr[i]
        j = i - 1
        while j >= 0 and arr[j] > key:
            arr[j + 1] = arr[j]
            j -= 1
        arr[j + 1] = key
    return arr

assert insertion_sort([3,1,2]) == [1,2,3]
```

---

## Level 4: Advanced

### Soal 1: Generate Kombinasi (Backtracking)
Deskripsi: Diberikan list unik `nums` dan integer `k`, hasilkan semua kombinasi berukuran `k` dalam urutan leksikografis.

Solusi:
```python
def combinations(nums: list[int], k: int) -> list[list[int]]:
    nums = sorted(nums)
    res = []
    path = []

    def backtrack(start: int):
        if len(path) == k:
            res.append(path[:])
            return
        for i in range(start, len(nums)):
            path.append(nums[i])
            backtrack(i + 1)
            path.pop()

    backtrack(0)
    return res

assert combinations([1,2,3], 2) == [[1,2],[1,3],[2,3]]
```

### Soal 2: Evaluasi Ekspresi Aritmetika Sederhana
Deskripsi: Evaluasi string ekspresi berisi non-negative integers, '+', '-', dan spasi. Contoh: "1 + 2 - 3 + 4" → 4.

Solusi:
```python
def eval_simple(expr: str) -> int:
    total = 0
    num = 0
    sign = 1
    s = expr + "+"  # sentinel
    for ch in s:
        if ch.isdigit():
            num = num * 10 + int(ch)
        elif ch in "+-":
            total += sign * num
            num = 0
            sign = 1 if ch == "+" else -1
        else:
            # spasi atau karakter lain diabaikan untuk kesederhanaan
            pass
    return total

assert eval_simple("1 + 2 - 3 + 4") == 4
```

---

## Level 5: Expert

### Soal 1: Optimisasi Rute Kurir (Greedy + Heuristik)
Deskripsi: Diberikan koordinat depot (0,0) dan daftar titik pengantaran (x,y). Cari urutan kunjungan dengan heuristik "nearest neighbor" lalu estimasi total jarak, kembali ke depot.

Spesifikasi:
- Input: list of tuples koordinat
- Output: (urutan_kunjungan, total_jarak)

Solusi:
```python
import math

def nearest_neighbor_route(points: list[tuple[float, float]]):
    if not points:
        return [], 0.0
    unvisited = points[:]
    route = []
    cur = (0.0, 0.0)
    total = 0.0

    def dist(a, b):
        return math.hypot(a[0]-b[0], a[1]-b[1])

    while unvisited:
        nxt = min(unvisited, key=lambda p: dist(cur, p))
        total += dist(cur, nxt)
        route.append(nxt)
        cur = nxt
        unvisited.remove(nxt)
    total += dist(cur, (0.0, 0.0))
    return route, total

# Contoh uji sederhana
pts = [(1,0), (1,1), (2,1)]
route, total = nearest_neighbor_route(pts)
assert set(route) == set(pts)
```

### Soal 2: Pipeline Data Mini (Multi-langkah)
Deskripsi: Bangun pipeline yang menerima list transaksi (type: "income"/"expense", amount) lalu:
1) Validasi amount > 0 dan type valid
2) Hitung total income, total expense, dan net = income - expense
3) Kelompokkan expense berdasarkan pembulatan ratusan (0-99 → 0, 100-199 → 100, dst.) dan hitung frekuensi

Solusi:
```python
from collections import Counter
from typing import Iterable, Dict, Any

def summarize_transactions(transactions: Iterable[Dict[str, Any]]) -> Dict[str, Any]:
    income = 0.0
    expense = 0.0
    buckets = Counter()

    for tx in transactions:
        t = tx.get("type")
        amt = tx.get("amount", 0)
        if t not in {"income", "expense"} or not isinstance(amt, (int, float)) or amt <= 0:
            # invalid, skip atau bisa raise
            continue
        if t == "income":
            income += amt
        else:
            expense += amt
            bucket = int(amt) // 100 * 100
            buckets[bucket] += 1

    return {
        "income": income,
        "expense": expense,
        "net": income - expense,
        "expense_buckets": dict(sorted(buckets.items()))
    }

data = [
    {"type": "income", "amount": 1000},
    {"type": "expense", "amount": 120},
    {"type": "expense", "amount": 80},
    {"type": "income", "amount": 500},
]

res = summarize_transactions(data)
assert res["income"] == 1500
assert res["expense"] == 200
assert res["net"] == 1300
```

---

## HOTS (Analyze–Evaluate–Create)

1) Analisis kompleksitas waktu dan memori untuk setiap solusi di atas. Mana yang bisa dioptimalkan?
2) Evaluasi: untuk data besar, kapan Anda beralih dari insertion sort ke algoritma lain (mis. Timsort/merge sort)? Jelaskan.
3) Kreasi: rancang problem baru bertema data real (mis. log server, transaksi) lengkap dengan spesifikasi, contoh uji, dan solusi baseline.

---

## Kesimpulan

Latihan bertingkat membantu memperkuat pemahaman dan meningkatkan ketangkasan algoritmik. Dengan membiasakan diri menulis solusi yang bersih, teruji, dan mempertimbangkan kompleksitas, Anda akan lebih siap menghadapi tantangan pengembangan perangkat lunak di dunia nyata.
