# 📘 **Struktur / Format Dokumen Incident Response Plan (IRP)**

## 🧾 **1. Pendahuluan**

Isi:

* Tujuan dokumen
* Ruang lingkup (sistem, unit, atau organisasi mana yang dicakup)
* Dasar hukum atau kebijakan keamanan informasi
* Referensi standar (misal: NIST SP 800-61, ISO 27035)

🧩 **Contoh:**

> Dokumen ini menjelaskan langkah-langkah respons insiden keamanan informasi di lingkungan Universitas XYZ yang melibatkan sistem akademik, email, dan server web.

---

## 👥 **2. Struktur Tim Incident Response**

Isi:

* Susunan tim IR (Incident Response Team / CSIRT)
* Peran dan tanggung jawab tiap anggota
* Kontak darurat

🧩 **Contoh tabel:**

| Peran                     | Nama/Jabatan     | Tanggung Jawab        | Kontak                                    |
| ------------------------- | ---------------- | --------------------- | ----------------------------------------- |
| Incident Response Manager | Kepala IT        | Koordinasi IR         | 0812xxxxxxx                               |
| Analyst                   | Staf Keamanan TI | Analisis dan forensik | 0813xxxxxxx                               |
| PR Officer                | Humas            | Komunikasi publik     | [humas@xyz.ac.id](mailto:humas@xyz.ac.id) |

---

## 🚨 **3. Definisi dan Klasifikasi Insiden**

Isi:

* Definisi “insiden” dalam konteks organisasi
* Jenis-jenis insiden (malware, phishing, kebocoran data, DoS, dll)
* Tingkat keparahan (*severity level*) dan prioritas respons

🧩 **Contoh klasifikasi:**

| Level  | Dampak                 | Contoh                  | Waktu Respons |
| ------ | ---------------------- | ----------------------- | ------------- |
| High   | Gangguan layanan utama | Server akademik diretas | < 1 jam       |
| Medium | Gangguan terbatas      | Phishing email dosen    | < 4 jam       |
| Low    | Potensi ancaman        | Scan port dari luar     | < 24 jam      |

---

## ⚙️ **4. Prosedur Incident Response (Lifecycle / Tahapan)**

Isi:

* Langkah-langkah sesuai tahapan NIST:

  1. Preparation
  2. Identification
  3. Containment
  4. Eradication
  5. Recovery
  6. Lessons Learned

🧩 **Contoh ringkas:**

> **Containment:** Segera isolasi perangkat terinfeksi dari jaringan dan buat salinan log untuk analisis.

---

## 🧰 **5. Tools dan Sumber Daya**

Isi:

* Software / hardware yang digunakan untuk mendeteksi dan menangani insiden
* Template log, form pelaporan, dan daftar kontak eksternal (CERT, vendor, ISP)

🧩 **Contoh:**

> Tools utama: Wazuh (IDS/IPS), Wireshark (packet capture), TheHive (case management).

---

## 🗂️ **6. Prosedur Pelaporan dan Eskalasi**

Isi:

* Alur pelaporan dari staf ke tim IR
* Format form laporan insiden
* Mekanisme eskalasi ke level manajemen atau regulator

🧩 **Contoh flow:**

> User → Helpdesk → Tim IR → Kepala IT → Rektor/Humas (jika berdampak publik).

---

## 📄 **7. Dokumentasi dan Pelaporan Insiden**

Isi:

* Template *Incident Report Form* (tanggal, deskripsi, dampak, langkah yang dilakukan)
* Cara penyimpanan dan arsip bukti (*evidence handling*)

🧩 **Contoh isian laporan:**

```vi
Tanggal kejadian: 25 Oktober 2025
Jenis insiden: SQL Injection pada sistem akademik
Langkah containment: Blok IP penyerang, backup database
Status: Dipulihkan
Catatan tambahan: Patch keamanan diterapkan
```

---

## 🧠 **8. Lessons Learned & Review**

Isi:

* Evaluasi efektivitas respon
* Rencana perbaikan (update SOP, training ulang, perbaikan patch)
* Jadwal simulasi insiden (drill)

---

## 🔒 **9. Lampiran**

Isi:

* Daftar kontak eksternal (CERT, vendor, penyedia cloud)
* Template form dan checklist
* Diagram alur incident response

---

## 📂 Contoh Format Singkat (1 Halaman)

Kalau kamu butuh versi ringkas untuk tugas mahasiswa atau latihan di kelas, bisa pakai format ini:

| Komponen               | Isian                                 |
| ---------------------- | ------------------------------------- |
| **Nama Sistem / Aset** | Sistem Informasi Akademik (SIAKAD)    |
| **Jenis Insiden**      | Phishing / Kebocoran data             |
| **Tanggal / Waktu**    | 28 Oktober 2025, 10.30 WIB            |
| **Identifikasi**       | Ditemukan aktivitas login tidak wajar |
| **Containment**        | Nonaktifkan akun terindikasi          |
| **Eradication**        | Reset password, hapus email phishing  |
| **Recovery**           | Aktifkan kembali akun & edukasi user  |
| **Lessons Learned**    | Perkuat MFA dan filter spam           |
| **PIC / Tim IR**       | Unit IT Kampus                        |
