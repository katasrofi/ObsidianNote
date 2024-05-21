# Learning Curve
from sklearn.model_selection import learning_curve

#### Buat fungsi untuk plot kurva pembelajaran
def plot_learning_curve(model, x, y):
    train_sizes, train_scores, val_scores = learning_curve(model, x, y, cv=5,
                                                           scoring='neg_mean_squared_error')
    train_scores_mean = -np.mean(train_scores, axis=1)
    val_scores_mean = -np.mean(val_scores, axis=1)
    
    plt.figure(figsize=(8, 6))
    plt.plot(train_sizes, train_scores_mean, label='Training error')
    plt.plot(train_sizes, val_scores_mean, label='Validation error')
    plt.xlabel('Training set size')
    plt.ylabel('Mean Squared Error')
    plt.title('Learning Curve')
    plt.legend()
    plt.show()

#### Plot kurva pembelajaran
plot_learning_curve(lasso, x_train, y_train)

# Hitung residual pada data pelatihan
y_train_pred = lasso.predict(x_train)
residuals = y_train - y_train_pred

#### Plot residual
plt.scatter(y_train_pred, residuals)
plt.xlabel('Predicted values')
plt.ylabel('Residuals')
plt.title('Residual Plot')
plt.show()

# Accuracy
from sklearn.metrics import mean_squared_error
mse = mean_squared_error(y_test, y_pred)
print("MSE pada data uji:", mse)

# Cross validation
scores = cross_val_score(lasso, x_train, y_train, cv=3, scoring='neg_mean_absolute_error')
mean_mse = -np.mean(scores)
print('Mean MSE: ', mean_mse)