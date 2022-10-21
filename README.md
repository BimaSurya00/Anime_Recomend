# Laporan Proyek Machine Learning - Bima Surya Nurwahid

## Domain Proyek

Domain yang dipilih pada proyek ini adalah Anime, sistem rekomendasi untuk menentukan dan filtering Anime.

## Latar Belakang
Anime sangat populer dikalangan remaja saat ini bahkan sekarang bisa dikatakan semua umur cocok dengan Anime dengan sesuai genrenya, Anime adalah gambaran yang bisa digambar menggunakan tulis tangan ataupun teknologi komputer. Anime sangat populer di dalam dan di luar Jepang sehingga banyak situs atau sistem steaming online yang memungkinkan pengguna untuk menonton anime dimana saja. Namun, jumlah anime yang beredar saat ini sangatlah banyak dan juga membuat penikmatnya kebingungan saat akan memilih genre atau selera anime apa yang ingin ditonton. 

oleh karena itu proyek ini dibuat karena tingginya tingkat menonton anime di Indonesia atau bahkan dunia, dimana para penonton akan dapat mudah menemui anime yang bergenre dengan keinginan mereka sehingga mereka akan menonton rekomendasi yang model berikan dan itu akan sangat membantu baik untuk perusahaan anime dan juga penikmatnya.

## Business Understanding

### Problem Statements

Berdasarkan Latar belakang diatas bisa kita simpulkan permasalahan dan goal yang akan dicapai pada proyek ini:

- Bagaimana cara analisis dan pemrosesan data sehingga bisa digunakan pada model rekomendasi?
- Bagaimana sistem memberikan sejumlah rekomendasi anime yang diberikan model oleh pengguna?

### Goals

Goals dari proyek ini :
- Mendapat data yang sudah dianalisis dan bisa digunakan pada model rekomendasi.
- Merekomendasikan anime kepada user oleh sistem rekomendasi menggunakan teknik content-based filtering.

### Solution statements
Berikut merupakan solusi yang bisa dilakukan guna memenuhi goals:

- Melakukan Eksploratory data dimana didalamnya termasuk seperti, analisa, eksplorasi, processing data, handling missing value, dengan visualisasi data lebih mudah dilihat dan dimengerti, berikut analisa yang bisa dilakukan:

 * Menangalisis pesebaran data pada kolom.
 * Handling Missing value pada data.
 * Membuat sistem rekomendasi yang bisa memberikan rekomendasi anime kepada user.
- Menyiapkan data agar bisa digunakan dalam membangun model

