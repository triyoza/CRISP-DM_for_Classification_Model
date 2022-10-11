## Menggunakan Metodologi CRISP-DM untuk Model Klasifikasi Memprediksi Buyer Rating di Suatu Marketplace
### Sebuah Final Project di Sharing Vision Data Science Bootcamp
#### Instruksi
Gunakan metodologi CRISP DM: business understanding, data understanding, data preparation, feature engineering, modeling, evaluasi, deployment untuk masalah klasifikasi memprediksi kolom 'label' pada dataset
### Pendahuluan
CRISP DM (The CRoss Industry StandardProcess for Data Mining), terdiri dari beberapa tahapan:
- Bussinees Understanding
- Data Understanding
- Data Preparation
- Feature Engineering
- Modeling
- Evaluasi
- Deployment (Pada project ini hanya sampai tahapn evaluasi)
### Bussines Understanding
#### - Bussiness Objectives
Suatu perusahaan marketplace ingin membuat guideline berisi tips untuk seller bagaimana agar mendapatkan rating 5 dari buyer
#### - Model Objectives
Membuat mesin klasifikasi untuk menentukan apakah buyer memberikan rating 5 terhadap barang yang dibeli (label 1) atau rating di bawah 5 (label 0)
#### - Model Succes Kriteria
Recall > 0.6; Precision > 0.6; FPR < 0.45
Model yang dibuat mencapai atau bahkan melebihi model success criteria. Apabila tidak berhasil, pilih model dengan performace terbaik
