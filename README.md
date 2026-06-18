Secara umum, terdapat beberapa jenis sensor pada modul kamera RHYX M21-45 yang digunakan untuk ESP32 Cam yaitu:
- OV2640
- GC2145
- SC031GS
- GC032A
- sensor custom lainnya

Cara menentukan jenis sensor pada modul kamera RHYX M21-45 dapat dilakukan dengan melihat Product ID (PID) melalui pengujian untuk memastikan sensor RHYX M21-45 dapat terdeteksi.
Program yang digunakan: _https://github.com/ekodemecheng/ESP32-CAM_Modul-RHYX-M21-45/blob/main/Program%20RHYX%20M21-45%20Test%20Grayscale_

Dari serial monitor dapat dilihat:
__Camera Initialized!_

_load:0x3fff0030,len:4876
ho 0 tail 12 room 4
load:0x40078000,len:16560
load:0x40080400,len:3500
entry 0x400805b4__

_RHYX M21-45 Camera Test_

_Camera Initialized!
PID : 0x2145
VER : 0x00
MIDH: 0x00
MIDL: 0x00_

**Analisis:**
PID 0x2145 menunjukkan bahwa kamera kemungkinan besar menggunakan GalaxyCore GC2145 (2 MP), bukan OV2640.

Inilah penyebab utama error sebelumnya:
_JPEG format is not supported on this sensor
Init Failed With Error 0x106_

_Artinya:_
✅ Wiring benar
✅ ESP32 bekerja normal
✅ Driver GC2145 sudah tersedia pada ESP32 Camera Driver

Tahap selanjutnya dapat dilakukan pengujian diantaranya:

| Tahap               | Status |
| ------------------- | ------ |
| Deteksi RHYX M21-45 | ✅      |
| RGB565 Capture      | ✅      |
| SD Card Mount       | ✅      |
| Write File SD       | ✅      |
| RAW Save            | ✅      |
| JPEG Conversion     | ✅      |
| JPEG Save           | ✅      |

Semua code sudah terdapat di dalam repositori ini.
Infografis juga diberikan untuk memudahkan pengujian.

Terimakasih.
