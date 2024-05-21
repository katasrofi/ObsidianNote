- ML untuk identifikasi categorical
	- Biasa digunakan untuk memprediksi apakah kustomer akan pergi atau tetap setia berlangganan
	- Identifikasi email spam
# Logistic Regression
- Evaluasi metriks
	- from sklearn.metrics import confussion_matrix 
		- ==untuk membandingkan jumlah prediksi yang benar, salah dan meleset==
	- from sklearn.metrics import accuracy_score 
		- ==Untuk menilai akurasi model ==
- Library
	- from sklearn.linear_model import LogisticRegression
	- log_model = LogisticRegression

# K-Nearest Neighbors
- Digunakan untuk clustering
- Jumlah k (cluster) ditetapkan berapa, nilai default nya 5 sehingga jumlah kelompok akan tergantung jumlah k
- Jika ada sampel baru maka algoritma K-Nearest Neighbors akan menghitung jarak paling dekat dengan tetangganya dan mengelompokkan ke kelompok terdekat
- library
	- from sklearn.neighbors import KNeighborsClassifier
	- k_model = KNeighborsClassifier(n_neighbors = 5, metric = 'minkowski', p = 2)
		- n_neighbors adalah jumlah tetangga pada cluster, semakin dekat variable baru pada kluster dengan lebih banyak tetangga maka ia akan masuk kedalam kelompok itu
		- metric adalah fungsi yang digunakan untuk mengukur jarak dengan variable baru, nilai defaultnya minkowski tetapi bisa diubah menjadi euclidean dan manhattan
		- nilai p digunakan untuk mengatur sensitifitas pengukuran, nilai defaultnya 2, 
			- semakin besar nilai p maka sensitifitasnya akan lebih peka ke  perbedaan nilai yang besar 
			- jika semakin kecil maka sensitifitasnya akan lebih peka ke perbedaan nilai yang kecil

# Support Vector Machine (SVM)
- Biasa digunakan untuk mencari garis pemisah terbaik dengan margin maksimum dalam pembagian klasifikasi sehingga pengamatan baru dapat diprediksi dengan lebih akurat
- Sangat tahan terhadap outlier
- Memiliki kekuatan analisis yang lebih baik karena menggunakan support vector secara maksimum
- Tidak disarankan untuk dataset besar karena akan menghabiskan banyak kekuatan komputasi = Mahal
- library 
	- from sklearn.svm
	- Search in sklearn website
	- example : from sklearn.svm import SVC
		- svc = SVC(kernel = 'linear', random_state = 1)
			- untuk penjelasan kernel dan random state, ==**Baca di note Regression bagian SVR**==
# Kernel SVM
- Kernel SVM adalah sebuah fungsi yang ada di SVM dan SVR, dia berfungsi untuk membuat garis pemisah maximum margin yang membedakan dua kelompok secara akurat
- Kernel SVM dapat memisahkan data secara linear dan non linear
- Untuk linear Kernel SVM menghitung menggunakan support vector hingga didapatkan margin maximum
- Untuk non-linear kernel SVM menggunakan metode 
	- Mapping to Higher Dimension, metode ini mengubah data yang awalnya 2D menjadi 3D dengan perhitungan kompleks sehingga memungkinkan menghitung margin maximum kemudian kembali ke 2D dan diproyeksikan menjadi non linear
		- Metode ini mahal karena butuh kekuatan komputasi yang kuat
	- Cara kedua menggunakan Gaussian RBF Kernel yang dapat menghitung margin maximum tanpa melakukan proyeksi ke 3D sehingga kekuatan komputasi yang dibutuhkan jauh lebih sedikit dan efektif
# Naive Bayes
- P(B|A) = P(A|B) x P(B)/P(A)
	- P(B) -> Prior Probability
	- P(A) -> Margin Likelihood
	- P(A|B) -> Likelihood
	- P(B|A) -> Posterior Probability
- Mempredksi peristiwa berdasarkan informasi yang sudah diketahui
- Disebut naive karena berdasarkan asumsi yang ada sehingga jika asumsi salah maka prediksi menjadi tidak dapat diandalkan
- library
	- from sklearn.naive_bayes import GaussianNB
	- naive_bayes = GaussianNB()
# Decision Tree Classification
- library 
	- from sklearn.tree import DecisionTreeClassifier
	- classifier = DecisionTreeClassifier(criterion = 'entropy', random_state = 1)
		- criterion
			- gini -> mengukur impuritas kelas 
			- entropy -> mengukur ketidakpastian atau keragaman pada kelas
# Random Forest Classification
- Same with Random Forest Regression

# Evaluasi Classifier model
- Confussion matrix
|            　　　  | Prediksi Negatif | Prediksi Positif      |
|--------------|------------------|------------------|
| Negatif           | True Negatif         | False Positif         |
| Positif    　　  | False Negatif        | True Positif          |
- Accuracy paradox harus dihindari karena meski meningkatkan akurasi tetapi tidak meningkatkan kekuatan prediksi dari model 
- Gunakan metode yang lebih canggih yaitu CAP (Cumulative Accuracy Profile) Curve dan ROC (Receiver Operating Characteristic)
	- CAP Curve
		- If X < 60% => Sampah
		- if 60% < X < 70% => Buruk
		- if 70% < X < 80% => Bagus
		- if 80% < X < 90% => Very Good
		- if 90% < X < 100% => Sangat bagus tapi mencurigakan (Overfitting)


