# Tensors
- Creating Tensors using 
	- `torch.tensor([[[]]])`
- Buat random tensor untuk Neural Network 
	- `torch.rand()`
- Tensor type digunakan dalam pengukuran yang presisi agar didapatkan perhitungan yang tepat
	- float16 -> Half Precision
	- float32 -> Umum digunakan (Single Precision)
		- torch.float()
	- float64 -> lebih akurat tetapi butuh memori dua kali float32 (Double Precision)
	- float128 -> sangat akurat tapi lambat karena terlalu kompleks
# Data Aggregation
- Reshape
	- Mengubah shape sesuai peraturan PyTorch
		- (m x n) @ (a x b) = (m x b)
- Stacking
	- Menggabungkan kolom atau row dengan `torch.stack`
- Squeeze
	- Menghilangkan semua dimensi pertama dari tensor `torch.squeeze`
- Unsqueeze
	- Menambahkan satu dimensi kedalam tensor `torch.unsqueeze(dim=0)`
- Permute
	- Mengatur ulang dimensi dengan berbagi memori yang sama dengan variable yang digunakan `torch.permute` biasa digunakan untuk images
# Convert
- Numpy (array) to Tensors (PyTorch)
	- `torch.from_numpy(ndarray)`
- Tensors to Array
	- `torch.Tensor.numpy()`
- To Reduce randomness use random seed
	- `torch.manual_seed()`