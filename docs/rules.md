# ClynSchedule — Development Rules & Coding Guidelines

## 1. Overview

Dokumen ini berisi aturan dan standar pengembangan proyek **ClynSchedule**, sebuah aplikasi Dynamic Time-Blocking & Smart Cascade Scheduler yang memungkinkan pengguna mengatur jadwal harian secara dinamis.

Tujuan utama dokumen ini adalah menjaga konsistensi kode, struktur proyek, kualitas implementasi, keamanan, dan kemudahan pemeliharaan aplikasi.

Dokumen ini wajib menjadi acuan bagi seluruh developer dan AI coding assistant yang berkontribusi dalam proyek ClynSchedule.

### Main Objectives

- Menjaga struktur kode tetap modular dan terorganisasi.
- Menggunakan standar penamaan yang konsisten.
- Memisahkan business logic dari UI.
- Menjaga integritas data dan jadwal pengguna.
- Memastikan Smart Cascade Engine bekerja sesuai aturan.
- Menghindari duplikasi kode dan implementasi yang tidak diperlukan.
- Memastikan aplikasi responsif, mudah digunakan, dan mudah dikembangkan.

---

## 2. Technology Stack Rules

Seluruh implementasi harus mengikuti teknologi yang telah ditetapkan dalam `architecture.md`.

| Layer | Technology |
|---|---|
| **Web Frontend** | React + TypeScript |
| Web Build Tool | Vite |
| Web Styling | Tailwind CSS |
| Web Icons | Lucide React |
| Web Routing | React Router |
| Web Local Storage | IndexedDB |
| Web PWA | vite-plugin-pwa |
| **Mobile Frontend** | Expo (React Native + TypeScript) |
| Mobile Navigation | Expo Router |
| Mobile Styling | NativeWind / Tailwind CSS |
| Mobile Icons | Lucide React Native |
| Mobile Local Storage | AsyncStorage & Expo SQLite |
| Mobile Push & Local Notif | Expo Notifications |
| Mobile Haptics | Expo Haptics |
| Mobile Build & Tooling | Expo Application Services (EAS) |
| **Shared Client State** | Zustand (Global UI State) & TanStack Query (Server State) |
| **BaaS & Platform** | Supabase (Managed PostgreSQL, Supabase Auth, RLS) |
| **Backend** | Node.js + Express.js |
| Backend Language | TypeScript |
| Database | PostgreSQL (Supabase) |
| Authentication | Supabase Auth (JWT) |
| ORM | Prisma ORM |
| Validation | Zod |
| Logging | Pino |
| Testing | Vitest & React Native Testing Library |

### Technology Restrictions

1. Jangan menambahkan framework atau library baru tanpa alasan teknis yang jelas.
2. Jangan menggunakan JavaScript biasa untuk modul baru jika TypeScript sudah ditetapkan.
3. Jangan mencampurkan business logic dengan komponen UI web atau mobile.
4. Jangan mengakses database secara langsung dari komponen frontend atau mobile.
5. Jangan menyimpan secret, API key, atau database credentials di aplikasi client.
6. Gunakan library yang sudah tersedia sebelum membuat implementasi alternatif sendiri.
7. Setiap penambahan dependency harus memiliki tujuan dan manfaat yang jelas.
8. Jangan mengimpor atau menggunakan elemen DOM Web (`div`, `span`, `p`, `window`, `document`, `localStorage`) di dalam direktori `mobile/`.

---

## 3. Project Structure Rules

Gunakan struktur direktori modular sesuai pembagian `web/`, `mobile/`, dan `backend/`.

### Root Workspace Structure

```text
clynflow-workspace/
├── docs/                     # Dokumentasi arsitektur, PRD, rules, schema, dan design
├── web/                      # Aplikasi Web Frontend (React + Vite PWA)
├── mobile/                   # Aplikasi Mobile Frontend (Expo + React Native)
└── backend/                  # Aplikasi Backend API (Node.js + Express + Prisma)
```

### Web Structure (`web/`)

