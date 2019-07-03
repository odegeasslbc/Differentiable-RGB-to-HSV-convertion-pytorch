# Differentiable-RGB-to-HSV-convertion-pytorch
A pytorch implementation that converts image RGB color space into HSV allowing differentiable back-propagate


## Value range
Each H,S,V are values in the range of [0, 1]


## How to use
It comes within a Loss function
```
from pytorch_hsv import HSVLoss

target_h = 0 #red color
target_s = 0.5
target_v = 0.8
loss_hsv = HSVLoss(h=target_h, s=target_s, v=target_v, threshold_h=0.03, threshold_sv=0.1)
```
Convert rgb image into hsv space
```
img_rgb = torch.rand(1,3,256,256)
img_hue, img_saturation, img_value = loss_hsv.get_hsv(img_rgb)
# img_hue, ig_stauration and img_value each has the size of 1*256*256
```
Compute the loss given an image and target hsv
```
# you can compute the loss value between img_rgb and target h,s,v directly
loss = loss_hsv(img_rgb)
```
You can also convert back from hsv to rgb
```
r,g,b = loss_hsv.get_rgb_from_hsv()
```
