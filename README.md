# Liver Segmentation
Unet network for liver CT image segmentation

## 使用提示

该项目网络结构如下图，参考文献：U-Net: Convolutional Networks for Biomedical Image Segmentation

![avatar](https://lmb.informatik.uni-freiburg.de/people/ronneber/u-net/u-net-architecture.png)

项目文件分布如下
```
  --project
  	main.py
  	 --data
   		--train
   		--val
```

直接修改main.py中的main函数为train或test，并设置好test函数中模型路径即可直接运行main.<span>py

本实现使用的数据集和模型文件可以使用百度云下载，链接如下: 

链接: https://pan.baidu.com/s/1LbhpNMyqc9dN1G70lrUTmA 提取码: s7j0

全部数据集: https://competitions.codalab.org/competitions/15595



## 多类别实现
修改2个地方即可：unet最后一层的通道数设置为类别数；损失函数使用交叉熵损失函数
```python
bath_size,img_size,num_classes=2,3,4
#model = Unet(3, num_classes)
criterion = nn.CrossEntropyLoss()
#assume the pred is the output of the model
pred=torch.rand(bath_size,num_classes,img_size,img_size)
target=torch.randint(num_classes,(bath_size,img_size,img_size))
loss=criterion(pred,target)
```
