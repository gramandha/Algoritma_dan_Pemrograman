# PROSES PERULANGAN (LOOPING) DALAM BAHASA C

## 1. Tujuan Pembelajaran
Pembelajaran ini bertujuan untuk membekali pemahaman mengenai:
*   Konsep dan struktur **perulangan** (*looping*) dalam bahasa C.
*   Penggunaan pernyataan **`for`**, **`while`**, dan **`do-while`**.
*   Penggunaan pernyataan pengontrol eksekusi: **`break`**, **`continue`**, dan **`goto`**.
*   Penerapan **perulangan bersarang** (*nested loop*).

---

## 2. Pernyataan Perulangan Utama

Bahasa C menyediakan tiga struktur perulangan utama untuk mengeksekusi blok kode secara berulang selama kondisi tertentu terpenuhi.

### A. Pernyataan `for`
Pernyataan `for` digunakan ketika **jumlah perulangan sudah diketahui atau ditentukan di awal**.

#### Sintaksis:
```c
for (ungkapan1; ungkapan2; ungkapan3) {
    pernyataan;
}
```

*   **`ungkapan1` (Inisialisasi)**: Memberikan nilai awal untuk variabel pengendali *loop*.
*   **`ungkapan2` (Kondisi)**: Ekspresi relasional/logika yang diuji sebelum tiap iterasi. Jika bernilai **BENAR** (non-nol), *loop* berlanjut; jika **SALAH** (0), *loop* berhenti.
*   **`ungkapan3` (Pengatur / Modifikasi)**: Mengubah nilai variabel pengendali *loop* (increment/decrement) setelah setiap iterasi selesai.

#### Contoh Kode & Alur Kerja:
```c
#include <stdio.h>

int main(void) {
    int bil;
    for (bil = 1; bil <= 15; bil += 3) {
        printf("%d\n", bil);
    }
    return 0;
}
```
**Output**:
```text
1
4
7
10
13
```

---

### B. Pernyataan `while`
Pernyataan `while` melakukan pengecekan kondisi di **bagian awal** (*pre-test loop*). Jika kondisi bernilai **SALAH** sejak awal, maka pernyataan di dalam *loop* tidak akan pernah dieksekusi sama sekali.

#### Sintaksis:
```c
while (kondisi) {
    pernyataan;
}
```

#### Contoh Kode:
```c
#include <stdio.h>

int main(void) {
    int bil = 1;
    while (bil <= 15) {
        printf("%d\n", bil);
        bil += 3;
    }
    return 0;
}
```
**Output**:
```text
1
4
7
10
13
```

---

### C. Pernyataan `do-while`
Pernyataan `do-while` melakukan pengecekan kondisi di **bagian akhir** (*post-test loop*). Hal ini menjamin bahwa blok pernyataan di dalamnya **pasti dieksekusi minimal satu kali**, meskipun kondisi bernilai salah pada pengujian pertama.

#### Sintaksis:
```c
do {
    pernyataan;
} while (kondisi);
```

#### Contoh Kode:
```c
#include <stdio.h>

int main(void) {
    int bil = 1;
    do {
        printf("%d\n", bil);
        bil += 3;
    } while (bil <= 15);
    return 0;
}
```
**Output**:
```text
1
4
7
10
13
```

---

## 3. Perbandingan `while` vs `do-while`

| Fitur / Karakteristik | `while` (*Pre-test*) | `do-while` (*Post-test*) |
| :--- | :--- | :--- |
| **Lokasi Evaluasi Kondisi** | Di **awal** perulangan sebelum eksekusi blok. | Di **akhir** perulangan setelah eksekusi blok. |
| **Jumlah Minimal Eksekusi** | **0 kali** (jika kondisi awal salah). | **Minimal 1 kali** (blok dijalankan dulu baru diuji). |
| **Penggunaan Ideal** | Ketika jumlah iterasi tergantung input dan bisa bernilai 0. | Ketika menu/input interaktif harus ditampilkan minimal sekali. |

---

## 4. Pernyataan Pengontrol Perulangan

### A. Pernyataan `break`
Pernyataan `break` berfungsi untuk **menghentikan dan memaksa keluar** dari struktur perulangan (`for`, `while`, `do-while`) atau struktur sakelar (`switch`) secara seketika. Eksekusi program akan dilanjutkan ke pernyataan setelah *loop*.

#### Bentuk Penggunaan:
```c
while (kondisi) {
    if (kondisi_keluar) {
        break; // Menghentikan seluruh loop
    }
    // Pernyataan ini dilewati jika break diaktifkan
}
```

---

### B. Pernyataan `continue`
Pernyataan `continue` berfungsi untuk **mengabaikan sisa pernyataan** dalam iterasi saat ini dan langsung melompati eksekusi ke **iterasi berikutnya** (atau evaluasi kondisi berikutnya).

#### Perbandingan Perilaku `break` vs `continue`:

