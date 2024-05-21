## Missing Value

### Dataset kecil :
Mengganti nilai yang hilang dengan nilai rata-rata, nilai tengah atau nilai yang paling sering muncul(biasanya untuk categorical) menggunakan 
sklearn.impute import SimpleImputer

##### Mengganti nilai dengan nilai rata-rata
imputer = SimpleImputer(missing_value=np.nan, strategy='mean')

##### Mengganti nilai dengan nilai tengah
imputer = SimpleImputer(missing_value=np.nan, strategy='median')

##### Mengganti nilai dengan nilai paling sering muncul
imputer = SimpleImputer(missing_value=np.nan, strategy='most_frequent')

###### Cara menggunakannya
imputer.fit_transform(variable_names[:, index])

### Dataset Besar :
gunakan dropna, selain untuk menangani data yang terlalu besar juga untuk memperingan komputasi, selain kondisi itu gunakan dropna jika data yang hilang disemua faktor


## Encoding

gunakan library ini
sklearn.preprocessing import OneHoteEncoder 
	- ==untuk encoding==
sklearn.compose import ColumnTransformer 
- ==[*untuk mengubah langsung kedalam data sehingga tidak diperlukan concat*] ==
ct = ColumnTransformer(transformers = [('encoder', OneHotEncoder(), kolom)], remainder = 'passthrough')

## Label Encodeing
sklearn.preprocessing import LabelEncoder
le = LabelEncoder()
y = le.fit_transform(y)

## Split data to train and test
sklearn.model_selection import train_test_split
x_train, x_test, y_train, y_test = train_test_split(independent, dependent, test_size=0.2, random_state=1)
data always in array or tensor(for neural network)

## Feature Scaling
- Feature scaling pada dummies variable tidak begitu berguna karena tidak akan mengubah nilainya
- sklearn.preprocessing import StandardScaler
- sc = StandardScaler()
| Standardisation | -> -3 ~ 3 
==Bekerja dalam kondisi apapun dengan baik==
- sklearn.preprocessing import MinMaxScaler
- sc = MinMaxScaler(feature_range = (0, 1))
| Normalization | -> 0 ~ 1 
==Bekerja pada data normalisasi dan bekerja lebih baik dari standardization==



# For Loop for Take data apriori
- Jika data dalam file csv dalam bentuk daftar panjang yang memiliki banyak kolom dan row sehingga tidak bisa langsung diambil maka gunakan for loop
	- transactions = []
	- for i in range(len(dataset) + 1):
		- transactions.append([str(dataset.values[i, j])] for j in range(0, 20))
# One Way to Download script Python

import requests
from pathlib import Path

`if Path("name_file.py").is_file():
	`print("name_file.py already Exist")
`else:
	`print("Downloading name_file.py")
	`request = requests.get("link")
	`with open("name_file.py", "wb") as file: # file also can write as f
		`file.write(request.content)`