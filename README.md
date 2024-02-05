# Laporan Proyek Machine Learning - Salsabila Ramadhan

## Project Overview

Dalam era digital saat ini, seseorang memiliki akses yang luas terhadap berbagai pilihan film dari berbagai genre, sutradara, dan tahun rilis. Namun, kemudahan akses ini seringkali disertai dengan tantangan dalam menavigasi pilihan konten yang besar dan beragam. Pengalaman menonton film yang memuaskan terkadang dapat terhalang oleh kesulitan dalam menemukan film yang sesuai dengan preferensi pribadi.

Pada konteks ini, sistem rekomendasi film menjadi solusi yang relevan. Sistem ini dapat membantu pengguna menemukan film-film yang serupa dengan film yang telah mereka tonton. Melalui proyek ini, pengguna dapat mencari film yang sesuai preferensi mereka. Dengan memanfaatkan teknik Content-Based Filtering, proyek ini diharapkan dapat mengatasi beberapa tantangan utama dalam menciptakan pengalaman menonton yang lebih khusus dan memuaskan bagi setiap pengguna. Proyek ini penting diselesaikan karena dapat membantu pengguna untuk memilih film sesuai preferensi pribadi mereka. Jadi tidak ada lagi kebingungan ketika menentukan film yang ingin ditonton.

## Business Understanding

### Problem Statements

- Bagaimana cara membuat sistem rekomendasi film berdasarkan genre?
- Bagaimana menghasilkan rekomendasi yang sesuai dengan preferensi pengguna?

### Goals

- Berhasil membuat sistem rekomendasi film berdasarkan genre
- Berhasil memberikan rekomendasi film yang sesuai dengan preferensi pengguna

    ### Solution statements
    - Menggunakan content based filtering untuk memberikan rekomendasi film berdasarkan genre
    - Mengevaluasi hasil rekomandasi apakah sesuai dengan preferensi pengguna atau tidak

