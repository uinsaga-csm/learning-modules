# IDENTITY & ACCESS MANAGEMENT (IAM), AUTHENTICATION, AND ACCESS CONTROL

---

## 📘 1. Pendahuluan

### 1.1 Latar Belakang

Dalam era digital yang semakin terhubung, identitas digital telah menjadi perimeter keamanan baru. Identity and Access Management (IAM) merupakan fondasi kritis yang memastikan hanya pihak yang berwenang yang dapat mengakses sumber daya organisasi pada waktu, alasan, dan kondisi yang tepat.

### 1.2 Konteks Strategis

IAM bukan hanya tentang teknologi, tetapi tentang mengelola risiko bisnis, memenuhi kepatuhan regulasi, dan memungkinkan transformasi digital yang aman. Implementasi IAM yang efektif dapat mengurangi risiko insiden keamanan hingga 70% berdasarkan studi industri.

### 1.3 Realitas Ancaman

- 80% pelanggaran data melibatkan penggunaan kredensial yang lemah atau dicuri
- Rata-rata organisasi memiliki 3-4 kali lebih banyak akun privileged daripada karyawan
- 65% organisasi mengalami insiden keamanan karena akses berlebih

---

## 🎯 2. Tujuan

### 2.1 Tujuan Strategis

1. **Menjamin Akuntabilitas**: Setiap akses dapat ditelusuri ke individu tertentu
2. **Mengurangi Risiko**: Mencegah akses tidak sah dan penyalahgunaan hak akses
3. **Meningkatkan Efisiensi**: Otomatisasi proses manajemen siklus hidup identitas
4. **Memastikan Kepatuhan**: Memenuhi regulasi seperti UU PDP, GDPR, PCI DSS

### 2.2 Target Kinerja

- Menerapkan MFA untuk 100% akses privileged dalam 6 bulan
- Mengurangi orphan accounts hingga 95% dalam 1 tahun
- Melakukan access review quarterly untuk aplikasi kritis
- Mencapai mean time to deprovision 24 jam setelah terminasi

---

## 🧭 3. Ruang Lingkup

### 3.1 Cakupan Pengguna

- **Karyawan**: Tetap, kontrak, magang
- **Mitra Bisnis**: Vendor, konsultan, pihak ketiga
- **Non-human Identities**: Service accounts, API keys, robot accounts
- **Customer**: Untuk organisasi yang menyediakan layanan eksternal

### 3.2 Cakupan Sistem

- **Aplikasi**: On-premise, cloud, hybrid
- **Infrastruktur**: Server, jaringan, database
- **Data**: Structured dan unstructured data
- **Endpoint**: Desktop, mobile, IoT devices

### 📋 STUDI KASUS: SolarWinds Supply Chain Attack 2020

**Kejadian**: Pelaku ancaman menyusupkan backdoor dalam update software SolarWinds, mengkompromikan banyak organisasi pemerintah dan perusahaan.

**Akar Masalah IAM**:

- Weak vendor access controls
- Inadequate monitoring of privileged access
- Lack of zero-trust principles in supply chain

**Dampak**:

- Kompromi data di multiple government agencies
- Kerugian reputasi dan finansial signifikan
- Peningkatan regulasi untuk software supply chain

**Pelajaran**: Pentingnya third-party access management dan privileged access controls.

---

## 🧠 4. Konsep Dasar

### 4.1 Identity & Access Management Framework

| Konsep             | Deskripsi                                | Contoh Implementasi          |
| ------------------ | ---------------------------------------- | ---------------------------- |
| **Identification** | Proses mengklaim identitas               | Username, email, employee ID |
| **Authentication** | Memverifikasi klaim identitas            | Password, MFA, biometric     |
| **Authorization**  | Menentukan hak akses setelah autentikasi | RBAC, ABAC, permissions      |
| **Accounting**     | Mencatat dan melaporkan aktivitas        | Audit logs, monitoring       |

### 4.2 Prinsip Desain IAM

- **Uniqueness**: Satu identitas unik per individu
- **Lifecycle Management**: Manage dari provisioning hingga deprovisioning
- **Least Privilege**: Minimum access required
- **Separation of Duties**: Prevent conflict of interest
- **Continuous Verification**: Always verify, never trust

---

## 🔐 5. Identity and Access Management (IAM)

### 5.1 Identity Lifecycle Management

#### 5.1.1 Provisioning Process

```
HR System Trigger → Create Identity → Assign to Groups → Provision Access → Notify User → Training & Onboarding
```

**Best Practices**:

- **Automated Provisioning**: Integrasi dengan HR system untuk auto-provisioning
- **Standardized Roles**: Template role-based access packages
- **Approval Workflows**: Manager approval untuk sensitive access requests

#### 5.1.2 Maintenance Activities

- **Role Changes**: Update access berdasarkan job changes
- **Temporary Access**: Time-bound access untuk project-specific needs
- **Access Reviews**: Quarterly certification untuk critical access

#### 5.1.3 Deprovisioning Process

- **Immediate Action**: Disable accounts within 24 hours of termination
- **Comprehensive Cleanup**: Remove dari semua systems dan groups
- **Data Preservation**: Archive data sesuai retention policies

### 5.2 Access Control Models

#### 5.2.1 Role-Based Access Control (RBAC)

**Implementasi**:

```yaml
Role: Finance Analyst
Permissions:
  - read_financial_reports
  - update_expense_reports
  - view_customer_financial_data
Restrictions:
  - no_approval_authority
  - no_system_configuration
```

#### 5.2.2 Attribute-Based Access Control (ABAC)

**Policy Example**:

```
IF user.department == "HR"
AND user.location == "Indonesia"
AND time.between("08:00", "17:00")
AND device.compliant == true
THEN ALLOW access_to_hr_system
```

#### 5.2.3 Privileged Access Management (PAM)

**Critical Controls**:

- **Just-in-Time Access**: Privileged access hanya ketika dibutuhkan
- **Session Monitoring**: Record dan monitor semua privileged sessions
- **Password Vaulting**: Secure storage untuk privileged credentials
- **Approval Workflows**: Multi-level approval untuk sensitive operations

### 📋 STUDI KASUS: Twitter Bitcoin Scam 2020

**Kejadian**: Hacker mengkompromikan akun Twitter terverifikasi untuk scam Bitcoin melalui social engineering terhadap karyawan.

**Akar Masalah IAM**:

- Weak internal access controls
- Insufficient privileged access management
- Lack of multi-factor authentication untuk administrative tools

**Dampak**:

- Kompromi akun high-profile termasuk Obama, Musk, Gates
- Kerugian finansial dari scam victims
- Kerusakan reputasi Twitter yang signifikan

**Pelajaran**: Pentingnya strong access controls dan privileged access management.

---

## 🔑 6. Authentication (Autentikasi)

### 6.1 Authentication Methods Matrix

| Method                   | Security Level | Use Case                              | Implementation Cost |
| ------------------------ | -------------- | ------------------------------------- | ------------------- |
| **Password**             | Low-Medium     | General user access                   | Low                 |
| **MFA (Soft Token)**     | Medium-High    | Remote access, privileged access      | Medium              |
| **MFA (Hardware Token)** | High           | Administrative access, sensitive data | High                |
| **Biometric**            | High           | Mobile access, physical security      | High                |
| **Certificate-based**    | High           | System-to-system authentication       | Medium-High         |

### 6.2 Multi-Factor Authentication (MFA)

#### 6.2.1 MFA Implementation Strategy

**Phase 1 (Critical)**:

- Administrative accounts
- Remote access (VPN)
- Cloud administrator consoles

**Phase 2 (High Risk)**:

- Finance and HR systems
- Developer access to production
- Third-party vendor access

**Phase 3 (All Users)**:

- Email and collaboration tools
- Business applications
- Endpoint devices

#### 6.2.2 MFA Best Practices

- **Phishing-Resistant MFA**: FIDO2/WebAuthn untuk high-risk scenarios
- **Backup Methods**: Multiple authentication methods untuk recovery
- **Conditional Access**: Context-aware authentication policies
- **User Experience**: Balance security dengan usability

### 6.3 Password Policy

#### 6.3.1 Modern Password Guidelines

```
Password Requirements:
  - Minimum length: 12 characters
  - No complexity requirements (per NIST guidelines)
  - Check against known breach databases
  - No mandatory periodic reset
  - Password managers encouraged
```

#### 6.3.2 Passwordless Authentication

**Options**:

- **Windows Hello for Business**: Biometric dan PIN
- **FIDO2 Security Keys**: Hardware-based authentication
- **Certificate-based Auth**: Smart cards atau digital certificates

### 6.4 Single Sign-On (SSO)

#### 6.4.1 SSO Architecture

```
User → Identity Provider → Application 1
                      → Application 2
                      → Application 3
```

#### 6.4.2 SSO Protocols

- **SAML 2.0**: Enterprise applications
- **OpenID Connect**: Modern web and mobile apps
- **OAuth 2.0**: API authorization
- **SCIM**: User provisioning standard

---

## 🧱 7. Access Control (Kontrol Akses)

### 7.1 Access Control Models Deep Dive

