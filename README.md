 
<h1>Student-Result-Analysis<h1>

<h2>Problem Statement for Data Analysis Project<h2>

<h3>Title: Analyzing the Impact of Personal and Professional Factors on Student Academic Performance<h3>

<h4>Introduction:<h4>

In the pursuit of understanding the determinants of academic success, it is essential to analyze both personal and professional factors that influence students' scores across various subjects. By identifying these key factors, educators and policymakers can devise targeted strategies to improve educational outcomes.
<h5>
Objective:
<h5>
##
The objective of this data analysis project is to examine how personal factors and professional factors affect students' academic performance. The study aims to uncover significant relationships and trends that can provide insights into the multifaceted nature of educational achievement.
##
CODE:
##
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
DROP COLUMN 
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
DISTRIBUTION OD ETHNIC GROUPS
##
groupA = df.loc[df["EthnicGroup"] == "group A"].count()

groupB = df.loc[df["EthnicGroup"] == "group B"].count()

groupC = df.loc[df["EthnicGroup"] == "group C"].count()

groupD = df.loc[df["EthnicGroup"] == "group D"].count()

groupE = df.loc[df["EthnicGroup"] == "group E"].count()

lab1 = ["groupA","groupB","groupC","groupD","groupE"]

explode1 = (0, 0, 0.08, 0, 0)

custom_palette1 = ["#000080","#00FFFF","#FF1493","#708090","#800080"]

mlist = [groupA["EthnicGroup"],groupB["EthnicGroup"],groupC["EthnicGroup"],groupD["EthnicGroup"],groupE["EthnicGroup"]]

plt.title("Distribution of Ethnic Group")

plt.pie(mlist,labels=lab1, colors=custom_palette1 ,explode = explode1,autopct = "%1.2f%%", shadow = True, startangle=140)

plt.legend(lab1, loc="center left", bbox_to_anchor = (1,0.8))

