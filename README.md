# Laporan Proyek Machine Learning - Salsabila Ramadhan

## Project Overview

Dalam era digital saat ini, seseorang memiliki akses yang luas terhadap berbagai pilihan film dari berbagai genre, sutradara, dan tahun rilis. Namun, kemudahan akses ini seringkali disertai dengan tantangan dalam menavigasi pilihan konten yang besar dan beragam. Pengalaman menonton film yang memuaskan terkadang dapat terhalang oleh kesulitan dalam menemukan film yang sesuai dengan preferensi pribadi.

Pada konteks ini, sistem rekomendasi film menjadi solusi yang relevan. Seperti yang dilansir dari sebuah studi yang dilakukan oleh Lemantara J. bahwa "98,4% orang merasa terbantu dengan adanya sistem rekomendasi film ini dan sebesar 93,5% berminat menggunakan sistem rekomendasi film ini untuk merekomendasikan judul film yang hendak ditonton" [1]. Ini menunjukkan bahwa sistem rekomendasi film telah membuktikan nilai dan penerimaannya dalam meningkatkan pengalaman pengguna serta membantu dalam memilih judul film yang sesuai dengan preferensi individu. Sistem ini dapat membantu pengguna menemukan film-film yang serupa dengan film yang telah mereka tonton. Melalui proyek ini, pengguna dapat mencari film yang sesuai preferensi mereka. Dengan memanfaatkan teknik Content-Based Filtering, proyek ini diharapkan dapat mengatasi beberapa tantangan utama dalam menciptakan pengalaman menonton yang lebih khusus dan memuaskan bagi setiap pengguna. 
Proyek ini memiliki beberapa manfaat signifikan terhadap pengalaman pengguna dan potensi penerapan dalam industri film. Berikut adalah beberapa manfaat tersebut:
### Manfaat terhadap pengalaman pengguna

- Personalisasi Pengalaman: Rekomendasi film memungkinkan pengguna untuk mendapatkan rekomendasi yang disesuaikan dengan preferensi mereka. Ini membantu meningkatkan personalisasi pengalaman pengguna, membuatnya lebih relevan dan memuaskan. Pengguna dapat kepuasan tersendiri ketika mendapatkan rekomendasi film yang sesuai dengan preferensi mereka.

- Eksplorasi Konten Baru: Dengan algoritma rekomendasi yang canggih, pengguna dapat menemukan film-film baru yang mungkin tidak akan mereka temui secara manual. Ini membuka peluang untuk mengeksplorasi berbagai genre dan karya seni.

### Potensi penerapan dalam industri film

Dengana adanya sistem rekomendasi yang efektif, informasi yang diperoleh dari sistem rekomendasi dapat membantu industri film mengidentifikasi tren dan preferensi baru. Ini dapat merangsang para sutradara dalam menciptakan sebuah karya yang lebih sesuai dengan selera penonton.

Oleh karena itu proyek ini penting diselesaikan karena dapat membantu pengguna untuk memilih film sesuai preferensi pribadi mereka. Jadi tidak ada lagi kebingungan ketika menentukan film yang ingin ditonton.

## Business Understanding

Implementasi sistem rekomendasi dalam industri film memiliki dampak yang signifikan, baik terhadap pengalaman pengguna maupun industri film secara keseluruhan. Berikut adalah beberapa dampak utama:
### Dampak terhadap pengalaman pengguna 
- Sistem rekomendasi memungkinkan personalisasi konten, memastikan bahwa pengguna menerima rekomendasi yang sesuai dengan preferensi dan sejarah penonton mereka. Ini meningkatkan kemungkinan pengguna menemukan konten yang menarik bagi mereka.
- Pengguna tidak perlu menghabiskan waktu berlebihan untuk mencari film baru yang sesuai dengan selera mereka. Sistem rekomendasi membantu mengurangi kerumitan dan meningkatkan efisiensi dalam menemukan konten yang relevan.

