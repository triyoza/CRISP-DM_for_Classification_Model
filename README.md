## Menggunakan Metodologi CRISP-DM untuk Model Klasifikasi Memprediksi Buyer Rating di Suatu Marketplace
## Sebuah Final Project di Sharing Vision Data Science Bootcamp
## Pendahuluan
CRISP DM (The CRoss Industry Standard Process for Data Mining):
- Bussinees Understanding
- Data Understanding
- Data Preparation
- Feature Engineering
- Modeling
- Evaluasi
- Deployment (Pada project ini hanya sampai tahapn evaluasi)
## Bussiness Understanding
Terbagi menjadi tiga yang mana telah ditentukan oleh instructor:
- Bussiness Objectives: Suatu perusahaan marketplace ingin membuat guideline berisi tips untuk seller bagaimana agar mendapatkan rating 5 dari buyer
- Model Objectives: Membuat mesin klasifikasi untuk menentukan apakah buyer memberikan rating 5 terhadap barang yang dibeli (label 1) atau rating di bawah 5 (label 0)
- Model Succes Kriteria  (Recall> 0.6; Precision > 0.6; FPR < 0.45), Model yang dibuat mencapai atau bahkan melebihi model success criteria. Apabila tidak berhasil, pilih model dengan performace terbaik
## Data Understanding
### Data Description
Data yang digunakan:
- 'model_development_set.csv', digunakan untuk pembuatan model
- 'back_testing_set.csv', digunakan untuk menguji model yang dibuat dan memprediksi kolom 'label' (buyer rating) karena pada back_testing_set ini kolom 'label' disembunyikan oleh instruktor
- Data 'model_development_set.csv' terdiri dari 13645 baris dan 40 kolom atau fitur dengan tipe data numerik, kategorik, dan datetime
- Fitur Numerik
gambar
- Fitur Kategorik 
gambar
-Fitur Datetime
gambar
## Exploraatory Data Analysis (EDA)
### Fitur Numerik
#### Univariat Numerik
#### Multivariat Numerik
#### Numerik-Label
### Fitur kategorik
