# Panduan Lengkap Dasar Pemrograman C: Variabel, Operator, dan Input/Output

---

## 1. Tujuan Pembelajaran

Setelah mempelajari materi ini, Anda diharapkan mampu memahami [1]:
* **Tipe Data Dasar**: Memahami ragam tipe data dasar yang tersedia dalam bahasa C beserta representasi memorinya.
* **Variabel & Konstanta**: Menguasai aturan penulisan identifier, cara deklarasi, inisialisasi, serta penggunaan konstanta.
* **Operator C**: Memahami cara kerja operator aritmatika, increment/decrement, penugasan, dan operator kombinasi (compound assignment) beserta tingkat prioritasnya.
* **Instruksi Input/Output (I/O)**: Menguasai penggunaan fungsi input-output standar seperti `printf()`, `scanf()`, `puts()`, `putchar()`, `getchar()`, dan `getch()`.

---

## 2. Tipe Data Dasar dan Ukuran Memori

Data dalam bahasa C secara garis besar dapat berupa **konstanta** (nilainya tetap) atau **variabel** (nilainya dapat berubah selama program berjalan) [1]. Berdasarkan sifat datanya, bahasa C membagi data menjadi lima kelompok tipe data dasar [1]:
1. **Bilangan Bulat (*Integer*)**
2. **Bilangan Real Presisi-Tunggal (*Float*)**
3. **Bilangan Real Presisi-Ganda (*Double*)**
4. **Karakter (*Char*)**
5. **Tak-Bertipe (*Void*)**

### Tabel Spesifikasi Tipe Data: Klasik vs Modern
*Catatan: Ukuran tipe data dalam bahasa C sangat bergantung pada arsitektur perangkat keras dan compiler yang digunakan [2]. Berikut adalah tabel perbandingan ukuran memori dan jangkauan nilai antara arsitektur 16-bit klasik (seperti Turbo C) dan sistem 32/64-bit modern (seperti GCC/Clang modern).*

| Tipe Data | Ukuran (Modul - 16 bit) [2] | Jangkauan Nilai (16 bit) [2] | Ukuran Modern (32/64 bit) | Jangkauan Nilai (Modern) | Keterangan [2] |
| :--- | :---: | :--- | :---: | :--- | :--- |
| **`char`** | 8 bit (1 byte) | -128 s/d 127 | 8 bit (1 byte) | -128 s/d 127 | Karakter tunggal / Huruf |
| **`int`** | 16 bit (2 byte) | -32.768 s/d 32.767 | **32 bit (4 byte)** | -2.147.483.648 s/d 2.147.483.647 | Bilangan bulat (*signed*) |
| **`short int`** | 16 bit (2 byte) | -32.768 s/d 32.767 | 16 bit (2 byte) | -32.768 s/d 32.767 | Bilangan bulat pendek |
| **`unsigned int`**| 16 bit (2 byte) | 0 s/d 65.535 | **32 bit (4 byte)** | 0 s/d 4.294.967.295 | Bilangan bulat tak bertanda |
| **`long int`** | 32 bit (4 byte) | -2.147.483.648 s/d 2.147.483.647 | 32/64 bit | Bergantung arsitektur sistem | Bilangan bulat panjang |
| **`float`** | 32 bit (4 byte) | 1.7E-38 s/d 3.4E+38 *(Koreksi: 1.2E-38)* | 32 bit (4 byte) | ~1.2E-38 s/d ~3.4E+38 | Real presisi-tunggal (single) |
| **`double`** | 64 bit (8 byte) | 2.2E-308 s/d 1.7E+308 | 64 bit (8 byte) | ~2.2E-308 s/d ~1.7E+308 | Real presisi-ganda (double) |
| **`void`** | 0 bit | - | 0 bit | - | Tipe data kosong / tak bertipe |

---

## 3. Variabel

Variabel adalah sebuah identifier atau nama yang digunakan untuk menunjuk suatu lokasi memori komputer yang datanya dapat berubah selama program dieksekusi [1].

