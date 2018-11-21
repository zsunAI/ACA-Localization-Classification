# ACA-Localization-Classification-Based-on-Spaeth
## 定位算法 
在UBM图像中，首先自动定位房角隐窝的顶点。确定虹膜末端边界点，以虹膜末端的边界点作为起始点，在二值图像中依次向左分别标记每一列像素为1的点的位置并统计像素值为1的点的个数。当每一列上端、下端出现0像素的点时，分别停止该列上、下两端的运算和点的统计。效果如下：
![image](https://github.com/1579477793/ACA-Localization-Classification-Based-on-Spaeth/blob/master/data/a.bmp)   
![image](https://github.com/1579477793/ACA-Localization-Classification-Based-on-Spaeth/blob/master/data/b.bmp)
![image](https://github.com/1579477793/ACA-Localization-Classification-Based-on-Spaeth/blob/master/data/c.bmp)
![image](https://github.com/1579477793/ACA-Localization-Classification-Based-on-Spaeth/blob/master/data/d.bmp)

### 基于灰度特征的方法分类：
拟合出房角内侧边缘，并计算出房角隐窝角度、定性分析虹膜形态以及虹膜根部灰度特征等参数，最后基于Spaeth分级法将前房角分为开闭窄三类

![image](https://github.com/1579477793/ACA-Localization-Classification-Based-on-Spaeth/blob/master/data/e.bmp)
![image](https://github.com/1579477793/ACA-Localization-Classification-Based-on-Spaeth/blob/master/data/f.bmp)
![image](https://github.com/1579477793/ACA-Localization-Classification-Based-on-Spaeth/blob/master/data/g.bmp)
### 利用Libsvm进行分类：
首先分割出n×n的前房角区域；然后利用PCA技术进行压缩图像以降低图像的冗余度，使用HOG进行特征提取，对于特征向量使用L2范数归一化，避免过拟合，提升模型的泛化能力；最后为得到最佳模型的参数用5-折交叉枚举计算。
## 结果：
### 基于灰度特征的分类结果
                                   表1 各类分级方法的二分类效果比较
![image](https://github.com/1579477793/ACA-Localization-Classification-Based-on-Spaeth/blob/master/data/k.bmp)

(目前绝大多数算法都只能将图像分为两类,故单独将二分类效果放在一起比较，利用这种方法三分类准确率为75.93%。每张图像分类平均用时为1.364s)
### 基于SVM的三分类结果
该方法每幅图像只需0.132s，准确率为89.33%
##  
[1]Xu Y, Liu J, Tan N M, et al. Anterior chamber angle classification using multiscale histograms of oriented gradients for glaucoma subtype identification[C]// Engineering in Medicine and Biology Society. IEEE, 2012:3167-3170.

[2]Xu Y, Wong D W K, Baskaran M, et al. Automated anterior chamber angle localization and glaucoma type classification in OCT images[J]. Conf Proc IEEE Eng Med Biol Soc, 2013, 2013:7380-7383.

[3]Fu H, Xu Y, Lin S, et al. Segmentation and Quantification for Angle-Closure Glaucoma Assessment in Anterior Segment OCT.[J]. IEEE Transactions on Medical Imaging, 2017, PP(99):1-1.

[4]Ni, S. N., Tian, J., Marziliano, P., & Wong, H. T.. Anterior chamber angle shape analysis and classification of glaucoma in ss-oct images[J]. Journal of Ophthalmology,2014,(2014-8-5), 2014, 2014(1):942367.
