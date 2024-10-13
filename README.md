# Exno:1
Data Cleaning Process

# AIM
To read the given data and perform data cleaning and save the cleaned data to a file.

# Explanation
Data cleaning is the process of preparing data for analysis by removing or modifying data that is incorrect ,incompleted , irrelevant , duplicated or improperly formatted. Data cleaning is not simply about erasing data ,but rather finding a way to maximize datasets accuracy without necessarily deleting the information.

# Algorithm
STEP 1: Read the given Data

STEP 2: Get the information about the data

STEP 3: Remove the null values from the data

STEP 4: Save the Clean data to the file

STEP 5: Remove outliers using IQR

STEP 6: Use zscore of to remove outliers

# Coding and Output

import pandas as pd
import numpy as np
import seaborn as sns
from google.colab import files
uploaded = files.upload()
# Assuming your uploaded file is named 'data_set.csv'
df = pd.read_csv('heights.csv')

#OUTLIER DETECTION
#IQR,BOXPLOT,SCATTERPLOT
sns.boxplot(df)

sns.scatterplot(df)

#IQR
Q1 = df['height'].quantile(0.25)
Q3 = df['height'].quantile(0.75)
print(Q1)
print(Q3)
IQR = Q3-Q1
print(IQR)

Lower_limit = Q1-1.5*IQR
Upper_limit = Q3+1.5*IQR
Outliers = [x for x in df['height'] if x<Lower_limit or x>Upper_limit]

print(Lower_limit)
print(Upper_limit)
print(Outliers)

df

#Z SQUARE

mn =np.mean(df['height'])
sd =np.std(df['height'])
print("mean deviation = ",mn)
print("std deviation = ",sd)

threshold = 3
outliers_list = []
for x in df['height']:
  z = (x-mn)/sd
  if z>threshold:
    outliers_list.append(x)
print("Outlier Heights = ", outliers_list)

#HANDLING NULL VALUES
import pandas as pd
import numpy as np
import seaborn as sns
from google.colab import files
uploaded = files.upload()
# Assuming your uploaded file is named 'data_set.csv'
df = pd.read_csv('Data_set.csv')

df

df.isnull()

df.isnull().sum()

df.notnull()

df.dropna(axis=0)

df.dropna(axis=1)

df.fillna(0)

df.fillna(method='ffill')

df.fillna(method='bfill')

df['watchers'].fillna(df['watchers'].mean())

df['rating'].fillna(df['rating'].median())


            <<include your coding and its corressponding output screen shots here>>
