HEAD
# Clickjacking Vulnerability Checker

Aplikasi web sederhana untuk memeriksa apakah sebuah website rentan terhadap serangan **clickjacking**.

![Python](https://img.shields.io/badge/Python-3.12-blue)
![Flask](https://img.shields.io/badge/Flask-3.0-green)
![Docker](https://img.shields.io/badge/Docker-Ready-blue)

## 📋 Deskripsi

**Clickjacking** adalah teknik serangan di mana penyerang menyembunyikan elemen berbahaya di balik elemen yang terlihat aman. Aplikasi ini memeriksa apakah website target memiliki proteksi terhadap clickjacking dengan menganalisis header HTTP:

- **X-Frame-Options**: Header yang mencegah halaman dimuat dalam iframe
- **Content-Security-Policy (frame-ancestors)**: Directive CSP yang mengontrol embedding halaman

## 🚀 Cara Menjalankan

### Prasyarat

- [Docker](https://docs.docker.com/get-docker/) terinstall
- [Docker Compose](https://docs.docker.com/compose/install/) terinstall

### Langkah-langkah

1. **Clone repository**
   ```bash
   git clone <repository-url>
   cd uas-udb-ti2401
   ```

2. **Build dan jalankan dengan Docker Compose**
   ```bash
   docker compose up --build
   ```

   Atau jalankan di background:
   ```bash
   docker compose up --build -d
   ```

3. **Akses aplikasi**
   
   Buka browser dan akses: [http://localhost:15000](http://localhost:15000)

4. **Menghentikan aplikasi**
   ```bash
   docker compose down
   ```

### Menggunakan Docker secara manual

Jika tidak ingin menggunakan Docker Compose:

```bash
# Build image
docker build -t clickjacking-checker .

# Jalankan container
docker run -p 15000:15000 clickjacking-checker
```

## 💻 Cara Penggunaan

1. Buka aplikasi di browser: `http://localhost:15000`
2. Masukkan URL website yang ingin diperiksa (contoh: `google.com` atau `https://example.com`)
3. Klik tombol **Periksa**
4. Lihat hasil analisis:
   - ✅ **TERLINDUNGI**: Website memiliki proteksi clickjacking
   - ⚠️ **RENTAN**: Website tidak memiliki proteksi clickjacking

## 🔍 Contoh Hasil

### Website Terlindungi
```
✅ Website TERLINDUNGI dari clickjacking
Proteksi: X-Frame-Options: DENY
```

### Website Rentan
```
⚠️ Website RENTAN terhadap clickjacking!
Tidak ditemukan header X-Frame-Options atau CSP frame-ancestors.
```

## 📁 Struktur Proyek

```
uas-udb-ti2401/
├── app.py                 # Aplikasi Flask utama
├── templates/
│   └── index.html         # Template HTML
├── requirements.txt       # Dependencies Python
├── Dockerfile             # Docker build configuration
├── docker-compose.yml     # Docker Compose configuration
├── .dockerignore          # Files to ignore in Docker build
└── README.md              # Dokumentasi
```

## 🛠️ Teknologi

- **Python 3.12** - Bahasa pemrograman
- **Flask 3.0** - Web framework
- **Gunicorn** - WSGI HTTP Server
- **Docker** - Containerization
- **Docker Compose** - Container orchestration

## 📖 Referensi

- [OWASP Clickjacking Defense Cheat Sheet](https://cheatsheetseries.owasp.org/cheatsheets/Clickjacking_Defense_Cheat_Sheet.html)
- [MDN X-Frame-Options](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/X-Frame-Options)
- [MDN Content-Security-Policy: frame-ancestors](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Content-Security-Policy/frame-ancestors)

## 📝 Lisensi

Proyek ini dibuat untuk tugas UAS UDB TI2401.
UAS Manajemen Jaringan  
Nama: Novi Ardianto  
NIM: 240104012  

origin/uasmanajemenjaringan
# Update dev branch
