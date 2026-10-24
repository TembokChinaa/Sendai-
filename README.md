# FisioNotes
## Aplikasi Dokumentasi Fisioterapi Offline-First untuk Android

**FisioNotes** adalah aplikasi Android berbasis Jetpack Compose yang dirancang untuk membantu fisioterapis mencatat, mengelola, dan mendokumentasikan sesi terapi pasien secara cepat, sistematis, dan terstruktur.

Aplikasi ini mengutamakan pengalaman pengisian catatan berbasis pilihan (*option-first*), pengelolaan pengukuran klinis secara *multi-entry*, serta penyimpanan lokal agar dapat digunakan tanpa koneksi internet.

---

## 1. Informasi Versi

**Nama Aplikasi:** FisioNotes  
**Versi:** `1.0.023`  
**Platform:** Android  
**Bahasa Pemrograman:** Kotlin  
**UI Toolkit:** Jetpack Compose dan Material 3  
**Metode Penyimpanan:** SharedPreferences dengan format JSON  
**Minimum Android:** Android 7.0 (API 24)  
**Target SDK:** Android 14 (API 34)

### Fokus Pengembangan Versi 1.0.023

Rilis ini berfokus pada peningkatan efisiensi dokumentasi fisioterapi melalui:

- Formulir catatan baru berbasis pilihan (*option-first*).
- Editor multi-entry untuk pengukuran ROM, MMT, modalitas, dan latihan.
- Skala respons pasien dengan indikator visual.
- Beranda interaktif dengan navigasi yang adaptif terhadap perangkat Android.
- Penyimpanan lokal serta fitur pencadangan dan pemulihan data.

---

## 2. Fitur Utama

### 2.1. Beranda Interaktif

Beranda dirancang sebagai pusat navigasi dan ringkasan aktivitas dokumentasi fisioterapi.

**Fitur yang tersedia:**

- **Sapaan dinamis:** Menyesuaikan dengan waktu pada perangkat, yaitu pagi, siang, sore, atau malam.
- **Hero Card:** Menampilkan jumlah kunjungan hari ini dan total catatan.
- **Quick Action Cards:** Pintasan menuju fitur Catatan Baru dan Semua Pasien.
- **Statistik interaktif:** Empat kartu statistik yang dapat ditekan untuk membuka daftar data terkait:
  - Total catatan.
  - Kunjungan hari ini.
  - Jumlah pasien unik.
  - Rata-rata skala nyeri.
- **Jadwal kontrol mendatang:** Menampilkan hingga tiga jadwal kontrol terdekat berdasarkan data catatan.
- **Catatan terbaru:** Menampilkan empat catatan terakhir dengan tombol untuk melihat seluruh catatan.
- **Empty state:** Menampilkan tombol Buat Catatan Pertama ketika belum terdapat catatan.
- **Ruang aman navigasi:** Menggunakan `padding bottom 120.dp` untuk mengurangi risiko konten tertutup oleh FAB atau bilah navigasi.

### 2.2. Catatan Baru  Wizard Lima Langkah

Formulir catatan baru menggunakan pendekatan *option-first*. Pengguna dapat memilih opsi yang tersedia sebelum memasukkan informasi secara manual.

#### Langkah 1 Data Pasien

Fitur pada tahap ini meliputi:

- Memilih pasien lama melalui tombol **Pilih Pasien Lama**.
- Mengisi otomatis nama pasien, nomor rekam medis, umur, dan jenis kelamin berdasarkan data yang tersedia.
- Memasukkan identitas pasien secara manual.
- Mengatur nomor sesi menggunakan kontrol stepper untuk menaikkan atau menurunkan nomor sesi.

#### Langkah 2 Keluhan Pasien

Tahap ini digunakan untuk mendokumentasikan keluhan utama pasien.

**Lokasi tubuh:** Tersedia pilihan 11 region tubuh serta kolom input manual.

**Diagnosis umum:** Pilihan diagnosis menyesuaikan region tubuh yang dipilih. Sebagai contoh, region lumbal dapat menampilkan pilihan seperti LBP, HNP, dan stenosis. Pengguna juga dapat memasukkan diagnosis secara manual.

**Keluhan utama:** Tersedia pilihan berikut:

- Nyeri.
- Kaku.
- Kelemahan.
- Kesemutan.
- Bengkak.
- Keterbatasan gerak.
- Kesulitan berjalan.
- Mudah lelah.

Pengguna dapat menambahkan keluhan melalui input manual.

**Skala nyeri:** Slider dengan rentang 0–10, dilengkapi emoji, label dinamis, dan indikator warna berdasarkan nilai yang dipilih.

