# MODUL 3: MANAJEMEN FILE, MODUL, DAN TEKNIK LANJUTAN PYTHON
## Program Studi Teknik Informatika
### Mata Kuliah: Pemrograman Python

---

## DESKRIPSI MODUL

Modul ini membahas aspek lanjutan dalam pemrograman Python yang meliputi manajemen file, konsep modul dan package, serta teknik-teknik pemrograman lanjutan. Mahasiswa akan mempelajari cara membaca dan menulis file, membuat dan menggunakan modul, menangani error dengan exception handling, dan menerapkan teknik web scraping serta tips dan trik Python untuk pengembangan aplikasi yang lebih kompleks.

---

## CAPAIAN PEMBELAJARAN

### Capaian Pembelajaran Umum
Setelah menyelesaikan modul ini, mahasiswa diharapkan dapat:
1. Mengelola file dan direktori menggunakan Python
2. Membuat dan menggunakan modul untuk organisasi kode yang lebih baik
3. Menangani error dan exception dengan tepat
4. Mengimplementasikan teknik web scraping untuk mengambil data dari website
5. Menerapkan tips dan trik Python untuk meningkatkan efisiensi programming
6. Merancang aplikasi Python yang modular dan maintainable

### Pemetaan Capaian Pembelajaran Berdasarkan LOTS dan HOTS

#### LOTS (Lower Order Thinking Skills)
- **Remember (C1):** Mengingat sintaks file I/O, import statement, dan exception handling
- **Understand (C2):** Menjelaskan konsep modul, package, dan manajemen file
- **Apply (C3):** Menerapkan operasi file dan menggunakan modul built-in Python

#### HOTS (Higher Order Thinking Skills)
- **Analyze (C4):** Menganalisis struktur aplikasi dan membuat modul yang efisien
- **Evaluate (C5):** Mengevaluasi keamanan dan efisiensi dalam file handling dan web scraping
- **Create (C6):** Merancang aplikasi kompleks dengan arsitektur modular

---

## CHAPTER 1: MANAJEMEN FILE

### 1.1 Membaca File

Python menyediakan berbagai cara untuk membaca file dengan fungsi `open()`.

```python
# Membaca file teks sederhana
def baca_file_sederhana(nama_file):
    """Membaca seluruh isi file sekaligus"""
    try:
        with open(nama_file, 'r', encoding='utf-8') as file:
            isi = file.read()
            return isi
    except FileNotFoundError:
        return f"File {nama_file} tidak ditemukan"
    except Exception as e:
        return f"Error membaca file: {e}"

# Membaca file baris per baris
def baca_file_per_baris(nama_file):
    """Membaca file baris demi baris"""
    try:
        with open(nama_file, 'r', encoding='utf-8') as file:
            baris_list = []
            for nomor, baris in enumerate(file, 1):
                baris_list.append(f"Baris {nomor}: {baris.strip()}")
            return baris_list
    except FileNotFoundError:
        return [f"File {nama_file} tidak ditemukan"]

# Membaca file dengan readline()
def baca_beberapa_baris(nama_file, jumlah_baris=5):
    """Membaca beberapa baris pertama dari file"""
    try:
        with open(nama_file, 'r', encoding='utf-8') as file:
            baris_list = []
            for i in range(jumlah_baris):
                baris = file.readline()
                if not baris:  # Jika sudah mencapai akhir file
                    break
                baris_list.append(baris.strip())
            return baris_list
    except FileNotFoundError:
        return [f"File {nama_file} tidak ditemukan"]
```

### 1.2 Menulis File

Berbagai mode penulisan file untuk kebutuhan yang berbeda.

```python
# Menulis file baru (overwrite jika sudah ada)
def tulis_file_baru(nama_file, konten):
    """Menulis file baru atau menimpa file yang sudah ada"""
    try:
        with open(nama_file, 'w', encoding='utf-8') as file:
            file.write(konten)
        return f"Berhasil menulis ke file {nama_file}"
    except Exception as e:
        return f"Error menulis file: {e}"

# Menambah konten ke file yang sudah ada
def tambah_ke_file(nama_file, konten):
    """Menambahkan konten ke akhir file"""
    try:
        with open(nama_file, 'a', encoding='utf-8') as file:
            file.write(konten + '\n')
        return f"Berhasil menambah konten ke {nama_file}"
    except Exception as e:
        return f"Error menambah ke file: {e}"

# Menulis list ke file
def tulis_list_ke_file(nama_file, data_list):
    """Menulis setiap elemen list ke baris terpisah"""
    try:
        with open(nama_file, 'w', encoding='utf-8') as file:
            for item in data_list:
                file.write(str(item) + '\n')
        return f"Berhasil menulis {len(data_list)} item ke {nama_file}"
    except Exception as e:
        return f"Error menulis list ke file: {e}"

# Contoh penggunaan
data_mahasiswa = [
    "Ahmad Fauzi - 12345 - Teknik Informatika",
    "Siti Aminah - 67890 - Sistem Informasi", 
    "Budi Santoso - 11111 - Teknik Elektro"
]

print(tulis_list_ke_file("mahasiswa.txt", data_mahasiswa))
print(baca_file_per_baris("mahasiswa.txt"))
```

### 1.3 Operasi File Lanjutan

