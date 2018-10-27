# 标题、作者
Combining Image and Text Features: A Hybrid Approach to Mobile Book Spine Recognition

Sam S.Tsai, David Chen, Huizhong Chen……

# 摘要
结合文字与图像根据书脊识别图书。首先用书脊文字作为关键词搜索数据库。
以往的识别方法仅匹配图像或者文字，此方法两种方法兼顾，正确率上升。
截图图像时去除透视变形。
文字定位采用[Maximally Stable Extremal Regions (MSER)](https://en.wikipedia.org/wiki/Maximally_stable_extremal_regions)和Stroke Width Transform (SWT)。识别文字使用[Optical Character Recognition (OCR)](https://en.wikipedia.org/wiki/Optical_character_recognition)

# 截取书脊
1. 检测书脊的边缘垂直线
2. 直接把垂直线的两端连接，形成四边形。

# 获取文字
1. 使用MSER和SWT检测文字。
2. 截取文字部分图像，使用滤波器去除噪音。
3. 使用OCR engine来识别文字。

# 文字搜索
- 使用[Inverted files Index（文件倒排索引）](https://blog.csdn.net/Woolseyyy/article/details/51559937)的方法
- Nearest neighbor word matching.

# 识别图像
- [Speed-Up Robust Features (SURF)](https://opencv-python-tutroals.readthedocs.io/en/latest/py_tutorials/py_feature2d/py_surf_intro/py_surf_intro.html)加速稳健特征
- [RANdom SAmple Consensus (RANSA)](https://blog.csdn.net/u013339596/article/details/18797667)随机抽样一致