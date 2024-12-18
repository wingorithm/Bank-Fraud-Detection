# Analisis Transaksi Fraud Perbankan - Erwin Gunawan

## Domain Proyek (Keuangan, Ekonomi, dan Bisnis)
_Fraud Detection_ (deteksi penipuan) dalam transaksi keuangan telah menjadi hal yang krusial bagi bank dan lembaga keuangan di seluruh dunia. Seiring berkembangnya transaksi digital karena kemajuan teknologi yang pesat, aktivitas penipuan juga meningkat sama pesatnya dan menyebabkan kerugian finansial yang merusak kepercayaan konsumen. Association of Certified Fraud Examiners (ACFE) melaporkan, organisasi setidaknya kehilangan sekitar 5% dari annual revenue karena penipuan, yang berarti miliaran dolar secara global setiap tahun [[1]](https://legacy.acfe.com/report-to-the-nations/2020/). Data ini menggarisbawahi adanya urgensi untuk memiliki mekanisme _fraud detection_ yang efektif. Laporan oleh Komisi Perdagangan Federal (FTC) juga mengungkapkan peningkatan 70% dalam kasus pencurian identitas yang dilaporkan dalam beberapa tahun terakhir, menekankan perlunya strategi pencegahan penipuan yang kuat [[3]](https://www.ftc.gov/system/files/ftc_gov/pdf/CSN%20Annual%20Data%20Book%202021%20Final%20PDF.pdf). Melihat perkembangan digital dan finansial di Indonesia, sekarang Indonesia menempati peringkat 56 dari 63 negara dalam hal digital literacy (survei dari World Digital Competitiveness Index oleh Institute Management Development) [[4]](https://indonesiabaik.id/videografis/indonesia-makin-melek-literasi-digital). Selama beberapa tahun terakhir, Indonesia juga telah mengalami peningkatan yang signifikan dalam adopsi layanan perbankan digital. Penggunaan channel ini tiap bulannya tumbuh 2 kali lipat dari negara berkembang di Asia lainnya. Hingga tahun 2023, 58% konsumen Indonesia memanfaatkan layanan perbankan digital, peningkatan yang signifikan dari tahun-tahun sebelumnya menurut laporan dari McKinsey [[5]](https://www.mckinsey.com/industries/financial-services/our-insights/digital-banking-in-indonesia-building-loyalty-and-generating-growth).

![Fraud Detection In Banking](https://artificialpaintings.com/wp-content/uploads/2024/06/632_AI_fraud_detection_in_banking.webp "Fraud Detection In Banking")

_Machine learning_ (ML) muncul sebagai alat yang penting dan efektif dalam memerangi fraud, menawarkan teknik canggih untuk menganalisis data transaksi dalam jumlah besar serta mengidentifikasi pola anomali (anomaly pattern) yang mungkin menunjukkan perilaku fraud. Hal ini dibuktikan dengan performa model seperti _Random Forest_ dan _Support Vector Machines_ yang secara signifikan mengungguli metode statistik tradisional dalam efektivitas mendeteksi penipuan kartu kredit [[2]](https://www.researchgate.net/publication/383699937_Financial_fraud_detection_through_the_application_of_machine_learning_techniques_a_literature_review). Kemampuan _machine learning_ untuk belajar dari data historis dan beradaptasi dengan pola baru membuatnya sangat cocok untuk lingkungan yang dinamis seperti transaksi keuangan. Selain itu, semakin canggihnya skema penipuan memerlukan peningkatan berkelanjutan dalam metodologi deteksi. Karena lembaga keuangan berusaha untuk melindungi aset mereka dan menjaga kepercayaan pelanggan, memanfaatkan _machine learning_ untuk analisis prediktif (predictive analysis) dalam _fraud detection_ tidak hanya bermanfaat tetapi juga penting.

Dari kondisi pertumbuhan finansial di sektor digital di Indonesia, rendahnya literasi digital, dan pesatnya pertumbuhan skema fraud, integrasi _machine learning_ menjadi semakin penting. _Machine learning_ untuk proses _fraud detection_ merupakan pendekatan yang proaktif dan solusi inovatif untuk memerangi penipuan secara efektif.

## Business Understanding
### Problem Statements
Berdasarkan latar belakang yang telah dijelaskan, maka permasalahan yang ingin diselesaikan dalam proyek ini meliputi:
1. Bagaimana cara mempersiapkan dataset transaksi perbankan agar siap digunakan untuk membangun model _machine learning_?
2. Bagaimana cara membangun model _machine learning_ yang efektif untuk mendeteksi kecurangan dalam transaksi perbankan?
3. Apa saja metrik evaluasi yang tepat untuk menilai performa model dalam mendeteksi fraud?

### Goals
Berdasarkan rumusan masalah yang telah dipaparkan di atas, tujuan utama proyek ini adalah:
1. Melakukan proses data preparation yang mencakup pembersihan, transformasi, dan eksplorasi dataset (EDA) untuk memastikan data siap digunakan dalam pembuatan model.
2. Membuat model clustering _machine learning_ yang mampu mendeteksi potensi transaksi yang mencurigakan secara akurat.
3. Menggunakan metrik evaluasi seperti Silhouette Score, membandingkan prediksi antar model, serta membuat threat map dari prediksi-prediksi model.

### Solution Statements
1. Melakukan *data preparation*:
   - Melakukan data cleaning yang meliputi: memastikan NaN values, missing values, dan duplicate rows.
   - Melakukan Feature Selection dan standarisasi nilai pada data fitur numerik untuk mencegah terjadinya penyimpangan nilai data yang cukup besar.
2. Tahap pembuatan model clustering *_machine learning_* akan digunakan 3 model dengan algoritma *_machine learning_* yang berbeda. Algoritma yang akan digunakan adalah _K-means Clustering_, _DBSCAN Clustering_, _Isolation Forest Clustering_. Dari ketiga model tersebut akan dilakukan evaluasi performa dan kinerja masing-masing algoritma dan akan dikombinasikan untuk mendapatkan hasil fraud prediction yang baik.

## Data Understanding
![image](https://github.com/user-attachments/assets/efeac73c-3571-4e0d-be85-cbc6e7c4174c "Bank Transaction Dataset for Fraud Detection")

[Dataset ini](https://www.kaggle.com/datasets/valakhorasani/bank-transaction-dataset-for-fraud-detection) memberikan gambaran rinci tentang perilaku transaksi dan pola aktivitas keuangan, yang sangat cocok untuk eksplorasi deteksi penipuan dan identifikasi anomali. Terdiri dari 2.512 sampel data transaksi:

![image](https://github.com/user-attachments/assets/7d0b41b1-3a5f-4d41-a8bf-c670046d0902)

Berikut penjelasan setiap fitur pada gambar diatas:
- TransactionID: Identifikasi unik untuk setiap transaksi.
- AccountID: ID unik untuk setiap akun, dengan beberapa transaksi per akun.
- TransactionAmount: Nilai nominal transaksi, mencakup pengeluaran harian kecil hingga pembelian besar.
- TransactionDate: Tanggal dan waktu pelaksanaan transaksi.
- TransactionType: Jenis transaksi, berupa kategori 'Credit' atau 'Debit'.
- Location: Lokasi geografis transaksi, direpresentasikan dengan nama kota di AS.
- DeviceID: Identifikasi perangkat yang digunakan untuk melakukan transaksi.
- IP Address: Alamat IPv4 terkait transaksi, dengan kemungkinan perubahan pada beberapa akun.
- MerchantID: Identifikasi unik untuk merchant, menunjukkan merchant favorit dan merchant yang jarang digunakan oleh pelanggan.
- AccountBalance: Saldo akun setelah transaksi, sesuai dengan jenis dan jumlah transaksi.
- PreviousTransactionDate: Tanggal transaksi terakhir pada akun tersebut, berguna untuk menghitung frekuensi transaksi.
- Channel: Saluran transaksi seperti Online, ATM, atau Cabang.
- CustomerAge: Usia pemegang akun, dengan pengelompokan berdasarkan pekerjaan.
- CustomerOccupation: Pekerjaan pemegang akun (misalnya Dokter, Insinyur, Mahasiswa, Pensiunan), yang mencerminkan pola pendapatan.
- TransactionDuration: Durasi transaksi dalam detik, bervariasi berdasarkan jenis transaksi.
- LoginAttempts: Jumlah percobaan login sebelum transaksi, dengan angka yang lebih tinggi dapat menunjukkan potensi anomali.


Setelah memahami dataset kemudian dataset transaksi yang terdiri dari 16 fitur perlu evaluasi awal untuk mengidentifikasi masalah data yang dapat memengaruhi hasil analisis, sebelum melanjutkan ke tahap data preparation.

```python
# Check for duplicate rows
duplicates = df.duplicated().sum()

# Check for missing values
missing_values = df.isnull().sum().sum()

# Check for NaN values
nan_values = df.isna().sum().sum()

if duplicates == 0 and missing_values == 0 and nan_values == 0:
    print("The data is clean.")
else:
    print("The data has issues:")
    if duplicates > 0:
        print(f"There are {duplicates} duplicate rows.")
    if missing_values > 0:
        print(f"There are {missing_values} missing values.")
    if nan_values > 0:
        print(f"There are {nan_values} NaN values.")
```
1. Pengecekan Duplikasi
Dataset diperiksa untuk keberadaan baris duplikat menggunakan metode `.duplicated()`.

Hasil: Dataset tidak memiliki {duplicates} baris duplikat, yang dapat memengaruhi kualitas model jika tidak ditangani.

2. Pengecekan Missing Values
Dataset diperiksa untuk nilai yang hilang (missing values) menggunakan fungsi `.isnull().sum()`.

Hasil: Tidak terdapat {missing_values} missing values di dataset.

3. Pengecekan NaN Values
Dataset juga diperiksa untuk keberadaan nilai NaN menggunakan fungsi `.isna().sum()`.

Hasil: Tidak terdapat {nan_values} nilai NaN di dataset.


Selain memahami deskripsi setiap fiturnya, *Exploratory Data Analysis* (EDA) sebagai investigasi awal untuk menganalisis karakteristik, menemukan pola, anomali, dan memeriksa asumsi pada data dengan menggunakan teknik statistik dan representasi grafis atau visualisasi juga dilakukan.

1. **Univariate Analysis**
![image](https://github.com/user-attachments/assets/98a770c2-f23d-4fa6-a991-ab34b64e4eec)
![image](https://github.com/user-attachments/assets/af30f1b6-3611-4046-ac9c-de6f289eabc9)

Dari analisis data univariat, diperoleh beberapa informasi berikut:
- Mayoritas transaksi adalah debit (77,39%), sedangkan transaksi credit hanya sebesar 22,61%.
- Nilai transaksi cenderung condong ke jumlah kecil, dengan transaksi debit mendominasi di semua rentang, sementara transaksi credit lebih banyak pada nilai yang lebih besar.
- Konsentrasi transaksi tinggi di kota seperti Fort Worth, Oklahoma, dan Los Angeles, dengan penurunan bertahap di lokasi lainnya.
- Transaksi terbagi hampir merata antara Branch (34,55%), ATM (33,16%), dan Online (32,29%).
- Puncak jumlah transaksi terjadi pada kelompok usia 20–30 tahun dan 40–50 tahun, dengan penurunan pada kelompok usia 30–40 tahun dan usia yang lebih tua.
- Pembagian yang cukup merata di antara kelompok mahasiswa (26,15%), dokter (25,12%), insinyur (24,88%), dan pensiunan (23,85%).

2. **Multivariate Analysis**
![image](https://github.com/user-attachments/assets/93e82170-05a7-43d6-ac14-d335d61b3556)
![image](https://github.com/user-attachments/assets/b33a7b77-70e2-45f6-9b49-f7d8a02af165)

Heatmap korelasi (_Correlation Matrix_) memberikan beberapa wawasan penting:
- Customer Age memiliki korelasi positif sedang (0,32) dengan `Account Balance`, menunjukkan bahwa pelanggan yang lebih tua cenderung memiliki saldo akun yang lebih tinggi.
- Sebagian besar fitur memiliki korelasi positif yang lemah satu sama lain, yang mengindikasikan bahwa fitur-fitur tersebut kemungkinan terkait dengan proses transaksi.

## Data Preparation
Sebelum membangun model clustering, dilakukan beberapa langkah persiapan data untuk memastikan kualitas data dan kompatibilitas dengan algoritma clustering. Berikut adalah proses dan hasil dari tahap data preparation berdasarkan kode yang digunakan:

```python

df.drop(columns=['TransactionID', 'AccountID', 'TransactionDate', 'TransactionType', 'Location', 'DeviceID', 'MerchantID', 'PreviousTransactionDate', 'Channel', 'IP Address', 'CustomerOccupation'])

features = ['TransactionAmount', 'CustomerAge']
X = df[features]

scaler = StandardScaler()
X_scaled = scaler.fit_transform(X)
```

1. Pemilihan Fitur (Feature Selection)
Pertama perlunya menghapus kolom yang tidak relevan seperti `TransactionID`, `DeviceID`, atau `IP Address`, kolom Non-Numeric seperti `CustomerOccupation`, `AccountID`, and `Channel`, serta kolom yang sefatnya hanya identifier unique `TransactionID`, `AccountID`, `DeviceID`, and `MerchantID`.

Selanjutnya menentukan fitur yang relevan untuk analisis clustering dipilih:
`TransactionAmount`: Nilai transaksi memberikan wawasan tentang perilaku finansial pelanggan.
`CustomerAge`: Usia pelanggan dapat mencerminkan pola dan kebutuhan transaksi yang berbeda.

2. Normalisasi Data
Untuk memastikan skala data seragam, fitur yang dipilih dinormalisasi menggunakan StandardScaler:
`TransactionAmount` dan `CustomerAge` diubah menjadi data dengan distribusi standar (mean = 0, standard deviation = 1).
Langkah ini penting karena algoritma clustering sensitif terhadap skala fitur.

3. Hasil Transformasi
Fitur yang dipilih, yaitu TransactionAmount dan CustomerAge, memiliki skala yang berbeda. Oleh karena itu, normalisasi dilakukan menggunakan _StandardScaler_ untuk mengubah data menjadi distribusi standar (mean = 0, standard deviation = 1). Langkah ini penting untuk mencegah algoritma clustering menjadi bias terhadap fitur dengan skala besar.
Kemudian Data yang telah dinormalisasi disimpan dalam variabel X_scaled dan akan digunakan sebagai input untuk membangun model clustering.
Dengan data yang sudah diproses, langkah berikutnya adalah membangun dan mengevaluasi model clustering menggunakan tiga algoritma berbeda.

## Modeling
Pada tahap ini, digunakan tiga algoritma clustering untuk mendeteksi potensi fraud dalam data transaksi. Setiap algoritma digunakan untuk menganalisis pola dalam data yang telah dinormalisasi dan memberikan label cluster yang sesuai. Semua hasil prediksi digabungkan untuk membangun threat map, yang menjadi hasil akhir dari analisis.

1. K-Means Clustering

![image](https://github.com/user-attachments/assets/d22ee8c4-5c2c-460d-83b9-08d96ccc2281)

Tahapan:
- Data dikelompokkan menjadi 3 cluster menggunakan metode _K-Means_.
- Setiap titik data diklasifikasikan ke cluster terdekat berdasarkan jarak euclidean dari centroid.
- Potensi fraud ditentukan berdasarkan 5% data terjauh dari centroid, menggunakan nilai threshold jarak.
- Visualisasi dilakukan untuk melihat distribusi cluster dan titik yang diindikasikan sebagai potensi fraud.

Parameter yang Digunakan:
- `n_clusters=3`: Menentukan jumlah cluster.
- `n_init=10`: Algoritma dijalankan 10 kali untuk menghindari local minima.
- `max_iter=300`: Batas maksimum iterasi.

Model ini sangat sederhana dan cepat untuk dataset berukuran sedang. Namun sensitif terhadap outlier, dan memerlukan definisi jumlah cluster sebelumnya (n_clusters).

2. DBSCAN (Density-Based Spatial Clustering of Applications with Noise)

![image](https://github.com/user-attachments/assets/c5f59593-a11b-49c3-9eb8-98a1240a7da0)

Tahapan:
- Algoritma ini mengidentifikasi area dengan densitas tinggi sebagai cluster, sementara titik di luar area tersebut dianggap noise.
- Parameter `eps` dan `min_samples` diatur secara manual untuk menghasilkan Silhouette Score terbaik.
- Data diindikasikan sebagai:
Potential Fraud (label -1). Normal atau kelompok mencurigakan lainnya.

Parameter yang Digunakan:
- `eps=0.3`: Radius maksimum dari neighborhood.
- `min_samples=8`: Minimum jumlah titik untuk membentuk cluster.

Model ini tidak memerlukan jumlah cluster (n_clusters) pada inisiasi. Serta dapat menangani data dengan noise dan bentuk cluster yang tidak beraturan. Namun model ini juga sensitif terhadap pemilihan parameter eps dan min_samples.

3. Isolation Forest

![image](https://github.com/user-attachments/assets/e747f50c-65e9-459f-bfc2-2a48ccbd0a06)

Tahapan:
- Algoritma mendeteksi outlier dengan membangun pohon keputusan yang memisahkan titik data.
- Data ditandai sebagai:
Potential Fraud (-1).
Normal (1).

Parameter yang Digunakan:
- `contamination=0.01`: Persentase data yang diindikasikan sebagai outlier.
- `random_state=42`: Untuk hasil yang konsisten.

Model ini dirancang khusus untuk deteksi anomali, dan tidak memerlukan data label. Menjadikannya cocok untuk skenario dan dataset ini. Namun Model ini kurang efektif untuk dataset kecil atau sangat tidak seimbang.

## **Evaluation**

Pada tahap evaluasi, kami menggunakan metrik **Silhouette Score**, hasil prediksi dari masing-masing model, dan visualisasi berupa **Threat Level Chart** untuk menilai kinerja model unsupervised learning dalam mendeteksi potensi fraud pada data transaksi. Berikut adalah detail metrik evaluasi dan hasilnya:

### **1. Silhouette Score**
- **Definisi**:  
  Silhouette Score mengukur seberapa baik data dalam cluster tertentu dikelompokkan. Nilai berkisar antara **-1 hingga 1**:
  - Nilai mendekati **1**: Data terkelompok dengan baik.
  - Nilai mendekati **0**: Data berada di batas antara cluster.
  - Nilai negatif: Data mungkin salah dikelompokkan.  

- **Formula**:  
   $$S=\frac{b-a}{\max(a, b)}$$

  Di mana:  
  - \(a\): Jarak rata-rata antara suatu titik dan semua titik lain dalam cluster yang sama.  
  - \(b\): Jarak rata-rata antara suatu titik dan semua titik dalam cluster terdekat lainnya.  

- **Hasil & Dampaknya** terhadap Goals dan Solusi:  
  - **K-Means**:  
    - Silhouette Score: **{kmeans_silhouette}** = 0.46962506821788885
    
    Hasil menunjukkan bahwa model cukup mampu membedakan transaksi mencurigakan dari yang normal, meskipun tidak ideal untuk semua cluster. Ini relevan dengan tujuan mendeteksi transaksi mencurigakan secara tersegmentasi.
      
  - **DBSCAN**:  
    - Silhouette Score: **{DBSCAN_silhouette}** = 0.5437089419372249  
    
    DBSCAN memberikan hasil lebih baik dibandingkan K-Means, terutama dalam mendeteksi kelompok kecil transaksi (outlier) yang sering dikaitkan dengan fraud.

  - **Isolation Forest**:
    
    Tidak menggunakan Silhouette Score, namun fokus pada identifikasi outlier berdasarkan isolasi data.

### **2. Hasil Prediksi Model**
![image](https://github.com/user-attachments/assets/1d736420-0990-4a06-b257-05d462f15712)
![image](https://github.com/user-attachments/assets/ba54a134-3c4d-4e03-8668-36bc6c52f08d)

Kembali pada problem statement, Salah satu permasalahan utama dalam kasus ini adalah bagaimana _fraud detection_ dalam transaksi perbankan dapat dilaksanakan. Berdasarkan hasil diatas, dengan memanfaatkan tiga algoritma clustering, setiap model memberikan jumlah prediksi transaksi mencurigakan yang berbeda, memungkinkan analisis risiko yang lebih komperhensif. Hasil ini bisa menjadi bahan pertimbangan tim risiko untuk menilai suatu transaksi.

- **K-Means Clustering**:  
  - **Jumlah transaksi potensial fraud**: 5.02% dari total transaksi).
    Angka ini memberikan cakupan yang luas untuk investigasi, namun mungkin menyebabkan tim risiko menangani banyak kasus yang tidak relevan (false positives).

- **DBSCAN**:  
  - **Jumlah transaksi potensial fraud**: 2.35% dari total transaksi).
    Dari angka ini DBSCAN lebih selektif dan berhasil mengelompokkan transaksi outlier dengan lebih presisi, memberikan daftar prioritas untuk investigasi.

- **Isolation Forest**:  
  - **Jumlah transaksi potensial fraud**: 1.04% dari total transaksi).
    Angka ini membantu mengurangi beban investigasi karena lebih fokus pada kasus yang sangat mencurigakan, meskipun dapat meningkatkan risiko melewatkan beberapa kasus (false negatives).
 
Alhasil Ketiga model memberikan perspektif berbeda dalam _fraud detection_. _DBSCAN_ dan _Isolation Forest_ lebih relevan untuk prioritas bisnis karena mampu memberikan daftar transaksi yang lebih terfokus, sesuai dengan kebutuhan efisiensi tim risiko.

### **3. Visualisasi: Threat Level Chart**
![image](https://github.com/user-attachments/assets/9297a790-05ca-4005-9e2c-5e33f9fb674e)

Heatmap menampilkan 20 transaksi dengan tingkat ancaman tertinggi (**Threat Level**) berdasarkan kombinasi hasil dari ketiga model (_K-Means, DBSCAN, Isolation Forest_). Warna dalam heatmap menunjukkan tingkat ancaman, di mana warna yang lebih terang menunjukkan ancaman yang lebih tinggi. Heatmap ini membantu mengidentifikasi transaksi yang memerlukan investigasi lebih lanjut, memberikan pandangan yang jelas kepada tim risiko.

### **Kesimpulan**

Dari evaluasi yang dilakukan, ditemukan bahwa:
- Hasil evaluasi model menunjukkan bahwa pendekatan clustering dapat digunakan untuk mendeteksi transaksi mencurigakan. _Silhouette Score_, jumlah transaksi _fraud_, dan _threat level chart_ memberikan dasar yang kuat untuk mendukung pemahaman bisnis dan mitigasi risiko. Yang mana hal ini menjawab problem statement dala penelitian ini.
- Dalam penelitian ini data telah diproses dan disiapkan dengan baik melalui langkah-langkah seperti standarisasi dan seleksi fitur. Model clustering berhasil mengidentifikasi transaksi mencurigakan dengan tingkat akurasi yang berbeda-beda, memberikan pilihan yang fleksibel untuk bisnis. Serta visualisasi _threat level chart_ memberikan informasi yang dapat diimplementasikan langsung oleh tim risiko.
- Dari penelitian ini dapat dilihat bahwa pendekatan _machine learning_ dalam hal model clustering berdampak untuk memberikan solusi yang langsung dapat digunakan untuk meningkatkan efisiensi investigasi risiko. 
     
Evaluasi ini tidak hanya menunjukkan performa teknis tetapi juga relevansi model dengan kebutuhan bisnis, menjawab pertanyaan inti, dan memberikan dampak langsung pada mitigasi risiko transaksi khususnya _fraud transaction_ perbankan.

## Reference
[1] Association of Certified Fraud Examiners (ACFE). (2020). Report to the Nations: Global Study on Occupational Fraud and Abuse.

[2] Zhang, Y., Wang, S., & Chen, X. (2019). Behavioral analytics for _fraud detection_: A review. IEEE Access, 7, 11212-11223.

[3] Federal Trade Commission (FTC). (2021). Consumer Sentinel Network Data Book.

[4] Indonesia digital literacy -> https://indonesiabaik.id/videografis/indonesia-makin-melek-literasi-digital

[5] Digital banking in indonesia -> https://www.mckinsey.com/industries/financial-services/our-insights/digital-banking-in-indonesia-building-loyalty-and-generating-growth
