# KMeans Clustering
- Pengelompokan data yang tidak memiliki label (Unsupervised Learning)
- Centroid pada cluster akan diinisialisasi secara otomatis K-Means++ sehingga menghindari Random Initialization Trap dan menghasilkan cluster yang optimal
- Ditentukan clusternya secara manual
	- Untuk penentuan cluster yang optimal digunakan Elbow Methode
		- Menggunakan fungsi dari kmeans.inertia_ untuk mendapatkan nilai WCSS (Within-Cluster Sum of Squares) untuk Elbow Methode
	- Untuk mendapatkan pusat centroid gunakan fungsi kmeans.cluster_centers_
# Hierarchical Clustering
- Agglomerative -> Pengelompokkan dari bawah keatas
	- Setiap data dianggap satu cluster dan kemudian data terdekat akan dijalin hingga membentuk cluster baru, sampai semua data menjadi satu cluster
		- Gunakan dendrogram untuk melihat urutan pembuatan clusternya
- Divisive -> Pendekatan sebaliknya dari agglomerative
- library
	- import scipy.cluster.hierarchy as sch
	- from sklearn.cluster import AgglomerativeCluster
	- dendrogram = sch.dendrogram(sch.linkage(x, method = 'ward'))