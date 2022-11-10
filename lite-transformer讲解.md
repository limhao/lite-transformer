---
title: lite transformer讲解
---

### 传统transformer

![](https://pic1.imgdb.cn/item/636bbb0d16f2c2beb1aacb34.png)

传统

input 通常包含 数据的长度N 数据的维度d

### 模型参数量与性能对比

![](https://pic1.imgdb.cn/item/636bbb0d16f2c2beb1aacb3b.png)

d下降的情况下，会导致attention单元 上下文捕捉关系不足，导致效果差

d不变的情况下，会导致参数量变多，上下文捕获好，效果好

作者的想法 d不变，参数量给他变少一点 同时效果较好

作者在 维度 和 局部和全体关注下 下了功夫

### LSRA (长短距离注意力)

![](https://pic1.imgdb.cn/item/636bbb0d16f2c2beb1aacb43.png)

翻译任务要注意全局以及上下文

左侧为传统transformer结构

右侧为专门处理局部关系的卷积分支

LSRA 模块遵循两分支设计。左侧注意力分支负责捕获全局上下文，右侧卷积分支则建模局部上下文。研究者没有将整个输入馈送到两个分支，**而是将其沿通道维度分为两部分，然后由后面的 FFN 层进行混合**。这种做法将整体计算量减少了 50% 

### 啥是GLU

https://zhuanlan.zhihu.com/p/359147080

GLU(Gated Linear Unit，门控线性单元)

**核心**： GLU可以理解为能够并行处理时序数据的CNN网络架构，即利用CNN及门控机制实现了RNN的功能。优点在进行时序数据处理时严格按时序位置保留信息从而提升了性能，并且通过并行处理结构加快了的运算速度。 

![](https://pic1.imgdb.cn/item/636c617016f2c2beb18ea90d.jpg)