```python
import os
import shutil
from pathlib import Path

# Cek keberadaan file
def cek_file_ada(nama_file):
    """Mengecek apakah file atau direktori ada"""
    path = Path(nama_file)
    return {
        'ada': path.exists(),
        'adalah_file': path.is_file(),
        'adalah_direktori': path.is_dir(),
        'ukuran': path.stat().st_size if path.exists() else 0
    }

# Operasi file dan direktori
def operasi_file_direktori():
    """Demonstrasi berbagai operasi file dan direktori"""
    try:
        # Membuat direktori
        os.makedirs("data/backup", exist_ok=True)
        print("Direktori 'data/backup' dibuat")
        
        # Membuat file contoh
        with open("data/contoh.txt", "w") as f:
            f.write("Ini file contoh untuk operasi file")
        
        # Copy file
        shutil.copy("data/contoh.txt", "data/backup/contoh_backup.txt")
        print("File berhasil dicopy")
        
        # List file dalam direktori
        files = os.listdir("data")
        print(f"File dalam direktori 'data': {files}")
        
        # Rename file
        os.rename("data/contoh.txt", "data/contoh_renamed.txt")
        print("File berhasil di-rename")
        
        # Informasi file
        info = cek_file_ada("data/contoh_renamed.txt")
        print(f"Info file: {info}")
        
    except Exception as e:
        print(f"Error dalam operasi file: {e}")

# Membaca file CSV sederhana
def baca_csv_manual(nama_file, delimiter=','):
    """Membaca file CSV tanpa menggunakan library pandas"""
    try:
        data = []
        with open(nama_file, 'r', encoding='utf-8') as file:
            for baris in file:
                kolom = baris.strip().split(delimiter)
                data.append(kolom)
        return data
    except FileNotFoundError:
        return [["Error: File tidak ditemukan"]]
    except Exception as e:
        return [["Error:", str(e)]]

# Menulis file CSV sederhana
def tulis_csv_manual(nama_file, data, header=None, delimiter=','):
    """Menulis data ke file CSV"""
    try:
        with open(nama_file, 'w', encoding='utf-8') as file:
            if header:
                file.write(delimiter.join(header) + '\n')
            for baris in data:
                file.write(delimiter.join(map(str, baris)) + '\n')
        return f"Data berhasil ditulis ke {nama_file}"
    except Exception as e:
        return f"Error menulis CSV: {e}"

# Contoh data dan penggunaan CSV
data_nilai = [
    ["Ahmad", 85, 90, 78],
    ["Siti", 92, 88, 95],
    ["Budi", 78, 82, 85]
]
header = ["Nama", "Matematika", "Fisika", "Kimia"]

print(tulis_csv_manual("nilai.csv", data_nilai, header))
print(baca_csv_manual("nilai.csv"))
```

### 1.4 Working with Binary Files

```python
# Membaca dan menulis file binary
def copy_file_binary(source, destination):
    """Menyalin file dalam mode binary"""
    try:
        with open(source, 'rb') as src:
            with open(destination, 'wb') as dst:
                # Baca file dalam chunk untuk file besar
                chunk_size = 8192
                while True:
                    chunk = src.read(chunk_size)
                    if not chunk:
                        break
                    dst.write(chunk)
        return f"File berhasil dicopy dari {source} ke {destination}"
    except Exception as e:
        return f"Error copying file: {e}"

# Membaca informasi file
def info_file_detail(nama_file):
    """Mendapatkan informasi detail tentang file"""
    try:
        stat_info = os.stat(nama_file)
        return {
            'ukuran_bytes': stat_info.st_size,
            'waktu_modifikasi': stat_info.st_mtime,
            'waktu_akses': stat_info.st_atime,
            'mode': stat_info.st_mode,
            'readable': os.access(nama_file, os.R_OK),
            'writable': os.access(nama_file, os.W_OK),
            'executable': os.access(nama_file, os.X_OK)
        }
    except Exception as e:
        return f"Error getting file info: {e}"
```

 

## CHAPTER 2: TIPS DAN TRIK PYTHON

### 2.1 List Comprehensions Lanjutan

```python
# List comprehension dengan nested loops
def generate_coordinate_grid(max_x, max_y):
    """Generate koordinat grid menggunakan list comprehension"""
    coordinates = [(x, y) for x in range(max_x) for y in range(max_y)]
    return coordinates

# Dictionary comprehension
def buat_kamus_kuadrat(n):
    """Membuat dictionary dengan angka dan kuadratnya"""
    return {x: x**2 for x in range(1, n+1)}

# Set comprehension
def huruf_unik(kalimat):
    """Mendapatkan huruf unik dari kalimat"""
    return {char.lower() for char in kalimat if char.isalpha()}

# Generator expression untuk memory efficiency
def generate_fibonacci(n):
    """Generator untuk deret Fibonacci"""
    a, b = 0, 1
    for _ in range(n):
        yield a
        a, b = b, a + b

# Contoh penggunaan
print("Koordinat grid 3x3:")
print(generate_coordinate_grid(3, 3))

print("\nKamus kuadrat 1-10:")
print(buat_kamus_kuadrat(10))

print("\nHuruf unik dalam 'Hello World':")
print(huruf_unik("Hello World"))

print("\n10 angka Fibonacci pertama:")
for fib in generate_fibonacci(10):
    print(fib, end=" ")
print()
```

### 2.2 Built-in Functions yang Powerful