```text
web/
├── public/
│   ├── icons/
│   └── manifest.json
│
├── src/
│   ├── assets/
│   ├── components/
│   │   ├── ui/
│   │   ├── layout/
│   │   ├── activity/
│   │   ├── schedule/
│   │   └── dashboard/
│   │
│   ├── pages/
│   │   ├── DashboardPage.tsx
│   │   ├── SchedulePage.tsx
│   │   ├── HistoryPage.tsx
│   │   └── SettingsPage.tsx
│   │
│   ├── hooks/
│   ├── services/
│   ├── stores/
│   ├── types/
│   ├── utils/
│   ├── lib/
│   ├── styles/
│   ├── App.tsx
│   └── main.tsx
│
├── package.json
└── vite.config.ts
```

### Mobile Structure (`mobile/` - Expo)

```text
mobile/
├── app/
│   ├── (tabs)/
│   │   ├── _layout.tsx
│   │   ├── index.tsx         # Dashboard mobile screen
│   │   ├── schedule.tsx      # Timeline & schedule screen
│   │   ├── history.tsx       # Riwayat perubahan & Undo
│   │   └── settings.tsx      # Pengaturan & preferensi pengguna
│   │
│   ├── activity/
│   │   ├── [id].tsx          # Form edit aktivitas
│   │   └── create.tsx        # Form pembuatan aktivitas baru
│   │
│   ├── cascade-preview.tsx   # Modal sheet pratinjau Smart Cascade
│   └── _layout.tsx           # Root provider layout
│
├── assets/
│   ├── icon.png
│   ├── splash.png
│   └── adaptive-icon.png
│
├── src/
│   ├── components/
│   │   ├── ui/               # Button, Input, Card native
│   │   ├── layout/           # SafeScreen, Header, BottomSheet
│   │   ├── activity/         # ActivityCard, StatusBadge, TimerWidget
│   │   └── schedule/         # DailyTimeline, ConflictBanner
│   │
│   ├── hooks/                # Custom React Native hooks
│   ├── services/             # API client & local notification service
│   ├── stores/               # Zustand UI stores
│   ├── storage/              # AsyncStorage & SQLite helper
│   ├── types/                # Shared domain interfaces
│   └── utils/                # Date/time & schedule formatters
│
├── app.json
├── babel.config.js
├── tailwind.config.js
├── tsconfig.json
└── package.json
```

### Backend Structure (`backend/`)

```text
backend/
├── prisma/
│   ├── schema.prisma
│   └── migrations/
│
├── src/
│   ├── config/
│   ├── modules/
│   │   ├── activities/
│   │   │   ├── activity.controller.ts
│   │   │   ├── activity.service.ts
│   │   │   ├── activity.repository.ts
│   │   │   ├── activity.routes.ts
│   │   │   └── activity.schema.ts
│   │   │
│   │   ├── scheduling/
│   │   ├── cascade/
│   │   ├── history/
│   │   ├── reminders/
│   │   └── auth/
│   │
│   ├── middlewares/
│   ├── utils/
│   ├── types/
│   ├── app.ts
│   └── server.ts
│
├── tests/
├── package.json
└── tsconfig.json
```

### Folder Responsibilities

| Folder | Responsibility |
|---|---|
| `components/` | Reusable UI components (Web & Mobile native) |
| `pages/` (Web) | Halaman utama aplikasi web |
| `app/` (Mobile) | Screen dan routing berbasis file (Expo Router) |
| `hooks/` | Custom hooks untuk state, sensor, network, atau data fetching |
| `services/` | Komunikasi dengan REST API dan native services (Notifications) |
| `stores/` | Global client UI state (Zustand) |
| `types/` | TypeScript interfaces dan contract types |
| `utils/` | Helper functions dan time-calculation utilities |
| `modules/` | Backend business modules |
| `controllers/` | Menangani HTTP request dan response |
| `services/` | Menjalankan business logic backend |
| `repositories/` | Mengelola akses database PostgreSQL via Prisma |
| `middlewares/` | Authentication, validation, dan error handling |
| `prisma/` | Database schema dan migrations |

Jangan membuat file dengan tanggung jawab yang terlalu banyak. Pecah modul apabila kompleksitasnya mulai meningkat.

---

## 4. Naming Conventions

Seluruh kode harus mengikuti aturan penamaan berikut.

