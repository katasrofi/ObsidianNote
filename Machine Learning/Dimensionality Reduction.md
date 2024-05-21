# Principal Components Analysis (PCA)
- Dimensional Reduction dengan mencari korelasi antar variable
- Unsupervised
- PCA digunakan untuk menghilangkan redundansi dalam data dan mengidentifikasi dimensi yang paling berpengaruh dalam data.
- Digunakan untuk
	- Noise Filtering
	- Visualization
	- Feature Extraction
	- Stock Market Prediction
	- Gene Data Analysis
##### Applying PCA
from sklearn.decomposition import PCA
pca = PCA(n_components=5)
x_train = pca.fit_transform(x_train)
x_test = pca.transform(x_test )
	- n_components diisi dengan melakukan percobaan terus menerus agar mendapat parameter terbaik
	
#### Applying KernelPCA
from sklearn.decomposition import KernelPCA
kpca = KernelPCA(n_components=6, kernel = 'rbf')
x_train = kpca.fit_transform(x_train)
x_test = kpca.transform(x_test )
# Linear Discriminant Analysis (LDA)
- Supervised
- Dimensionality Reduction dengan mencari fitur yang paling bermanfaat untuk dalam membedakan kelompok
- Cocok digunakan untuk klasifikasi dan pengenalan pola

#### Applying LDA
from sklearn.discriminant_analysis import LinearDiscriminantAnalysis as LDA
n_components = min(x_train.shape[1], len(np.unique(y_train))) - 1
lda = LDA(n_components=n_components)
x_train = lda.fit_transform(x_train, y_train)
x_test = lda.transform(x_test)
# Perbedaan PCA dan LDA
Linear Discriminant Analysis (LDA):

1. Tujuan: LDA digunakan untuk mencari fitur-fitur yang paling bermanfaat dalam membedakan dua atau lebih kelompok dalam data.
    
2. Berdasarkan Kelompok: LDA mempertimbangkan informasi label kelas dalam data. Itu berarti LDA berfokus pada membedakan antara kelas yang berbeda.
    
3. Keluaran: LDA menghasilkan fitur-fitur baru yang disusun untuk memaksimalkan pemisahan antara kelompok-kelompok.
    
4. Penggunaan: LDA sangat berguna dalam tugas-tugas klasifikasi dan pengenalan pola, di mana kita ingin meningkatkan kemampuan membedakan antara kelas-kelas data.
    

Principal Component Analysis (PCA):

1. Tujuan: PCA digunakan untuk mengurangi dimensi data tanpa mempertimbangkan kelas atau labelnya. Tujuan utamanya adalah untuk menghilangkan redundansi dalam data.
    
2. Berdasarkan Variabilitas: PCA tidak mempertimbangkan label kelas dan hanya memperhatikan variasi keseluruhan data.
    
3. Keluaran: PCA menghasilkan komponen utama (principal components) yang merupakan kombinasi linear dari fitur asli. Komponen utama ini adalah vektor-vektor orthogonal yang tidak berkorelasi satu sama lain.
    
4. Penggunaan: PCA berguna untuk visualisasi data dalam ruang 2D atau 3D, kompresi data, dan preproses data sebelum digunakan dengan algoritma pembelajaran mesin.
    

Ringkasan Perbedaan:

- LDA fokus pada membedakan antara kelompok-kelompok dalam data dengan mempertimbangkan label kelas, sedangkan PCA tidak memperhatikan label kelas dan hanya memperhatikan variasi keseluruhan data.
- LDA menghasilkan fitur-fitur baru yang lebih baik dalam membedakan antara kelompok-kelompok, sedangkan PCA menghasilkan komponen utama yang merupakan kombinasi linear dari fitur asli untuk mengurangi dimensi data.
- Penggunaan LDA lebih cocok untuk tugas-tugas klasifikasi, sementara PCA lebih cocok untuk tugas visualisasi dan preproses data.
