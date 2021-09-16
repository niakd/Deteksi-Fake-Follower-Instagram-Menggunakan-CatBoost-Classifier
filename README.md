# Deteksi-Fake-Follower-Instagram-Menggunakan-CatBoost-Classifier

Bahasa pemrograman yang digunakan adalah Python versi 3.7.6 dengan bantuan beberapa modul di antaranya CatBoost, Matplotlib, Scikit-learn, dan Pandas. 

Data yang digunakan adalah dataset yang telah tersedia di https://github.com/fcakyon/instafake-dataset, yakni kumpulan data fake account yang dikumpulkan dari beberapa akun Instagram di berbagai negara yang telah dilabeli sebanyak 994 akun nyata dan 200 akun palsu. Penelitian ini dilakukan untuk mengklasifikasikan akun Instagram yang termasuk ke dalam fake account dan real account dengan menggunakan Metode CatBoost Classifier yang dilatih dengan menggunakan k-fold cross validation, dengan memilih nilai k = 5. Teknik SMOTE-NC dilakukan dengan tujuan untuk menyeimbangkan data latih antar kelas. Selain itu, teknik feature selection juga dilakukan untuk memilih fitur yang paling berpengaruh dalam menentukan hasil klasifikasi. 

## Penjelasan dari masing-masing fitur yang digunakan adalah sebagai berikut:
1.	follower_count, berupa fitur numerik yang berisi informasi mengenai jumlah follower dari setiap akun.
2.	following_count, berupa fitur numerik yang berisi informasi mengenai jumlah following dari setiap akun.
3.	media_count, berupa fitur numerik yang berisi informasi mengenai jumlah posting-an yang terdapat pada setiap akun.
4.	profil¬_pic, berupa fitur kategori yang berisi informasi mengenai foto profil pada setiap akun, bernilai 1 untuk akun yang memiliki foto profil dan sebaliknya bernilai 0 untuk akun yang tidak memiliki foto profil.
5.	private, berupa fitur kategori yang berisi informasi mengenai akun disembunyikan (private) atau tidak, bernilai 1 untuk akun yang disembunyikan dan bernilai 0 untuk akun yang tidak disembunyikan.
6.	biography_length, berupa fitur numerik yang berisi informasi mengenai jumlah karakter yang terdapat pada biografi akun.
7.	username¬_length, berupa fitur numerik yang berisi informasi mengenai jumlah karakter yang terdapat pada username.
8.	username_digit_count, berupa fitur numerik yang berisi informasi mengenai jumlah digit yang terdapat pada username.
9.	follower_following_ratio, berupa fitur numerik yang berisi informasi mengenai perbandingan jumlah follower dengan jumlah following dari setiap akun.

## Langkah-langkah penelitiannya adalah sebagai berikut:
1.	Pengumpulan data yang diambil dari dataset yang telah tersedia di https://github.com/fcakyon/instafake-dataset.
2.	Eksplorasi data untuk melihat gambaran umum dari data yang ditampilkan melalui plot dan diagram, kemudian dibuat fitur baru yaitu fitur follower_following_ratio yang diperoleh dari hasil perbandingan fitur follower_count dan following_count.
3.	Membangun model dengan CatBoost Classifier untuk melakukan pengujian parameter dan memilih parameter optimal yang akan digunakan untuk melatih model.
4.	Oversampling data dengan menggunakan teknik SMOTE-NC (Synthetic Minority Oversampling Technique-Nominal Continuous).
5.	Feature Selection yang dipilih berdasarkan Feature Importance yang telah dihitung sebelumnya.
6.	Pembentukan model dengan menggunakan metode klasifikasi CatBoost (CatBoost Classifier) yang dilatih dengan k-fold cross validation. Pelatihan model dilakukan pada empat model yang berbeda, yaitu model tanpa SMOTE-NC dan tanpa feature selection, model tanpa SMOTE-NC dengan feature selection, model dengan SMOTE-NC tanpa feature selection, dan model dengan SMOTE-NC juga dengan feature selection.
7.	Evaluasi keempat model yang telah dilatih dengan melihat performa model dan running time yang dibutuhkan selama pelatihan. Performa model dilihat berdasarkan nilai akurasi, presisi, recall, F1, dan nilai AUC. 
8.	Pemilihan model terbaik yang memiliki nilai akurasi, presisi, recall, FI, nilai AUC tertinggi, dan running time tercepat di antara keempat model yang telah dilatih. 
9.	Penarikan kesimpulan.

Model terbaik dihasilkan dari model klasifikasi CatBoost dengan SMOTE-NC dan feature selection dengan nilai akurasi sebesar 98.04%, nilai recall sebesar 98.61% yang artinya model memiliki tingkat kesalahan dalam mendeteksi kelas fake account sebesar 11.39%, nilai presisi sebesar 97.71%, F1-score sebesar 98.04%, dan nilai AUC sebesar 99.71%. Adapun waktu yang dibutuhkan selama pelatihan model adalah 11.1 detik.