| Element | Convention | Example |
|---|---|---|
| React Components | PascalCase | `ActivityCard.tsx` |
| Pages | PascalCase | `DashboardPage.tsx` |
| Functions | camelCase | `calculateDuration()` |
| Variables | camelCase | `activityList` |
| Constants | UPPER_SNAKE_CASE | `MAX_DURATION` |
| Interfaces | PascalCase | `ActivityBlock` |
| Types | PascalCase | `ActivityStatus` |
| Hooks | camelCase with use prefix | `useActivities()` |
| Files | kebab-case or module-specific convention | `schedule-service.ts` |
| Database Tables | snake_case | `activity_blocks` |
| Database Columns | snake_case | `start_minute` |
| API Routes | kebab-case | `/schedule-events` |

### Naming Rules

1. Gunakan nama yang menjelaskan fungsi dan tujuan.
2. Hindari nama terlalu pendek seperti `x`, `tmp`, atau `data1`, kecuali untuk variabel sementara dengan konteks yang jelas.
3. Gunakan kata kerja untuk nama function yang melakukan tindakan.
4. Gunakan kata benda untuk nama variabel dan objek.
5. Gunakan nama konsisten untuk status dan tipe aktivitas di seluruh aplikasi.

---

## 5. TypeScript Rules

TypeScript wajib digunakan untuk menjaga keamanan tipe data.

### Rules

1. Hindari penggunaan `any`.
2. Gunakan `unknown` jika tipe data belum diketahui.
3. Definisikan interface atau type untuk data API dan database.
4. Gunakan union types untuk status dan kategori yang memiliki nilai terbatas.
5. Hindari type assertion tanpa alasan yang kuat.
6. Jangan menduplikasi definisi tipe yang sama di banyak tempat.
7. Gunakan tipe khusus untuk request, response, dan domain model apabila strukturnya berbeda.

### Example

```ts
export type ActivityStatus =
  | "pending"
  | "active"
  | "completed"
  | "skipped";

export type BlockType = "flexible" | "fixed";

export type CascadeMode =
  | "ripple_shift"
  | "compress_duration";

export interface ActivityBlock {
  id: string;
  title: string;
  activityDate: string;
  startMinute: number;
  endMinute: number;
  duration: number;
  minDuration: number;
  blockType: BlockType;
  status: ActivityStatus;
  locked: boolean;
  allowCompression: boolean;
}
```

Gunakan shared domain types sebagai acuan antara frontend dan backend jika memungkinkan.

---

## 6. React (Web) and React Native / Expo (Mobile) Rules

### Shared Component & Business Logic Rules

1. Gunakan functional components dan React Hooks.
2. Setiap komponen harus memiliki tanggung jawab tunggal yang jelas (Single Responsibility Principle).
3. Pisahkan komponen yang dapat digunakan kembali ke dalam folder `components/ui/` masing-masing platform.
4. Hindari membuat satu komponen dengan terlalu banyak kondisi dan tanggung jawab.
5. Gunakan props dengan tipe TypeScript yang ketat dan eksplisit.
6. Hindari duplikasi logika bisnis; logika murni (perhitungan waktu, formatters, domain helpers) harus konsisten antara web dan mobile.
7. Jangan pernah menempatkan business logic Smart Cascade Engine di dalam komponen UI client.

### React Native & Expo Rules (Mobile)

1. **Native Primitives Only:** Selalu gunakan komponen native React Native (`View`, `Text`, `Pressable`, `ScrollView`, `FlatList`) atau wrapper khusus. Dilarang keras menggunakan elemen HTML DOM (`div`, `span`, `p`, `button`, `a`) pada kode di dalam `mobile/`.
2. **Expo Router Conventions:**
   - Gunakan navigasi file-based Expo Router: `app/(tabs)/` untuk tab utama (`index.tsx`, `schedule.tsx`, `history.tsx`, `settings.tsx`).
   - Gunakan nested routes untuk modal atau stack screens (misalnya `app/activity/[id].tsx` dan `app/cascade-preview.tsx`).
   - Gunakan layout wrapper `_layout.tsx` untuk konfigurasi stack atau tab navigation.
