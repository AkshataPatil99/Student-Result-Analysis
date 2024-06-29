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
##
What is the impact of students' ethnic group on their academic performance?
##
Does the marital status of parents influence students' scores, and if so, how?
##
Is there a relationship between the number of siblings and students' academic achievement?
##
2.Professional Factors:
##
How does participation in test preparation programs affect students' scores?
##
What is the correlation between weekly study hours and academic performance across various subjects?
##
CODE:
##
#IMPORT LIBRARIES
##
import numpy as np
##
import pandas as pd
##
import matplotlib.pyplot as plt
##
import seaborn as sns
##
#READ CSV FILES
##
df=pd.read_csv(r"C:\Users\ap446\OneDrive\Desktop\datasets\Expanded_data_with_more_features.csv")
##
pd.set_option('display.max_columns',None)
##
#CONDUCT EXPLORATORY DATA ANALYSIS
##
print(df.head(10))
##
df.describe()
##
df.info()
##
df.isnull().sum()

