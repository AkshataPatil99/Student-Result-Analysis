## Student-Result-Analysis
##
Problem Statement for Data Analysis Project
##
Title: Analyzing the Impact of Personal and Professional Factors on Student Academic Performance
##
Introduction:
##
In the pursuit of understanding the determinants of academic success, it is essential to analyze both personal and professional factors that influence students' scores across various subjects. By identifying these key factors, educators and policymakers can devise targeted strategies to improve educational outcomes.
##
Objective:
##
The objective of this data analysis project is to examine how personal factors (parents' education, ethnic group, parents' marital status, and siblings) and professional factors (test preparation and weekly study hours) affect students' academic performance. The study aims to uncover significant relationships and trends that can provide insights into the multifaceted nature of educational achievement.
##
Analysis Questions:
##
1.Personal Factors:
##
How does parents' education level correlate with students' scores in different subjects?

What is the impact of students' ethnic group on their academic performance?

Does the marital status of parents influence students' scores, and if so, how?

Is there a relationship between the number of siblings and students' academic achievement?
##
2.Professional Factors:
##
How does participation in test preparation programs affect students' scores?

What is the correlation between weekly study hours and academic performance across various subjects?

CODE:
##
IMPORT LIBRARIES
##
import numpy as np

import pandas as pd

import matplotlib.pyplot as plt

import seaborn as sns
##
READ CSV FILES
##
df=pd.read_csv(r"C:\Users\ap446\OneDrive\Desktop\datasets\Expanded_data_with_more_features.csv")

pd.set_option('display.max_columns',None)
##
CONDUCT EXPLORATORY DATA ANALYSIS
##
print(df.head(10))

df.describe()

df.info()

df.isnull().sum()
##
DROP UNNAMED COLUMN THAT ARE NOT USEFUL
##
df = df.drop("Unnamed: 0",axis = 1)
##
CHANGING DATA TYPE OF COLUMN
##
df["Gender"] = df["Gender"].astype('category')
##
GENDER DISTIRBUTION
##
plt.figure(figsize = (5,5))
plt.title("Gender Distribution")
custom_palette = ['#000080', '#00FFFF']  # Example colors: Navy for Male and Cyan for Female
ax = sns.countplot(data = df, x ="Gender", palette=custom_palette)
for p in ax.patches:
    ax.annotate(f'{p.get_height()}', (p.get_x() + p.get_width() / 2., p.get_height()), ha='center', va='center', xytext=(0, 5), textcoords='offset points')
plt.show()
##
OUTPUT:
##
![image](https://github.com/AkshataPatil99/Student-Result-Analysis/assets/171495035/a7df4387-8f4b-4c71-a2fb-a7b5b07393a0)
##
Speculation:
From the chart, it can be observed that the dataset contains a higher number of female students compared to males students.
##
RELATIONSHIP BETWEEN PARENT'S EDUCATION AND STUDENT SCORES
##
gb = df.groupby("ParentEduc").agg({"MathScore":'mean', "ReadingScore":'mean', "WritingScore":'mean'})
plt.figure(figsize = (4,4))
plt.title("Relationship between Parent's Education and Student Scores")
sns.heatmap(gb, annot=True)
plt.show()
##
![image](https://github.com/AkshataPatil99/Student-Result-Analysis/assets/171495035/6df1eeeb-183c-41c1-932e-97093f40a44f)
##
Speculation:
Based on the chart, we have concluded that parents' marital status has a negligible impact on student results.
##
DETECT OUTLAIRS OR EXTREME VALUES
##




