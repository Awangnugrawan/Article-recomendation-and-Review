# Laporan Proyek Machine Learning – Awang Mulya Nugrawan

## Domain Proyek
Banyaknya jumlah informasi yang tersedia di internet saat ini. Banyak orang yang memiliki akses ke internet dan mencari informasi yang relevan dan terpercaya. 
Namun, dengan banyaknya informasi yang tersedia, seringkali menimbulkan kesulitan bagi pengguna untuk menemukan artikel yang sesuai dengan kebutuhan mereka.Terkadang, 
pengguna harus menelusuri berbagai sumber dan membaca banyak artikel sebelum menemukan yang mereka butuhkan. Ini dapat menjadi proses yang memakan waktu 
dan membosankan. Oleh karena itu, diperlukan sistem yang mampu membantu pengguna dalam menemukan artikel yang sesuai dengan kebutuhan mereka dengan cepat dan efisien.

Sistem recomendasi artikel memainkan peran penting dalam membantu pengguna menemukan artikel yang relevan dan terpercaya. Sistem ini menggunakan algoritma untuk 
menganalisis data seperti preferensi pengguna, tipe artikel yang dicari, dan interaksi sebelumnya dengan artikel lain. Berdasarkan analisis ini, sistem memberikan 
rekomendasi artikel yang  sesuai dengan kebutuhan pengguna. Ini dapat membantu pengguna menemukan informasi yang mereka cari dengan lebih cepat dan mudah.

## Business Understanding

### Problem Statements
Bagaimana cara membuat sistem rekomendasi artikel yang dapat meningkatkan tingkat interaksi dan engagement pengguna dengan konten yang diterima?

Menjelaskan pernyataan masalah latar belakang:
- Kurangnya aksesibilitas terhadap artikel yang relevan bagi pengguna, sehingga membuat mereka kesulitan menemukan artikel yang sesuai dengan kebutuhan dan minat mereka.
- Artikel yang dibagikan seringkali tidak relevan dengan minat dan kebutuhan pengguna, sehingga membuat mereka tidak tertarik untuk membacanya.
- Terlalu banyak artikel yang tersedia, sehingga membuat pengguna kesulitan menemukan artikel yang sesuai dengan kebutuhan dan minat mereka.
- Sistem rekomendasi artikel yang tidak memperhitungkan perkembangan dan perubahan minat dan kebutuhan pengguna secara berkala.

### Goals
Menjelaskan tujuan dari pernyataan masalah:
- Mengidentifikasi kebutuhan dan preferensi pembaca terhadap artikel yang akan mereka baca.
- Meningkatkan tingkat interaksi dan engagemen pembaca dengan artikel yang mereka baca.
- Memperbaiki relevansi dan keakuratan rekomendasi artikel.
- Meningkatkan brand awareness dan meningkatkan loyalitas pembaca.
- Menciptakan pengalaman yang lebih baik bagi pembaca dengan memberikan artikel yang sesuai dengan kebutuhan dan preferensi mereka

 ### Solution statements
 Solusi pada rekomendasi artikel akan  menggunakan 2 model yaitu:
 
 - Content-based filtering adalah teknik rekomendasi yang berdasarkan pada karakteristik item yang direkomendasikan. Dalam artikel rekomendasi, content-based filtering 
 dapat digunakan dengan menentukan fitur artikel seperti judul, deskripsi, kategori, tag, dll. Kemudian, algoritma menentukan artikel yang sesuai dengan preferensi 
 pengguna berdasarkan bagaimana fitur artikel tersebut cocok dengan preferensi pengguna sebelumnya. Misalnya, jika seorang pengguna sering membaca artikel tentang 
 teknologi, algoritma akan merekomendasikan artikel-artikel terbaru tentang teknologi yang sesuai dengan preferensi pengguna tersebut. 
 
 - Collaborative filtering adalah teknik rekomendasi yang berdasarkan pada interaksi pengguna dengan item-item tertentu. Teknik ini membuat rekomendasi berdasarkan pengalaman 
 pengguna lain yang mirip dengan preferensi pengguna saat ini. Dalam artikel rekomendasi, collaborative filtering dapat digunakan untuk menentukan artikel yang mungkin akan 
 disukai oleh pengguna berdasarkan pada bagaimana pengguna lain dengan preferensi yang sama memberikan nilai pada artikel tertentu. 
 