### Dampak Terhadap Industri Film
- Film independen atau karya yang kurang dikenal dapat mendapatkan eksposur lebih besar melalui rekomendasi. Sistem rekomendasi dapat membuka peluang baru bagi film-film ini untuk menjangkau khalayak yang lebih luas.
- Dengan rekomendasi yang baik, platform dapat memperluas katalog film mereka dengan menyertakan film-film yang mungkin tidak populer tetapi sesuai dengan preferensi sebagian besar penonton.

### Problem Statements

- Bagaimana cara membuat sistem rekomendasi film berdasarkan genre?
- Bagaimana menghasilkan rekomendasi yang sesuai dengan preferensi pengguna?

### Goals

- Membuat sistem rekomendasi film berdasarkan genre
- Memberikan rekomendasi film yang sesuai dengan preferensi pengguna. Preferensi disini mengacu pada genre. Kenapa genre dipilih adalah karena genre film adalah cara yang sederhana dan mudah dimengerti untuk menggambarkan konten suatu film. Dengan memfokuskan rekomendasi pada genre, pengguna dapat dengan cepat memahami dan mengidentifikasi jenis film yang mereka sukai.

    ### Solution statements
    - Menggunakan content based filtering untuk memberikan rekomendasi film berdasarkan genre
    - Mengevaluasi hasil rekomandasi apakah menggunakan metriks evaluasi yaitu recall. Jika recall yang dihasilkan lebih dari 90% maka model telah berhasil memberikan rekomendasi yang akurat.
    - Untuk mencapai goals yang telah diterapkan maka perlu membuat sebuah model content-based filtering yang dapat memberikan rekomendasi film. Adapun langkah langkah yang perlu ditempuh adalah pertama mencari derajat kesamaan antar setiap film. Lalu membuat fungsi yang mengembalikkan daftar rekomendasi film diurutkan berdasarkan tingkat kesamaan.