```python
# Menggunakan map, filter, dan reduce
from functools import reduce

def demo_functional_programming():
    """Demonstrasi functional programming di Python"""
    angka = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
    
    # Map: transformasi setiap elemen
    kuadrat = list(map(lambda x: x**2, angka))
    print(f"Kuadrat: {kuadrat}")
    
    # Filter: menyaring elemen berdasarkan kondisi
    genap = list(filter(lambda x: x % 2 == 0, angka))
    print(f"Genap: {genap}")
    
    # Reduce: menggabungkan elemen menjadi satu nilai
    jumlah = reduce(lambda x, y: x + y, angka)
    print(f"Jumlah: {jumlah}")
    
    # Kombinasi map dan filter
    kuadrat_genap = list(map(lambda x: x**2, filter(lambda x: x % 2 == 0, angka)))
    print(f"Kuadrat genap: {kuadrat_genap}")

# Zip untuk menggabungkan iterables
def demo_zip():
    """Demonstrasi penggunaan zip"""
    nama = ["Ahmad", "Siti", "Budi"]
    nilai = [85, 92, 78]
    jurusan = ["TI", "SI", "TE"]
    
    # Zip sederhana
    mahasiswa = list(zip(nama, nilai, jurusan))
    print("Data mahasiswa:")
    for mhs in mahasiswa:
        print(f"Nama: {mhs[0]}, Nilai: {mhs[1]}, Jurusan: {mhs[2]}")
    
    # Zip dengan unpacking
    print("\nDengan unpacking:")
    for n, nil, jur in zip(nama, nilai, jurusan):
        print(f"{n} - {jur}: {nil}")
    
    # Unzip
    data = [("A", 1), ("B", 2), ("C", 3)]
    huruf, angka = zip(*data)
    print(f"Huruf: {huruf}, Angka: {angka}")

# Enumerate untuk index dan value
def demo_enumerate():
    """Demonstrasi enumerate"""
    buah = ["apel", "mangga", "jeruk", "pisang"]
    
    # Enumerate biasa
    print("Dengan enumerate:")
    for i, buah_item in enumerate(buah):
        print(f"{i+1}. {buah_item}")
    
    # Enumerate dengan start
    print("\nDengan start=1:")
    for i, buah_item in enumerate(buah, start=1):
        print(f"{i}. {buah_item}")

demo_functional_programming()
print("\n" + "="*50 + "\n")
demo_zip()
print("\n" + "="*50 + "\n")
demo_enumerate()
```

### 2.3 String Manipulation Lanjutan

```python
# String formatting techniques
def demo_string_formatting():
    """Demonstrasi berbagai teknik formatting string"""
    nama = "Ahmad"
    umur = 25
    ipk = 3.75
    
    # f-strings (Python 3.6+)
    print(f"Nama: {nama}, Umur: {umur}, IPK: {ipk:.2f}")
    
    # format() method
    print("Nama: {}, Umur: {}, IPK: {:.2f}".format(nama, umur, ipk))
    
    # Named placeholders
    print("Nama: {name}, Umur: {age}, IPK: {gpa:.2f}".format(
        name=nama, age=umur, gpa=ipk))
    
    # % formatting (old style)
    print("Nama: %s, Umur: %d, IPK: %.2f" % (nama, umur, ipk))

# String methods yang berguna
def demo_string_methods():
    """Demonstrasi string methods"""
    text = "  Python Programming adalah Menyenangkan  "
    
    print(f"Original: '{text}'")
    print(f"Strip: '{text.strip()}'")
    print(f"Lower: '{text.lower()}'")
    print(f"Upper: '{text.upper()}'")
    print(f"Title: '{text.title()}'")
    print(f"Replace: '{text.replace('Programming', 'Coding')}'")
    
    # Split dan join
    words = text.strip().split()
    print(f"Words: {words}")
    print(f"Joined: '{'-'.join(words)}'")
    
    # String checking methods
    email = "user@example.com"
    print(f"\nEmail checks for '{email}':")
    print(f"Contains @: {'@' in email}")
    print(f"Starts with user: {email.startswith('user')}")
    print(f"Ends with .com: {email.endswith('.com')}")

# Regular expressions untuk pattern matching
import re

def demo_regex():
    """Demonstrasi regex untuk pattern matching"""
    text = "Telepon Ahmad: 081234567890, Email: ahmad@email.com"
    
    # Mencari nomor telepon
    phone_pattern = r'\b\d{12}\b'
    phones = re.findall(phone_pattern, text)
    print(f"Nomor telepon: {phones}")
    
    # Mencari email
    email_pattern = r'\b[A-Za-z0-9._%+-]+@[A-Za-z0-9.-]+\.[A-Z|a-z]{2,}\b'
    emails = re.findall(email_pattern, text)
     print(f"Email: {emails}")
    
demo_string_formatting()
print("\n" + "="*50 + "\n")
demo_string_methods()
print("\n" + "="*50 + "\n")
demo_regex()

### 🧠 Mini Quiz - Chapter 2 (Tips & Trik Python)

1) Apa hasil dari list(map(lambda x: x**2, filter(lambda x: x % 2 == 0, [1,2,3,4])))?
    a) [1,4,9,16]  b) [4,16]  c) [2,4]  d) [1,9]

2) Fungsi bawaan mana yang menggabungkan dua iterable menjadi pasangan (pair)?
    a) enumerate  b) zip  c) map  d) filter

3) Pada f-string f"{nilai:.2f}", .2f berarti:
    a) Lebar 2 karakter  b) 2 angka di depan koma  c) 2 angka di belakang koma  d) Bilangan bulat

Kunci: 1) b, 2) b, 3) c

### 💪 Mini Exercise - Chapter 2

- Tulis fungsi summarize_numbers(angka) yang mengembalikan dict: min, max, mean, even_sq (kuadrat bilangan genap) menggunakan map/filter/reduce.
- Buat fungsi sanitize_emails(teks) yang mengekstrak semua email valid dengan regex dan mengembalikannya unik (set → list terurut).
- Implementasikan enumerate_like(iterable, start=1) yang meniru enumerate hanya dengan range dan indexing.
    # Substitusi
    clean_text = re.sub(r'\d+', '[NUMBER]', text)
    print(f"Text with numbers replaced: {clean_text}")

demo_string_formatting()
print("\n" + "="*50 + "\n")
demo_string_methods()
print("\n" + "="*50 + "\n")
demo_regex()
```