```c
// Menggunakan break:
while (kondisi) {
    if (kondisi_uji)
        break;      // KELUAR DARI LOOP SEPENUHNYA
    statement_x;
}
statement_y;        // Eksekusi berlanjut di sini

// Menggunakan continue:
while (kondisi) {
    if (kondisi_uji)
        continue;   // MELOMPATI statement_x, KEMBALI KE KONDISI WHILE
    statement_x;
}
statement_y;
```

---

### C. Pernyataan `goto`
Pernyataan `goto` digunakan untuk mengarahkan alur eksekusi secara tak bersyarat ke suatu baris yang diawali dengan sebuah **label**.

#### Sintaksis:
```c
goto nama_label;

// ... beberapa baris kode ...

nama_label:
    pernyataan;
```

> **Catatan Penting**: Penggunaan `goto` sangat tidak dianjurkan dalam pemrograman terstruktur modern karena membuat alur program sulit dilacak (*spaghetti code*).

---

## 5. Perulangan Bersarang (*Nested Loop*)

*Nested loop* terjadi ketika suatu perulangan berada di dalam perulangan lainnya. Setiap kali *outer loop* (loop luar) berjalan 1 kali, *inner loop* (loop dalam) akan berjalan secara penuh sampai selesai.

### Contoh Program: Tabel Perkalian
```c
#include <stdio.h>

int main(void) {
    int baris, kolom, hasil_kali;
    
    for (baris = 1; baris <= 10; baris++) {
        for (kolom = 1; kolom <= 10; kolom++) {
            hasil_kali = baris * kolom;
            printf("%4d", hasil_kali);
        }
        printf("\n"); /* Pindah baris setelah inner loop selesai */
    }
    return 0;
}
```

---

## 6. Koreksi Materi & Penyesuaian Standar Modern (PENTING)

Terdapat beberapa kesalahan teknis dan *bug* logika pada contoh program yang ada di modul slide asli. Berikut adalah analisis dan perbaikannya:

### 1. Kesalahan `scanf("%s", &pil)` pada Variabel Karakter Tunggal
*   **Kode di Slide Asli**:
    ```c
    char pil;
    ...
    scanf("%s", &pil); // SALAH & BERBAHAYA
    ```
*   **Analisis Kesalahan**: Tipe `%s` digunakan untuk membaca *string* (array karakter) dan secara otomatis menambahkan karakter penutup `\0` (*null terminator*). Karena variabel `pil` hanya berupa `char` tunggal (1 byte), membaca string ke dalamnya menyebabkan **Buffer Overflow**, merusak memori variabel lain di sebelahnya (*undefined behavior*).
*   **Perbaikan Standar C Modern**:
    ```c
    char pil;
    ...
    scanf(" %c", &pil); // BENAR (spasi sebelum %c mengabaikan karakter newline/whitespace)
    ```

---

### 2. Kesalahan Penggunaan `break` vs `continue` pada Filter Bilangan Ganjil
*   **Kode di Slide Asli**:
    ```c
    /* Menampilkan bilangan ganjil antara 7 - 25 kecuali 15 */
    int x = 5;
    do {
        x = x + 2;
        if (x == 15)
            break; // KESALAHAN LOGIKA
        printf("%d ", x);
    } while (x < 25);
    ```
*   **Analisis Kesalahan**: Komentar modul menyatakan ingin menampilkan angka ganjil dari 7 hingga 25 *kecuali 15*. Namun kode menggunakan `break` ketika `x == 15`. Akibatnya, saat `x` mencapai 15, perulangan **langsung berhenti total**, sehingga angka 17, 19, 21, 23, dan 25 **tidak pernah dicetak** (output terhenti di: `7 9 11 13`).
*   **Perbaikan yang Benar**:
    ```c
    #include <stdio.h>

    int main(void) {
        int x = 5;
        while (x < 25) {
            x += 2;
            if (x == 15)
                continue; // Melewati angka 15 dan melanjutkan perulangan
            printf("%d ", x);
        }
        printf("\n");
        return 0;
    }
    ```
    **Output Perbaikan**: `7 9 11 13 17 19 21 23 25`

---

### 3. Logika Menghitung Karakter dan Spasi
*   **Kode di Slide Asli**:
    ```c
    do {
        kar = getchar();
        if (kar == ' ')
            jumspasi = jumspasi + 1;
        else
            jumkar = jumkar + 1;
    } while(kar != '\n');
    printf("\nJumlah karakter = %d", jumkar - 1);
    ```
*   **Analisis Kesalahan**: Pada percabangan `if (kar == ' ')`, ketika ditemukan spasi, variabel `jumspasi` bertambah tetapi `jumkar` tidak bertambah. Berarti `jumkar` hanya menghitung karakter *non-spasi*. Namun pada output ditulis `"Jumlah karakter = jumkar - 1"`. Hal ini membingungkan karena `jumkar` bukan total seluruh karakter, melainkan total karakter selain spasi (ditambah `\n`).
*   **Perbaikan yang Lebih Jelas**:
    ```c
    #include <stdio.h>

    int main(void) {
        char kar;
        int total_karakter = 0, jumspasi = 0, huruf_angka = 0;
        
        printf("Masukkan kalimat, akhiri dgn ENTER.\n\n");
        while ((kar = getchar()) != '\n') {
            total_karakter++;
            if (kar == ' ') {
                jumspasi++;
            } else {
                huruf_angka++;
            }
        }
        
        printf("\nTotal Karakter (tanpa ENTER) = %d", total_karakter);
        printf("\nJumlah Spasi                 = %d", jumspasi);
        printf("\nJumlah Non-Spasi             = %d\n\n", huruf_angka);
        
        return 0;
    }
    ```

