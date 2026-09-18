## 5. Pembahasan dan Solusi Tugas Mandiri (Slide 22 & 23) Keputusan

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
