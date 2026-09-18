# DASAR PEMROGRAMAN C: Pengambilan Keputusan (Decision Making)

## 1. Tujuan Pembelajaran
Modul ini bertujuan untuk memberikan pemahaman mengenai:
* Penggunaan **Operator Kondisi** (Operator Relasi dan Operator Logika).
* Penggunaan **Pernyataan `if`** untuk percabangan tunggal.
* Penggunaan **Pernyataan `if-else`** untuk percabangan ganda.
* Penggunaan **Pernyataan `if` Bersarang (*Nested IF*)** dan **`else-if` (*Else-If Ladder*)** untuk percabangan majemuk.
* Penggunaan **Operator Ternary (`? :`)** sebagai bentuk ringkas dari `if-else`.
* Penggunaan **Pernyataan `switch-case`** sebagai kontrol kondisi berbasis konstanta.

---

## 2. Operator Kondisi: Relasi dan Logika

Pengambilan keputusan dalam bahasa C mengevaluasi suatu **ekspresi kondisi**. Ekspresi tersebut menghasilkan nilai Boolean:
* **`1` (BENAR / True)**: Jika kondisi terpenuhi.
* **`0` (SALAH / False)**: Jika kondisi tidak terpenuhi.

### A. Operator Relasi
Operator relasi digunakan untuk membandingkan dua nilai (*operand*).

| Operator | Makna / Arti | Contoh | Hasil |
| :---: | :--- | :--- | :--- |
| `>` | Lebih dari | `5 > 2` | `1` (Benar) |
| `>=` | Lebih dari atau sama dengan | `4 >= 4` | `1` (Benar) |
| `<` | Kurang dari | `1 < 2` | `1` (Benar) |
| `<=` | Kurang dari atau sama dengan | `3 <= 2` | `0` (Salah) |
| `==` | Sama dengan | `A == 1` | `1` jika `A` bernilai 1, `0` jika tidak |
| `!=` | Tidak sama dengan | `3 != 2` | `1` (Benar) |

*Catatan Karakter ASCII*: Pembandingan karakter dilakukan berdasarkan nilai kode ASCII-nya.
Contoh: `'A' < 'B'` bernilai **BENAR (1)** karena kode ASCII `'A'` (65) kurang dari `'B'` (66).

---

### B. Operator Logika
Operator logika digunakan untuk mengombinasikan satu atau lebih ekspresi relasi.

| Operator | Makna / Arti | Bentuk Umum | Keterangan |
| :---: | :--- | :--- | :--- |
| `&&` | DAN (*AND*) | `operand1 && operand2` | Bernilai `1` HANYA JIKA kedua operand bernilai BENAR. |
| `\|\|` | ATAU (*OR*) | `operand1 \|\| operand2` | Bernilai `1` JIKA SALAH SATU atau KEDUA operand bernilai BENAR. |
| `!` | TIDAK (*NOT*) | `!operand` | Membalikkan nilai logika (BENAR jadi SALAH, SALAH jadi BENAR). |

#### Tabel Kebenaran (Truth Table)
| `Operand1` | `Operand2` | `Operand1 && Operand2` | `Operand1 \|\| Operand2` | `!Operand1` |
| :---: | :---: | :---: | :---: | :---: |
| `0` (Salah) | `0` (Salah) | `0` | `0` | `1` |
| `0` (Salah) | `1` (Benar) | `0` | `1` | `1` |
| `1` (Benar) | `0` (Salah) | `0` | `1` | `0` |
| `1` (Benar) | `1` (Benar) | `1` | `1` | `0` |

---

### C. Hierarki dan Prioritas Operator
Urutan eksekusi operator dalam bahasa C (dari prioritas tertinggi ke terendah):

1. **`!`** (NOT Unary)
2. **Operator Aritmatika** (`*`, `/`, `%`, diikuti `+`, `-`)
3. **Operator Relasi Hirarki 1** (`>`, `>=`, `<`, `<=`)
4. **Operator Relasi Hirarki 2** (`==`, `!=`)
5. **Operator Logika `&&`** (AND)
6. **Operator Logika `||`** (OR)
7. **Operator Penugasan** (`=`, `+=`, `-=`, dll.)

---

### D. Solusi Latihan Evaluasi Kondisi (Modul Slide 10)

Mari kita evaluasi ekspresi logika berikut secara eksplisit:

1. **`2 > 1 || 3 <= 4 && 4 < 1`**
   * `2 > 1` $\rightarrow$ `1` (Benar)
   * `3 <= 4` $\rightarrow$ `1` (Benar)
   * `4 < 1` $\rightarrow$ `0` (Salah)
   * Evaluasi `&&` terlebih dahulu: `1 && 0` $\rightarrow$ `0`
   * Evaluasi `||`: `1 || 0` $\rightarrow$ **`1` (BENAR)**.

