# Migrasi dan Sejarah Sistem Operasi

## 1. Migrasi Fitur Sistem Operasi
Sistem operasi yang awalnya dirancang untuk mainframe, seperti MULTICS (Multiplexed Information and Computing Service), memengaruhi perkembangan sistem operasi modern seperti UNIX. Fitur manajemen memori, multitasking, dan proteksi sistem yang sebelumnya hanya ada di mainframe kini menjadi standar, termasuk di perangkat mobile.

---

## 2. Sistem Komputer Awal
Komputer seperti Manchester Mark 1 (1949) dan Ferranti Mark 1 (1951) menggunakan konsep stored-program. Programmer bertindak sebagai operator, memuat program secara manual dengan pita kertas atau kartu berlubang. Perkembangan perangkat keras dan perangkat lunak, seperti assembler dan compiler (FORTRAN, COBOL), mempermudah pemrograman tetapi meningkatkan kompleksitas operasi komputer.

---

## 3. Sistem Batch dan Spooling
- **Sistem Batch:** Menggunakan monitor residen untuk otomatisasi pekerjaan. Namun, masih terkendala I/O yang lambat.
- **Spooling:** Data input/output disimpan sementara di disk, memungkinkan CPU dan perangkat I/O bekerja bersamaan sehingga meningkatkan efisiensi.

---

## 4. Atlas
Atlas adalah sistem operasi berbasis paging pertama yang menggunakan drum sebagai memori utama dan core memory sebagai cache. Algoritma penggantian halaman canggih diterapkan untuk memprediksi akses memori.

---

## 5. XDS-940
Sistem operasi time-sharing ini mendukung beberapa proses pengguna secara bersamaan, menggunakan paging untuk relokasi memori, dan memperkenalkan konsep system call untuk pengelolaan sumber daya.

---

## 6. THE
Sistem batch dengan struktur lapisan bersih ini menggunakan semaphore untuk sinkronisasi proses dan banker's algorithm untuk mencegah deadlock. Paging diimplementasikan secara software.

---

## 7. RC 4000
Sistem ini adalah kernel dasar yang mendukung proses konkuren dan menggunakan message passing untuk komunikasi antar proses. Perangkat I/O juga dikelola sebagai proses.

---

## 8. CTSS dan MULTICS
- **CTSS:** Sistem time-sharing eksperimental yang memungkinkan beberapa pengguna mengakses sistem secara bersamaan.
- **MULTICS:** Mengembangkan konsep segmentasi dan paging memori serta sistem file hierarkis, menjadi inspirasi untuk sistem operasi modern.

---

## 9. IBM OS/360
Sistem operasi serbaguna ini menghadapi tantangan kompleksitas dan ukuran besar. Perkembangannya menghasilkan MVS (Multiple Virtual Storage), yang mendukung memori virtual.

---

## 10. CP/M dan MS-DOS
- **CP/M:** Sistem operasi awal untuk komputer berbasis Intel 8080.
- **MS-DOS:** Sistem operasi teks untuk PC IBM yang menjadi dominan pada era 1980-an, dengan set perintah yang lebih kaya dibanding CP/M.

---

## 11. Macintosh dan Windows
Macintosh memperkenalkan antarmuka grafis yang ramah pengguna, sementara Windows menjadi sistem operasi dominan untuk PC. Keduanya mendorong adopsi komputer pribadi di rumah dan kantor.

---

## 12. Mach
Mach dirancang untuk komputasi paralel dan terdistribusi, menggunakan mikrokernel modular yang menjadi dasar bagi macOS dan iOS.

---

## 13. Sistem Berbasis Kapabilitas (Hydra dan CAP)
- **Hydra:** Mendukung amplifikasi hak akses untuk fleksibilitas proteksi.
- **CAP:** Membagi kapabilitas menjadi data capability dan software capability untuk pengelolaan hak akses yang aman.

---

## 14. Sistem Operasi Lainnya
Sistem seperti MCP (untuk Burroughs) dan SCOPE (untuk CDC 6600) menawarkan fitur seperti dukungan multiple CPU dan manajemen memori canggih.
