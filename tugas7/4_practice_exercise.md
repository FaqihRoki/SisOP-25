# TUGAS SISTEM OPERSI  MINGGU KE-7

---

![Image](https://github.com/user-attachments/assets/8a53bec9-2a18-4d15-8889-2bd3ce1d9467)

<b>Dosen Pengempu:
Dr.ferry Astika Saputra ST,M.Sc

Disusun oleh :
Abdullah Faqih(3124521026)D3-LA-IT-A</b

# PRACTICE EXERCISE: Konsep dan Implementasi Multithreading dalam Pemrograman

## **5.1 Berikan tiga contoh program yang memanfaatkan multithreading untuk meningkatkan performa dibanding solusi single-threaded.**
Multithreading dapat meningkatkan performa program secara signifikan. Berikut tiga contoh penerapannya:

- **Image Processing**  
  Program pengolah gambar dapat membagi gambar menjadi beberapa bagian dan memprosesnya secara paralel dengan multiple thread. Misalnya, penerapan filter pada foto beresolusi tinggi dapat dipercepat dengan memproses region berbeda secara bersamaan.

- **Game Engine**  
  Game modern menggunakan multithreading untuk memisahkan proses render grafis, physics calculation, AI, dan input pengguna. Hal ini memungkinkan game berjalan lancar tanpa bottleneck pada satu thread.

- **Database Server**  
  Server database menggunakan multithreading untuk menangani query dari banyak client secara bersamaan. Setiap thread dapat melayani permintaan berbeda, sehingga meningkatkan throughput dan responsivitas server.

---

## **5.2 Menggunakan Hukum Gustafson, hitung peningkatan kecepatan (speedup) aplikasi dengan 70% komponen paralel untuk (a) dua core dan (b) delapan core.**
Hukum Gustafson menghitung speedup dengan formula:

\[
\text{Speedup} = S + P \times N
\]

Dimana:
- \( S = 0.3 \) (30% komponen serial)
- \( P = 0.7 \) (70% komponen paralel)
- \( N \) = jumlah core

### **(a) Dengan 2 Core:**
\[
\text{Speedup} = 0.3 + 0.7 \times 2 = 0.3 + 1.4 = 1.7
\]

### **(b) Dengan 8 Core:**
\[
\text{Speedup} = 0.3 + 0.7 \times 8 = 0.3 + 5.6 = 5.9
\]

---

## **5.3 Apakah layanan streaming video yang menjalankan encoding video paralel menunjukkan task parallelism atau data parallelism? Jelaskan.**
Layanan streaming video yang melakukan encoding video paralel menerapkan **data parallelism**. Dalam proses ini:

- Video dibagi menjadi beberapa segmen (chunks)
- Setiap thread mengerjakan tugas encoding yang identik
- Perbedaannya hanya pada data (bagian video) yang diproses
- Hasil akhir digabungkan menjadi satu video yang terenkode

Ini merupakan contoh data parallelism karena operasi yang sama diterapkan pada bagian data yang berbeda secara paralel.

---

## **5.4 Apa perbedaan utama antara thread-pool dan fork-join model? Kapan sebaiknya menggunakan masing-masing model?**
### **Thread Pool**
- Kumpulan thread yang dibuat di awal dan siap digunakan
- Thread menunggu tugas di queue dan mengeksekusinya secara berurutan
- Menghindari overhead pembuatan dan penghapusan thread berulang

### **Fork-Join**
- Thread dibuat (fork) saat diperlukan untuk menyelesaikan subtask
- Thread bergabung kembali (join) setelah subtask selesai
- Cocok untuk algoritma divide-and-conquer

**Kapan Menggunakan:**  
- **Thread Pool**: Cocok untuk server yang menangani banyak permintaan dengan pola yang sama, seperti web server atau database server.
- **Fork-Join**: Lebih baik untuk tugas rekursif seperti sorting algorithm, tree traversal, atau problem solving dengan pendekatan divide-and-conquer.

---

## **5.5 Jelaskan bagaimana implementasi mutex dapat menyebabkan kondisi busy waiting dan bagaimana spin lock bekerja.**
### **Busy Waiting dengan Mutex**
Saat implementasi mutex menggunakan polling terus-menerus:
1. Thread mencoba mengakuisisi mutex yang sudah terkunci
2. Thread terus memeriksa status mutex dalam loop
3. CPU terus bekerja tanpa melakukan progress yang berarti
4. Menghabiskan siklus CPU untuk menunggu

### **Spin Lock**
Spin lock adalah implementasi mutex yang dirancang untuk busy waiting:
1. Thread mencoba mengakuisisi lock dengan instruksi atomik
2. Jika gagal, thread "berputar" (spin) dalam loop pendek
3. Thread terus mencoba tanpa menyerahkan kontrol ke scheduler
4. Efektif untuk waktu tunggu yang sangat singkat pada sistem multi-core

Spin lock efisien ketika waktu tunggu diperkirakan sangat singkat dan overhead context switch lebih besar dari waktu spinning.

---

## **5.6 Bandingkan sumber daya yang dibutuhkan saat menggunakan async/await pattern dibandingkan dengan thread konvensional.**
### **Thread Konvensional**
- Membutuhkan alokasi stack memory (biasanya 1MB per thread)
- Memerlukan context switching yang dikelola kernel
- Jumlah thread terbatas oleh memori sistem
- Overhead yang signifikan untuk pembuatan dan penghapusan

### **Async/Await Pattern**
- Menggunakan model eksekusi berbasis event
- Tidak memerlukan stack terpisah untuk setiap operasi asinkron
- Dapat menangani ribuan operasi konkuren dengan memori minimal
- Menggunakan state machine daripada thread terpisah

Async/await lebih efisien untuk operasi I/O-bound, sementara thread konvensional lebih cocok untuk tugas CPU-bound yang membutuhkan paralelisme sejati.

---

## **5.7 Dalam konteks multithreading, jelaskan perbedaan antara race condition, deadlock, dan starvation. Berikan contoh sederhana untuk masing-masing.**
### **Race Condition**
Kondisi di mana hasil eksekusi bergantung pada urutan eksekusi thread.

**Contoh Simple:**
```java
// Dua thread menambahkan nilai counter tanpa sinkronisasi
int counter = 0;

// Thread 1
counter++; // Baca, tambah, tulis

// Thread 2 (bersamaan)
counter++; // Baca, tambah, tulis

// Hasil akhir mungkin 1, bukan 2 yang diharapkan
```

### **Deadlock**
Situasi di mana dua atau lebih thread saling menunggu resource yang dikuasai oleh thread lain.

**Contoh Simple:**
```java
// Thread 1
synchronized(lockA) {
    // Melakukan sesuatu
    synchronized(lockB) {
        // Operasi dengan kedua lock
    }
}

// Thread 2 (bersamaan)
synchronized(lockB) {
    // Melakukan sesuatu
    synchronized(lockA) {
        // Operasi dengan kedua lock
    }
}
```

### **Starvation**
Kondisi di mana thread tidak mendapatkan akses ke sumber daya yang dibutuhkan dalam waktu yang wajar.

**Contoh Simple:**
```java
// Thread prioritas tinggi terus menerus mengakses resource
while(true) {
    synchronized(sharedResource) {
        // Thread prioritas tinggi menggunakan resource
        // untuk waktu yang lama
    }
}

// Thread prioritas rendah jarang mendapat giliran
synchronized(sharedResource) {
    // Thread ini jarang bisa mengakses resource
}
```

---

## **5.8 Jelaskan implementasi future dan promise dalam pemrograman asinkron. Bagaimana kedua konsep ini membantu dalam paralelisme?**
### **Future**
- Object yang mewakili hasil dari operasi asinkron
- Menyediakan metode untuk mengecek status (selesai/gagal)
- Memungkinkan pengambilan hasil saat operasi selesai

### **Promise**
- Mekanisme untuk mengatur status future
- Object yang dapat "menyelesaikan" (resolve) atau "menolak" (reject) future
- Biasanya digunakan oleh produsen (yang menjalankan tugas)

**Contoh Implementasi Sederhana:**
```javascript
// Membuat promise yang menyelesaikan tugas
let promise = new Promise((resolve, reject) => {
    // Operasi asinkron
    setTimeout(() => {
        const result = calculateValue();
        if (result) {
            resolve(result); // Sukses
        } else {
            reject("Calculation failed"); // Gagal
        }
    }, 1000);
});

// Menggunakan future (hasil promise)
promise
    .then(value => console.log("Result:", value))
    .catch(error => console.log("Error:", error));
```

Future dan promise membantu paralelisme dengan:
- Memungkinkan operasi non-blocking
- Menyediakan model untuk penanganan hasil asinkron
- Mendukung komposisi dan penggabungan tugas paralel
