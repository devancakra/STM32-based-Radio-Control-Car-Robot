[![Open Source Love](https://badges.frapsoft.com/os/v1/open-source.svg?style=flat)](https://github.com/ellerbrock/open-source-badges/)
[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg?logo=github&color=%23F7DF1E)](https://opensource.org/licenses/MIT)
![GitHub last commit](https://img.shields.io/github/last-commit/cakraawijaya/STM32-based-Wheeled-Robot-with-Bluetooth-control?logo=Codeforces&logoColor=white&color=%23F7DF1E)
![Project](https://img.shields.io/badge/Project-STM32-light.svg?style=flat&logo=STMicroelectronics&logoColor=white&color=%23F7DF1E)
![Type](https://img.shields.io/badge/Type-Personal%20Experiment-light.svg?style=flat&logo=gitbook&logoColor=white&color=%23F7DF1E)

# STM32-based-Wheeled-Robot-with-Bluetooth-control
Robot adalah alat yang mampu meringankan beban manusia. Robot dapat dikendalikan oleh manusia secara langsung, namun sebenarnya robot juga dapat mengambil keputusannya sendiri jika diberi algoritma cerdas. Jenis robot yang sering dipakai dalam kegiatan sekolah yaitu robot beroda. Robot beroda adalah robot yang bergerak dengan menggunakan roda. Proyek ini dibuat pada dasarnya untuk memberikan edukasi kepada masyarakat luas tentang bagaimana cara membuat robot beroda yang sederhana. Proyek ini telah dilaksanakan dan memakan waktu kurang lebih 3 hari. Protokol komunikasi UART digunakan sebagai media untuk pertukaran data antara Bluetooth dengan board STM32. Sedangkan jenis UART yang dipakai berupa Hardware Serial. Manfaat dari pembuatan proyek ini tidak lain adalah untuk menambah wawasan. Hasil dari penelitian ini menunjukkan bahwa robot dapat bergerak sesuai dengan perintah pengguna.

<br><br>

## Kebutuhan Proyek
| Bagian | Deskripsi |
| --- | --- |
| Papan Pengembangan | STM32F103C8T6 |
| Editor Kode | Arduino IDE |
| Alat Pemrogram | USB FTDI |
| Driver | CDM FTDI USB Driver |
| Protokol Komunikasi | Universal Asynchronous Receiver-Transmitter (UART) |
| Dukungan Aplikasi | • STM32CubeProgrammer<br>• Bluetooth RC Controller |
| Bahasa Pemrograman | C/C++ |
| Aktuator | Motor Gear / Motor DC (x2) |
| Sensor | JDY-31 SPP-C: Modul Bluetooth (x1) |
| Komponen Lainnya | • Kabel USB Mini - USB tipe A (x1)<br>• Kabel USB Mikro - JST 2 pin (x1)<br>• Kabel jumper (1 set)<br>• KCD11: Saklar Pengayun SPST (x1)<br>• Baterai Li-ion 18650 (x2)<br>• Tempat baterai seri 2 slot (x1)<br>• Roda robot (x2)<br>• Roda kastor (x1)<br>• Motor driver L298N (x1)<br>• Kerangka robot mobil (x1)<br>• Baut spicer (1 set)<br>• Baut plus (1 set)<br>• Mur (1 set) |

<br><br>

## Unduh & Instal
1. Arduino IDE

   <table><tr><td width="810">
         
   ```
   https://bit.ly/ArduinoIDE_Installer
   ```

   </td></tr></table><br>

2. CDM FTDI USB Driver

   <table><tr><td width="810">

   ```
   https://bit.ly/CDM_FTDI_USBdriver
   ```

   </td></tr></table><br>

3. STM32CubeProgrammer

   <table><tr><td width="810">
   
   ```
   https://bit.ly/STM32CubeProgrammer_Installer
   ```

   </td></tr></table>
   
<br><br>

## Rancangan Proyek
<table>
<tr>
<th width="420">Diagram Blok</th>
<th width="420">Diagram Ilustrasi</th>
</tr>
<tr>
<td><img src="Assets/Documentation/Diagram/Block Diagram.jpg" alt="block-diagram"></td>
<td><img src="Assets/Documentation/Diagram/Pictorial Diagram.jpg" alt="pictorial-diagram"></td>
</tr>
</table>
<table>
<tr>
<th width="840">Pengkabelan</th>
</tr>
<tr>
<td><img src="Assets/Documentation/Table/Device Wiring.jpg" alt="wiring"></td>
</tr>
</table>

<br><br>

## Pengetahuan Dasar
Pada dasarnya, suatu perangkat itu dapat dikomunikasikan dengan perangkat lain baik secara nirkabel maupun dengan kabel. Komunikasi antar perangkat keras yang umum digunakan salah satunya adalah ``` Komunikasi Serial ```. Dapat diketahui bersama bahwa ``` Komunikasi Serial ``` ini ada tiga jenis, yaitu meliputi: ``` UART (Universal Asynchronous Receiver-Transmitter) ```, ``` SPI (Serial Peripheral Interface) ```, dan ``` I2C (Inter Integrated Circuit) ```. Ada dua macam ``` Komunikasi Serial UART ```, yaitu ``` Hardware Serial ``` dan ``` Software Serial ```.  ``` Komunikasi Hardware Serial ``` dapat dilakukan dengan cara menghubungkan pin ``` TX ``` dan pin ``` RX ``` secara ``` menyilang ``` pada masing-masing papan pengembangan, misalnya: ``` RX-TX ```, kemudian ``` TX-RX ```. Pin ``` TX ``` yaitu untuk ``` mengirim data ```, sedangkan pin ``` RX ``` yaitu untuk ``` menerima data ```. ``` Komunikasi Software Serial ``` ini kurang lebih sama dengan ``` Komunikasi Hardware Serial ``` dalam segi pengkabelan, namun ada perbedaan dalam segi pengkodean. Dengan menggunakan ``` Software Serial ``` inilah anda dapat mengatasi masalah keterbatasan pin ``` RX ``` dan ``` TX ``` yang ada di papan pengembangan. Untuk berkomunikasi dengan ``` Software Serial ``` ini cukup mudah, yaitu dengan menggunakan ``` Pin Digital ``` tertentu sebagai ``` pengganti pin TX dan pin RX ```.

<br><br>

## Pengaturan Arduino IDE
1. Buka ``` Arduino IDE ``` terlebih dahulu, kemudian buka proyek ini dengan cara klik ``` File ``` -> ``` Open ``` :

   <table><tr><td width="810">
      
      ``` stm32_btrobot.ino ```

   </td></tr></table><br>
   
2. Isi ``` Url Pengelola Papan Tambahan ``` di Arduino IDE

   <table><tr><td width="810">
      
      Klik ``` File ``` -> ``` Preferences ``` -> masukkan ``` Boards Manager Url ``` dengan menyalin tautan berikut :
      
      ```
      https://github.com/stm32duino/BoardManagerFiles/raw/main/package_stmicroelectronics_index.json
      ```

   </td></tr></table><br>
   
3. ``` Pengaturan Board ``` di Arduino IDE

   <table>
      <tr><th width="810">

      Cara mengatur board ``` STM32F103C8T6 ```
            
      </th></tr>
      <tr><td>
      
      • Klik ``` Tools ``` -> ``` Board ``` -> ``` Boards Manager ``` -> Instal ``` STM32 MCU based boards ```.

      • Kemudian klik ``` Tools ``` -> ``` Board ``` -> ``` STM32 boards groups ``` -> ``` Generic STM32F1 series ```.

      </td></tr>
   </table><br>
   
4. ``` Ubah Nomor Bagian Papan ``` di Arduino IDE

   <table><tr><td width="810">
      
      Klik ``` Tools ``` -> ``` Board part number ``` -> ``` BluePill F103C8 ```

   </td></tr></table><br>
   
5. ``` Ubah Dukungan U(S)ART ``` di Arduino IDE

   <table><tr><td width="810">
      
      Klik ``` Tools ``` -> ``` U(S)ART Support ``` -> ``` Enabled (generic 'Serial') ```

   </td></tr></table><br>

6. ``` Ubah Metode Pengunggahan ``` di Arduino IDE

   <table><tr><td width="810">
      
      Klik ``` Tools ``` -> ``` Upload method ``` -> ``` STM32CubeProgrammer (Serial) ```

   </td></tr></table><br>
   
7. ``` Pengaturan Port ``` di Arduino IDE

   <table><tr><td width="810">
      
      Klik ``` Port ``` -> Pilih sesuai dengan port perangkat anda ``` (anda dapat melihatnya di Device Manager) ```

   </td></tr></table><br>

8. Sebelum mengunggah program, silakan klik: ``` Verify ```.<br><br>

9. Jika tidak ada kesalahan dalam kode program, langkah selanjutnya yaitu menggunakan alat pemrograman ``` STM32 ``` sesuai dengan prosedur. Kemudian klik: ``` Upload ```.<br><br>

10. Jika masih ada masalah saat unggah program, maka coba periksa pada bagian ``` driver ``` / ``` port ``` / ``` alat pemrogram ``` / ``` yang lainnya ```.

<br><br>

## Pengaturan USB FTDI
1. ``` Mode Pemrograman ``` :
   
   • Pastikan belum mengunggah program.
   
   • Pastikan posisi ``` jumper BOOT0 ``` yang ada pada ``` STM32F1 ``` berada pada posisi ``` 1 ```.
   
   • Pastikan posisi ``` jumper BOOT1 ``` yang ada pada ``` STM32F1 ``` berada pada posisi ``` 0 ```.

   • Pastikan posisi ``` jumper Vout ``` yang ada pada ``` FTDI ``` berada pada posisi ``` 3.3V ```.

   • Sambungkan ``` board STM32F103C8T6 ``` ini ke ``` FTDI ```.
      
      <img width="810" src="Assets/Documentation/STM32-Mode/Programming Mode.jpg" alt="programming-mode">
   
   • Kemudian sambungkan ``` FTDI ``` ke ``` PC/Laptop ``` anda dengan kabel ``` Mini USB - USB tipe A ```.
   
   • Tekan tombol ``` Reset ``` agar seluruh program yang tersemat dalam ``` board STM32 ``` ini menjadi bersih (siap untuk diprogram ulang).

   • Kompilasi dan unggah program anda melalui editor kode, dalam hal ini ``` Arduino IDE ```.<br><br><br>
   
2. ``` Mode Pengoperasian ``` :
   
   • Pastikan telah mengunggah program.

   • Lepaskan ``` FTDI ``` dari perangkat.
   
   • Pastikan posisi ``` jumper BOOT0 & BOOT1 ``` yang ada pada ``` STM32F1 ``` berada pada posisi ``` 0 ```.
      
      <img width="810" src="Assets/Documentation/STM32-Mode/Operating Mode.jpg" alt="operating-mode">
   
   • Kode program yang telah tertanam dalam ``` board STM32 ``` ini siap untuk dioperasikan (sudah tidak ada aktivitas pemrograman lagi).

   • Untuk menghidupkan ``` board STM32F1 ``` ini, anda dapat menggunakan catu daya eksternal seperti baterai atau yang lainnya.

<br>

<h3><img src="https://github.com/user-attachments/assets/932b96eb-cbc7-42f1-8938-43cb431889a5" width="16" height="16"> Catatan :</h3>
<blockquote>
   <ul>
   <li>

   Untuk mengunggah program, selain menggunakan ``` USB FTDI ```, anda juga dapat menggunakan alat pemrogram lainnya seperti: ``` ST-Link/V2 ```, ``` USB CP2102 ```, ``` USB CH340 ```, atau dengan ``` USB PL2303 ```.

   </li>
   <li>

   Berdasarkan pengalaman, saya akui bahwa penggunaan ``` ST-Link/V2 ``` ini jauh lebih baik daripada alat pemrogram lainnya karena diketahui kinerjanya lebih stabil. ``` ST-Link/V2 ``` juga memiliki kekurangan yaitu hanya dapat digunakan pada board ``` STM32 ``` dan ``` STM8 ``` saja.

   </li>
   </ul>
</blockquote>

<br><br>

## Pengaturan Bluetooth RC Controller
1. Buka direktori ``` Assets/APK ``` untuk mendapatkan aplikasi yang bernama ``` Bluetooth RC Controller ``` -> kemudian instal aplikasi tersebut pada gawai anda.
   
2. Buka aplikasi ``` Bluetooth RC Controller ```.
   
3. Hidupkan ``` bluetooth ```.
   
4. Klik tombol ``` gerigi ``` -> pilih ``` Connect to car ```.
   
5. Klik tombol ``` Scan for devices ``` -> pilih ``` JDY-31-SPP ```.

6. Kemudian ``` menyandingkan perangkat ``` dengan memasukkan kata sandi: ``` 0000 ``` atau ``` 1234 ```.
  
7. Antarmuka pengguna siap digunakan. Hal ini seperti yang terlihat pada gambar berikut.

   <img width="810" src="Assets/Documentation/Experiment/Bluetooth RC Controller.jpg" alt="user-interface">

<br><br>

## Memulai
1. Unduh dan ekstrak repositori ini.<br><br>
   
2. Pastikan anda memiliki komponen elektronik yang diperlukan.<br><br>
   
3. Pastikan komponen anda telah dirancang sesuai dengan diagram.<br><br>
    
4. Konfigurasikan perangkat anda menurut pengaturan di atas.<br><br>

5. Selamat menikmati [Selesai].

<br><br>

## Sorotan
<img width="840" src="Assets/Documentation/Experiment/Device.jpg" alt="rc-car-robot">

<br><br>

## Apresiasi
Jika karya ini bermanfaat bagi anda, maka dukunglah karya ini sebagai bentuk apresiasi kepada penulis dengan mengklik tombol ``` ⭐Bintang ``` di bagian atas repositori.

<br><br>

## LISENSI
LISENSI MIT - Hak Cipta © 2023 - Devan C. M. Wijaya, S.Kom

Dengan ini diberikan izin tanpa biaya kepada siapa pun yang mendapatkan salinan perangkat lunak ini dan file dokumentasi terkait perangkat lunak untuk menggunakannya tanpa batasan, termasuk namun tidak terbatas pada hak untuk menggunakan, menyalin, memodifikasi, menggabungkan, mempublikasikan, mendistribusikan, mensublisensikan, dan/atau menjual salinan Perangkat Lunak ini, dan mengizinkan orang yang menerima Perangkat Lunak ini untuk dilengkapi dengan persyaratan berikut:

Pemberitahuan hak cipta di atas dan pemberitahuan izin ini harus menyertai semua salinan atau bagian penting dari Perangkat Lunak.

DALAM HAL APAPUN, PENULIS ATAU PEMEGANG HAK CIPTA DI SINI TETAP MEMILIKI HAK KEPEMILIKAN PENUH. PERANGKAT LUNAK INI DISEDIAKAN SEBAGAIMANA ADANYA, TANPA JAMINAN APAPUN, BAIK TERSURAT MAUPUN TERSIRAT, OLEH KARENA ITU JIKA TERJADI KERUSAKAN, KEHILANGAN, ATAU LAINNYA YANG TIMBUL DARI PENGGUNAAN ATAU URUSAN LAIN DALAM PERANGKAT LUNAK INI, PENULIS ATAU PEMEGANG HAK CIPTA TIDAK BERTANGGUNG JAWAB, KARENA PENGGUNAAN PERANGKAT LUNAK INI TIDAK DIPAKSAKAN SAMA SEKALI, SEHINGGA RISIKO ADALAH MILIK ANDA SENDIRI.
