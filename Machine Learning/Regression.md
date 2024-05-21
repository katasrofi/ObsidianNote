# Linear Regression
Build The Model
- y = b0 + b1x1 + ....+ bnxn
- from sklearn.linear_model import LinearRegression
- All-in 
	- ==Berdasarkan SOP atau instruksi client==
- Backward Elimination 
	- ==Menyingkirkan variable dengan p-value diatas 5% lalu rebuild model==
- Forward Selection 
	- ==Membangun model dengan cara menambahkan variable dengan p value dibawah 5%(level signifikansi) secara bertahap hingga variable baru yang ditambahkan dan memiliki p value diatas 5%, pertahankan model sebelumnya jika  hal itu terjadi==
- Bidirectional Elimination 
	- ==Gabungan forward dan backward dengan urutan pertama menambah variabel yang ada dibawah 5%(Level signifikansi) lalu menjalankan backward dengan mengeliminasi setiap variable yang memiliki p value diatas 5%, dilakukan hingga tidak ada variabel yang bisa ditambahkan dan tidak bisa dikurangkan==
- All Possible Model 
	- ==Model yang menggunakan semua kombinasi contohnya dataset A memiliki 10 kolom maka akan ada 1023 model yang dilakukan dihitung dengan 2^N - 1 sehingga ini akan memakan banyak waktu dan kekuatan komputasi, jangan dilakukan kecuali ingin menghancurkan laptop lama==
- Feature scaling digunakan tergantung dataset yang digunakan


# Polynomial Regression
- y = b0 + b1x1 ^1 + ...... + bnx1 ^n
*from sklearn.linear_model import LinearRegression
from sklearn.preprocessing import PolynomialFeatures
poly = PolynomialFeatures(degree = 2)
x_poly = poly.fit_transform(x)
poly_reg = LinearRegression()
poly_reg.fit(x_poly, y)*
- Digunakan untuk mengukur pertumbuhan yang eksponensial, seperti pertumbuhan teknologi, epidemi, pandemu, etc.
- penggunaan degree harus diperhatikan karena jika terlalu tinggi maka akan menyebabkan overfitting
- Single predict 
	- poly_reg.predict(poly.fit_transform([[value]]))
- 



# Support Vector Regression (SVR)
- Epsilon(insensitive tube)
	- Batas kesalahan dalam tabung garis linar SVR dapat diabaikan margin kesalahannya 
	- Jika diluar maka akan diperhitungkan dan dianggap penting disebut dengan Support Vector(SV)
	- Feature Scaling yang digunakan 
		- sc_X = StandardScaler() 
		  sc_y = StandardScaler() 
		  x = sc_X.fit_transform(x) 
		  y = sc_y.fit_transform(y)
		  *Terdapat dua kali pembentukan scaling karena nilai indenpendent dan dependent variable berbeda sehingga membutuhkan deklarasi scaler yang berbeda*
	- Library
		- from sklearn.linear_model import SVR
		- svr = SVR(kernel = 'rbf', random_state = 1)
			- kernel adalah fungsi matematika untuk menghitung data produk dalam ruang fitur yang diubah
			- 'rbf' adalah Radial Basis Function yang digunakan untuk regresi non linear yang menggunakan dimensi tak terhingga dengan rumus gaussian
			- selain rbf ada kernel lain seperti kernel linear yang digunakan untuk SVR linear
			- kernel Sigmoid memodelkan hubungan non-linear dengan bentuk S
			- Polynomial kernel
			- Precomputed Kernel: Kernel ini memungkinkan pengguna untuk menggunakan matriks kernel yang telah dihitung sebelumnya sebagai masukan ke model SVR. Matriks kernel ini mencerminkan hubungan antara pasangan data dalam ruang fitur yang diubah.
			- Custom Kernel: Membuat kernel kustom sesuai kebutuhan. Kernel kustom ini dapat menggambarkan hubungan non-linier yang kompleks berdasarkan sifat data yang spesifik.
			- random_state memastikan hasil prediksi pertama akan tetap sama dengan selanjutnya
		- Single prediction
			- sc_y.inverse_transform(model.predict(sc_X.transform([[value]])).reshape(-1, 1))

# Decision Tree Regression
- Decision tree regression menggunakan struktur pohon keputusan untuk memprediksi nilai kontinu.
- Pohon keputusan terdiri dari serangkaian pertanyaan (pemisahan) yang membagi data menjadi kelompok yang semakin kecil.
- Setiap node dalam pohon keputusan mewakili pertanyaan atau kondisi yang digunakan untuk membagi data.
- Proses pemisahan dilakukan berulang-ulang hingga mencapai daun pohon yang berisi nilai prediksi.
- Pada setiap node, kita mencari fitur yang memberikan pemisahan terbaik berdasarkan kriteria tertentu.
- Saat membuat prediksi pada data baru, kita mengikuti jalur dalam pohon keputusan berdasarkan jawaban terhadap pertanyaan yang sesuai dengan fitur-fitur dari data tersebut.
- Nilai prediksi akhir adalah nilai rata-rata dari sampel yang jatuh di daun yang sesuai.
- Decision tree regression memungkinkan prediksi nilai kontinu dan dapat menangkap hubungan non-linear antara fitur-fitur dan target.
- library
	- from sklearn.tree import DecisionTreeRegressor
	- tree = DecisionTreeRegressor(random_state = 1)
	- tree.fit(x, y)

# Random Forest Regressor
- Secara sederhana adalah ensemble learning
	- Random forest seperti kumpulan prediksi decision tree yang disatukan sehingga menjadi sebuah hutan yang cocok dengan namanya Random Forest
- Sangat stabil karena satu prediksi tidak bisa mengguncang satu hutan
- Toleransi yang tinggi terhadap overfitting
- Membutuhkan banyak Ram
- library
	- from sklearn.ensemble import RandomForestRegressor
		- ==Untuk Regression==
	- from sklearn.ensemble import RandomForestClassifier
		- ==Untuk klasifikasi==
	- forest_model = RandomForestRegressor(n_estimators = 10, random_state = 1)
		- n_estimators : menentukan akan seberapa banyak pohon yang digunakan, jika n = 10 maka ada 10 pohon yang digunakan, jika dikosongkan maka akan terisi nilai defaultnya yaitu 100
		- random_state memastikan sample tidak akan teracak lagi sehingga bisa mendapat hasil yang sama dengan prediksi sebelumnya
	- forest_model.fit(x,y)

# Evaluasi Model Regression
- R Squared
	- Goodnes of fit (Greater is better)
	- R^2 = 0, model tidak cocok dengan data
	- R^2 < 4, terrible harus diperbaiki
	- R^2 < 3, tidak begitu bagus tapi masih bisa diterima
	- R^2 < 9, bagus model bisa digunakan dengan baik
	- R^2 = 1, mencurigakan, mungkin overfitting
- Adjusted R Squared
	- Digunakan saat penambahan variable baru pada model karena dikhawatirkan terjadi kesalahan pada R Squared dimana nilai R Squared tidak berubah sehingga penambahan variable tidak diketahui memiliki pengaruh terhadap model, sehingga tidak diketahui apakah perlu atau tidak menambahkan variable baru pada model