# TUGAS SISTEM OPERASI 5

---

![Image](https://github.com/user-attachments/assets/838b068c-4d85-452a-aca6-352d279fbd3f)

#### Dosen Pengampu :
**Dr. Ferry Astika Saputra ST, M.Sc**

#### Disusun oleh :
**Abdullah Faqih**
**(3124521026)**
D3-LA IT-A

<br>

# Rangkuman 1.34-1.35

## 1. Transisi Antara Mode Pengguna dan Mode Kernel
- **Timer**: Berfungsi untuk menghentikan proses yang berjalan terlalu lama agar tidak memonopoli sumber daya.
- **Interupsi Waktu**: Timer menghitung mundur dan menghasilkan interupsi saat mencapai nol, mengembalikan kendali kepada sistem operasi.
- **Pengaturan Proses**: Interupsi memungkinkan sistem menghentikan proses yang melampaui waktu, menjadwalkan proses baru, dan menjaga efisiensi.

## 2. Manajemen Proses
- **Proses**: Program aktif yang dijalankan untuk menyelesaikan tugas tertentu dengan memanfaatkan sumber daya seperti CPU, memori, perangkat I/O, dan file.
- **Terminasi Proses**: Sumber daya harus dikembalikan setelah proses selesai.
- **Eksekusi Proses**:
  - *Single-threaded*: Memiliki satu utas dan satu program counter.
  - *Multi-threaded*: Memiliki beberapa utas dengan program counter masing-masing.

## 3. Aktivitas Manajemen Proses
- **Pembuatan & Penghapusan Proses**: Sistem operasi bertanggung jawab atas pembuatan dan penghapusan proses.
- **Penangguhan & Pelanjutan Proses**: Proses dapat ditangguhkan atau dilanjutkan sesuai kebutuhan.
- **Sinkronisasi & Komunikasi**: Mekanisme tersedia untuk menjaga koordinasi dan pertukaran data antar proses.
- **Penanganan Deadlock**: Sistem memastikan tidak terjadi deadlock yang menyebabkan proses saling tergantung.

## 4. Manajemen Memori
- Mengelola data dan instruksi di memori untuk mengoptimalkan penggunaan CPU serta respons sistem.
- Aktivitas meliputi pelacakan memori, pemindahan data antar memori & penyimpanan, serta alokasi dan dealokasi ruang.

## 5. Manajemen File Sistem
- **Abstraksi Penyimpanan**: Mengubah perangkat penyimpanan fisik menjadi unit logis bernama file.
- **Organisasi File**: File diatur dalam direktori dengan kontrol akses.
- **Aktivitas Sistem Operasi**:
  - Pembuatan, manipulasi, dan penghapusan file serta direktori.
  - Pemetaan file ke penyimpanan sekunder.
  - Pencadangan ke penyimpanan non-volatile.

## 6. Manajemen Penyimpanan Massal
- **Disk**: Digunakan untuk penyimpanan data jangka panjang.
- **Manajemen**: Penting untuk meningkatkan kinerja sistem. Aktivitas mencakup pengelolaan ruang kosong, penjadwalan disk, dan partisi.
- **Penyimpanan Tersier**: Media seperti optik dan pita magnetik juga diatur meskipun kecepatan bukan prioritas.

## 7. Caching
- **Prinsip**: Data yang sering digunakan disalin sementara ke penyimpanan lebih cepat untuk akses lebih efisien.
- **Lapisan**: Caching diterapkan di perangkat keras, sistem operasi, dan perangkat lunak.
- **Manajemen Cache**: Mengatur kapasitas cache yang kecil dengan kebijakan penggantian yang tepat.
