# 📘 Modul Pembelajaran: Incident Response Plan (IRP)

## 🎯 **Capaian Pembelajaran**

Setelah menyelesaikan modul ini, mahasiswa mampu:

1. Menjelaskan konsep dan tujuan dari Incident Response Plan (IRP)
2. Mengidentifikasi tahapan utama dalam proses penanganan insiden keamanan siber
3. Menyusun contoh sederhana rencana penanganan insiden untuk organisasi atau sistem tertentu

## 🧭 **Deskripsi Singkat**

**Incident Response Plan (IRP)** adalah panduan langkah-langkah sistematis yang digunakan organisasi ketika terjadi *insiden keamanan siber* seperti serangan malware, kebocoran data, atau akses ilegal. Tujuan utamanya adalah **mengurangi dampak, mengendalikan kerusakan, dan memulihkan sistem dengan cepat.**

---

## 📖 **Materi Pembelajaran**

### 🎯 **1. Pengantar Insiden Keamanan Siber**

#### **Definisi Insiden Keamanan Siber**

Insiden keamanan siber adalah setiap kejadian yang mengancam kerahasiaan, integritas, atau ketersediaan informasi sistem.

#### **Kategori Insiden Keamanan:**

- **Insiden Kerahasiaan**: Kebocoran data, pencurian informasi
- **Insiden Integritas**: Perubahan data tanpa otorisasi, manipulasi informasi
- **Insiden Ketersediaan**: Serangan DDoS, ransomware yang mengunci akses

#### **Contoh Insiden Nyata:**

- Serangan phishing yang mencuri kredensial login
- Ransomware yang mengenkripsi data dan meminta tebusan
- Serangan DDoS yang membuat layanan tidak dapat diakses
- Akses tanpa izin oleh pihak eksternal ke sistem internal

### ⚙️ **2. Konsep Dasar Incident Response Plan**

#### **Definisi IRP**

IRP adalah dokumen formal yang berisi prosedur dan panduan yang menjelaskan bagaimana organisasi harus merespons ketika terjadi insiden keamanan siber.

#### **Tujuan IRP:**

- Menangani insiden secara cepat dan terkoordinasi
- Meminimalkan dampak bisnis dan finansial
- Memulihkan sistem ke kondisi normal secepat mungkin
- Memenuhi kewajiban hukum dan regulasi
- Meningkatkan kesiapan terhadap insiden di masa depan

#### **Manfaat Implementasi IRP:**

- Respons yang lebih terstruktur dan efektif
- Pengurangan waktu pemulihan (downtime)
- Perlindungan reputasi organisasi
- Pemenuhan kebutuhan compliance

### 🔄 **3. Tahapan Incident Response Plan (Framework NIST)**

#### **Tahap 1: Preparation (Persiapan)**

**Tujuan**: Membangun kapabilitas untuk merespons insiden secara efektif

**Aktivitas Utama:**

- Membentuk tim Incident Response
- Menyusun kebijakan dan prosedur IRP
- Menyiapkan tools dan infrastruktur
- Melakukan pelatihan dan simulasi
- Membuat komunikasi dan kontak darurat

**Contoh Implementasi:**

- Membuat contact list tim IR 24/7
- Menyiapkan incident management system
- Melakukan table-top exercises

#### **Tahap 2: Identification (Identifikasi)**

**Tujuan**: Mendeteksi dan mengonfirmasi terjadinya insiden

**Aktivitas Utama:**

- Monitoring dan deteksi anomali
- Analisis log dan alert
- Verifikasi insiden
- Klasifikasi tingkat keparahan

**Indikator Insiden:**

- Alert dari IDS/IPS
- Laporan dari pengguna
- Anomali pada log system
- Keluhan dari customer

#### **Tahap 3: Containment (Pembatasan)**

**Tujuan**: Mencegah penyebaran dan membatasi dampak insiden

**Jenis Containment:**

- **Short-term**: Tindakan segera (memutus koneksi, mematikan sistem)
- **Long-term**: Solusi berkelanjutan (isolasi jaringan, penerapan aturan firewall)

**Contoh Tindakan:**

- Memutus koneksi internet sistem terinfeksi
- Mengisolasi segment jaringan
- Mematikan service yang compromised

#### **Tahap 4: Eradication (Pemberantasan)**

**Tujuan**: Menghapus completely penyebab insiden

**Aktivitas Utama:**

- Menghapus malware dan backdoor
- Mem-patch kerentanan
- Melakukan cleaning sistem
- Mengidentifikasi root cause

**Contoh Implementasi:**

- Scanning dan removal malware
- Patching sistem dan aplikasi
- Rebuilding sistem dari scratch

#### **Tahap 5: Recovery (Pemulihan)**

**Tujuan**: Mengembalikan sistem ke operasi normal

**Aktivitas Utama:**

- Restore dari backup
- Testing sistem sebelum production
- Monitoring pasca-pemulihan
- Validasi keamanan

**Pertimbangan:**

- Waktu restore yang acceptable
- Integritas backup
- Testing comprehensif

#### **Tahap 6: Lessons Learned (Pembelajaran)**

**Tujuan**: Meningkatkan kemampuan respons untuk masa depan

**Aktivitas Utama:**

- Post-incident meeting
- Dokumentasi lessons learned
- Update IRP dan prosedur
- Pelatihan tambahan

**Output:**

- Laporan insiden lengkap
- Rekomendasi perbaikan
- Update playbook insiden

### 🧑‍💻 **4. Struktur Tim Incident Response**

#### **Peran dan Tanggung Jawab:**