2. **`2 > 1 && 3 <= 4 || 4 < 1`**
   * `2 > 1` $\rightarrow$ `1`
   * `3 <= 4` $\rightarrow$ `1`
   * Evaluasi `&&` terlebih dahulu: `1 && 1` $\rightarrow$ `1`
   * Evaluasi `||`: `1 || (4 < 1)` $\rightarrow$ `1 || 0` $\rightarrow$ **`1` (BENAR)**.

3. **`!(2 > 1) && (3 <= 4)`**
   * `2 > 1` $\rightarrow$ `1`, maka `!(1)` $\rightarrow$ `0` (Salah)
   * `3 <= 4` $\rightarrow$ `1` (Benar)
   * Evaluasi `&&`: `0 && 1` $\rightarrow$ **`0` (SALAH)**.

4. **`(5 > 1 || 3 != 2) && ((2 > 1) || (4 == 2))`**
   * Kurung kiri: `(1 || 1)` $\rightarrow$ `1`
   * Kurung kanan: `(1 || 0)` $\rightarrow$ `1`
   * Evaluasi `&&`: `1 && 1` $\rightarrow$ **`1` (BENAR)**.

---

## 3. Struktur Pengambilan Keputusan dalam C

### A. Pernyataan `if` (Percabangan Tunggal)
Digunakan untuk mengeksekusi blok kode hanya jika kondisi bernilai BENAR.

```c
if (kondisi) {
    // Pernyataan yang dieksekusi jika kondisi BENAR
}
```

*Contoh Program: Menghitung Diskon Pembelian (`discount.c`)*
```c
#include <stdio.h>

int main() {
    float total_pembelian, discount = 0.0f;
    
    printf("Total pembelian = Rp ");
    scanf("%f", &total_pembelian);
    
    if (total_pembelian >= 100000.0f) {
        discount = 0.05f * total_pembelian;
    }
    
    printf("Besarnya discount = Rp %6.2f\n", discount);
    
    return 0;
}
```

---

### B. Pernyataan `if-else` (Percabangan Ganda)
Digunakan untuk memilih satu dari dua blok pernyataan berdasarkan hasil kondisi.

```c
if (kondisi) {
    // Dieksekusi jika kondisi BENAR
} else {
    // Dieksekusi jika kondisi SALAH
}
```

*Contoh Program: Menentukan Nilai Minimal Dua Bilangan (`minim.c`)*
```c
#include <stdio.h>

int main() {
    int minim, nilai1, nilai2;
    
    printf("Masukkan 2 buah nilai:\n");
    scanf("%d %d", &nilai1, &nilai2);
    
    if (nilai1 < nilai2) {
        minim = nilai1;
    } else {
        minim = nilai2;
    }
    
    printf("Nilai minimalnya adalah: %d\n", minim);
    
    return 0;
}
```

---

### C. Pernyataan `if` Bersarang (*Nested IF*)
Pernyataan `if` atau `if-else` yang berada di dalam struktur `if` atau `else` lainnya.

*Contoh Program: Menentukan Bilangan Positif / Negatif*
```c
#include <stdio.h>

int main() {
    int x, y;
    
    printf("Masukkan 2 buah nilai:\n");
    scanf("%d %d", &x, &y);
    
    if (x > 0) {
        if (y > 0) {
            printf("Nilai x dan y adalah positif\n");
        } else {
            printf("Nilai x positif dan y negatif\n");
        }
    } else {
        printf("Nilai x negatif\n");
    }
    
    return 0;
}
```

---

### D. Tangga `else-if` (*Else-If Ladder*)
Digunakan untuk mengevaluasi banyak kondisi secara berurutan dari atas ke bawah.

```c
if (kondisi_1) {
    // Pernyataan 1
} else if (kondisi_2) {
    // Pernyataan 2
} else if (kondisi_n) {
    // Pernyataan n
} else {
    // Pernyataan default jika tidak ada kondisi yang terpenuhi
}
```

*Contoh Program: Kalkulator Sederhana (`kalkulator1.c`)*
```c
#include <stdio.h>

int main() {
    int valid_operator = 1;
    char op;
    float number1, number2, result = 0.0f;
    
    printf("Masukkan 2 buah bilangan dan sebuah operator\n");
    printf("dengan format: number1 operator number2\n\n");
    scanf("%f %c %f", &number1, &op, &number2);
    
    if (op == '*') {
        result = number1 * number2;
    } else if (op == '/') {
        if (number2 != 0) {
            result = number1 / number2;
        } else {
            printf("Error: Pembagian dengan nol!\n");
            valid_operator = 0;
        }
    } else if (op == '+') {
        result = number1 + number2;
    } else if (op == '-') {
        result = number1 - number2;
    } else {
        valid_operator = 0;
    }
    
    if (valid_operator) {
        printf("\n%g %c %g is %g\n", number1, op, number2, result);
    } else {
        printf("Invalid operator!\n");
    }
    
    return 0;
}
```

