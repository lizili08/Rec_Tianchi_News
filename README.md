### 本项目基于[阿里天池新闻推荐赛](https://tianchi.aliyun.com/competition/entrance/531842/rankingList)的Datawhale方案复现
### 此次比赛是新闻推荐场景下的用户行为预测挑战赛， 该赛题是以新闻APP中的新闻推荐为背景， 目的是要求我们根据用户历史浏览点击新闻文章的数据信息预测用户未来的点击行为， 即用户的最后一次点击的新闻文章， 这道赛题的设计初衷是引导大家了解推荐系统中的一些业务背景， 解决实际问题。

### 该数据来自某新闻APP平台的用户交互数据，包括30万用户，近300万次点击，共36万多篇不同的新闻文章，同时每篇新闻文章有对应的embedding向量表示。为了保证比赛的公平性，从中抽取20万用户的点击日志数据作为训练集，5万用户的点击日志数据作为测试集A，5万用户的点击日志数据作为测试集B。具体数据表和参数， 大家可以参考赛题说明。下面说一下拿到这样的数据如何进行理解， 来有效的开展下一步的工作。

### 评价指标的公式如下：
 ![image](https://github.com/user-attachments/assets/dcee9312-61a9-4e0e-bda0-7f059baa732b)
