# **Laporan Proyek Machine Learning Terapan - Renaldi Panji Wibowo**
## Sistem Rekomendasi Video Games - Sumber dataset [_Discovering Hidden Trends in Global Video Games_](https://www.kaggle.com/datasets/thedevastator/discovering-hidden-trends-in-global-video-games/code)

## **Project Overview**

![dataset-cover (7)](https://github.com/renaldipanji/video-games-reccomendattion/assets/75974146/969f6d57-2cd7-4486-bc6d-bc4c73603b76)


Perubahan tren permainan dari konsol game menjadi game digital telah mengubah cara pendistribusian game tersebut. Game digital memiliki berbagai keunggulan dibandingkan dengan game konsol, seperti kemudahan akses dan fitur bermain online. Oleh karena itu, ada berbagai platform yang digunakan untuk mendistribusikan game digital kepada para pengguna [1][2]. Namun, keberagaman genre game yang ada seringkali membuat para pemain bingung dalam memilih game yang ingin dimainkan [3]. Salah satu solusi yang efektif untuk mengatasi masalah ini adalah dengan menggunakan Sistem Rekomendasi pada setiap platform game [4][5].

Dalam konteks platform game, Sistem Rekomendasi membantu para pemain dengan menyajikan rekomendasi game berdasarkan genre yang disukai oleh pemain atau berdasarkan game-game yang sedang populer saat itu [4][5]. Dengan memanfaatkan Sistem Rekomendasi, para pemain dapat dengan mudah menemukan game-game yang sesuai dengan minat mereka, sehingga meningkatkan pengalaman bermain game secara keseluruhan. Sistem ini memainkan peran penting dalam mengurangi kompleksitas pengambilan keputusan dan memberikan rekomendasi yang dipersonalisasi sesuai dengan preferensi masing-masing individu [1][4].

Sebagai hasilnya, platform game dapat meningkatkan keterlibatan pengguna dan mempertahankan loyalitas pelanggan dengan menyajikan rekomendasi game yang relevan dan menarik bagi setiap pemain [2][3]. Secara keseluruhan, Sistem Rekomendasi telah menjadi alat yang tak tergantikan dalam industri permainan, memfasilitasi distribusi game digital, dan memperkaya pengalaman bermain game bagi para pemain di seluruh dunia.

## **Business Understanding**

### **Problem Statements**

* Bagaimana cara menghadirkan rekomendasi game yang telah dipilih oleh satu pemain kepada pemain lainnya?

### **Goals**

* Mampu mengembangkan sistem rekomendasi yang efisien berdasarkan penilaian dan aktivitas sebelumnya dari para pemain.

### **Solution statements**

Proyek ini memanfaatkan dua algoritma _Machine Learning_ untuk mengimplementasikan sistem rekomendasi :

* _**Content Based Filtering**_, yang merekomendasikan game dengan genre serupa berdasarkan tindakan dan umpan balik eksplisit dari pemain di masa lalu.

  _**Content Based Filtering**_ adalah sebuah algoritma dalam sistem rekomendasi yang bertujuan untuk merekomendasikan item-item yang serupa dengan item yang disukai oleh pengguna, berdasarkan atribut atau karakteristik dari item tersebut. Dalam konteks proyek ini, algoritma Content Based Filtering digunakan untuk merekomendasikan game-game yang memiliki genre serupa dengan game yang disukai oleh pemain. Hal ini dilakukan dengan menganalisis tindakan dan umpan balik eksplisit yang diberikan oleh pemain pada masa lalu terhadap game-game yang pernah mereka mainkan.

* **_Collaborative Filtering_**, yang mengandalkan preferensi komunitas pengguna tanpa memerlukan atribut khusus untuk setiap item.

  _**Collaborative Filtering**_ adalah sebuah algoritma dalam sistem rekomendasi yang mengandalkan pendapat atau preferensi komunitas pengguna untuk merekomendasikan item-item tertentu. Algoritma ini tidak memerlukan atribut atau karakteristik dari setiap item yang ada dalam sistem, melainkan berfokus pada pola hubungan antara pengguna dan item yang diakses oleh mereka.

Algoritma Content Based Filtering digunakan untuk merekomendasikan game berdasarkan aktivitas pemain sebelumnya, sedangkan Collaborative Filtering digunakan untuk merekomendasikan game berdasarkan peringkat tertinggi.

## **Data Understanding**

Dataset ini berisi informasi tentang penjualan video game dari berbagai _platform_, genre, dan wilayah di seluruh dunia. Data yang terdapat dalam dataset ini mencakup game-game yang dianggap sebagai hit dalam industri game saat ini [_Discovering Hidden Trends in Global Video Games_](https://www.kaggle.com/datasets/thedevastator/discovering-hidden-trends-in-global-video-games/code). Meskipun dataset ini awalnya dikumpulkan untuk menganalisis penjualan game, pada proyek ini akan mencoba menggunakan data yang ada untuk mengembangkan sebuah sistem rekomendasi. Total data yang tersedia dalam dataset ini mencapai 1907 data, sedangkan total atribut data yang tersedia sebanyak 12 atribut.

### **Atribut Data**

Atribut data pada Discovering Hidden Trends in Global Video Games dataset adalah sebagai berikut:

- `Rank`	Peringkat game dalam hal penjualan global. (Int)
- `Game Title` : Judul game. (String)
- `Platform` : Platform tempat game dirilis. (String)
- `Year` : Tahun game dirilis. (Integer)
- `Genre` : Genre game. (String)
- `Publisher` : Penerbit game. (String)
- `North America` : Penjualan game di Amerika Utara. (Integer)
- `Europe` : Penjualan game di Eropa. (Integer)
- `Japan` : Penjualan game di Jepang. (Integer)
- `Rest of World` : Penjualan game di seluruh dunia. (Integer)
- `Global` : Total penjualan game secara global. (Integer)
- `Review` : Skor ulasan game. (Float)

### **Exploratory Data Analysis**

![Platform Video Games](https://github.com/renaldipanji/video-games-reccomendattion/assets/75974146/38e7dc9c-4308-48f9-8c0c-ad68163f890c)

$$Gambar\ 1.1\ Platform$$

Dari analisis pada $Gambar\ 1.1$, terlihat bahwa PS2 merupakan platform yang paling sering merilis game dibandingkan platform lainnya. Hal ini menunjukkan bahwa PS2 telah menjadi salah satu platform yang populer dan banyak digunakan oleh para pengembang game untuk merilis produk-produk mereka. Data ini memberikan wawasan yang berharga tentang dominasi PS2 dalam industri game dan dapat menjadi informasi yang relevan bagi para pengambil keputusan di dalam industri tersebut.

![Publisher Video Games](https://github.com/renaldipanji/video-games-reccomendattion/assets/75974146/977d6551-bafb-43b7-ae82-484e10bfcf25)

$$Gambar\ 1.2\ Publisher$$

Berdasarkan visualisasi pada gambar 1.2, dapat dilihat bahwa Electronic Arts (EA) merupakan perusahaan penerbit game yang merilis paling banyak game dibandingkan perusahaan penerbit game lainnya. Grafik menunjukkan bahwa EA mendominasi jumlah rilisan game di atas platform-platform yang tercantum, sehingga menjadikan EA sebagai perusahaan penerbit game dengan kontribusi paling besar dalam industri permainan.

![Genre Video Games](https://github.com/renaldipanji/video-games-reccomendattion/assets/75974146/ed47ed61-72b9-43ad-96ff-64e52b58c412)

$$Gambar\ 1.3\ Genre$$

Berdasarkan Gambar 1.3, dapat diketahui bahwa genre Sport menjadi genre yang paling dominan dalam industri game, dengan jumlah game yang paling banyak dibuat dibandingkan dengan genre lainnya. Genre Sport memiliki frekuensi tertinggi dalam dataset, menunjukkan popularitas yang tinggi di kalangan pembuat game.

![Tahun Video Games](https://github.com/renaldipanji/video-games-reccomendattion/assets/75974146/4d16b360-7590-403c-82c9-584fc799e269)

$$Gambar\ 1.4\ Year$$

Berdasarkan Gambar 1.4, terlihat bahwa jumlah game yang dirilis mencapai puncaknya pada tahun 2008. Pada tahun tersebut, terdapat sekitar 1907 game yang dirilis, menjadikannya tahun dengan jumlah game terbanyak dalam dataset ini.

Visualisasi tersebut menunjukkan tren yang menarik dalam industri game, di mana pada tahun 2008 terjadi lonjakan signifikan dalam jumlah game yang dirilis. Hal ini dapat menjadi fokus perhatian bagi para pengambil keputusan di industri game untuk menganalisis faktor-faktor yang berkontribusi pada peningkatan jumlah game pada tahun tersebut.


## **Data Preparation**

Sebelum menciptakan model sistem rekomendasi, ada beberapa tahapan yang perlu dilakukan. Tahapan-tahapan tersebut adalah sebagai berikut:

1. `Pembuatan Fitur User_ID`: Data awal tidak memiliki fitur user_id, sehingga setiap baris dianggap sebagai user_id dan diindekskan sebagai user_id.
2. `Pemilihan Fitur`: Karena i adalah proyek sistem rekomendasi, dilakukan pemilihan fitur yang relevan, termasuk User_ID, Game Title, Platform, Year, Genre, Publisher, dan Review.
3. `Format UlanFitur`: Kom Review diubah menjadi bilangan bulat dengan melakukan pembulatan nilai.
4. `Pembuatan Fitur Game_ID`: Data Game Title yang unik diasumsikan sebagai game_id dan diberi label.
5. `Penghapusan Duplikasi Data`: Data duplikasi dihapus berdasarkan fitur Game_ID untuk memastikan keakuratan hasil.
6. `Pembuatan Dictionary`: Membuat DataFrame baru dengan hanya beberapa fitur yang relevan.
7. `Pembuatan DataFrame`: DataFrame yang baru berisi fitur-fitur yang terpilih untuk proses pembuatan model.
8. `Penggunaan TF-IDF Vectorizer`: Menghitung bobot kata dalam konteks data yang ada.
9. `Penghitungan Cosine Similarity`: Menghitung nilai kemiripan antara data satu dengan yang lain untuk mendapatkan hasil rekomendasi yang akurat.
10. `Train-test split` : proses membagi data menjadi data latih (train data) dan data uji (test data). Data latih digunakan untuk melatih model, sementara data uji digunakan untuk menguji kinerja model yang telah dilatih.

    Pada proyek ini, setelah melewati proses pembersihan data. jumlah data yang siap digunakan sebanyak 1505 data akan dibagi menjadi 1204 untuk data latih dan 301 untuk data uji. Dalam hal ini, sekitar 80% dari data akan digunakan sebagai data latih, sedangkan sekitar 20% akan digunakan sebagai data uji. Pembagian ini dapat dilakukan dengan menggunakan teknik random sampling untuk memastikan representativitas data dalam kedua subset.

    Data latih akan digunakan untuk melatih model _machine learning_ dan menyesuaikan parameter model. Setelah model dilatih, data uji akan digunakan untuk menguji performa dan mengukur akurasi model yang dihasilkan.

    Dengan membagi data menjadi data latih dan data uji, ini memungkinkan evaluasi yang obyektif terhadap kinerja model di luar data yang digunakan untuk melatihnya, sehingga memberikan perkiraan yang lebih baik tentang bagaimana model tersebut akan berperforma pada data baru yang belum pernah dilihat sebelumnya.


## **Modeling dan Results**

### **A. Model Development dengan _Content Based Filtering_**

Setelah mengaplikasikan TF-IDF Vectorizer dan menganalisis Cosine Similarity, langkah selanjutnya adalah membuat model Content Based Filtering. TF-IDF Vectorizer digunakan dalam sistem rekomendasi untuk mengidentifikasi fitur-fitur penting dari setiap genre game. Sementara itu, Cosine Similarity digunakan untuk mengukur tingkat kesamaan antara genre game dengan menggunakan teknik cosine similarity.

Model Content Based Filtering bekerja dengan cara merekomendasikan daftar game berdasarkan indeks kemiripan dari game yang telah dimainkan sebelumnya. Dengan demikian, sistem dapat menyarankan game-game yang memiliki kemiripan dengan game-game yang pernah dimainkan oleh pengguna sebelumnya. Hal ini membantu meningkatkan akurasi rekomendasi dan memberikan rekomendasi yang lebih relevan dengan preferensi pengguna.

Dengan menggunakan teknik Content Based Filtering, sistem rekomendasi dapat memberikan rekomendasi yang lebih personal dan sesuai dengan minat pengguna, karena didasarkan pada kemiripan antara game-game yang telah dimainkan sebelumnya dan game-game yang diusulkan.

$Tabel\ 1.1\ Game\ yang\ pernah\ di\ mainkan$
| game_id | genre  |                         title |
| ------- | -------|------------------------------ |
|     1182 | Platform | Super Mario Bros. |

Berdasarkan Tabel 1.1, terlihat bahwa pemain pernah memainkan game **Super Mario Bros.** yang memiliki genre Platform. Dengan menggunakan sistem rekomendasi, kita dapat mencari dan merekomendasikan 5 game teratas yang memiliki tingkat kesamaan yang tinggi dengan game yang telah dimainkan tersebut. Proses ini dilakukan dengan menghitung cosine similarity antara genre game yang dimainkan sebelumnya (**Super Mario Bros.** dengan genre Platform) dengan genre game lain dalam dataset.

Setelah proses perhitungan cosine similarity, sistem rekomendasi mengidentifikasi lima game dengan tingkat kesamaan tertinggi dengan game Super Mario Bros. yang dimainkan sebelumnya. Berikut adalah lima game yang direkomendasikan:

$Tabel\ 1.2\ Hasil\ rekomendasi\ model$
|                         title	|  genre |
| ----------------------------- | ------ |
| Super Mario Bros. 2 (FDS)		      | Platform |
| Donkey Kong Country 2: Diddy's Kong Quest	                | Platform |
| Sonic Adventure DX: Director's Cut	| Platform |
| LittleBigPlanet	  | Platform |
| Super Mario Advance 4: Super Mario Bros. 3	           | Platform |

Berdasarkan Tabel 1.2, kita dapat melihat bahwa model sistem rekomendasi berhasil berkinerja baik dalam merekomendasikan game dengan genre Platform. Hal ini terjadi karena pemain sebelumnya telah memainkan game Super Mario Bros. yang juga memiliki genre Platform. Model ini mengasumsikan bahwa pemain cenderung menyukai game dengan genre serupa, meskipun judul gamenya berbeda.

Dengan menggunakan teknik Content Based Filtering dan memanfaatkan metode TF-IDF Vectorizer dan Cosine Similarity, sistem rekomendasi mampu mengidentifikasi game-game dengan tingkat kemiripan tinggi terhadap game yang telah dimainkan sebelumnya oleh pemain, seperti Super Mario Bros. Dengan demikian, model dapat memberikan rekomendasi game yang diharapkan akan lebih sesuai dengan preferensi dan minat pemain berdasarkan genre yang telah disukai.

Dengan adanya sistem rekomendasi ini, pemain dapat menemukan game lain yang mungkin belum mereka ketahui sebelumnya namun sesuai dengan selera mereka. Proses ini dapat meningkatkan pengalaman bermain game dan memperluas pilihan game yang sesuai dengan preferensi individu pemain. Selain itu, model ini memberikan dukungan dalam memilih game baru yang sejalan dengan minat dan kesukaan pemain berdasarkan data sebelumnya.

## **B. Model Development dengan Collaborative Filtering**

Model ini berfokus pada konsep merekomendasikan game berdasarkan rating yang telah diberikan oleh pemain lain. Sebelum membuat model ini, data harus melalui proses Training terlebih dahulu. Sebagai langkah awal, data perlu dibagi menjadi dua bagian, yaitu data training dan data validation, dengan perbandingan skala 80:20. Selanjutnya, untuk proses training, model menggunakan activation function sigmoid.

Namun, sebelum melakukan training, data user dan game perlu dipetakan menjadi satu nilai yang representatif. Selain itu, rating game yang diberikan oleh pemain juga perlu diubah dalam skala 0 sampai 1 agar memudahkan proses training dan perhitungan pada model.

Setelah seluruh tahapan di atas selesai, langkah berikutnya adalah melakukan uji coba pada model. Dengan menggunakan data training dan data validation yang telah dipersiapkan sebelumnya, model akan diuji untuk melihat performanya dalam merekomendasikan game berdasarkan rating yang telah diubah ke dalam skala 0 sampai 1. Uji coba ini bertujuan untuk memastikan bahwa model dapat berfungsi dengan baik dan memberikan rekomendasi yang akurat berdasarkan rating dari pemain lain.

Dengan melakukan proses training dan uji coba pada model, diharapkan sistem rekomendasi ini dapat memberikan rekomendasi game yang relevan dan sesuai dengan preferensi serta rating yang telah diberikan oleh pemain lain. Model ini dapat meningkatkan pengalaman bermain game dan membantu pemain menemukan game yang sesuai dengan minat dan kesukaan mereka.

$Tabel\ 2.1\ Hasil\ rekomendasi\ untuk\ user$
| Showing recommendations for users: 470 |              |
| -------------------------------------- | ------------ |
| Game with high ratings from user       |              |
| -------------------------------------- | ------------ |
| Sonic Adventure 2 Battle               | Platform     |
| -------------------------------------- | ------------ |
| Top 10 Game Recommendation             |              |
| -------------------------------------- | ------------ |
| Super Mario World                      | Platform     |
| Call of Duty: Modern Warfare 2         | Shooter      |
| The Legend of Zelda: Ocarina of Time   | Adventure    |
| Tekken 3                               | Fighting     |
| The Legend of Zelda: Twilight Princess | Action       |
| The Elder Scrolls IV: Oblivion         | Role-Playing | 
| BioShock                               | Shooter      |
| Half-Life 2                            | Shooter      |
| SSX Tricky                             | Sports       |
| Super Puyo Puyo                        | Puzzle       |

Dari tabel 2.1, dapat dilihat bahwa model sistem rekomendasi ini berhasil merekomendasikan game-game yang sesuai dengan minat dan preferensi dari user_id: 470 berdasarkan rating tinggi yang diberikan oleh pemain lain. Rekomendasi game ini didasarkan pada kesamaan genre dengan game yang pernah dinilai tinggi oleh user_id: 470.

Selain itu, hasil dari Top 10 rekomendasi game menunjukkan bahwa genre yang mendominasi adalah Shooter. Hal ini menunjukkan bahwa user_id: 470 memiliki kesukaan atau minat yang tinggi pada genre Shooter, sehingga model merekomendasikan banyak game dengan genre tersebut.

Dengan adanya sistem rekomendasi ini, user_id: 470 dapat menemukan game-game berkualitas yang sesuai dengan minatnya dengan mudah dan cepat. Selain itu, model ini juga membantu meningkatkan pengalaman bermain game bagi user_id: 470 dengan memberikan rekomendasi yang relevan dan berkualitas tinggi.

## **Evaluation**

### **A. _Content Based Filtering_**

Untuk evaluasi pada model ini sederhana saja dengan menggunakan rumus precision sebagai berikut:

$$ \text{recommender system precision : } P = \frac{ \text{of our recommendations that are relevant} }{ \text{of items we recommended} } $$

$$Persamaan\ 2.1\ Rumus Precision$$

Berdasarkan Persamaan 2.1 yang merupakan rumus dari precision, kita dapat menghitung nilai precision berdasarkan model yang telah diuji coba. Dalam kasus ini, nilai precision nya adalah 100% karena dari 5 rekomendasi yang diberikan oleh model, maka cara menghitung nilai precision berdasarkan model yang telah diuji cobakan adalah P = 5/5 atau nilai precision nya adalah 100%. Nilai 5 didapatkan dari genre yang muncul pada rekomendasi semuanya adalah "Platform", sesuai dengan genre game yang pernah dimainkan sebelumnya oleh pemain. Artinya, semua rekomendasi yang diberikan oleh model merupakan rekomendasi yang relevan dan sesuai dengan preferensi pemain.

### **_B. Collaborative Filtering_**

Model ini menggunakan Binary Crossentropy untuk menghitung loss function, Adam (Adaptive Moment Estimation) sebagai optimizer, dan Root Mean Squared Error (RMSE) sebagai metrics evaluation.

$$ RMSE = \sqrt{\frac{1}{n} \sum_{i=1}^{n} (y_i - \hat{y}_i)^2} $$

$$Persamaan\ 2.2\ Rumus RMSE$$

Berikut penjelasan dari $Persamaan\ 2.2$
- At = Nilai data Aktual
- Ft = Nilai hasil prediksi
- N = banyaknya data
- ∑ = Summation (Jumlahkan keseluruhan  nilai) [6]

RMSE (Root Mean Squared Error) adalah sebuah metode pengukuran yang digunakan untuk mengevaluasi sejauh mana perbedaan nilai antara prediksi dari sebuah model dengan nilai yang sebenarnya yang telah diobservasi. Metrik ini mengukur akar kuadrat dari rata-rata dari selisih kuadrat antara nilai prediksi dan nilai sebenarnya pada setiap data. Dengan menggunakan RMSE, kita dapat menilai seberapa akurat model dalam memprediksi nilai target.

Kelebihan dari RMSE adalah metrik ini menghukum kesalahan besar lebih berat, sehingga model yang memiliki RMSE yang kecil dianggap lebih akurat daripada model yang memiliki RMSE yang besar. Hal ini membuat RMSE lebih sensitif dalam mendeteksi kesalahan besar dan lebih tepat dalam beberapa kasus.

Namun, kekurangan dari RMSE adalah bobot yang relatif tinggi diberikan pada kesalahan besar. Artinya, RMSE cenderung memberikan perhatian lebih pada prediksi yang jauh dari nilai sebenarnya, sehingga dalam beberapa kasus, metrik ini mungkin tidak sepenuhnya merepresentasikan kualitas prediksi keseluruhan.

Dalam evaluasi performa model, nilai RMSE yang lebih kecil menunjukkan performa yang lebih baik, karena perbedaan antara nilai prediksi dan nilai sebenarnya lebih rendah. Namun, penting juga untuk mempertimbangkan konteks dan kebutuhan spesifik dari aplikasi atau kasus yang sedang dihadapi[6].

Berikut Hasil Visualisasi nilai RMSE

![RMSE](https://github.com/renaldipanji/video-games-reccomendattion/assets/75974146/d9097c12-876f-485a-bc4f-791b31c545f8)

$Gambar\ 3.1\ Visualisasi\ proses\ training$

Visualisasi model training pada $Gambar\ 3.1$ menggunakan konvergen pada epochs sebanyak 100, dan didapatkan nilai akhir sebagai berikut
- **loss** : 0.5197
- **root_mean_squared_error** : 0.0352
- **val_loss** : 0.6931
- **val_root_mean_squared_error** : 0.2789

Dapat diamati bahwa garis horizontal lurus pada grafik mengindikasikan bahwa nilai memiliki nilai konstan. Hal ini disebabkan oleh karakteristik dataset yang merupakan satu kesatuan, dan antara variabel "user" dan variabel pembandingnya yaitu "game," tidak memiliki fitur id masing-masing. Oleh karena itu, fitur id diperoleh melalui proses pelabelan, sehingga jumlah nilai unik antara "user" dan "game" sama.

## **Conclusion**

Setelah mengimplementasikan dua model dalam sistem rekomendasi, yaitu Content Based Filtering dan Collaborative Filtering, dapat dilihat bahwa hanya model Content Based Filtering yang memiliki kemampuan untuk memberikan rekomendasi dengan tingkat akurasi yang tinggi. Namun, model Collaborative Filtering masih tergolong kurang efektif karena terdapat selisih yang cukup besar antara nilai root_mean_squared_error dan val_root_mean_squared_error, yaitu sebesar 0.2437. Hal ini menandakan bahwa model tersebut masih memerlukan peningkatan atau improvisasi lebih lanjut.

Kemungkinan penyebab rendahnya akurasi model Collaborative Filtering dapat disebabkan oleh pemilihan dataset yang tidak tepat atau karakteristik dataset yang kurang cocok untuk model tersebut. Oleh karena itu, perbaikan pada pemilihan dataset juga menjadi salah satu solusi untuk menciptakan model dengan akurasi yang lebih tinggi.

Secara keseluruhan, sistem rekomendasi yang telah dibangun dalam proyek ini hanya mampu merekomendasikan game berdasarkan aktivitas pemain pada masa lalu, dan belum sepenuhnya memenuhi standar dalam memberikan rekomendasi game berdasarkan rating yang diberikan oleh pemain lain. Diperlukan upaya lebih lanjut dalam melakukan peningkatan dan penyesuaian model agar dapat memberikan rekomendasi yang lebih akurat dan sesuai dengan preferensi pemain.

## **Referensi**
[1]	E. Blancaflor, J. M. Gomez, and S. Miguel, “Analyzing Digital Game Distribution in Gaming Industry: A Case Study,” in Proceedings of the 2nd Indian International Conference on Industrial Engineering and Operations Management Warangal, 2022, pp. 674–681.

[2]	M. J. Pakhrani, M. A. Varghese, M. S. Vyas, M. H. Purohit, and C. H. Patil, “Comparative Study of PC and Gaming Console for Video Games,” International Journal of Engineering Research & Technology (IJERT), vol. 8, no. 5, pp. 1–5, 2020, [Online]. Available: www.ijert.org

[3]	G. Gao, A. Min, and P. C. Shih, “Gendered design bias: Gender differences of in-game character choice and playing style in league of legends,” in ACM International Conference Proceeding Series, Association for Computing Machinery, Nov. 2017, pp. 307–317. doi: 10.1145/3152771.3152804.

[4]	G. Cheuque, J. Guzmán, and D. Parra, “Recommender systems for online video game platforms: The case of steam,” in The Web Conference 2019 - Companion of the World Wide Web Conference, Association for Computing Machinery, Inc, May 2019, pp. 763–771. doi: 10.1145/3308560.3316457.

[5]	G. F. Tondello and L. E. Nacke, “Validation of User Preferences and Effects of Personalized Gamification on Task Performance,” Front Comput Sci, vol. 2, no. 29, pp. 1–23, Aug. 2020, doi: 10.3389/fcomp.2020.00029.

[6] Khoiri, "Pengertian dan Cara Menghitung Root Mean Square Error (RMSE)
