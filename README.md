# ECE-2112-PA-4

### Made by John Felix C. Francisco | 2ECE-C

##### This repository contains the solution to the Programming Assignment 4 for the course “Advance Computer Programming and Algorithms,” this S.Y. 2026-2027. It tackles three python problems involving Module 4, which is about Data Wrangling and Visualization. 

##### The objective of this experiment is for students to:
##### 1. filter tabular data using several categorical and numerical conditions;
##### 2. construct focused DataFrames by selecting relevant features;
##### 3. summarize the relationship between categorical features and a numerical variable; and
##### 4. communicate a data comparison using clear and correctly labeled plots.

##### Before continuing, the Pandas and Mathplot Library were imported as pd and plt, respectively. Additionally, the board2.xlsx file was read and the mean per student was gathered into a dataframe. Afterwards, it was added back to the original dataset to use in the problems below.

# A. Visayas Communication Dataframe
##### From the board2.xlsx dataset, create a dataframe called “VisComm” that contains students whose hometown is “Visayas” and whose track is “Communication.” The columns Name, Gender, Math, Electronics, and Average are to be retained. 

##### The main method used in the solution is the function `.loc()` as well as column selecting. ##### The `.loc()` function was used to locate the desired hometown and track through boolean filtering. Afterwards, column selection was used to retain the required columns. Through these methods, the program was made,
```python
VisComm = df.loc[(df['Hometown'] == 'Visayas')&(df['Track'] == "Communication")]
VisComm[['Name','Gender','Math','Electronics','Average']]
```

# B. Visayas Female Dataframe
##### From the same dataset, create a dataframe called “VisFemale” that contains students whose hometown is “Visayas” and whose gender is “Female.” The columns Name, Track, GEAS, Electronics, and Average are to be retained. Afterwards, display only the rows of VisFemale whose Average is at least 60. 

##### The main method used in the solution is the function `.loc()` as well as column selecting. The `.loc()` function was used to locate the desired hometown and gender through boolean filtering. Another set of filtering was used to get the rows whose average was greater than 60 Afterwards, column selection was used to retain the required columns. Through these methods, the program was made,
```python
VisFemale = df.loc[(df['Hometown'] == 'Visayas')&(df['Gender'] == 'Female')]
VisFemale[['Name','Track','GEAS','Electronics','Average']]
VisFemale[['Name','Track','GEAS','Electronics','Average']].loc[(df['Average']>60)]
```

# C. Category-Average Visualization
##### Using Pandas, compute and display the mean of the Average for the three categorical features Track, Gender, and Hometown. Afterwards, create one figure containing the bar charts of the mean Average by Track, by Gender, and by Hometown. Below the figure, write three concise statements identifying the category with the highest sample mean for each feature.

##### To get the mean average of the categories, `.groupby()` was used to group the unique values under each category. Through filtering, it was able to isolate the numerical values to get its mean. `.reset_index()` returns the results as a standard dataframe. Subplotting methods and techniques using Matplotlib helped create the figure of the bar charts, creating the program, 
```python
Track = df.groupby('Track')['Average'].mean().reset_index()
Gender = df.groupby('Gender')['Average'].mean().reset_index()
Hometown = df.groupby('Hometown')['Average'].mean().reset_index()

fig, axes = plt.subplots(nrows=1,ncols=3, figsize=(14,5), sharey=True)
fig.text(0.52,-0.03, 'Figure 1: Bar Graph of the Mean Average by Track, Gender, and Hometown', ha='center',style='italic')
fig.text(0,-0.1, 'In the Track category, Communication had the highest sample mean among the three.', fontsize=12) 
fig.text(0,-0.16, 'In the Gender category, Male students have the highest sample mean.', fontsize=12) 
fig.text(0,-0.22, 'In the Hometown category, Luzon recorded the highest sample mean among the three.', fontsize=12) 

axes[0].bar(Track['Track'], Track['Average'])
axes[0].set_title('Mean Average by Track')
axes[0].grid(axis='y',alpha=0.7)
axes[0].set_axisbelow(True)

axes[1].bar(Gender['Gender'],Gender['Average'])
axes[1].set_title('Mean Average by Gender')
axes[1].grid(axis='y',alpha=0.7)
axes[1].set_axisbelow(True)

axes[2].bar(Hometown['Hometown'],Hometown['Average'])
axes[2].set_title('Mean Average by Hometown')
axes[2].grid(axis='y',alpha=0.7)
axes[2].set_axisbelow(True)

axes[0].set_ylabel('Mean Average')
plt.tight_layout()
plt.show()
```

##### For the interpretation of each bar chart, the Track category has communication as the highest sample mean among the three. Moreover, male students have the highest sample mean in the Gender category. Additionally, Luzon recorded the highest sample mean in the Hometown category.

##### Thank you for reading!

##### If you want to try the main program for the Programming Assignment 3, kindly refer to the link: https://github.com/JFFrancisco0/Problem-Assignment-4---Francisco.git , and download the ipnyb file. Afterwards, open it in Jupyter Notebook and run all the cells. 

##### Version History
##### September 17, 2026 - initial content uploaded
