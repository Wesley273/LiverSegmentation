# unet liver
Unet network for liver CT image segmentation

## 使用提示
项目文件分布如下
```
  --project
  	main.py
  	 --data
   		--train
   		--val
```

数据和权重可以使用百度云下载 链接: 

链接: https://pan.baidu.com/s/1yLDLVlxXPZYORHs12usV2w 提取码: cvb6

全部数据集: https://competitions.codalab.org/competitions/15595

```
## 多类别实现
修改2个地方即可：unet最后一层的通道数设置为类别数；损失函数使用CrossEntropyLoss
```python
bath_size,img_size,num_classes=2,3,4
#model = Unet(3, num_classes)
criterion = nn.CrossEntropyLoss()
#assume the pred is the output of the model
pred=torch.rand(bath_size,num_classes,img_size,img_size)
target=torch.randint(num_classes,(bath_size,img_size,img_size))
loss=criterion(pred,target)
```