### 2.4 Error Handling dan Debugging

```python
# Exception handling yang baik
def safe_divide(a, b):
    """Pembagian dengan error handling"""
    try:
        result = a / b
        return result
    except ZeroDivisionError:
        print("Error: Tidak bisa membagi dengan nol")
        return None
    except TypeError:
        print("Error: Input harus berupa angka")
        return None
    except Exception as e:
        print(f"Error tidak terduga: {e}")
        return None
    finally:
        print("Operasi pembagian selesai")

# Custom exceptions
class ValidationError(Exception):
    """Custom exception untuk validasi"""
    def __init__(self, message, field=None):
        self.message = message
        self.field = field
        super().__init__(self.message)

def validate_mahasiswa_data(nama, umur, ipk):
    """Validasi data mahasiswa dengan custom exception"""
    try:
        if not nama or len(nama.strip()) == 0:
            raise ValidationError("Nama tidak boleh kosong", "nama")
        
        if not isinstance(umur, int) or umur < 17 or umur > 30:
            raise ValidationError("Umur harus integer antara 17-30", "umur")
        
        if not isinstance(ipk, (int, float)) or ipk < 0 or ipk > 4:
            raise ValidationError("IPK harus angka antara 0-4", "ipk")
        
        return True
        
    except ValidationError as e:
        print(f"Validation Error in {e.field}: {e.message}")
        return False
    except Exception as e:
        print(f"Unexpected error: {e}")
        return False

# Context manager untuk resource management
class FileManager:
    """Context manager untuk file operations"""
    def __init__(self, filename, mode):
        self.filename = filename
        self.mode = mode
        self.file = None
    
    def __enter__(self):
        print(f"Opening file {self.filename}")
        self.file = open(self.filename, self.mode)
        return self.file
    
    def __exit__(self, exc_type, exc_val, exc_tb):
        print(f"Closing file {self.filename}")
        if self.file:
            self.file.close()
        if exc_type:
            print(f"Exception occurred: {exc_val}")
        return False  # Re-raise exception

# Menggunakan context manager
def demo_context_manager():
    """Demo penggunaan context manager"""
    try:
        with FileManager("test.txt", "w") as f:
            f.write("Hello, World!")
        print("File operation completed successfully")
    except Exception as e:
        print(f"Error in file operation: {e}")

# Testing
print("Testing safe_divide:")
print(safe_divide(10, 2))
print(safe_divide(10, 0))
print(safe_divide("10", 2))

print("\nTesting validation:")
validate_mahasiswa_data("Ahmad", 25, 3.75)
validate_mahasiswa_data("", 25, 3.75)
validate_mahasiswa_data("Ahmad", 35, 3.75)

print("\nTesting context manager:")
demo_context_manager()
```

---

## CHAPTER 3: WEB SCRAPING DASAR

### 3.1 Pengenalan Web Scraping

Web scraping adalah proses otomatis untuk mengekstrak data dari website. Python menyediakan berbagai library untuk web scraping.

```python
import requests
from bs4 import BeautifulSoup
import json
import time

# Basic HTTP requests
def simple_web_request(url):
    """Melakukan HTTP request sederhana"""
    try:
        response = requests.get(url)
        response.raise_for_status()  # Raise exception untuk status error
        
        return {
            'status_code': response.status_code,
            'content_type': response.headers.get('content-type'),
            'content_length': len(response.content),
            'content': response.text[:500] + "..." if len(response.text) > 500 else response.text
        }
    except requests.exceptions.RequestException as e:
        return {'error': str(e)}

# Web scraping dengan BeautifulSoup
def scrape_simple_data(url):
    """Scraping data sederhana dari website"""
    try:
        # Headers untuk menghindari blocking
        headers = {
            'User-Agent': 'Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36'
        }
        
        response = requests.get(url, headers=headers)
        response.raise_for_status()
        
        soup = BeautifulSoup(response.content, 'html.parser')
        
        # Extract basic information
        title = soup.find('title').text.strip() if soup.find('title') else "No title"
        
        # Find all links
        links = []
        for link in soup.find_all('a', href=True):
            links.append({
                'text': link.text.strip(),
                'url': link['href']
            })
        
        # Find all paragraphs
        paragraphs = [p.text.strip() for p in soup.find_all('p') if p.text.strip()]
        
        return {
            'title': title,
            'links_count': len(links),
            'links': links[:5],  # First 5 links
            'paragraphs_count': len(paragraphs),
            'first_paragraph': paragraphs[0] if paragraphs else "No paragraphs"
        }
        
    except Exception as e:
        return {'error': str(e)}

# Scraping with rate limiting
class WebScraper:
    """Class untuk web scraping dengan rate limiting"""
    
    def __init__(self, delay=1):
        self.delay = delay
        self.session = requests.Session()
        self.session.headers.update({
            'User-Agent': 'Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36'
        })
    
    def get_page(self, url):
        """Get single page with rate limiting"""
        try:
            time.sleep(self.delay)  # Rate limiting
            response = self.session.get(url)
            response.raise_for_status()
            return response
        except requests.exceptions.RequestException as e:
            print(f"Error fetching {url}: {e}")
            return None
    
    def scrape_multiple_pages(self, urls):
        """Scrape multiple pages with rate limiting"""
        results = []
        
        for i, url in enumerate(urls):
            print(f"Scraping page {i+1}/{len(urls)}: {url}")
            
            response = self.get_page(url)
            if response:
                soup = BeautifulSoup(response.content, 'html.parser')
                title = soup.find('title').text.strip() if soup.find('title') else "No title"
                
                results.append({
                    'url': url,
                    'title': title,
                    'status_code': response.status_code
                })
            else:
                results.append({
                    'url': url,
                    'title': 'Failed to scrape',
                    'status_code': None
                })
        
        return results

# API scraping
def scrape_json_api(api_url):
    """Scraping data dari JSON API"""
    try:
        response = requests.get(api_url)
        response.raise_for_status()
        
        data = response.json()
        return data
    except requests.exceptions.RequestException as e:
        return {'error': f'Request error: {e}'}
    except json.JSONDecodeError as e:
        return {'error': f'JSON decode error: {e}'}

# Example usage (commented out to avoid actual web requests in example)
"""
# Test simple request
print("Testing simple web request:")
result = simple_web_request("https://httpbin.org/html")
print(json.dumps(result, indent=2))

# Test scraping
print("\nTesting web scraping:")
scrape_result = scrape_simple_data("https://httpbin.org/html")
print(json.dumps(scrape_result, indent=2))

# Test JSON API
print("\nTesting JSON API:")
api_result = scrape_json_api("https://jsonplaceholder.typicode.com/posts/1")
print(json.dumps(api_result, indent=2))
"""
```

