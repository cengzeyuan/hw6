# hw6
# 数字图像处理第六次作业  
**学生姓名：曾泽源  
班级：自动化65  
学号：2160504116  
提交日期：2019/4/1**  
**摘要：**  图像的复原和重建是图像处理领域的一个重要的分支，它和图像增强一样都是以预先确定的目标来改善图像，但是图像的复原和重建是面向退化模型的，它是基于图像退化的先验知识采取相反的方式对图像进行处理，来恢复、增强原图像的。本文基于基本退化模型，在此基础上对图像的Gaussian noise、salt & pepper和运动模糊通过不同的滤波器进行处理，对比分析优劣。  
**关键词：Gaussian noise,salt & pepper,运动模糊、维纳滤波器、约束最小二乘滤波器、退化、谐波均值、逆谐波均值、中点、中值、算术、几何、最大最小、修正的阿尔法**  
  
Project6：
----------------------------------------
1.在测试图像上产生高斯噪声lena图-需能指定均值和方差；并用多种滤波器恢复图像，分析各自优缺点；  
2.在测试图像lena图加入椒盐噪声（椒和盐噪声密度均是0.1）；用学过的滤波器恢复图像；在使用反谐波分析Q大于0和小于0的作用；  
3.推导维纳滤波器并实现下边要求；  
(a) 实现模糊滤波器如方程Eq. (5.6-11).  
(b) 模糊lena图像：45度方向，T=1；  
(c) 再模糊的lena图像中增加高斯噪声，均值= 0 ，方差=10 pixels 以产生模糊图像；  
(d)分别利用方程 Eq. (5.8-6)和(5.9-4)，恢复图像；并分析算法的优缺点.  
  
结果讨论：   
----------------------------------------  

