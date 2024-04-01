# E-Commerce Customer Churn Prediction (Classification Model)
by Ocky Daniel 

<br>Jika ada image yang tidak bisa diload, silahkan kunjungi [link ini](https://nbviewer.org/github/OckyDaniel/Purwadhika-Capstone-Project_Module-3/blob/main/Ecommerce_Capstone_Project_Module_3-3.ipynb).

# **E-Commerce Customer *churn***

 Industri Ecommerce menghadapi permasalahan serius terkait dengan churn pelanggan, di mana pelanggan memutuskan untuk berhenti menggunakan layanan perusahaan. Customer churn adalah adalah kecenderungan pelanggan untuk meninggalkan penyedia layanan, atau beralihnya pelanggan dari satu penyedia layanan ke yang lainnya. Churn pelanggan juga erat kaitannya dengan cost yang ditanggung oleh perusahaan, dilansir dari [Amy Gallo, 2014](https://hbr.org/2014/10/the-value-of-keeping-the-right-customers) memperoleh pelanggan baru (Customer Acquisition Cost/CAC) membutuhkan biaya lebih besar 5 kali lipat dibandingkan dengan mempertahankan pelanggan loyal (Customer Retention Cost/CRC). Kita akan membangun model klasifikasi yang akan membantu perusahaan kita dapat mengurangi potensi kehilangan pelanggan loyal, tetapi tanpa membuat cost marketing dari perusahaan yang sia-sia,. Jadi kita ingin sebanyak mungkin prediksi kelas positif yang benar, dengan sesedikit mungkin prediksi *False Positive*.
 
Dataset milik perusahaan E-Commerce online terkemuka. Source: [Purwadhika](https://drive.google.com/drive/folders/1PITb78NtK9Ra6wOkQdXCIgItZkj29Ves).
Dimana kita akan melakukan Data Cleaning berupa Handling Missing value dengan **Iterative Imputer**, dikarenakan merupakan data multivariate atau missing values memiliki hubungan dengan variabel lain, drop duplikat data, handling inconsistent data drop beberapa outlier dan beberapa membiarkan outlier karena kita anggap sebagai hal yang natural. Kita juga melakukan One Hot Encoding dan Binary Encoder dan data merupakan imbalanced data pada kelas 1 yang sedikit (16.30%) dibanding kelas 0 (83.70%).

Benchmarking Model dilakukan untuk mendapatkan hasil yang terbaik, diantaranya Logistic Regression, Decision Tree, Random Forest, KNN, XGBoost,dan LightGBM dengan metode Cross-Validation dan Prediction ROC_AUC Score. **LightGBM** menjadi model terbaik dengan parameter `learning_rate`: `0.1`, `max_bin`: `300`, `max_depth`: `21`, `min_data_in_leaf`: `20`, `num_iterations`: `100`, `num_leaves`: `51`,`lambda_l1`: `0.01`,`lambda_l2`: `0.01`,`min_gain_to_split`: `0`. Score yang dihasilkan pada Train 94.54% dan pada Test 96.50%.

Features paling berpengaruh terhadap Customer Churn yaitu `Tenure`, `Complain`, dan `NumberOfAddress`. Semakin kecil nilai `Tenure` artinya semakin baru customer berlangganan semakin besar kemungkinan Customer akan churn dan semakin lama customer berlangganan semakin betah dia terhadap layanan perusahaan sebaliknya pada `Complain` dan `NumberOfAddress`, semakin tinggi semakin cenderung untuk Churn.

Kita bisa melihat 10 Customer paling berpotensi melakukan Churn dilihat dari Probabilitas dia melakukan churn.
- 10 customer tersebut memiliki probabilitas 99.93 - 99.85% melakukan Churn.
- 10 customer tersebut memiliki `Tenure` 0 atau 1 
- 10 customer tersebut 1 bulan terakhir bertransaksi dengan kategori `Mobile Phone` dan `Laptop & Accessory`.
- 10 Customer tersebut melakukan Complain.

Efek Model ML yang dibangun terhadap profitabilitas perusahaan 
- Sebelum pakai ML: perusahaan merugi **-7.620 USD** per bulan
- Setelah menggunakan ML: perusahaan berhasil menghasilkan profit **15.575 USD** per bulan

Untuk kedepannya perusaahaan perlu melakukan beberapa hal:

Untuk Business
1. Perusahaan e-commerce perlu menyusun strategi agar dapat tetap menjaga kualitas produk dan pelayanan agar dapat menghindari complain yang masuk.
1. Perusahaan e-commerce perlu menyusun strategi agar dapat menciptakan loyalitas pelanggan, baik dengan melakukan inovasi pada produk yang dipasarkan dan memberikan penawaran yang menarik, sehingga tenure customer semakin tinggi.
1. Perusahaan dapat memberikan penawaran berupa pengurangan biaya ongkos kirim kepada pelanggan yang memiliki jarak yang jauh dari gudang, bisa dengan melakukan kerja sama dengan pihak jasa pengantar (kurir) untuk meringankan cost dari perusahaan.
1. Perusahaan perlu menggunakan machine learning yang sudah dibuat, agar dapat mengurangi kerugian bagi perusahaan dengan memberikan promosi tepat sasaran kepada customer yang akan melakukan churn.
1.Perusahaan dapat memberikan penawaran khusus (Promo Cashback paket produk) kepada pelanggan yang memiliki masa tenure 0 - 1 bulan untuk mencegah potensi churn terhadap pelanggan baru.

Untuk Model
1. Mengumpulkan lebih banyak data khususnya pada minority class.
1. Menambahkan parameter lain dalam hyperparameter tuning.
1. Menambahkan ID customer untuk memastikan dan mengetahui data yang duplikat.
1. Menambahkan feature lain seperti lama pengiriman produk, ketepatan waktu pengiriman, dan lain-lain.
1. Meminimalisir kesalahan penulisan data dan memastikan data yang diperoleh tidak ada yang kosong atau tidak terisi.
1. Mencoba ML algorithm diluar ML algorithm yang dipakai di project ini, dan mencoba dengan hyperparamater tuning kembali seperti SMOTENC dan lain sebagainya.
1. Mencoba dengan urutan pipeline yang berbeda.
   
**Thank You!!!**