### 3.2 Web Scraping Best Practices

```python
import csv
from urllib.parse import urljoin, urlparse
from datetime import datetime

class EthicalWebScraper:
    """Web scraper dengan praktik ethical scraping"""
    
    def __init__(self, delay=1, respect_robots=True):
        self.delay = delay
        self.respect_robots = respect_robots
        self.session = requests.Session()
        self.session.headers.update({
            'User-Agent': 'Educational Web Scraper 1.0'
        })
        self.scraped_urls = set()
    
    def check_robots_txt(self, base_url):
        """Check robots.txt for scraping permissions"""
        if not self.respect_robots:
            return True
        
        try:
            robots_url = urljoin(base_url, '/robots.txt')
            response = self.session.get(robots_url)
            
            if response.status_code == 200:
                print(f"Found robots.txt: {robots_url}")
                print(response.text[:500] + "..." if len(response.text) > 500 else response.text)
                return True
            else:
                print(f"No robots.txt found at {robots_url}")
                return True
        except:
            print("Could not check robots.txt")
            return True
    
    def scrape_with_metadata(self, url):
        """Scrape page with metadata collection"""
        if url in self.scraped_urls:
            print(f"URL already scraped: {url}")
            return None
        
        try:
            time.sleep(self.delay)
            response = self.session.get(url)
            response.raise_for_status()
            
            soup = BeautifulSoup(response.content, 'html.parser')
            
            # Extract metadata
            metadata = {
                'url': url,
                'scraped_at': datetime.now().isoformat(),
                'status_code': response.status_code,
                'content_type': response.headers.get('content-type'),
                'title': soup.find('title').text.strip() if soup.find('title') else None,
                'meta_description': None,
                'h1_tags': [h1.text.strip() for h1 in soup.find_all('h1')],
                'links_count': len(soup.find_all('a')),
                'images_count': len(soup.find_all('img')),
                'word_count': len(soup.get_text().split())
            }
            
            # Extract meta description
            meta_desc = soup.find('meta', attrs={'name': 'description'})
            if meta_desc:
                metadata['meta_description'] = meta_desc.get('content')
            
            self.scraped_urls.add(url)
            return metadata
            
        except Exception as e:
            return {
                'url': url,
                'error': str(e),
                'scraped_at': datetime.now().isoformat()
            }
    
    def save_to_csv(self, data, filename):
        """Save scraped data to CSV file"""
        if not data:
            print("No data to save")
            return
        
        try:
            with open(filename, 'w', newline='', encoding='utf-8') as csvfile:
                fieldnames = data[0].keys()
                writer = csv.DictWriter(csvfile, fieldnames=fieldnames)
                
                writer.writeheader()
                for row in data:
                    writer.writerow(row)
                
                print(f"Data saved to {filename}")
        except Exception as e:
            print(f"Error saving to CSV: {e}")

# Data extraction utilities
def extract_table_data(soup, table_selector='table'):
    """Extract data from HTML tables"""
    tables = soup.select(table_selector)
    table_data = []
    
    for table in tables:
        rows = table.find_all('tr')
        if not rows:
            continue
        
        # Get headers
        headers = [th.text.strip() for th in rows[0].find_all(['th', 'td'])]
        
        # Get data rows
        for row in rows[1:]:
            cells = [td.text.strip() for td in row.find_all(['td', 'th'])]
            if len(cells) == len(headers):
                table_data.append(dict(zip(headers, cells)))
    
    return table_data

def extract_form_data(soup):
    """Extract form information"""
    forms = soup.find_all('form')
    form_data = []
    
    for form in forms:
        form_info = {
            'action': form.get('action', ''),
            'method': form.get('method', 'GET'),
            'inputs': []
        }
        
        inputs = form.find_all(['input', 'textarea', 'select'])
        for inp in inputs:
            input_info = {
                'name': inp.get('name', ''),
                'type': inp.get('type', 'text'),
                'required': inp.has_attr('required')
            }
            form_info['inputs'].append(input_info)
        
        form_data.append(form_info)
    
    return form_data

# Example comprehensive scraper
def comprehensive_page_analysis(url):
    """Comprehensive analysis of a web page"""
    scraper = EthicalWebScraper(delay=1)
    
    # Check robots.txt
    base_url = f"{urlparse(url).scheme}://{urlparse(url).netloc}"
    scraper.check_robots_txt(base_url)
    
    # Scrape page
    metadata = scraper.scrape_with_metadata(url)
    if not metadata or 'error' in metadata:
        print(f"Failed to scrape: {metadata.get('error', 'Unknown error')}")
        return None
    
    # Get page for detailed analysis
    try:
        response = scraper.session.get(url)
        soup = BeautifulSoup(response.content, 'html.parser')
        
        # Extract additional data
        analysis = metadata.copy()
        analysis.update({
            'table_data': extract_table_data(soup),
            'forms': extract_form_data(soup),
            'external_links': [
                link.get('href') for link in soup.find_all('a', href=True)
                if link.get('href').startswith(('http:', 'https:'))
            ][:10]  # First 10 external links
        })
        
        return analysis
        
    except Exception as e:
        print(f"Error in comprehensive analysis: {e}")
          return metadata
```

