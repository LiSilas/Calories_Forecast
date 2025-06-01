项目简介：
本项目基于 Kaggle 比赛 Predict Calorie Expenditure Playground Series - Season 5, Episode 5，使用 XGBoost、LightGBM、CatBoost 模型融合，搭建卡路里消耗预测模型。

项目结构：
```
calories_forecast/
├── output/
│ └── submission.csv
├── calories_forecast.ipynb
├── README.md
├── README.zh.md
```

注意：由于 Kaggle 中的文件路径与本地不同，如果想在本地运行该项目，请将 calories_forecast.ipynb 中的数据读取路径改为本地路径。
**因为版权限制，如需原始数据集，请自行前往 Kaggle 下载并解压到相应位置。**

项目流程：
1、读取 train.csv 与 test.csv，输出数据维度、数据类型和基本统计信息；
2、使用 LabelEncoder() 对性别特征进行编码；
3、绘制每个特征与目标变量 Calories 的散点图、热力图、箱型图以及 KDE 分布图，探索各特征与目标变量之间的关系，识别影响较大的特征；
4、对目标变量应用 np.log1p() 进行对数变换以减小偏态，并使用 train_test_split 划分训练集与验证集；
5、使用 GridSearchCV() 对 XGBoost、LightGBM 和 CatBoost 模型分别进行网格搜索，寻找最优超参数组合，优化 RMSE 作为评价指标；
6、结合验证集结果，基于 RMSE 反向优化策略搜索 XGB/LGBM/Cat 的最优加权比例，对模型进行加权融合；
7、使用融合模型对测试集进行预测并还原对数变换，生成最终提交结果。

**因个人疏忽，在比赛最后截止前，未能将加权融合的结果正确接入预测输出，导致提交的结果为单模型预测结果，最终得分为 0.05912，后续修正融合输出后，得分提升至 0.05900。此版本的代码已修正为融合输出版本。**

项目总结：
- 初期尝试使用随机森林与线性回归模型进行预测，但效果不佳；
- 后续借鉴社区优秀方案，采用 XGBoost、LightGBM 与 CatBoost 模型融合，预测效果明显提升；
- 使用 GridSearchCV 搜索模型最优参数，并通过反向优化策略搜索融合最优权重，取得理想成绩；
- 最后阶段尝试引入新特征与 Keras MLP 网络，但模型表现下降，最终弃用。

比赛结果：
- 截止前提交得分：0.05912（CatBoost 单模型）
- 修正后融合得分：0.05900（融合模型）
- 最终排名：第 1123 / 4316（Top 27%）
- 获得：1 枚铜牌、18 个点赞、7 次 Fork

项目链接：
https://www.kaggle.com/code/nalanzuikano/calories-forecast
