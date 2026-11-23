# PRODUCT REQUIREMENTS DOCUMENT (PRD)
# ClynSchedule
**Dynamic Time-Blocking & Smart Cascade Scheduler**

| Informasi | Detail |
|---|---|
| Nama Produk | ClynSchedule |
| Jenis Produk | Aplikasi Penjadwalan Harian |
| Platform | Web Application & Progressive Web App (PWA) |
| Versi Dokumen | 1.0 |
| Status | Draft |
| Bahasa | Indonesia |
| Dokumen | Product Requirements Document |

---

# 1. PROJECT OVERVIEW

## 1.1 Deskripsi Produk

ClynSchedule adalah aplikasi pengelolaan jadwal harian berbasis Dynamic Time-Blocking yang dirancang untuk membantu pengguna mengatur, memantau, dan menyesuaikan aktivitas sehari-hari secara lebih fleksibel.

Berbeda dengan aplikasi To-Do List atau kalender konvensional yang umumnya hanya menampilkan daftar aktivitas berdasarkan waktu yang telah ditentukan, ClynSchedule memiliki mekanisme Smart Cascade Scheduling yang memungkinkan sistem menyesuaikan jadwal aktivitas berikutnya ketika terjadi perubahan pada aktivitas yang sedang berlangsung.

Penyesuaian tersebut dapat dilakukan ketika pengguna terlambat memulai aktivitas, membutuhkan waktu tambahan, menyelesaikan aktivitas lebih cepat, atau melewati aktivitas tertentu.

ClynSchedule juga menyediakan mekanisme Fixed Anchor Protection untuk melindungi aktivitas penting yang memiliki waktu tetap agar tidak ikut bergeser ketika sistem melakukan penyesuaian jadwal.

## 1.2 Visi Produk

Menjadi aplikasi penjadwalan harian yang adaptif dan cerdas, membantu pengguna mengelola waktu secara realistis tanpa harus terus-menerus menyusun ulang jadwal secara manual.

## 1.3 Misi Produk

1. Membantu pengguna menyusun jadwal aktivitas harian secara terstruktur.
2. Mengurangi pekerjaan manual ketika terjadi perubahan jadwal.
3. Mengoptimalkan penggunaan waktu melalui penyesuaian jadwal otomatis.
4. Melindungi aktivitas penting yang memiliki waktu tetap.
5. Memberikan pengalaman pengelolaan waktu yang sederhana, intuitif, dan mudah digunakan.

## 1.4 Unique Value Proposition

**"Your schedule should adapt to your life, not force your life to follow a rigid schedule."**

ClynSchedule menawarkan kemampuan penyesuaian jadwal secara dinamis sehingga pengguna tidak perlu mengatur ulang seluruh aktivitas secara manual setiap kali rencana berubah.

---

# 2. PROBLEM STATEMENT

## 2.1 Latar Belakang Masalah

Pengelolaan jadwal harian sering kali menghadapi kendala karena aktivitas yang direncanakan tidak selalu berjalan sesuai waktu yang telah ditentukan.

Beberapa kondisi yang sering terjadi adalah aktivitas dimulai terlambat, membutuhkan waktu lebih lama, selesai lebih cepat, atau bahkan tidak dapat dilaksanakan.

Pada aplikasi penjadwalan konvensional, perubahan tersebut sering kali mengharuskan pengguna menyesuaikan jadwal berikutnya secara manual. Hal ini dapat menghabiskan waktu dan menyebabkan jadwal menjadi tidak teratur.

Selain itu, aktivitas yang memiliki waktu tetap seperti ibadah, janji temu, dan kegiatan penting lainnya perlu mendapatkan perlindungan agar tidak terganggu oleh perubahan aktivitas yang bersifat fleksibel.

## 2.2 Identifikasi Masalah

ClynSchedule dikembangkan untuk mengatasi beberapa masalah berikut:

1. **Jadwal terlalu kaku:** Pengguna kesulitan menyesuaikan jadwal ketika aktivitas tidak berjalan sesuai rencana.
2. **Penyesuaian masih manual:** Pengguna harus mengubah waktu aktivitas berikutnya satu per satu ketika terjadi keterlambatan.
3. **Durasi aktivitas tidak konsisten:** Aktivitas dapat membutuhkan waktu lebih lama atau lebih cepat dari perkiraan.
4. **Aktivitas penting berisiko tergeser:** Tidak semua aplikasi penjadwalan memberikan mekanisme perlindungan terhadap aktivitas dengan waktu tetap.
5. **Waktu tidak dimanfaatkan secara optimal:** Waktu kosong akibat aktivitas selesai lebih cepat tidak selalu dimanfaatkan dengan baik.
6. **Kurangnya pemantauan aktivitas:** Pengguna kesulitan mengetahui aktivitas yang sedang berlangsung dan aktivitas berikutnya.

## 2.3 Rumusan Masalah

1. Bagaimana membantu pengguna mengelola jadwal harian secara fleksibel?
2. Bagaimana menyesuaikan jadwal berikutnya secara otomatis ketika terjadi perubahan aktivitas?
3. Bagaimana melindungi aktivitas penting agar tidak tergeser oleh proses penyesuaian jadwal?
4. Bagaimana mengoptimalkan durasi aktivitas ketika pengguna mengalami keterlambatan atau menyelesaikan aktivitas lebih cepat?
5. Bagaimana menyediakan pengalaman pengelolaan jadwal yang sederhana dan mudah digunakan?

---

# 3. PRODUCT GOALS

## 3.1 Tujuan Utama

Tujuan utama ClynSchedule adalah mengembangkan sistem penjadwalan harian yang mampu menyesuaikan jadwal secara dinamis berdasarkan kondisi aktivitas pengguna.

## 3.2 Tujuan Spesifik

- Menyediakan pengelolaan aktivitas harian dalam satu tampilan.
- Mengimplementasikan Smart Cascade Engine untuk penyesuaian jadwal otomatis.
- Menyediakan dua metode penyesuaian jadwal: Ripple Shift dan Compress Duration.
- Memisahkan aktivitas fleksibel dan aktivitas dengan waktu tetap.
- Menyediakan timer dan pengingat aktivitas.
- Menyimpan perubahan jadwal agar pengguna dapat melihat riwayat dan membatalkan perubahan.
- Mendukung penggunaan aplikasi melalui desktop dan perangkat mobile.

## 3.3 Target Pengguna

Target pengguna utama ClynSchedule adalah individu yang memiliki berbagai aktivitas harian dan membutuhkan pengelolaan waktu yang fleksibel.

Contoh target pengguna:

- Pelajar dan mahasiswa yang memiliki jadwal belajar.
- Freelancer yang mengelola beberapa pekerjaan.
- Developer yang memiliki jadwal pengerjaan proyek.
- Pencari kerja yang membagi waktu untuk mencari lowongan dan mempersiapkan lamaran.
- Individu yang ingin membangun rutinitas harian secara lebih teratur.

## 3.4 Contoh Aktivitas Pengguna

Aplikasi menyediakan beberapa contoh aktivitas awal yang dapat digunakan sebagai data demonstrasi:

| Aktivitas | Kategori |
|---|---|
| Belajar CPNS | Belajar |
| Mengerjakan Proyek Coding | Pekerjaan |
| Mencari Lowongan Kerja | Karier |
| Istirahat dan Ibadah | Pribadi |
| Bermain Game | Hiburan |

---

# 4. PROJECT SCOPE

## 4.1 In-Scope (Termasuk dalam Pengembangan)

Versi awal ClynSchedule akan berfokus pada pengelolaan jadwal harian dan mekanisme penyesuaian otomatis.

Fitur yang termasuk dalam ruang lingkup proyek:

1. Pengelolaan aktivitas (Create, Read, Update, Delete).
2. Tampilan jadwal harian berbasis timeline.
3. Pengaturan waktu mulai dan durasi aktivitas.
4. Status aktivitas.
5. Klasifikasi aktivitas fleksibel dan waktu tetap.
6. Smart Cascade Scheduling.
7. Ripple Shift.
8. Compress Duration.
9. Fixed Anchor Protection.
10. Start Now dan Re-align Now.
11. Complete Activity dan Skip Activity.
12. Activity Timer.
13. Pengingat aktivitas.
14. Deteksi keterlambatan berdasarkan waktu dan status aktivitas.
15. Riwayat perubahan jadwal dan Undo.
16. Penyimpanan data.
17. Tampilan responsif untuk desktop dan mobile.

