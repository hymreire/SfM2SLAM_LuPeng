## 摄像机标定
摄像机标定：求解摄像机内外参

目标：从1张或多张图像估算内外参

透视投影方程：p=MP=K\[R,T\]P

标定板：得到世界点P和像素点p

![](attachments/Pasted%20image%2020251025142755.png)

1对点可以得到2个方程，6对点可以得到12个方程，总共11个未知数，可以求解。  
不过一般选取的点都远超于6个，避免线性解性质不好。

![](attachments/Pasted%20image%2020251025143142.png)

超定方程用最小二乘法解。

![](attachments/Pasted%20image%2020251025143551.png)

具体求法，可以写代码求解，这里的m范数存在一个未知数乘：

![](attachments/Pasted%20image%2020251025143811.png)

提取摄像机参数，这里的m范数存在一个未知数乘：

![](attachments/Pasted%20image%2020251025144016.png)

内外参的推导听不懂，大概就是用旋转阵的正交性来消元，不推，推了也没用，跳过，直接看结论就好：

![](attachments/Pasted%20image%2020251025145249.png)

要求：不能让所有点都取在一个平面上，否则会退化：

![](attachments/Pasted%20image%2020251025145455.png)

## 径向畸变
径向畸变：像素以畸变中心为中心点，沿着径向产生位置偏差，从而导致图像中所成像发生形变。

径向畸变模型，离中心越远的像素收缩的越厉害：

![](attachments/Pasted%20image%2020251025170558.png)

方程非线性：

![](attachments/Pasted%20image%2020251025172711.png)

最小二乘法可以用优化方法解决：

![](attachments/Pasted%20image%2020251025172811.png)

除法消元构造线性方程组，先把m1、m2求出来：

![](attachments/Pasted%20image%2020251025173133.png)

最后把剩下的非线性方程未知数求出来就好了【已经求出的部分也可以再优化一下，避免线性解出现不好的性质】：

![](attachments/Pasted%20image%2020251025173227.png)

## 2D和3D的变换
2D，欧式变换，等距变换，旋转平移和镜像：

![](attachments/Pasted%20image%2020251025181928.png)

2D，相似变换，均匀伸缩：

![](attachments/Pasted%20image%2020251025182003.png)

2D，仿射变换，平行保持：

![](attachments/Pasted%20image%2020251025182122.png)

2D，透视变换，共线点交比保持（没学过）：

![](attachments/Pasted%20image%2020251025182146.png)

3D，欧式变换：

![](attachments/Pasted%20image%2020251025182314.png)

3D，仿射变换：

![](attachments/Pasted%20image%2020251025182342.png)

3D，透视变换：

![](attachments/Pasted%20image%2020251025182351.png)