3. **Safe Area & Responsive Layout:** Selalu gunakan `react-native-safe-area-context` (`SafeAreaView` atau `useSafeAreaInsets`) agar konten tidak tertutup notch, dynamic island, atau navigation bar.
4. **Haptic Feedback:** Gunakan `expo-haptics` untuk memberikan respon getaran pada interaksi penting:
   - `Haptics.notificationAsync(NotificationFeedbackType.Success)` saat menyelesaikan aktivitas atau menerapkan Smart Cascade.
   - `Haptics.impactAsync(ImpactFeedbackStyle.Medium)` saat toggle Fixed Anchor atau tombol Start Now.
5. **No Web APIs:** Jangan memanggil `window`, `document`, atau `localStorage` di mobile. Gunakan `AsyncStorage` untuk key-value storage atau `Expo SQLite` untuk basis data lokal.
6. **Icons:** Gunakan `lucide-react-native` untuk ikon pada aplikasi mobile.
7. **Touch Targets:** Pastikan setiap tombol dan area interaktif memiliki ukuran sentuh minimum 44x44 pt.

### State Management Rules

Gunakan pembagian state berikut:

| State Type | Tool | Usage |
|---|---|---|
| Server State | TanStack Query | Data aktivitas dan history jadwal dari REST API |
| Global UI State | Zustand | Modal status, timer aktif, filter, preferensi UI sementara |
| Local State | React useState / useReducer | Input form dan interaksi lokal komponen |
| Offline Storage (Web) | IndexedDB | Cache data dan antrean mutasi offline PWA |
| Offline Storage (Mobile) | AsyncStorage & Expo SQLite | Cache jadwal, token auth, dan antrean mutasi offline |

Ketentuan:

- Jangan menggunakan global state untuk seluruh data jika tidak diperlukan.
- Jangan menyimpan data yang sama di beberapa state tanpa kebutuhan jelas.
- Gunakan query invalidation setelah perubahan data server.
- Tampilkan loading, error, dan empty state.
- Tangani perubahan offline dan proses sinkronisasi secara eksplisit.

### Styling Rules

1. **Web:** Gunakan Tailwind CSS sebagai sistem styling utama.
2. **Mobile:** Gunakan NativeWind (Tailwind CSS untuk React Native) atau `StyleSheet` yang mematuhi design tokens dari `design.md`.
3. Ikuti warna dan design tokens dari `design.md`.
4. Gunakan komponen UI yang konsisten di seluruh platform.
5. Pastikan tampilan mobile-first dan responsif.
6. Hindari inline styles acak di luar design system.
7. Pastikan kontras teks dan background mudah dibaca.

---

## 7. Backend and API Rules

### Backend Architecture

Backend harus menggunakan pola modular dengan pemisahan tanggung jawab:

- Controller: menangani request dan response.
- Service: menjalankan business logic.
- Repository: mengelola akses database.
- Schema: melakukan validasi input.
- Routes: mendefinisikan endpoint.

Controller tidak boleh berisi seluruh business logic.

### API Rules

1. Gunakan prefix `/api/v1`.
2. Gunakan HTTP methods sesuai fungsi.
3. Gunakan format JSON untuk request dan response.
4. Validasi setiap input dari client.
5. Gunakan status code HTTP yang sesuai.
6. Jangan mengirim stack trace atau informasi internal database kepada pengguna.
7. Semua endpoint yang memerlukan autentikasi harus memverifikasi identitas pengguna.
8. Setiap query data harus membatasi akses berdasarkan kepemilikan pengguna.

### HTTP Status Codes

| Status | Usage |
|---|---|
| 200 | Request berhasil |
| 201 | Data berhasil dibuat |
| 204 | Request berhasil tanpa response body |
| 400 | Request tidak valid |
| 401 | Belum terautentikasi |
| 403 | Tidak memiliki izin |
| 404 | Data tidak ditemukan |
| 409 | Konflik data atau jadwal |
| 422 | Validasi business rule gagal |
| 500 | Kesalahan internal server |

### API Response Format

Success:

```json
{
  "success": true,
  "message": "Activity created successfully",
  "data": {
    "id": "uuid",
    "title": "Belajar CPNS"
  }
}
```

Error:

```json
{
  "success": false,
  "message": "Schedule conflict detected",
  "error": {
    "code": "SCHEDULE_CONFLICT",
    "details": []
  }
}
```

Gunakan format response yang konsisten pada seluruh endpoint.

---

## 8. Database Rules