## 4.2 Out-of-Scope (Tidak Termasuk MVP)

Fitur berikut tidak menjadi prioritas pengembangan versi awal:

- AI Schedule Assistant.
- Rekomendasi jadwal berbasis kecerdasan buatan.
- Estimasi durasi otomatis berdasarkan riwayat pengguna.
- Analitik produktivitas lanjutan.
- Habit Tracking lengkap.
- Sinkronisasi real-time multi-perangkat.
- Kolaborasi dan berbagi jadwal antar pengguna.
- Integrasi Google Calendar atau kalender eksternal.
- Sistem langganan dan pembayaran.
- Rekomendasi otomatis menggunakan machine learning.

Fitur tersebut dapat dipertimbangkan pada tahap pengembangan selanjutnya setelah fitur inti berjalan stabil.

---

# 5. MVP FEATURES

MVP (Minimum Viable Product) merupakan versi awal ClynSchedule yang berisi fitur paling penting untuk membuktikan fungsi utama produk.

## 5.1 Activity Management

Pengguna dapat membuat, melihat, mengubah, dan menghapus aktivitas.

Informasi aktivitas minimal meliputi:

- Nama aktivitas.
- Tanggal aktivitas.
- Waktu mulai.
- Durasi.
- Waktu selesai.
- Kategori.
- Status aktivitas.
- Jenis blok aktivitas.
- Pengaturan fleksibilitas durasi.

Status aktivitas:

| Status | Keterangan |
|---|---|
| Pending | Aktivitas belum dimulai |
| Active | Aktivitas sedang berlangsung |
| Completed | Aktivitas telah selesai |
| Skipped | Aktivitas dilewati |

## 5.2 Dynamic Daily Timeline

Menampilkan seluruh aktivitas dalam satu tampilan berdasarkan urutan waktu.

Fitur:

- Menampilkan jadwal harian.
- Menampilkan waktu mulai dan selesai.
- Menampilkan durasi aktivitas.
- Menampilkan status aktivitas.
- Menandai aktivitas yang sedang berlangsung.
- Menampilkan perubahan waktu setelah proses cascade.

## 5.3 Smart Cascade Engine

Merupakan fitur inti ClynSchedule yang bertugas menyesuaikan jadwal aktivitas berikutnya berdasarkan perubahan aktivitas sebelumnya.

Kondisi yang harus didukung:

**A. Start Late / Delay**

Ketika pengguna terlambat memulai aktivitas, sistem dapat menyesuaikan waktu aktivitas berikutnya.

**B. Extend Duration**

Ketika aktivitas membutuhkan waktu tambahan, pengguna dapat memperpanjang durasinya dan sistem menghitung ulang jadwal berikutnya.

**C. Complete Early**

Ketika aktivitas selesai lebih cepat, sistem dapat mengembalikan waktu yang tersisa ke jadwal berikutnya.

**D. Skip Activity**

Ketika pengguna melewati aktivitas, sistem dapat mengatur ulang jadwal berikutnya berdasarkan waktu yang tersedia.

**E. Re-align Now**

Pengguna dapat meminta sistem menyelaraskan kembali jadwal berdasarkan waktu saat ini.

## 5.4 Scheduling Modes

ClynSchedule menyediakan dua metode penyesuaian jadwal.

### A. Ripple Shift

Sistem menggeser aktivitas fleksibel berikutnya berdasarkan perubahan waktu aktivitas sebelumnya.

Contoh:

| Aktivitas | Jadwal Awal | Setelah Cascade |
|---|---|---|
| Belajar CPNS | 08.00–10.00 | 09.00–11.00 |
| Coding | 10.00–12.00 | 11.00–13.00 |
| Mencari Lowongan | 13.00–14.00 | 14.00–15.00 |

Ripple Shift mempertahankan durasi aktivitas fleksibel dan menggeser waktu mulai serta selesai sesuai kebutuhan.

