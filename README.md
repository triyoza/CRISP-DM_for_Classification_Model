## Menggunakan Metodologi CRISP-DM untuk Model Klasifikasi Memprediksi Buyer Rating di Suatu Marketplace
- Sebuah Final Project di Sharing Vision Data Science Bootcamp
- Ditulis oleh: Triyoza Aprianda
- Lebih lengkap silahkan membuka file ipynb yang dilampirkan:)
## Pendahuluan
CRISP-DM (The CRoss Industry Standard Process for Data Mining):
- Business Understanding
- Data Understanding
- Data Preparation
- Feature Engineering
- Modeling
- Evaluasi
- Deployment (Pada project ini hanya sampai tahapan evaluasi)
## Business Understanding
Terbagi menjadi tiga yang telah ditentukan oleh instruktor:
- Bussiness Objectives: Suatu perusahaan marketplace ingin membuat guideline berisi tips untuk seller bagaimana agar mendapatkan rating 5 dari buyer
- Model Objectives: Membuat mesin klasifikasi untuk menentukan apakah buyer memberikan rating 5 terhadap barang yang dibeli (label 1) atau rating di bawah 5 (label 0)
- Model Succes Kriteria  (Recall> 0.6; Precision > 0.6; FPR < 0.45), Model yang dibuat mencapai atau bahkan melebihi model success criteria. Apabila tidak berhasil, pilih model dengan performace terbaik

## Data Understanding
### Data Description
Data yang digunakan:
- 'model_development_set.csv', digunakan untuk pembuatan model
- 'back_testing_set.csv', digunakan untuk menguji model yang dibuat dan memprediksi kolom 'label' (buyer rating) karena pada back_testing_set ini kolom 'label' disembunyikan oleh instruktor
- Data 'model_development_set.csv' terdiri dari 13645 baris dan 40 kolom atau fitur dengan tipe data numerik, kategorik, dan datetime
#### Fitur Numerik