## 1.  
####  Gaussian噪声   
**结果展示：**    
![](https://github.com/cengzeyuan/hw6/blob/master/2160504116/1.1.jpg)
**结果分析：**  
通过观察图像不难看出，当Gaussian噪声均值不变为0时，随着方差增加，噪声越密集，图像受噪声影响越严重越明显；而当Gaussian噪声方差不变时，均值将影响到整个图像的灰度值，均值的增大会使整个图像变亮。
####  算术均值滤波  
**结果展示：**  
![](https://github.com/cengzeyuan/hw6/blob/master/2160504116/1.2.jpg)  
####  几何均值滤波  
**结果展示：**  
![](https://github.com/cengzeyuan/hw6/blob/master/2160504116/1.3.jpg)  
####  谐波均值滤波  
**结果展示：**  
![](https://github.com/cengzeyuan/hw6/blob/master/2160504116/1.4.jpg)  
####  逆谐波均值滤波  
**结果展示：**  
![](https://github.com/cengzeyuan/hw6/blob/master/2160504116/1.5.jpg)  
####  中点滤波  
**结果展示：**  
![](https://github.com/cengzeyuan/hw6/blob/master/2160504116/1.6.jpg)  
**结果分析：**  
算术均值滤波器算是一个中规中矩的滤波器，它可以平滑一个图像中的局部变化，故而在去除噪声的时候他也将使源图像模糊；  
几何均值滤波器与算术均值滤波器相仿，但是几何滤波器在图像较暗区域及附近出现黑色正方形点，对图像质量造成影响；  
谐波滤波会使原图像变暗，虽然如此，但是他对于高斯噪声的处理效果较好；同时，谐波滤波器在图像较暗区域及附近出现黑色正方形点，对图像质量造成影响；  
逆谐波滤波器（Q>0）使原图像变亮，对高斯噪声的处理比较中规中矩，需要合理选择参数。  
中点滤波器对于随机噪声的处理应该有较好的效果，但是在这些滤波器中，对于这样的一张图片，并没有太突出。  

## 2. 
####  salt & pepper  
####  中值滤波  
**结果展示：**    
![](https://github.com/cengzeyuan/hw6/blob/master/2160504116/2.1.jpg)  
####  最大值、最小值滤波  
**结果展示：**   
![](https://github.com/cengzeyuan/hw6/blob/master/2160504116/2.2.jpg)  
####  修正的阿尔法滤波  
**结果展示：**   
![](https://github.com/cengzeyuan/hw6/blob/master/2160504116/2.3.jpg)  
####  谐波均值滤波  
**结果展示：**   
![](https://github.com/cengzeyuan/hw6/blob/master/2160504116/2.4.jpg)  
####  反谐波滤波  
**结果展示：**   
![](https://github.com/cengzeyuan/hw6/blob/master/2160504116/2.5.jpg)  
**结果分析：**   
对比可以看出，中值滤波器对于椒盐噪声的处理毫无疑问是最好的，同时它引起的模糊也不大，对于椒盐噪声此类冲激噪声去除效果特别好。  
最大最小值滤波器，分别对于椒、盐单独噪声的处理效果较好，但若是处理混合噪声的话，则会导致另一种噪声信号的突出，严重影响原图，故而不适合在椒盐混合噪声的处理中使用。  
修正的阿尔法均值滤波器可退化成中值滤波器，在合理选择参数的情况下对于椒盐噪声的处理也尚可；此外，对于多样的噪声混合的情况，修正的阿尔法均值滤波器处理效果应该会更为突出。   
谐波滤波器并不适用于处理椒盐噪声。在椒盐噪声污染的情况下，经过谐波滤波后反而使得图像更为糟糕；
反谐波滤波器通过参数的不同选择，会得到不一样的结果。当Q大于0时，对于去除图像的椒噪声是有效的，但是也相应让盐噪声更为严重，同时相较于最大值滤波器而言，反谐波滤波器对图像原始信息的保留更加完整清晰；当Q小于0时，对于去除图像额的盐噪声是有效的，但是也相应让椒噪声更为严重。可以看出，反谐波滤波器对处理单一椒噪声或者单一盐噪声效果都很好，但是并不适合处理混合噪声。  

## 3.   
####  维纳滤波器推导&最小二乘原理
（由于不会使用markdown编辑公式，选择直接粘贴图片）
![](https://github.com/cengzeyuan/hw6/blob/master/wiener%26least-square%20method/1.jpg)  
![](https://github.com/cengzeyuan/hw6/blob/master/wiener%26least-square%20method/2.jpg)  
![](https://github.com/cengzeyuan/hw6/blob/master/wiener%26least-square%20method/3.jpg)  
![](https://github.com/cengzeyuan/hw6/blob/master/wiener%26least-square%20method/4.jpg)  
![](https://github.com/cengzeyuan/hw6/blob/master/wiener%26least-square%20method/5.jpg)  
####  模糊lena图像  
####  在模糊的lena图像中增加高斯噪声  
####  Wiener滤波器
**结果展示：**  
![](https://github.com/cengzeyuan/hw6/blob/master/2160504116/3.1.jpg)  
![](https://github.com/cengzeyuan/hw6/blob/master/2160504116/3.2.jpg) 
（MATLAB自带的函数得到的Wiener滤波效果如下）
![](https://github.com/cengzeyuan/hw6/blob/master/2160504116/MATLABWiener1.jpg)   
**结果分析：** 
对于自己设计的wiener滤波器，在选择合适的K的情况下，可以对运动模糊+高斯噪声的图像有一定的恢复，但是如果K选择不好，效果很差。 这里对于K值的选择，选取K初始值为10，采用wiener滤波后的图像矩阵与原图像矩阵的矩阵距离的平方为参照，当该距离平方小于2时，输出滤波后图像和K，否则K不断减少0.01；得到的合适的K值接近于0。  
对于MATLAB自带的运动模糊函数，得到的模糊效果是左下到右上的模糊效果，而自己编写的运动模糊是左上到右下的模糊效果，即在不同对角线上的模糊。而MATLAB自带的函数Wiener滤波处理后，对运动模糊的处理效果较好，但噪声影响未被较好去除，导致滤波后图像质量并不佳。  
####  约束最小二乘滤波器  
**结果展示：**    
![](https://github.com/cengzeyuan/hw6/blob/master/2160504116/3.3.jpg)  
![](https://github.com/cengzeyuan/hw6/blob/master/2160504116/3.4.jpg) 
![](https://github.com/cengzeyuan/hw6/blob/master/2160504116/3.5.jpg)  
![](https://github.com/cengzeyuan/hw6/blob/master/2160504116/3.6.jpg)  
**结果分析：**   
对于最小二乘滤波器，参数V得自己确定,而与K类似，参数的选择对图像处理的影响较大。首先尝试对V在0.000001到0.01之间随机取数，同Wiener滤波器考虑使用滤波后图像的矩阵与原图像矩阵的矩阵距离的平方为参照，随机取1000次，选择最佳的V和最小的矩阵距离的平方。可以看出，理想V值应该在0.00005附近，同时得到的结果也较为理想。  
之后，令V从0.000001开始，迭代1000次，每次V增加0.000001，比较选取最小的矩阵距离。 
从迭代的过程不难看出，0.00004是一个很理想的局部（0.001至0.000001间，精度为0.000001）最优值，得到的滤波后图像效果也较理想。    
在选择较合适参数的情况下，最小二乘滤波算法的结果优于维纳滤波的结果，在更好处理运动模糊的同时，也很好地抑制了噪声的影响。    

参考文献：
---------------------------------------- 
[1]《数字图像处理（第三版）》Rafael C.Gonzalez、Richard E.Wodds等著；阮秋琦 阮智宇等译、电子工业出版社  
[2]CSDN，椒盐噪声， <u>https://blog.csdn.net/sunmc1204953974/article/details/50622940</u>  
[3]CSDN，[数字图像处理]图像去噪初步(1)—均值滤波器，<u>https://blog.csdn.net/zhoufan900428/article/details/37698107</u>  
[4]cnblogs，图像加噪和图像滤波，<u>http://www.cnblogs.com/hustlx/p/5245522.html</u>  
[5]CSDN，中值滤波，<u>https://blog.csdn.net/tiemaxiaosu/article/details/51660558</u>  
[6]CSDN，维纳滤波，<u>https://blog.csdn.net/weiweiwanye/article/details/53709493?locationNum=8&fps=1</u>  
