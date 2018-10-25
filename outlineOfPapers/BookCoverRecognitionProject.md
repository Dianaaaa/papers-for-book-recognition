# 相似工作
- Video-based Car Surveilance: License Plate, Make, and Model Recognition
- Shape Matching and Object Recognition Using Low Distortion Correspondence

# 数据库
从Google Print Beta、Amazon获取

# 拍摄图片
- 稍差质量的图片： webcam拍摄
- 质量好的图片：数码相机拍摄

# ROI兴趣区和分割

# 识别的特征
- Affine Covariant Region Detectors(特别是Harris Affine transformation)
- SIFT(Scale Invariant Keypoints)
- 使用不同的算法实验（欧式距离/RANSAC）

# 分类算法
逻辑：先将图书分类成多个簇，匹配时先匹配到簇，再匹配到单个图片。
- K-means算法
- SVM支持向量机