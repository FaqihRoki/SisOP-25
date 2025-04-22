# LATIHAN PROGRAM: Implementasi Thread di Berbagai Platform

## 1. **Thread di Java (`SumTask.java`)**

Program `SumTask.java` memanfaatkan **Framework Fork/Join** untuk menjalankan tugas secara paralel di Java. Pendekatan ini membagi beban kerja besar menjadi bagian-bagian kecil yang dapat dijalankan secara bersamaan di beberapa thread.

### **Struktur Kelas**
```java
public class SumTask extends RecursiveTask<Integer>
```
Kelas `SumTask` mewarisi `RecursiveTask<Integer>`, memungkinkan pembagian tugas secara rekursif dan eksekusi paralel.

### **Pembagian Tugas**
```java
if (end - begin < THRESHOLD) {
} else {
}
```
Ketika volume data lebih kecil dari nilai `THRESHOLD`, penjumlahan dilakukan secara langsung (**conquer**). Untuk dataset yang lebih besar, array dibagi menjadi dua subtugas (**divide**) untuk eksekusi paralel.

### **Eksekusi Paralel**
```java
leftTask.fork();
rightTask.fork();
return rightTask.join() + leftTask.join();
```
Setelah pembagian, dua subtugas (`leftTask` dan `rightTask`) dieksekusi secara paralel, dengan hasil yang digabungkan setelah semua thread selesai.

### **Penggunaan ForkJoinPool**
```java
ForkJoinPool pool = new ForkJoinPool();
int sum = pool.invoke(task);
```
Dalam fungsi `main()`, sebuah array berisi 10.000 elemen acak dibuat dan diproses oleh objek `SumTask` menggunakan `ForkJoinPool`, yang secara otomatis mengelola thread-thread yang diperlukan.

Pendekatan Fork/Join memungkinkan penjumlahan dibagi menjadi subproses paralel, meningkatkan efisiensi pemrosesan, terutama pada sistem multi-core.

---

## 2. **Thread di Linux (`thrd-posix.c`)**

Program `thrd-posix.c` menggunakan **POSIX Thread** (pthreads) untuk mengelola eksekusi paralel di sistem operasi Linux. Program ini menjalankan thread tambahan untuk menghitung jumlah angka dari 0 hingga batas tertentu.

### **Membuat Thread Baru**
```c
pthread_t tid;
pthread_create(&tid, NULL, runner, argv[1]);
```
Fungsi `pthread_create()` menghasilkan thread baru. Parameter `runner` mendefinisikan fungsi yang dijalankan oleh thread, sementara `argv[1]` berisi batas numerik untuk perhitungan.

### **Fungsi Eksekusi Thread**
```c
void *runner(void *param) {
    int i, upper = atoi(param);
    sum = 0;
    for (i = 1; i <= upper; i++)
        sum += i;
    pthread_exit(0);
}
```
Thread yang dibuat menjalankan fungsi `runner`, yang mengkonversi parameter menjadi integer (`upper`), kemudian menjumlahkan angka dari 1 hingga `upper`.

### **Menunggu Penyelesaian Eksekusi**
```c
pthread_join(tid, NULL);
```
Thread utama tidak akan melanjutkan sampai thread tambahan menyelesaikan pekerjaannya, menggunakan `pthread_join()` untuk memastikan hasil siap digunakan.

Pendekatan ini memungkinkan pemrosesan yang lebih responsif dan fleksibel, karena tugas-tugas intensif dapat didelegasikan ke thread terpisah tanpa mengganggu eksekusi utama.

---

## 3. **Thread di Windows (`thrd-win32.c`)**

Program `thrd-win32.c` mengimplementasikan **thread di sistem operasi Windows** menggunakan API `CreateThread()`. Fungsinya sama dengan versi POSIX, melakukan penjumlahan angka hingga batas yang ditentukan melalui command line.

### **Membuat Thread Baru**
```c
DWORD ThreadId;
HANDLE ThreadHandle;
ThreadHandle = CreateThread(NULL, 0, Summation, argv[1], 0, &ThreadId);
```
`CreateThread()` membuat thread baru. Fungsi `Summation` akan dieksekusi dengan argumen yang didefinisikan oleh `argv[1]`.

### **Eksekusi Thread**
```c
DWORD WINAPI Summation(LPVOID Param) {
    int upper = atoi(Param);
    Sum = 0;
    for (int i = 1; i <= upper; i++)
        Sum += i;
    return 0;
}
```
Thread menjalankan fungsi `Summation`, yang mengkonversi parameter menjadi integer dan menghitung jumlah angka dari 1 hingga batas yang ditentukan.

### **Menunggu Penyelesaian Thread**
```c
WaitForSingleObject(ThreadHandle, INFINITE);
```
Untuk mencegah thread utama melanjutkan sebelum perhitungan selesai, `WaitForSingleObject()` memastikan eksekusi selesai sebelum hasil diakses.

Manajemen thread di Windows menggunakan `CreateThread()` menawarkan fleksibilitas lebih tetapi membutuhkan penanganan lebih eksplisit dibandingkan dengan pthreads di Linux, karena setiap thread memiliki pengidentifikasi sendiri (`HANDLE`), dan fungsi eksekusi harus mengikuti format tertentu.
