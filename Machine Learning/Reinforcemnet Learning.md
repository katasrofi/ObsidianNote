# Upper Confidence Bounds (UCB)
- Digunakan untuk masalah Multi-Armd Bandits Problem
- Eksplorasi dan eksploitasi secara acak tetapi lebih efisien dari AB Test
	- Konsep utama adalah untuk mencari keseimbangan antara eksplorasi dan eksploitasi dalam pengambilan keputusan. 
		- Eksplorasi berarti mencoba pilihan yang belum banyak dijelajahi untuk mengetahui tingkat rewardnya, 
		- sementara eksploitasi berarti memilih pilihan dengan tingkat reward terbaik yang sudah diketahui berdasarkan data yang telah dikumpulkan.
- Confidence Bound: 
	- UCB menghitung interval kepercayaan (confidence bound) untuk setiap pilihan berdasarkan data yang telah dikumpulkan. Interval ini mencakup tingkat ketidakpastian tentang reward sebenarnya untuk setiap pilihan.
- Pengambilan Keputusan: 
	- UCB memilih pilihan dengan reward terbaik yang berada pada batas atas interval kepercayaan (confidence bound) tertinggi. Dengan kata lain, pilihan dengan reward yang memiliki potensi tertinggi untuk menjadi yang terbaik dipilih.
- Peningkatan Akurasi: 
	- Saat eksperimen berlanjut dan data terus dikumpulkan, interval kepercayaan akan menyempit sehingga akurasi estimasi reward meningkat. Ini membantu algoritma menjadi lebih yakin dalam mengambil keputusan.
- Tidak Diberi Bias: 
	- UCB tidak memberi preferensi atau bias terhadap pilihan tertentu pada awal eksperimen, sehingga ia cenderung mencoba semua pilihan untuk mengetahui reward yang lebih baik.
- Penggunaan dalam Eksperimen Bandit: 
	- UCB adalah salah satu algoritma yang umum digunakan dalam eksperimen multi-armed bandit, di mana tujuannya adalah memaksimalkan total reward yang diterima dalam jangka panjang.
# Thompson Sampling
- Probabilistic methode
- Multi-Armed Bandit: Analogi dari mesin slot dengan banyak tuas (lengan) yang memberikan hadiah dengan probabilitas tertentu. 
- Tujuan: Mencari lengan yang memberikan hadiah tertinggi.
- Thompson Sampling: Metode probabilistik untuk memilih lengan dengan probabilitas tertentu.
- Eksplorasi: Mencoba lengan-lengan baru untuk mendapatkan informasi baru.
- Eksploitasi: Memilih lengan yang dianggap paling menguntungkan berdasarkan pengetahuan saat ini.
- Adaptif: Mampu menyesuaikan pemilihan lengan seiring berjalannya waktu.
- Probabilitas Distribusi: Menghitung probabilitas untuk setiap lengan berdasarkan data sebelumnya.
- Keuntungan: Dapat mencapai kecepatan konvergensi yang lebih cepat dan hasil yang lebih baik dalam eksperimen.
- Efisiensi: Thompson Sampling memadukan eksplorasi dan eksploitasi dengan cerdas, mengoptimalkan pencarian hadiah tertinggi.
- Fleksibel: Cocok untuk berbagai masalah yang melibatkan pengambilan keputusan adaptif dengan ketidakpastian dalam probabilitas hadiah.