### 🧠 Mini Quiz - Chapter 3 (Web Scraping Dasar)

1) Header User-Agent digunakan untuk:
    a) Mengatur timeout  b) Meniru identitas browser  c) Menghindari rate limit  d) Parsing HTML

2) Metode yang tepat untuk mencegah server overload saat scraping:
    a) Mengirim request secara paralel maksimal 1000 req/detik
    b) Mengabaikan robots.txt
    c) Menggunakan delay antar request dan caching
    d) Menonaktifkan SSL verification

3) Fungsi BeautifulSoup.find_all('a', href=True) mengembalikan:
    a) Satu tag pertama  b) Semua tag a yang memiliki atribut href  c) Semua link eksternal  d) Dict href→text

Kunci: 1) b, 2) c, 3) b

### 💪 Mini Exercise - Chapter 3

- Buat fungsi get_all_links(url) yang mengembalikan daftar URL absolut dan unik dari halaman.
- Buat crawler sederhana crawl(start_url, depth=1) yang menghormati robots.txt dan max 1 req/detik.
- Parselah tabel HTML pertama pada suatu halaman menjadi list of dicts.

---

## CHAPTER 4: WORKING WITH FILES (LANJUTAN)

### 4.1 File Formats Khusus

```python
import json
import xml.etree.ElementTree as ET
import configparser
from datetime import datetime

# JSON file operations
class JSONManager:
    """Manager untuk operasi file JSON"""
    
    @staticmethod
    def save_to_json(data, filename, indent=2):
        """Menyimpan data ke file JSON"""
        try:
            with open(filename, 'w', encoding='utf-8') as f:
                json.dump(data, f, indent=indent, ensure_ascii=False, default=str)
            return f"Data berhasil disimpan ke {filename}"
        except Exception as e:
            return f"Error menyimpan JSON: {e}"
    
    @staticmethod
    def load_from_json(filename):
        """Membaca data dari file JSON"""
        try:
            with open(filename, 'r', encoding='utf-8') as f:
                return json.load(f)
        except FileNotFoundError:
            return {"error": "File tidak ditemukan"}
        except json.JSONDecodeError as e:
            return {"error": f"Error parsing JSON: {e}"}
        except Exception as e:
            return {"error": f"Error membaca JSON: {e}"}
    
    @staticmethod
    def update_json(filename, updates):
        """Update data dalam file JSON"""
        data = JSONManager.load_from_json(filename)
        if "error" in data:
            return data["error"]
        
        data.update(updates)
        return JSONManager.save_to_json(data, filename)

# XML file operations
class XMLManager:
    """Manager untuk operasi file XML"""
    
    @staticmethod
    def create_xml_from_dict(data, root_name="root"):
        """Membuat XML dari dictionary"""
        root = ET.Element(root_name)
        
        def dict_to_xml(parent, data):
            if isinstance(data, dict):
                for key, value in data.items():
                    child = ET.SubElement(parent, key)
                    dict_to_xml(child, value)
            elif isinstance(data, list):
                for item in data:
                    child = ET.SubElement(parent, "item")
                    dict_to_xml(child, item)
            else:
                parent.text = str(data)
        
        dict_to_xml(root, data)
        return ET.ElementTree(root)
    
    @staticmethod
    def save_xml(xml_tree, filename):
        """Menyimpan XML tree ke file"""
        try:
            xml_tree.write(filename, encoding='utf-8', xml_declaration=True)
            return f"XML berhasil disimpan ke {filename}"
        except Exception as e:
            return f"Error menyimpan XML: {e}"
    
    @staticmethod
    def load_xml(filename):
        """Membaca file XML"""
        try:
            tree = ET.parse(filename)
            root = tree.getroot()
            
            def xml_to_dict(element):
                result = {}
                if element.text and element.text.strip():
                    result['text'] = element.text.strip()
                
                for child in element:
                    if child.tag in result:
                        if not isinstance(result[child.tag], list):
                            result[child.tag] = [result[child.tag]]
                        result[child.tag].append(xml_to_dict(child))
                    else:
                        result[child.tag] = xml_to_dict(child)
                
                return result
            
            return {root.tag: xml_to_dict(root)}
        except Exception as e:
            return {"error": f"Error membaca XML: {e}"}

# Configuration file operations
class ConfigManager:
    """Manager untuk file konfigurasi"""
    
    def __init__(self, config_file):
        self.config_file = config_file
        self.config = configparser.ConfigParser()
    
    def create_default_config(self):
        """Membuat file konfigurasi default"""
        self.config['DATABASE'] = {
            'host': 'localhost',
            'port': '5432',
            'name': 'myapp',
            'user': 'admin'
        }
        
        self.config['APP'] = {
            'debug': 'True',
            'log_level': 'INFO',
            'max_connections': '100'
        }
        
        return self.save_config()
    
    def load_config(self):
        """Memuat file konfigurasi"""
        try:
            self.config.read(self.config_file)
            return True
        except Exception as e:
            print(f"Error membaca config: {e}")
            return False
    
    def save_config(self):
        """Menyimpan file konfigurasi"""
        try:
            with open(self.config_file, 'w') as f:
                self.config.write(f)
            return f"Config berhasil disimpan ke {self.config_file}"
        except Exception as e:
            return f"Error menyimpan config: {e}"
    
    def get_value(self, section, key, fallback=None):
        """Mendapatkan nilai konfigurasi"""
        return self.config.get(section, key, fallback=fallback)
    
    def set_value(self, section, key, value):
        """Mengatur nilai konfigurasi"""
        if not self.config.has_section(section):
            self.config.add_section(section)
        self.config.set(section, key, str(value))
    
    def get_all_config(self):
        """Mendapatkan semua konfigurasi sebagai dictionary"""
        config_dict = {}
        for section in self.config.sections():
            config_dict[section] = dict(self.config.items(section))
        return config_dict

# Example usage
def demo_file_formats():
    """Demonstrasi berbagai format file"""
    
    # Sample data
    sample_data = {
        "mahasiswa": [
            {"nama": "Ahmad", "nim": "12345", "ipk": 3.75},
            {"nama": "Siti", "nim": "67890", "ipk": 3.90}
        ],
        "metadata": {
            "created": datetime.now().isoformat(),
            "version": "1.0"
        }
    }
    
    # JSON operations
    print("=== JSON Operations ===")
    print(JSONManager.save_to_json(sample_data, "data.json"))
    loaded_json = JSONManager.load_from_json("data.json")
    print("Loaded JSON:", loaded_json)
    
    # XML operations
    print("\n=== XML Operations ===")
    xml_tree = XMLManager.create_xml_from_dict(sample_data, "university_data")
    print(XMLManager.save_xml(xml_tree, "data.xml"))
    loaded_xml = XMLManager.load_xml("data.xml")
    print("Loaded XML:", loaded_xml)
    
    # Config operations
    print("\n=== Config Operations ===")
    config_manager = ConfigManager("app.cfg")
    print(config_manager.create_default_config())
    
    config_manager.load_config()
    print("Database host:", config_manager.get_value('DATABASE', 'host'))
    
    config_manager.set_value('DATABASE', 'host', '192.168.1.100')
    print(config_manager.save_config())
    
    print("All config:", config_manager.get_all_config())

# Log file manager
class LogManager:
    """Manager untuk file log"""
    
    def __init__(self, log_file, max_size_mb=10):
        self.log_file = log_file
        self.max_size = max_size_mb * 1024 * 1024  # Convert to bytes
    
    def write_log(self, message, level="INFO"):
        """Menulis log dengan timestamp"""
        timestamp = datetime.now().strftime("%Y-%m-%d %H:%M:%S")
        log_entry = f"[{timestamp}] [{level}] {message}\n"
        
        try:
            # Check file size before writing
            if os.path.exists(self.log_file):
                if os.path.getsize(self.log_file) > self.max_size:
                    self._rotate_log()
            
            with open(self.log_file, 'a', encoding='utf-8') as f:
                f.write(log_entry)
            return True
        except Exception as e:
            print(f"Error writing log: {e}")
            return False
    
    def _rotate_log(self):
        """Rotate log file when it gets too large"""
        try:
            backup_file = f"{self.log_file}.{int(time.time())}"
            os.rename(self.log_file, backup_file)
            print(f"Log rotated to {backup_file}")
        except Exception as e:
            print(f"Error rotating log: {e}")
    
    def read_logs(self, lines=50):
        """Membaca n baris terakhir dari log"""
        try:
            with open(self.log_file, 'r', encoding='utf-8') as f:
                all_lines = f.readlines()
                return all_lines[-lines:] if len(all_lines) > lines else all_lines
        except Exception as e:
            return [f"Error reading logs: {e}"]

# Example log usage
def demo_logging():
    """Demo sistem logging"""
    logger = LogManager("app.log")
    
    logger.write_log("Aplikasi dimulai", "INFO")
    logger.write_log("User login: admin", "INFO")
    logger.write_log("Database connection failed", "ERROR")
    logger.write_log("Mencoba reconnect database", "WARNING")
    logger.write_log("Database connected", "INFO")
    
    print("Recent logs:")
    recent_logs = logger.read_logs(5)
    for log_line in recent_logs:
        print(log_line.strip())

demo_file_formats()
print("\n" + "="*50 + "\n")
demo_logging()
```

