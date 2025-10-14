# Standar & Kerangka Kerja Keamanan Siber

## **Daftar Isi**

1. **Pendahuluan: Mengapa Membutuhkan Standar dan Framework?**
2. **ISO/IEC 27001:2013 - Sistem Manajemen Keamanan Informasi (ISMS)**
   - 2.1. Pengertian dan Konsep Inti
   - 2.2. Struktur Klausul (Ps 4-10) dan Annex A
   - 2.3. Siklus Hidup PDCA dalam ISO 27001
   - 2.4. Contoh dan Studi Kasus Penerapan
   - 2.5. Langkah-Langkah Implementasi dan Sertifikasi
3. **NIST Cybersecurity Framework (CSF) 1.1**
   - 3.1. Pengertian dan Tujuan
   - 3.2. Komponen Inti: Core, Profiles, dan Tiers
   - 3.3. Fungsi-Fungsi CSF: Identify, Protect, Detect, Respond, Recover
   - 3.4. Contoh dan Studi Kasus Penerapan
   - 3.5. Langkah-Langkah Implementasi
4. **Perbandingan ISO 27001 vs. NIST CSF**
5. **Integrasi Framework: Menggunakan ISO 27001 dan NIST CSF Secara Bersamaan**
6. **Tugas Praktikum / Studi Kasus**

---

### **1. Pendahuluan: Mengapa Membutuhkan Standar dan Framework?**

Dalam mengelola keamanan siber, organisasi sering dihadapkan pada kompleksitas yang tinggi. Pertanyaan seperti "Apakah kita sudah aman?" atau "Di mana harus memulai?" sulit dijawab tanpa sebuah peta. **Standar dan kerangka kerja (framework)** keamanan siber hadir untuk menjawab tantangan ini.

**Manfaat Menggunakan Framework:**

- **Menstandarisasi Pendekatan:** Menciptakan bahasa dan proses yang umum untuk manajemen risiko.
- **Menyediakan Best Practices:** Berisi kumpulan pengetahuan dan praktik terbaik dari para ahli global.
- **Membantu Prioritisasi:** Memungkinkan organisasi fokus pada upaya yang paling penting dan berisiko tinggi.
- **Meningkatkan Kredibilitas:** Demonstrasi komitmen terhadap keamanan informasi kepada klien, mitra, dan regulator.
- **Memenuhi Kepatuhan (Compliance):** Membantu mematuhi regulasi seperti PDPI, GDPR, PCI DSS, dll.

Dua framework paling berpengaruh saat ini adalah **ISO/IEC 27001** (standar internasional) dan **NIST Cybersecurity Framework** (yang banyak digunakan secara global, termasuk di Indonesia).

---

### **2. ISO/IEC 27001:2013 - Sistem Manajemen Keamanan Informasi (ISMS)**

#### **2.1. Pengertian dan Konsep Inti**

- **Apa itu?** ISO 27001 adalah standar internasional yang menyediakan spesifikasi untuk menerapkan, memelihara, dan terus meningkatkan **Sistem Manajemen Keamanan Informasi (ISMS)**.
- **Konsep Inti ISMS:** ISMS bukan hanya tentang teknologi, tetapi merupakan **sistem holistik** yang mencakup **orang (people), proses (process), dan teknologi (technology)**. ISMS adalah pendekatan sistematis untuk mengelola informasi sensitif perusahaan sehingga tetap aman.
- **Sertifikasi:** Organisasi dapat diaudit oleh lembaga sertifikasi independen (seperti TÜV, BSI, DNV) untuk mendapatkan sertifikat ISO 27001, yang meningkatkan kepercayaan pasar.

#### **2.2. Struktur Klausul (Ps 4-10) dan Annex A**

Standar ini dibagi menjadi dua bagian utama:

- **Klausul 4-10 (Bagian Wajib):** Menentukan persyaratan untuk menetapkan, menerapkan, memelihara, dan meningkatkan ISMS.
  - **Pasal 4:** Konteks Organisasi -> Memahami kebutuhan dan harapan pihak terkait.
  - **Pasal 5:** Kepemimpinan -> Komitmen manajemen puncak, membuat kebijakan.
  - **Pasal 6:** Perencanaan -> Menilai risiko, merumuskan tujuan keamanan.
  - **Pasal 7:** Dukungan -> Sumber daya, kompetensi, kesadaran, komunikasi.
  - **Pasal 8:** Operasi -> Melakukan penilaian risiko, menerapkan kontrol.
  - **Pasal 9:** Evaluasi Kinerja -> Pemantauan, audit internal, tinjauan manajemen.
  - **Pasal 10:** Peningkatan -> Menangani ketidaksesuaian, tindakan korektif.
