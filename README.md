# AWS SaaS Sales Data Analysis

Repositori ini berisi analisis data transaksi penjualan produk SaaS pada AWS (Amazon Web Services).  
Tujuan utama: memahami dan mengoptimalkan performa bisnis—terutama profitabilitas—dengan mengeksplorasi faktor penjualan, segmentasi pelanggan, dan distribusi pasar.

---

## 📖 Latar Belakang
**AWS (Amazon Web Services)** Diluncurkan pada 2006, AWS adalah platform komputasi awan “pay‑as‑you‑go” yang menyediakan infrastruktur TI—mulai dari server virtual (EC2), penyimpanan objek (S3), database terkelola, hingga layanan jaringan—tanpa perlu investasi pusat data fisik. Dengan arsitektur global yang terbagi per region dan Availability Zone, AWS menawarkan skalabilitas otomatis, ketersediaan tinggi, serta berbagai fitur keamanan dan kepatuhan untuk menjalankan beban kerja apa pun, dari aplikasi web sederhana hingga big data dan machine learning.

Sebagai Data Analyst, kita akan:  
- Menganalisa bagaimana karakteristik tren penjualan dan profit produk SaaS di berbagai region, segmen pelanggan, dan produk, serta sejauh mana variasi diskon mempengaruhi profit margin.

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
Berdasarkan seluruh rangkaian analisis — mulai dari pola musiman, kontribusi regional & subregional, segmentasi pelanggan, kinerja produk, hingga dampak diskon — diperoleh poin‑poin utama berikut:

1. **Pola dan Tren Musiman**  
   - Tidak ada pola musim yang konsisten pada Sales maupun Profit Margin bulanan; fluktuasi terjadi secara sporadis sepanjang 2020–2023.  
   - Terdapat kecenderungan margin sedikit lebih tinggi pada Agustus–September dan Desember, serta terendah pada April, Mei, dan Oktober.

2. **Kontribusi Regional & Subregional**  
   - **EMEA** memimpin total Sales & Profit (≈ \$1.04 M & \$147K), margin rata‑rata 17 %.  
   - **AMER** memiliki margin tertinggi (≈ 22 %) dengan Sales ≈ \$838K dan Profit ≈ \$127K.  
   - **APJ** mencatat margin negatif (≈ – 15 %) meski Sales mencapai ≈ \$415K, menyiratkan masalah pricing atau biaya di wilayah ini.  
   - Subregion **NAMER** & **UKIR** unggul dari sisi margin (> 27 %) dan volume, sedangkan **JAPN** & **ANZ** (APJ) mencetak margin sangat negatif (> – 34 %).

3. **Perbandingan Segmen Pelanggan**  
   - **Enterprise**: AOV tertinggi (~ \$473) & margin ~ 14.3 %.  
   - **Strategic**: AOV ~ \$466 & margin ~ 12.1 %.  
   - **SMB**: AOV terendah (~ \$449) & margin ~ 11.2 %.  
   - Uji ANOVA menunjukkan perbedaan margin antar segmen tidak signifikan pada α=5 % (p = 0.055), meski secara bisnis Enterprise menonjol.

4. **Kinerja Produk**  
   - **ContactMatcher** & **Big Ol Database**: Sales tinggi (> \$189K) tetapi margin rendah (≤ 3 %).  
   - **Alchemy**, **Data Smasher**, **Support**: margin tinggi (25–37 %) dengan volume menengah (≈ \$125–150K).  
   - **Marketing Suite (standar)**: margin negatif (~ – 3 %) dengan outlier rugi besar.

5. **Dampak Kebijakan Diskon**  
   - Korelasi **Discount vs Profit Margin** sangat negatif (r = – 0.86), vs Profit juga negatif (r = – 0.22), vs Sales hampir nol (r = – 0.03).  
   - **Diskon ≤ 16 %**: sales & profit margin paling sehat.  
   - **Diskon 16–32 %**: margin mulai tertekan, namun profit masih positif.  
   - **Diskon > 32 %**: menimbulkan lonjakan sales jangka pendek (bin 32–48 %), tetapi profit & margin menjadi negatif.
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