![numerik](https://user-images.githubusercontent.com/113491625/195153492-871d6ef0-326c-4fcb-96f8-1cbcb74b550d.PNG)
#### Fitur Kategorik

![newww](https://user-images.githubusercontent.com/113491625/195238075-a17ac0b1-5a93-45e0-ab81-f3824dc27b1b.PNG)

#### Fitur Datetime

![dtime beru](https://user-images.githubusercontent.com/113491625/195235458-85223345-b70c-48e9-bb94-72f487c1d8db.PNG)

## Exploratory Data Analysis (EDA)
### Fitur Numerik
#### Multivariat Numerik
Salah satu regplot dengan korelasi tinggi

![regplot](https://user-images.githubusercontent.com/113491625/195235492-94246ed8-5985-4cc2-a4cd-446b645a7fb0.PNG)

#### Numerik-Label

![kkkk](https://user-images.githubusercontent.com/113491625/195237690-813f5d64-9ad9-494a-9c61-8d253bd01d35.PNG)

- Dari plot yang dihasilkan, pada umumnya di setiap fitur numerik memiliki rata-rata nilai yang lebih tinggi pada label 0 (rating di bawah 5)
- Namun untuk fitur 'price' dan 'description length' yang ditampilkan berlaku sebaliknya, memiliki rata-rata nilai yang lebihtinggi pada label 1 (buyer memberi rating 5)

### Fitur kategorik
Countplot dan stacked barplot 

![count and stacked](https://user-images.githubusercontent.com/113491625/195235503-e58eb066-b03c-404f-b1be-24d8c72cbd4c.PNG)

Dari beberapa barplot dan stacked barplot yang ditampilkan dapat dilihat bahwa untuk setiap fitur kategorik, label 1 atau pemberian rating 5 lebih unggul untuk masing-masing kategori yang ada dalam fitur

### Fitur Datetime
Dari fitur datetime dapat diidentifikasi lama waktu pemrosesan pesanan dengan cara mengidentifikasi selisih antar fitur datetime, sehingga dapat dibuat kolom barupa lama waktu yang dibutuhkan, sebagai berikut:

![dtmiee](https://user-images.githubusercontent.com/113491625/195238570-25838d02-5db7-4052-ba26-e6fee0be7659.PNG)

- Beberapa hasil plot berupa jointplot

![jointploat](https://user-images.githubusercontent.com/113491625/195235477-56bee122-c5c7-4fe0-b276-e2d935fa2244.PNG)

- Titik-titk berwarna biru pada plot lebih banyak terdapat jauh dari sumbu 0 yang menandakan pemberian rating di bawah 5 (label 0). Hal ini menunjukkan semakin lama waktu yang dibutuhkan rating dominan yang diberikan oleh buyer dibawah 5.
- Titik-titk berwarna orange pada plot lebih banyak terkumpul di dekat sumbu 0 yang menandakan pemberian rating di atas 5 (label 1). Menunjukkan bahwa semakin cepat waktu yang dibutuhka rating yang diberikan oleh buyer pada umumnya di bawah 5

### Insight dari EDA
- Pada fitur numerik untuk 'price' dan 'description length' cukup unik karena rata-rata untuk nilai fitur tersebut lebih tinggi pada pemberian rating 5 daripada dibawah 5, berbeda dengan fitur numerik lain yang berlaku sebaliknya
- Pada fitur kategorik, di setiap kategori dalam yang terdapat dalam fitur lebih banyak pemberian dengan rating 5 daripada di bawah 5, namun kurang dapat dijelaskan hubungannya
- Dari ketiga tipe data, yang paling berpengaruh terhadap pemberian rating terdapat pada fitur datetime yaitu lama waktu yang dibutuhkan dalam proses pesanan. Dimana semakin lama waktu tahapan pemrosesan, maka rating yang diberikan oleh buyer lebih dominan di bawah 5

## Data Preparation dan fitur Engineering
### Train Test Split
- Drop fitur yang tidak diperlukan
- Lakukakan train test split:

![tts](https://user-images.githubusercontent.com/113491625/195228237-275526fa-4b0d-41d4-afda-7cb2700f8fdf.PNG)

### Missing Value Handling
Persentase missing value tiap fitur

![mv](https://user-images.githubusercontent.com/113491625/195228246-6b00a3b1-cfc1-47cf-bdcc-ae95a04569f7.PNG)

Handling:
- Simple imputer (strategy = median) untuk fitur numerik
- Simple imputer (strategy = most_frequent ) untuk fitur kategorik

### Transformasi
- Scaling untuk fitur numerik
- One hot encoder untuk fitur kategorik

### Feature Selection
- Multicolinearity Reduction
- Mutual Information

### Testing Set
Melakukan semua tahapan: Missing value handling, transformasi, dan feature selection ke testing set seperti yang dilakuakan pada train set tanpa fit ulang

## Modeling
- Menentukan model
- Tuning Hyperparameter menggunakan GridSearchCV
- Mendapatkan parameter terbaik
- Fitting ke training set
- Periksa performanasi (train dan test)
- Dilakukan hingga menemukan model yang sesuai kriteria atau performance terbaik

### Model klasifikasi final
- Model klasifikasi yang dibuat yaitu: Logistic Regression, Decision Tree, Random Forest, Ada boost, dan XGBoost
- Dipilih XGboost karena memiliki performance yang terbaik
- Hyperparameter

![hyp](https://user-images.githubusercontent.com/113491625/195229327-a7bebee6-87d5-493c-916a-e345ee107c26.PNG)

- Perfoemance XGBoost final

![perfromance](https://user-images.githubusercontent.com/113491625/195229397-73b55262-32ce-4b4e-988d-7ddb958ade80.PNG)

Karena telah melebihi model succes criteria yang ditentukan di awal, maka model XGboost final digunakan untuk memprediksi kolom label pada 'backtesting_set'

## Evaluasi
- Menggunakan data'back_testing_set.csv yang sudah ditransformasi dan diseleksi mengikuti apa yang dilakukan kepada training set
- Didapatkan kolom prediksi label yang berisi 0 dan 1 ( 0: buyer memberi rating di bawah 5, 1: buyer memberi rating 5), kemudian dijadikan kolom sendiri dan diextract ke file csv

![eval](https://user-images.githubusercontent.com/113491625/195231539-c4a1a7ad-c223-441d-97e4-8daeb584f2cf.PNG)

### Penutup
- Setelah disubmit, instruktor membandingkan kolom label yang diperoleh dengan kolom label asli yang disembunyikan
- Didapatkan performansi untuk back testing set dari model yang saya buat yaitu: 
Recall 0.68,
Precision 0.68,
FPR 0.45

# ![WhatsApp Image 2022-10-12 at 08 56 53](https://user-images.githubusercontent.com/113491625/195231126-4d58b3a0-c050-4bf4-bbd2-bb0620962ad9.jpeg)

Terima kasih
