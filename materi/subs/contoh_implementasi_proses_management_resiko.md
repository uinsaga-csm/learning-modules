# Contoh Implementasi Proses Manajemen Risiko Keamanan Siber

## **4.1 Identifikasi Aset dan Risiko**

**Studi Kasus:** Universitas X memiliki sistem e-learning berbasis web untuk mahasiswa dan dosen.

* **Inventarisasi Aset:**

  * Perangkat keras: Server aplikasi, server database, laptop staf IT.
  * Perangkat lunak: Aplikasi e-learning (LMS), database MySQL, sistem autentikasi.
  * Data: Data mahasiswa (nama, NIM, nilai, presensi), materi kuliah, akun dosen.
  * Orang: Admin IT, dosen, mahasiswa.
  * Fasilitas: Ruang server dengan pendingin khusus.

* **Klasifikasi Data:**

  * Publik: Materi kuliah yang diunggah untuk umum.
  * Internal: Catatan presensi.
  * Rahasia: Nilai mahasiswa.
  * Sangat Rahasia: Data pribadi mahasiswa (NIK, alamat, email, nomor telepon).

* **Identifikasi Ancaman & Kerentanan:**

  * Ancaman: Serangan DDoS, pencurian akun mahasiswa, kebocoran database.
  * Kerentanan: Password lemah, server belum di-*patch*, tidak ada enkripsi data sensitif.

---

## **4.2 Penilaian Risiko (Risk Assessment) & Analisis**

* **Contoh Risiko:**

  * **Serangan brute force login akun mahasiswa**

    * Likelihood: Tinggi (karena banyak user tidak mengganti password default).
    * Impact: Sedang (akses materi, namun terbatas).
    * Tingkat Risiko: **Sedang**.

  * **Kebocoran database mahasiswa**

    * Likelihood: Sedang.
    * Impact: Katastropik (data pribadi bocor → reputasi hancur, tuntutan hukum).
    * Tingkat Risiko: **Sangat Tinggi**.

* **Visualisasi Matriks Risiko (contoh sederhana):**

| Likelihood ↓ / Impact → | Tidak Signifikan | Sedang | Tinggi        | Katastropik   |
| ----------------------- | ---------------- | ------ | ------------- | ------------- |
| Rendah                  | Rendah           | Rendah | Sedang        | Tinggi        |
| Sedang                  | Rendah           | Sedang | Tinggi        | Sangat Tinggi |
| Tinggi                  | Sedang           | Tinggi | Sangat Tinggi | Sangat Tinggi |

👉 Database mahasiswa = **Sangat Tinggi → prioritas utama mitigasi.**

---

## **4.3 Mitigasi Risiko (Perlakuan Risiko)**

* **Hindari:** Menonaktifkan modul lama pada LMS yang tidak digunakan dan rentan.
* **Kurangi / Mitigasi:**

  * Kontrol Teknis: Pasang firewall, IDS/IPS, MFA untuk dosen dan admin, enkripsi database.
  * Kontrol Administratif: Aturan password kuat, kebijakan backup data mingguan.
  * Kontrol Fisik: Kunci biometrik untuk ruang server, CCTV.
* **Transfer:** Kontrak dengan penyedia *cloud hosting* dengan SLA + beli asuransi siber.
* **Terima:** Risiko kecil seperti mahasiswa lupa password dianggap wajar (diterima dengan dokumentasi).

---

## **4.4 Implementasi Kontrol Keamanan**

* **Tindakan nyata yang dilakukan:**

  * Konfigurasi firewall untuk memblokir serangan brute force.
  * Implementasi enkripsi data sensitif di database (AES-256).
  * Buat kebijakan password minimal 8 karakter dengan kombinasi angka & simbol.
  * Pelatihan keamanan siber untuk staf IT & dosen.
  * Akses admin menggunakan VPN + MFA.

👉 Prinsip **Least Privilege:** Mahasiswa hanya bisa akses akun sendiri, dosen hanya nilai kelasnya, admin hanya teknis, bukan isi nilai.

---

## **4.5 Pemantauan dan Review Berkelanjutan**

* **Pemantauan:** Gunakan SIEM untuk monitoring log login mencurigakan.
* **Audit:** Setiap 6 bulan dilakukan penetration testing eksternal.
* **Simulasi:** Tabletop exercise: “Bagaimana jika database bocor?” → tim latihan prosedur respons.
* **Review:** Setelah ada perubahan (misal: migrasi ke cloud), penilaian risiko diperbarui.

---
