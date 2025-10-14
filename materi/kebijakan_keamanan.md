# SECURITY POLICY (Kebijakan Keamanan siber) **

---

## 📘 **1. Pendahuluan**

### **1.1 Latar Belakang**

Di era digital yang semakin kompleks, ancaman siber terus berkembang dengan cepat. Kebijakan Keamanan Informasi merupakan fondasi utama dalam membangun budaya keamanan siber yang efektif dan berkelanjutan. Dokumen ini menjadi kerangka kerja strategis untuk melindungi aset informasi dari berbagai ancaman yang dapat mengganggu operasional organisasi.

### **1.2 Konteks Strategis**

Kebijakan ini selaras dengan visi dan misi organisasi dalam menjaga reputasi, kepercayaan stakeholder, dan keberlangsungan bisnis. Implementasi kebijakan keamanan informasi merupakan investasi strategis yang mendukung pencapaian tujuan organisasi secara keseluruhan.

### **1.3 Definisi Konsep**

- **Keamanan Siber**: Praktik melindungi sistem, jaringan, dan program dari serangan digital
- **Kebijakan Keamanan**: Pernyataan formal yang mendefinisikan perilaku yang diharapkan dan kontrol keamanan
- **Aset Informasi**: Semua data, sistem, dan infrastruktur yang memiliki nilai bagi organisasi

---

## 🎯 **2. Tujuan Kebijakan**

### **2.1 Tujuan Strategis**

1. **Menetapkan standar keamanan informasi** yang konsisten dan terukur
2. **Melindungi aset data dan sistem informasi** dari penyalahgunaan dan ancaman
3. **Menjamin kepatuhan hukum** terhadap UU PDP, UU ITE, dan regulasi internasional
4. **Membangun budaya keamanan** melalui peningkatan kesadaran seluruh stakeholder

### **2.2 Target Kinerja**

- Mengurangi insiden keamanan hingga 80% dalam 1 tahun
- Mencapai kepatuhan 100% terhadap regulasi yang berlaku
- Melakukan pelatihan keamanan untuk seluruh karyawan secara berkala

### **📋 STUDI KASUS: Equifax Data Breach 2017**

**Latar Belakang**: Perusahaan kredit rating terkemuka AS mengalami breach data yang mengkompromikan 147 juta konsumen.

**Akar Masalah**:

- Tidak menerapkan patch keamanan untuk vulnerability Apache Struts yang diketahui
- Sistem deteksi intrusi yang tidak efektif
- Pembagian tanggung jawab keamanan yang tidak jelas

**Dampak**:

- Kerugian finansial $1.4 miliar
- Turun 35% nilai saham
- Gugatan class action dan denda regulator

**Pelajaran**: Pentingnya patch management yang disiplin dan monitoring keamanan yang proaktif.

---

## 🧩 **3. Ruang Lingkup**

### **3.1 Cakupan Personal**

- **Pegawai**: Tetap, kontrak, magang, dan tenaga ahli
- **Mitra**: Vendor, konsultan, pihak ketiga yang mengakses sistem organisasi
- **Stakeholder**: Dewan direksi, komisaris, dan pemegang saham

### **3.2 Cakupan Teknologi**

- **Infrastruktur**: Server, jaringan, cloud, data center
- **Aplikasi**: Software custom, paket, mobile apps, web services
- **Data**: Structured dan unstructured data, intellectual property
- **Perangkat**: Endpoints, mobile devices, IoT devices

### **3.3 Cakupan Proses**

- Business process yang melibatkan data kritikal
- Pengembangan sistem dan aplikasi
- Manajemen perubahan dan incident response

---

## 🔐 **4. Prinsip Utama Keamanan Informasi**

### **4.1 CIA Triad Extended**

| Prinsip             | Deskripsi                                       | Implementasi                                    |
| ------------------- | ----------------------------------------------- | ----------------------------------------------- |
| **Confidentiality** | Informasi hanya diakses oleh pihak berwenang    | Encryption, access control, data classification |
| **Integrity**       | Informasi akurat, lengkap, dan terpercaya       | Digital signature, hash, change control         |
| **Availability**    | Sistem dan data dapat diakses ketika dibutuhkan | Redundancy, backup, disaster recovery           |
| **Authenticity**    | Memastikan keaslian identitas dan data          | MFA, digital certificate, biometric             |
| **Non-Repudiation** | Mencegah penyangkalan transaksi                 | Digital signature, audit trail                  |