#### 7.1.1 Discretionary Access Control (DAC)

**Use Case**: File sharing, collaborative environments
**Risks**: Potential for permission sprawl, lack of centralized control

#### 7.1.2 Mandatory Access Control (MAC)

**Use Case**: Government, military, highly regulated environments
**Implementation**: Security labels, clearance levels

#### 7.1.3 Role-Based Access Control (RBAC)

**Implementation Pattern**:

```yaml
Role: Sales Manager
Inherits: Sales Representative
Adds:
  - approve_deals_up_to_10000
  - view_team_performance
  - manage_sales_forecast
```

#### 7.1.4 Attribute-Based Access Control (ABAC)

**Policy Example**:

```json
{
  "effect": "permit",
  "conditions": [
    "user.role == 'manager'",
    "resource.sensitivity == 'confidential'",
    "time.hour between 8 and 18",
    "network.ip_range == 'corporate'"
  ]
}
```

### 7.2 Privileged Access Management (PAM)

#### 7.2.1 PAM Architecture Components

- **Discovery**: Identify semua privileged accounts
- **Vaulting**: Secure storage untuk credentials
- **Session Management**: Controlled access dengan monitoring
- **Audit & Compliance**: Comprehensive logging dan reporting

#### 7.2.2 Just-In-Time Privileged Access

```
Access Request → Approval Workflow → Temporary Access → Time-bound Elevation → Automatic Revocation → Audit Log
```

### 7.3 Access Certification & Reviews

#### 7.3.1 Access Review Process

**Frequency**:

- Critical systems: Quarterly
- High-risk access: Semi-annually
- Standard access: Annually

#### 7.3.2 Review Components

- **User Access Reviews**: Validate current access rights
- **Role Reviews**: Ensure role definitions remain appropriate
- **Policy Reviews**: Update access control policies
- **Exception Reviews**: Review dan approve/deny exceptions

### 📋 STUDI KASUS: Colonial Pipeline Ransomware Attack 2021

**Kejadian**: Ransomware mengganggu operasi pipeline bahan bakar terbesar di AS melalui compromised VPN password.

**Akar Masalah IAM**:

- Single-factor authentication untuk VPN access
- Compromised password yang tidak protected dengan MFA
- Lack of network segmentation berdasarkan identity

**Dampak**:

- Shutdown pipeline selama beberapa hari
- Kekurangan bahan bakar di East Coast
- Pembayaran ransom $4.4 juta

**Pelajaran**: Critical importance of MFA untuk remote access dan network segmentation.

---

## ⚙️ 8. Implementasi Teknis IAM & Access Control

### 8.1 IAM Architecture Blueprint

#### 8.1.1 Core Components

```
Identity Sources    IAM Platform    Target Systems
HR System       → Identity Governance → Applications
Active Directory → Access Management  → Infrastructure
Cloud Directories → Directory Services → Data Sources
                 → Audit & Analytics
```

#### 8.1.2 Integration Patterns

- **HR-Driven Provisioning**: Automatic account creation dari HR events
- **Federation**: SSO across cloud dan on-premise applications
- **API-Based Integration**: Modern applications menggunakan REST APIs
- **Agent-Based Integration**: Legacy systems dengan connector agents

### 8.2 Implementation Roadmap

#### 8.2.1 Phase 1: Foundation (Months 1-6)

- Deploy core identity governance
- Implement MFA untuk privileged access
- Establish basic access certification
- Deploy password management tools

#### 8.2.2 Phase 2: Enhancement (Months 7-18)

- Expand MFA to all users
- Implement privileged access management
- Deploy advanced access governance
- Establish identity analytics

#### 8.2.3 Phase 3: Optimization (Months 19+)

- Implement AI/ML untuk anomaly detection
- Deploy passwordless authentication
- Establish zero-trust architecture
- Continuous optimization

---

## 🔄 9. Monitoring dan Audit

### 9.1 IAM Monitoring Framework

#### 9.1.1 Key Monitoring Scenarios

- **Failed Authentication Attempts**: Multiple failures dari source yang sama
- **Impossible Travel**: Logins dari geographically distant locations dalam waktu singkat
- **After-Hours Access**: Unusual access patterns outside business hours
- **Privileged Access**: Monitoring semua privileged account activities

#### 9.1.2 Alerting Thresholds

```yaml
High Priority Alerts:
  - 5+ failed logins dalam 10 menit
  - Privileged access outside maintenance windows
  - Access from blocked countries
  - New privileged account creation

Medium Priority Alerts:
  - First-time access to sensitive data
  - Access outside normal working hours
  - Bulk data downloads
```

