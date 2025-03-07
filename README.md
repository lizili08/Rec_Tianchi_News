# [阿里天池新闻推荐赛Datawhale方案复现项目](https://tianchi.aliyun.com/competition/entrance/531842/rankingList)

## 项目简介
本项目旨在基于阿里天池新闻推荐场景下的用户行为预测挑战赛，结合Datawhale的方案进行复现，以深入学习推荐比赛的相关知识和技能。

## 赛题理解
### 赛题简介
本次比赛是一个新闻推荐场景下的用户行为预测挑战赛，背景为新闻APP中的新闻推荐。目标是根据用户历史浏览点击新闻文章的数据信息，预测用户未来的最后一次点击的新闻文章，引导参与者了解推荐系统业务背景并解决实际问题。

### 数据概况
数据来自某新闻APP平台的用户交互数据，涵盖30万用户、近300万次点击以及36万多篇不同的新闻文章，每篇新闻文章有对应的embedding向量表示。训练集为20万用户的点击日志数据，测试集A和测试集B分别为5万用户的点击日志数据。具体数据表和参数可参考赛题说明。

## 评价方式理解
根据提交文件格式（sample.submit.csv），针对每个用户需给出五篇文章的推荐结果，按点击概率从高到低排序。真实的每个用户最后一次点击的文章仅有一篇。评价指标公式为：

$$
score(user) = \sum_{k = 1}^{5} \frac{s(user, k)}{k} 
$$

其中，若第 $k$ 篇文章命中真实点击文章，则 $s(user, k) = 1$，否则为 $0$。若都未命中，则 $score(user) = 0$。

## 赛题解决思路
赛题目标是根据用户历史浏览点击数据预测用户最后一次点击的新闻文章。与普通结构化比赛不同，此次比赛在目标和数据上具有特殊性：
1. **目标**：预测的是新闻文章，而非数值或数据类别。
2. **数据**：是基于真实业务场景的用户点击日志，而非传统的特征+标签数据。

因此，需要将预测问题转化为监督学习问题（特征+标签），进而进行建模预测。通过思考，将原问题转化为点击率预测问题（用户, 文章） --> 点击的概率（软分类），即用户是否会点击某篇文章作为分类标签，用户和文章作为特征，训练分类模型预测用户最后一次点击某篇文章的概率。

同时，还需解决以下问题：
1. 如何将问题转化为监督学习问题？
2. 训练集和测试集如何制作？
3. 可利用的特征有哪些？
4. 可尝试哪些模型？
5. 面对大规模文章和用户推荐，如何缩减问题规模？
6. 如何进行最后的预测？

