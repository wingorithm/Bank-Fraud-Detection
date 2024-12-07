# Analasis Transaksi Fraud Perbankan - Erwin Gunawan

## Domain Proyek (Keuangan, Ekonomi, dan bisnis)
Fraud Detection (deteksi penipuan) dalam transaksi keuangan telah menjadi hal yang krusial bagi bank dan lembaga keuangan di seluruh dunia. Seiring berkembangnya transaksi digital karena kemajuan teknologi yang pesat, aktivitas penipuan juga meningkat sama pesatnya, dan menyebabkan kerugian finansial yang merusak kepercayaan konsumen. Association of Certified Fraud Examiners (ACFE) melaporkan, organisasi setidaknya kehilangan sekitar 5% dari annual revenue karena penipuan, yang berarti miliaran dolar secara global setiap tahun [[1]](https://legacy.acfe.com/report-to-the-nations/2020/). data ini menggarisbawahi bahwa adanya urgensi untuk memiliki mekanisme _fraud detection_ yang efektif. Laporan oleh Komisi Perdagangan Federal (FTC) juga mengungkapkan peningkatan 70% dalam kasus pencurian identitas yang dilaporkan dalam beberapa tahun terakhir, menekankan bahwa perlunya strategi pencegahan penipuan yang kuat [[3]](https://www.ftc.gov/system/files/ftc_gov/pdf/CSN%20Annual%20Data%20Book%202021%20Final%20PDF.pdf). Melihat perkembangan digital dan finansial di Indonesia, Indonesia sekarang menenpati ranking 56 dari 63 negara dalam hal digital literacy (survey daru World Digital Competitiveness Index oleh Institute Management Development) [[4]](https://indonesiabaik.id/videografis/indonesia-makin-melek-literasi-digital). Selama beberapa tahun terakhir, Indonesia juga telah mengalami peningkatan yang signifikan dalam adopsi layanan perbankan digital. Penggunaan channel ini tiap bulannya tumbuh 2x lipat dari negara berkembang di Asia lainnya. Hingga tahun 2023, 58% konsumen Indonesia memanfaatkan layanan perbankan digital, peningkatan yang signifikan dari tahun-tahun sebelumnya laporan dari McKinsey [[5]](https://www.mckinsey.com/industries/financial-services/our-insights/digital-banking-in-indonesia-building-loyalty-and-generating-growth).

Machine Learning (ML) muncul sebagai alat yang peting dan efektif dalam memerangi _fraud_, menawarkan teknik canggih untuk menganalisis data transaksi dalam jumlah besar serta mengidentifikasi _anomaly pattern_ yang mungkin menunjukkan perilaku _fraud_. Hal ini dibuktikan dengan performa model seperti Random Forest dan Support Vector Machines secara signifikan mengungguli metode statistik tradisional dalam efektivitasnya untuk mendeteksi penipuan kartu kredit [[2]](https://www.researchgate.net/publication/383699937_Financial_fraud_detection_through_the_application_of_machine_learning_techniques_a_literature_review). Kemampuan ML untuk belajar dari data historis dan beradaptasi dengan pattern baru membuatnya sangat cocok untuk lingkungan yang dinamis seperti transaksi keuangan. Selain itu, semakin canggihnya skema penipuan memerlukan peningkatan berkelanjutan dalam metodologi deteksi. Karena lembaga keuangan berusaha untuk melindungi aset mereka dan menjaga kepercayaan pelanggan, memanfaatkan machine learning untuk predictive analysis dalam fraud detection tidak hanya bermanfaat tetapi juga penting. Dari kondisi pertumbuhan financial di sektor digital di Indoneisa, rendahnya literasi digital, dan pesatnya pertumbuhan skema fraud, integrasi Machine Learning menjadi semakin penting. Machine Learning untuk proses fraud detection merupakan pendekatan yang proaktif, dan solusi inovatif untuk memerangi penipuan secara efektif.

## Business Understanding
### Problem Statements
Berdasarkan latar belakang yang telah dijelaskan, maka permasalahan yang ingin diselesaikan dalam proyek ini meliputi:
1. Bagaimana cara mempersiapkan dataset transaksi perbankan agar siap digunakan untuk membangun model machine learning?
2. Bagaimana cara membangun model machine learning yang efektif untuk mendeteksi kecurangan dalam transaksi perbankan?
3. Apa saja metrik evaluasi yang tepat untuk menilai performa model dalam mendeteksi fraud?

### Goals

Berdasarkan rumusan masalah yang telah dipaparkan di atas, tujuan utama proyek ini adalah::
1. Melakukan proses data preparation yang mencakup pembersihan, transformasi, dan eksplorasi dataset (EDA) untuk memastikan data siap digunakan dalam pembuatan model.
2. Membuat model machine learning yang mampu mendeteksi transaksi mencurigakan secara akurat dengan tingkat false positive yang rendah.
3. Menggunakan metrik evaluasi seperti precision, recall, dan F1-score untuk mengukur performa model dalam mendeteksi fraud.

### Solution Statements
Untuk mencapai tujuan yang telah ditetapkan, solusi yang diajukan dalam proyek ini meliputi:
1. **Baseline Model**, Menggunakan algoritma seperti Logistic Regression dan Decision Tree untuk membuat model awal (baseline model). Model ini akan memberikan gambaran awal tentang performa model tanpa optimasi.

2. **Advanced Model**, Meningkatkan performa model dengan menggunakan algoritma yang lebih kompleks seperti Random Forest, Gradient Boosting (XGBoost/LightGBM), atau Neural Networks. Algoritma ini akan dibandingkan dengan model baseline untuk mendapatkan hasil yang optimal.

3. **Hyperparameter Tuning**:
Melakukan hyperparameter tuning untuk meningkatkan akurasi model dan meminimalkan false positive dalam pendeteksian transaksi fraud.

_Data Augmentation dan Resampling:
Mengatasi masalah ketidakseimbangan data (jika ada) menggunakan teknik seperti SMOTE atau undersampling untuk memastikan model tidak bias terhadap kelas mayoritas.
_
=========================================================================================
## Data Understanding
Paragraf awal bagian ini menjelaskan informasi mengenai data yang Anda gunakan dalam proyek. Sertakan juga sumber atau tautan untuk mengunduh dataset. Contoh: [UCI Machine Learning Repository](https://archive.ics.uci.edu/ml/datasets/Restaurant+%26+consumer+data).

Selanjutnya uraikanlah seluruh variabel atau fitur pada data. Sebagai contoh:  

### Variabel-variabel pada Restaurant UCI dataset adalah sebagai berikut:
- accepts : merupakan jenis pembayaran yang diterima pada restoran tertentu.
- cuisine : merupakan jenis masakan yang disajikan pada restoran.
- dst

**Rubrik/Kriteria Tambahan (Opsional)**:
- Melakukan beberapa tahapan yang diperlukan untuk memahami data, contohnya teknik visualisasi data atau exploratory data analysis.

## Data Preparation
Pada bagian ini Anda menerapkan dan menyebutkan teknik data preparation yang dilakukan. Teknik yang digunakan pada notebook dan laporan harus berurutan.

**Rubrik/Kriteria Tambahan (Opsional)**: 
- Menjelaskan proses data preparation yang dilakukan
- Menjelaskan alasan mengapa diperlukan tahapan data preparation tersebut.

## Modeling
Tahapan ini membahas mengenai model machine learning yang digunakan untuk menyelesaikan permasalahan. Anda perlu menjelaskan tahapan dan parameter yang digunakan pada proses pemodelan.

**Rubrik/Kriteria Tambahan (Opsional)**: 
- Menjelaskan kelebihan dan kekurangan dari setiap algoritma yang digunakan.
- Jika menggunakan satu algoritma pada solution statement, lakukan proses improvement terhadap model dengan hyperparameter tuning. **Jelaskan proses improvement yang dilakukan**.
- Jika menggunakan dua atau lebih algoritma pada solution statement, maka pilih model terbaik sebagai solusi. **Jelaskan mengapa memilih model tersebut sebagai model terbaik**.

## Evaluation
Pada bagian ini anda perlu menyebutkan metrik evaluasi yang digunakan. Lalu anda perlu menjelaskan hasil proyek berdasarkan metrik evaluasi yang digunakan.

Sebagai contoh, Anda memiih kasus klasifikasi dan menggunakan metrik **akurasi, precision, recall, dan F1 score**. Jelaskan mengenai beberapa hal berikut:
- Penjelasan mengenai metrik yang digunakan
- Menjelaskan hasil proyek berdasarkan metrik evaluasi

Ingatlah, metrik evaluasi yang digunakan harus sesuai dengan konteks data, problem statement, dan solusi yang diinginkan.

**Rubrik/Kriteria Tambahan (Opsional)**: 
- Menjelaskan formula metrik dan bagaimana metrik tersebut bekerja.

## Reference
[1] Association of Certified Fraud Examiners (ACFE). (2020). Report to the Nations: Global Study on Occupational Fraud and Abuse.

[2] Zhang, Y., Wang, S., & Chen, X. (2019). Behavioral analytics for fraud detection: A review. IEEE Access, 7, 11212-11223.

[3] Federal Trade Commission (FTC). (2021). Consumer Sentinel Network Data Book.

[4] indonesia digital literacy -> https://indonesiabaik.id/videografis/indonesia-makin-melek-literasi-digital

[5] digital banking in indonesia -> https://www.mckinsey.com/industries/financial-services/our-insights/digital-banking-in-indonesia-building-loyalty-and-generating-growth
