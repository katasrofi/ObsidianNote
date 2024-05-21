# Logistic Graph

from matplotlib.colors import ListedColormap
x_set, y_set = sc.inverse_transform(x_train), y_train
x1, x2 = np.meshgrid(np.arange(start = x_set[:, 0].min() - 10, stop = x_set[:, 0].max() + 10, step = 0.25),
                     np.arange(start = x_set[:, 1].min() - 1000, stop = x_set[:, 1].max() + 1000, step = 0.25))

plt.contourf(x, x2, log_model.predict(sc.transform(np.array([x1.ravel(), x2.ravel]).T)).reshape(x1.shape),
             alpha = 0.75, cmap = ListedColormap('red', 'blue'))
plt.xlim(x1.min(), x1.max())
plt.ylim(x2.min(), x2.max())

for i, j in enumerate(np.unique(y_set)):
    plt.scatter(x_set[y_set == j, 0], x_set[y_set == j, 1], c = ListedColormap('red', 'blue'), label = j)
    
plt.title('Logistic Graph')
plt.legend()
plt.show()


# Linear Graph
plt.scatter(x, y, color = 'blue', label = 'True value')
plt.plot(x, model.predict(x), color = 'red', label = 'Predict Value')
plt.title('Linear Model')
plt.xlabel('x')
plt.ylabel('y')
plt.legend()
plt.show()

# Polynomial Linear Graph
x_grid = np.arange(min(x), max(x), 0.1)
x_grid = x_gird.reshape(len(x_grid), axis = 1)
plt.scatter(x, y, color = 'blue', label = 'True value')
plt.plot(x_grid, poly_model.predict(x_grid), color = 'red', label = 'Predict Value')
plt.title('Polynomial Linear Model')
plt.xlabel('x')
plt.ylabel('y')
plt.legend()
plt.show()

# SVR Linear Graph
x_grid = np.arange(min(sc_X.inverse_transform(x)), max(sc_X.inverse_transform(x)), 0.1)
x_grid = x_grid.reshape(len(x_grid), axis = 1)
plt.scatter(sc_X.inverse_transform(x), sc_y.inverse_transform(y), color = 'blue', label = 'True value')
plt.plot(xgird,  sc_y.inverse_transform(svr_model.predict(sc_X.transform(x_grid)).reshape(-1, 1)), color = 'red', label = 'Predict Value')
plt.title('SVR Linear Model')
plt.xlabel('x')
plt.ylabel('y')
plt.legend()
plt.show()

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

#### Hitung residual pada data pelatihan
y_train_pred = lasso.predict(x_train)
residuals = y_train - y_train_pred

# Analyzing Graph
def plot_decision_boundary(model: torch.nn.Module, X: torch.Tensor, y: torch.Tensor):
    """Plots decision boundaries of model predicting on X in comparison to y.

    Source - https://madewithml.com/courses/foundations/neural-networks/ (with modifications)
    """
    # Put everything to CPU (works better with NumPy + Matplotlib)
    model.to("cpu")
    X, y = X.to("cpu"), y.to("cpu")

    # Setup prediction boundaries and grid
    x_min, x_max = X[:, 0].min() - 0.1, X[:, 0].max() + 0.1
    y_min, y_max = X[:, 1].min() - 0.1, X[:, 1].max() + 0.1
    xx, yy = np.meshgrid(np.linspace(x_min, x_max, 101), np.linspace(y_min, y_max, 101))

    # Make features
    X_to_pred_on = torch.from_numpy(np.column_stack((xx.ravel(), yy.ravel()))).float()

    # Make predictions
    model.eval()
    with torch.inference_mode():
        y_logits = model(X_to_pred_on)

    # Test for multi-class or binary and adjust logits to prediction labels
    if len(torch.unique(y)) > 2:
        y_pred = torch.softmax(y_logits, dim=1).argmax(dim=1)  # mutli-class
    else:
        y_pred = torch.round(torch.sigmoid(y_logits))  # binary

    # Reshape preds and plot
    y_pred = y_pred.reshape(xx.shape).detach().numpy()
    plt.contourf(xx, yy, y_pred, cmap=plt.cm.RdYlBu, alpha=0.7)
    plt.scatter(X[:, 0], X[:, 1], c=y, s=40, cmap=plt.cm.RdYlBu)
    plt.xlim(xx.min(), xx.max())
    plt.ylim(yy.min(), yy.max())


### Plot linear data or training and test and predictions (optional)
def plot_predictions(
    train_data, train_labels, test_data, test_labels, predictions=None
):
    """
  Plots linear training data and test data and compares predictions.
  """
    plt.figure(figsize=(10, 7))

    # Plot training data in blue
    plt.scatter(train_data, train_labels, c="b", s=4, label="Training data")

    # Plot test data in green
    plt.scatter(test_data, test_labels, c="g", s=4, label="Testing data")

    if predictions is not None:
        # Plot the predictions in red (predictions were made on the test data)
        plt.scatter(test_data, predictions, c="r", s=4, label="Predictions")

    # Show the legend
    plt.legend(prop={"size": 14})