### A. Aturan Baku Penamaan Variabel (Identifier)
Agar program dapat dikompilasi dengan baik dan memenuhi standar penulisan C, berikut aturan penulisannya [2]:
1. **Karakter Pertama**: Harus berupa huruf (`A..Z`, `a..z`) atau karakter garis bawah (`_`) [2].
2. **Karakter Selanjutnya**: Boleh berupa huruf, angka (`0..9`), atau garis bawah (`_`) [2]. *(Karakter khusus seperti tanda dollar `$` tidak diperbolehkan dalam standar C modern)*.
3. **Panjang Nama**: Meskipun panjang variabel bisa melebihi 31 karakter, standar C menetapkan hanya **31 karakter pertama** yang dibaca dan dianggap signifikan oleh compiler [2].
4. **Kata Cadangan (*Reserved Words*)**: Tidak boleh menggunakan kata-kata kunci bawaan C seperti `int`, `float`, `char`, `if`, `while`, dll [2].

### B. Deklarasi, Pengisian Nilai, dan Inisialisasi
Setiap variabel wajib dideklarasikan terlebih dahulu sebelum digunakan guna memesan ruang memori [3].
* **Deklarasi**: `tipe_data daftar_nama_variabel;` [3]
  ```c
  int var_bulat1;
  float var_pecahan1, var_pecahan2;
  ```
* **Pengisian Nilai (Assignment)**: Menaruh nilai ke dalam variabel menggunakan operator `=` [3].
  ```c
  var_bulat1 = 34;
  var_pecahan1 = 34.52;
  ```
* **Inisialisasi**: Mendeklarasikan variabel sekaligus memberikan nilai awal pada saat yang bersamaan [3].
  ```c
  int nilai = 10; // Mendeklarasikan variabel 'nilai' sekaligus mengisinya dengan angka 10 [4]
  ```

### C. Contoh Program Variabel: Menghitung Harga Total
Berikut adalah kode program sederhana untuk menghitung total belanjaan [4]:
```c
#include <stdio.h>

int main() {
    int jumlah;
    float harga_unit, harga_total;
    
    jumlah = 10;
    harga_unit = 17.5f; // Penggunaan 'f' menandakan konstanta float
    harga_total = jumlah * harga_unit;
    
    printf("Harga total = %f\n", harga_total);
    
    return 0;
}
```

---

## 4. Konstanta

Konstanta adalah nilai yang bersifat tetap dan tidak dapat diubah oleh instruksi program setelah didefinisikan [4]. Berbeda dengan variabel, konstanta tidak perlu dideklarasikan tipe datanya secara eksplisit, tetapi jenis penulisannya menentukan tipe datanya secara implisit [4]:

* **Konstanta Karakter**: Diapit oleh tanda petik tunggal, mewakili satu karakter tunggal [4]. Contoh: `'A'`, `'@'`.
* **Konstanta Integer**: Ditulis langsung berupa angka bilangan bulat tanpa tanda petik, tanpa pecahan, dan tanpa pemisah ribuan [4]. Contoh: `-1`, `32767`.
* **Konstanta Real (`float`/`double`)**: Menggunakan tanda titik sebagai pemisah desimal, atau ditulis dalam notasi eksponensial (notasi `e` / ilmiah) [4]. Contoh: `27.5f` (untuk float), `27.5` (untuk double), atau `2.1e+5` (berarti $2,1 \times 10^5$).
* **Konstanta String**: Merupakan rangkaian karakter yang diapit oleh tanda petik ganda [4]. Contoh: `"Program Dasar"`.

### Cara Mendefinisikan Konstanta dalam Kode Program
Ada dua pendekatan utama untuk membuat konstanta [5]:
1. **Menggunakan Preprosesor `#define`**:
   ```c
   #define PI 3.14159 // Tanpa tanda titik koma (;) di akhir
   ```
2. **Menggunakan Kata Kunci `const`**:
   ```c
   const float PI = 3.14159; // Harus diakhiri titik koma (;)
   ```

---

## 5. Operator dalam Bahasa C

Operator adalah simbol yang digunakan untuk memproses data atau melakukan operasi matematis/logis terhadap satu atau lebih operand [5].

### A. Operator Aritmatika [6]
Operator aritmatika dalam C terbagi menjadi:
1. **Operator Unary**: Melibatkan hanya satu operand [6].
   * `+` (Tanda Plus / Positif) [6]
   * `-` (Tanda Minus / Negatif) [6]
