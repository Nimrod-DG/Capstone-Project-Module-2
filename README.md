# Capstone Project Module 2 – Analisis Penjualan & Laporan Otomatis

## Deskripsi
Proyek ini mengintegrasikan beberapa komponen untuk:
- **Analisis Data**: Menampilkan hasil penjualan dan profit berdasarkan kategori produk (2011–2014).
- **Dashboard Interaktif**: Dashboard Tableau untuk visualisasi data.
- **Transformasi Data Organisasi**: Script Python untuk meratakan (flatten) hierarki organisasi menjadi format datar demi keperluan Power BI.
- **Otomasi Laporan**: Mengonversi proses R Markdown otomatis menjadi Python script untuk menghasilkan laporan PDF berdasarkan parameter.
- **Styling Front-end**: SCSS untuk komponen sidebar di aplikasi web.

## Fitur Utama
1. **Visualisasi Penjualan & Profit**  
   - Grafik pie *sales by category* (2011–2014)  
   - Grafik pie *profit by category*

2. **Dashboard Tableau**  
   - File `dashboards/CapstoneProject_Module2_DavidGosal.twbx`

3. **Data Flattening untuk Power BI**  
   - Script `scripts/generate_flat_paths.py`

4. **Automasi Laporan PDF**  
   - Konversi R Markdown (`internal_development_report.Rmd`) → Python (`scripts/report_generator.py`)  
   - Input: `data/BcgDemoFinal2_shortUID.xlsx`  
   - Output: folder `reports/` berisi PDF per entitas

5. **SCSS Styling**  
   - File `styles/_sidebar.scss`  
   - Penyesuaian spacing: `.sidebar-title { padding-bottom: 0.55rem; }`

## Struktur Direktori