## Data Understanding
Dataset yang saya gunakan adalah Movie Recommendation yang saya ambil dari
[Kaggle](https://www.kaggle.com/datasets/CooperUnion/anime-recommendations-database).

Pada dataset ini memiliki **12294** entries dan **7** kolom dimana didalamnya seperti berikut:

Dataset yang saya ambil adalah dataset publik yang berasal dari kaggle, berikut keterangan mengenai variabel didalmnya :

- anime_id : kode berdasarkan anime
- name     : nama anime
- genre    : jenis plot atau alur cerita dari anime
- type     : type anime 
- episodes : riwayat atau peristiwa dari anime
- rating   : penilaian anime
- members  : jumlah penonton anime

## Explatory Data Analysis
- Drop Colomn
pada tahap ini saya drop beberapa kolom yang dapat mengganggu pada saat pemodelan agar nanti pada tahap pemodelan tidak ada kolom yang menghambat, diantaranya ada "Anime_id"
- Handling missing value pada dateset

- membuat sebuah analysis mengenai type anime yang ada pada data.

![1](https://user-images.githubusercontent.com/105061172/197259162-cc5cac3a-79c3-44d8-90a4-922ed1d0d8d5.png)



Gambar .4 type Anime

Pada Gambar .4 kita bisa lihat bahwa type terbanyak dalam Movie dimiliki oleh type **TV** dan **OVA** 


## Data Preparation

Berikut tahapan dalam pemrosesan data:

### Menghapus Fitur yang tidak diperlukan
Karena pada proyek ini kita tidak memerlukan fitur seperti **'Anime_id'** maka kita bisa drop fitur tersebut.

### Handling missing value
pada tahap ini dalam projek kita melakukan handling missing value dengan drop seluruh data yang memiliki missing value agar pada saat modelling tidak terhabat oleh data yang missing.
ada dua teknik dalam handling missing value diantaranya adalah drop value yang kita gunakan pada proyek ini atau mengisi mising value dengan nilai rata rata.

## Modeling

### Content Based Filtering
Content Based Filtering merekomendasikan Anime berdasarkan Genre sebelumnya yang disukai atau dipilih oleh penonton Anime, kemiripan Anime dihitung berdasarkan fitur yang ada dalam item yang dibandingkan, berikut merupakan parameternya :

- Anime_name : berisi nama Anime yang ingin dicari rekomendasinya.
- similarity_data : berisi dataframe yang berisi similarity yang telah didefinisakan menggunakan cosine similarity.
- items : berisi nama nama fitur yang akan dimunculkan pada saat direkomendasikan, disini saya menaruh fitur **'Name', 'Genre', 'Episode', 'Rating'**.
- k : banyaknya Anime film yang ingin direkomendasikan, disini saya menaruh 5 rekomendasi film yang akan ditampilkan

-kelebihan
 -  mudah digunakan untuk mencari kemiripan pada data untuk rekomendasi.
 
-kekurangan
 - Anime yang akan dimunculkan terbatas.

### Hasil pemodelan

Berikut saya masukkan beberapa name Anime yang akan direkomendasikan:

|index|name|genre|type|episodes|rating|members|
|---|---|---|---|---|---|---|
|16|Shigatsu wa Kimi no Uso|Drama, Music, Romance, School, Shounen|TV|22|8\.92|416397|

Tabel 1. Shigatsu wa kimi no uso Anime

- berikut output dari rekomendasinya Anime **Shigatsu wa kimi no uso**

|index|name|genre|episodes|rating|
|---|---|---|---|---|
|0|D\.C\.III: Da Capo III Special|Drama, Music, Romance, School|1|6\.49|
|1|Kimi no Iru Machi: Tasogare Kousaten|Drama, Romance, School, Shounen|2|7\.33|
|2|Shinkyoku Soukai Polyphonica Crimson S|Drama, Fantasy, Music, Romance, School|12|7\.33|
|3|Chiisana Love Letter: Mariko to Nemunoki no Kodomo-tachi|Drama, Music, School|1|5\.57|
|4|Hibike\! Euphonium: Kakedasu Monaka|Drama, Music, School|1|7\.5|


Tabel .2 Shigatsu wa kimi no uso rekomendasi


## Evaluation
pada bagian ini saya mengambil 2 sampel Anime yang akan menampilkan rekomendasinya:

- Rekomendasi Anime yang bernama **Gintama**

|index|name|genre|type|episodes|rating|members|
|---|---|---|---|---|---|---|
|12|Gintama|Action, Comedy, Historical, Parody, Samurai, Sci-Fi, Shounen|TV|201|9\.04|336376|

Tabel .3 Anime Gintama

- berikut output dari rekomendasinya Anime **Gintama**

|index|name|genre|episodes|rating|
|---|---|---|---|---|
|0|Gintama: Shinyaku Benizakura-hen|Action, Comedy, Historical, Parody, Samurai, Sci-Fi, Shounen|1|8\.31|
|1|Gintama: Yorinuki Gintama-san on Theater 2D|Action, Comedy, Historical, Parody, Samurai, Sci-Fi, Shounen|2|8\.6|
|2|Gintama Movie: Kanketsu-hen - Yorozuya yo Eien Nare|Action, Comedy, Historical, Parody, Samurai, Sci-Fi, Shounen|1|9\.1|
|3|Gintama Movie: Shinyaku Benizakura-hen|Action, Comedy, Historical, Parody, Samurai, Sci-Fi, Shounen|1|8\.59|
|4|Gintama: Jump Festa 2014 Special|Action, Comedy, Historical, Parody, Samurai, Sci-Fi, Shounen|1|8\.2|

Tabel .4 Anime rekomendasi Gintama


- Rekomendasi pada Anime bernama **One Piece**

|index|name|genre|type|episodes|rating|members|
|---|---|---|---|---|---|---|
|74|One Piece|Action, Adventure, Comedy, Drama, Fantasy, Shounen, Super Power|TV|Unknown|8\.58|504862|

Tabel .5 Anime One Piece

- Output rekomendasi dari Anime **One Piece**

|index|name|genre|episodes|rating|
|---|---|---|---|---|
|0|One Piece: Episode of Nami - Koukaishi no Namida to Nakama no Kizuna|Action, Adventure, Comedy, Drama, Fantasy, Shounen, Super Power|1|8\.27|
|1|One Piece: Episode of Sabo - 3 Kyoudai no Kizuna Kiseki no Saikai to Uketsugareru Ishi|Action, Adventure, Comedy, Drama, Fantasy, Shounen, Super Power|1|7\.78|
|2|One Piece: Episode of Merry - Mou Hitori no Nakama no Monogatari|Action, Adventure, Comedy, Drama, Fantasy, Shounen, Super Power|1|8\.29|
|3|One Piece: Oounabara ni Hirake\! Dekkai Dekkai Chichi no Yume\!|Action, Adventure, Comedy, Fantasy, Shounen, Super Power|1|7\.43|
|4|One Piece Movie 5: Norowareta Seiken|Action, Adventure, Comedy, Fantasy, Shounen, Super Power|1|7\.44|

Tabel .5 One Piece rekomendasi

Pada Tabel .4 dan .5 terlihat rekomendasi dari sistem sesuai dengan yang kita ingingkan berdasarkan genre melalui nama yang pengguna inginkan dengan menampilkan 5 Anime rekomendasi.

mengingat kita mencari rekomendasi berdasarkan Name yang dimiliki oleh Anime, maka bisa kita evaluasi dengan rumus :

#### `P =(  # of our recommendations that are relevant) / (# of items we recommended)`

Untuk p = 1, karena rekomendasi yang relevan dibagi dengan Anime yang kita rekomendasikan yang mana untuk rekomendasi relevan = 5, Anime yang direkomendasi = 5.

Maka, 5/5 = 1

Pada rumus diatas kita bisa mengetahui presisi dari rekomendasi yang kita berikan. kita telah memberikan 5 rekomendasi berdasarkan genre melalui nama Gintama dan One Piece, dan sistem memberikan kita rekomendasi yang sama. dengan perhitungan **(rekomendasi yang relevan) / (item yang kita rekomendasikan)** 

oleh karena itu dengan rumus perhitungan sederhana pada rumus diatas sistem rekomendasi bisa memilki presisi yang sangat baik.

## Referensi
- λ.eranga (Nov 29, 2021), Recommendation System with Content-based Filtering from medium https://medium.com/rahasak/recommendation-system-with-content-based-filtering-500231e31a60
-Anime industry report (2016). http://aja.gr.jp/jigyou/chousa/sangyo_toukei. Accessed 30 Mar 2017
- Elahi, M., Deldjoo, Y., Bakhshandegan Moghaddam, F., Cella, L., Cereda, S., Cremonesi, P.: Exploring the semantic gap for movie recommendations. In: Proceedings of the Eleventh ACM Conference on Recommender Systems, pp. 326–330 (2017)