1. Gunakan Prisma ORM untuk mengakses PostgreSQL.
2. Semua tabel harus memiliki primary key.
3. Relasi antarentitas harus menggunakan foreign key.
4. Gunakan UUID untuk primary key.
5. Gunakan `snake_case` untuk nama tabel dan kolom database.
6. Gunakan migration untuk setiap perubahan schema.
7. Jangan mengubah migration yang sudah diterapkan pada production.
8. Gunakan database transaction untuk operasi yang mengubah banyak data.
9. Jangan menyimpan data sensitif yang tidak diperlukan.
10. Terapkan pembatasan akses berdasarkan `user_id`.
11. Gunakan index untuk query yang sering dilakukan.
12. Jangan mengandalkan validasi frontend sebagai satu-satunya perlindungan data.

### Database Integrity

Setiap aktivitas harus memenuhi aturan berikut:

- `start_minute` harus lebih kecil dari `end_minute`.
- `duration` harus sesuai dengan selisih waktu mulai dan selesai.
- `min_duration` tidak boleh melebihi `duration`.
- `priority` harus berada dalam rentang 1–5.
- Aktivitas Fixed Anchor tidak boleh digeser otomatis.
- Aktivitas Completed dan Skipped tidak boleh ikut cascade.

---

## 9. Smart Cascade Engine Rules

Smart Cascade Engine merupakan salah satu fitur inti ClynSchedule. Seluruh implementasinya harus mengikuti aturan berikut.

### General Rules

1. Cascade hanya boleh mengubah aktivitas yang memenuhi syarat.
2. Aktivitas Fixed Anchor tidak boleh digeser.
3. Aktivitas dengan `locked = true` tidak boleh diubah otomatis.
4. Aktivitas Completed dan Skipped harus dikecualikan dari perubahan jadwal.
5. Sistem harus memeriksa konflik sebelum perubahan diterapkan.
6. Semua perubahan harus dapat ditelusuri melalui Schedule History.
7. Operasi cascade harus mendukung Undo.
8. Jangan menerapkan perubahan sebagian jika transaksi keseluruhan gagal.

### Ripple Shift Rules

- Menggeser aktivitas fleksibel berdasarkan keterlambatan atau perubahan waktu.
- Mempertahankan durasi aktivitas.
- Tidak menggeser Fixed Anchor.
- Memeriksa kemungkinan konflik setelah pergeseran.
- Melanjutkan penyesuaian pada aktivitas fleksibel setelah anchor jika memungkinkan.
- Menghasilkan konflik jika tidak tersedia ruang penjadwalan yang valid.

### Compress Duration Rules

- Hanya aktivitas dengan `allow_compression = true` yang dapat dikompresi.
- Durasi tidak boleh lebih kecil dari `min_duration`.
- Aktivitas Fixed Anchor tidak boleh dikompresi.
- Aktivitas Locked, Completed, dan Skipped tidak boleh dikompresi otomatis.
- Prioritas dapat digunakan untuk menentukan urutan kompresi.
- Jika kapasitas penghematan waktu tidak cukup, sistem harus melaporkan konflik.

### Cascade Preview

Sebelum perubahan diterapkan, sistem harus dapat menampilkan:

- Aktivitas yang akan berubah.
- Waktu sebelum perubahan.
- Waktu setelah perubahan.
- Durasi yang dikurangi.
- Fixed Anchor yang dilindungi.
- Konflik yang ditemukan.
- Status apakah perubahan dapat diterapkan.

### Cascade Execution Flow

```text
Receive Schedule Change
        |
        v
Load Relevant Activities
        |
        v
Validate Input and Ownership
        |
        v
Calculate Schedule Changes
        |
        v
Protect Fixed Anchors
        |
        v
Run Conflict Detection
        |
        v
Generate Cascade Preview
        |
        v
Apply Changes in Transaction
        |
        v
Save History and Snapshot
        |
        v
Return Updated Schedule
```

Jangan menggabungkan proses preview dengan proses apply tanpa mekanisme validasi ulang. Data dapat berubah di antara kedua proses tersebut.

---

## 10. Time Management Rules

