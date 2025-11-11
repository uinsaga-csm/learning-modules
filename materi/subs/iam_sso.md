# Single Sign On (SSO)

## 🧩 **1. SAML 2.0 (Security Assertion Markup Language)**

### 📍 Tujuan:

> Digunakan untuk **Single Sign-On (SSO)** di **lingkungan enterprise (perusahaan)** — biasanya antar aplikasi internal seperti HR, ERP, CRM, dsb.

### 📚 Konsep Dasar:

SAML menggunakan **XML** sebagai format pesan dan bekerja terutama di **web berbasis browser**.

Ada tiga komponen utama:

1. **User (Principal)** – pengguna yang login.
2. **Identity Provider (IdP)** – pihak yang mengelola login (misalnya: Microsoft ADFS, Okta, Google Workspace).
3. **Service Provider (SP)** – aplikasi yang ingin diakses (misalnya: Salesforce, SAP, Zendesk).

---

### 🔁 Alur Kerja (Flow):

1. **User mengakses aplikasi (SP)** → contoh: karyawan buka `https://salesforce.company.com`
2. **SP mendeteksi user belum login** → SP mengarahkan user ke **Identity Provider (IdP)**.
3. **User login di IdP** → misal login ke `https://sso.company.com` pakai email & password.
4. **IdP membuat “SAML Assertion”** (berisi identitas user dalam format XML).
5. **Assertion dikirim kembali ke SP** (biasanya via browser redirect / POST).
6. **SP memverifikasi tanda tangan digital (digital signature)** dari IdP.
7. **SP membuat session login untuk user** tanpa user harus login ulang.

---

### 🧠 Contoh Nyata:

> Perusahaan menggunakan **Okta** sebagai IdP dan **Salesforce** sebagai SP.
> Karyawan hanya login sekali ke portal Okta → lalu bisa langsung masuk ke Salesforce, SAP, Confluence tanpa memasukkan password lagi.

---

## 🌐 **2. OpenID Connect (OIDC)**

### 📍 Tujuan:

> Digunakan untuk **modern web & mobile apps** sebagai protokol **authentication (otentikasi)** berbasis **OAuth 2.0**.

### 📚 Konsep Dasar:

OpenID Connect = OAuth 2.0 + Lapisan tambahan identitas.
Format pesannya **JSON** (lebih ringan dari SAML).

Komponen utama:

1. **User (Resource Owner)**
2. **Client (Aplikasi)** – contoh: aplikasi mobile.
3. **Authorization Server (Identity Provider)** – contoh: Google, Apple, Auth0.
4. **Resource Server (API)** – server yang menyimpan data user.

---

### 🔁 Alur Kerja (Flow):

1. User membuka aplikasi (misal: login dengan Google).
2. Aplikasi mengarahkan user ke halaman login Google.
3. Setelah login sukses, Google mengirim:

   * **ID Token** (berisi identitas user → siapa dia),
   * **Access Token** (untuk mengakses API).
4. Aplikasi memverifikasi ID Token dan membuat session login untuk user.

---

### 🧠 Contoh Nyata:

> Aplikasi mobile seperti **Spotify** atau **Medium** yang menawarkan “Login with Google / Apple”.
> Mereka memakai **OpenID Connect** untuk otentikasi user secara aman dan cepat.

---

## 🔐 **3. OAuth 2.0 (Open Authorization)**

### 📍 Tujuan:

> Untuk **otorisasi (authorization)** — memberi izin aplikasi pihak ketiga mengakses **API** atas nama pengguna.

### 📚 Konsep Dasar:

OAuth 2.0 **tidak mengurus login user**, tapi **izin akses data**.

Pihak yang terlibat:

1. **Resource Owner (User)**
2. **Client (Aplikasi pihak ketiga)**
3. **Authorization Server**
4. **Resource Server (API)**

---

### 🔁 Alur Kerja (Flow):

