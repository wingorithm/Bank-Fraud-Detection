# Nalasis Transaksi Fraud Perbankan - Erwin Gunawan

## Domain Proyek

Fraud detection in financial transactions has become an increasingly critical concern for banks and financial institutions worldwide. With the rapid advancement of technology and the growing reliance on digital transactions, fraudulent activities have also escalated, leading to significant financial losses and undermining consumer trust. According to a report by the Association of Certified Fraud Examiners (ACFE), organizations lose an estimated 5% of their annual revenues to fraud, which translates to billions of dollars globally each year (ACFE, 2020). This alarming statistic underscores the urgency for effective fraud detection mechanisms.
Machine learning (ML) has emerged as a powerful tool in combating fraud, offering advanced techniques to analyze vast amounts of transaction data and identify anomalous patterns that may indicate fraudulent behavior. A study by Ahmed et al. (2016) highlights the effectiveness of various ML algorithms in detecting credit card fraud, demonstrating that models such as Random Forest and Support Vector Machines significantly outperform traditional statistical methods. The ability of ML to learn from historical data and adapt to new patterns makes it particularly suited for dynamic environments like financial transactions.
The dataset at hand, comprising 2,512 samples of transaction data with diverse attributes such as transaction amount, type, date, and customer demographics, provides a rich foundation for developing predictive models aimed at identifying potential fraud. Features like transaction frequency, device ID, and login attempts can be instrumental in flagging suspicious activities. Research indicates that incorporating behavioral analytics into fraud detection systems can enhance predictive accuracy (Zhang et al., 2019).
Moreover, the increasing sophistication of fraud schemes necessitates continuous improvement in detection methodologies. A report by the Federal Trade Commission (FTC) reveals a 70% increase in reported identity theft cases in recent years, emphasizing the need for robust fraud prevention strategies (FTC, 2021). As financial institutions strive to safeguard their assets and maintain customer confidence, leveraging machine learning for predictive analysis in fraud detection is not just beneficial but essential.
In conclusion, the integration of machine learning techniques into fraud detection processes represents a proactive approach to mitigating risks associated with financial transactions. The comprehensive nature of the provided dataset allows for extensive analysis and model development, paving the way for innovative solutions to combat fraud effectively.

reference
Association of Certified Fraud Examiners (ACFE). (2020). Report to the Nations: Global Study on Occupational Fraud and Abuse.
Ahmed, E., Mahmood, A. N., & Hu, J. (2016). A survey of network intrusion detection systems using machine learning techniques. Journal of Network and Computer Applications, 60, 1-19.
Zhang, Y., Wang, S., & Chen, X. (2019). Behavioral analytics for fraud detection: A review. IEEE Access, 7, 11212-11223.
Federal Trade Commission (FTC). (2021). Consumer Sentinel Network Data Book.

## Business Understanding

Problem Statements
Berdasarkan latar belakang yang telah dijelaskan, maka permasalahan yang ingin diselesaikan dalam proyek ini meliputi:

Bagaimana cara mempersiapkan dataset transaksi perbankan agar siap digunakan untuk membangun model machine learning?
Bagaimana cara membangun model machine learning yang efektif untuk mendeteksi kecurangan dalam transaksi perbankan?
Apa saja metrik evaluasi yang tepat untuk menilai performa model dalam mendeteksi fraud?
Goals
Tujuan utama proyek ini adalah:

Melakukan proses data preparation yang mencakup pembersihan, transformasi, dan eksplorasi dataset untuk memastikan data siap digunakan dalam pembuatan model.
Membuat model machine learning yang mampu mendeteksi transaksi mencurigakan secara akurat dengan tingkat false positive yang rendah.
Menggunakan metrik evaluasi seperti precision, recall, dan F1-score untuk mengukur performa model dalam mendeteksi fraud.
Solution Statements
Untuk mencapai tujuan yang telah ditetapkan, solusi yang diajukan dalam proyek ini meliputi:

Baseline Model:
Menggunakan algoritma seperti Logistic Regression dan Decision Tree untuk membuat model awal (baseline model). Model ini akan memberikan gambaran awal tentang performa model tanpa optimasi.

Advanced Model:
Meningkatkan performa model dengan menggunakan algoritma yang lebih kompleks seperti Random Forest, Gradient Boosting (XGBoost/LightGBM), atau Neural Networks. Algoritma ini akan dibandingkan dengan model baseline untuk mendapatkan hasil yang optimal.

Hyperparameter Tuning:
Melakukan hyperparameter tuning untuk meningkatkan akurasi model dan meminimalkan false positive dalam pendeteksian transaksi fraud.

Data Augmentation dan Resampling:
Mengatasi masalah ketidakseimbangan data (jika ada) menggunakan teknik seperti SMOTE atau undersampling untuk memastikan model tidak bias terhadap kelas mayoritas.

---------------------------------------------------------------------------------------------------------------------
## Business Understanding

Pada bagian ini, kamu perlu menjelaskan proses klarifikasi masalah.

Bagian laporan ini mencakup:

### Problem Statements

Menjelaskan pernyataan masalah latar belakang:
- Pernyataan Masalah 1
- Pernyataan Masalah 2
- Pernyataan Masalah n

### Goals

Menjelaskan tujuan dari pernyataan masalah:
- Jawaban pernyataan masalah 1
- Jawaban pernyataan masalah 2
- Jawaban pernyataan masalah n

Semua poin di atas harus diuraikan dengan jelas. Anda bebas menuliskan berapa pernyataan masalah dan juga goals yang diinginkan.

**Rubrik/Kriteria Tambahan (Opsional)**:
- Menambahkan bagian “Solution Statement” yang menguraikan cara untuk meraih goals. Bagian ini dibuat dengan ketentuan sebagai berikut: 

    ### Solution statements
    - Mengajukan 2 atau lebih solution statement. Misalnya, menggunakan dua atau lebih algoritma untuk mencapai solusi yang diinginkan atau melakukan improvement pada baseline model dengan hyperparameter tuning.
    - Solusi yang diberikan harus dapat terukur dengan metrik evaluasi.

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

**---Ini adalah bagian akhir laporan---**

_Catatan:_
- _Anda dapat menambahkan gambar, kode, atau tabel ke dalam laporan jika diperlukan. Temukan caranya pada contoh dokumen markdown di situs editor [Dillinger](https://dillinger.io/), [Github Guides: Mastering markdown](https://guides.github.com/features/mastering-markdown/), atau sumber lain di internet. Semangat!_
- Jika terdapat penjelasan yang harus menyertakan code snippet, tuliskan dengan sewajarnya. Tidak perlu menuliskan keseluruhan kode project, cukup bagian yang ingin dijelaskan saja.