### B. Compress Duration

Sistem mengurangi durasi aktivitas fleksibel untuk mengakomodasi keterlambatan tanpa selalu menggeser waktu selesai keseluruhan jadwal.

Contoh:

| Aktivitas | Durasi Awal | Setelah Kompresi |
|---|---:|---:|
| Coding | 120 menit | 90 menit |
| Mencari Lowongan | 60 menit | 45 menit |

Kompresi hanya boleh dilakukan jika aktivitas mengizinkannya dan durasinya tidak kurang dari batas minimum yang ditentukan pengguna.

Jika kapasitas waktu tidak mencukupi, sistem harus menampilkan konflik dan tidak boleh memaksakan penyesuaian.

## 5.5 Fixed Anchor Protection

Memungkinkan pengguna menentukan aktivitas yang tidak boleh digeser secara otomatis.

Contoh:

- Ibadah.
- Janji temu.
- Rapat.
- Waktu istirahat yang telah ditetapkan.
- Aktivitas penting lainnya.

Aturan:

- Fixed Anchor memiliki waktu mulai dan selesai yang dilindungi.
- Smart Cascade tidak boleh mengubah waktu Fixed Anchor.
- Aktivitas fleksibel dapat menyesuaikan jadwal di sekitar Fixed Anchor.
- Jika terjadi benturan yang tidak dapat diselesaikan, sistem harus menampilkan peringatan konflik.

## 5.6 Activity Timer

Menyediakan timer untuk membantu pengguna menjalankan aktivitas sesuai jadwal.

Fitur:

- Start.
- Pause.
- Resume.
- Complete.
- Menampilkan durasi berjalan.
- Menampilkan sisa waktu aktivitas.
- Mengidentifikasi aktivitas yang melewati durasi rencana.

## 5.7 Reminder & Notification

Memberikan pengingat kepada pengguna terkait aktivitas.

Fitur MVP:

- Pengingat sebelum aktivitas dimulai.
- Pengingat ketika waktu aktivitas dimulai.
- Pengingat aktivitas yang terlambat.
- Notifikasi penyelesaian atau perubahan jadwal yang relevan.

Notifikasi harus memperhatikan izin pengguna dan kemampuan platform. Pengingat berbasis browser tidak boleh diasumsikan tetap berjalan ketika aplikasi benar-benar tertutup tanpa mekanisme push atau penjadwalan tambahan.

## 5.8 Schedule History & Undo

Menyimpan riwayat perubahan jadwal yang dihasilkan oleh sistem maupun tindakan pengguna.

Fitur:

- Mencatat perubahan waktu aktivitas.
- Mencatat jenis tindakan.
- Menyimpan jadwal sebelum dan sesudah perubahan.
- Menyediakan fungsi Undo untuk membatalkan perubahan terakhir yang didukung.

---

# 6. FUNCTIONAL REQUIREMENTS

| ID | Kebutuhan Fungsional | Prioritas |
|---|---|---|
| FR-01 | Sistem dapat membuat aktivitas baru. | Must Have |
| FR-02 | Sistem dapat mengubah aktivitas. | Must Have |
| FR-03 | Sistem dapat menghapus aktivitas. | Must Have |
| FR-04 | Sistem menampilkan jadwal harian dalam bentuk timeline. | Must Have |
| FR-05 | Sistem menyediakan status aktivitas. | Must Have |
| FR-06 | Sistem dapat memulai dan menyelesaikan aktivitas. | Must Have |
| FR-07 | Sistem dapat melewati aktivitas. | Must Have |
| FR-08 | Sistem dapat mendeteksi aktivitas yang terlambat. | Must Have |
| FR-09 | Sistem dapat melakukan penyesuaian jadwal otomatis. | Must Have |
| FR-10 | Sistem menyediakan metode Ripple Shift. | Must Have |
| FR-11 | Sistem menyediakan metode Compress Duration. | Must Have |
| FR-12 | Sistem melindungi Fixed Anchor. | Must Have |
| FR-13 | Sistem menyediakan fitur Re-align Now. | Must Have |
| FR-14 | Sistem menyediakan Activity Timer. | Must Have |
| FR-15 | Sistem menyediakan pengingat aktivitas. | Should Have |
| FR-16 | Sistem menyimpan riwayat perubahan jadwal. | Should Have |
| FR-17 | Sistem menyediakan fitur Undo. | Should Have |
| FR-18 | Sistem menyimpan preferensi pengguna. | Should Have |

