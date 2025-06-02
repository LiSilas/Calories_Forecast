Project Overview:
This project is based on the Kaggle competition [Predict Calorie Expenditure - Playground Series, Season 5 Episode 5]. It builds a calorie consumption prediction model using an ensemble of XGBoost, LightGBM, and CatBoost.

Project Structure:
```
calories_forecast/  
├── output/  
│   └── submission.csv  
├── calories_forecast.ipynb  
├── README.md
├── README.zh.md
```

Note:
Since file paths on Kaggle are different from local ones, please update the file paths in calories_forecast.ipynb if you want to run it locally.
**Due to copyright restrictions, the original dataset is not included. You can download it from the Kaggle competition page and extract it to the appropriate location.**

Workflow:
- 1.Load train.csv and test.csv, check dimensions, data types, and basic statistics.
- 2.Encode the Gender feature using LabelEncoder().
- 3.Visualize each feature's relationship with the target Calories, using scatter plots, heatmaps, box plots, and KDE plots to identify important features.
- 4.Apply np.log1p() to the target variable to reduce skewness, and split the dataset using train_test_split.
- 5.Perform hyperparameter tuning with GridSearchCV() for XGBoost, LightGBM, and CatBoost separately. Use RMSE as the evaluation metric.
- 6.Based on validation results, use a reverse-optimization strategy to find the optimal weighted combination of the three models.
- 7.Predict on the test set using the final ensemble model and revert the log-transformation to generate the final submission.

**The final submission before the deadline scored 0.05908. After optimizing the output using an ensemble prediction, the score improved to 0.05900. This version of the notebook has been updated to reflect the improved result.**

Summary:
- Initially tried Random Forest and Linear Regression, but they performed poorly.
- Improved the model by learning from top community notebooks and switching to a tree-based ensemble.
- Applied GridSearchCV for fine-tuning and used a reverse optimization strategy to find the best ensemble weights.
- Later experiments (e.g., adding features, Keras MLP) didn’t improve the score and were removed in the final version.

Competition Results:
- Submitted Ensemble Score: 0.05908
- Optimized Ensemble Score: 0.05900
- Rank: 1123 / 4316 (Top 27%)
- Awards: 1 Bronze Medal, 18 Likes, 7 Forks

Project Link
https://www.kaggle.com/code/nalanzuikano/calories-forecast