## Data Understanding
Data yang digunakan untuk proyek ini diambil dari [Kaggle](https://www.kaggle.com/datasets/harshitshankhdhar/imdb-dataset-of-top-1000-movies-and-tv-shows/data) Berikut beberapa informasi pada dataset :

- Dataset memiliki format CSV (Comma-Seperated Values).
- Dataset yang dimiliki pada proyek ini memiliki 16 fitur
- Memiliki 1000 sampel
- Dataset memiliki 13 fitur bertipe object
- Dataset memiliki 2 fitur bertipe float64
- Dataset memiliki 1 fitur bertipe int64
- Terdapat missing value dalam dataset
- Tidak terdapat data duplikat dalam dataset
- Distribusi genre film yang merata dan memiliki 21 genre
- Genre tersebut diantaranya yaitu 'Action', 'Adventure', 'Animation', 'Biography', 'Comedy', 'Crime',
       'Drama', 'Family', 'Fantasy', 'Film-Noir', 'History', 'Horror', 'Music',
       'Musical', 'Mystery', 'Romance', 'Sci-Fi', 'Sport', 'Thriller', 'War',
       'Western'.

Variabel-variabel pada IMDB Movies Dataset dataset adalah sebagai berikut:
- Poster_Link: Tautan poster yang digunakan imdb
- Series_Title: Judul film
- Released_Year: Tahun rilis film tersebut. Film yang ada di dataset ini adalah film yang rilis pada rentang waktu 1920-2019
- Certificate: Sertifikat yang diperoleh oleh film tersebut. Sertifikat pada film biasanya merujuk pada rating atau sertifikat usia yang menunjukkan seberapa cocok suatu film untuk penonton berdasarkan usia mereka. Contoh rating atau sertifikat usia termasuk, A (film ini umumnya diperuntukkan untuk penonton dewasa), UA (Universal Adult), U (Universal), PG-13 (Parents Strongly Cautioned), R (Restricted), PG (Parental Guidance), G (General Audience), Passed (film lulus sensor), TV-14 (konten ini mungkin cocok untuk penonton usia 14 tahun ke atas ketika ditayangkan di televisi), 16 (film ini cocok untuk penonton yang berusia 16 tahun ke atas), TV-MA (konten ini mungkin hanya cocok untuk penonton dewasa), Unrated (film ini mungkin tidak memiliki rating usia resmi), GP (General Patronage), Approved (Film ini mungkin telah disetujui oleh otoritas sensor atau badan penilaian setempat), TV-PG (konten ini mungkin memerlukan panduan orang tua dan dapat tidak sesuai untuk anak-anak di bawah 7 tahun) dan U/A (Universal with Adult).
- Runtime: Total waktu tayang film tersebut
- Genre: Genre film tersebut
- IMDB_Rating: Rating film di situs IMDB
- Overview: Sinopsis/ringkasan dari film
- Meta_score: Skor yang diperoleh film tersebut
- Director: Nama sutradara yang menggarap film
- Star1, Star2, Star3, Star4: Nama artis yang memainkan film
- No_of_votes: Jumlah total suara yang didapatkan sebuah film ketika pemilihan pada ajang penghargaan
- Gross: Uang yang diperoleh dari film tersebut

Sebaran fitur IMDB_Rating memiliki nilai sebagai berikut:

Tabel 1. Distribusi data pada fitur IMDB_Rating
|Distribusi data| Nilai|
|:----:|:----:|
|mean|7.949300|
|std|0.275491|
|min|7.600000|
|25%|7.700000|
|50%|7.900000|
|75%|8.100000|
|max|9.300000|

Tabel 1 diatas dapat memberikan informasi mengenai sebaran data fitur IMDB_Rating. Dapat dilihat bahwa sebagian besar data berada dalam kisaran antara kuartil pertama (7.7) dan kuartil ketiga (8.1), dengan sebagian kecil data yang mungkin ekstrem di atas atau di bawah kisaran tersebut. Rata-rata dan median yang relatif dekat menunjukkan bahwa distribusi data cenderung simetris. Deviasi standar yang tidak terlalu tinggi menunjukkan bahwa data memiliki variasi yang cukup terkendali.

Untuk genre dari film memiliki kategori seperti ini.
```Jenis Genre:  ['Drama' 'Crime, Drama' 'Action, Crime, Drama' 'Action, Adventure, Drama'
 'Biography, Drama, History' 'Action, Adventure, Sci-Fi' 'Drama, Romance'
 'Western' 'Action, Sci-Fi' 'Biography, Crime, Drama'
 'Action, Adventure, Fantasy' 'Comedy, Drama, Thriller'
 'Adventure, Drama, Sci-Fi' 'Animation, Adventure, Family' 'Drama, War'
 'Crime, Drama, Fantasy' 'Comedy, Drama, Romance' 'Crime, Drama, Mystery'
 'Crime, Drama, Thriller' 'Action, Drama, Mystery'
 'Drama, Family, Fantasy' 'Drama, Music' 'Biography, Comedy, Drama'
 'Drama, Mystery, Sci-Fi' 'Biography, Drama, Music'
 'Crime, Mystery, Thriller' 'Animation, Adventure, Drama'
 'Animation, Drama, War' 'Adventure, Comedy, Sci-Fi'
 'Horror, Mystery, Thriller' 'Drama, Romance, War' 'Comedy, Drama, Family'
 'Animation, Drama, Fantasy' 'Action, Biography, Drama'
 'Animation, Action, Adventure' 'Drama, Western' 'Action, Adventure'
 'Comedy, Drama' 'Drama, Family' 'Drama, Mystery, Thriller'
 'Mystery, Thriller' 'Drama, Horror' 'Drama, Mystery, War'
 'Horror, Sci-Fi' 'Drama, Musical' 'Comedy' 'Drama, Film-Noir'
 'Comedy, Drama, War' 'Drama, Thriller, War' 'Drama, Fantasy, Horror'
 'Crime, Drama, Music' 'Adventure, Drama, War' 'Drama, Romance, Sci-Fi'
 'Comedy, Romance' 'Comedy, Crime' 'Drama, Family, Sport'
 'Animation, Adventure, Comedy' 'Adventure, Drama, Thriller'
 'Comedy, Crime, Drama' 'Crime, Drama, Sci-Fi' 'Adventure, Sci-Fi'
 'Adventure, Biography, Drama' 'Adventure, Mystery, Thriller'
 'Mystery, Romance, Thriller' 'Comedy, Musical, Romance'
 'Crime, Drama, Film-Noir' 'Drama, Mystery' 'Drama, Sci-Fi'
 'Action, Drama, War' 'Action, Drama' 'Adventure, Comedy, Drama'
 'Biography, Drama, Sport' 'Action, Comedy, Crime'
 'Action, Biography, Crime' 'Drama, Mystery, Romance'
 'Action, Drama, Sport' 'Drama, Fantasy, War' 'Action, Drama, Sci-Fi'
 'Biography, Drama' 'Action, Comedy, Romance' 'Animation, Family, Fantasy'
 'Action, Thriller' 'Action, Adventure, Comedy'
 'Adventure, Comedy, Fantasy' 'Adventure, Drama, History'
 'Action, Drama, Thriller' 'Comedy, Music, Romance'
 'Drama, Fantasy, History' 'Crime, Thriller' 'Adventure, Drama, Western'
 'Comedy, War' 'Drama, Thriller' 'Animation, Drama, Family'
 'Drama, Romance, Thriller' 'Comedy, Drama, Musical'
 'Comedy, Drama, Fantasy' 'Adventure, Comedy, Crime'
 'Adventure, Drama, Fantasy' 'Biography, Drama, Family'
 'Animation, Comedy, Drama' 'Drama, Sport' 'Animation, Action, Drama'
 'Adventure, Drama, Musical' 'Drama, Music, Romance'
 'Comedy, Crime, Romance' 'Comedy, Crime, Sport' 'Drama, History, Romance'
 'Adventure, Drama' 'Animation, Adventure, Fantasy'
 'Horror, Mystery, Sci-Fi' 'Drama, Fantasy, Music'
 'Action, Sci-Fi, Thriller' 'Drama, Fantasy' 'Drama, Horror, Thriller'
 'Drama, History' 'Film-Noir, Mystery, Thriller'
 'Fantasy, Horror, Mystery' 'Action, Crime, Thriller'
 'Comedy, Drama, Music' 'Biography, Drama, Thriller'
 'Animation, Biography, Drama' 'Action, Mystery, Thriller'
 'Crime, Drama, Romance' 'Action, Adventure, Thriller'
 'Crime, Drama, Musical' 'Animation, Crime, Mystery'
 'Action, Crime, Comedy' 'Mystery, Sci-Fi, Thriller'
 'Animation, Action, Crime' 'Comedy, Fantasy, Romance'
 'Drama, History, Thriller' 'Animation, Action, Sci-Fi'
 'Adventure, Family, Fantasy' 'Drama, Fantasy, Romance'
 'Drama, History, War' 'Adventure, Thriller' 'Horror'
 'Drama, Family, Musical' 'Action, Drama, Western' 'Crime, Drama, Horror'
 'Drama, Film-Noir, Mystery' 'Comedy, Crime, Thriller'
 'Film-Noir, Mystery' 'Comedy, Crime, Mystery' 'Drama, Fantasy, Mystery'
 'Comedy, Horror' 'Action, Adventure, History' 'Drama, Music, Mystery'
 'Comedy, Music' 'Comedy, Family' 'Drama, Music, Musical'
 'Action, Adventure, Horror' 'Action, Adventure, Biography'
 'Biography, Drama, War' 'Action, Adventure, Western' 'Horror, Thriller'
 'Comedy, Mystery, Romance' 'Drama, Thriller, Western'
 'Crime, Film-Noir, Thriller' 'Drama, Film-Noir, Romance'
 'Crime, Film-Noir, Mystery' 'Action, Adventure, Romance'
 'Comedy, Music, Musical' 'Adventure, Horror, Sci-Fi' 'Fantasy, Horror'
 'Action, Drama, History' 'Adventure, Comedy, Family'
 'Animation, Biography, Crime' 'Adventure, Biography, Crime'
 'Adventure, Fantasy' 'Drama, History, Mystery' 'Action, Comedy, Mystery'
 'Adventure, Drama, Romance' 'Drama, Sci-Fi, Thriller'
 'Crime, Drama, History' 'Action, Comedy, Fantasy' 'Family, Sci-Fi'
 'Adventure, History, War' 'Animation, Sci-Fi' 'Family, Fantasy, Musical'
 'Thriller' 'Comedy, Family, Fantasy' 'Adventure, Comedy, Film-Noir'
 'Film-Noir, Thriller' 'Comedy, Family, Romance' 'Drama, Horror, Sci-Fi'
 'Comedy, Musical, War' 'Biography, Drama, Romance'
 'Drama, History, Music' 'Animation, Action, Fantasy'
 'Animation, Comedy, Fantasy' 'Comedy, Western' 'Action, Adventure, War'
 'Drama, Horror, Mystery' 'Animation, Comedy, Crime'
 'Action, Adventure, Crime' 'Action, Adventure, Mystery'
 'Action, Adventure, Family' 'Action, Crime, Mystery'
 'Animation, Drama, Romance' 'Drama, War, Western'
 'Adventure, Comedy, War']
```

Dari kategori tersebut dapat dilihat bahwa jenis genre dapat memiliki banyak kombinasi genre. Tidak hanya kombinasi genre, namun jika merujuk pada data diatas terdapat juga film yang hanya memiliki 1 genre. Contohnya film The Shawshank Redemption yang hanya memiliki 1 genre yaitu Drama. Jika dianilisis lebih dalam jenis genre ini bisa dijadikan one hot encoding untuk selanjutnya di hitung similarity nya. 

## Data Preparation
- Membuang missing value

    Pada tahap pre-processing data, akan dilakukan penghapusan terhadap nilai yang nulll. Hal ini dilakukan agar tidak mempengaruhi proses rekomendasi. Karena jika terdapat missing value dapat menyebabkan gangguan dalam proses rekomendasi, mengingat nilai yang tidak lengkap dapat menghasilkan hasil yang tidak akurat. Penghapusan missing value dilakukan untuk semua fitur. 

- Menghapus data duplikat

    Penghapusan data duplikat dilakukan agar mengurangi risiko distorsi atau bias dalam analisis dan model rekomendasi. Jika terdapat entri duplikat dalam dataset, dapat menyebabkan ketidakseimbangan dalam bobot atau frekuensi munculnya suatu item atau fitur, memberikan dampak yang tidak seimbang pada hasil rekomendasi. Dampak dari penghapusan data duplikat ini adalah dapat mencegah sistem menghasilkan data film yang sama.

- Menghapus kolom yang tidak diperlukan

    Penghapusan kolom yang tidak diperlukan dilakukan untuk mempermudah proses pengelolaan data. Kolom yang dihapus diantaranya yaitu Poster_Link, Overview, Gross, Released_Year, Runtime, Meta_score, No_of_Votes dan Certificate. Alasan mengapa kolom tersebut dihapus adalah karena kolom tersebut tidak diperlukan dalam membuat sistem rekomendasi. Serta agar dapat fokus pada kolom-kolom yang penting. Berikut merupakan alasan rinci dari setiap kolom

    - Poster_Link: Dilakukan penghapusan karena kolom ini berisi link poster dari film. Jadi link poster tidak dibutuhkan untuk membuat sistem rekomendasi film berdasarkan genre.
    - Overview: Dilakukan penghapusan karena kolom ini berisi sinopsis dari film. Jadi sinopsis tidak dibutuhkan untuk membuat sistem rekomendasi film berdasarkan genre.
    - Gross: Dilakukan penghapusan karena kolom ini berisi uang yang diperoleh dari film. Jadi jumlah uang juga tidak dibutuhkan untuk membuat sistem rekomendasi film berdasarkan genre.
    - Released_Year: Dilakukan penghapusan karena kolom ini berisi tahun liris film. Jadi tahun rilis tidak dibutuhkan untuk membuat sistem rekomendasi film berdasarkan genre.
    - Runtime: Dilakukan penghapusan karena kolom ini berisi durasi penayangan film. Jadi durasi penayangan tidak dibutuhkan untuk membuat sistem rekomendasi film berdasarkan genre.
    - Meta_score: Dilakukan penghapusan karena kolom ini berisi skor yang diperoleh film. Jadi skor tidak dibutuhkan untuk membuat sistem rekomendasi film berdasarkan genre.
    - No_of_Votes: Dilakukan penghapusan karena kolom ini berisi jumlah total suara dari film. Jadi total suara tidak dibutuhkan untuk membuat sistem rekomendasi film berdasarkan genre.
    - Certificate: Dilakukan penghapusan karena kolom ini berisi sertifikat yang diperoleh film. Jadi sertifikat tidak dibutuhkan untuk membuat sistem rekomendasi film berdasarkan genre.

- One-hot Encoding

    Pada tahap ini dilakukan proses konversi fitur genre menjadi representasi biner menggunakan metode one-hot encoding. One-hot encoding bertujuan untuk mengubah variabel kategorikal menjadi vektor biner, di mana setiap kategori direpresentasikan sebagai suatu kolom dengan nilai biner 1 atau 0. Hasil dari one-hot encoding dapat dilihat ditabel berikut:

  Tabel 2. Hasil one-hot encoding

    | Series_Title | Action | Comedy | Crime | Drama|
    |:-----------:|:----------:|:---------:|:---------:|:---------:|
    | The Shawshank Redemption| 0  | 0  | 0  | 1  |
    | The Godfather| 0  | 0  | 1  | 1  |
    | The Dark Knight| 1  | 0  | 1  | 1  |

    Dapat dilihat bahwa setiap film memiliki lebih dari 1 genre. Ini menunjukkan bahwa 1 film bisa memiliki berbagai macam genre. Keberadaan multiple genres memberikan informasi lebih detail tentang karakteristik film, dan dapat membantu dalam meningkatkan ketepatan dan keberagaman rekomendasi. Misalnya, jika seorang pengguna menikmati film dengan kombinasi "Action" dan "Crime," model rekomendasi dapat memberikan saran yang lebih spesifik berdasarkan preferensi yang lebih kompleks tersebut. Keuntungan dari one-hot encoding untuk sistem rekomendasi ini adalah one-hot encoding sederhana dan efisien untuk mengubah data kategorikal menjadi bentuk yang dapat diproses oleh algoritma machine learning. Cocok untuk memproses genre yang merupakan data kategorikal. Kelemahan dari one-hot encoding untuk sistem rekomendasi ini adalah jika terdapat banyak kategori, one-hot encoding dapat menghasilkan vektor dengan dimensi tinggi, yang bisa menyebabkan masalah "curse of dimensionality" dan membutuhkan penyimpanan dan pemrosesan yang lebih besar. Oleh karena itu hanya genre yang di proses menggunakan one-hot encoding, karena genre memiliki nilai yang terbatas.

## Modeling
### Cosine Similarity

Pada tahap ini dilakukan proses penghitungan derajat kesamaan antar genre dengan teknik cosine similarity. Sample dari hasil dapat dilihat pada tabel dibawah ini.

Tabel 3. Hasil cosine similarity

|Series_Title |The Conversation |What Ever Happened to Baby Jane?|The Dark Knight|
|:-----------:|:----------:|:---------:|:---------:|
| The Bourne Ultimatum| 0.666667 |0.333333| 0.333333|
| Life of Pi| 0.333333 |0.333333| 0.333333|
| The Innocents	|0.000000 |0.577350	| 0.000000|

Dapat dilihat pada tabel di atas bahwa antar film dengan film lainnya memimiliki derajat kesamaan antara 0 sampai 1. Nilai 0 menunjukkan bahwa film tidak memiliki kemiripan. Dan nilai yang semakin mendekati 1 menunjukkan bahwa film memiliki kemiripan yang kuat. Alasan pemilihan cosine similarity sebagai metode perbandingan dalam content-based filtering adalah karena mudah diterapkan pada fitur yang berbentuk teks. Karena fitur yang digunakan untuk memberikan rekomendasi adalah series_title dan genre yang merupakan fitur bertipe teks atau string. Maka cosine similarity cocok untuk digunakan dalam mengukur kesamaan antara vektor representasi teks dengan baik. Ini lah mengapa cosine similarity dipilih dari algoritma lainnya untuk pendekatan content-based filtering. Keuntungan cosine similarity terhadap sistem rekomendasi ini adalah perhitungannya yang efisien, terutama dalam situasi dengan data vektor yang besar. Cocok dengan fitur genre karena memiliki 21 tipe. Kelemahan cosine similarity terhadap sistem rekomendasi ini adalah cosine similarity hanya mempertimbangkan arah, sehingga sensitif terhadap pemilihan fitur. Jika fitur yang dipilih tidak memahami dengan baik preferensi pengguna, hasilnya bisa kurang akurat.

### Hasil rekomendasi

Setelah menghitung derajat kesamaan pada setiap film, langkah selanjutnya adalah membuat fungsi untuk menghasilkan rekomendasi film. Parameter yang di set pada function diantaranya sebagai berikut:

- ```nama_film``` : Nama film yang akan dicari rekomendasi nya
- ```Similarity_data``` : Dataframe yang berisi data similarity yang telah di definisikan sebelumnya
- ```Items``` : Nama dan fitur yang digunakan untuk mendefinisikan kemiripan, dalam hal ini adalah ‘Series_Title’ dan ‘Genre’
- ```k``` : Banyak rekomendasi yang ingin diberikan. Pada proyek ini k di isi 5. Jadi hanya mengambil 5 rekomendasi teratas.

Fungsi ini bekerja dengan cara mengambil data dengan menggunakan ```argpartition``` untuk mengambil sejumlah nilai k tertinggi dari similarity data. Setelah itu mengambil data dengan similarity terbesar dari index yang ada. Data tersebut lalu dimasukkan ke variabel ```closest```. 
Untuk menghindari munculnya nama film yang dicari dalam daftar rekomendasi maka, nama film yang dicari dihapus dari variabel ```closest```. 
Nilai yang dikembalikan dari function ini adalah dataframe yang memiliki daftar film yang memiliki kemiripan yang tinggi. Fungsi ini mengacu pada materi Model Development dengan Content Based Filtering di course Machine Learning Terapan di dicoding. Dengan beberapa penyesuaian parameter fungsi ini digunakan untuk merekomendasikan film.

Tabel 4. Hasil rekomendasi dari film Titanic.

|Series_Title| Genre|
|:----------:|:----:|
|Call Me by Your Name|Drama, Romance|
|Fa yeung nin wah|Drama, Romance|
|The Bridges of Madison County|	Drama, Romance|
|Before Midnight|Drama, Romance|
|Brokeback Mountain|Drama, Romance|

Dapat dilihat dari tabel 4 di atas bahwa ketika memasukkan judul Titanic sistem menghasilkan 5 rekomendasi film yang bergenre drama dan romance. Ini mmenunjukkan bahwa sistem rekomendasi dapat memahami konteks dan karakteristik film yang diinginkan oleh pengguna, dalam hal ini, genre "drama" dan "romance".

## Evaluation

Metrik evaluasi yang digunakan adalah precision. Precision dipilih menjadi metriks evaluasi karena menunjukkan seberapa banyak dari item yang direkomendasikan yang benar-benar disukai oleh pengguna. Pilihan yang tepat untuk model ini untuk mengukur film yang benar-benar disukai oleh pengguna. Untuk menghitung precision adalah sebagai berikut.

$Precision = \frac{\text{Jumlah item relevan yang direkomendasikan}}{\text{Total item yang direkomendasikan}} \$

$Precision = \frac{\text{5}}{\text{5}} \ = 100$

Dari hasil rekomendasi sebelumnya, diketahui bahwa Titanic masuk ke dalam kategori Drama, Romance. Dan dapat dilihat dari 5 film yang direkomendasikan, kelimanya memiliki genre Drama, Romance. Artinya, precision yang didapat sebesar 5/5 atau 100%. Ini menunjukkan hasil yang sangat bagus. Hasil ini menandakan bahwa sistem telah berhasil memberikan rekomendasi yang kuat. Meskipun nilai precision yang tinggi (100%) terlihat bagus, tetapi perlu dilakukan analisis lebih lanjut untuk memahami potensi kelemahan atau bias dari model rekomendasi tersebut. Salah satu aspek yang perlu diperhatikan adalah resiko model overfitting. Model mungkin terlalu "memahami" preferensi pengguna tertentu, bahkan mungkin ke preferensi yang sangat spesifik. Ini bisa mengarah pada overfitting di mana model tidak dapat menggeneralisasi dengan baik untuk pengguna lain yang memiliki preferensi yang lebih beragam. Model yang overfitting dapat menyebabkan model belajar dengan sangat baik sehingga ketika ada data yang baru model cenderung tidak belajar dan tidak bisa memahami pola yang ada. Untuk mendapatkan pemahaman yang baik terhadap masalah ini perlu dilakukan analisis lebih lanjut.

Hasil dari proyek ini dilihat berdasarkan:

- Konteks data: Data yang dimiliki telah berhasil menghasilkan sistem rekomendasi film yang akurat.
- Problem statement: Hasil dari proyek ini telah berhasil untuk menjawab pertanyaan yang ada di problem statement. Sistem ini dapat memberikan rekomendasi film berdasarkan genre dengan akurat.
- Goals: Hasil dari proyek ini telah berhasil menghasilkan rekomendasi yang tepat sesuai dengan preferensi pengguna.

Kesimpulannya, proyek ini telah memberikan dampak positif dan berhasil mencapai tujuan yang telah ditetapkan. Dengan memanfaatkan data yang ada, sistem rekomendasi film yang akurat telah berhasil dikembangkan. Problem statement yang dihadapi berhasil diatasi, dan sistem mampu memberikan rekomendasi film dengan tingkat akurasi yang baik, terutama dalam menanggapi preferensi pengguna terkait genre. Pencapaian tujuan proyek menunjukkan bahwa model rekomendasi yang dikembangkan dapat secara efektif memahami preferensi pengguna dan memberikan rekomendasi yang relevan. Keberhasilan ini memperkuat nilai sistem rekomendasi dalam meningkatkan pengalaman menonton film pengguna dengan menyediakan rekomendasi yang sesuai dan memenuhi ekspektasi mereka.

## Referensi
[1]    J. Lemantara, "Sistem Pendukung Keputusan Penentuan Film Berdasarkan dengan Metode Weighted Product," Jurnal Riset Sistem Informasi Dan Teknik Informatika (JURASIK), vol. 8, no. 1, pp. 1-14, 2023. 
