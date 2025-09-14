# TUGAS-SCRAPING-1-AHMAD-AQIIL-FARRAS

## Latar Belakang Pemilihan Portal Berita

Saya memilih dua portal berita, **Liputan6.com** dan **Antara News**, dengan pertimbangan sebagai berikut:

1. **Aksesibilitas Struktur HTML**

   - Liputan6.com memiliki struktur berita yang konsisten menggunakan elemen `<div>` dengan kelas tertentu untuk daftar artikel.
   - Antara News lebih sederhana dan banyak menggunakan elemen `<article>` dan `<h2>`, sehingga cocok untuk latihan scraping dengan BeautifulSoup.

2. **Variasi Data**

   - Liputan6 menyediakan kategori berita yang beragam, termasuk bisnis, teknologi, dan gaya hidup.
   - Antara menonjol sebagai portal berita resmi negara dengan gaya penyajian berbeda, sehingga menarik untuk membandingkan hasil scraping dari dua tipe media.

3. **Studi Kasus Nyata**  
   Dengan menggabungkan Liputan6 dan Antara, saya dapat menunjukkan bagaimana satu skrip scraping dapat diadaptasi untuk situs media komersial (Liputan6) dan situs berita resmi (Antara).

---

## Penjelasan Rinci Alur Kode

### 1. Persiapan Alat

- **requests** → mengambil halaman web.
- **BeautifulSoup (bs4)** → parsing HTML dan mencari elemen tertentu.
- **pandas** → menyusun hasil scraping dalam bentuk tabel (CSV/Excel).
- **json** → menyimpan data dalam format JSON.

### 2. Mengunjungi Halaman & Mengambil Artikel

- Skrip mengakses URL target (Liputan6 & Antara).
- Dengan `soup.find_all(...)`, skrip mencari blok berita sesuai struktur HTML masing-masing portal.

### 3. "Membongkar" Isi Artikel

**Liputan6:**

- **Judul** → dari tag `<a>` dengan kelas `articles--rows--item__title-link`.
- **Link** → dari atribut `href` di dalam tag `<a>`.
- **Ringkasan/lead** → dari tag `<p>` atau deskripsi singkat artikel.

**Antara:**

- **Judul** → dari tag `<h2>` di dalam `<article>`.
- **Link** → dari tag `<a>` pada judul artikel.
- **Metadata tambahan** (penulis/waktu) tidak selalu tersedia di halaman utama, sehingga diisi nilai default (`None`).

### 4. Mengumpulkan & Mengekspor Data

- Setiap berita disimpan sebagai dictionary (judul, link, ringkasan/kategori).
- Semua berita dimasukkan ke dalam list `collected_data`.
- Data diekspor ke **JSON**, **CSV**, dan **XLSX** untuk memudahkan analisis lebih lanjut.

---

## Kesimpulan

Scraping portal berita membutuhkan pemahaman struktur HTML setiap situs.

- **Liputan6** lebih kaya akan variasi kategori.
- **Antara** lebih sederhana namun tetap memberikan data berita yang relevan.

Dengan kombinasi keduanya, hasil scraping lebih variatif dan bisa dijadikan bahan analisis perbandingan.
