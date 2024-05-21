# Apriori
Algoritma untuk menemukan ketergantungan/hubungan antar produk
- Apriori digunakan secara khusus dalam analisis data transaksional dan sering digunakan dalam tugas seperti analisis keranjang belanja, rekomendasi produk, atau analisis pola dalam data transaksi.
- Algoritma Apriori 
	- Support
		- Support(Purchased x) = Total of purchased x / all purchased
	- Confident
		- Confident(Purchased x -> y) = Total purchased x and y / support (purchased x)
	- Lift
		- Lift = Confident(Purchased x -> y) / Support(Purchased x)
- #### For Loop for Take data apriori
- Jika data dalam file csv dalam bentuk daftar panjang yang memiliki banyak kolom dan row sehingga tidak bisa langsung diambil maka gunakan for loop
	- transactions = []
	- for i in range(len(dataset) + 1):
		- transactions.append([str(dataset.values[i, j])] for j in range(0, 20))
- For Sort data
	def inspect(results):
	 lha         = [tuple(result[2][0][0])[0] for result in results]
	 rhs         = [tuple(result[2][0][1])[0] for result in results]
	 support     = [result[1] for result in results]
	 confidence  = [result[2][0][2] for result in results]    
	 lift        = [result[2][0][3] for result in results]
	 return list(zip(lha, rhs, support, confidence, lift))
	results_df = pd.DataFrame(inspect(results), columns = ['Left Hand Side', 'Right Hand Side', 'Support', 'Condfidence', 'Lift'])
	results_df = results_df.nlargest(n = 44, columns = 'Lift')

- library lain untuk apriori
	from mlxtend.preprocessing import TransactionEncoder
    from mlxtend.frequent_patterns import apriori, association_rules
		te = TransactionEncoder()
		te_ary = te.fit(transactions).transform(transactions)
		df_transactions = pd.DataFrame(te_ary, columns=te.columns_)
	- 
# Eclat
- Apriori yang disederhanakan, hanya ada support, tidak ada confidence dan lift
- Sangat cepat dibandingkan apriori
- Jangan gunakan pada data kompleks karena akan menghasilkan hasil yang silly