| Peran | Tanggung Jawab | Keterampilan yang Dibutuhkan |
|-------|----------------|------------------------------|
| **Incident Response Manager** | Koordinasi tim, pengambilan keputusan, komunikasi dengan manajemen | Leadership, komunikasi, pengetahuan security |
| **Technical Analyst** | Analisis teknis, forensik, eradication | Networking, security tools, forensik digital |
| **Communications Officer** | Komunikasi internal dan eksternal | Public speaking, writing, crisis communication |
| **Legal/Compliance Officer** | Memastikan kepatuhan hukum dan regulasi | Pengetahuan hukum siber, compliance |
| **Public Relations** | Menangani komunikasi publik | Media relations, crisis management |

#### **Struktur Tim yang Direkomendasikan:**

- **Core Team**: Tim internal yang selalu siap
- **Extended Team**: Pakar dari departemen lain
- **External Support**: Konsultan atau vendor khusus

### 🧰 **5. Tools Pendukung Incident Response**

#### **Kategori Tools dan Contoh Implementasi:**

| Kategori | Contoh Tools | Fungsi Utama |
|----------|---------------|--------------|
| **Monitoring & Detection** | Splunk, Wazuh, ELK Stack | Analisis log, deteksi anomali, real-time monitoring |
| **Malware Analysis** | Cuckoo Sandbox, VirusTotal | Analisis perilaku malware, deteksi signature |
| **Network Analysis** | Wireshark, Zeek, Nmap | Analisis traffic, identifikasi serangan |
| **Digital Forensics** | Autopsy, FTK Imager, Volatility | Preservasi evidence, analisis memori, recovery data |
| **Incident Management** | TheHive, RTIR, JIRA Service Desk | Tracking insiden, kolaborasi tim, dokumentasi |

### 🔍 **6. Studi Kasus Komprehensif**

#### **Kasus 1: Serangan Ransomware pada Sistem Akademik**

**Latar Belakang:**

- Sistem akademik kampus terinfeksi ransomware
- File data mahasiswa dan dosen terenkripsi
- Tampilan layar menunjukkan pesan tebusan

**Langkah Respons:**

1. **Identification**
   - Konfirmasi insiden melalui monitoring system
   - Identifikasi jenis ransomware
   - Assess dampak: 500 GB data terenkripsi

2. **Containment**
   - Isolasi sistem terinfeksi dari jaringan
   - Nonaktifkan akses remote
   - Backup sistem yang belum terinfeksi

3. **Eradication**
   - Identifikasi vulnerability yang dieksploitasi
   - Hapus malware dari sistem
   - Patch kerentanan yang ditemukan

4. **Recovery**
   - Restore data dari backup terakhir
   - Testing sistem sebelum production
   - Implementasi security hardening

5. **Lessons Learned**
   - Perlunya backup rutin dan terisolasi
   - Pentingnya patch management
   - Pelatihan awareness untuk pengguna

#### **Kasus 2: Kebocoran Data Mahasiswa**

**Scenario:**

- Database mahasiswa terekspos secara tidak sengaja
- Informasi pribadi dapat diakses publik
- Laporan dari researcher keamanan

**Langkah Respons:**

1. **Identifikasi sumber kebocoran**
2. **Segera tutup akses yang terekspos**
3. **Assess data yang terbocorkan**
4. **Notifikasi pihak yang affected**
5. **Perbaikan konfigurasi**

---

## 🛠️ **Aktivitas Pembelajaran**

### **Tugas Kelompok: Penyusunan IRP**

**Instruksi:**
Berdasarkan pemahaman tentang IRP, buatlah dokumen Incident Response Plan untuk salah satu scenario berikut:

**Pilihan Scenario:**

1. Universitas dengan sistem informasi akademik
2. E-commerce startup
3. Rumah sakit dengan sistem elektronik medical record

**Struktur Dokumen IRP:**

```markdown
1. Pendahuluan dan Ruang Lingkup
2. Tim Incident Response (Struktur dan Kontak)
3. Klasifikasi Insiden
4. Prosedur Respons (6 Tahap NIST)
5. Tools dan Resources
6. Template Dokumentasi Insiden
7. Appendices (Kontak Darurat, Checklist)
```

[penjelasan & contoh dokumen](./subs/irp_document.md)

## 📚 **Resources Tambahan**

### **Referensi Wajib:**

1. NIST SP 800-61 Rev.2 - "Computer Security Incident Handling Guide"
2. ISO/IEC 27035 - "Information Security Incident Management"
3. SANS Institute Reading Room - Incident Response Articles

### **Tools untuk Eksplorasi:**

- **Wazuh**: Open-source security monitoring
- **TheHive**: Platform incident response
- **Cuckoo Sandbox**: Malware analysis sandbox

### **Studi Kasus Nyata:**

- Case study: Equifax Data Breach
- Case study: NotPetya Ransomware Attack
- Case study: Target Data Breach

---

## 🎯 **Refleksi Pembelajaran**

Setelah menyelesaikan modul ini, renungkan:

1. Bagaimana IRP berkontribusi pada resilience organisasi?
2. Tantangan apa yang mungkin dihadapi dalam implementasi IRP?
3. Bagaimana mengukur efektivitas sebuah IRP?
4. Perkembangan tren apa yang mempengaruhi masa depan incident response?

**"Preparation is the key to success in incident response. The time to prepare is before the incident occurs, not during (Prepare an umbrella before it rains)."**

---

Disusun berdasarkan standar NIST SP 800-61 dan best practices industry untuk Manajemen keamanan siber.