- **Annex A (Bagian Informasi):** Berisi 114 kontrol keamanan yang terorganisir dalam 14 domain (A.5 - A.18), seperti kebijakan keamanan, manajemen aset, keamanan SDM, kontrol kriptografi, dll. Organisasi harus memilih kontrol yang relevan berdasarkan hasil penilaian risiko.

#### **2.3. Siklus Hidup PDCA dalam ISO 27001**

ISO 27001 mengadopsi siklus **Plan-Do-Check-Act (PDCA)** untuk perbaikan berkelanjutan.

- **PLAN (Rencanakan):** Menetapkan kebijakan, tujuan, proses, dan risiko terkait ISMS (Klausul 4,6).
- **DO (Lakukan):** Menerapkan dan mengoperasikan kebijakan, kontrol, proses, dan prosedur (Klausul 7,8).
- **CHECK (Periksa):** Memantau dan meninjau kinerja ISMS terhadap kebijakan dan tujuan (Klausul 9).
- **ACT (Tindak Lanjuti):** Melakukan tindakan perbaikan dan peningkatan berkelanjutan berdasarkan hasil audit dan tinjauan manajemen (Klausul 10).

#### **2.4. Contoh dan Studi Kasus Penerapan**

- **Perusahaan:** Sebuah FinTech startup (PT "Aman Digital").
- **Tujuan:** Mendapatkan kepercayaan investor dan mematuhi regulasi Otoritas Jasa Keuangan (OJK).
- **Penerapan ISO 27001:**
  1. **Plan:** Management menyetujui proyek ISMS. Tim ditunjuk. Risiko dinilai: ancaman utama adalah kebocoran data nasabah dan serangan DDoS. Tujuan: "Tidak ada kebocoran data pelanggan dalam 12 bulan."
  2. **Do:** Memilih kontrol dari Annex A yang relevan:
     - **A.9.2.1 (Akses Pengguna):** Menerapkan _Multi-Factor Authentication_ (MFA) untuk semua akses admin.
     - **A.10.1.1 (Kebijakan Penggunaan Kriptografi):** Mengenkripsi data sensitif nasabah baik saat disimpan (_at rest_) dan dikirim (_in transit_).
     - **A.13.2.1 (Manajemen Kerentanan):** Membuat prosedur patch management bulanan.
     - **A.7.2.2 (Security Awareness):** Menyelenggarakan pelatihan phishing simulation bagi semua karyawan.
  3. **Check:** Melakukan audit internal setiap 6 bulan. Memantau log akses dan insiden keamanan.
  4. **Act:** Hasil audit menunjukkan pelatihan perlu ditingkatkan. Materi pelatihan diperbarui dengan contoh serangan terbaru.

#### **2.5. Langkah-Langkah Implementasi dan Sertifikasi**

1. **Dapatkan Komitmen Manajemen Puncak.**
2. **Tentukan Ruang Lingkup ISMS** (apakah seluruh perusahaan atau hanya divisi tertentu).
3. **Lakukan Gap Analysis** (membandingkan praktik saat ini dengan persyaratan ISO 27001).
4. **Lakukan Penilaian Risiko dan Perlakuan Risiko** (identifikasi risiko dan pilih kontrol dari Annex A).
5. **Dokumentasikan Semua Proses dan Kebijakan** (misalnya, Kebijakan Kemanan Informasi, Prosedur Incident Response).
6. **Implementasikan Kontrol dan Prosedur.**
7. **Lakukan Pelatihan dan Sosialisasi** kepada semua karyawan.
8. **Lakukan Audit Internal.**
9. **Tinjauan Manajemen** untuk mengevaluasi kinerja ISMS.
10. **Pilih Lembaga Sertifikasi** dan lakukan **Audit Sertifikasi** (Tahap 1: review dokumen, Tahap 2: audit utama).
11. **Pertahankan dan Tingkatkan** secara berkelanjutan.

---

### **3. NIST Cybersecurity Framework (CSF) 1.1**

#### **3.1. Pengertian dan Tujuan**

