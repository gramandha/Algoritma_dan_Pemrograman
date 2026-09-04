## 8. Pembahasan Lengkap Latihan Soal (Exercises)

Berikut adalah ulasan mendalam beserta analisis teoritis dari kelima butir soal latihan yang terdapat di akhir modul [13, 14]:

### Soal 1
Mengapa nama-nama variabel di bawah ini tidak valid? [13]
* **a. `value$sum`**: Tidak valid karena mengandung karakter khusus tanda dollar (`$`) yang tidak diizinkan oleh standar ANSI/ISO C [2, 13].
* **b. `exit flag`**: Tidak valid karena mengandung karakter spasi kosong di antara kata `exit` dan `flag`. Nama variabel harus berupa satu kesatuan karakter yang utuh [13].
* **c. `3lotsofmoney`**: Tidak valid karena diawali oleh karakter angka (`3`). Aturan utama mewajibkan karakter pertama diawali huruf atau garis bawah (`_`) [2, 13].
* **d. `char`**: Tidak valid karena kata `char` adalah kata kunci bawaan (*reserved word*) yang digunakan untuk mendefinisikan tipe data karakter [2, 13].

---

### Soal 2
Berapakah hasil akhir dari program berikut [13]:
```c
#include <stdio.h>

int main() { 
    int a = 22;
    a = a + 5; 
    a = a - 2; 
    printf("a = %d\n", a); 
    return 0;
}
```
**Jawaban & Pembahasan**:
1. Langkah 1: Variabel `a` dideklarasikan dan diinisialisasi dengan nilai awal `22` [13].
2. Langkah 2: Nilai `a` diperbarui dengan operasi `a = a + 5`, sehingga nilai `a` menjadi `22 + 5 = 27` [13].
3. Langkah 3: Nilai `a` diperbarui kembali dengan operasi `a = a - 2`, sehingga nilai `a` akhir menjadi `27 - 2 = 25` [13].
4. **Hasil Akhir**: Program akan mencetak **`a = 25`** ke layar.

---

### Soal 3
Berapakah nilai `x` setelah pernyataan-pernyataan berikut dijalankan, apabila `x` bertipe `int`? [13]
* **a. `x = (2 + 3) - 10 * 2;`** [13]
  * Evaluasi tanda kurung: `(2 + 3) = 5`.
  * Evaluasi perkalian karena prioritasnya lebih tinggi daripada pengurangan: `10 * 2 = 20`.
  * Hasil: `5 - 20 = -15`.
  * **Nilai `x` = `-15`**.
* **b. `x = (2 + 3) - (10 * 2);`** [13]
  * Evaluasi tanda kurung pertama: `(2 + 3) = 5`.
  * Evaluasi tanda kurung kedua: `(10 * 2) = 20`.
  * Hasil: `5 - 20 = -15`.
  * **Nilai `x` = `-15`**.
* **c. `x = 10 % 3 * 2 + 1;`** [13]
  * Operator `%` (modulo) dan `*` (perkalian) berada pada tingkat prioritas yang sama. Oleh karena itu, evaluasi dilakukan berurutan dari kiri ke kanan.
  * Modulo: `10 % 3 = 1` (sisa dari hasil pembagian 10 dibagi 3).
  * Perkalian: `1 * 2 = 2`.
  * Penjumlahan (prioritas lebih rendah): `2 + 1 = 3`.
  * **Nilai `x` = `3`**.

---

### Soal 4
Nyatakan dalam bentuk pernyataan bahasa C! [13]
* **a. $y = bx^2 + 0,5x - c$** [13]
  * *Jawaban*:
    ```c
    y = b * x * x + 0.5 * x - c;
    ```
    *(Alternatif menggunakan fungsi perpangkatan `pow(x, 2)` dari pustaka `<math.h>`, namun penulisan langsung `x * x` jauh lebih efisien untuk perpangkatan kuadrat)*.
* **b. $Y = \frac{0,3xy}{2a}$** [14]
  * *Jawaban*:
    ```c
    Y = (0.3 * x * y) / (2 * a);
    ```
    *(Sangat penting membungkus penyebut `(2 * a)` di dalam tanda kurung. Jika Anda menulis `0.3 * x * y / 2 * a`, maka compiler akan membagi hasil perkalian pembilang dengan `2`, lalu hasilnya dikalikan dengan `a`, yang mana secara matematis menjadi $\frac{0.3xy}{2} \cdot a$)* .

---

### Soal 5
Apa hasil eksekusi dari program berikut [14]:
```c
#include <stdio.h>

int main() {
    char kar = 'A'; 
    kar = kar + 32; 
    printf("%c\n", kar);
    return 0;
}
```
**Jawaban & Pembahasan**:
1. Karakter `'A'` memiliki representasi angka biner yang sesuai dengan nilai desimal **65** pada tabel Standard ASCII [14].
2. Pernyataan `kar = kar + 32;` menjumlahkan nilai numerik karakter tersebut: `65 + 32 = 97` [14].
3. Nilai desimal **97** dalam tabel ASCII berpadanan dengan karakter huruf kecil **`'a'`** [14].
4. Karena fungsi `printf()` menggunakan penentu format `%c` (karakter), variabel tersebut dicetak kembali sebagai bentuk huruf [14].
5. **Hasil Akhir**: Layar komputer akan menampilkan huruf **`a`**.

---