plt.show()
##
![image](https://github.com/AkshataPatil99/Student-Result-Analysis/assets/171495035/5d6ee949-9a4a-47c6-b6bb-8898f5655708)
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
Analysis from the charts are, that students whose parents have a Master's Degree scored significantly higher marks in results. Whereas student whose have only a high school degree have scored the lowest marks. 
To conlude, higher the grade of education of parents, greater is its impact on students performance.
##
RELATIONSHIP BETWEEN PARENTS MARITAL STATUS AND STUDENT SCORES
##

gb1 = df.groupby("ParentMaritalStatus").agg({"MathScore": 'mean', "ReadingScore": 'mean', "WritingScore": 'mean'})

plt.figure(figsize=(8, 6))  # Adjusted figsize for better visualization

plt.title("Relationship between Parents Marital Status and Student Scores")

sns.heatmap(gb1, annot=True, fmt=".2f", annot_kws={"rotation": 0})    # Setting fmt=".2f" for 2 decimal places and annot_kws={"rotation": 0} for horizontal annotations

plt.show()
##
![image](https://github.com/AkshataPatil99/Student-Result-Analysis/assets/171495035/f428d29a-bbc7-418c-91df-befff3e13cce)
##
Speculation:
Based on the heatmap analysis, it is evident that parental marital status has no significant impact on student academic performance.
##
DETECT OUTLAIRS OR EXTREME VALUES
##
sns.boxplot(data = df,x = "MathScore")

plt.show()

sns.boxplot(data = df,x = "ReadingScore")

plt.show()

sns.boxplot(data = df,x = "WritingScore")

plt.show()
##
Mathscore:
![image](https://github.com/AkshataPatil99/Student-Result-Analysis/assets/171495035/c69df466-fc70-46be-8e45-1715b0a4f64e)
##
Readingscore:
![image](https://github.com/AkshataPatil99/Student-Result-Analysis/assets/171495035/d5b135a1-38dc-45e1-8009-4a8226ae60dc)
##
Writingscore:
![image](https://github.com/AkshataPatil99/Student-Result-Analysis/assets/171495035/6b42d835-4e42-4ec4-9b17-4777fabb3c26)
##
Speculation:
The box plot analysis reveals a notable observation regarding the distribution of scores across subjects. Specifically, the MathScore exhibits a higher incidence of outliers, including values approaching zero, compared to both ReadingScore and WritingScore.
##
IMPACT OF TEST PREPARATION ON THE RESULTS
##
test = df.groupby("TestPrep").agg({"MathScore":'mean', "ReadingScore":'mean', "WritingScore":'mean'})

plt.figure(figsize = (4,4))

plt.title("IMPACT OF TEST PREPARATION ON THE RESULTS")

sns.heatmap(test, annot=True)

plt.show()
##
![image](https://github.com/AkshataPatil99/Student-Result-Analysis/assets/171495035/a1ba3178-b6e8-4938-a2ed-001d74eb4f36)
##
Speculations:
From the above chart, we can conclude that there is a good impact of test preparation on the students results compared to students with no exam preparation.
##
IMPACT OF WEEKLY STUDY HOURS ON STUDENT RESULTS
##

gb2 = df.groupby("WklyStudyHours").agg({"MathScore":'mean', "ReadingScore":'mean', "WritingScore":'mean'})

plt.figure(figsize = (6,6))

plt.title("Relationship between Weekly study hours and Student Scores")

sns.heatmap(gb2, annot=True, annot_kws={"rotation": 0})

plt.show()
##
![image](https://github.com/AkshataPatil99/Student-Result-Analysis/assets/171495035/6fa39b16-0144-47ef-bd25-f009f06e3fee)
##
Speculations:
From the above heatmap we can conclude that there is moderate impact of weekly study hours on the student results.
##
Summarizing Findings
##
The key analysis question here was to identify the relationship between personal factors and professional factors that affect students' academic performance. From the above mentioned analysis 3 major patterns have been identified. These are: Summary of Findings

1. Parental Education Impact: The analysis of student performance in relation to parental education levels reveals a significant correlation. Students with parents holding Master's Degrees achieved notably higher marks, contrasting with those whose parents have only completed high school, who demonstrated the lowest scores. This underscores the influential role of parental educational attainment on student academic outcomes.

2. Parental Marital Status: Contrary to expectations, the heatmap analysis indicates that parental marital status does not exhibit a discernible impact on student academic performance. This suggests that other factors may play a more significant role in influencing student outcomes.

3. Subject Score Distribution: Examination of score distributions across subjects through box plot analysis highlights distinct patterns. Math scores notably feature more outliers, including values approaching zero, compared to Reading and Writing scores. This insight into score variability underscores the unique challenges and potential areas of improvement specific to mathematical proficiency among students.

4. Effect of Test Preparation: The findings suggest a beneficial impact of test preparation on student performance compared to those without such preparation. This indicates that structured preparation efforts positively contribute to academic achievement outcomes.

5. Weekly Study Hours Impact: Analysis via heatmap suggests a moderate impact of weekly study hours on student academic results. While significant, this influence indicates that other factors beyond study hours also play crucial roles in determining student success.

Overall, these findings provide valuable insights into the multifaceted influences shaping student academic performance, emphasizing the pivotal roles of parental education, subject-specific challenges, preparation strategies, and study habits.
##
Conclusion:
##
Based on the findings, here are some suggestions on how educational institutions can potentially improve student academic performance:

Support for Lower-Educated Parents: Provide targeted support programs for parents with lower educational backgrounds. This could involve offering educational resources, counseling, or workshops aimed at enhancing their ability to support their children's academic development.

Subject-Specific Interventions: Develop targeted interventions and support systems, particularly in subjects like Mathematics where students exhibit higher variability in scores. This may include additional tutoring, adaptive learning tools, or peer support programs focused on improving subject-specific skills.

Enhanced Test Preparation: Expand or improve existing test preparation programs to ensure all students have access to effective strategies and resources. This could involve partnerships with educational specialists, leveraging technology for personalized learning experiences, or offering mock exams and feedback sessions.

Promotion of Effective Study Habits: Educate students and parents about the importance of consistent study habits and time management. Implement programs that promote healthy study routines and provide guidance on how to optimize study hours effectively.

Data-Driven Decision Making: Continuously monitor and analyze student performance data to identify trends and areas needing improvement. Use this information to tailor interventions and educational strategies to better meet the diverse needs of students.

Professional Development for Educators: Offer ongoing professional development opportunities for teachers to enhance their instructional practices and strategies for supporting diverse student needs. This may include workshops on differentiated instruction, use of educational technology, and cultural competence.