- **Apa itu?** NIST CSF adalah framework berbasis risiko yang menyediakan panduan bagi organisasi untuk mengelola dan mengurangi risiko siber. Berbeda dengan ISO 27001, CSF **tidak untuk disertifikasi** tetapi sebagai pedoman praktis dan fleksibel.
- **Tujuan:** Membantu organisasi memahami, mengelola, dan mengurangi risiko siber mereka serta melindungi infrastruktur dan data yang vital. CSF sangat baik untuk berkomunikasi dengan manajemen non-teknis.

#### **3.2. Komponen Inti: Core, Profiles, dan Tiers**

- **The Framework Core:** Sekumpulan aktivitas keamanan siber yang diinginkan, disusun dalam 5 Fungsi. Dinyatakan dalam bahasa yang mudah dipahami.
- **The Framework Profile:** Adalah penyesuaian Core sesuai dengan kebutuhan bisnis, toleransi risiko, dan sumber daya organisasi. Profile menjembatani kesenjangan antara "keadaan saat ini" (_Current Profile_) dan "keadaan yang diinginkan" (_Target Profile_).
- **The Framework Tiers:** Menggambarkan seberapa matang proses manajemen risiko siber suatu organisasi (dari Tier 1: Partial hingga Tier 4: Adaptive). Tiers membantu organisasi menilai tingkat kecanggihan mereka.

#### **3.3. Fungsi-Fungsi CSF: Identify, Protect, Detect, Respond, Recover**

Kelima fungsi ini membentuk siklus hidup manajemen risiko siber yang tinggi.

1. **IDENTIFY (Pahami):** Mengembangkan pemahaman organisasi untuk mengelola risiko terhadap sistem, aset, data, dan kemampuan.

   - **Contoh Aktivitas:** Membuat inventaris aset fisik dan software, menilai risiko, memahami kebijakan hukum dan regulatoris.

2. **PROTECT (Lindungi):** Mengembangkan dan menerapkan safeguards yang tepat untuk memastikan delivery of critical infrastructure services.

   - **Contoh Aktivitas:** Melatih kesadaran keamanan (awareness), menerapkan kontrol akses (MFA), mengamankan data (enkripsi), melakukan maintenance.

3. **DETECT (Deteksi):** Mengembangkan dan menerapkan aktivitas untuk mengidentifikasi kejadian siber.

   - **Contoh Aktivitas:** Memantau log dan jaringan secara terus-menerus, melakukan pemindaian kerentanan (_vulnerability scanning_).

4. **RESPOND (Tanggapi):** Mengembangkan dan menerapkan aktivitas untuk mengambil tindakan terhadap insiden siber yang terdeteksi.

   - **Contoh Aktivitas:** Membuat rencana tanggapan insiden (_Incident Response Plan_), melakukan analisis, komunikasi, dan mitigasi selama insiden.

5. **RECOVER (Pulihkan):** Mengembangkan dan menerapkan aktivitas untuk memulihkan layanan dan kemampuan yang terganggu akibat insiden siber.
   - **Contoh Aktivitas:** Membuat rencana pemulihan bencana (_DRP_), melakukan perbaikan, mengimplementasikan pelajaran yang didapat (_lessons learned_).

#### **3.4. Contoh dan Studi Kasus Penerapan**

- **Perusahaan:** Rumah Sakit "Sehat Sentosa".
- **Masalah:** Sering terjadi insiden ransomware yang mengganggu sistem rekam medis elektronik.
- **Penerapan NIST CSF:**
  1. **IDENTIFY:** Tim IT membuat inventaris semua perangkat medis yang terhubung ke jaringan. Mereka menemukan banyak perangkat tua dan rentan.
  2. **PROTECT:** Mereka memisahkan jaringan perangkat medis dari jaringan utama (_network segmentation_), melatih staf untuk tidak mengklik link email mencurigakan, dan menerapkan backup harian.
  3. **DETECT:** Memasang sistem pemantauan untuk mendeteksi aktivitas mencurigakan di jaringan.
  4. **RESPOND:** Membuat playbook khusus untuk menanggapi serangan ransomware (siapa yang harus dihubungi, bagaimana mengisolasi sistem).
  5. **RECOVER:** Melatih tim untuk memulihkan data dari backup yang bersih setelah serangan.

#### **3.5. Langkah-Langkah Implementasi**