---

# 7. NON-FUNCTIONAL REQUIREMENTS

## 7.1 Performance

- Tampilan utama harus dapat dimuat dengan cepat pada perangkat yang didukung.
- Proses penyesuaian jadwal harus berjalan efisien untuk jadwal harian dengan jumlah aktivitas yang wajar.
- Perubahan jadwal harus ditampilkan tanpa perlu memuat ulang seluruh halaman.
- Operasi database harus menjaga konsistensi data.

## 7.2 Usability

- Antarmuka harus mudah dipahami oleh pengguna baru.
- Pengguna dapat melakukan tindakan utama dengan langkah sesedikit mungkin.
- Informasi aktivitas harus mudah dibaca.
- Tampilan harus responsif pada desktop, tablet, dan mobile.

## 7.3 Reliability

- Sistem tidak boleh menggeser Fixed Anchor secara otomatis.
- Sistem tidak boleh menghasilkan jadwal yang saling bertabrakan tanpa memberikan peringatan.
- Perubahan jadwal harus dapat divalidasi sebelum disimpan.
- Kegagalan proses cascade tidak boleh menyebabkan data jadwal menjadi tidak konsisten.

## 7.4 Security

- Data pengguna harus dilindungi.
- API harus melakukan validasi terhadap input.
- Endpoint yang mengakses data pribadi harus memiliki autentikasi dan otorisasi yang sesuai.
- Informasi sensitif tidak boleh disimpan secara sembarangan di frontend.
- Database harus menggunakan mekanisme akses yang aman.

## 7.5 Compatibility

- Mendukung browser modern.
- Mendukung tampilan desktop dan mobile.
- Memiliki fondasi Progressive Web App.
- Mendukung penggunaan offline untuk data yang telah tersimpan secara lokal, sesuai kemampuan implementasi.

---

# 8. TECHNICAL REQUIREMENTS

## 8.1 Technology Stack

| Bagian | Teknologi | Fungsi |
|---|---|---|
| Frontend | React | Membangun antarmuka aplikasi |
| Styling | Tailwind CSS | Mengelola tampilan dan design system |
| Programming Language | TypeScript | Menjaga konsistensi tipe data |
| Backend Runtime | Node.js | Menjalankan backend |
| Backend Framework | Express.js | Menyediakan REST API |
| Database | PostgreSQL | Menyimpan data aplikasi |
| Authentication | Supabase Auth (opsional) | Autentikasi pengguna |
| Database Hosting | Supabase (opsional) | Menyediakan layanan PostgreSQL terkelola |
| Local Storage | IndexedDB | Menyimpan data lokal untuk dukungan offline |
| PWA | Vite PWA Plugin | Mendukung instalasi aplikasi |
| Icons | Lucide React | Menyediakan ikon antarmuka |

## 8.2 Backend Responsibilities

Backend bertanggung jawab untuk:

1. Mengelola data aktivitas.
2. Memvalidasi perubahan jadwal.
3. Menjalankan Smart Cascade Engine.
4. Mengelola aturan Fixed Anchor Protection.
5. Menyimpan riwayat perubahan jadwal.
6. Mengelola preferensi pengguna.
7. Menyediakan endpoint untuk frontend.

## 8.3 Smart Cascade Engine Requirements

Algoritma Smart Cascade harus memenuhi aturan berikut:

1. Hanya aktivitas fleksibel yang boleh digeser secara otomatis.
2. Fixed Anchor tidak boleh berubah waktu.
3. Durasi aktivitas tidak boleh berada di bawah minimum yang ditetapkan.
4. Aktivitas yang sudah Completed atau Skipped tidak boleh diubah secara tidak sengaja.
5. Perubahan jadwal harus memperhatikan urutan waktu.
6. Sistem harus mendeteksi benturan antaraktivitas.
7. Sistem harus memperhatikan batas akhir jadwal harian.
8. Jika penyesuaian tidak memungkinkan, sistem harus menampilkan konflik.
9. Perubahan harus dapat divalidasi sebelum disimpan.
10. Setiap perubahan jadwal harus tercatat dalam riwayat.