---

### 4. Standar Deklarasi `main()`
*   **Sesuai Standar C99/C11/C17**: Hindari penulisan `main()` tanpa tipe data pengembalian. Gunakan selalu **`int main(void)`** dan diakhiri **`return 0;`**.

---

## 7. Pembahasan & Solusi Tugas (Exercises)

Berikut adalah solusi lengkap untuk tugas-tugas yang ada di akhir modul slide:

### Tugas 1: Pola Angka dengan Loop `for` dan Nested `while`
Menampilkan pola berikut:
```text
1
22
333
4444
55555
```

#### Kode Solusi C:
```c
#include <stdio.h>

int main(void) {
    int i, j;
    
    // Outer loop menggunakan 'for'
    for (i = 1; i <= 5; i++) {
        j = 1;
        // Inner loop menggunakan 'while'
        while (j <= i) {
            printf("%d", i);
            j++;
        }
        printf("\n"); // Pindah baris
    }
    
    return 0;
}
```

---

### Tugas 2: Program Menghitung Faktorial ($n!$)
Membuat program faktorial menggunakan tiga jenis perulangan (`for`, `while`, `do-while`).

#### A. Menggunakan `for`:
```c
#include <stdio.h>

int main(void) {
    int n, i;
    unsigned long long faktorial = 1;
    
    printf("Masukkan bilangan bulat positif: ");
    scanf("%d", &n);
    
    if (n < 0) {
        printf("Faktorial tidak terdefinisi untuk bilangan negatif.\n");
    } else {
        for (i = 1; i <= n; i++) {
            faktorial *= i;
        }
        printf("Faktorial dari %d (%d!) = %llu\n", n, n, faktorial);
    }
    return 0;
}
```

#### B. Menggunakan `while`:
```c
#include <stdio.h>

int main(void) {
    int n, i = 1;
    unsigned long long faktorial = 1;
    
    printf("Masukkan bilangan bulat positif: ");
    scanf("%d", &n);
    
    if (n < 0) {
        printf("Faktorial tidak terdefinisi untuk bilangan negatif.\n");
    } else {
        while (i <= n) {
            faktorial *= i;
            i++;
        }
        printf("Faktorial dari %d (%d!) = %llu\n", n, n, faktorial);
    }
    return 0;
}
```

#### C. Menggunakan `do-while`:
```c
#include <stdio.h>

int main(void) {
    int n, i = 1;
    unsigned long long faktorial = 1;
    
    printf("Masukkan bilangan bulat positif: ");
    scanf("%d", &n);
    
    if (n < 0) {
        printf("Faktorial tidak terdefinisi untuk bilangan negatif.\n");
    } else {
        do {
            if (n == 0) break; // 0! = 1
            faktorial *= i;
            i++;
        } while (i <= n);
        printf("Faktorial dari %d (%d!) = %llu\n", n, n, faktorial);
    }
    return 0;
}
```

---

### Tugas 3: Menjumlahkan Bilangan 10 s/d 100 Tanpa Inisialisasi `total = 0`
Soal meminta penjumlahkan seluruh bilangan antara 10 sampai 100 ke dalam variabel `total` dengan asumsi variabel `total` **tidak diinisialisasi terlebih dahulu dengan nilai nol**.

#### Analisis & Solusi:
Di dalam bahasa C, variabel lokal yang tidak diinisialisasi akan berisi nilai acak (*garbage value*). Jika kita langsung melakukan `total += i`, hasilnya akan salah. Oleh karena itu, pada iterasi pertama (saat `i == 10`), nilai `total` harus diisi secara langsung (`total = i`), baru pada iterasi selanjutnya menggunakan akumulasi (`total += i`).

#### Kode Solusi C:
```c
#include <stdio.h>

int main(void) {
    int total; // Tidak diinisialisasi dengan 0
    int i;
    
    for (i = 10; i <= 100; i++) {
        if (i == 10) {
            total = i; // Mengisi nilai awal pada iterasi pertama untuk menimpa garbage value
        } else {
            total += i; // Menambahkan nilai selanjutnya
        }
    }
    
    printf("Total penjumlahan 10 sampai 100 = %d\n", total);
    return 0;
}
```
*Catatan Matematika*: Hasil penjumlahan deret aritmatika $10 + 11 + \dots + 100$ adalah $\frac{91}{2} \times (10 + 100) = 5005$. Output program terbukti menghasilkan angka **5005**.