2. **Operator Binary**: Melibatkan dua operand [6].
   * `*` (Perkalian)
   * `/` (Pembagian)
   * `%` (Sisa Pembagian / Modulo)
   * `+` (Penjumlahan)
   * `-` (Pengurangan)

### B. Tingkat Prioritas Operator Aritmatika & Evaluasi Ekspresi
Ketika terdapat beberapa operator dalam satu baris ekspresi, bahasa C akan mengevaluasi berdasarkan urutan prioritas pengerjaan berikut (dari prioritas tertinggi ke terendah):

| Prioritas | Operator | Arah Evaluasi (Asosiativitas) | Keterangan |
| :--- | :--- | :--- | :--- |
| **1 (Tertinggi)** | `( )` | Dari kiri ke kanan | Pengelompokan / Kurung |
| **2** | `!`, `++`, `--`, `+` (unary), `-` (unary) | **Dari kanan ke kiri** | Unary operator / Negasi / Increment / Decrement |
| **3** | `*`, `/`, `%` | Dari kiri ke kanan | Perkalian, pembagian, dan modulo [6] |
| **4** | `+`, `-` | Dari kiri ke kanan | Penjumlahan dan pengurangan |
| **5 (Terendah)** | `=`, `+=`, `-=`, `*=`, `/=`, `%=`, dsb. | **Dari kanan ke kiri** | Operator penugasan (Assignment) |

### C. Operator Increment (`++`) dan Decrement (`--`)
Operator ini digunakan untuk menaikkan atau menurunkan nilai variabel sebesar 1 [6]. Operator ini memiliki dua cara penulisan yang menghasilkan efek berbeda dalam ekspresi majemuk [6]:

| Operator | Jenis | Arti | Perilaku dalam Ekspresi |
| :---: | :--- | :--- | :--- |
| **`++x`** | Pre-increment | `x = x + 1` [6] | Nilai `x` ditambah 1 terlebih dahulu, baru nilai baru tersebut digunakan dalam ekspresi [7]. |
| **`x++`** | Post-increment | `x = x + 1` [6] | Nilai `x` yang sekarang digunakan terlebih dahulu dalam ekspresi, setelah itu nilai `x` ditambah 1 [7]. |
| **`--y`** | Pre-decrement | `y = y - 1` [7] | Nilai `y` dikurangi 1 terlebih dahulu, baru nilai baru tersebut digunakan dalam ekspresi [7]. |
| **`y--`** | Post-decrement | `y = y - 1` [7] | Nilai `y` yang sekarang digunakan terlebih dahulu dalam ekspresi, setelah itu nilai `y` dikurangi 1 [7]. |

#### Contoh Program Demonstrasi Increment:
```c
#include <stdio.h>

int main() {
    int count = 0, loop;
    
    // Demonstrasi Pre-increment (++count)
    loop = ++count; 
    // Hasil: count bertambah menjadi 1, lalu dimasukkan ke loop.
    printf("loop = %d, count = %d\n", loop, count); // Output: loop = 1, count = 1
    
    // Demonstrasi Post-increment (count++)
    loop = count++; 
    // Hasil: nilai count saat ini (1) diberikan ke loop, setelah itu count bertambah menjadi 2.
    printf("loop = %d, count = %d\n", loop, count); // Output: loop = 1, count = 2
    
    return 0;
}
```

### D. Operator Penugasan (Assignment) dan Kombinasi
* **Operator Penugasan Standar (`=`)**: Digunakan untuk memasukkan nilai dari suatu ekspresi ke dalam variabel [8]. Operator ini dapat ditulis berantai [8]:
  ```c
  a = b = c = 10; // Variabel a, b, dan c semuanya bernilai 10
  ```
  Contoh ekspresi terikat: `a = (b = 1) + 5;` (Mula-mula `b` diisi nilai 1, lalu `a` diisi nilai `1 + 5 = 6`) [8].

* **Operator Kombinasi (Compound Assignment)**: Digunakan untuk menyingkat penulisan operasi aritmatika yang mengubah nilai variabel itu sendiri [8].