## 8.4 Data Storage Strategy

MVP menggunakan PostgreSQL sebagai penyimpanan utama ketika backend sudah tersedia.

IndexedDB digunakan untuk menyimpan data lokal dan mendukung penggunaan offline.

Apabila keduanya digunakan bersamaan, mekanisme sinkronisasi harus dirancang secara eksplisit agar perubahan lokal dan server tidak saling menimpa.

---

# 9. USER FLOW

## 9.1 Alur Penggunaan Utama

1. Pengguna membuka ClynSchedule.
2. Sistem menampilkan dashboard dan jadwal hari ini.
3. Pengguna membuat atau memilih aktivitas.
4. Pengguna menentukan waktu, durasi, dan jenis aktivitas.
5. Pengguna memulai aktivitas menggunakan Start.
6. Sistem memantau waktu aktivitas.
7. Jika terjadi keterlambatan atau perubahan durasi, sistem menawarkan penyesuaian jadwal.
8. Pengguna memilih metode penyesuaian.
9. Sistem menjalankan Smart Cascade Engine.
10. Sistem memvalidasi perubahan dan menampilkan jadwal terbaru.
11. Pengguna dapat membatalkan perubahan melalui Undo jika diperlukan.

## 9.2 Alur Smart Cascade

**Contoh kondisi:**

Pengguna memiliki jadwal belajar CPNS pukul 08.00–10.00, tetapi baru selesai pukul 11.00.

1. Sistem mendeteksi keterlambatan selama 60 menit.
2. Sistem menghitung aktivitas berikutnya yang terdampak.
3. Sistem mengidentifikasi aktivitas Fixed Anchor.
4. Sistem menghitung penyesuaian menggunakan mode yang dipilih.
5. Sistem memeriksa durasi minimum, konflik, dan batas waktu.
6. Sistem menampilkan hasil penyesuaian.
7. Perubahan diterapkan dan disimpan setelah validasi.

---

# 10. SUCCESS METRICS

Keberhasilan MVP diukur berdasarkan indikator berikut.

| Indikator | Target Awal |
|---|---|
| Keberhasilan CRUD aktivitas | 100% operasi dasar berfungsi sesuai kebutuhan |
| Keberhasilan proses Smart Cascade | Minimal 95% pada skenario pengujian yang valid |
| Perlindungan Fixed Anchor | 100% terlindungi dalam skenario pengujian |
| Deteksi konflik jadwal | 100% pada skenario konflik yang telah didefinisikan |
| Konsistensi database | Tidak ada perubahan parsial yang merusak jadwal |
| Responsivitas UI | Dapat digunakan dengan baik pada desktop dan mobile |
| Penggunaan fitur inti | Pengguna dapat menyelesaikan alur penyesuaian jadwal tanpa bantuan teknis |

Target di atas merupakan sasaran pengujian awal, bukan klaim performa yang sudah dicapai.

## 10.1 Pengujian Keberhasilan Smart Cascade

Sistem harus diuji menggunakan beberapa kondisi:

- Aktivitas dimulai terlambat.
- Aktivitas berlangsung lebih lama.
- Aktivitas selesai lebih cepat.
- Aktivitas dilewati.
- Terdapat Fixed Anchor di antara aktivitas fleksibel.
- Durasi aktivitas tidak dapat dikompresi lagi.
- Waktu yang tersedia tidak mencukupi.
- Terjadi benturan dengan batas akhir hari.

---

# 11. DEVELOPMENT ROADMAP

## Phase 1 — MVP Foundation

Fokus: membangun fungsi utama penjadwalan.

- Setup frontend dan backend.
- Setup database.
- Activity Management.
- Dynamic Daily Timeline.
- Activity Status.
- Start, Complete, dan Skip.
- Smart Cascade Engine.
- Ripple Shift.
- Compress Duration.
- Fixed Anchor Protection.
- Re-align Now.
- Activity Timer.
- Responsive UI.

