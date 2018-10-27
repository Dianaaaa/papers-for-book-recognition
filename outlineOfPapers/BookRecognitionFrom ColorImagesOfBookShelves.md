# 标题、作者
Book Recognition from COLOR images of Book Shelves

Yukari Akiyama, Minoru Ito

# Introduction
1. 采用min/max filtering来切取书脊图像， 可以有效避免阴影的影响
2. 通过分析HSY图片和edge direction distribution来切取书脊

# 获取HSY图像
放置一张粉色的背景在书后面以避免深色背景不稳定的色彩
图片的RGB值转换成HSY值以产生:
- H(hue) image （色相）
- S(saturation) image （饱和度）
- Y(intensity) image （明亮度）

$$ Y = 0.3R+0.59G+0.11B\\
H = tan^{-1}(C_1/C_2 - \alpha) \\
s = \sqrt{C_1^2 + C_2^2}$$

其中$ C_1 = R - Y，C_2 = B - Y$，$\alpha$是色相角

获得四张图片：
- (a) Intensity [Intensity Image] 
- (b) Hue I [Hue Image 当 $\alpha$ 为$0\degree$]
- (c) Hue II [Hue Image 当$\alpha$ 为$90\degree$]
- (d) Saturation [Saturation image]
# 提取书的边缘
使用一个3 * 3的特殊滤波器计算边缘强度分布，然后图像的最大边缘强度水平来归一化。
使用hue和saturation image，能够使灰度相近的书脊被识别出来
1. 将上面提到的四张图合成一张。合成公式：
   $$ f(x,y) = max\{f_i(x,y)|i = 1,2,3,4\}$$
2. 将处理得到的unified edge image使用empirically given level（实验得到）阈值化，此法利于消除书籍上文字的边缘，从而更方便提取书脊区域。
3. Hough变化，常用于检测边缘图像中直线。识别出偏斜不超过$20\degree$的直线（inverse Hough transformation）
4. 找到书脊的上下边界，即找到跟垂直线相交的线。
# 提取书脊文字
基于min/max filtering，解决文字背景不均匀问题
1. 单独截取每本书的区域。
2. 然后使用min/max filter，如果文字明亮度大于文字背景，使用minimun filter扫描图片；如果文字明亮度小于文字背景，使用maxmmum filter扫描图片。
3. 得到背景一致，文字醒目的图片。

# 识别图书（跟项目关系不大）
1. 准备书脊图片数据库，宽度一致
2. 准备两个参数，第一是大号字如书的标题，第二个是小号字如信息如作者等。
3. 比较输入图片和数据库图片。

# 总结
- HSY图片
- 边缘分布
- Hough transformation
- 对比