1. **Prioritize and Scope:** Tentukan area bisnis mana yang akan difokuskan.
2. **Orient:** Identifikasi aset dan sistem terkait yang mendukung area bisnis tersebut.
3. **Create a Current Profile:** Tentukan kategori dan subkategori dari Framework Core mana yang saat ini sudah Anda terapkan (_Current State_).
4. **Conduct a Risk Assessment:** Analisis risiko operasional terhadap area bisnis tersebut.
5. **Create a Target Profile:** Tentukan kategori dan subkategori mana yang ingin Anda capai (_Target State_).
6. **Determine, Analyze, and Prioritize Gaps:** Bandingkan _Current_ dan _Target Profile_ untuk menemukan kesenjangan.
7. **Implement Action Plan:** Rencanakan dan lakukan tindakan untuk menutup kesenjangan tersebut.

---

### **4. Perbandingan ISO 27001 vs. NIST CSF**

| Aspek          | ISO 27001                                           | NIST CSF                                      |
| :------------- | :-------------------------------------------------- | :-------------------------------------------- |
| **Sifat**      | Standar Internasional (Sertifikasi)                 | Framework / Pedoman (Tidak untuk Sertifikasi) |
| **Struktur**   | Kaku, dengan klausul dan kontrol spesifik (Annex A) | Fleksibel, berbasis hasil dan kategori        |
| **Fokus**      | Membangun dan mengelola Sistem Manajemen (ISMS)     | Manajemen Risiko Siber dan Komunikasi         |
| **Pendekatan** | Proses-oriented, "Plan-Do-Check-Act"                | Outcome-oriented, "5 Functions"               |
| **Tujuan**     | Sertifikasi, kepatuhan global, kepercayaan pasar    | Peningkatan berkelanjutan, komunikasi risiko  |

---

### **5. Integrasi Framework: Menggunakan ISO 27001 dan NIST CSF Secara Bersamaan**

Kedua framework ini sangat **komplementer** (saling melengkapi), bukan bersaing.

- **Strategi:** Gunakan **NIST CSF sebagai peta** untuk mengidentifikasi area prioritas dan kesenjangan. Kemudian, gunakan **ISO 27001 (dan Annex A-nya) sebagai toolbox** untuk memilih kontrol spesifik yang akan diterapkan untuk menutup kesenjangan tersebut.
- **Contoh:** Dari profil NIST CSF, Anda menemukan kesenjangan dalam fungsi "DETECT". Anda kemudian melihat ke ISO 27001 Annex A kontrol **A.12.4.1 (Event Logging)** dan **A.16.1.2 (Reporting Information Security Events)** untuk menerapkan solusi logging dan monitoring yang memenuhi persyaratan kedua framework.

---

### **6. Tugas Praktikum / Studi Kasus**

**Judul Tugas:** Merancang Rencana Awal Penerapan Framework Keamanan Siber untuk Perusahaan "X"

**Instruksi:**

1. Pilih salah satu skenario perusahaan di bawah ini:

   - **Skenario A:** Sebuah Universitas swasta yang ingin melindungi data penelitian dan data mahasiswa.
   - **Skenario B:** Sebuah E-Commerce lokal yang mengalami pertumbuhan pesat dan sering mendapat serangan DDoS.
   - **Skenario C:** Sebuah Rumah Sakit pemerintah yang sistem rekam medisnya masih terisolasi dan ingin melakukan digitalisasi.

2. **Berdasarkan skenario pilihan Anda, jawab pertanyaan berikut:**
   - **Bagian 1 (ISO 27001):**
     - Sebutkan 3 pihak terkait (_stakeholders_) utama dan kebutuhan mereka terkait keamanan informasi.
     - Identifikasi 5 aset informasi paling kritis pada perusahaan tersebut.
     - Pilih 5 kontrol dari ISO 27001 Annex A yang paling prioritas untuk diterapkan dan jelaskan alasannya.
   - **Bagian 2 (NIST CSF):**
     - Untuk setiap fungsi CSF (Identify, Protect, Detect, Respond, Recover), sebutkan minimal 2 (dua) aktivitas yang harus dilakukan oleh perusahaan tersebut.
     - Buatlah sebuah _Target Profile_ sederhana dengan menentukan 3 tujuan keamanan siber yang ingin dicapai dalam 1 tahun ke depan.
   - **Bagian 3 (Analisis):**
     - Analisis bagaimana ISO 27001 dan NIST CSF dapat digunakan secara bersamaan untuk membantu perusahaan tersebut. Berikan 1 contoh konkret.

**Format Pengumpulan:**

- Dokumen PDF.
- Panjang: Maksimal 5 halaman (tidak termasuk sampul).
- Font: Times New Roman 12, spasi 1.5.
- Dikumpulkan dalam 2 minggu.
