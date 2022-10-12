## Menggunakan Metodologi CRISP-DM untuk Model Klasifikasi Memprediksi Buyer Rating di Suatu Marketplace
- Sebuah Final Project di Sharing Vision Data Science Bootcamp
- Ditulis oleh: Triyoza Aprianda
- Lebih lengkap silahkan buka file ipynb dan pdf:)
## Pendahuluan
CRISP-DM (The CRoss Industry Standard Process for Data Mining):
- Bussinees Understanding
- Data Understanding
- Data Preparation
- Feature Engineering
- Modeling
- Evaluasi
- Deployment (Pada project ini hanya sampai tahapan evaluasi)
## Bussiness Understanding
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

![kategorik](https://user-images.githubusercontent.com/113491625/195223820-076f3174-cb15-431f-af49-d9548334d3ca.PNG)
### Fitur Datetime

![datetime](https://user-images.githubusercontent.com/113491625/195223888-0bcaf27b-868a-4840-ac05-a2fd01fc8367.PNG)
## Exploratory Data Analysis (EDA)
### Fitur Numerik
#### Multivariat Numerik
Salah satu hasil plot dengan korelasi tinggi

![numriknumerik](https://user-images.githubusercontent.com/113491625/195224394-ffb706e0-04c5-4b4a-b44f-ef7ee3e82c06.PNG)
#### Numerik-Label
![numerik label](https://user-images.githubusercontent.com/113491625/195224483-19494df0-783f-444d-bd63-103faea26c24.PNG)
- Dari plot yang dihasilkan, pada umumnya di setiap fitur numerik memiliki rata- rata nilai yang lebih tinggi pada label 0 (rating di bawah 5)
- Namun untuk fitur 'price' dan 'description length' yang ditampilkan berlaku sebaliknya,memiliki rata- rata nilai yang lebihtinggi pada label 1 (buyer memberirating 5)
### Fitur kategorik
Counplot dan bar plot 

![kategorik labe](https://user-images.githubusercontent.com/113491625/195224533-c6820f80-3af2-4ad4-a2b6-9569a181b800.PNG)

Dari beberapa barplot danstacked barplot yangditampilkan dapat dilihat bahwauntuk setiap fitur kategorik,label 1 atau pemberian rating 5lebih unggul untuk setiap  kategori yang ada dalam fitur
### Fitur datetime
-Dari fitur datetime dapat diidentifikasi lama waktu pemrosesan pesanan dengan cara mengidentifikasi selisih antar fitur datetime, sehingga dapat dibuat kolom barupa lama waktu yang dibutuhkan, sebagai berikut:

![dt](https://user-images.githubusercontent.com/113491625/195225850-18bf900a-4c90-423f-afac-4baca328e559.PNG)

- Beberapa hasil plot berupa jointplot

![datetimee](https://user-images.githubusercontent.com/113491625/195224767-88eaf7d7-9aeb-4dbb-896e-ad82256d909c.PNG)

Titik berwarna biru lebih banyak terdapat jauh dari sumbu 0 yang menandakan pemeberian rating di bawah 5 (label 0) sebandung dengan lama waktu pemorsesan, semakin lama waktu yang dibutuhkan, rating dominan yang diberikan buyer adalh 0 dan sebaliknya untuk rating di ataas 5
#### Insight dari EDA
- Pada fitur numerik untuk 'price' dan 'description length' cukup unik karena rata-rata untuk nilai fitur tersebut lebih tinggi padapemberian rating 5 daripada dibawah 5, berbeda dengan fitur numerik lain yang berlaku sebaliknya
- Pada fitur kategorik, di setiap kategori dalam fitur lebih banyak pemberian degan rating 5 daripada di bawah 5, namun kurang dapat dijelaskan hubungannya
- Dari ketiga tipe data, yang paling berpengaruh terhadap pemberian rating terdapat pada fitur datetime yaitu lama waktu yang dibutuhkan dalam proses pesanan. Dimana semakin lama waktu tahapan pemrosesan, maka rating yang diberikan oleh buyer lebih dominan di bawah 5





