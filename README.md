# FreeRTOS LED Blinking Task Demo

Implementasi sederhana dari **FreeRTOS** yang menunjukkan pengendalian dua LED (hijau dan merah) menggunakan thread dengan prioritas yang berbeda. Contoh ini bertujuan untuk memahami dasar-dasar multitasking menggunakan FreeRTOS pada mikrokontroler STM32.

## Fitur
- **Thread Management**:
  - **Green Task**: Menyalakan dan mematikan LED hijau dengan pola tertentu.
  - **Red Task**: Menyalakan dan mematikan LED merah dengan pola tertentu.
  - Default Task aktif tetapi tidak melakukan apa-apa.
- **GPIO Control**:
  - Menyalakan, mematikan, dan mengedipkan LED menggunakan GPIO.
- **Task Prioritization**:
  - Red Task memiliki prioritas lebih tinggi daripada Green Task.

---

## Cara Kerja Program
Program ini menggunakan FreeRTOS untuk membuat multitasking antara dua tugas utama yang mengontrol LED. Berikut adalah cara kerja masing-masing task:

### 1. **Green Task**
- **Fungsi**: Mengontrol LED hijau.
- **Proses Kerja**:
  1. LED hijau dinyalakan (`GreenTask_Pin` diset HIGH).
  2. LED hijau berkedip 80 kali dengan interval 50 ms:
     - ON selama 25 ms.
     - OFF selama 25 ms.
  3. LED hijau dimatikan (`GreenTask_Pin` diset LOW).
  4. Task ditunda selama 6 detik (`osDelay(6000)`).
- **Prioritas**: Normal (`osPriorityNormal`).

### 2. **Red Task**
- **Fungsi**: Mengontrol LED merah.
- **Proses Kerja**:
  1. LED merah dinyalakan (`RedTask_Pin` diset HIGH).
  2. LED merah berkedip 10 kali dengan interval 50 ms:
     - ON selama 25 ms.
     - OFF selama 25 ms.
  3. LED merah dimatikan (`RedTask_Pin` diset LOW).
  4. Task ditunda selama 1,5 detik (`osDelay(1500)`).
- **Prioritas**: Lebih tinggi dari Green Task (`osPriorityAboveNormal`).

### 3. **Default Task**
- **Fungsi**: Tidak ada fungsi spesifik, hanya sebagai placeholder.
- **Proses Kerja**:
  - Task ini berjalan dalam loop tak hingga dengan delay 1 ms.

---

## Prioritas Task
- Red Task memiliki prioritas lebih tinggi daripada Green Task. 
  - Jika kedua task siap dijalankan, Red Task akan berjalan terlebih dahulu.
- Default Task memiliki prioritas terendah sehingga hanya berjalan saat semua task lain dalam status idle.

---

## Persyaratan Sistem
- **Perangkat Keras**:
  - Mikrokontroler STM32.
  - Dua LED (hijau dan merah) terhubung ke pin GPIO.
- **Toolchain**:
  - STM32CubeIDE atau alat pengembangan yang kompatibel dengan STM32.
- **Library**:
  - FreeRTOS sudah diintegrasikan melalui STM32 HAL.

---

## Cara Menjalankan
1. **Persiapkan Hardware**:
   - Hubungkan LED hijau dan merah ke pin GPIO yang telah dikonfigurasi di `main.c`.

2. **Import Proyek**:
   - Buka proyek di STM32CubeIDE atau IDE lainnya.

3. **Build dan Flash**:
   - Kompilasi kode.
   - Flash firmware ke mikrokontroler STM32 Anda.

4. **Pengamatan**:
   - LED merah dan hijau akan menyala dan berkedip sesuai dengan logika di masing-masing task.


https://github.com/user-attachments/assets/eda2dce9-2b40-4b62-b2b3-fd2fb64c0f2a

