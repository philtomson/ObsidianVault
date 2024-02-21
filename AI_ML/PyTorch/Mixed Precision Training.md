|  |
| ---- |
| Use **torch.cuda.amp** in PyTorch for mixed precision training. This method mixes 32-bit and 16-bit data to reduce memory use and speed up model training, without much loss in accuracy.   <br><br>  <br><br>It takes advantage of the quick computing of 16-bit data and controls precision by handling specific operations in 32-bit. This approach offers a balance between speed and accuracy in training models. |
| <br>`import torch`<br>`from torch.cuda.amp import autocast, GradScaler`<br>`from torch import nn, optim`<br><br>`model = nn.Linear(10, 2).cuda()`<br>`optimizer = optim.SGD(model.parameters(), lr=0.01)`<br>`scaler = GradScaler()`<br><br>`data, target = torch.randn(5, 10).cuda(),` <br> `torch.randint(0, 2, (5,)).cuda()`<br><br>`optimizer.zero_grad()`<br><br>`with autocast():`<br> `loss = nn.functional.cross_entropy(model(data), target)`<br><br>`scaler.scale(loss).backward()`<br>`scaler.step(optimizer)`<br>`scaler.update()`<br><br> |
|  |
