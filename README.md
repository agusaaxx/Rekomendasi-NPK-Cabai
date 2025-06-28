# Rekomendasi-NPK-Cabai

##Gambaran Umum Sistem
Sistem Anda akan bekerja dalam dua tahap utama:
1. Tahap Prediksi (Model ML): Model XGBoost akan memprediksi kadar N, P, dan K optimal yang seharusnya ada di tanah berdasarkan kondisi lingkungan saat itu (cahaya, suhu, kelembaban udara). Ini adalah jantung dari kecerdasan sistem Anda.
2. Tahap Kalkulasi (Logika Dosis): Setelah mengetahui kadar optimal dari model, sistem akan mengambil data kadar N, P, K saat ini dari sensor Anda. Kemudian, sistem akan menghitung selisihnya dan merekomendasikan berapa gram pupuk NPK yang perlu ditambahkan.
Berikut adalah diagram alurnya
[Sensor Lingkungan: Suhu, Cahaya, Kelembaban Udara] --> [Model XGBoost] --> [Prediksi NPK Optimal]
                                                                                    |
                                                                                    V
[Sensor Tanah: N, P, K Saat Ini] ---------------------> [Logika Kalkulator] --> [Rekomendasi Dosis (gram)]

##Langkah 1: Pengumpulan dan Persiapan Data
Ini adalah langkah paling kritis. Kualitas model Anda sangat bergantung pada kualitas data. Anda memerlukan dataset historis yang berisi semua fitur input dan output yang Anda inginkan.
Input (X): kelembaban_tanah, intensitas_cahaya, suhu_udara, kelembaban_udara.
Output (y): N_optimal, P_optimal, K_optimal.
Data tersebut tersaji pada file Crop_Recommendation.csv yang didalamnya terdapat semua aspek yang telah disebutkan 

##Langkah 2: Membuat Model Rekomendasi dengan XGBoost
Setelah data siap, kita akan melatih model XGBoost. Karena kita ingin memprediksi tiga nilai (N, P, dan K), kita akan melatih tiga model regresi terpisah. 
untuk file model pelatihan tersaji pada file model_pelatihan.ipynb

##Langkah 3: Persiapan di Firebase
Menggunakan Firebase sebagai perantara untuk memudahkan komunikasi antara perangkat keras (ESP32) dan skrip Python.
Hal ini dilakukan agar akuisis data dari sensor dapat dilaksanakan secara realtime kemudian data dari sensor yang telah berhasil di akuisisi langsung dikirimkan ke firebase lalu baru dari firebase dikirimkan ke script python untuk diolah menjadi sistem rekomendasi yang terkoneksi

##Langkah 4: Menjalankan Sistem Rekomendasi NPK Pemupukan
Setelah semua file tersedia seperti file hasil pelatihan model dan juga data sensor secara realtime telak terkoneksi, maka akan menjalankan sistem rekomendasi seutuhnya
Data tersebut tersaji pada file Rekomendasi_pemupukan.ipynb
