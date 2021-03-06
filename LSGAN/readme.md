# LSGAN

LSGAN 全称Least Squares GANs(最小二乘GAN)

### 解决问题
1. 针对标准的GAN生成的图像质量不高
2. 训练过程不稳定

### 改进方法
将GAN的目标函数由交叉熵损失 换成 最小二乘损失

### 最小二乘损失
作者认为交叉熵损失使得生成器不会再优化那些被判别器识别为真实图片的生成图片，即使这些生成图片距离判别器的决策边界仍然很远；(因为这个时候交叉熵损失已经很小了，判别器默认生成的图片已经ok了)
    
sigmoid交叉熵损失很容易就达到饱和状态（饱和是指梯度为0），而最小二乘损失只在中间点一点达到饱和
![交叉熵&最小二乘](https://github.com/jiangfeng94/Pytorch_Learning/blob/master/LSGAN/%E4%BA%A4%E5%8F%89%E7%86%B5%26%E6%9C%80%E5%B0%8F%E4%BA%8C%E4%B9%98.jpg) 
最小二乘损失：
认为生成图片和真实数据之间的距离可以由生成图片和决策边界之间的距离来反映。这是因为学到的决策边界必须穿过真实数据点，否则就是学习过程饱和了。
### 损失函数
![最小二乘损失函数](https://github.com/jiangfeng94/Pytorch_Learning/blob/master/LSGAN/%E6%9C%80%E5%B0%8F%E4%BA%8C%E4%B9%98%E6%8D%9F%E5%A4%B1%E5%87%BD%E6%95%B0.jpg)

### 工作展望
在未来工作中作者也提到可以改进的一点就是直接把生成图片拉向真实数据，而不是拉向决策边界。