### 🧠 Mini Quiz - Chapter 4 (Working with Files Lanjutan)

1) json.dump(data, f, ensure_ascii=False) berguna untuk:
    a) Mengkompres file  b) Menyimpan karakter non-ASCII dengan benar  c) Meningkatkan kecepatan write  d) Menghindari BOM

2) Pada XML, elemen baru dibuat dengan:
    a) ET.Parse  b) ET.SubElement  c) ET.Tree  d) ET.Attrib

3) configparser cocok untuk menyimpan:
    a) Data tabel besar  b) Binary blobs  c) Konfigurasi key-value per section  d) Gambar

Kunci: 1) b, 2) b, 3) c

### 💪 Mini Exercise - Chapter 4

- Simpan hasil analisis penjualan (dict kompleks) ke JSON lalu baca kembali dan update satu field.
- Konversi dict bersarang ke XML dan simpan, lalu parse kembali menjadi dict.
- Buat config.ini dengan 2 section (database, app), lalu tulis dan baca konfigurasi menggunakan configparser.

 

## LATIHAN DAN QUIZ

### Quiz Pilihan Ganda

1. Manakah cara yang paling aman untuk membuka file di Python?
   a) `file = open("data.txt")`
   b) `with open("data.txt") as file:`
   c) `file = open("data.txt"); file.close()`
   d) `file = open("data.txt", "r")`

