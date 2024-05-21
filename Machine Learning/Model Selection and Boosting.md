# Model Selection
### K-Fold Cross Validation
from sklearn.model_selection import cross_val_score
accuracies = cross_val_score(model, x_train, y_train, cv = 10)
print('Accuracy: {:.2f} %'.format(accuracies.mean()*100))
print('Standard Deviation: {:.2f} %'.format(accuracies.std()*100))
	- cv adalah parameter untuk menentukan berapa fold yang digunakan
		- Semakin tinggi akurasi yang didapat akan semakin baik tetapi akan membutuhkan lebih banyak resource sehingga tidak worth*
### GridSearchCV

from sklearn.model_selection import GridSearchCV
parameters = [{'penalty': ['l1'], 
               'C': [0.25, 0.5, 0.75, 1], 
               'solver': ['liblinear', 'saga']},
              {'penalty': ['l2'], 
               'C': [0.25, 0.5, 0.75, 1], 
               'solver': ['newton-cg', 'lbfgs', 'sag']}]
grid_search = GridSearchCV(log_model, 
                           parameters, 
                           scoring = 'accuracy', 
                           cv = 10, 
                           n_jobs=-1)
grid_search.fit(x_train, y_train)
best_accuracy = grid_search.best_score_
best_parameters = grid_search.best_params_
print('Best Accuracy: {:.2f} %'.format(best_accuracy*100))
print('Best Parameters: ',best_parameters)
-  Sesuaikan parameters dengan model yang digunakan, lihat API sklearn, yang diatas untuk klasifikasi logistic regression
# Boosting