### **4.2 Prinsip Desain Keamanan**

- **Defense in Depth**: Multiple layers of security controls
- **Least Privilege**: Minimum access necessary to perform job functions
- **Separation of Duties**: Membagi tanggung jawab untuk mencegah fraud
- **Fail-Safe Defaults**: Deny access unless explicitly permitted

### **📋 STUDI KASUS: Twitter Bitcoin Scam 2020**

**Kejadian**: Akun-akun terverifikasi Twitter seperti Elon Musk, Bill Gates diretas untuk scam Bitcoin.

**Akar Masalah**:

- Social engineering terhadap karyawan Twitter
- Weak internal access controls
- Tidak ada separation of duties untuk akses administratif

**Dampak**:

- Kerugian $120,000 dari korban scam
- Kerusakan reputasi Twitter
- Investigasi oleh regulator

**Pelajaran**: Pentingnya access control yang ketat dan protection against social engineering.

---

## 🏢 **5. Kebijakan Utama**

### **5.1 Manajemen Akses**

#### **5.1.1 Access Control Policy**

- **Role-Based Access Control (RBAC)**: Akses berdasarkan job function
- **Principle of Least Privilege**: Hak akses minimum yang diperlukan
- **Regular Access Review**: Audit akses setiap 6 bulan
- **Access Revocation**: Immediate revocation upon termination

#### **5.1.2 Authentication Requirements**

- **Password Policy**: Minimum 12 karakter, complexity requirements
- **Multi-Factor Authentication**: Wajib untuk akses privileged dan remote
- **Session Management**: Timeout automatic setelah 15 menit inactivity
- **Biometric Authentication**: Untuk data sangat sensitif

### **5.2 Penggunaan Sistem dan Jaringan**

#### **5.2.1 Acceptable Use Policy**

- **Business Use Only**: Tidak untuk aktivitas pribadi yang signifikan
- **Content Filtering**: Blokir akses ke malicious/malware sites
- **Bandwidth Management**: Prioritaskan traffic bisnis kritikal
- **Monitoring**: Log semua aktivitas jaringan untuk security monitoring

#### **5.2.2 Network Security**

- **Network Segmentation**: Pisahkan network berdasarkan sensitivity
- **VPN Requirement**: Wajib untuk remote access
- **Wireless Security**: WPA3 Enterprise, separate SSID untuk guest
- **Firewall Configuration**: Default deny, explicitly allow necessary services

### **5.3 Keamanan Data**

#### **5.3.1 Data Classification**

| Kategori           | Contoh                                | Protection Requirements                    |
| ------------------ | ------------------------------------- | ------------------------------------------ |
| **Sangat Rahasia** | Intellectual property, financial data | Encryption, strict access control, logging |
| **Rahasia**        | Customer data, employee records       | Encryption, access control                 |
| **Internal**       | Internal documents, policies          | Access control, basic protection           |
| **Public**         | Marketing materials, press releases   | No special protection                      |

#### **5.3.2 Data Protection Measures**

- **Encryption**: AES-256 untuk data at rest dan in transit
- **Data Loss Prevention (DLP)**: Monitor dan block unauthorized data transfer
- **Backup Strategy**: 3-2-1 rule (3 copies, 2 media, 1 offsite)
- **Data Retention**: Sesuai regulatory requirements dan business needs

### **📋 STUDI KASUS: Marriott International Data Breach 2018**

**Kejadian**: 500 juta record guest data dicuri melalui compromised third-party system.

**Akar Masalah**:

- Weak security assessment untuk akuisisi Starwood
- Inadequate data encryption
- Poor third-party risk management

**Dampak**:

- Denda £18.4 juta dari ICO UK
- Class action lawsuits
- Kerusakan reputasi brand

**Pelajaran**: Critical importance of third-party risk management dan data encryption.

### **5.4 Manajemen Perangkat**

#### **5.4.1 Endpoint Security**

- **Device Encryption**: Wajib untuk semua mobile devices
- **Endpoint Protection**: Antivirus, anti-malware, EDR solutions
- **Patch Management**: Critical patches within 72 hours, others within 30 days
- **Mobile Device Management (MDM)**: Wajib untuk BYOD yang akses corporate data

#### **5.4.2 BYOD Policy**