## Data Understanding
Dataset yang digunakan pada laporan ini berisi informasi tentang aktivitas pengguna dalam berbagi dan membaca artikel. Data ini diambil dari Deskdrop, sebuah platform internal 
untuk berbagi artikel bagi tim CI&T. Dataset ini berisi informasi tentang pengguna, artikel yang dibagikan dan dibaca, dan waktu aktivitas. Ini dapat digunakan untuk membuat sistem 
rekomendasi artikel yang memberikan rekomendasi artikel berdasarkan preferensi pengguna dan perilaku sebelumnya.Dataset ini terdiri dari dua file csv yaitu Shared_articles dan Users_interactions
[Kaggle Repository](https://www.kaggle.com/datasets/gspmoreira/articles-sharing-reading-from-cit-deskdrop)

### Variabel-variabel pada Articles sharing and reading from CI&T DeskDrop Kaggle Dataset adalah sebagai berikut:
####  Shared_articles

1. "timestamp"  memuat waktu pada saat suatu event terjadi, dan format UNIX timestamp digunakan untuk merepresentasikannya.
2. "EventType" adalah variabel yang mencatat jenis aktivitas yang terjadi dalam sistem ada dua jenis aktivitas yang tercatat, yaitu "CONTENT SHARED" dan "CONTENT REMOVED".
3. "contentId" adalah identifikasi unik untuk suatu konten, seperti ID artikel.
4. "authorPersonId" adalah identifikasi unik untuk penulis suatu konten.
5. "authorSessionId" adalah identifikasi unik untuk sesi penulis pada saat event terjadi.
6. "authorUserAgent" adalah informasi mengenai perangkat atau browser yang digunakan oleh penulis saat event terjadi.
7. "authorRegion" adalah informasi mengenai wilayah geografis penulis.
8. "authorCountry" adalah informasi mengenai negara tempat tinggal penulis.
9. "contentType" menjelaskan jenis konten, seperti HTML, VIDEO, dan RICH.
10. "url" adalah URL untuk konten.
11. "title" adalah judul konten.
12. "text" adalah teks dari konten.
13. "lan" adalah informasi mengenai bahasa konten.
  
#### Users_interactions

1. "timestamp"  memuat waktu pada saat suatu event terjadi, dan format UNIX timestamp digunakan untuk merepresentasikannya.
2. "eventType" adalah variabel yang mencatat jenis aktivitas yang terjadi dalam 
sistem ada beberapa jenis aktivitas seperti VIEW, LIKE, COMMENT CREATED, DLL
3. "contentId" adalah identifikasi unik untuk suatu konten, seperti ID artikel.
4. "personId" merupakan identitas unik dari setiap pengguna. Variabel ini digunakan untuk mengidentifikasi setiap pengguna secara individual.
5. "sessionId" adalah identitas unik dari sesi aktivitas pengguna. Variabel ini digunakan untuk mengidentifikasi interaksi pengguna yang terkait dengan sesi            tertentu.
6. "userAgent" menyimpan informasi tentang perangkat dan browser yang digunakan oleh pengguna saat melakukan interaksi. Informasi ini dapat berisi nama perangkat,      sistem operasi, versi browser, dll.
7. "userRegion" menyimpan informasi tentang wilayah geografis dari pengguna. Ini dapat berisi informasi tentang negara atau provinsi dimana pengguna berada.
8. "userCountry" menyimpan informasi tentang negara dari pengguna. Ini digunakan untuk mengidentifikasi negara asal pengguna dan dapat digunakan untuk analisis        demografis.

### Explorasi data analisis:
####  Shared_articles
- Jumlah baris: 3122
- Jumlah kolom : 13
- Info dataset:

										

|   NO	| Column            |Non-Null Count 	 |Dtype		   |
|---	|---	                 |---			           |---     		|
|   1 	|timestamp        	 |3122 non-null   	|int64    	|
|   2 	|eventType          |3122 non-null    |object   	|
|   3	|contentId     	     |3122 non-null   	|int64    	|
|   4	|authorPersonId	     |3122 non-null   	|int64    	|
|   5	|authorSessionId     |3122 non-null   	|int64    	|
|   6	|authorUserAgent  	  |680 non-null   	 |object   	|
|   7	|authorRegion 	      |680 non-null     |object   	|
|   8	|authorCountry   	   |680 non-null     |object   	|
|   9	|contentType  	      |3122 non-null    |object   	|
|   10	|url                |3122 non-null    |object   	|
|   11	|title    	         |3122 non-null   	|object  	 |
|   12	|text    	          |3122 non-null   	|object  	 |
|   13	|	lang    	         |3122 non-null   	|object  	 |


Tabel 1. Info detail tiap kolom Shared_articles

Pada tabel 1 terdiri atas 13 kolom dan tipe datanya terdiri atas 9 _object_ dan 5 _int64_

####  Users_interactions
- Jumlah baris: 72312
- Jumlah kolom : 8
- Info dataset:
										

|   NO	| Column            |Non-Null Count 	 |Dtype		   |
|---	|---	                 |---			           |---     		|
|   1 	|timestamp        	 |72312 non-null   	|int64    	|
|   2 	|eventType          |72312 non-null    |object   	|
|   3	|contentId     	     |72312 non-null   	|int64    	|
|   4	|personId      	     |72312 non-null   	|int64    	|
|   5	|sessionId           |72312 non-null   	|int64    	|
|   6	|userAgent  	  |56918 non-null   	 |object   	|
|   7	|userRegion 	      |56907 non-null     |object   	|
|   8	|userCountry   	   |56918 non-null     |object   	|



Tabel 2. Info detail tiap kolom Users_interactions

Pada tabel 2 terdiri atas 8 kolom dan tipe datanya terdiri atas 4 _object_ dan 4 _int64_


## Data Preparation
Teknik yang digunakan pada notebook secara berurutan : 
- 

## Modeling
Pada dataset ini menggunakan 3 modelling yaitu :
1. KNeighborsRegressor 

Kelebihan:
-	Mudah diimplementasikan: KNeighborsRegressor sangat mudah diimplementasikan dan bisa digunakan hanya dengan beberapa baris kode.
-	Menangani data yang hilang: KNeighborsRegressor bisa menangani data yang hilang tanpa memerlukan imputasi apa pun.
-	Berfungsi dengan baik pada dataset kecil: KNeighborsRegressor berfungsi dengan baik pada dataset kecil dan merupakan pilihan yang baik saat data yang tersedia terbatas.

Kekurangan:
-	Sensitif terhadap fitur yang tidak relevan: KNeighborsRegressor sensitif terhadap fitur yang tidak relevan dan bisa terpengaruh oleh adanya fitur bising atau berlebihan dalam data.
-	Mahal secara komputasional: KNeighborsRegressor bisa mahal secara komputasional saat jumlah titik data besar, karena algoritma harus menghitung jarak antara semua titik data.
-	Kinerja tergantung pada pilihan k: Kinerja KNeighborsRegressor tergantung pada pilihan k, jumlah tetangga terdekat untuk dipertimbangkan, yang bisa sulit ditentukan.

Kode `knn = KNeighborsRegressor(n_neighbors=3)` ini digunakan untuk membuat objek model K-Nearest Neighbor Regression (KNN). Pada baris ini, parameter `n_neighbors=3` digunakan untuk menentukan jumlah tetangga terdekat (K) yang akan digunakan dalam memprediksi tarif penerbangan. Artinya, dalam hal ini, 3 tetangga terdekat dalam data historis akan digunakan untuk memprediksi tarif penerbangan.

Kode `knn.fit(X_train, y_train)` digunakan untuk melatih model KNN dengan data latih (X_train, y_train). X_train adalah data fitur yang digunakan untuk memprediksi tarif penerbangan, sedangkan y_train adalah data target (tarif penerbangan) yang akan diprediksi oleh model. Setelah melatih model, model KNN akan mempelajari hubungan antara fitur-fitur dan tarif penerbangan dan siap untuk memprediksi tarif penerbangan baru.

2. Random Forest Regressor

Kelebihan:
-	Bisa menangani hubungan non-linier: Random Forest Regressor bisa menangani hubungan non-linier antara fitur dan variabel target, membuatnya pilihan yang baik untuk dataset yang kompleks.
-	Tahan terhadap outliers: Random Forest Regressor tahan terhadap outliers dan tidak membuat asumsi yang kuat tentang distribusi data.
-	Mengurangi overfitting: Dengan mengambil rata-rata prediksi dari banyak pohon keputusan, Random Forest Regressor mengurangi overfitting, yang merupakan masalah umum pada algoritma pohon keputusan.


Kekurangan:
-	Mahal secara komputasional: Random Forest Regressor bisa mahal secara komputasional, terutama saat jumlah pohon besar atau saat jumlah fitur tinggi.
-	Rawan overfitting: Meskipun Random Forest Regressor kurang rawan overfitting dibandingkan pohon keputusan, ia masih bisa overfitting jika jumlah pohon terlalu besar atau jika kedalaman pohon terlalu dalam.
-	Sulit diterjemahkan: Berbeda dengan model regresi linier sederhana, prediksi Random Forest Regressor sulit diterjemahkan, karena berdasarkan pada kombinasi dari banyak pohon keputusan.

Kode `RF = RandomForestRegressor(n_estimators=50, max_depth=16, random_state=55, n_jobs=-1)` ini digunakan untuk membuat objek model Random Forest Regression. Pada baris ini, parameter `n_estimators=50` digunakan untuk menentukan jumlah pohon yang akan dibangun dalam model Random Forest. Parameter `max_depth=16` digunakan untuk menentukan kedalaman maksimal pohon dalam model. Parameter `random_state=55` digunakan untuk memastikan hasil reproduksi model Random Forest. Dan `Parameter n_jobs=-1` digunakan untuk menentukan jumlah kerja paralel yang akan digunakan dalam melatih model.

Kode `RF.fit(X_train, y_train)` digunakan untuk melatih model Random Forest Regression dengan data latih (X_train, y_train). X_train adalah data fitur yang digunakan untuk memprediksi tarif penerbangan, sedangkan y_train adalah data target (tarif penerbangan) yang akan diprediksi oleh model. Setelah melatih model, model Random Forest akan mempelajari hubungan antara fitur-fitur dan tarif penerbangan dan siap untuk memprediksi tarif penerbangan baru.

3. Decision Tree Regressor

Kelebihan 
-	Mudah dipahami dan diimplementasikan: Decision Tree Regressor memiliki representasi visual yang mudah dipahami, sehingga memudahkan interpretasi hasil dan membuat model ini mudah dipahami oleh stakeholder.
-	Dapat menangani fitur numerik dan kategorikal: Decision Tree Regressor dapat menangani fitur numerik dan kategorikal dengan baik, sehingga dapat digunakan untuk berbagai jenis data.
-	Dapat menangani outliers dan non-linearitas: Decision Tree Regressor memiliki kemampuan membagi data secara berulang-ulang sehingga dapat menangani outlier dan non-linearitas dalam data.


Kekurangan :
-	Mudah overfitting: Decision Tree Regressor memiliki kecenderungan untuk overfitting jika depth-nya terlalu dalam. Ini dapat diatasi dengan teknik seperti pemotongan pohon, tetapi membutuhkan pemahaman yang baik dari model dan dataset.
-	Instabilitas: Decision Tree Regressor sangat sensitif terhadap perubahan kecil pada data, sehingga model yang dibangun dengan dataset yang berbeda mungkin sangat berbeda.
-	Bias terhadap fitur yang memiliki banyak data: Decision Tree Regressor cenderung memprioritaskan fitur yang memiliki banyak data dalam membuat pembagian data.

Kode `DTR= DecisionTreeRegressor(max_depth=20, random_state=3)` ini digunakan untuk membuat objek model Decision Tree Regression. Pada baris ini, parameter `max_depth=20` digunakan untuk menentukan kedalaman maksimal pohon dalam model.Dan parameter `random_state=3` digunakan untuk memastikan hasil reproduksi model Decision Tree.

Kode `DTR.fit(X_train, y_train)` digunakan untuk melatih model Decision Tree Regression dengan data latih (X_train, y_train). X_train adalah data fitur yang digunakan untuk memprediksi tarif penerbangan, sedangkan y_train adalah data target (tarif penerbangan) yang akan diprediksi oleh model. Setelah melatih model, model Decision Tree akan mempelajari hubungan antara fitur-fitur dan tarif penerbangan dan siap untuk memprediksi tarif penerbangan baru.

## Evaluation
Pada tahap evaluasi digunakan tiga metrik evaluasi yang digunakan yaitu:

1. R2_Score

R2 Score adalah metrik yang digunakan untuk mengukur seberapa baik model regresi memprediksi target. 
Formula R2 Score adalah:

$$ R2 = {1 - {SSres \over SStot}} $$

Ket:
- SSres adalah sum of squared residuals, yaitu jumlah kuadrat selisih antara nilai target aktual dan nilai target prediksi.
- SStot adalah total sum of squares, yaitu jumlah kuadrat selisih antara nilai target aktual dan nilai rata-rata target.

Metrik ini mengukur seberapa baik model regresi menjelaskan variasi dari target (tarif pesawat). Nilai R2_Score berkisar antara 0 dan 1, dimana nilai 1 menunjukkan model regresi yang sempurna dan nilai 0 menunjukkan model regresi yang buruk. Dalam hal prediksi tarif pesawat, nilai R2_Score yang tinggi menunjukkan bahwa model regresi memiliki kemampuan yang baik dalam memprediksi tarif pesawat.

Dengan menggunakan metrik R2_Score tersebut di dapatkan hasil dari 3 modelling :

| Model	|  train 	|  test 	|
|---	|---		|---		|
|KNN   	|0.798497   	|0.624805   	|
|RF   	|0.941121   	|0.825389   	|
|DTR   	|0.972591   	|0.737278   	|

Tabel 3. Metrik R2_Score

Pada tabel 3 dapat diketahui bahwa model dengan r2_score tertinggi untuk data _training_ dan data _test_ adalah model _Random Forest Regressor_ Sedangkan model dengan r2_score terendah untuk data _training_ dan data _test_ adalah _KNN_  

![plot r2_score](https://raw.githubusercontent.com/Awangnugrawan/Predictive-Analysis-and-Review/main/plot_R2_SCORE.jpg)

Gambar 2. Plot R2 Score

Pada gambar 2 dapat dilihat bahwa urutan model dari yang terbaik ke terburuk adalah RF , DTR , dan KNN


2. Mean Square Error

Mean Squared Error (MSE) adalah metrik yang digunakan untuk mengukur kualitas model regresi. 
Formula MSE adalah:

$$ MSE = {Σ * (yi - ŷi)^2 \over n} $$

ket:
- n adalah jumlah data
- yi adalah nilai target aktual
- ŷi adalah nilai target prediksi
- Σ (yi - ŷi)^2 adalah jumlah kuadrat selisih antara nilai target aktual dan nilai target prediksi

Metrik ini mengukur rata-rata kuadrat selisih antara nilai target aktual (tarif pesawat) dan nilai target prediksi. Semakin kecil nilai MSE, semakin baik model regresi dalam memprediksi tarif pesawat. Dalam hal prediksi tarif pesawat, model regresi dengan MSE yang lebih kecil akan dianggap memiliki performa yang lebih baik dibandingkan dengan model yang memiliki MSE yang lebih besar.

Dengan menggunakan metrik Mean Square Error tersebut di dapatkan hasil dari 3 modelling:

| Model	|  train 	|  test 	|
|---	|---		|---		|
|KNN   	|4186.297999   	|8712.025152   	|
|RF   	|1223.235661   	|4054.469   	|
|DTR   	|569.42498   	|6100.403468   	|

Tabel 4 Metrik Mean Square Error

Pada tabel tersebut model yang memiliki _error_ yang tinggi adalah _KNN_ dan model yang memiliki _error_ terendah adalah _RF_

![plot MSE](https://raw.githubusercontent.com/Awangnugrawan/Predictive-Analysis-and-Review/main/PLOT%20MSE.jpg)

Gambar 3. PLOT MSE

Berdasarkan hasil plot pada gambar 3 urutan model yang memiliki error sedikit ke terbanyak adalah _RF_ , _DTR_ , dan _KNN_


3. Mean Absolute Error

Mean Absolute Error (MAE) adalah metrik yang digunakan untuk mengukur kualitas model regresi. 
Formula MAE adalah:

$$ MAE = {Σ * |yi - ŷi| \over n} $$

ket:
- n adalah jumlah data
- yi adalah nilai target aktual
- ŷi adalah nilai target prediksi
- Σ |yi - ŷi| adalah jumlah absolute selisih antara nilai target aktual dan nilai target prediksi

Metrik ini mengukur rata-rata selisih antara nilai target aktual (tarif pesawat) dan nilai target prediksi. Semakin kecil nilai MAE, semakin baik model regresi dalam memprediksi tarif pesawat. Dalam hal prediksi tarif pesawat, model regresi dengan MAE yang lebih kecil akan dianggap memiliki performa yang lebih baik dibandingkan dengan model yang memiliki MAE yang lebih besar.

Dengan menggunakan metrik Mean Absolute Error tersebut di dapatkan hasil dari 3 modelling :

| Model	|  train 	|  test 	|
|---	|---		|---		|
|KNN   	|1.24639   	|1.799676   	|
|RF   	|0.690195   	|1.236153   	|
|DTR   	|0.296922   	|1.440906   	|

Tabel 5. Metrik Mean Absolute Error

Pada tabel 5 sama seperti MSE model yang memiliki _error_ yang tinggi adalah _KNN_ dan model yang memiliki _error_ terendah adalah _RF_

![plot MAE](https://raw.githubusercontent.com/Awangnugrawan/Predictive-Analysis-and-Review/main/Plot%20MAE.jpg)

Gambar 4. PLOT MAE

Berdasarkan gambar 4 dan dari ketiga plot metrik dapat disimpulkan bahwa model _Random Forest Regression_ adalah model yang terbaik



Referensi:
Wang, T., Pouyanfar, S., Tian, H., Tao, Y., Alonso, M., Luis, S., & Chen, S. C. (2019, July). A framework for airfare price prediction: a machine learning approach. In 2019 IEEE 20th international conference on information reuse and integration for data science (IRI) (pp. 200-207). IEEE.

**---Ini adalah bagian akhir laporan---**