1. User ingin menghubungkan aplikasi pihak ketiga → contoh: aplikasi “Calendar Sync” ingin mengakses Google Calendar user.
2. Aplikasi redirect user ke Google untuk **izin akses**.
3. User menekan tombol “Allow”.
4. Google mengirim **Authorization Code** ke aplikasi.
5. Aplikasi menukar code tersebut dengan **Access Token**.
6. Aplikasi pakai token itu untuk memanggil API (misal, membaca daftar acara di Google Calendar).

---

### 🧠 Contoh Nyata:

> Saat kamu login ke aplikasi dengan opsi “Connect with Facebook” dan aplikasi bisa mengakses **foto atau daftar teman**, itu memakai **OAuth 2.0** untuk otorisasi data — **tanpa tahu password-mu**.

---

## 👥 **4. SCIM (System for Cross-domain Identity Management)**

### 📍 Tujuan:

> Untuk **user provisioning** — yaitu membuat, memperbarui, atau menghapus akun user secara otomatis di berbagai sistem.

### 📚 Konsep Dasar:

* SCIM **bukan protokol login**, tapi **standar untuk sinkronisasi identitas** antar sistem.
* Biasanya bekerja **bersama SSO** agar user dan hak akses tetap sinkron.
* Format data: **JSON / REST API**.

---

### 🔁 Alur Kerja (Flow):

1. HR menambahkan karyawan baru di sistem HR (misalnya Workday).
2. SCIM secara otomatis mengirim request ke aplikasi lain (misalnya Okta, Google Workspace, Jira) untuk **membuat akun user baru** dengan data yang sama.
3. Jika karyawan resign → SCIM menghapus atau menonaktifkan akun di semua aplikasi.

---

### 🧠 Contoh Nyata:

> Perusahaan menggunakan **Azure AD + SCIM**.
> Saat HR menambahkan karyawan baru, **akun otomatis dibuat di Slack, Zoom, dan GitHub** tanpa manual input oleh admin IT.

---

## 📊 **Ringkasan Perbandingan**

| Protokol           | Tujuan Utama                               | Format Data | Use Case                    | Contoh                                                |
| ------------------ | ------------------------------------------ | ----------- | --------------------------- | ----------------------------------------------------- |
| **SAML 2.0**       | SSO untuk aplikasi enterprise              | XML         | Web perusahaan, ERP, CRM    | Login ke Salesforce via Okta                          |
| **OpenID Connect** | Login modern (authentication)              | JSON (JWT)  | Web & Mobile Apps           | Login with Google / Apple                             |
| **OAuth 2.0**      | API authorization                          | JSON        | Izin akses API pihak ketiga | Aplikasi bisa baca Google Calendar                    |
| **SCIM**           | User provisioning (sinkronisasi identitas) | JSON / REST | HR & Identity Sync          | Otomatis buat akun Slack saat karyawan baru bergabung |

---

## ⚙️ **1. Konsep Dasar**

| Aspek                | **OAuth 2.0**                                                    | **OpenID Connect (OIDC)**                                              |
| -------------------- | ---------------------------------------------------------------- | ---------------------------------------------------------------------- |
| **Tujuan utama**     | Memberikan **izin akses (authorization)** ke API atas nama user. | Melakukan **otentikasi (authentication)** untuk mengenali siapa user.  |
| **Fungsi utama**     | “Apakah aplikasi ini boleh mengakses data user?”                 | “Siapa user ini?”                                                      |
| **Output utama**     | ✅ *Access Token* (untuk akses API).                              | ✅ *ID Token* (untuk identitas user) + Access Token (opsional).         |
| **Format token**     | Biasanya string acak (bisa JWT, bisa tidak).                     | Selalu JWT (JSON Web Token) dengan klaim identitas (nama, email, dsb). |
| **Digunakan oleh**   | API dan aplikasi pihak ketiga (authorization server).            | Aplikasi yang butuh login user (web, mobile, dll).                     |
| **Standar tambahan** | —                                                                | Lapisan tambahan di atas OAuth 2.0 (menambahkan “Identity Layer”).     |

