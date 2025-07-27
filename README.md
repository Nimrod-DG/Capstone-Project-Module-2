# AWS SaaS Sales Data Analysis

Repositori ini berisi analisis data transaksi penjualan produk SaaS pada AWS (Amazon Web Services).  
Tujuan utama: memahami dan mengoptimalkan performa bisnis—terutama profitabilitas—dengan mengeksplorasi faktor penjualan, segmentasi pelanggan, dan distribusi pasar.

---

## 📖 Latar Belakang
**AWS (Amazon Web Services)** Diluncurkan pada 2006, AWS adalah platform komputasi awan “pay‑as‑you‑go” yang menyediakan infrastruktur TI—mulai dari server virtual (EC2), penyimpanan objek (S3), database terkelola, hingga layanan jaringan—tanpa perlu investasi pusat data fisik. Dengan arsitektur global yang terbagi per region dan Availability Zone, AWS menawarkan skalabilitas otomatis, ketersediaan tinggi, serta berbagai fitur keamanan dan kepatuhan untuk menjalankan beban kerja apa pun, dari aplikasi web sederhana hingga big data dan machine learning.

Sebagai Data Analyst, kita akan:  
- Menganalisa bagaimana karakteristik tren penjualan dan profit produk SaaS di berbagai region, segmen pelanggan, dan produk, serta sejauh mana variasi diskon mempengaruhi profit margin.


- 

Pertanyaan Analitis:
- Apakah terdapat pola musiman dalam volume penjualan dan profit SaaS?
- Region mana yang memberikan kontribusi penjualan dan profit tertinggi?
- Bagaimana perbandingan rata-rata nilai pesanan (Average Order Value) dan margin profit antar segmen?
- Produk SaaS mana yang paling laris dan paling menguntungkan?
- Sejauh mana variasi diskon mempengaruhi profit margin pada setiap transaksi?




---

## 🎯 Tujuan Proyek
> "Menganalisa bagaimana karakteristik tren penjualan dan profit produk SaaS di berbagai region, segmen pelanggan, dan produk, serta sejauh mana variasi diskon mempengaruhi profit margin."

---

## 📝 Business Problem Statements
1. **Profit Identification**  
   - Mengidentifikasi segmen pelanggan dan region yang menghasilkan profit tertinggi. 

2. **Sales Optimisation**  
   - Mengoptimisasi penjualan agar mencapai profit tertinggi.

3. **Product Focus**  
   - Fokus mengembangkan dan promosi produk tertentu


---

## 📊 Dataset
- **Sumber**: AWS SaaS Sales, ~9.994 transaksi (B2B)  
- **Periode**: Jan 2020–Des 2023  
- **Kolom Utama**:

  | Kolom         | Deskripsi                                          |
  | ------------- | -------------------------------------------------- |
  | `Order Date`  | Tanggal transaksi                                  |
  | `Region`      | Region penjualan (AMER, EMEA, APJ, dll.)           |
  | `Subregion`   | Sub‑region dalam setiap region                    |
  | `Segment`     | Segmen pelanggan (SMB, Enterprise, Strategic, dll.) |
  | `Industry`    | Industri pelanggan                                 |
  | `Product`     | Nama produk                                        |
  | `Discount`    | Persentase diskon                                  |
  | `Sales`       | Nilai penjualan                                    |
  | `Profit`      | Keuntungan (bisa negatif)                          |
  | …             | (Total 19 kolom setelah pembersihan & perhitungan ulang `Profit Margin`) |

---

## Alur Analisis

| Tahap | Deskripsi Singkat |
| ----- | ---------------- |
| **1 • Pembersihan** | - Konversi tanggal & tipe data <br> - Deteksi & penanganan nilai hilang / outlier (*IQR* & visual) |
| **2 • EDA** | Statistik deskriptif & visualisasi awal (histogram, box plot, heatmap korelasi) |
| **3 • Time‑Series** | Resampling bulanan/kuartalan, analisis tren & musiman *Profit Margin* |
| **4 • Segmentasi** | Performa per `Segment`, `Industry`, `Customer Size` (RFM sederhana) |
| **5 • Geospasial** | Kontribusi `Region` ➜ `Sub‑Region` menggunakan peta choropleth & bar plot |
| **6 • Diskon vs Kinerja** | Korelasi Pearson & scatter plot 3‑D (Discount‑Sales‑Profit) |
| **7 • Visualisasi Interaktif** | Dashboard Tableau yang menggabungkan filter region, industri, & periode |

---

## 📈 Temuan Utama
- **Marketing Suite**: consistently negative profit margin; perlu prioritas perbaikan.  
- **Diskon vs Profit**: korelasi negatif kuat — diskon > 20 % cenderung menurunkan profit tajam.  
- **Regional Performance**:  
  - AMER: volume tinggi, margin sedang  
  - EMEA & APJ: margin rendah/negatif → strategi lokal diperlukan  
- **Sub‑region & Country**:  
  - Kanada & Mesir menunjukkan profit positif  
  - Prancis & Jepang mengalami kerugian signifikan  
- **Segmentasi**:  
  - SMB terbesar dari segi jumlah pelanggan, namun margin lebih rendah  
  - Enterprise & Strategic memberikan sumbangan profit lebih besar  
- **Customer Highlights**:  
  - **Profit Leaders**: Apple, UPS, Amazon  
  - **High‑Frequency but Loss‑Making**: BNP Paribas, Wells Fargo → peluang upsell atau renegosiasi

---

## Rekomendasi

1. **Strategi Regional**  
   - **Perkuat EMEA & AMER**: alokasikan fokus penjualan dan pemasaran di wilayah berkontribusi tinggi.  
   - **Audit APJ** (terutama JAPN & ANZ): evaluasi ulang pricing, diskon, dan cost structure untuk menghentikan kerugian.

2. **Segmentasi Pelanggan**  
   - **Enterprise**: prioritas upsell, loyalty & paket premium.  
   - **Strategic**: pertahankan dan kembangkan penawaran tambahan.  
   - **SMB**: perkenalkan bundle/add‑on untuk meningkatkan AOV & margin.

3. **Portofolio Produk**  
   - **Optimasi ContactMatcher & Big Ol Database**: atur diskon lebih konservatif, tekankan value‑proposition.  
   - **Skala Alchemy, Data Smasher, Support**: manfaatkan margin tinggi lewat bundling atau promosi terarah.  
   - **Revisi Marketing Suite (standar)**: hentikan atau perbaiki loss‑leader, sesuaikan pricing/cost.

4. **Kebijakan Diskon Terukur**  
   - **Cap diskon di ≤ 20 %** untuk mayoritas transaksi.  
   - **Diskon 20–30 %** hanya untuk campaign terbatas di industry/region toleran (mis. Tech, Manufacturing di AMER/EMEA).  
   - **Hindari diskon > 30 %** secara luas — meski mendorong sales singkat, profitabilitas akan tergerus.

5. **Monitoring & Eksperimen**  
   - Bangun **dashboard real‑time** untuk memantau Sales, Profit, Margin, dan efek diskon per region/industry.  
   - Lakukan **A/B testing** pada skema diskon dan pricing di area kritis (APJ, Retail).  
   - Review berkala hasil implementasi dan sesuaikan strategi sesuai dinamika pasar.

Dengan kesimpulan dan rekomendasi ini, perusahaan siap mengambil langkah-langkah terukur untuk meningkatkan volume penjualan sekaligus memaksimalkan profitabilitas dan efisiensi kebijakan diskon di seluruh dimensi bisnis SaaS.  


---