# Binomial Graph
```
# Plot function
from matplotlib.lines import Line2D
def statplot(data, lim, obs_stat, title):
    
    # Create a kdeplot
    plt.figure(figsize=(12,4), tight_layout=True)
    ax = sns.kdeplot(data, linewidth = 0.8, color = 'black')
    
    # Simple formatting
    frame = ['right', 'left', 'top']
    for i in frame:
        ax.spines[i].set_visible(False)

    plt.title(title)
    plt.ylabel('')
    plt.yticks([], [])
    
    # Legend
    line = Line2D([0], [0], color='red', linestyle = '-', label='zero value')
    line_dashed = Line2D([0], [0], color='black', linestyle = '--', label='mean and standard deviation')
    plt.legend(handles=[line, line_dashed], loc='upper left');
    
    # Create a list of 3 standard deviation to the left and to the right and mean
    std_list = []
    std_list_format = []
    for i in range(-3,4):
        std_dev = np.std(data) * i + np.mean(data)
        std_list.append(std_dev)
        std_list_format.append('{0:.3f}'.format(std_dev) + '\n {} std'.format(i))
        
    # Create a list of corresponding y values
    data_x, data_y = ax.lines[0].get_data()
    height = []
    for i in std_list:
        height.append(np.interp(i, data_x, data_y))
        
    # Plotting vertical lines representing std deviations 
    for a, b in zip(std_list, height):
        plt.axvline(a, 0, b/lim, color = 'black', alpha = 1, linewidth = 0.8, linestyle = '--')
        plt.plot(a, b, marker = 'o', color = 'blue')
    
    # Plotting observed statistic
    obs_line_height = np.interp(obs_stat, data_x, data_y)
    plt.axvline(obs_stat, 0, obs_line_height/lim, color = 'red', alpha = 1, linewidth = 1.5, linestyle = '-')
    plt.plot(obs_stat, obs_line_height, marker = 'o', color = 'red')
            
    # Plotting x ticks
    x_ticks = std_list
    x_labels = std_list_format
    plt.xticks(x_ticks, x_labels)
    plt.ylim(0,lim)
    
import scipy.stats as stats
def shading(data, left, right, color):
    
    # Shading areas
    kde = stats.gaussian_kde(data)
    shade = np.linspace(left, right, 100)
    plt.fill_between(shade, kde(shade), color = color, alpha = 0.2);
```
```
# For fischer test using data dataset and not df
contingency = pd.pivot_table(data=dataset, 
                             index='experiment', 
                             columns='response', 
                             aggfunc='count')['auction_id']

from scipy.stats import fisher_exact
stats, pval = fisher_exact(contingency, alternative="two-sided")

# Print the value
print(f"Fischer Test p-value: {pval:.3f}")

from scipy.stats import norm
zscore = norm.ppf(1 - .05/2)

print(f"ZScore: {zscore:.3f}")

# Calculate mean values
exp_mean = dataset.query('experiment=="exposed"')["yes"].mean()
ctr_mean = dataset.query('experiment=="control"')["yes"].mean()

# Calculate STD values
exp_std = dataset.query('experiment=="exposed"')["yes"].std()
ctr_std = dataset.query('experiment=="control"')["yes"].std()

# The shape
exp_num = dataset.query('experiment=="exposed"')["yes"].shape[0]
ctr_num = dataset.query('experiment=="control"')["yes"].shape[0]

# Calculate pooled variance
var_pooled = (((exp_num-1) * exp_std**2 + (ctr_num-1)*ctr_std**2) / (exp_num + ctr_num-2))**0.5

# Calculate the boarder high and low intervals
CI_low = (exp_mean - ctr_mean) - zscore * var_pooled * (1/exp_num * 1/ctr_num)**0.5
CI_high = (exp_mean - ctr_mean) + zscore * var_pooled * (1/exp_num + 1/ctr_num)**0.5
```
```
# Generate Binomial Distribution
exp_binom = np.random.binomial(exp_num, exp_mean, 100000)/exp_num
ctr_binom = np.random.binomial(ctr_num, ctr_mean, 100000)/ctr_num

# Calculate the diff
binom_diff = exp_binom - ctr_binom

# Generate Normal distribution
norm_dist = np.random.normal(0, np.std(binom_diff), len(binom_diff))

# Visualize
statplot(binom_diff, 15, np.mean(norm_dist), "95% Confidence Interval")
shading(binom_diff, binom_diff.min(), CI_low, "#fc032c")
shading(binom_diff, CI_low, CI_high, "#03fc49")
shading(binom_diff, CI_high, binom_diff.max(), "#fc032c")
plt.show()

print(f"95% Confidence level:  [{CI_low:.2f}, {CI_high:.2f}]") 
```
# Plot All data to Graph and Compare
```
columns = dataset_df.columns
for i in range(len(columns) - 1):
    for j in range(i + 1, len(columns)):
        plt.scatter(dataset_df[columns[i]], dataset_df[columns[j]])
        plt.title(f'Scatter plot: {columns[i]} vs {columns[j]}')
        plt.xlabel(columns[i])
        plt.ylabel(columns[j])
        plt.show()
        ```
``