| Operator Kombinasi | Arti Padanan | Operator Kombinasi | Arti Padanan |
| :---: | :--- | :---: | :--- |
| **`x += y`** | `x = x + y` [8] | **`x <<= y`** | `x = x << y` (Bitwise Left Shift) |
| **`x -= y`** | `x = x - y` | **`x >>= y`** | `x = x >> y` (Bitwise Right Shift) |
| **`x *= y`** | `x = x * y` [8] | **`x &= y`** | `x = x & y` (Bitwise AND) |
| **`x /= y`** | `x = x / y` | **`x \|=`** | `x = x \| y` (Bitwise OR) |
| **`x %= y`** | `x = x % y` | **`x ^= y`** | `x = x ^ y` (Bitwise XOR) |

---

## 6. Instruksi Input dan Output (I/O)

Bahasa C menyediakan fungsi pustaka bawaan untuk menangani operasi input (membaca data dari keyboard) dan output (menampilkan data ke layar).

### A. Fungsi Output

#### 1. `printf()` (Print Formatted)
Fungsi utama untuk menampilkan berbagai tipe data ke layar secara terformat [8].
* **Bentuk Umum**: `printf("string kontrol", argumen1, argumen2, ...);` [9]

##### Tabel Penentu Format (Format Specifiers) `printf()`:
| Penentu Format | Tipe Data yang Ditampilkan | Format Keluaran |
| :---: | :--- | :--- |
| **`%c`** | `char` | Satu karakter tunggal [9] |
| **`%s`** | `char[]` (String) | Deretan karakter / teks [9] |
| **`%d` / `%i`**| `int` (signed) | Bilangan bulat desimal bertanda |
| **`%u`** | `unsigned int` | Bilangan bulat desimal tak bertanda |
| **`%o`** | `unsigned int` | Bilangan bulat dalam format oktal (basis 8) |
| **`%x` / `%X`**| `unsigned int` | Hexadecimal basis 16 (`%x` huruf kecil, `%X` huruf besar) |
| **`%f`** | `float` / `double` | Bilangan real dalam format desimal standar (default 6 digit belakang koma) |
| **`%e` / `%E`**| `float` / `double` | Bilangan real dalam format eksponensial ilmiah (e.g. `2.51e+05`) |
| **`%g` / `%G`**| `float` / `double` | Otomatis memilih `%f` atau `%e` yang paling pendek (menghilangkan angka nol tidak berarti) [9] |
| **`l` (awalan)**| `long` | Awalan untuk tipe data integer panjang (e.g., `%ld`, `%lu`) atau tipe `double` (`%lf`) |
| **`L` (awalan)**| `long double` | Awalan untuk menampilkan data bilangan real presisi tinggi (`%Lf`) |
| **`h` (awalan)**| `short` | Awalan untuk menampilkan data short integer (`%hd`) |

##### Spesifikasi Medan Lebar (Field Width) pada `printf()`
Kita dapat menyisipkan bilangan bulat di antara tanda `%` dan huruf penentu format untuk mengatur ukuran lebar kolom tampilan [9]:
* **Integer (`%4d`)**: Angka dicetak dengan lebar minimal 4 karakter [9]. Jika jumlah digit kurang dari 4, sisa lebar akan diisi spasi di bagian kiri (rata kanan secara default).
  * *Contoh*: `printf("Abad %4d", 20);` -> Menghasilkan `Abad   20` (dua spasi di depan angka 20) [9].
* **Real / Floating Point (`%m.nf`)**:
  * `m` = total lebar kolom (termasuk titik desimal dan seluruh angka desimal) [10].
  * `n` = jumlah digit di belakang koma (presisi pecahan) [10].
  * *Contoh*: `printf("Harga : Rp %8.2f\n", 500.0);` -> Menghasilkan `Harga : Rp   500.00` (total panjang 8 karakter, rata kanan dengan 2 angka di belakang koma) [10].
* **String (`%12s` & `%-12s`)**:
  * `%12s` (Positif): Mencetak string dengan lebar kolom 12 karakter rata kanan (menyisakan spasi kosong di kiri) [10].
  * `%-12s` (Negatif): Mencetak string dengan lebar kolom 12 karakter rata kiri (menyisakan spasi kosong di kanan) [10].