## Data Understanding
Data yang digunakan untuk proyek ini diambil dari [Kaggle](https://www.kaggle.com/datasets/harshitshankhdhar/imdb-dataset-of-top-1000-movies-and-tv-shows/data) Berikut beberapa informasi pada dataset :

- Dataset memiliki format CSV (Comma-Seperated Values).
- Dataset yang dimiliki pada proyek ini memiliki 16 fitur
- Memiliki 1000 sampel
- Dataset memiliki 13 fitur bertipe object
- Dataset memiliki 2 fitur bertipe float64
- Dataset memiliki 1 fitur bertipe int64
- Terdapat missing value dalam dataset

Variabel-variabel pada IMDB Movies Dataset dataset adalah sebagai berikut:
- Poster_Link: Tautan poster yang digunakan imdb
- Series_Title: Judul film
- Released_Year: Tahun rilis film tersebut
- Certificate: Sertifikat yang diperoleh oleh film tersebut
- Runtime: Total waktu tayang film tersebut
- Genre: Genre film tersebut
- IMDB_Rating: Rating film di situs IMDB
- Overview: Sinopsis/ringkasan dari film
- Meta_score: Skor yang diperoleh film tersebut
- Director: Nama sutradara yang menggarap film
- Star1, Star2, Star3, Star4: Nama artis yang memainkan film
- No_of_votes: Jumlah total suara
- Gross: Uang yang diperoleh dari film tersebut

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

Jika dianilisis lebih dalam jenis genre ini bisa dijadikan one hot encoding untuk selanjutnya di hitung similarity nya. 

## Data Preparation
- Membuang missing value

    Pada tahap pre-processing data, akan dilakukan penghapusan terhadap nilai yang nulll. Hal ini dilakukan agar tidak mempengaruhi proses rekomendasi. Karena jika terdapat missing value dapat menyebabkan gangguan dalam proses rekomendasi, mengingat nilai yang tidak lengkap dapat menghasilkan hasil yang tidak akurat. Penghapusan missing value dilakukan untuk semua fitur. Setelah dilakukan penghapusan sample data berkurang menjadi 714. Ini merupakan penurunan yang sangat besar dan dapat menunjukkan juga bahwa data memiliki banyak missing value.

- Menghapus data duplikat

    Penghapusan data duplikat dilakukan agar mengurangi risiko distorsi atau bias dalam analisis dan model rekomendasi. Jika terdapat entri duplikat dalam dataset, dapat menyebabkan ketidakseimbangan dalam bobot atau frekuensi munculnya suatu item atau fitur, memberikan dampak yang tidak seimbang pada hasil rekomendasi. Dampak dari penghapusan data duplikat ini adalah dapat mencegah sistem menghasilkan data film yang sama.

- Menghapus kolom yang tidak diperlukan

    Penghapusan kolom yang tidak diperlukan dilakukan untuk mempermudah proses pengelolaan data. Kolom yang dihapus diantaranya yaitu Poster_Link, Overview, Gross, Released_Year, Runtime, Meta_score, No_of_Votes dan Certificate. Alasan mengapa kolom tersebut dihapus adalah karena kolom tersebut tidak diperlukan dalam membuat sistem rekomendasi. Serta agar dapat fokus pada kolom-kolom yang penting.

## Modeling
### One-hot Encoding
Pada tahap ini dilakukan proses konversi fitur genre menjadi representasi biner menggunakan metode one-hot encoding. One-hot encoding bertujuan untuk mengubah variabel kategorikal menjadi vektor biner, di mana setiap kategori direpresentasikan sebagai suatu kolom dengan nilai biner 1 atau 0. Hasil dari one-hot encoding dapat dilihat digambar berikut:

![one-hot-encoding](https://github.com/salsabilar311/Movie-Recommendation-System/blob/7c8b61e85a4b9257d2dce5320b58d9e201f93944/one-hot-encoding.png?raw=true)

Dapat dilihat bahwa setiap film memiliki lebih dari 1 genre. Ini menunjukkan bahwa 1 film bisa memiliki berbagai macam genre. Keberadaan multiple genres memberikan informasi lebih detail tentang karakteristik film, dan dapat membantu dalam meningkatkan ketepatan dan keberagaman rekomendasi. Misalnya, jika seorang pengguna menikmati film dengan kombinasi "Action" dan "Adventure," model rekomendasi dapat memberikan saran yang lebih spesifik berdasarkan preferensi yang lebih kompleks tersebut.

### Cosine Similarity

Pada tahap ini dilakukan proses penghitungan derajat kesamaan antar genre dengan teknik cosine similarity. Sample dari hasil dapat dilihat pada gambar dibawah ini.

![cosine similarity](https://github.com/salsabilar311/Movie-Recommendation-System/blob/7c8b61e85a4b9257d2dce5320b58d9e201f93944/cosine%20similarity.png?raw=true)

Dapat dilihat pada gambar di atas bahwa antar film dengan film lainnya memimiliki derajat kesamaan antara 0 sampai 1. Nilai 0 menunjukkan bahwa film tidak memiliki kemiripan. Dan 1 menunjukkan bahwa film memiliki kemiripan yang kuat. 

### Hasil rekomendasi

![hasil rekomendasi](https://github.com/salsabilar311/Movie-Recommendation-System/blob/7c8b61e85a4b9257d2dce5320b58d9e201f93944/hasil%20rekomendasi.png)

Dapat dilihat dari gambar di atas bahwa ketika memasukkan judul Titanic sistem menghasilkan 5 rekomendasi film yang bergenre drama dan romance. Ini mmenunjukkan bahwa sistem rekomendasi dapat memahami konteks dan karakteristik film yang diinginkan oleh pengguna, dalam hal ini, genre "drama" dan "romance".

## Evaluation

Metrik evaluasi yang digunakan adalah precision. Precision dipilih menjadi metriks evaluasi karena menunjukkan seberapa banyak dari item yang direkomendasikan yang benar-benar disukai oleh pengguna. Pilihan yang tepat untuk model ini untuk mengukur film yang benar-benar disukai oleh pengguna. Untuk menghitung precision adalah sebagai berikut.

$Precision = \frac{\text{Jumlah item relevan yang direkomendasikan}}{\text{Total item yang direkomendasikan}} \$

$Precision = \frac{\text{5}}{\text{5}} \ = 100$

Dari hasil rekomendasi sebelumnya, diketahui bahwa Titanic masuk ke dalam kategori Drama, Romance. Dan dapat dilihat dari 5 film yang direkomendasikan, kelimanya memiliki genre Drama, Romance. Artinya, precision yang didapat sebesar 5/5 atau 100%. Ini menunjukkan hasil yang sangat bagus. Hasil ini menandakan bahwa sistem telah berhasil memberikan rekomendasi yang kuat.

Hasil dari proyek ini dilihat berdasarkan:

- Konteks data: Data yang dimiliki telah berhasil menghasilkan sistem rekomendasi film yang akurat.
- Problem statement: Hasil dari proyek ini telah berhasil untuk menjawab pertanyaan yang ada di problem statement. Sistem ini dapat memberikan rekomendasi film berdasarkan genre dengan akurat.
- Goals: Hasil dari proyek ini telah berhasil menghasilkan rekomendasi yang tepat sesuai dengan preferensi pengguna.

Kesimpulannya, proyek ini telah memberikan dampak positif dan berhasil mencapai tujuan yang telah ditetapkan. Dengan memanfaatkan data yang ada, sistem rekomendasi film yang akurat telah berhasil dikembangkan. Problem statement yang dihadapi berhasil diatasi, dan sistem mampu memberikan rekomendasi film dengan tingkat akurasi yang baik, terutama dalam menanggapi preferensi pengguna terkait genre. Pencapaian tujuan proyek menunjukkan bahwa model rekomendasi yang dikembangkan dapat secara efektif memahami preferensi pengguna dan memberikan rekomendasi yang relevan. Keberhasilan ini memperkuat nilai sistem rekomendasi dalam meningkatkan pengalaman menonton film pengguna dengan menyediakan rekomendasi yang sesuai dan memenuhi ekspektasi mereka.