## Phase 2 — Productivity Enhancement

Fokus: meningkatkan pengalaman penggunaan.

- Reminder dan Notification.
- Schedule History.
- Undo dan Redo.
- Drag and Drop.
- Recurring Activities.
- Routine Templates.
- Offline PWA.
- Cloud Backup dan sinkronisasi data.

## Phase 3 — Smart Intelligence

Fokus: pengembangan kecerdasan sistem.

- AI Schedule Assistant.
- Smart Duration Estimation.
- Productivity Analytics.
- Habit Analysis.
- Schedule Optimization.
- Smart Break Suggestions.

---

# 12. PROJECT CONSTRAINTS

Batasan berikut harus diperhatikan selama pengembangan:

1. Pengembangan awal berfokus pada penjadwalan harian, bukan manajemen proyek kompleks.
2. MVP tidak memerlukan integrasi AI.
3. Sistem tidak boleh menggeser Fixed Anchor secara otomatis.
4. Sistem tidak boleh mengubah durasi di bawah batas minimum.
5. Sistem tidak boleh menerapkan perubahan jadwal jika terjadi konflik yang belum diselesaikan.
6. Fitur tambahan di luar scope harus dievaluasi sebelum diimplementasikan.
7. Perubahan arsitektur dan database harus mengikuti dokumentasi teknis.
8. Pengingat browser memiliki keterbatasan ketika aplikasi ditutup dan tidak boleh dijanjikan berjalan tanpa mekanisme pendukung.

---

# 13. ACCEPTANCE CRITERIA

MVP ClynSchedule dianggap memenuhi kebutuhan awal apabila:

- Pengguna dapat membuat, mengubah, melihat, dan menghapus aktivitas.
- Pengguna dapat melihat jadwal dalam bentuk timeline.
- Pengguna dapat memulai, menyelesaikan, dan melewati aktivitas.
- Sistem dapat melakukan penyesuaian jadwal menggunakan Ripple Shift.
- Sistem dapat melakukan penyesuaian durasi menggunakan Compress Duration.
- Sistem dapat melindungi Fixed Anchor.
- Sistem dapat mendeteksi dan melaporkan konflik jadwal.
- Sistem menyediakan Re-align Now.
- Sistem menyediakan Activity Timer.
- Sistem dapat menyimpan perubahan jadwal.
- Antarmuka dapat digunakan pada desktop dan perangkat mobile.

---

# 14. PRODUCT PRINCIPLES

Seluruh pengembangan ClynSchedule harus mengikuti prinsip berikut:

**1. Adaptability Over Rigidity**

Jadwal harus dapat menyesuaikan perubahan aktivitas pengguna.

**2. Protect Important Time**

Aktivitas penting yang memiliki waktu tetap harus dilindungi.

**3. Simplicity Over Complexity**

Antarmuka harus sederhana dan tidak dipenuhi fitur yang tidak diperlukan.

**4. User Control First**

Pengguna tetap memiliki kendali atas perubahan jadwal yang dilakukan sistem.

**5. Reliability Before Intelligence**

Keakuratan algoritma penjadwalan harus menjadi prioritas sebelum menambahkan fitur AI.

---

# 15. FINAL PRODUCT DEFINITION

ClynSchedule adalah aplikasi Dynamic Time-Blocking & Smart Cascade Scheduler yang membantu pengguna mengelola aktivitas harian secara fleksibel melalui penyesuaian jadwal otomatis.

Fokus utama produk adalah menyelesaikan permasalahan jadwal yang kaku, penyesuaian manual, serta risiko tergesernya aktivitas penting.

Melalui fitur Smart Cascade Engine, Ripple Shift, Compress Duration, dan Fixed Anchor Protection, ClynSchedule memungkinkan pengguna mengelola perubahan aktivitas tanpa harus menyusun ulang seluruh jadwal secara manual.

**Prinsip utama produk:**

"Plan your day. Adapt to changes. Stay on track."

---

**END OF DOCUMENT — ClynSchedule PRD v1.0**