#### 2. `puts()` (Put String)
Digunakan khusus untuk menampilkan data bertipe string ke layar [10]. Keunggulannya adalah secara otomatis menambahkan karakter baris baru (*newline* / `\n`) di akhir tampilan [10].
* *Contoh*: `puts("Selamat mencoba");` setara dengan `printf("Selamat mencoba\n");` [10].

#### 3. `putchar()` (Put Character)
Digunakan khusus untuk menampilkan sebuah karakter tunggal ke layar komputer [10].
* *Contoh*: `putchar('F');` setara dengan `printf("%c", 'F');` [10].

---

### B. Fungsi Input

#### 1. `scanf()` (Scan Formatted)
Digunakan untuk menerima masukan data terformat dari keyboard [11]. Fungsi ini memerlukan argumen berupa **alamat memori** tempat data input disimpan [11]. Untuk itu, nama variabel wajib dibubuhi operator alamat yaitu tanda ampersand (`&`) [11].
* **Bentuk Umum**: `scanf("string kontrol", &nama_variabel);` [11]
* *Contoh*:
  ```c
  scanf("%f", &radius); // Membaca input real dan menyimpannya di alamat memori variabel 'radius' [11, 12]
  scanf("%d %d", &data1, &data2); // Membaca dua bilangan bulat sekaligus yang dipisahkan spasi [12]
  ```

##### Tabel Penentu Format `scanf()`:
| Penentu Format | Kegunaan / Tipe Data yang Dibaca |
| :---: | :--- |
| **`%c`** | Membaca sebuah karakter tunggal |
| **`%s`** | Membaca sebuah string (teks hingga menemui spasi pertama) |
| **`%d` / `%i`**| Membaca integer desimal bertanda |
| **`%u`** | Membaca integer desimal tak bertanda |
| **`%o`** | Membaca integer berbentuk oktal (basis 8) |
| **`%x`** | Membaca integer berbentuk heksadesimal (basis 16) |
| **`%e` / `%f`**| Membaca bilangan real (mendukung format desimal standar maupun eksponensial) |
| **`l` (awalan)**| Awalan untuk tipe data `long int` (`%ld`) atau `double` (`%lf`) |
| **`L` (awalan)**| Awalan untuk tipe data `long double` (`%Lf`) |
| **`h` (awalan)**| Awalan untuk tipe data `short int` (`%hd`) |

#### 2. `getchar()` (Get Character)
Membaca sebuah karakter dari keyboard tanpa memerlukan parameter formal [12]. Karakter yang ditekan pengguna **akan ditampilkan** di layar (*echoing*) dan program akan menunggu hingga tombol Enter ditekan [12].
* *Contoh*: `kar = getchar();` [12]

#### 3. `getch()` (Get Character No Echo)
Fungsi ini membaca sebuah karakter dari keyboard **tanpa menampilkannya** di layar monitor (*non-echoing*) dan program langsung memproses karakter tersebut seketika tanpa perlu menekan tombol Enter [12].

---

### C. Contoh Program Bujursangkar
Berikut adalah implementasi program sederhana untuk menghitung luas dan keliling sebuah bujursangkar menggunakan interaksi input/output:
```c
/* File program : bujursangkar.c 
   Menghitung luas dan keliling bujursangkar [12] */
#include <stdio.h>

int main() {
    int luas, keliling, panjang_sisi;
    
    printf("Masukkan panjang sisi bujursangkar : ");
    scanf("%d", &panjang_sisi); // Meminta input dari keyboard [12]
    
    luas = panjang_sisi * panjang_sisi; // Rumus luas [12]
    keliling = panjang_sisi * 4;        // Rumus keliling [12]
    
    printf("\nData bujursangkar\n");
    printf("Panjang sisi = %6d\n", panjang_sisi); // Mencetak lebar medan 6 [12]
    printf("Luas         = %6d\n", luas);
    printf("Keliling     = %6d\n", keliling);
    
    return 0;
}
```

---

## 7. Koreksi Komprehensif Terhadap Modul Asli

Untuk menjaga ketepatan akademis, beberapa kekeliruan atau materi yang tidak standar/usang dalam file PDF asli telah diidentifikasi dan dikoreksi sebagai berikut:

| No | Poin dalam Modul Asli | Status / Kesalahan | Penjelasan & Koreksi Standar Modern (ANSI/ISO C) |
| :---: | :--- | :--- | :--- |
| **1** | Menyatakan `printf` merupakan *Reserved Word* (Kata Cadangan) bersama `int`, `if`, `while` [2]. | **SALAH** | `printf` **bukan** kata cadangan bahasa C. `printf` adalah nama fungsi dari pustaka standard (`<stdio.h>`). Kata cadangan (*keyword*) murni bahasa C adalah kata-kata khusus bawaan parser compiler seperti `int`, `return`, `for`, `if`, `while`. Anda bisa menamai variabel Anda `printf`, tetapi sangat tidak disarankan karena akan menimpa rujukan ke fungsi cetak tersebut. |
| **2** | Menyatakan aturan penulisan variabel boleh mengandung karakter tanda dollar (`$`) [2]. | **TIDAK STANDAR** | Standar ANSI/ISO C menetapkan bahwa identifier (nama variabel/fungsi) hanya boleh terdiri dari huruf (`a..z, A..Z`), angka (`0..9`), dan garis bawah (`_`). Penggunaan tanda `$` tidak valid dalam kode C standar. Meskipun compiler tertentu seperti GCC mengizinkannya sebagai ekstensi non-standar, kode tersebut tidak portabel. |
| **3** | Menyatakan ukuran tipe data `int` adalah 16 bit (2 byte) dengan jangkauan -32.768 s/d 32.767 [2]. | **USANG** | Ukuran ini hanya berlaku pada sistem operasi 16-bit jadul (seperti MS-DOS dan compiler Turbo C). Pada sistem operasi dan arsitektur prosesor 32-bit atau 64-bit modern, ukuran default `int` adalah **32 bit (4 byte)** dengan jangkauan dari **-2.147.483.648 s/d 2.147.483.647**. |
| **4** | Menyatakan jangkauan nilai `float` adalah `1.7E-38 s/d 3.4E+38` [2]. | **SALAH KETIK** | Berdasarkan standar representasi biner IEEE 754 untuk tipe data *single-precision float*, rentang nilai positif minimum adalah sekitar **`1.175E-38`** (atau dibulatkan menjadi `1.2E-38`). Angka `1.7` di modul asli tertukar dengan batas minimum tipe data `double` yang bernilai `1.7E-308` (atau `2.2E-308`). |
| **5** | Mencontohkan penggunaan fungsi `getch()` secara langsung bersama pustaka standar `<stdio.h>` [12]. | **KETERGANTUNGAN SISTEM** | Fungsi `getch()` **bukan** fungsi pustaka standar C (ANSI C). `getch()` adalah fungsi bawaan pustaka non-standar `<conio.h>` yang spesifik untuk arsitektur MS-DOS/Windows. Pada platform Linux atau macOS, file header `<conio.h>` tidak terpasang secara default sehingga program yang menggunakan `getch()` akan gagal melakukan kompilasi. |
| **6** | Menuliskan deklarasi fungsi `main()` secara langsung sebagai `main() { ... }` tanpa tipe data pengembalian [4, 6, 7]. | **TIDAK STANDAR (C99)** | Sejak standar **C99**, aturan "implicit int" (mengizinkan fungsi tanpa tipe data eksplisit diasumsikan sebagai int) telah resmi dihapus. Setiap deklarasi fungsi harus menyatakan tipe pengembalian secara jelas. Praktik modern yang benar untuk fungsi utama adalah **`int main()`** dan diakhiri dengan baris pernyataan **`return 0;`** [4]. |
| **7** | Menggunakan tanda petik cerdas atau miring (*smart quotes*) `“` dan `”` dalam penulisan kode program [4, 6, 9]. | **SALAH SINTAKS** | Bahasa C hanya mengenali tanda petik lurus (`"`) untuk string dan (`'`) untuk karakter. Menyalin kode langsung dengan tanda petik miring hasil pengetikan aplikasi editor dokumen (seperti MS Word) akan menyebabkan kegagalan kompilasi berantai (*syntax error*). |

---