### 9.2 Audit dan Compliance

#### 9.2.1 Audit Requirements

- **Regulatory**: SOX, GDPR, PCI DSS, HIPAA
- **Internal Policies**: Access review certifications
- **Industry Standards**: ISO 27001, NIST CSF

#### 9.2.2 Audit Evidence

- **User Access Reviews**: Quarterly certification reports
- **Privileged Access Logs**: Session recordings dan command logs
- **Change Management**: Access provisioning dan deprovisioning records
- **Policy Compliance**: Evidence of policy enforcement

---

## 🧠 10. Best Practices IAM, Authentication & Access Control

### 10.1 Strategic Best Practices

#### 10.1.1 Program Management

- **Executive Sponsorship**: C-level support untuk IAM initiatives
- **Cross-Functional Team**: Representatives dari IT, security, HR, legal
- **Phased Approach**: Incremental implementation dengan quick wins
- **User Experience Focus**: Balance security dengan productivity

#### 10.1.2 Technical Excellence

- **Zero Trust Principles**: Verify explicitly, assume breach
- **Defense in Depth**: Multiple layers of access controls
- **Automation**: Reduce manual processes dan human error
- **Continuous Improvement**: Regular assessment dan enhancement

### 10.2 Operational Best Practices

| Area                   | Best Practice                         | Metric                             |
| ---------------------- | ------------------------------------- | ---------------------------------- |
| **Identity Lifecycle** | Automated provisioning/deprovisioning | Time to deprovision < 24h          |
| **Authentication**     | Phishing-resistant MFA                | MFA coverage > 95%                 |
| **Access Control**     | Regular access reviews                | Quarterly certification completion |
| **Privileged Access**  | Just-in-time elevation                | Privileged session monitoring 100% |
| **Monitoring**         | Real-time anomaly detection           | Mean time to detect < 1h           |

### 📋 STUDI KASUS: Microsoft Exchange Server Vulnerabilities 2021

**Kejadian**: Exploitation of zero-day vulnerabilities in on-premise Exchange Server mengakibatkan widespread compromises.

**IAM Lessons**:

- Importance of patch management untuk identity systems
- Need for application-level access controls
- Value of credential hardening dan monitoring

**Response Actions**:

- Emergency patching dan credential rotation
- Enhanced monitoring untuk anomalous activities
- Review dan hardening of service account permissions

---

## 📚 11. Referensi

### 11.1 Standards & Frameworks

1. **NIST SP 800-63-3** - Digital Identity Guidelines
2. **ISO/IEC 27001:2022** - Information Security Management Systems
3. **NIST CSF 2.0** - Cybersecurity Framework
4. **ISO/IEC 27002:2022** - Information Security Controls
5. **PCI DSS v4.0** - Payment Card Industry Data Security Standard

### 11.2 Books & Research

6. "Identity and Access Management" by Dr. Abhishek Chopra
7. "Zero Trust Networks" by Evan Gilman and Doug Barth
8. "Cloud Security and Privacy" by Tim Mather et al.
9. Gartner Research - Identity and Access Management
10. Forrester Research - Zero Trust Framework

### 11.3 Regulatory Requirements

11. **UU No. 27 Tahun 2022** - Perlindungan Data Pribadi
12. **GDPR** - General Data Protection Regulation
13. **SOX** - Sarbanes-Oxley Act
14. **HIPAA** - Health Insurance Portability and Accountability Act

---

## 🏁 12. Penutup

### 12.1 Continuous Evolution

IAM bukan destination, melainkan continuous journey. Teknologi, ancaman, dan kebutuhan bisnis terus berkembang, membutuhkan adaptasi dan peningkatan berkelanjutan.

### 12.2 Business Enablement

IAM yang efektif tidak hanya melindungi organisasi, tetapi juga memungkinkan transformasi digital, meningkatkan produktivitas, dan mendukung inovasi bisnis.

### 12.3 Call to Action

Setiap individu dalam organisasi memiliki peran dalam menjaga keamanan identitas dan akses. Melalui kolaborasi, kesadaran, dan disiplin, kita dapat membangun lingkungan digital yang aman dan produktif.

---

## 🔍 Lampiran

### A. IAM Maturity Model

### B. Access Review Templates

### C. IAM RFP Template

### D. Incident Response Playbooks

---

_Handbook ini akan ditinjau dan diperbarui secara berkala untuk memastikan relevansi dengan perkembangan teknologi, ancaman, dan kebutuhan bisnis._

**Ditetapkan di**: [Kota]
**Pada tanggal**: [Tanggal]
**Penanggung Jawab**: Chief Information Security Officer
