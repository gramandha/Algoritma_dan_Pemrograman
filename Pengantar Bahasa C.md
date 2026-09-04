# Bahasa C dan Compiler MinGW

## 1. Apa Itu Bahasa C?

**C** adalah bahasa pemrograman yang digunakan untuk memberikan instruksi kepada komputer agar melakukan tugas tertentu.

Bahasa C termasuk bahasa pemrograman yang relatif dekat dengan **hardware**, sehingga banyak digunakan untuk:

* Sistem embedded
* Mikrokontroler
* Robotika
* Internet of Things (IoT)
* Sistem operasi
* Driver perangkat keras
* Sistem real-time
* Pengendalian motor dan sensor

Contoh program sederhana dalam bahasa C:

```c
#include <stdio.h>

int main() {
    printf("Hello World");
    return 0;
}
```

Ketika program tersebut dijalankan, hasilnya adalah:

```text
Hello World
```

---

## 2. Mengapa Bahasa C Banyak Digunakan?

Salah satu keunggulan bahasa C adalah kemampuannya untuk bekerja cukup dekat dengan perangkat keras.

Contohnya, dalam sistem embedded kita dapat melakukan pengolahan:

* Memori
* Pointer
* Bit
* Register
* Input/output
* Sensor
* PWM
* Komunikasi serial
* Timer
* Interrupt

Karena karakteristik tersebut, bahasa C banyak digunakan dalam pengembangan sistem berbasis mikrokontroler seperti:

```text
Arduino
ESP32
STM32
AVR
PIC
```

Untuk sistem seperti **Embbeded berbasis ESP32**, bahasa C/C++ juga sangat relevan untuk mengembangkan sistem kontrol, pembacaan sensor, komunikasi, dan pengendalian thruster.

---

# 3. Apa Itu Compiler?

Komputer tidak dapat langsung menjalankan kode C yang kita tulis.

Misalnya kita membuat program:

```c
int a = 10;
int b = 20;
int c = a + b;
```

Kode tersebut masih berupa **source code**.

Source code harus diterjemahkan menjadi instruksi yang dapat dipahami oleh prosesor.

Prosesnya secara sederhana:

```text
Source Code C
      |
      v
   Compiler
      |
      v
Machine Code
      |
      v
Program yang dapat dijalankan
```

### Pengertian Compiler

**Compiler adalah perangkat lunak yang menerjemahkan source code dari bahasa pemrograman menjadi kode mesin atau bentuk kode yang dapat dijalankan oleh komputer.**

Untuk bahasa C, salah satu compiler yang paling populer adalah **GCC (GNU Compiler Collection)**.

---

# 4. Apa Itu GCC?

**GCC (GNU Compiler Collection)** adalah kumpulan compiler dari proyek GNU yang dapat digunakan untuk melakukan kompilasi berbagai bahasa pemrograman, termasuk:

* C
* C++
* Objective-C
* Fortran
* Ada

Untuk bahasa C, compiler yang digunakan biasanya adalah:

```bash
gcc
```

Contohnya, kita mempunyai file:

```text
program.c
```

Kemudian kita menjalankan:

```bash
gcc program.c -o program
```

GCC akan melakukan proses kompilasi sehingga menghasilkan program:

```text
program
```

Pada Windows, hasilnya biasanya berupa:

```text
program.exe
```

---

# 5. Apa Itu MinGW?

**MinGW (Minimalist GNU for Windows)** adalah lingkungan/toolchain yang memungkinkan compiler GNU seperti **GCC** digunakan pada sistem operasi Windows.

Dengan kata sederhana:

> **MinGW memungkinkan kita menggunakan GCC untuk melakukan kompilasi program C/C++ di Windows.**

Contoh:

```text
Program C
   |
   | program.c
   v
 MinGW / GCC
   |
   | proses compile
   v
program.exe
```

---

# 6. Fungsi MinGW

MinGW digunakan untuk menyediakan berbagai tools yang diperlukan untuk mengembangkan program C/C++ di Windows.

Salah satu komponen utamanya adalah:

```text
GCC
```

Sehingga kita dapat melakukan kompilasi program C melalui terminal Windows.

Contohnya:

```bash
gcc program.c -o program.exe
```

Setelah proses kompilasi berhasil, akan dihasilkan:

```text
program.exe
```

Program tersebut dapat dijalankan di Windows.

---

# 7. Hubungan C, GCC, MinGW, dan VS Code

Keempat istilah ini memiliki fungsi yang berbeda.

| Komponen    | Fungsi                                              |
| ----------- | --------------------------------------------------- |
| **C**       | Bahasa pemrograman                                  |
| **GCC**     | Compiler untuk C/C++                                |
| **MinGW**   | Toolchain untuk menggunakan GCC di Windows          |
| **VS Code** | Code editor untuk menulis dan mengelola source code |
| **`.c`**    | Ekstensi file source code C                         |
| **`.exe`**  | File executable Windows                             |

Hubungannya dapat digambarkan sebagai berikut:

```text
             Bahasa C
                 |
                 v
             program.c
                 |
                 v
        +----------------+
        |      GCC       |
        |    Compiler    |
        +----------------+
                 ^
                 |
              MinGW
                 |
                 v
           program.exe
                 |
                 v
             Windows
```

Sedangkan VS Code digunakan sebagai tempat untuk menulis kode:

