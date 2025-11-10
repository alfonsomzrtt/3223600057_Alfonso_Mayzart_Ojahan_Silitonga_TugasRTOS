# -3223600057_Alfonso_Mayzart_Ojahan_Silitonga_TugasRTOS
Tugas RTOS mengakses 8 periferal yang terdiri dari oled, led, buzzer, button, potensiometer, stepper, servo, rotary-encoder di ESP32-S3 pada platform wokwi.com
# Dual-Core ESP32-S3 Multitasking with FreeRTOS  


Repositori ini berisi serangkaian percobaan untuk **mengeksplorasi kemampuan dua core ESP32-S3** dengan **multitasking berbasis FreeRTOS**.  
Setiap percobaan menjalankan **dua task identik** di **Core 0** dan **Core 1**, menggunakan fungsi **'xTaskCreatePinnedToCore()'**.  

Periferal yang diuji meliputi total 8 jenis perangkat:

---
1.ESP32-S3 Board
2. Potentiometer, Rotary-Encoder KY-040, Stepper Nema-17, Servo SG-90
3. LED, OLED, Buzzer, Button
4. Breadboard dan kabel jumper
5. Arduino IDE/Wokwi.com/PlatformIO

## Tujuan Percobaan
- Memaksimalkan penggunaan **dua core ESP32-S3**.  
- Menerapkan konsep **multitasking** menggunakan **FreeRTOS**.  
- Membagi beban kerja antar core untuk meningkatkan **efisiensi pemrosesan**.  
- Mengamati bagaimana kedua core dapat menjalankan task secara **paralel** dan **stabil**.  
- Menguji komunikasi dan sinkronisasi dasar antar task jika diperlukan.  

---

##  Langkah Pemrograman / Percobaan  

### 1. Persiapan  

- IDE: **Arduino IDE** atau **PlatformIO**  
- Board: `ESP32S3 Dev Module`  
- Library tambahan:  
  - `ESP32Servo.h` (untuk servo)  
  - `Wire.h` + `Adafruit_SSD1306.h` (untuk OLED)  
  - `Arduino.h` (default)  

### 2. Struktur Proyek  

Setiap periferal memiliki sketch terpisah untuk memudahkan eksperimen paralel:  

| No | File | Deskripsi |
|----|------|------------|
| 1 | `servo.ino` | Dua servo dikendalikan di Core 0 & Core 1 |
| 2 | `stepper.ino` | Dua motor bipolar bergerak independen |
| 3 | `potentiometer.ino` | Dua potensiometer dibaca bersamaan |
| 4 | `rotary-encoder.ino` | Dua rotary encoder KY-040 dengan interrupt |
| 5 | `Oled.ino` | OLED menampilkan status task atau nilai sensor |
| 6 | `LED.ino` | Dua LED berkedip dengan ritme berbeda di tiap core |
| 7 | `Buzzer.ino` | satu buzzer menghasilkan frekuensi berbeda di tiap core |
| 8 | `Button.ino` | Dua tombol dibaca di core terpisah untuk interaksi input |

---

## Kegunaan xTaskCreatePinnedToCore()
Fungsi inti FreeRTOS pada ESP32 yang memungkinkan untuk menentukan pada core apa task dijalankan



