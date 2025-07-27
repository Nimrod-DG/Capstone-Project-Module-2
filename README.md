# 📊  Capstone Project Module 2 – **Analisis Penjualan SaaS**

Repositori ini berisi rangkaian *data analysis* untuk memahami pola penjualan ‑ sampai profitabilitas ‑ sebuah perusahaan **Software‑as‑a‑Service (SaaS)** fiktif berdasarkan dataset **AWS SaaS Sales**.  
Hasil akhir berupa **notebook Jupyter**, **dashboard Tableau**, dan **deck presentasi** yang dapat langsung digunakan manajemen dalam pengambilan keputusan.

---

## Daftar Isi
1. [Latar Belakang](#latar-belakang)  
2. [Tujuan Proyek](#tujuan-proyek)  
3. [Dataset](#dataset)  
4. [Alur Analisis](#alur-analisis)  
5. [Insight Utama](#insight-utama)  
6. [Struktur Repositori](#struktur-repositori)  
7. [Cara Menjalankan Proyek](#cara-menjalankan-proyek)  
8. [Dashboard Tableau](#dashboard-tableau)  
9. [Lisensi & Kredit](#lisensi--kredit)  

---

## Latar Belakang
Pertumbuhan bisnis SaaS sangat dipengaruhi oleh **struktur harga, kebijakan diskon, dan segmentasi pelanggan**. Evaluasi periodik terhadap performa penjualan membantu perusahaan untuk:

* Mengidentifikasi segmen & wilayah dengan kontribusi tertinggi/t terendah  
* Mengoptimalkan strategi penetapan harga dan diskon  
* Memetakan peluang ekspansi berdasarkan tren profit margin  

---

## Tujuan Proyek
*Menjawab pertanyaan bisnis kunci:*

| Kategori Pertanyaan | Contoh |
| ------------------- | ------ |
| **Tren & Musiman**  | Bagaimana pola *sales* dan *profit margin* 2020‑2023? |
| **Segmentasi**      | Segmen pelanggan & industri apa yang paling menguntungkan? |
| **Geografi**        | Wilayah mana yang layak diprioritaskan untuk ekspansi? |
| **Harga & Diskon**  | Sejauh mana diskon memengaruhi volume penjualan dan laba? |

---

## Dataset
| Sumber | Kaggle – [*AWS SaaS Sales*](https://www.kaggle.com/datasets/nnthanh101/aws-saas-sales) |
| ------ | ----------------------------------------------- |
| Periode | Jan 2020 – Des 2023 |
| Observasi | ± 10 000 transaksi |
| Fitur utama* | `Order Date`, `Region`, `Segment`, `Industry`, `Product Category`, `Quantity`, `Sales`, `Discount`, `Profit`, `Profit Margin`, dll. |
| Catatan | Kolom tidak relevan (`Date Key`, `Row ID`, `License`) dihapus; `Profit Margin` dihitung ulang. |

\*Total 19 kolom setelah pembersihan.

---

## Alur Analisis

| Tahap | Deskripsi Singkat |
| ----- | ---------------- |
| **1 • Pembersihan** | - Konversi tanggal & tipe data <br> - Deteksi & penanganan nilai hilang / outlier (*IQR* & visual) |
| **2 • EDA** | Statistik deskriptif & visualisasi awal (histogram, box plot, heatmap korelasi) |
| **3 • Time‑Series** | Resampling bulanan/kuartalan, analisis tren & musiman *Profit Margin* |
| **4 • Segmentasi** | Performa per `Segment`, `Industry`, `Customer Size` (RFM sederhana) |
| **5 • Geospasial** | Kontribusi `Region` ➜ `Sub‑Region` menggunakan peta choropleth & bar plot |
| **6 • Diskon vs Kinerja** | Korelasi Pearson & scatter plot 3‑D (Discount‑Sales‑Profit) |
| **7 • Visualisasi Interaktif** | Dashboard Tableau yang menggabungkan filter region, industri, & periode |

---

> Rekomendasi lengkap dapat dilihat pada slide [📑 View Presentation on Canva](https://www.canva.com/design/DAGuWZfF5ss/Elxe7XaNsuGPvbYMEihmhA/edit?utm_content=DAGuWZfF5ss&utm_campaign=designshare&utm_medium=link2&utm_source=sharebutton)

---