---

### E. Operator Ternary (`? :`)
Operator kondisi tiga operand yang berfungsi sebagai bentuk ringkas dari `if-else`.

*Sintaks*:
```c
variabel = (kondisi) ? ungkapan_benar : ungkapan_salah;
```

*Contoh*:
```c
#include <stdio.h>

int main() {
    float nilai1, nilai2, max;
    
    printf("Masukkan dua buah nilai: ");
    scanf("%f %f", &nilai1, &nilai2);
    
    max = (nilai1 > nilai2) ? nilai1 : nilai2;
    
    printf("Nilai terbesar = %g\n", max);
    
    return 0;
}
```

---

### F. Pernyataan `switch-case`
Digunakan untuk percabangan banyak arah berdasarkan nilai **konstanta integer atau karakter**.

*Sintaks*:
```c
switch (ekspresi) {
    case konstanta_1:
        pernyataan_1;
        break;
    case konstanta_2:
        pernyataan_2;
        break;
    default:
        pernyataan_default;
        break;
}
```

*Contoh Program: Kalkulator Sederhana dengan `switch`*
```c
#include <stdio.h>

int main() {
    int valid_operator = 1;
    char op;
    float number1, number2, result = 0.0f;
    
    printf("Masukkan 2 buah bilangan dan sebuah operator\n");
    printf("dengan format: number1 operator number2\n\n");
    scanf("%f %c %f", &number1, &op, &number2);
    
    switch (op) {
        case '*':
            result = number1 * number2;
            break;
        case '/':
            if (number2 != 0) {
                result = number1 / number2;
            } else {
                printf("Error: Pembagian dengan nol!\n");
                valid_operator = 0;
            }
            break;
        case '+':
            result = number1 + number2;
            break;
        case '-':
            result = number1 - number2;
            break;
        default:
            valid_operator = 0;
            break;
    }
    
    if (valid_operator) {
        printf("%g %c %g is %g\n", number1, op, number2, result);
    } else {
        printf("Invalid operator!\n");
    }
    
    return 0;
}
```

---

## 4. Koreksi Materi & Penyesuaian Standar Modern (PENTING)

Terdapat beberapa kesalahan materi dan praktik penulisan pada modul asli yang wajib diperbaiki:

### 1. Jebakan Logika Ekspresi Rentang Nilai (Paling Krusial!)
* **Kesalahan Modul (Slide 23 / Tugas 2)**:
  Tabel pada modul menuliskan rentang nilai seperti: `70 < Nilai <= 80`.
* **Bahaya Logika**:
  Jika seorang pemula menuliskan `if (70 < Nilai <= 80)` dalam kode C, compiler **TIDAK AKAN** mengecek apakah `Nilai` berada di antara 70 dan 80! Bahasa C mengevaluasi ekspresi ini dari kiri ke kanan:
  1. `70 < Nilai` dievaluasi dulu, menghasilkan `1` (True) atau `0` (False).
  2. Hasil `1` atau `0` tersebut kemudian dibandingkan dengan `80` (`1 <= 80` atau `0 <= 80`).
  3. Karena `0` dan `1` selalu kurang dari atau sama dengan `80`, ekspresi `if (70 < Nilai <= 80)` akan **SELALU BERNILAI BENAR (1)** untuk angka berapapun!
* **Solusi Bahasa C yang Benar**: Harus menggunakan operator logika `&&`:
  ```c
  if (Nilai > 70 && Nilai <= 80)
  ```

### 2. Sintaks Kode yang Hilang pada Slide Modul
* Pada Slide 16 (Program Positif/Negatif), kode di modul tertulis:
  `#include <stdio.h> { int x,y; ... }` (fungsi `main()` terhapus secara tidak sengaja).
* **Solusi**: Wajib menambahkan fungsi utama `int main()` secara eksplisit.

### 3. Pembersihan Buffer pada Input `scanf` untuk Karakter (`%c`)
* Saat membaca format `%f %c %f` menggunakan `scanf`, karakter `newline` (Enter) dari input sebelumnya bisa terserap oleh `%c`.
* **Solusi**: Tambahkan spasi sebelum `%c` pada format `scanf(" %c", &op)` untuk mengabaikan karakter *whitespace* atau *newline*.

### 4. Penanganan Pembagian dengan Nol
* Pada program kalkulator di modul, pembagian dengan angka nol (`number2 = 0`) belum diantisipasi sehingga bisa menyebabkan runtime error (*Division by Zero*). Pada kode perbaikan di atas, telah ditambahkan pengecekan `if (number2 != 0)`.

