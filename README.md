# WaterFaceReg
利用训练的人类识别器 分类器样板进行人脸识别，成功率还是可以的
效果图：
![image](https://github.com/caiyishui/WaterFaceReg/blob/master/raw/111.png)
![image](https://github.com/caiyishui/WaterFaceReg/blob/master/raw/222.png)
![image](https://github.com/caiyishui/WaterFaceReg/blob/master/raw/333.png)

处理流程与原理：
第一步：
1. NDK 环境
2. 加载分类器 先加载资源的分类器
第二步：
3. 将java层的surface传递到JNI层形成对应的nativeWindow用于原生绘制.
4. 在将画布传到 JNI层后，我们需要对加载来的bitmap执行识别工作。
       如何识别图像：
   1. 将bitmap 转变成为OpenCV 可以识别的格式
   2. 将图像转变为灰度图像
   3. 将直方图均匀化，增强对比效果
   4. 识别
   5. 画一个识别的矩形框到图像中
       原生绘制：
   6. 锁定绘图区
   7. 将颜色进行转变，转变成为RGBA 格式的图片，
   8. 将数据绘制到 windowbuffer 上面
   9.解锁