1. Gunakan minute-of-day untuk perhitungan jadwal harian.
2. Gunakan `TIMESTAMPTZ` untuk waktu aktual dan timestamp sistem.
3. Gunakan timezone pengguna untuk konversi waktu lokal.
4. Jangan menggunakan string waktu sebagai nilai perhitungan.
5. Pastikan hasil perhitungan tidak melewati batas hari yang didukung.
6. Hindari asumsi bahwa seluruh pengguna menggunakan timezone yang sama.
7. Tangani perubahan waktu lokal dan daylight saving time melalui timezone-aware conversion.

### Example

```ts
const startMinute = 8 * 60;
const endMinute = 9 * 60 + 30;

const duration = endMinute - startMinute;

console.log(duration); // 90
```

---

## 11. Error Handling and Logging Rules

### Error Handling

- Gunakan centralized error handler.
- Buat custom error untuk kesalahan business logic.
- Jangan menggunakan `try/catch` tanpa penanganan yang jelas.
- Berikan pesan error yang mudah dipahami.
- Bedakan validation error, authentication error, conflict error, dan server error.
- Jangan membocorkan informasi sensitif.

### Logging

Gunakan Pino untuk logging backend.

Log yang diperbolehkan:

- Request ID.
- Jenis operasi.
- Durasi proses.
- Status operasi.
- Error code.
- Informasi debugging yang tidak sensitif.

Hindari mencatat:

- Password.
- Access token.
- API key.
- Session secret.
- Data pribadi yang tidak diperlukan.

---

## 12. Security Rules

Keamanan harus menjadi bagian dari seluruh proses pengembangan.

1. Gunakan authentication untuk endpoint yang memerlukan identitas pengguna.
2. Gunakan authorization untuk memeriksa kepemilikan data.
3. Validasi input menggunakan Zod.
4. Gunakan HTTPS pada production.
5. Simpan secret dalam environment variables.
6. Jangan menyimpan secret di repository Git.
7. Gunakan `.env.example` tanpa nilai secret.
8. Terapkan rate limiting pada endpoint yang sensitif.
9. Gunakan secure cookie settings jika autentikasi berbasis cookie.
10. Cegah akses data lintas pengguna.
11. Terapkan CORS sesuai domain aplikasi.
12. Terapkan Row Level Security (RLS) di Supabase dan verifikasi token JWT Supabase Auth pada middleware backend Express untuk mencegah akses data lintas pengguna.

---

## 13. PWA, Mobile App, and Offline Rules

ClynSchedule harus tetap dapat digunakan ketika koneksi internet tidak tersedia, sesuai batasan fitur offline.

### PWA Rules (Web)

- Gunakan Service Worker untuk cache asset aplikasi web.
- Gunakan manifest untuk instalasi PWA di desktop dan browser mobile.
- Pastikan tampilan responsif dan nyaman digunakan.
- Sediakan indikator status online dan offline.
- Simpan perubahan lokal ke IndexedDB.
- Sinkronkan perubahan ketika koneksi kembali tersedia.

### Mobile Offline & Notification Rules (Expo)

- Gunakan AsyncStorage untuk menyimpan token, preferensi, dan snapshot jadwal terbaru.
- Gunakan Expo SQLite untuk menyimpan entitas jadwal dan antrean mutasi (mutation queue) saat perangkat offline.
- Tampilkan banner status jaringan ketika perangkat offline.
- Gunakan `expo-notifications` untuk menjadwalkan notifikasi pengingat lokal (local scheduled alarms) yang dieksekusi langsung oleh sistem operasi (Android AlarmManager / iOS Notification Center) sehingga tetap berdering andal meskipun aplikasi ditutup.
- Gunakan Expo Push Service untuk notifikasi darurat atau notifikasi yang dipicu oleh backend.

### Offline Data Rules

1. Jangan menganggap IndexedDB atau AsyncStorage/SQLite sebagai pengganti database utama.
2. Tandai perubahan lokal yang belum tersinkronisasi (`is_synced: false`).
3. Tangani konflik ketika data lokal dan server berbeda (server authority dengan pemberitahuan ke user).
4. Gunakan client-generated UUID agar data baru yang dibuat offline dapat dikenali saat sinkronisasi.
5. Jangan menghapus data lokal sebelum sinkronisasi berhasil dikonfirmasi server.

---

## 14. Testing Rules

