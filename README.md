# 基于yolo5实现的山桃模型

## 修改的地方：

1.在train 238行注释掉了以下语句，因标签不是从零开始的

```
assert mlc < nc, f'Label class {mlc} exceeds nc={nc} in {data}. Possible class labels are 0-{nc - 1}'
```

2.coco128里面放入了自己的数据集地址

```
path: ../datasets/MP  # 数据集的根目录
train: images/train  # 训练集地址
val: images/train  # 验证集地址
test:  # test images (optional) ，暂时不用管

# Classes
nc: 1  # 标签的数量，由于是山桃模型专版，这里为1
names: ['mountain peach']  # 标签名
```

3.山桃模型（杏）存放的权重位置：

```
runs/train/exp13/weights/best.pt
```

4.将数据集的地址和yolov5的地址放在同目录下

5.验证：也可以输入图片，或者摄像头等等，以下是视频

```
python detect.py --source E:/video/VID_20220610_125626.mp4 --weights runs/train/exp13/weights/best.pt
```

6.解帧推荐ffmpeg

```
ffmpeg -i VID_20220610_125739.mp4 -r 5 E:/data/frame%04d.jpg
```



## 效果展示：

[![X2uvB6.md.jpg](https://s1.ax1x.com/2022/06/12/X2uvB6.md.jpg)](https://imgtu.com/i/X2uvB6)

当然，yolov5s.pt正常人物也是可以检测出来的 ,还有输出的视频等，可在exp目录查看

```
runs/detect/exp8、exp9...
```

[![X2ujnx.md.jpg](https://s1.ax1x.com/2022/06/12/X2ujnx.md.jpg)](https://imgtu.com/i/X2ujnx)
