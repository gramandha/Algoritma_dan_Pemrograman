
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