Testing wajib dilakukan pada fitur inti sebelum dianggap selesai.

### Testing Tools

- Vitest untuk unit testing backend dan web.
- React Testing Library untuk komponen frontend web.
- React Native Testing Library (RNTL) untuk komponen mobile Expo.
- Supertest untuk API testing.
- Integration testing untuk database dan cascade operations.

### Required Test Cases

| Module | Test Scenario |
|---|---|
| Activities | Create activity |
| Activities | Update activity |
| Activities | Delete activity |
| Activities | Validate duration |
| Scheduling | Sort activities by start time |
| Scheduling | Detect overlapping activities |
| Cascade | Ripple Shift |
| Cascade | Compress Duration |
| Cascade | Protect Fixed Anchor |
| Cascade | Exclude completed activities |
| Cascade | Exclude locked activities |
| Cascade | Detect unresolved conflicts |
| History | Save schedule snapshot |
| History | Undo schedule changes |
| Auth | Prevent unauthorized access |
| Offline | Save local changes |
| Sync | Handle synchronization conflicts |

### Smart Cascade Edge Cases

Minimal pengujian harus mencakup:

1. Aktivitas dimulai terlambat.
2. Aktivitas selesai lebih awal.
3. Aktivitas dilewati.
4. Aktivitas berlangsung lebih lama.
5. Terdapat Fixed Anchor di tengah jadwal.
6. Aktivitas fleksibel memiliki durasi minimum.
7. Tidak tersedia ruang waktu yang cukup.
8. Dua aktivitas mengalami bentrok.
9. Pengguna mengubah jadwal ketika cascade preview sedang terbuka.
10. Proses Undo dilakukan setelah perubahan lain terjadi.

Jangan menganggap fitur selesai hanya karena berjalan pada satu skenario normal.

---

## 15. Git and Version Control Rules

Gunakan Git untuk mengelola perubahan kode.

### Branch Naming

| Branch | Purpose |
|---|---|
| `main` | Production-ready code |
| `develop` | Development integration |
| `feature/*` | Fitur baru |
| `fix/*` | Perbaikan bug |
| `refactor/*` | Refactoring |
| `docs/*` | Dokumentasi |

### Commit Convention

Gunakan Conventional Commits.

| Prefix | Purpose |
|---|---|
| `feat:` | Menambahkan fitur |
| `fix:` | Memperbaiki bug |
| `docs:` | Mengubah dokumentasi |
| `style:` | Perubahan formatting atau styling |
| `refactor:` | Refactoring kode |
| `test:` | Menambahkan atau memperbarui test |
| `chore:` | Perubahan konfigurasi atau maintenance |

Examples:

```bash
git commit -m "feat: add activity management"
git commit -m "fix: prevent fixed anchor shifting"
git commit -m "docs: update database schema"
git commit -m "test: add cascade engine tests"
```

### Git Rules

- Jangan commit file `.env`.
- Jangan commit dependency build artifacts.
- Jangan melakukan perubahan langsung pada `main` tanpa proses review.
- Gunakan pull request untuk perubahan besar.
- Pastikan test dan build berhasil sebelum merge.

---

## 16. Documentation Rules

Dokumentasi harus diperbarui ketika ada perubahan penting.

File dokumentasi utama:

| File | Responsibility |
|---|---|
| `prd.md` | Product requirements |
| `architecture.md` | System architecture |
| `design.md` | UI/UX guidelines |
| `schema.md` | Database structure |
| `rules.md` | Development standards |

Aturan:

1. Jangan mengubah keputusan arsitektur tanpa memperbarui dokumentasi terkait.
2. Dokumentasikan endpoint API baru.
3. Dokumentasikan perubahan database.
4. Berikan komentar pada algoritma kompleks jika diperlukan.
5. Hindari komentar yang hanya mengulang kode.
6. Pastikan contoh kode dokumentasi sesuai dengan implementasi aktual.

---

## 17. AI Coding Assistant Rules

Bagian ini ditujukan untuk AI coding assistant seperti ChatGPT, Cursor, Claude Code, atau Antigravity yang membantu mengembangkan ClynSchedule.

### General Instructions

