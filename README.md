### Use PyTorch to build the following model
- Deep NN:
      conv - relu - conv- relu - pool -
      conv - relu - conv- relu - pool -
      conv - relu - conv- relu - pool -
      affine - relu - dropout - affine - dropout - softmax

- Initialize parameters by kaiming_normal 
- Use dropout after fully-connected layers


### Test memo:

#### Model 1
|dataset size(train/test)|#epoch|      model  |  optimizer | parameters |lr| accuracy  |
|-----------------------|-------|--------------|------------|------------|--|------------|
|60000/10000|5|(conv - relu - conv- relu - pool)x2, linearx1 |torch.optim.SGD|-|0.01| 97.03%|
|60000/10000|5|(conv - relu - conv- relu - pool)x2, linearx1 |torch.optim.Adam|-|0.01| 97.69%|
|60000/10000|5|(conv - relu - conv- relu - pool)x2, linearx1 |torch.optim.Adam|Kaiming He|0.01| 98.48%|
|60000/10000|5|(conv - relu - conv- relu - pool)x2, linearx1 |torch.optim.Adam|Kaiming He|0.001| 99.11%|

#### Model 2
|dataset size(train/test)|#epoch|      model  |  optimizer | parameters |lr| accuracy  |
|-----------------------|-------|--------------|------------|------------|--|------------|
|60000/10000|5|(conv - relu - conv- relu - pool)x3, linear-relu-dropout-linear-dropout |torch.optim.Adam|Kaiming He|0.01| 96.83%|
|60000/10000|10|(conv - relu - conv- relu - pool)x3, linear-relu-dropout-linear-dropout |torch.optim.Adam|Kaiming He|0.001| 99.15%|
|60000/10000|20|(conv - relu - conv- relu - pool)x3, linear-relu-dropout-linear-dropout |torch.optim.Adam|Kaiming He|0.001| 99.37%|