- **Security Requirements**: Device encryption, passcode, approved OS versions
- **Acceptable Use**: Clear separation personal vs business data
- **Remote Wipe Capability**: Untuk device lost/stolen atau employment termination
- **Compliance Monitoring**: Regular checks for compliance

### **5.5 Keamanan Aplikasi**

#### **5.5.1 Secure Development Lifecycle**

- **Security Requirements**: Include security dalam initial requirements
- **Secure Coding**: OWASP Top 10 awareness, code review
- **Security Testing**: SAST, DAST, penetration testing
- **Secure Deployment**: Environment separation, security approval sebelum production

#### **5.5.2 Application Security Controls**

- **Input Validation**: Sanitize semua user inputs
- **Authentication & Authorization**: Consistent implementation across applications
- **Error Handling**: Generic error messages, detailed logging
- **Security Headers**: Implement HTTP security headers

### **5.6 Kesadaran dan Pelatihan Keamanan**

#### **5.6.1 Security Awareness Program**

- **New Hire Training**: Security orientation within first week
- **Annual Refresher**: Updated training based on current threats
- **Phishing Simulation**: Monthly simulated phishing campaigns
- **Specialized Training**: Untuk roles dengan specific security responsibilities

#### **5.6.2 Metrics and Evaluation**

- **Participation Rate**: 100% completion required
- **Phishing Click Rate**: Target <5%
- **Knowledge Assessment**: Pre/post training evaluation
- **Behavioral Metrics**: Reduction in security incidents

### **📋 STUDI KASUS: Target Corporation Breach 2013**

**Kejadian**: 40 juta credit card numbers dicuri melalui HVAC vendor credentials.

**Akar Masalah**:

- Third-party vendor management yang lemah
- Lack of network segmentation
- Delayed response to security alerts

**Dampak**:

- Kerugian $202 juta
- CEO mengundurkan diri
- Massive reputational damage

**Pelajaran**: Network segmentation yang efektif dan vendor risk management yang ketat.

### **5.7 Penanganan Insiden Keamanan**

#### **5.7.1 Incident Response Plan**

- **Preparation**: Team formation, tool preparation, playbooks
- **Detection & Analysis**: Monitoring, alerting, threat intelligence
- **Containment**: Short-term dan long-term containment strategies
- **Eradication & Recovery**: Remove threats, restore systems
- **Post-Incident Activity**: Lessons learned, improvement planning

#### **5.7.2 Incident Classification**

| Severity     | Impact                                | Response Time   |
| ------------ | ------------------------------------- | --------------- |
| **Critical** | Business operations severely impacted | Immediate, 24/7 |
| **High**     | Significant business impact           | Within 4 hours  |
| **Medium**   | Limited business impact               | Within 24 hours |
| **Low**      | Minimal business impact               | Within 72 hours |

---

## ⚙️ **6. Kepatuhan dan Audit**

### **6.1 Compliance Framework**

- **Regulatory Compliance**: UU PDP, UU ITE, sector-specific regulations
- **International Standards**: ISO 27001, NIST CSF, COBIT
- **Industry Standards**: PCI DSS untuk payment processing, HIPAA untuk healthcare

### **6.2 Audit Program**

- **Internal Audit**: Quarterly assessments oleh internal audit team
- **External Audit**: Annual third-party security assessment
- **Penetration Testing**: Bi-annual comprehensive penetration tests
- **Vulnerability Scanning**: Monthly automated scans

### **6.3 Enforcement**

- **Progressive Discipline**: Verbal warning, written warning, termination
- **Performance Impact**: Security compliance sebagai bagian performance evaluation
- **Legal Action**: Untuk violations yang menyebabkan significant harm

---

## 🧭 **7. Tinjauan dan Pemutakhiran**

### **7.1 Review Cycle**

- **Annual Review**: Comprehensive policy review setiap tahun
- **Event-Driven Review**: Setiap major security incident atau regulatory change
- **Stakeholder Feedback**: Regular input dari semua business units

### **7.2 Change Management**

- **Change Control Board**: Approval untuk semua policy changes
- **Stakeholder Communication**: Clear communication tentang policy updates
- **Training Updates**: Corresponding training materials revision

---

## 🧾 **8. Penutup**

### **8.1 Management Commitment**

Management sepenuhnya mendukung implementasi kebijakan ini dan mengalokasikan resources yang diperlukan untuk keberhasilannya.

### **8.2 Employee Responsibility**

Setiap employee bertanggung jawab untuk:

- Memahami dan mematuhi kebijakan ini
- Melaporkan suspected violations atau security concerns
- Berpartisipasi aktif dalam security awareness programs

### **8.3 Continuous Improvement**

Kebijakan ini merupakan living document yang akan terus disempurnakan berdasarkan lessons learned, technological developments, dan evolving threat landscape.

---

# **9. Best Practices Implementasi Kebijakan Keamanan Informasi**

Agar _Security Policy_ dapat berjalan efektif, organisasi perlu memastikan bahwa kebijakan tidak hanya disusun, tetapi juga **diimplementasikan secara konsisten, diukur efektivitasnya, dan diperbaharui secara berkelanjutan**.
Bagian ini menjelaskan praktik terbaik (_best practices_) yang dapat digunakan dalam penyusunan dan penerapan kebijakan keamanan informasi di lingkungan organisasi.

---

## 🔹 **9.1. Perancangan dan Pengembangan Kebijakan (Policy Design and Development)**

### 1. **Lakukan Penilaian Risiko (Risk Assessment)**

Identifikasi dan evaluasi aset informasi, ancaman, serta kerentanannya untuk memahami risiko yang dihadapi sebelum menyusun aturan.
Gunakan pendekatan _risk-based_ agar kebijakan relevan dan proporsional terhadap ancaman nyata.

### 2. **Tetapkan Tujuan dan Ruang Lingkup yang Jelas**

Tentukan apa yang ingin dicapai, siapa yang terlibat, dan sistem apa saja yang termasuk dalam cakupan kebijakan.
Ruang lingkup yang jelas membantu menghindari tumpang tindih tanggung jawab.

### 3. **Libatkan Pemangku Kepentingan (Stakeholder Involvement)**

Ajak partisipasi dari karyawan, manajemen, tim IT, dan pihak ketiga dalam proses perumusan kebijakan.
Keterlibatan ini meningkatkan rasa memiliki dan kepatuhan terhadap kebijakan.

### 4. **Gunakan Bahasa yang Jelas dan Mudah Dipahami**

Tulislah kebijakan dengan bahasa non-teknis dan komunikatif.
Pastikan tersedia secara digital melalui intranet atau portal khusus agar mudah diakses semua pihak.

### 5. **Tentukan Peran dan Tanggung Jawab**

Definisikan siapa yang bertanggung jawab atas keamanan data, akses sistem, audit, serta pelaporan insiden.
Gunakan matriks RACI (_Responsible, Accountable, Consulted, Informed_) untuk memperjelas peran.

### 6. **Terapkan Prinsip Least Privilege**

Berikan akses minimum sesuai kebutuhan pekerjaan.
Hal ini membatasi potensi penyalahgunaan dan memperkecil dampak jika terjadi pelanggaran.

---

## 🔹 **9.2. Implementasi Teknis dan Operasional (Technical and Operational Implementation)**

### 1. **Gunakan Kontrol Teknis (Technical Controls)**

Terapkan mekanisme keamanan seperti:

- Firewall dan IDS/IPS
- Multi-Factor Authentication (MFA)
- Enkripsi data (saat disimpan dan dikirim)
- Endpoint protection dan antivirus

Kontrol teknis berfungsi menegakkan kebijakan secara otomatis dan mengurangi ketergantungan pada faktor manusia.

### 2. **Bangun Rencana Tanggap Insiden (Incident Response Plan)**

Siapkan prosedur yang jelas untuk mendeteksi, melaporkan, dan menanggulangi insiden keamanan, termasuk kebocoran data.
Lakukan uji coba (_simulation exercise_) secara berkala.

### 3. **Kendalikan Hak Akses (Access Control Management)**

Gunakan kebijakan akses berbasis peran (RBAC) dan audit secara berkala hak akses administratif.
Penerapan prinsip “need-to-know” menjadi dasar utama.

### 4. **Lakukan Pemantauan Berkelanjutan (Continuous Monitoring)**

Gunakan sistem pemantauan (_SIEM – Security Information and Event Management_) untuk mendeteksi aktivitas anomali, pelanggaran kebijakan, dan serangan siber secara real-time.

### 5. **Kelola Risiko Pihak Ketiga (Third-Party Risk Management)**

Pastikan seluruh mitra, vendor, atau penyedia layanan mengikuti standar keamanan yang sama.
Gunakan _Service Level Agreement (SLA)_ yang mencakup komitmen keamanan data.

---

