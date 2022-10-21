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
Dataset yang saya gunakan adalah Movie Recommendation yang saya ambil dari kaggle 
[Kaggle](https://www.kaggle.com/datasets/CooperUnion/anime-recommendations-database)

Pada dataset ini memiliki **12294** entries dan **7** kolom dimana didalamnya seperti berikut:

Dataset yang saya ambil adalah dataset publik yang berasal dari kaggle, berikut keterangan mengenai variabel didalmnya :

- anime_id
- name
- genre
- type
- episodes
- rating
- members

## Explatory Data Anlysis
- membuat sebuah analysis mengenai type anime yang ada pada data.

![type_anime]![](https://user-images.githubusercontent.com/105061172/196426680-33874fa0-66e1-4a19-b9b5-ce3e50b99cbd.png)


Gambar .4 genre TV

Pada Gambar .4 kita bisa lihat bahwa genre terbanyak dalam Movie dimiliki oleh genre **Drama** dan **Comedy** 

- Visualisasi Setiap Movie kapan dirilis 

![tahun_tv](https://user-images.githubusercontent.com/73319544/192697562-00a62b08-0bb2-4b4f-af59-4ac49828085f.png)

Gambar .5 tahun rilis MovieTV

pada Gambar .5 lihat bahwa semakin tahun produksi film semakin meningkat cukup pesat, dengan adanya teknologi khusus tahun demi tahun film menjadi bagian penting dalam peradaban.

## Data Preparation

Berikut tahapan dalam pemrosesan data:

### Menghapus Fitur yang tidak diperlukan
Karena pada proyek ini kita tidak memerluka fitur seperti **'notes' 'critics_vote' 'description'** maka kita bisa drop fitur tersebut.

### Handling missing value
pada tahap ini dalamprojek kita melakukan handling missing value dengan drop seluruh data yang memiliki missing value agar pada saat modelling tidak terhabat oleh data yang missing.
ada dua teknik dalam handling missing value diantaranya adalah drop value yang kita gunakan pada proyek ini atau mengisi mising value dengan nilai rata rata.

## Modeling

### Content Based Filtering
Content Based Filtering merekomendasikan item yang mirip dengan item sebelumnya yang disukai atau dipilih oleh penonton MovieTV, kemiripan item dihitung berdasarkan fitur yang ada dalam item yang dibandingkan, berikut merupakan parameternya :

- movie_name : berisi nama MovieTV yang ingin dicari rekomendasinya.
- similarity_data : berisi dataframe yang berisi similarity yang telah didefinisakan menggunakan cosine similarity.
- items : berisi nama nama fitur yang akan dimunculkan pada saat direkomendasikan, disini saya menaruh fitur **'title', 'year', 'genre', 'year', 'public_vote'**.
- k : banyaknya MovieTV film yang ingin direkomendasikan, disini saya menaruh 10 rekomendasi film yang akan ditampilkan

-kelebihan
 -  mudah digunakan untuk mencari kemiripan pada data untuk rekomendasi.
 
-kekurangan
 - item yang akan dimunculkan terbatas.

### Hasil pemodelan

Berikut saya masukkan beberapa name Anime yang akan direkomendasikan:

|index|name|genre|type|episodes|rating|members|
|---|---|---|---|---|---|---|
|16|Shigatsu wa Kimi no Uso|Drama, Music, Romance, School, Shounen|TV|22|8\.92|416397|

Tabel .1 dinner MovieTV

- berikut output dari rekomendasinya film **Dinner**

|no|title                                                                                                |genre                                                                                                                        |year   |public_vote|
|--------|----------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------|-------|--------|
|1   |Malizia                                                                                      |Comedy                                                                                         |1973  |6.0       |
|2    |Crooklyn                                                                   |Comedy                                                                  |1994     |8.0      |
|3   |Manolesta                                                                                    |Comedy                                                                                         |1981  |6.0       |
|4    |Tsisperi mtebi anu daujerebeli ambavi                                                                    |Comedy                                                                  |1983     |8.0      |
|5   |Ternosecco                                                                                     |Comedy                                                                                         |1986  |5.0       |
|6    |Three on a Couch                                                                |Comedy                                                                  |1966     |7.0      |
|7   |The Search for Santa Paws                                                                                    |Comedy                                                                                         |2010  |5.0       |
|8    |Who Was That Lady?                                                                  |Comedy                                                                  |1960    |7.0      |
|9   |Love Aaj Kal                                                                                    |Comedy                                                                                         |2009  |4.0       |
|10    |Cosi vanna le cose                                                                  |Comedy                                                                  |2008     |3.0      |

Tabel .2 dinner rekomendasi


## Evaluation
pada bagian ini saya mengambil 2 sampel MovieTV yang akan menampilkan rekomendasinya:

- Rekomendasi Pada film **Dinner** yang bergenre **Comedy**

|no|title                                                                                                |genre                                                                                                                        |year   |country |
|--------|----------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------|-------|--------|
|1   |Dinner                                                                                      |Comedy                                                                                         |1989  |United States       |

Tabel .3 dinner MovieTV

- berikut output dari rekomendasinya film **Dinner**

|no|title                                                                                                |genre                                                                                                                        |year   |public_vote|
|--------|----------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------|-------|--------|
|1   |Malizia                                                                                      |Comedy                                                                                         |1973  |6.0       |
|2    |Crooklyn                                                                   |Comedy                                                                  |1994     |8.0      |
|3   |Manolesta                                                                                    |Comedy                                                                                         |1981  |6.0       |
|4    |Tsisperi mtebi anu daujerebeli ambavi                                                                    |Comedy                                                                  |1983     |8.0      |
|5   |Ternosecco                                                                                     |Comedy                                                                                         |1986  |5.0       |
|6    |Three on a Couch                                                                |Comedy                                                                  |1966     |7.0      |
|7   |The Search for Santa Paws                                                                                    |Comedy                                                                                         |2010  |5.0       |
|8    |Who Was That Lady?                                                                  |Comedy                                                                  |1960    |7.0      |
|9   |Love Aaj Kal                                                                                    |Comedy                                                                                         |2009  |4.0       |
|10    |Cosi vanna le cose                                                                  |Comedy                                                                  |2008     |3.0      |

Tabel .4 dinner rekomendasi


- Rekomendasi pada film **Dead-bang** bergenre **Crime**

|no|title                                                                                                |genre                                                                                                                        |year   |country |
|--------|----------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------|-------|--------|
|1   |Dead-Bang                                                                                      |Crime                                                                                         |1989  |United States       |

Tabel .5 deadbang MovieTV

- Output rekomendasi dari film **Dead-Bang**

|no|title                                                                                                |genre                                                                                                                        |year   |public_vote|
|--------|----------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------|-------|--------|
|1   |A Bullet for Joey                                                                                      |Crime                                                                                         |1955  |6.0       |
|2    |I Wake Up Screaming                                                                   |Crime                                                                  |1941     |8.0      |
|3   |Tte de turc                                                                                     |Crime                                                                                         |2010  |6.0       |
|4    |Hunter: Back in Force                                                                    |Crime                                                                  |2003     |4.0      |
|5   |Roma violenta                                                                                      |Crime                                                                                         |1975  |6.0       |
|6    |Jack the Ripper                                                                 |Crime                                                                  |1988     |7.0      |
|7   |MR 73                                                                                     |Crime                                                                                         |2008  |7.0       |
|8    |Pollisse                                                                   |Crime                                                                  |20011    |7.0      |
|9   |The Big Easy                                                                                     |Crime                                                                                         |1986  |7.0       |
|10    |I Walk Alone                                                                   |Crime                                                                  |1948     |6.0      |

Tabel .6 deadbang rekomendasi

Pada Tabel .4 dan .6 terlihat rekomendasi dari sistem sesuai dengan yang kita ingingkan berdasarkan genre yang pengguna inginkan dengan menampilkan 10 film rekomendasi.

mengingat kita mencari rekomendasi berdasarkan genre yang dimiliki oleh MovieTV, mak bisa kita evaluasi dengan rumus :

#### `P =(  # of our recommendations that are relevant) / (# of items we recommended)`

Pada rumus diatas kita bisa mengetahui presisi dari rekomendasi yang kita berikan. kita telah memberikan 10 rekomendasi berdasarkan genre Comedy dan Crime, dan sistem memberikan kita rekomendasi yang sama. dengan perhitungan **(rekomendasi yang relevan) / (item yang kita rekomendasikan)** 

oleh karena itu dengan rumus perhitungan sederhana pada rumus diatas sistem rekomendasi bisa memilki presisi yang sangat baik.

## Referensi
- λ.eranga (Nov 29, 2021), Recommendation System with Content-based Filtering from medium https://medium.com/rahasak/recommendation-system-with-content-based-filtering-500231e31a60
- kunisetti s. (Springer, Singapore), Content-Based Movie Recommendation System Using Genre Correlation, from https://d1wqtxts1xzle7.cloudfront.net/62049148/contentbased20200209-27698-l8hk2i-with-cover-page-v2.pdf?Expires=1664349281&Signature=Odckc84PpURE5-xCpkpqUGGbk2VBLqRu-vBW-MmxGmhZzx4OnEHyY~Z2nQIknqVSeCcZaaufStSZxOsh2hrIayAoxOxmMgC0f7q7FHQprbl4MfYtZXKACJ6thEltg0e-9GoVYle-drD6K47VvA6lE0QnMwiAesyjH4vwDwtjkAOETaW~5~8eCOno7eWKp5koROKmbNgXmIPo593N1nmBjG6G3G9KXzTGxlS0Ek2JmgQl1OzcBz8qJQAj0rGMP4GHF0kgz1AzaanbRRCfEpdumjYbXbz26N5M39GoBRIXPxWdBCSZ6O5pc9oXTtmHt1qB7O8ldBcndN~E6OU-mBSzIQ__&Key-Pair-Id=APKAJLOHF5GGSLRBV4ZA