1. Selalu baca `prd.md`, `architecture.md`, `design.md`, `schema.md`, dan `rules.md` sebelum melakukan perubahan besar.
2. Pahami struktur proyek sebelum membuat atau mengubah file.
3. Jangan mengubah arsitektur utama tanpa persetujuan.
4. Jangan membuat fitur yang tidak termasuk scope tanpa alasan dan persetujuan.
5. Jangan menghapus kode yang masih digunakan.
6. Jangan mengganti teknologi yang telah ditetapkan tanpa alasan teknis.
7. Gunakan TypeScript dan standar penamaan yang sudah ditentukan.
8. Pisahkan UI, business logic, dan data access.
9. Gunakan komponen reusable.
10. Jangan membuat implementasi sementara seolah-olah sudah production-ready.

### Coding Workflow

Sebelum mengimplementasikan fitur:

1. Identifikasi kebutuhan fitur.
2. Periksa dokumentasi terkait.
3. Periksa file yang sudah tersedia.
4. Tentukan file yang perlu dibuat atau diubah.
5. Jelaskan pendekatan implementasi jika perubahan cukup besar.
6. Implementasikan perubahan secara bertahap.
7. Jalankan test dan build yang relevan.
8. Periksa kemungkinan regresi.
9. Perbarui dokumentasi jika diperlukan.

### Restrictions

AI coding assistant tidak boleh:

- Menghapus atau mengganti database schema secara sembarangan.
- Menonaktifkan validasi untuk mengatasi error.
- Mengabaikan perlindungan Fixed Anchor.
- Membuat algoritma cascade yang mengubah jadwal tanpa conflict detection.
- Menyimpan secret secara langsung di source code.
- Menggunakan data dummy sebagai data produksi.
- Mengklaim test berhasil jika belum dijalankan.
- Membuat dependency baru tanpa kebutuhan yang jelas.
- Mengubah banyak file yang tidak berhubungan dengan tugas.
- Mencampurkan elemen HTML DOM (`div`, `span`, `p`, `button`) ke dalam kode mobile Expo (`mobile/`).
- Mengabaikan konvensi file-based routing Expo Router di dalam direktori `mobile/app/`.

### Expected Output

Setiap implementasi fitur harus menyertakan:

- Ringkasan perubahan.
- Daftar file yang dibuat atau diubah.
- Penjelasan fungsi utama.
- Hasil pengujian yang benar-benar dijalankan.
- Catatan keterbatasan atau pekerjaan lanjutan jika ada.

---

## 18. Definition of Done

Sebuah fitur dianggap selesai apabila memenuhi kriteria berikut:

- [ ] Implementasi sesuai kebutuhan PRD.
- [ ] Mengikuti arsitektur proyek.
- [ ] Mengikuti design system.
- [ ] Mengikuti coding conventions.
- [ ] Validasi input sudah diterapkan.
- [ ] Error handling sudah tersedia.
- [ ] Tidak ada masalah keamanan yang diketahui dan belum ditangani.
- [ ] Test yang relevan berhasil.
- [ ] Build berhasil.
- [ ] Tampilan responsif jika fitur berkaitan dengan UI.
- [ ] Dokumentasi diperbarui jika diperlukan.

---

## 19. Final Development Principles

Seluruh pengembangan ClynSchedule harus berpegang pada prinsip berikut:

1. **Keep It Simple:** buat solusi sesederhana mungkin tanpa mengorbankan kebutuhan utama.
2. **Modular Architecture:** pisahkan setiap modul berdasarkan tanggung jawab.
3. **Maintainability:** tulis kode yang mudah dipahami dan dikembangkan.
4. **Data Integrity:** jangan mengorbankan konsistensi jadwal.
5. **User Control:** pengguna tetap memiliki kendali atas perubahan jadwal.
6. **Anchor Protection:** aktivitas penting tidak boleh berubah secara otomatis.
7. **Predictable Scheduling:** setiap perubahan harus dapat dipahami dan diprediksi pengguna.
8. **Test Before Release:** fitur penting harus diuji sebelum dirilis.

**Core Principle:**

ClynSchedule harus mampu menyesuaikan jadwal pengguna secara cerdas tanpa menghilangkan kendali pengguna atas aktivitasnya. Setiap perubahan harus aman, transparan, dapat dilacak, dan dapat dibatalkan apabila memungkinkan.