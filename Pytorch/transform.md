# pytorch torchvision transform

## Torchvision.Transforms

`Transforms`包含常用图像转换操作。可以使用[`Compose`](https://pytorch.org/docs/stable/torchvision/transforms.html#torchvision.transforms.Compose)将它们链接在一起。 此外，还有[`torchvision.transforms.functional`](https://pytorch.org/docs/stable/torchvision/transforms.html#module-torchvision.transforms.functional)模块，可以对转换进行细粒度控制。 如果需要构建更复杂的图像转换方式，这将很有用。

```python
class torchvision.transforms.Compose(transforms)
```

Example:

```python
transforms.Compose([
     transforms.CenterCrop(10),
     transforms.ToTensor(),
 ])
```

## Transforms on PIL Image

### CenterCrop

```py
class torchvision.transforms.CenterCrop(size)
```

将给定的PIL.Image进行中心切割，得到给定的size，size可以是`tuple`，`(target_height, target_width)`。size也可以是一个`Integer`，在这种情况下，切出来的图片的形状是正方形。

### RandomCrop

```py
class torchvision.transforms.RandomCrop(size, padding=None, pad_if_needed=False, fill=0, padding_mode='constant')
```

切割中心点的位置随机选取。size可以是`tuple`也可以是`Integer`。

### RandomResizedCrop

```py
class torchvision.transforms.RandomResizedCrop(size, 
	  scale=(0.08, 1.0), ratio=(0.75, 1.3333333333333333), interpolation=2)
```

将给定图像裁剪为随机大小和宽高比。裁剪为原始尺寸的随机尺寸（默认值：0.08至1.0）和原始宽高比的随机纵横比（默认值：3/4至4/3）。 最终将其crop为给定大小。 这通常用于训练Inception网络。

### Resize

```py
class torchvision.transforms.Resize(size, interpolation=2)
```

将输入图像调整为给定尺寸。 该图像可以是PIL图像或pytorch张量，在这种情况下，它应具有[…，H，W]形状，其中…表示任意数量的前导尺寸



## 对Tensor进行变换

```py
class torchvision.transforms.Normalize(mean, std)
```

给定均值：(R,G,B)，方差：（R，G，B），将会把Tensor正则化。即：`Normalized_image=(image-mean)/std`。



## ToTensor

```py
class torchvision.transforms.ToTensor
```

把一个取值范围是`[0,255]`的PIL.Image或者shape为`(H,W,C)`的numpy.ndarray，转换成形状为`[C,H,W]`，取值范围是`[0,1.0]`的torch.FloadTensor



## ToPILImage

```py
class torchvision.transforms.ToPILImage
```

将shape为`(C,H,W)`的Tensor或shape为`(H,W,C)`的numpy.ndarray转换成`PIL.Image`，值不变。



## Lambda(lambd)

```py
class torchvision.transforms.Lambda(lambd)
```

通过`Lambda`构建匿名函数，进行图像转换。

### 