2. Apa fungsi dari `robots.txt` dalam web scraping?
   a) Menyimpan data yang di-scrape
   b) Memberitahu bot/crawler apa yang boleh dan tidak boleh di-scrape
   c) Mempercepat proses scraping
   d) Mengamankan website dari scraping

3. Mode file manakah yang digunakan untuk menambah konten ke akhir file tanpa menghapus yang sudah ada?
   a) `w`
   b) `r`
   c) `a`
   d) `x`

4. Dalam exception handling, kapan blok `finally` dieksekusi?
   a) Hanya jika ada exception
   b) Hanya jika tidak ada exception
   c) Selalu, terlepas dari ada atau tidaknya exception
   d) Hanya jika ada return statement

5. Library Python manakah yang paling populer untuk parsing HTML dalam web scraping?
   a) requests
   b) urllib
   c) BeautifulSoup
   d) json

### Latihan Pemrograman

#### Latihan 1: File Manager System
Buatlah sistem manajemen file dengan fitur:
- Baca, tulis, dan hapus file
- Backup file otomatis
- Logging semua operasi file
- Validasi ekstensi file

```python
class FileManager:
    def __init__(self, base_dir="files"):
        # Implementasikan inisialisasi
        pass
    
    def create_file(self, filename, content):
        # Implementasikan pembuatan file
        pass
    
    def read_file(self, filename):
        # Implementasikan pembacaan file
        pass
    
    def backup_file(self, filename):
        # Implementasikan backup file
        pass
    
    def delete_file(self, filename):
        # Implementasikan penghapusan file
        pass
```

#### Latihan 2: Web Scraper untuk Berita
Buatlah web scraper sederhana untuk mengambil:
- Judul berita
- Tanggal publikasi
- Ringkasan berita
- URL sumber

Dengan fitur:
- Rate limiting (delay antar request)
- Error handling
- Export ke CSV/JSON

#### Latihan 3: Configuration Manager
Buatlah sistem manajemen konfigurasi yang dapat:
- Membaca/menulis file .ini, .json, dan .yaml
- Validasi nilai konfigurasi
- Default values
- Environment variable support

#### Latihan 4: Log Analyzer
Buatlah program untuk menganalisis file log dengan fitur:
- Parse berbagai format log
- Filter berdasarkan level (INFO, WARNING, ERROR)
- Statistik (jumlah error per hari, dll)
- Export laporan

### Proyek Akhir Modul

**Sistem Monitoring Website dan Data Collector**

Buatlah aplikasi yang menggabungkan semua konsep yang telah dipelajari:

1. **Web Monitoring:**
   - Monitor status website (up/down)
   - Scraping data tertentu dari website
   - Alert jika ada perubahan

2. **Data Management:**
   - Simpan data dalam berbagai format (JSON, CSV, XML)
   - Backup data otomatis
   - Kompresi file lama

3. **Configuration:**
   - File konfigurasi untuk setting monitor
   - Schedule monitoring
   - Email notifications

4. **Reporting:**
   - Generate laporan monitoring
   - Dashboard sederhana
   - Export data

**Kriteria Penilaian:**
- Arsitektur modular dan clean code (25%)
- File I/O dan data management (25%)
- Web scraping dan error handling (25%)
- Documentation dan testing (25%)

---

## EVALUASI PEMBELAJARAN

### Rubrik Penilaian

| Aspek | Sangat Baik (4) | Baik (3) | Cukup (2) | Kurang (1) |
|-------|-----------------|----------|-----------|------------|
| **File Management** | Menguasai berbagai operasi file dan format | Dapat melakukan operasi file dasar | Memahami konsep file I/O | Kesulitan dengan operasi file |
| **Error Handling** | Implementasi comprehensive exception handling | Good error handling practices | Basic try-catch implementation | Minimal error handling |
| **Code Organization** | Modular, reusable, dan well-structured | Good code organization | Adequate structure | Poor organization |
| **Documentation** | Excellent documentation dan comments | Good documentation | Basic documentation | Little to no documentation |

### Self-Assessment Checklist

Setelah menyelesaikan modul ini, pastikan Anda dapat:

- [ ] Membaca dan menulis berbagai format file (text, JSON, CSV, XML)
- [ ] Menggunakan context manager untuk file operations
- [ ] Membuat dan menggunakan custom exceptions
- [ ] Mengimplementasikan web scraping yang ethical
- [ ] Menggunakan requests dan BeautifulSoup
- [ ] Mengelola konfigurasi aplikasi
- [ ] Membuat sistem logging
- [ ] Mengorganisir kode dalam modul dan package
- [ ] Menerapkan best practices dalam Python programming

---

## REFERENSI DAN SUMBER BELAJAR

### Referensi Utama
1. Python Software Foundation. (2024). Python File I/O Documentation
2. Python Software Foundation. (2024). Python Modules and Packages
3. Requests Documentation. (2024). HTTP for Humans
4. Beautiful Soup Documentation. (2024). HTML/XML Parser

### Sumber Belajar Tambahan
1. Real Python - Working with Files in Python
2. Real Python - Web Scraping with Python
3. Automate the Boring Stuff with Python - File I/O
4. Python Module of the Week (PyMOTW)

### Tools dan Libraries
- requests: HTTP library
- BeautifulSoup4: HTML/XML parser
- configparser: Configuration file parser
- pathlib: Object-oriented filesystem paths
- json: JSON encoder/decoder

---

*Modul ini disusun sebagai bagian dari pembelajaran Python untuk mahasiswa Teknik Informatika. Fokus pada aplikasi praktis dan real-world scenarios.*
