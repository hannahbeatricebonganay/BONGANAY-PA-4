# BONGANAY-PA-4
Programming Assignment #4

# ECE BOARD EXAM PROBLEM:
### Using data wrangling and data visualization technique with storytelling, analyze the data and present different (i) data frames; and (ii) visuals using the dataset given.

```python
download the file board2.csv
```

## 1. Create the following data frames based on the format provided:

### a. Filename: Instru = [“Name”, “GEAS”, “Electronics >70”]; where track is constant as Instrumentation and hometown Luzon

#### a.1 Import Pandas library and load the dataset
```python
import pandas as pd
df = pd.read_csv("board2.csv")
```

#### a.2 Filter the instrumentation tech, hometown Luzon, and Electronics >70 using df
#### then keep only the "Name", "GEAS", and "Electronics" columns
```python
Instru = df[(df["Track"] == "Instrumentation") & 
            (df["Hometown"] == "Luzon") & 
            (df["Electronics"] > 70)] [["Name", "GEAS", "Electronics"]]
```

#### a.3 Output the Instru dataframe 
```python
print("INSTRU DATAFRAME:")
print(" ")
Instru
```


### b. Filename: Mindy = [ “Name”, “Track”, “Electronics”, “Average >=55”]; where hometown is constant as Mindanao and gender Female

#### b.1 Import Pandas library and load the dataset
```python
import pandas as pd
df = pd.read_csv("board2.csv")
```

#### b.2 Compute the Average or the mean column 
```python
df["Average"] = df[["Math", "Electronics", "GEAS", "Communication"]].mean(axis=1)
```

#### b.3 Filter only the Female students from Mindanao with Average >= 55 using df
#### and only output the "Name", "Track", "Electronics", and "Average" columns
```python
Mindy = df[(df["Hometown"] == "Mindanao") &
            (df["Gender"] == "Female") & 
            (df["Average"] >= 55)] [["Name", "Track", "Electronics", "Average"]]
```

#### b.4 Output the Mindy dataframe 
```python
print("MINDY DATAFRAME:")
print(" ")
Mindy
```

## 2. Create a visualization that shows how the different features contributes to average grade. Does chosen track in college, gender, or hometown contributes to a higher average score?

#### a. Import libraries and load the dataset
```python
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns
df = pd.read_csv("board2.csv")
```

#### b. Again, compute for the average or the mean column
```python
df["Average"] = df[["Math", "Electronics", "GEAS", "Communication"]].mean(axis=1)
```

#### c. Compare Gender column with Average score
```python
plt.figure(figsize=(6,6)) # set figure size
sns.barplot(data=df, x="Gender", y="Average", estimator="mean", errorbar=None) # barplot of mean Average
plt.title("Average Score by Gender") # set plot title
plt.ylabel("Mean Average Score") # set y-axis label
plt.xlabel("Gender") # set x-axis label
plt.show() # display the plot
```

#### d. Compare Track column with the Average score
```python
plt.figure(figsize=(8,6)) # set figure size
sns.barplot(data=df, x="Track", y="Average", estimator="mean", errorbar=None) # barplot of mean Average
plt.title("Average Score by College Track") # set plot title
plt.ylabel("Mean Average Score") # set y-axis label
plt.xlabel("Track") # set x-axis label
plt.show() # display the plot
```

#### e. Compare the Hometown with the Average score
```python
plt.figure(figsize=(8,6)) # set figure size
sns.barplot(data=df, x="Hometown", y="Average", estimator="mean", errorbar=None) # barplot of the mean Average
plt.title("Average Score by Hometown") # set plot title
plt.ylabel("Mean Average Score") # set y-axis label
plt.xlabel("Hometown") # set x-axis label
plt.show() # display the plot
```

#### f. The output will show bar graphs accurate to the required data