---

## 💡 **2. Analogi Mudah**

Bayangkan kamu masuk ke **perpustakaan digital**:

* **OAuth 2.0** = kamu memberi **izin** ke aplikasi (misalnya “BookApp”) agar bisa **mengambil daftar buku yang kamu pinjam** dari perpustakaan tanpa memberi password kamu.
  👉 Jadi fokusnya: **izin akses ke data**.

* **OpenID Connect** = kamu **login ke BookApp dengan akun perpustakaanmu** supaya aplikasi tahu siapa kamu.
  👉 Fokusnya: **login / autentikasi user**.

---

## 🔁 **3. Alur Singkat**

### 🟩 OAuth 2.0 Flow (Authorization)

1. User buka aplikasi pihak ketiga (misal: "Photo Editor").
2. Aplikasi redirect ke Google:
   “Boleh nggak saya akses foto kamu di Google Photos?”
3. User klik “Allow”.
4. Google kirim **Authorization Code** ke aplikasi.
5. Aplikasi tukar code → dapat **Access Token**.
6. Aplikasi pakai Access Token untuk **mengambil data foto user** lewat API.

📦 Token yang diterima:
→ `Access Token` (buat akses API).
Tidak tahu siapa usernya (tidak ada data nama/email).

---

### 🟦 OpenID Connect Flow (Authentication)

1. User buka aplikasi dan klik “Login with Google”.
2. Aplikasi redirect ke halaman login Google.
3. User login → Google kirim:

   * **ID Token (JWT)** → berisi identitas user (`name`, `email`, `sub`, dsb).
   * **Access Token (opsional)** → jika aplikasi juga perlu akses API.
4. Aplikasi verifikasi ID Token → tahu “Oh, ini user bernama Budi, emailnya [budi@gmail.com](mailto:budi@gmail.com)”.
5. User langsung login ke aplikasi.

📦 Token yang diterima:
→ `ID Token` (untuk autentikasi)
→ `Access Token` (opsional, untuk akses API)

---

## 🧠 **4. Contoh Nyata**

| Kasus                                                          | Teknologi yang Digunakan       | Tujuan                                        |
| -------------------------------------------------------------- | ------------------------------ | --------------------------------------------- |
| “Login with Google” di aplikasi web                            | **OpenID Connect**             | Aplikasi hanya ingin tahu siapa user (login). |
| Aplikasi pihak ketiga ingin membaca email user dari Gmail      | **OAuth 2.0**                  | Aplikasi butuh izin untuk akses data Gmail.   |
| Aplikasi ingin login user dan juga akses data Google Drive-nya | **OpenID Connect + OAuth 2.0** | Kombinasi: login + izin akses data.           |

---

## 🔐 **5. Visual Perbandingan Alur**

```
OAuth 2.0 → Authorization Only
--------------------------------
User → (grants permission) → App → Access Token → Access API data


OpenID Connect → Authentication + Authorization
-----------------------------------------------
User → (logs in) → Identity Provider → ID Token (who user is)
                                         + Access Token (optional)
```

---

## 📋 **Kesimpulan Akhir**

| Aspek       | **OAuth 2.0**                                | **OpenID Connect (OIDC)**              |
| ----------- | -------------------------------------------- | -------------------------------------- |
| Fokus       | Authorization (izin akses API)               | Authentication (login user)            |
| Token utama | Access Token                                 | ID Token (JWT)                         |
| Format      | Bisa apa saja                                | Selalu JWT                             |
| Tujuan      | Memberi akses ke data user                   | Mengidentifikasi user                  |
| Contoh      | “Izinkan aplikasi X membaca Google Calendar” | “Login ke aplikasi dengan akun Google” |