```text
              VS Code
                 |
                 | menulis
                 v
             program.c
                 |
                 v
          MinGW + GCC
                 |
                 | compile
                 v
            program.exe
```

---

# 8. Contoh Program C dengan MinGW

Misalkan kita membuat file:

```text
hello.c
```

Isi file:

```c
#include <stdio.h>

int main() {
    printf("Hello World!\n");

    return 0;
}
```

Kemudian buka terminal pada folder tempat file tersebut berada.

Jalankan:

```bash
gcc hello.c -o hello.exe
```

Jika tidak terdapat error, compiler akan menghasilkan:

```text
hello.exe
```

Kemudian jalankan:

```bash
hello.exe
```

Output:

```text
Hello World!
```

---

# 9. Apa yang Terjadi Saat Program Dikompilasi?

Secara sederhana prosesnya dapat digambarkan seperti berikut:

```text
                 SOURCE CODE
                     |
                     v
                 hello.c
                     |
                     v
              +-------------+
              |     GCC     |
              |   Compiler  |
              +-------------+
                     |
                     v
              Machine Code
                     |
                     v
                hello.exe
                     |
                     v
              Program berjalan
```

Pada proses sebenarnya, compiler melakukan beberapa tahap, seperti preprocessing, compilation, assembly, dan linking.

Secara sederhana:

```text
Source Code
     |
     v
Preprocessing
     |
     v
Compilation
     |
     v
Assembly
     |
     v
Linking
     |
     v
Executable
```

---

# 10. Apakah VS Code Adalah Compiler?

**Bukan.**

VS Code adalah **code editor**.

VS Code digunakan untuk:

* Menulis kode
* Mengedit kode
* Membuka project
* Debugging
* Mengelola file
* Menggunakan extension

Sedangkan compiler bertugas menerjemahkan kode menjadi program yang dapat dijalankan.

Contohnya:

```text
VS Code
   |
   | menulis
   v
program.c
   |
   | dikompilasi oleh
   v
GCC / MinGW
   |
   v
program.exe
```

Jadi, VS Code dan MinGW memiliki fungsi yang berbeda tetapi dapat digunakan bersama.

---

# 11. Apakah MinGW Digunakan untuk ESP32?

**Tidak secara langsung.**

MinGW digunakan terutama untuk melakukan kompilasi program yang ditujukan untuk lingkungan Windows.

Untuk ESP32, digunakan **toolchain compiler yang ditujukan untuk arsitektur ESP32**.

Gambaran sederhananya:

```text
                 Bahasa C/C++
                      |
          +-----------+-----------+
          |                       |
          v                       v
    MinGW + GCC             ESP32 Toolchain
          |                       |
          v                       v
     Windows PC                  ESP32
       .exe                    Firmware
```

Contohnya, ketika menggunakan **ESP-IDF**, proses pengembangan akan menggunakan toolchain yang sesuai dengan arsitektur ESP32.

---

# 12. Hubungan dengan Embedded System

Dalam pengembangan embedded system, konsep compiler menjadi sangat penting.

Misalnya kita ingin membuat program untuk ESP32:

```text
Source Code C/C++
        |
        v
ESP32 Compiler
        |
        v
Firmware
        |
        v
      ESP32
        |
        +------> Sensor
        |
        +------> Motor
        |
        +------> Thruster
        |
        +------> Komunikasi
```

Untuk aplikasi Robot, misalnya:

```text
                 ESP32
                   |
        +----------+----------+
        |          |          |
        v          v          v
       IMU     Depth Sensor  Communication
        |          |          |
        +----------+----------+
                   |
                   v
               PID Control
                   |
                   v
              Motor/Thruster
```

Program C/C++ dapat digunakan untuk mengimplementasikan:

* Pembacaan IMU
* Pembacaan sensor kedalaman
* Perhitungan PID
* PWM thruster
* Komunikasi serial
* UART
* I2C
* SPI
* CAN
* Task pada FreeRTOS
* Pengolahan data sensor

---

# 13. Kesimpulan

Dapat disimpulkan:

> **Bahasa C** adalah bahasa pemrograman yang digunakan untuk membuat program dan banyak digunakan pada sistem embedded karena mampu bekerja dekat dengan hardware.

> **Compiler** adalah program yang menerjemahkan source code menjadi kode yang dapat dijalankan oleh komputer.

> **GCC** adalah salah satu compiler yang digunakan untuk bahasa C dan C++.

> **MinGW** menyediakan lingkungan/toolchain agar GCC dapat digunakan pada Windows.

> **VS Code** adalah editor yang dapat digunakan untuk menulis source code, tetapi VS Code sendiri bukan compiler.

Hubungan sederhananya:

```text
C
|
| bahasa pemrograman
v
Source Code (.c)
|
v
GCC
|
| compiler
v
MinGW (Windows Toolchain)
|
v
Executable (.exe)
|
v
Windows
```

Sedangkan untuk sistem embedded:

```text
C/C++
   |
   v
Compiler/Toolchain sesuai hardware
   |
   v
Firmware
   |
   v
Mikrokontroler
   |
   v
Sensor + Aktuator + Sistem Kontrol
```

Dengan demikian, **C merupakan bahasa yang diprogram, GCC merupakan compiler, MinGW merupakan toolchain untuk lingkungan Windows, dan VS Code merupakan editor untuk menulis program tersebut.**
