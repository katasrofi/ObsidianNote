# Data Prepare and Load
# Prediction
- Use `torch.inference_mode` untuk membuat prediksi lebih cepat karena semua fitur training disable sehingga tidak ada beban memori tambahan
- Make training Loop
```epochs = 2
for epoch in range(epochs):
	model.train()
	
	1. Forward Pass
	y_pred = model(x_train)
	
	2. Calculate the loss
	loss = loss_fn(y_pred, y_test)
	
	3. Optimizer Zero Grad
	optimizer.zero_grad()
	
	4. BackPropagation
	loss.backward()
	
	5. Set the Optimizer
	optimizer.step()
	
	6. Evaluate Model
	model.eval()
```

# Saving Models
Ada tiga metode untuk saving models
- `torch.save()`
- `torch.load()`
- `torch.nn.Module.load_state_dict()`


# Evaluating Model
from torchmetrics import Accuracy, Precision, Recall, F1Score, ConfusionMatrix
### Torchvision data
NCHW - None, Color, Height, Width -- Default P yTorch
NHWC - None, Height, Width, Color -- Default other libraries
# Summary Using torchinfo
