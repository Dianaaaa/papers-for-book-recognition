# 标题、作者
Book Spine Segmentation for Bookshelf Reorganization

Lior Talker

# 摘要
解决书架上书籍位置错乱的问题，使得最终书籍按照高矮顺序摆放，且被扶正（:disappointed_relieved:)。照片是斜着拍的立体图。
提出一个方法来分割书脊部分的图片。解决背景明暗不均匀的问题。
方法分两步走：第一步从一个有着和书形状相似的物品的杂乱背景中分割得到候选的图像集。第二步用物理约束来筛选第一步得到的图片。
选取的方法是the active contours paradigm的变种。使用预先定义的边缘形状和四边形的透视投影（PR）。使用expanding seed的方法，（详情参见：[Seed, Expand and Constrain: Three Principles for Weakly-Supervised Image Segmentation 论文笔记](https://blog.csdn.net/zjc8888888888/article/details/80641063)）分割图片。
计算空间的一对消失点来约束切割图片的形状。

# Book Spine Segmentaion
第一步，获取与图像梯度和透视一致的PR候选集
第二步，根据其位置、空间关系和大小从第一步得到的候选集筛选。
假定书脊在同一个平面$\pi$，书脊们的一对消失点在直线$l$。
## 一、Identifying PR Candidates
### （一）、PR的参数化
四边形的位置由其四个顶点（8个参数）决定，假定PR的一个内部点$s$和平面$\pi$的成角透视消失点$v$、$v_\bot$可以获取，则只需5个参数，分别是：
- 决定成角透视点$v$、$v_\bot$的参数$\alpha$