#### Langkah 3 Pemeriksaan Fisioterapi

Tahap pemeriksaan menyediakan kolom anamnesis, pengukuran klinis, dan dokumentasi kemampuan fungsional.

**Anamnesis:** Kolom untuk mencatat informasi subjektif dan riwayat keluhan pasien.

**Range of Motion (ROM):** Editor multi-entry yang terdiri atas:

- Pilihan sendi.
- Pilihan hasil pemeriksaan: Normal, Terbatas, Nyeri saat Gerak, atau Kaku.
- Tombol tambah untuk memasukkan beberapa hasil pemeriksaan.

**Manual Muscle Testing (MMT):** Editor multi-entry yang terdiri atas:

- Pilihan otot atau sendi.
- Nilai kekuatan otot dari 0–5.
- Tombol tambah untuk memasukkan beberapa hasil pemeriksaan.

**Kemampuan fungsional:** Pilihan Mandiri, Bantuan Ringan, Bantuan Penuh, atau Imobilisasi.

**Catatan tambahan:** Kolom untuk mendokumentasikan temuan pemeriksaan lainnya.

#### Langkah 4 Intervensi Fisioterapi

Tahap ini digunakan untuk mencatat modalitas, terapi latihan, dan respons pasien terhadap intervensi.

**Modalitas fisioterapi:** Editor multi-entry yang menyediakan pilihan:

- TENS.
- Ultrasound (US).
- Microwave Diathermy (MWD).
- Infrared (IR).
- Cryotherapy.
- Traksi.
- Kompres hangat.

Setiap entri dilengkapi pilihan dosis atau parameter berbasis template FITT yang dapat disesuaikan oleh pengguna.

**Terapi latihan:** Editor multi-entry dengan pilihan:

- Strengthening.
- Stretching.
- ROM Exercise.
- Balance Training.
- Gait Training.
- Core Stability.

Setiap jenis latihan dilengkapi kolom dosis yang dapat diedit sesuai rencana terapi.

**Respons pasien:** Skala 1–5 dengan emoji, warna, dan label respons dari Sangat Tidak Membaik hingga Sangat Membaik. Kolom catatan opsional tersedia untuk menjelaskan respons pasien.

**Catatan intervensi tambahan:** Digunakan untuk menyimpan informasi lain yang berkaitan dengan pelaksanaan terapi.

#### Langkah 5 Rencana Terapi (*Plan*)

Tahap terakhir digunakan untuk menyusun tujuan, rencana intervensi, dan program latihan mandiri pasien.

**Tujuan terapi:** Editor multi-entry dengan pilihan aspek:

- Nyeri.
- Range of Motion (ROM).
- Kekuatan otot.
- Fungsi.
- Activities of Daily Living (ADL).
- Edukasi.

Setiap tujuan dapat dilengkapi target yang ingin dicapai.

**Rencana terapi:** Editor multi-entry untuk memasukkan jenis intervensi dan detail pelaksanaannya.

**Home Exercise Program (HEP):** Editor multi-entry untuk mencatat jenis latihan mandiri dan dosis latihan di rumah.

**Jadwal kontrol:** Kolom tanggal kontrol dan catatan kunjungan berikutnya.

**Ringkasan sebelum penyimpanan:** Kartu ringkasan menampilkan data yang telah diisi agar pengguna dapat memeriksa kembali catatan sebelum menyimpannya.

### 2.3. Format Penyimpanan Data Wizard

Data yang dihasilkan dari formulir disimpan dalam format teks terstruktur agar dapat dibaca kembali oleh aplikasi.

| Jenis Data | Format Penyimpanan |
|---|---|
| ROM | `Bagian=Hasil; Bagian=Hasil` |
| MMT | `Bagian=Hasil; Bagian=Hasil` |
| Tujuan terapi | `Bagian=Target; Bagian=Target` |
| Plan | `Intervensi=Detail; Intervensi=Detail` |
| HEP | `Jenis=Dosis; Jenis=Dosis` |
| Intervensi | `MOD§TENS=80Hz 20min§§LAT§Strengthening=3x10§§FREE§catatan` |
| Respons pasien | `4|catatan opsional` |

Format tersebut dirancang agar kompatibel dengan catatan dari versi sebelumnya. Ketika catatan lama diedit, data yang tersimpan dapat dibaca kembali dan ditampilkan pada antarmuka yang sesuai.

---

## 3. Manajemen Data Pasien

Fitur daftar pasien digunakan untuk mencari, memfilter, mengurutkan, dan mengelola catatan yang telah tersimpan.