---

## 5. Pembahasan dan Solusi Tugas Mandiri (Slide 22 & 23)

### Tugas 1: Program Persamaan Kuadrat & Akar-Akar ($ax^2 + bx + c = 0$)

*Rumus*:
* $D = b^2 - 4ac$
* Jika $D = 0$: $x_1 = x_2 = \frac{-b}{2a}$
* Jika $D > 0$: $x_1 = \frac{-b + \sqrt{D}}{2a}$, $x_2 = \frac{-b - \sqrt{D}}{2a}$
* Jika $D < 0$: $x_1 = \frac{-b}{2a} + \frac{\sqrt{-D}}{2a}i$, $x_2 = \frac{-b}{2a} - \frac{\sqrt{-D}}{2a}i$

*Kode Program C Lengkap (`persamaan_kuadrat.c`)*:
```c
#include <stdio.h>
#include <math.h>

int main() {
    float a, b, c;
    float D, x1, x2, realPart, imagPart;
    
    printf("=== Program Persamaan Kuadrat (ax^2 + bx + c = 0) ===\n");
    printf("Masukkan koefisien a, b, dan c: ");
    scanf("%f %f %f", &a, &b, &c);
    
    if (a == 0) {
        printf("Bukan persamaan kuadrat (a tidak boleh 0).\n");
        return 0;
    }
    
    D = (b * b) - (4 * a * c);
    printf("Nilai Diskriminan (D) = %.2f\n", D);
    
    if (D == 0) {
        x1 = -b / (2 * a);
        printf("Akar real kembar:\n");
        printf("x1 = x2 = %.2f\n", x1);
    } else if (D > 0) {
        x1 = (-b + sqrt(D)) / (2 * a);
        x2 = (-b - sqrt(D)) / (2 * a);
        printf("Dua akar real berlainan:\n");
        printf("x1 = %.2f\n", x1);
        printf("x2 = %.2f\n", x2);
    } else { // D < 0
        realPart = -b / (2 * a);
        imagPart = sqrt(-D) / (2 * a);
        printf("Dua akar imajiner (kompleks) berlainan:\n");
        printf("x1 = %.2f + %.2fi\n", realPart, imagPart);
        printf("x2 = %.2f - %.2fi\n", realPart, imagPart);
    }
    
    return 0;
}
```

---

### Tugas 2: Program Konversi Nilai Angka (0-100) ke Klasifikasi Huruf

*Aturan Klasifikasi*:
* Nilai > 80 $\rightarrow$ **A**
* 70 < Nilai $\le$ 80 $\rightarrow$ **B**
* 60 < Nilai $\le$ 70 $\rightarrow$ **C**
* 50 < Nilai $\le$ 60 $\rightarrow$ **D**
* Nilai $\le$ 50 $\rightarrow$ **E**

*Kode Program C Lengkap (`konversi_nilai.c`)*:
```c
#include <stdio.h>

int main() {
    float nilai;
    
    printf("Masukkan nilai siswa (0 - 100): ");
    scanf("%f", &nilai);
    
    if (nilai < 0 || nilai > 100) {
        printf("Nilai tidak valid! Masukkan angka antara 0 - 100.\n");
    } else if (nilai > 80) {
        printf("Klasifikasi Nilai: A\n");
    } else if (nilai > 70) { // Menangani rentang 70 < Nilai <= 80
        printf("Klasifikasi Nilai: B\n");
    } else if (nilai > 60) { // Menangani rentang 60 < Nilai <= 70
        printf("Klasifikasi Nilai: C\n");
    } else if (nilai > 50) { // Menangani rentang 50 < Nilai <= 60
        printf("Klasifikasi Nilai: D\n");
    } else { // Menangani Nilai <= 50
        printf("Klasifikasi Nilai: E\n");
    }
    
    return 0;
}
```

---

### Tugas 3: Program Mengurutkan 3 Bilangan dari Terbesar ke Terkecil

*Kode Program C Lengkap (`urutkan_tiga_bilangan.c`)*:
```c
#include <stdio.h>

int main() {
    int x, y, z;
    int temp;
    
    printf("Masukkan 3 buah bilangan (x y z): ");
    scanf("%d %d %d", &x, &y, &z);
    
    // Algoritma pengurutan sederhana (Bubble Sort untuk 3 variabel)
    if (x < y) {
        temp = x; x = y; y = temp;
    }
    if (x < z) {
        temp = x; x = z; z = temp;
    }
    if (y < z) {
        temp = y; y = z; z = temp;
    }
    
    printf("Urutan nilai dari terbesar ke terkecil: %d, %d, %d\n", x, y, z);
    
    return 0;
}
```
