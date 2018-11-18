# AUTOMATIC LIBRARY SHELF READING FROM BOOK-SPINE IMAGE RECOGNITION

- Akara Thammastitkul, Tatchayaphone Suriwong

## 解决问题

图书分类放置，相同类的书放在一起

## 基本方法

1. 根据图书类别，给每本书贴上颜色不同的圆形标签
2. 使用DoG(Defference of Gaussians)检测边缘
3. 使用兴趣区方法挑选出圆形的部分
4. 根据圆形部分的颜色匹配到图书类别