### 3.1. Pencarian Pasien

Pencarian instan tersedia berdasarkan:

- Nama pasien.
- Nomor rekam medis.
- Diagnosis.
- Keluhan.
- Region tubuh.

### 3.2. Filter dan Pengurutan

Pengguna dapat menyaring data berdasarkan diagnosis yang tersedia di dalam catatan serta mengurutkan daftar menggunakan pilihan:

- Terbaru.
- Terlama.
- Nama A–Z.
- Skala nyeri tertinggi.

### 3.3. Kartu Pasien

Setiap kartu pasien dapat menampilkan:

- Informasi identitas dan ringkasan catatan.
- Accent stripe dengan warna berdasarkan tingkat nyeri.
- Badge nomor sesi, misalnya Sesi ke-2.
- Tombol hapus dengan dialog konfirmasi.

---

## 4. Detail Catatan Fisioterapi

Halaman Detail Catatan menampilkan dokumentasi secara lengkap dan terstruktur.

### 4.1. Identitas dan Informasi Kunjungan

Informasi yang ditampilkan meliputi:

- Data pasien dan nomor rekam medis.
- Umur dan jenis kelamin.
- Region tubuh.
- Diagnosis dan keluhan utama.
- Jadwal kontrol.

### 4.2. Dokumentasi SOAP

Catatan disajikan dalam empat bagian utama:

- **S Subjective:** Keluhan dan informasi subjektif pasien.
- **O Objective:** Hasil pemeriksaan dan pengukuran klinis.
- **A Assessment:** Interpretasi atau penilaian fisioterapi.
- **P Plan:** Rencana terapi dan tindak lanjut.

Tampilan dilengkapi indikator skala nyeri serta rincian pengukuran ROM, MMT, modalitas, terapi latihan, dan HEP.

### 4.3. Tombol Aksi

Empat tindakan utama tersedia pada halaman detail:

| Tombol | Fungsi |
|---|---|
| Edit | Mengubah catatan yang sudah tersimpan. |
| Follow-up Baru | Membuat catatan lanjutan berdasarkan kunjungan sebelumnya. |
| Share | Membagikan catatan dalam bentuk teks terformat. |
| Hapus | Menghapus catatan setelah konfirmasi pengguna. |

---

## 5. Duplikasi dan Follow-up Cepat

Fitur Follow-up Baru memudahkan pembuatan catatan kunjungan berikutnya tanpa harus mengisi ulang seluruh informasi pasien.

Saat digunakan, aplikasi akan:

1. Membuat salinan berdasarkan catatan sebelumnya.
2. Menaikkan nomor sesi secara otomatis sebanyak satu.
3. Memperbarui tanggal kunjungan menjadi tanggal perangkat saat ini.
4. Mengosongkan data intervensi dan respons pasien agar dapat diisi kembali.
5. Mempertahankan data subjektif, objektif, dan diagnosis sebagai dasar pencatatan lanjutan.

Catatan hasil duplikasi harus disimpan sebagai entri baru agar tidak menimpa catatan kunjungan sebelumnya.

---

## 6. Backup dan Restore

Fitur pencadangan dan pemulihan membantu pengguna menjaga keberlanjutan data saat berpindah perangkat atau melakukan pemulihan data.

### 6.1. Export Backup

Seluruh catatan dapat diekspor ke dalam berkas JSON. Berkas kemudian dapat dibagikan melalui aplikasi yang tersedia di perangkat, seperti WhatsApp, email, atau layanan penyimpanan berkas.

### 6.2. Import dari JSON

Pengguna dapat memilih berkas JSON melalui pemilih berkas Android.

Mekanisme import dirancang untuk:

- Membaca data dari berkas backup.
- Menambahkan catatan yang belum tersedia berdasarkan ID unik.
- Mempertahankan catatan lokal yang sudah ada.
- Menampilkan notifikasi jumlah catatan yang berhasil ditambahkan.

Validasi struktur JSON dan penanganan ID duplikat diperlukan untuk mencegah data tidak valid atau penggandaan catatan yang tidak diinginkan.

---

## 7. Berbagi Catatan Individual

Setiap catatan dapat dibagikan dalam format teks yang terstruktur dan mudah dibaca.

Informasi yang dapat dimasukkan meliputi identitas pasien, tanggal kunjungan, keluhan, temuan pemeriksaan, penilaian fisioterapi, intervensi, respons pasien, serta rencana tindak lanjut.

Hasil berbagi dapat digunakan melalui aplikasi pesan, email, atau aplikasi dokumentasi lainnya yang mendukung penerimaan teks.

---

