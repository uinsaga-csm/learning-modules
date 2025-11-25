# **MODUL PEMBELAJARAN**

## **Business Continuity & Disaster Recovery (BC/DR)**

### **Untuk Mahasiswa S1/S2**

---

## **1. KONSEP DASAR (Mudah Dipahami)**

### **Apa itu BC/DR?**

**Analoginya:**

- **Business Continuity (BC)** = "RSG (Rencana Semua Gawat)" untuk perusahaan
- **Disaster Recovery (DR)** = "UGD (Unit Gawat Darurat)" untuk sistem IT

**Perbedaan Simple:**

- **BC**: Pastikan bisnis tetap jalan meski ada masalah
- **DR**: Perbaiki sistem IT yang rusak/hilang

### **Kenapa Penting?**

**Contoh Nyata:**

- **Bank**: Server down → nasabah tidak bisa transaksi
- **Rumah Sakit**: Data pasien hilang → obat salah diberikan
- **E-commerce**: Website down → rugi miliaran per jam

---

## **2. KOMPONEN UTAMA BC/DR**

### **2.1 Business Continuity (BC)**

**Yang harus disiapkan:**

``` bash
1. ORANG → Tim darurat, pelatihan
2. PROSES → Cara kerja manual jika komputer mati
3. TEMPAT → Kantor cadangan
4. TEKNOLOGI → Sistem backup
```

### **2.2 Disaster Recovery (DR)**

**Fokus pada:**

- **Backup data** (seperti fotocopy dokumen penting)
- **Server cadangan** (seperti rumah kontrakan sementara)
- **Jaringan internet** cadangan

---

## **3. TAHAPAN PRAKTIS MEMBUAT BC/DR**

### **Langkah 1: Identifikasi yang PENTING**

**Pertanyaan sederhana:**

- "Apa yang bikin perusahaan langsung mati jika hilang?"
- "Proses apa yang tidak boleh berhenti lebih dari 1 jam?"

### **Langkah 2: Hitung Waktu Pemulihan**

**Konsep Mudah:**

- **RTO** = "Berapa lama boleh offline?"
  _Contoh: Website e-commerce → RTO 1 jam_
- **RPO** = "Berapa data yang boleh hilang?"
  _Contoh: Data transaksi → RPO 15 menit_

### **Langkah 3: Pilih Strategi**

**Pilihan Lokasi DR:**
| Tipe | Biaya | Persiapan | Cocok untuk |
|------|-------|-----------|-------------|
| **Hot Site** | Mahal | Instant | Bank, RS |
| **Warm Site** | Sedang | 1-2 jam | Perusahaan menengah |
| **Cold Site** | Murah | 1-2 hari | Startup |

---

## **4. CONTOH KASUS NYATA**

### **Kasus 1: Serangan Ransomware**

**Apa yang terjadi:**

- Semua file dikunci hacker
- Minta tebusan untuk buka

**Solusi BC/DR:**

1. **BC**: Pakai proses manual sementara
2. **DR**: Restore dari backup yang bersih
3. **Komunikasi**: Beri tahu customer ada masalah

### **Kasus 2: Kebakaran Data Center**

**Apa yang terjadi:**

- Server hancur
- Data mungkin hilang

**Solusi BC/DR:**

1. **BC**: Pindah ke kantor cabang
2. **DR**: Hidupkan server di cloud
3. **Data**: Ambil dari backup luar kota

---

## \*\*5. BAGAIMANA MEMULAI?

### **Untuk Perusahaan Kecil:**

1. **List 5 aplikasi paling penting**
2. **Backup data setiap hari**
3. **Tentukan siapa yang bertanggung jawab**
4. **Simpan kontak darurat**

### **Untuk Perusahaan Besar:**

1. **Buat tim BC/DR**
2. **Lakukan risk assessment**
3. **Buat plan dokumentasi**
4. **Test secara berkala**

---

## **6. TEMPLATE SEDERHANA BC/DR PLAN**

### **Bagian 1: Tim Darurat**

```
- Koordinator: [Nama, No HP]
- IT Support: [Nama, No HP]
- Komunikasi: [Nama, No HP]
```

### **Bagian 2: Proses Penting**

```
1. Proses: [Transfer bank]
   - RTO: 2 jam
   - RPO: 30 menit
   - Backup: Cloud server B

2. Proses: [Email perusahaan]
   - RTO: 4 jam
   - RPO: 1 jam
   - Backup: Office 365
```

### **Bagian 3: Langkah Darurat**

```
1. Jika server mati → Hubungi [Nama IT]
2. Jika internet putus → Pakai [Provider cadangan]
3. Jika kantor tutup → Pindah ke [Alamat cadangan]
```

---

## **7. TESTING (Cara Mengecek)**

### **Testing Simple:**

- **Walkthrough**: Baca plan bersama, cari celah
- **Tabletop**: Simulasi "bagaimana jika..." dalam meeting
- **Simulasi**: Matikan 1 server, lihat respon tim

### **Hasil yang Dicari:**

- Semua orang tahu tugasnya
- Backup bekerja dengan baik
- Komunikasi lancar

---

## **8. KESALAHAN UMUM**

### **Yang Sering Terjadi:**

1. "Plan sudah dibuat, tapi tidak pernah di-test"
2. "Backup ada, tapi tidak pernah dicoba restore"
3. "Semua tahu ada plan, tapi tidak tahu lokasi penyimpanannya"
4. "Plan sudah ketinggalan zaman, teknologi sudah berubah"

### **Solusi:**

- **Review 6 bulan sekali**
- **Test backup setiap bulan**
- **Update kontak dan prosedur**

---

## **9. ALAT BANTU (Tools)**

### **Gratis:**

- **Backup**: Google Drive, AWS S3
- **Komunikasi**: WhatsApp Group, Slack
- **Dokumentasi**: Google Docs, Notion

### **Berbayar:**

- **Backup otomatis**: Veeam, Acronis
- **Monitoring**: Datadog, PRTG
- **DR otomatis**: AWS Disaster Recovery

---

## **10. ACTION PLAN**

### **Minggu 1:**

- Identifikasi 3 proses paling kritis
- Tentukan RTO/RPO untuk masing-masing

### **Minggu 2:**

- Buat backup untuk 3 proses tersebut
- Tentukan tim darurat

### **Minggu 3:**

- Dokumentasi dalam 1 halaman
- Sosialisasikan ke team

### **Minggu 4:**

- Test backup dan komunikasi
- Review dan perbaiki

---

## **KESIMPULAN**

**BC/DR itu seperti asuransi:**

- **Mahal jika tidak punya saat butuh**
- **Murah jika dipersiapkan dari awal**
- **Yang pintar sedia payung sebelum hujan**

**Start Small, Think Big:**

- Mulai dari yang paling kritikal
- Dokumentasi sederhana tapi jelas
- Practice makes perfect
