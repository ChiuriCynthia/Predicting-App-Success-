# Predicting-App-Success- *LIT THINK PROJECT*

## *Introduction*
As of March 2024, there are approximately 3.55 million apps available on the Google Play Store while the Apple App Store has around 1.96 million apps available for download.

The number of new apps released each year has grown substantially. In 2016, 2.4 million apps were published and in 2023, approximately 62 thousand mobile apps were released through the Google Play Store and 26.4 thousand on the Apple App Store.

It’s estimated that only 0.5% of apps are successful, meaning they get enough downloads and active users to be profitable.

Studies show that almost 68% of apps get below 1,000 downloads, nearly 18% get 1,000 or fewer active users, and another 7% close because they don’t see enough revenue.

However, understanding what makes an app successful can be a complex task. This project aims to unravel this complexity by developing a classification model that identifies the key factors contributing to an app’s success on the Google Play Store.

Why should developers care?
The insights derived from this model will not only guide developers in creating apps that resonate with users but also help them make informed decisions about feature development, user interface design, and marketing strategies. By predicting an app’s success, developers can optimize resources, reduce risk, and increase the likelihood of their app’s success in the marketplace.

 ## *Data Understanding*
We retrieved our dataset from Kaggle. This is the link to the Kaggle data set:

https://www.kaggle.com/datasets/lava18/google-play-store-apps

The Google Play Store dataset contains information about numerous apps available on the platform, including:

App name - The name of the mobile application

Category - The category the app belongs to E.g- Family, Education

Ratings - The user rating of the app.

Reviews - The number of reviews the app has received

Size - The size of the app in terms of storage space

Installs - Contains the installations count(The number of times the app has been installed)

Type - Whether the app is free or paid

Price - The Price of the app if it's not free

Content rating - The target audience or the age group for which the app is suitable

Genres - The specific category of the app, which is similar to the category columm

Last app update - The date when the app was last updated

Current app version - Current version number of the app

Android version - The minimum required android version to run the app

By analyzing this dataset, we can gain insights into the factors influencing app popularity, user engagement, and market trends within the Google Play Store ecosystem.

## *Data Pre processing*
The csv files were loaded from the local machine and read into a pandas dataframe. This was done after the necessary libraries were imported.
The data was then explored using functions and methods such as .describe(), .shape(), .info(), .head() and .duplicated()

## *Data Cleaning*
After exploring the data, the data was cleaned. There were 876 duplicates values in the dataset. The duplicates were dropped. Furthermore, there were missing values in the Rating, Type, Current Version and Android Version columns.  
    
We dropped the missing values in the Ratings columns since we felt like imputing would not be represnting the true feeelings of the users. This also took care of the other missing values in our dataset.

We also did some cleaning on the Size column by replacing 'Varies with device' with 12 MB (which is average size of most Android apps from research). Afterwards, we changed the whole column to KiloBytes (KB) for uniformity. Additionaly we converted some of the columns to numericals. These columns were Reviews, Size(KB), Installs and Price.

## *Data Visualisations*
We did a quite a number of visualisations to gain some insights such as the top categories by count. Below is a barchart showing the top 20 categories by count. 
![alt text](https://github.com/ChiuriCynthia/Predicting-App-Success-/assets/128600244/5c383b00-b3b5-4ee9-a6f5-42a20fd70b32)


We also had a histogram showing the distribution of app sizes. 


We did a bunch of bivariate analysis like: Distribution of Reviews by Top 20 Categories, average Ratings by Category and average Size of Apps by Category. Below is a violin plot showing the distibution of reviews by Top 20 Categories.

## *Feature Engineering*
Before modeling we undertook feature engineering. Here we used the installs column (our target variable) to create a new column (InstallCategory). We then converted the Last Updated column to number of years since last update. Furthermore, we split the values in current version and android version and retained the first value which represented the Major version in both cases.

We then binned the major Versions in both columns and preceeded to drop columns that were not to be used in our modeling. We then proceeded to one hot encoding the categorical column and label encoding some of the columns.

## *Modeling*
Our metric of Success was precision as it was the most appropriate.

Logistic regression as our baseline model and we then incorporated 4 more models, KNN,Random Forest,XG Boost and Decision trees.

## *Conclusion*
From this project,we uncovered significant information such as:

Finance had the highest number of reviews followed by books and references then health and fitnesss.

Paid apps were rated higher.

Most of the installed apps are in the marked range from 0 to around (12MB).

Game, Family and Sports categories have higher averages sizes in KB, ranging from 20000 to 40000 KB.

Apps with a higher number of reviews tend to have more installs, indicating a positive relationship between user engagement and app popularity.

larger apps may attract more user feedback, possibly due to their increased functionality or complexity.

Random Forests, at 88%, are the most precise of the five classification models, closely followed by XGBoost at 87%, and then decision trees at 86%.Consequently, 88% of the time we can reliably and precisely classify an app into low, medium, high, and very high using the Random Forest model. When utilizing the Random Forest mode with the reviews as the most important feature.

## *Recommendations*
Optimize App Installations: Pay attention to factors influencing app installations. By taking into consideration features that have a strong correlation with the number of installs ap developers will be able to optimize app descriptions, screenshots, and othe r promotion l materials to attract more users and increase app installatio

Enhance User Experience: Prioritize providing a positive user experience within your apps. Consider factors such as app size, performance, and compatibility with different Androin. Optimizing these aspects can contribute to higher user satisfaction and positive app ratin

Stay Updated on Market Trends: Continuously monitor market trends within the Google Play Store ecosystem. Identify emerging app categories and changes in user preferences over time. This information can help you stay ahead of the curve and align your app development and marketing strategies with the evolving needs and interests.

## *Next Steps*
Moving forward we suggest the following steps :

Collaborate with Marketers and Stakeholders: Share the findings and insights from the analysis with marketers and stakeholders. Collaborate with marketing teams to develop targeted promotional campaigns based on user preferences and market trends. Engage with stakeholders to align app development strategies with business objectives and market demands.

Explore User Segmentation: Segment the user base based on different characteristics such as demographics, preferences, and behavior patterns. Analyze how different user segments interact with apps and identify specific needs and preferences. This information can guide personalized app development and targeted marketing efforts.

Refine the Machine Learning Model: Evaluate and refine the machine learning model developed for predicting app success and classifying app installations. Consider exploring different algorithms, tuning hyperparameters, and performing feature selection to improve the model's accuracy and performance.