## 🔹 **9.3. Pemeliharaan dan Penguatan Budaya Keamanan (Ongoing Maintenance and Training)**

### 1. **Pelatihan dan Kesadaran Keamanan (Security Awareness Training)**

Seluruh pegawai harus mendapatkan pelatihan berkala tentang:

- Praktik aman dalam penggunaan email, password, dan perangkat kerja
- Cara mengenali serangan phishing atau rekayasa sosial
- Prosedur pelaporan insiden keamanan

### 2. **Tinjauan dan Pemutakhiran Kebijakan**

Kebijakan harus diperbaharui secara berkala agar tetap relevan dengan ancaman dan perubahan teknologi.
Audit internal dilakukan untuk memastikan efektivitas implementasi.

### 3. **Bangun Budaya Keamanan (Security Culture)**

Ciptakan lingkungan kerja di mana keamanan adalah tanggung jawab bersama.
Dorong komunikasi terbuka dan penghargaan bagi karyawan yang berkontribusi terhadap peningkatan keamanan informasi.

---

## 📗 **9.4. Ringkasan Best Practices**

| Tahap                   | Fokus Utama                                           | Praktik Kunci                                            |
| ----------------------- | ----------------------------------------------------- | -------------------------------------------------------- |
| **Desain Kebijakan**    | Menyusun kebijakan yang jelas dan berbasis risiko     | Penilaian risiko, pelibatan stakeholder, kejelasan peran |
| **Implementasi Teknis** | Mengoperasionalkan kebijakan melalui kontrol keamanan | Enkripsi, MFA, firewall, monitoring                      |
| **Pemeliharaan**        | Menjaga relevansi dan kesadaran keamanan              | Pelatihan rutin, pembaruan kebijakan, budaya keamanan    |

---

---

## 📚 **10. Daftar Referensi**

### **10.1 Standar Internasional**

1. **ISO/IEC 27001:2022** - Information Security Management Systems
2. **ISO/IEC 27002:2022** - Information Security Controls
3. **NIST Cybersecurity Framework 2.0** - Improving Critical Infrastructure Cybersecurity
4. **NIST SP 800-53 Rev. 5** - Security and Privacy Controls
5. **COBIT 20110** - Framework for Governance and Management of Enterprise IT

### **10.2 Buku Teks Akademik**

6. Whitman, M. E., & Mattord, H. J. (2022). _Principles of Information Security_ (7th ed.)
7. Stallings, W., & Brown, L. (2018). _Computer Security: Principles and Practice_ (4th ed.)
8. Anderson, R. (2020). _Security Engineering: A Guide to Building Dependable Distributed Systems_ (3rd ed.)
10. Schneier, B. (2015). _Data and Goliath: The Hidden Battles to Collect Your Data and Control Your World_

### **10.3 Jurnal dan Penelitian**

10. Von Solms, B., & Van Niekerk, J. (2013). "From Information Security to Cyber Security"
11. Siponen, M. T. (2005). "Analysis of modern IS security development approaches"
12. Werlinger, R., et al. (20010). "Security challenges in small and medium enterprises"

### **10.4 Sumber Online**

13. **SANS Institute** - Security Policy Templates and Resources
14. **ENISA** - European Union Agency for Cybersecurity Guidelines
15. **CIS Controls** - Center for Internet Security Critical Security Controls
16. **Kementerian Kominfo RI** - Pedoman Keamanan Informasi Nasional

### **10.5 Regulasi**

17. **Undang-Undang No. 27 Tahun 2022** - Perlindungan Data Pribadi
18. **Undang-Undang No. 19 Tahun 2016** - Perubahan atas UU ITE
19. **Peraturan Pemerintah** - Implementasi Teknis Keamanan Informasi

---

### **10.6 Referensi Best Practices**

1. NIST Special Publication 800-53 Rev.5 — _Security and Privacy Controls for Information Systems and Organizations._
2. ISO/IEC 27002:2022 — _Code of Practice for Information Security Controls._
3. ENISA (2021). _Good Practices for Security Policy Design._ European Union Agency for Cybersecurity.
4. SANS Institute (2023). _Information Security Policy Implementation Guide._
5. Whitman, M. E., & Mattord, H. J. (2022). _Principles of Information Security._ Cengage Learning.
6. Von Solms, B. & Van Niekerk, J. (2013). “From Information Security to Cyber Security.” _Computers & Security, 38_, 97–102.

---
