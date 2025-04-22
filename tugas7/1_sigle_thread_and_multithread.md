# Single Thread dan Multithread

## Single Thread
Single-threading adalah teknik pemrograman yang memungkinkan suatu proses berjalan dengan satu jalur eksekusi secara berurutan. Dalam metode ini, setiap tugas harus diselesaikan terlebih dahulu sebelum tugas berikutnya dapat dimulai. Pendekatan ini lebih sederhana dan mudah dikelola karena tidak memerlukan sinkronisasi antar thread atau menghadapi risiko kondisi balapan. Namun, dalam situasi yang memerlukan kecepatan dan pemrosesan paralel, single-threading bisa kurang efisien, terutama saat menangani operasi berat seperti pemrosesan data besar atau komunikasi jaringan.

## Multithread
Multithreading memungkinkan suatu program menjalankan beberapa jalur eksekusi secara bersamaan, meningkatkan efisiensi dan kecepatan pemrosesan. Dengan pendekatan ini, berbagai tugas dapat diproses tanpa harus menunggu satu sama lain. Sebagai contoh, dalam sebuah browser, satu thread dapat menangani pemuatan halaman sementara thread lain merespons input pengguna secara paralel. Teknik ini sangat berguna untuk meningkatkan performa aplikasi yang membutuhkan pemrosesan simultan.

![FotoSingle&Multi Thread](https://github.com/excotide/SisOp-25/blob/main/tugas7/thread.png)