## 8. Desain UI/UX

FisioNotes menggunakan pendekatan desain modern berbasis Material 3 dengan prioritas pada kemudahan penggunaan di perangkat Android.

### 8.1. Sistem Visual

- Material 3 dengan warna yang mengikuti tema aplikasi.
- Accent bar pada judul setiap bagian.
- Kartu dengan sudut membulat 16–24 dp.
- Elevasi ringan untuk memperjelas hierarki visual.
- Chip pilihan untuk mempercepat pengisian data.
- Emoji dan warna sebagai indikator visual untuk skala nyeri dan respons pasien.

### 8.2. Formulir dan Navigasi

- Dialog layar penuh dengan tinggi sekitar 92–94% layar.
- Penggunaan `imePadding()` agar formulir tidak tertutup oleh keyboard.
- `enableEdgeToEdge()` untuk mengatur tampilan di area status bar dan navigation bar.
- Navigasi bawah dengan ikon Beranda dan Pasien.
- Floating Action Button (FAB) dengan ikon tambah untuk membuat catatan baru.
- Jarak aman di bagian bawah halaman agar elemen penting tetap mudah dijangkau.

### 8.3. Prinsip Pengalaman Pengguna

Antarmuka dirancang agar:

1. Pengisian catatan lebih cepat melalui pilihan yang relevan.
2. Pengguna tetap dapat memasukkan data secara manual.
3. Informasi klinis disajikan dalam bagian yang mudah dibaca.
4. Catatan dapat diperiksa sebelum disimpan.
5. Navigasi utama mudah diakses pada layar ponsel.

---

## 9. Privasi dan Penyimpanan Lokal

FisioNotes dirancang dengan pendekatan **offline-first**, yaitu fungsi utama aplikasi berjalan tanpa memerlukan koneksi internet.

### 9.1. Penyimpanan

- Menggunakan `SharedPreferences`.
- Menyimpan data dalam format JSON.
- Menggunakan key penyimpanan `fisionotes_interactive`.
- Tidak memerlukan server untuk proses penyimpanan dan pembacaan catatan lokal.

### 9.2. Akses Perangkat

Aplikasi tidak memerlukan izin khusus untuk fungsi pencatatan lokal. Pemilihan berkas backup dan restore menggunakan file picker Android.

### 9.3. Batasan Keamanan

Penyimpanan lokal tidak otomatis menjamin data medis terenkripsi. Karena aplikasi dapat menyimpan identitas dan informasi kesehatan pasien, pengembangan berikutnya perlu mempertimbangkan enkripsi data, perlindungan akses aplikasi, mekanisme pemulihan yang aman, serta pengelolaan berkas backup secara hati-hati.

Berkas backup dapat berisi informasi sensitif sehingga pengguna perlu memastikan berkas hanya dibagikan kepada pihak yang berwenang.

---

## 10. Arsitektur dan Teknologi

| Komponen | Teknologi |
|---|---|
| Bahasa pemrograman | Kotlin |
| UI Toolkit | Jetpack Compose |
| Sistem desain | Material 3 |
| Penyimpanan lokal | SharedPreferences |
| Format data | JSON |
| Pengolahan JSON | `org.json` |
| Navigasi | State-based tab navigation |
| Dialog | Compose Dialog dengan tampilan hampir layar penuh |
| Minimum SDK | API 24  Android 7.0 |
| Target SDK | API 34  Android 14 |

### Struktur Utama

File utama aplikasi:

`MainActivity.kt`

File ini menjadi titik masuk aplikasi dan menampung implementasi antarmuka serta alur utama sesuai struktur proyek saat ini.

Untuk memudahkan pemeliharaan ketika aplikasi berkembang, implementasi berikutnya dapat dipisahkan ke dalam komponen UI, model data, repository penyimpanan, dan utilitas backup/restore.

---

## 11. Ringkasan

FisioNotes versi `1.0.023` merupakan aplikasi dokumentasi fisioterapi Android yang berfokus pada pencatatan SOAP, pengelolaan data pasien, pengukuran klinis multi-entry, dokumentasi intervensi, tindak lanjut, serta pencadangan dan pemulihan data.

Dengan pendekatan offline-first, aplikasi dapat digunakan untuk pencatatan lokal tanpa koneksi internet. Desain berbasis Jetpack Compose dan Material 3 mendukung pengalaman penggunaan yang lebih terstruktur, responsif, dan praktis bagi fisioterapis.

**Fokus utama FisioNotes:** dokumentasi fisioterapi yang cepat, terstruktur, mudah dikelola, dan dapat digunakan secara offline.