# Result
          <<include your Result he![BOX](https://github.com/user-attachments/assets/43338d13-5db2-4d9d-8d12-4cfa2f91a9d0)
![BOX](https://github.com/user-attachments/assets/8bd11992-15bc-48ae-aa20-fd2069171aa8)


5.25
6.175
0.9249999999999998

3.8625000000000003
7.5625
[14.5, 1.2]

            name	height
0	mohan	5.9
1	maria	5.2
2	sakib	5.1
3	tao	5.5
4	virat	4.9
5	khusbu	5.4
6	dmitry	6.2
7	selena	6.5
8	john	7.1
9	imran	14.5
10	jose	6.1
11	deepika	5.6
12	yoseph	1.2
13	binod	5.5

mean deviation =  6.05
std deviation =  2.6786857118477228

Outlier Heights =  [14.5]

show_name	country	num_episodes	aired_on	original_network	rating	current_overall_rank	lifetime_popularity_rank	watchers
0	NaN	South Korea	16	Friday, Saturday	tvN	8.9	33.0	          1	                                    111706.0
1	NaN	South Korea	16	Friday, Saturday	jTBC	8.7	89.0	          2	                                    100950.0
2	Descendants of the Sun	South Korea	16	Wednesday, Thursday	KBS2	8.7	77.0	3	                        96318.0
3	Boys Over Flowers	South Korea	25	Monday, Tuesday	KBS2	7.7	2249.0	4	                        94228.0
4	W	South Korea	16	Wednesday, Thursday	MBC	8.5	201.0	          5	                                    92121.0
...	...	...	...	...	...	...	...	...	...
95	Shut Up: Flower Boy Band	South Korea	16	Monday, Tuesday	tvN	8.1	806.0	99	            34668.0
96	Blood	South Korea	20	Monday, Tuesday	KBS2	7.4	3271.0	100	34666.0
97	Chicago Typewriter	South Korea	16	Friday, Saturday	tvN	8.8	51.0	101	                            NaN
98	Sungkyunkwan Scandal	South Korea	20	Monday, Tuesday	KBS2	8.2	605.0	102	                        34615.0
99	Vagabond	South Korea	16	Friday, Saturday	SBS, Netflix	8.5	238.0	103	                        34523.0
100 rows × 9 columns


show_name	country	num_episodes	aired_on	original_network	rating	current_overall_rank	lifetime_popularity_rank	watchers
0	True	False	False	False	False	            False	False	            False	                        False
1	True	False	False	False	False	            False	False	            False	                        False
2	False	False	False	False	False	            False	False	            False	                        False
3	False	False	False	False	False	            False	False	            False	                        False
4	False	False	False	False	False	            False	False	            False	                        False
...	...	...	...	...	...	            ...	...	            ...	                        ...
95	False	False	False	False	False	            False	False	            False	                        False
96	False	False	False	False	False	            False	False	            False	                        False
97	False	False	False	False	False	            False	False	            False	                        True
98	False	False	False	False	False	            False	False	            False	                        False
99	False	False	False	False	False	            False	False	            False	                        False


0
show_name	4
country	0
num_episodes	0
aired_on	1
original_network	1
rating	4
current_overall_rank	3
lifetime_popularity_rank	0
watchers	3

            show_name	country	num_episodes	aired_on	original_network	rating	current_overall_rank	lifetime_popularity_rank	watchers
0	False	True	            True	True	            True	True	            True	True	True
1	False	True	            True	True	            True	True	            True	True	True
2	True	True	            True	True	            True	True	            True	True	True
3	True	True	            True	True	            True	True	            True	True	True
4	True	True	            True	True	            True	True	            True	True	True
...	...	...	            ...	...	            ...	...	            ...	...	...
95	True	True	            True	True	            True	True	            True	True	True
96	True	True	            True	True	            True	True	            True	True	True
97	True	True	            True	True	            True	True	            True	True	False
98	True	True	            True	True	            True	True	            True	True	True
99	True	True	            True	True	            True	True	            True	True	True


	show_name	country	num_episodes	aired_on	original_network	rating	current_overall_rank	lifetime_popularity_rank	watchers
2	Descendants of the Sun	South Korea	16	Wednesday, Thursday	KBS2	8.7	77.0	3	96318.0
3	Boys Over Flowers	South Korea	25	Monday, Tuesday	KBS2	7.7	2249.0	4	94228.0
4	W	South Korea	16	Wednesday, Thursday	MBC	8.5	201.0	5	92121.0
5	You Who Came from the Stars	South Korea	21	Wednesday, Thursday	SBS	8.6	112.0	6	91360.0
6	Weightlifting Fairy Kim Bok Joo	South Korea	16	Wednesday, Thursday	MBC	8.8	40.0	7	91330.0
...	...	...	...	...	...	...	...	...	...
94	Flower of Evil	South Korea	16	Wednesday, Thursday	tvN	9.1	4.0	98	34901.0
95	Shut Up: Flower Boy Band	South Korea	16	Monday, Tuesday	tvN	8.1	806.0	99	34668.0
96	Blood	South Korea	20	Monday, Tuesday	KBS2	7.4	3271.0	100	34666.0
98	Sungkyunkwan Scandal	South Korea	20	Monday, Tuesday	KBS2	8.2	605.0	102	34615.0
99	Vagabond	South Korea	16	Friday, Saturday	SBS, Netflix	8.5	238.0	103	34523.0
86 rows × 9 columns



country	num_episodes	lifetime_popularity_rank
0	South Korea	16	1
1	South Korea	16	2
2	South Korea	16	3
3	South Korea	25	4
4	South Korea	16	5
...	...	...	...
95	South Korea	16	99
96	South Korea	20	100
97	South Korea	16	101
98	South Korea	20	102
99	South Korea	16	103
100 rows × 3 columns


show_name	country	num_episodes	aired_on	original_network	rating	current_overall_rank	lifetime_popularity_rank	watchers
0	0	South Korea	16	Friday, Saturday	tvN	8.9	33.0	1	111706.0
1	0	South Korea	16	Friday, Saturday	jTBC	8.7	89.0	2	100950.0
2	Descendants of the Sun	South Korea	16	Wednesday, Thursday	KBS2	8.7	77.0	3	96318.0
3	Boys Over Flowers	South Korea	25	Monday, Tuesday	KBS2	7.7	2249.0	4	94228.0
4	W	South Korea	16	Wednesday, Thursday	MBC	8.5	201.0	5	92121.0
...	...	...	...	...	...	...	...	...	...
95	Shut Up: Flower Boy Band	South Korea	16	Monday, Tuesday	tvN	8.1	806.0	99	34668.0
96	Blood	South Korea	20	Monday, Tuesday	KBS2	7.4	3271.0	100	34666.0
97	Chicago Typewriter	South Korea	16	Friday, Saturday	tvN	8.8	51.0	101	0.0
98	Sungkyunkwan Scandal	South Korea	20	Monday, Tuesday	KBS2	8.2	605.0	102	34615.0
99	Vagabond	South Korea	16	Friday, Saturday	SBS, Netflix	8.5	238.0	103	34523.0
100 rows × 9 columns



show_name	country	num_episodes	aired_on	original_network	rating	current_overall_rank	lifetime_popularity_rank	watchers
0	NaN	South Korea	16	Friday, Saturday	tvN	8.9	33.0	1	111706.0
1	NaN	South Korea	16	Friday, Saturday	jTBC	8.7	89.0	2	100950.0
2	Descendants of the Sun	South Korea	16	Wednesday, Thursday	KBS2	8.7	77.0	3	96318.0
3	Boys Over Flowers	South Korea	25	Monday, Tuesday	KBS2	7.7	2249.0	4	94228.0
4	W	South Korea	16	Wednesday, Thursday	MBC	8.5	201.0	5	92121.0
...	...	...	...	...	...	...	...	...	...
95	Shut Up: Flower Boy Band	South Korea	16	Monday, Tuesday	tvN	8.1	806.0	99	34668.0
96	Blood	South Korea	20	Monday, Tuesday	KBS2	7.4	3271.0	100	34666.0
97	Chicago Typewriter	South Korea	16	Friday, Saturday	tvN	8.8	51.0	101	34666.0
98	Sungkyunkwan Scandal	South Korea	20	Monday, Tuesday	KBS2	8.2	605.0	102	34615.0
99	Vagabond	South Korea	16	Friday, Saturday	SBS, Netflix	8.5	238.0	103	34523.0
100 rows × 9 columns


show_name	country	num_episodes	aired_on	original_network	rating	current_overall_rank	lifetime_popularity_rank	watchers
0	Descendants of the Sun	South Korea	16	Friday, Saturday	tvN	8.9	33.0	1	111706.0
1	Descendants of the Sun	South Korea	16	Friday, Saturday	jTBC	8.7	89.0	2	100950.0
2	Descendants of the Sun	South Korea	16	Wednesday, Thursday	KBS2	8.7	77.0	3	96318.0
3	Boys Over Flowers	South Korea	25	Monday, Tuesday	KBS2	7.7	2249.0	4	94228.0
4	W	South Korea	16	Wednesday, Thursday	MBC	8.5	201.0	5	92121.0
...	...	...	...	...	...	...	...	...	...
95	Shut Up: Flower Boy Band	South Korea	16	Monday, Tuesday	tvN	8.1	806.0	99	34668.0
96	Blood	South Korea	20	Monday, Tuesday	KBS2	7.4	3271.0	100	34666.0
97	Chicago Typewriter	South Korea	16	Friday, Saturday	tvN	8.8	51.0	101	34666.0
98	Sungkyunkwan Scandal	South Korea	20	Monday, Tuesday	KBS2	8.2	605.0	102	34615.0
99	Vagabond	South Korea	16	Friday, Saturday	SBS, Netflix	8.5	238.0	103	34523.0
100 rows × 9 columns



watchers
0	111706.0
1	100950.0
2	96318.0
3	94228.0
4	92121.0
...	...
95	34668.0
96	34666.0
97	34666.0
98	34615.0
99	34523.0

rating
0	8.9
1	8.7
2	8.7
3	7.7
4	8.5
...	...
95	8.1
96	7.4
97	8.8
98	8.2
99	8.5



