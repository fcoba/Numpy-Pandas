
# PyCitySchools HW 

First upload the necessary libraries.


```python
import pandas as pd
import numpy as np
```

Next, use the imported read function to get the data. 
I called the schools csv file "schools_df" and so forth. 


```python
schools_df = pd.read_csv('raw_data/schools_complete.csv')
students_df = pd.read_csv('raw_data/students_complete.csv')
```

Next, let's glance at what the data tables (data frames) looks like.


```python
schools_df
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>School ID</th>
      <th>name</th>
      <th>type</th>
      <th>size</th>
      <th>budget</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>0</td>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1</td>
      <td>Figueroa High School</td>
      <td>District</td>
      <td>2949</td>
      <td>1884411</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2</td>
      <td>Shelton High School</td>
      <td>Charter</td>
      <td>1761</td>
      <td>1056600</td>
    </tr>
    <tr>
      <th>3</th>
      <td>3</td>
      <td>Hernandez High School</td>
      <td>District</td>
      <td>4635</td>
      <td>3022020</td>
    </tr>
    <tr>
      <th>4</th>
      <td>4</td>
      <td>Griffin High School</td>
      <td>Charter</td>
      <td>1468</td>
      <td>917500</td>
    </tr>
    <tr>
      <th>5</th>
      <td>5</td>
      <td>Wilson High School</td>
      <td>Charter</td>
      <td>2283</td>
      <td>1319574</td>
    </tr>
    <tr>
      <th>6</th>
      <td>6</td>
      <td>Cabrera High School</td>
      <td>Charter</td>
      <td>1858</td>
      <td>1081356</td>
    </tr>
    <tr>
      <th>7</th>
      <td>7</td>
      <td>Bailey High School</td>
      <td>District</td>
      <td>4976</td>
      <td>3124928</td>
    </tr>
    <tr>
      <th>8</th>
      <td>8</td>
      <td>Holden High School</td>
      <td>Charter</td>
      <td>427</td>
      <td>248087</td>
    </tr>
    <tr>
      <th>9</th>
      <td>9</td>
      <td>Pena High School</td>
      <td>Charter</td>
      <td>962</td>
      <td>585858</td>
    </tr>
    <tr>
      <th>10</th>
      <td>10</td>
      <td>Wright High School</td>
      <td>Charter</td>
      <td>1800</td>
      <td>1049400</td>
    </tr>
    <tr>
      <th>11</th>
      <td>11</td>
      <td>Rodriguez High School</td>
      <td>District</td>
      <td>3999</td>
      <td>2547363</td>
    </tr>
    <tr>
      <th>12</th>
      <td>12</td>
      <td>Johnson High School</td>
      <td>District</td>
      <td>4761</td>
      <td>3094650</td>
    </tr>
    <tr>
      <th>13</th>
      <td>13</td>
      <td>Ford High School</td>
      <td>District</td>
      <td>2739</td>
      <td>1763916</td>
    </tr>
    <tr>
      <th>14</th>
      <td>14</td>
      <td>Thomas High School</td>
      <td>Charter</td>
      <td>1635</td>
      <td>1043130</td>
    </tr>
  </tbody>
</table>
</div>




```python
students_df.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Student ID</th>
      <th>name</th>
      <th>gender</th>
      <th>grade</th>
      <th>school</th>
      <th>reading_score</th>
      <th>math_score</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>0</td>
      <td>Paul Bradley</td>
      <td>M</td>
      <td>9th</td>
      <td>Huang High School</td>
      <td>66</td>
      <td>79</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1</td>
      <td>Victor Smith</td>
      <td>M</td>
      <td>12th</td>
      <td>Huang High School</td>
      <td>94</td>
      <td>61</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2</td>
      <td>Kevin Rodriguez</td>
      <td>M</td>
      <td>12th</td>
      <td>Huang High School</td>
      <td>90</td>
      <td>60</td>
    </tr>
    <tr>
      <th>3</th>
      <td>3</td>
      <td>Dr. Richard Scott</td>
      <td>M</td>
      <td>12th</td>
      <td>Huang High School</td>
      <td>67</td>
      <td>58</td>
    </tr>
    <tr>
      <th>4</th>
      <td>4</td>
      <td>Bonnie Ray</td>
      <td>F</td>
      <td>9th</td>
      <td>Huang High School</td>
      <td>97</td>
      <td>84</td>
    </tr>
  </tbody>
</table>
</div>



Before we do any fancy work, let's first see all the column headings which we need to change and manipulate. 


```python
students_df.columns
```




    Index(['Student ID', 'name', 'gender', 'grade', 'school', 'reading_score',
           'math_score'],
          dtype='object')




```python
schools_df.columns
```




    Index(['School ID', 'name', 'type', 'size', 'budget'], dtype='object')



Let's display a table called "District Summary" with the following informaiton: 
Total Schools
Total Students
Total Budget
Average Math Score
Average Reading Score
% Passing Math
% Passing Reading
Overall Passing Rate (Average of the above two)

Steps: Sum up the required column headings and rename them. 


```python
schools_df.count()
```




    School ID    15
    name         15
    type         15
    size         15
    budget       15
    dtype: int64



# District Summary


```python
District_rows = schools_df.loc[schools_df['type']== 'District']
```


```python
print(len(District_rows))
```

    7



```python
print(District_rows)
```

        School ID                   name      type  size   budget
    0           0      Huang High School  District  2917  1910635
    1           1   Figueroa High School  District  2949  1884411
    3           3  Hernandez High School  District  4635  3022020
    7           7     Bailey High School  District  4976  3124928
    11         11  Rodriguez High School  District  3999  2547363
    12         12    Johnson High School  District  4761  3094650
    13         13       Ford High School  District  2739  1763916



```python
District_names = District_rows['name']
```


```python
Total_Students = students_df.loc[students_df['school'].isin(District_names)]
#Total_Students
```


```python
Total_Budget = District_rows['budget'].sum()
#print(Total_Budget)
```


```python
avg_math_score = round(Total_Students['math_score'].mean(),2)
```


```python
avg_read_score = round(Total_Students['reading_score'].mean(),2)
```


```python
percent_math_passing = len(Total_Students.loc[Total_Students['math_score'] >= 70])/len(Total_Students)*100
```


```python
print(percent_math_passing)
```

    66.51838671411625



```python
percent_reading_passing = len(Total_Students.loc[Total_Students['reading_score'] >= 70])/len(Total_Students)*100
```


```python
print(percent_reading_passing)
```

    80.90524911032028



```python
(percent_math_passing + percent_reading_passing)/2
```




    73.71181791221827




```python
district_summary_data = pd.DataFrame({
    'Total Schools': [len(District_rows)],
    'Total Students':[len(Total_Students)],
    'Total Budget':[Total_Budget],
    'Average Math Score': [avg_math_score],
    'Average Reading Score': [avg_read_score],
    '% Passing Math': [percent_math_passing],
    '% Passing Reading': [percent_reading_passing],
    'Overall Passing Rate':[(percent_math_passing + percent_reading_passing)/2]
})

district_summary_data 

```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Total Schools</th>
      <th>Total Students</th>
      <th>Total Budget</th>
      <th>Average Math Score</th>
      <th>Average Reading Score</th>
      <th>% Passing Math</th>
      <th>% Passing Reading</th>
      <th>Overall Passing Rate</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>7</td>
      <td>26976</td>
      <td>17347923</td>
      <td>76.99</td>
      <td>80.96</td>
      <td>66.518387</td>
      <td>80.905249</td>
      <td>73.711818</td>
    </tr>
  </tbody>
</table>
</div>



# School Summary 


```python
School_Summary_df = schools_df.loc[:,['name', 
                                      'type', 'size', 
                                      'budget']].rename(
    columns={'name':'School Name',
             'type':'School Type', 
             'size':'Total Students',
             'budget':'Total School Budget'
            })

# Per Student Budget 
Total_Schools_Budget = School_Summary_df['Total School Budget']/School_Summary_df['Total Students']
School_Summary_df['Per Student Budget'] = Total_Schools_Budget

# Average Math Score
Avg_Math_Score_Per_Student = []
for school in School_Summary_df['School Name']:
    Total_Students = students_df.loc[students_df['school'] == school]
    avg_math_score = round(Total_Students['math_score'].mean(),2)
    Avg_Math_Score_Per_Student.append(avg_math_score)
School_Summary_df['Average Math Score'] = pd.Series(Avg_Math_Score_Per_Student)

#Average Reading Score 
Avg_Reading_Score_Per_Student = []
for school in School_Summary_df['School Name']:
    Total_Students = students_df.loc[students_df['school'] == school]
    avg_reading_score = round(Total_Students['reading_score'].mean(),2)
    Avg_Reading_Score_Per_Student.append(avg_reading_score)
School_Summary_df['Average Reading Score'] = pd.Series(Avg_Reading_Score_Per_Student)

# % Passing Math
Percent_Math_Score = []
for school in School_Summary_df['School Name']:
    Total_Students = students_df.loc[students_df['school'] == school]
    percent_math_passing = len(Total_Students.loc[Total_Students['math_score'] >= 70])/len(Total_Students)*100
    Percent_Math_Score.append(percent_math_passing)
School_Summary_df['% Passing Math'] = pd.Series(Percent_Math_Score)

# % Passing Read
Percent_Read_Score = []
for school in School_Summary_df['School Name']:
    Total_Students = students_df.loc[students_df['school'] == school]
    percent_read_passing = len(Total_Students.loc[Total_Students['reading_score'] >= 70])/len(Total_Students)*100
    Percent_Read_Score.append(percent_read_passing)
School_Summary_df['% Passing Reading'] = pd.Series(Percent_Read_Score)

#Overall Passing Rate

Overall_Passing_Rate = (School_Summary_df['% Passing Math']+ School_Summary_df['% Passing Reading'])/2
School_Summary_df['Overall Passing Rate'] = Overall_Passing_Rate


School_Summary_df



```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>School Name</th>
      <th>School Type</th>
      <th>Total Students</th>
      <th>Total School Budget</th>
      <th>Per Student Budget</th>
      <th>Average Math Score</th>
      <th>Average Reading Score</th>
      <th>% Passing Math</th>
      <th>% Passing Reading</th>
      <th>Overall Passing Rate</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
      <td>655.0</td>
      <td>76.63</td>
      <td>81.18</td>
      <td>65.683922</td>
      <td>81.316421</td>
      <td>73.500171</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Figueroa High School</td>
      <td>District</td>
      <td>2949</td>
      <td>1884411</td>
      <td>639.0</td>
      <td>76.71</td>
      <td>81.16</td>
      <td>65.988471</td>
      <td>80.739234</td>
      <td>73.363852</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Shelton High School</td>
      <td>Charter</td>
      <td>1761</td>
      <td>1056600</td>
      <td>600.0</td>
      <td>83.36</td>
      <td>83.73</td>
      <td>93.867121</td>
      <td>95.854628</td>
      <td>94.860875</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Hernandez High School</td>
      <td>District</td>
      <td>4635</td>
      <td>3022020</td>
      <td>652.0</td>
      <td>77.29</td>
      <td>80.93</td>
      <td>66.752967</td>
      <td>80.862999</td>
      <td>73.807983</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Griffin High School</td>
      <td>Charter</td>
      <td>1468</td>
      <td>917500</td>
      <td>625.0</td>
      <td>83.35</td>
      <td>83.82</td>
      <td>93.392371</td>
      <td>97.138965</td>
      <td>95.265668</td>
    </tr>
    <tr>
      <th>5</th>
      <td>Wilson High School</td>
      <td>Charter</td>
      <td>2283</td>
      <td>1319574</td>
      <td>578.0</td>
      <td>83.27</td>
      <td>83.99</td>
      <td>93.867718</td>
      <td>96.539641</td>
      <td>95.203679</td>
    </tr>
    <tr>
      <th>6</th>
      <td>Cabrera High School</td>
      <td>Charter</td>
      <td>1858</td>
      <td>1081356</td>
      <td>582.0</td>
      <td>83.06</td>
      <td>83.98</td>
      <td>94.133477</td>
      <td>97.039828</td>
      <td>95.586652</td>
    </tr>
    <tr>
      <th>7</th>
      <td>Bailey High School</td>
      <td>District</td>
      <td>4976</td>
      <td>3124928</td>
      <td>628.0</td>
      <td>77.05</td>
      <td>81.03</td>
      <td>66.680064</td>
      <td>81.933280</td>
      <td>74.306672</td>
    </tr>
    <tr>
      <th>8</th>
      <td>Holden High School</td>
      <td>Charter</td>
      <td>427</td>
      <td>248087</td>
      <td>581.0</td>
      <td>83.80</td>
      <td>83.81</td>
      <td>92.505855</td>
      <td>96.252927</td>
      <td>94.379391</td>
    </tr>
    <tr>
      <th>9</th>
      <td>Pena High School</td>
      <td>Charter</td>
      <td>962</td>
      <td>585858</td>
      <td>609.0</td>
      <td>83.84</td>
      <td>84.04</td>
      <td>94.594595</td>
      <td>95.945946</td>
      <td>95.270270</td>
    </tr>
    <tr>
      <th>10</th>
      <td>Wright High School</td>
      <td>Charter</td>
      <td>1800</td>
      <td>1049400</td>
      <td>583.0</td>
      <td>83.68</td>
      <td>83.95</td>
      <td>93.333333</td>
      <td>96.611111</td>
      <td>94.972222</td>
    </tr>
    <tr>
      <th>11</th>
      <td>Rodriguez High School</td>
      <td>District</td>
      <td>3999</td>
      <td>2547363</td>
      <td>637.0</td>
      <td>76.84</td>
      <td>80.74</td>
      <td>66.366592</td>
      <td>80.220055</td>
      <td>73.293323</td>
    </tr>
    <tr>
      <th>12</th>
      <td>Johnson High School</td>
      <td>District</td>
      <td>4761</td>
      <td>3094650</td>
      <td>650.0</td>
      <td>77.07</td>
      <td>80.97</td>
      <td>66.057551</td>
      <td>81.222432</td>
      <td>73.639992</td>
    </tr>
    <tr>
      <th>13</th>
      <td>Ford High School</td>
      <td>District</td>
      <td>2739</td>
      <td>1763916</td>
      <td>644.0</td>
      <td>77.10</td>
      <td>80.75</td>
      <td>68.309602</td>
      <td>79.299014</td>
      <td>73.804308</td>
    </tr>
    <tr>
      <th>14</th>
      <td>Thomas High School</td>
      <td>Charter</td>
      <td>1635</td>
      <td>1043130</td>
      <td>638.0</td>
      <td>83.42</td>
      <td>83.85</td>
      <td>93.272171</td>
      <td>97.308869</td>
      <td>95.290520</td>
    </tr>
  </tbody>
</table>
</div>



# Top Performing Schools (By Overall Passing Rate)


```python
Top_Performing_Schools_Overall = School_Summary_df.sort_values("Overall Passing Rate", ascending=False)
Top_Performing_Schools_Overall.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>School Name</th>
      <th>School Type</th>
      <th>Total Students</th>
      <th>Total School Budget</th>
      <th>Per Student Budget</th>
      <th>Average Math Score</th>
      <th>Average Reading Score</th>
      <th>% Passing Math</th>
      <th>% Passing Reading</th>
      <th>Overall Passing Rate</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>6</th>
      <td>Cabrera High School</td>
      <td>Charter</td>
      <td>1858</td>
      <td>1081356</td>
      <td>582.0</td>
      <td>83.06</td>
      <td>83.98</td>
      <td>94.133477</td>
      <td>97.039828</td>
      <td>95.586652</td>
    </tr>
    <tr>
      <th>14</th>
      <td>Thomas High School</td>
      <td>Charter</td>
      <td>1635</td>
      <td>1043130</td>
      <td>638.0</td>
      <td>83.42</td>
      <td>83.85</td>
      <td>93.272171</td>
      <td>97.308869</td>
      <td>95.290520</td>
    </tr>
    <tr>
      <th>9</th>
      <td>Pena High School</td>
      <td>Charter</td>
      <td>962</td>
      <td>585858</td>
      <td>609.0</td>
      <td>83.84</td>
      <td>84.04</td>
      <td>94.594595</td>
      <td>95.945946</td>
      <td>95.270270</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Griffin High School</td>
      <td>Charter</td>
      <td>1468</td>
      <td>917500</td>
      <td>625.0</td>
      <td>83.35</td>
      <td>83.82</td>
      <td>93.392371</td>
      <td>97.138965</td>
      <td>95.265668</td>
    </tr>
    <tr>
      <th>5</th>
      <td>Wilson High School</td>
      <td>Charter</td>
      <td>2283</td>
      <td>1319574</td>
      <td>578.0</td>
      <td>83.27</td>
      <td>83.99</td>
      <td>93.867718</td>
      <td>96.539641</td>
      <td>95.203679</td>
    </tr>
  </tbody>
</table>
</div>



# Bottom Performing Schools (By Overall Passing Rate)


```python
Bottom_Performing_Schools_Overall = School_Summary_df.sort_values("Overall Passing Rate", ascending=True)
Bottom_Performing_Schools_Overall.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>School Name</th>
      <th>School Type</th>
      <th>Total Students</th>
      <th>Total School Budget</th>
      <th>Per Student Budget</th>
      <th>Average Math Score</th>
      <th>Average Reading Score</th>
      <th>% Passing Math</th>
      <th>% Passing Reading</th>
      <th>Overall Passing Rate</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>11</th>
      <td>Rodriguez High School</td>
      <td>District</td>
      <td>3999</td>
      <td>2547363</td>
      <td>637.0</td>
      <td>76.84</td>
      <td>80.74</td>
      <td>66.366592</td>
      <td>80.220055</td>
      <td>73.293323</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Figueroa High School</td>
      <td>District</td>
      <td>2949</td>
      <td>1884411</td>
      <td>639.0</td>
      <td>76.71</td>
      <td>81.16</td>
      <td>65.988471</td>
      <td>80.739234</td>
      <td>73.363852</td>
    </tr>
    <tr>
      <th>0</th>
      <td>Huang High School</td>
      <td>District</td>
      <td>2917</td>
      <td>1910635</td>
      <td>655.0</td>
      <td>76.63</td>
      <td>81.18</td>
      <td>65.683922</td>
      <td>81.316421</td>
      <td>73.500171</td>
    </tr>
    <tr>
      <th>12</th>
      <td>Johnson High School</td>
      <td>District</td>
      <td>4761</td>
      <td>3094650</td>
      <td>650.0</td>
      <td>77.07</td>
      <td>80.97</td>
      <td>66.057551</td>
      <td>81.222432</td>
      <td>73.639992</td>
    </tr>
    <tr>
      <th>13</th>
      <td>Ford High School</td>
      <td>District</td>
      <td>2739</td>
      <td>1763916</td>
      <td>644.0</td>
      <td>77.10</td>
      <td>80.75</td>
      <td>68.309602</td>
      <td>79.299014</td>
      <td>73.804308</td>
    </tr>
  </tbody>
</table>
</div>



# Math Scores by Grade


```python
# We need school name, grade level, average math score. 
#students_df.loc[:,['name', 'school', 'grade']] 

pd.pivot_table(students_df, values=['math_score'], index=['school'], columns=['grade'])

```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead tr th {
        text-align: left;
    }

    .dataframe thead tr:last-of-type th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr>
      <th></th>
      <th colspan="4" halign="left">math_score</th>
    </tr>
    <tr>
      <th>grade</th>
      <th>10th</th>
      <th>11th</th>
      <th>12th</th>
      <th>9th</th>
    </tr>
    <tr>
      <th>school</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Bailey High School</th>
      <td>76.996772</td>
      <td>77.515588</td>
      <td>76.492218</td>
      <td>77.083676</td>
    </tr>
    <tr>
      <th>Cabrera High School</th>
      <td>83.154506</td>
      <td>82.765560</td>
      <td>83.277487</td>
      <td>83.094697</td>
    </tr>
    <tr>
      <th>Figueroa High School</th>
      <td>76.539974</td>
      <td>76.884344</td>
      <td>77.151369</td>
      <td>76.403037</td>
    </tr>
    <tr>
      <th>Ford High School</th>
      <td>77.672316</td>
      <td>76.918058</td>
      <td>76.179963</td>
      <td>77.361345</td>
    </tr>
    <tr>
      <th>Griffin High School</th>
      <td>84.229064</td>
      <td>83.842105</td>
      <td>83.356164</td>
      <td>82.044010</td>
    </tr>
    <tr>
      <th>Hernandez High School</th>
      <td>77.337408</td>
      <td>77.136029</td>
      <td>77.186567</td>
      <td>77.438495</td>
    </tr>
    <tr>
      <th>Holden High School</th>
      <td>83.429825</td>
      <td>85.000000</td>
      <td>82.855422</td>
      <td>83.787402</td>
    </tr>
    <tr>
      <th>Huang High School</th>
      <td>75.908735</td>
      <td>76.446602</td>
      <td>77.225641</td>
      <td>77.027251</td>
    </tr>
    <tr>
      <th>Johnson High School</th>
      <td>76.691117</td>
      <td>77.491653</td>
      <td>76.863248</td>
      <td>77.187857</td>
    </tr>
    <tr>
      <th>Pena High School</th>
      <td>83.372000</td>
      <td>84.328125</td>
      <td>84.121547</td>
      <td>83.625455</td>
    </tr>
    <tr>
      <th>Rodriguez High School</th>
      <td>76.612500</td>
      <td>76.395626</td>
      <td>77.690748</td>
      <td>76.859966</td>
    </tr>
    <tr>
      <th>Shelton High School</th>
      <td>82.917411</td>
      <td>83.383495</td>
      <td>83.778976</td>
      <td>83.420755</td>
    </tr>
    <tr>
      <th>Thomas High School</th>
      <td>83.087886</td>
      <td>83.498795</td>
      <td>83.497041</td>
      <td>83.590022</td>
    </tr>
    <tr>
      <th>Wilson High School</th>
      <td>83.724422</td>
      <td>83.195326</td>
      <td>83.035794</td>
      <td>83.085578</td>
    </tr>
    <tr>
      <th>Wright High School</th>
      <td>84.010288</td>
      <td>83.836782</td>
      <td>83.644986</td>
      <td>83.264706</td>
    </tr>
  </tbody>
</table>
</div>



# Reading Scores by Grade 


```python
pd.pivot_table(students_df, values=['reading_score'], index=['school'], columns=['grade'])
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead tr th {
        text-align: left;
    }

    .dataframe thead tr:last-of-type th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr>
      <th></th>
      <th colspan="4" halign="left">reading_score</th>
    </tr>
    <tr>
      <th>grade</th>
      <th>10th</th>
      <th>11th</th>
      <th>12th</th>
      <th>9th</th>
    </tr>
    <tr>
      <th>school</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Bailey High School</th>
      <td>80.907183</td>
      <td>80.945643</td>
      <td>80.912451</td>
      <td>81.303155</td>
    </tr>
    <tr>
      <th>Cabrera High School</th>
      <td>84.253219</td>
      <td>83.788382</td>
      <td>84.287958</td>
      <td>83.676136</td>
    </tr>
    <tr>
      <th>Figueroa High School</th>
      <td>81.408912</td>
      <td>80.640339</td>
      <td>81.384863</td>
      <td>81.198598</td>
    </tr>
    <tr>
      <th>Ford High School</th>
      <td>81.262712</td>
      <td>80.403642</td>
      <td>80.662338</td>
      <td>80.632653</td>
    </tr>
    <tr>
      <th>Griffin High School</th>
      <td>83.706897</td>
      <td>84.288089</td>
      <td>84.013699</td>
      <td>83.369193</td>
    </tr>
    <tr>
      <th>Hernandez High School</th>
      <td>80.660147</td>
      <td>81.396140</td>
      <td>80.857143</td>
      <td>80.866860</td>
    </tr>
    <tr>
      <th>Holden High School</th>
      <td>83.324561</td>
      <td>83.815534</td>
      <td>84.698795</td>
      <td>83.677165</td>
    </tr>
    <tr>
      <th>Huang High School</th>
      <td>81.512386</td>
      <td>81.417476</td>
      <td>80.305983</td>
      <td>81.290284</td>
    </tr>
    <tr>
      <th>Johnson High School</th>
      <td>80.773431</td>
      <td>80.616027</td>
      <td>81.227564</td>
      <td>81.260714</td>
    </tr>
    <tr>
      <th>Pena High School</th>
      <td>83.612000</td>
      <td>84.335938</td>
      <td>84.591160</td>
      <td>83.807273</td>
    </tr>
    <tr>
      <th>Rodriguez High School</th>
      <td>80.629808</td>
      <td>80.864811</td>
      <td>80.376426</td>
      <td>80.993127</td>
    </tr>
    <tr>
      <th>Shelton High School</th>
      <td>83.441964</td>
      <td>84.373786</td>
      <td>82.781671</td>
      <td>84.122642</td>
    </tr>
    <tr>
      <th>Thomas High School</th>
      <td>84.254157</td>
      <td>83.585542</td>
      <td>83.831361</td>
      <td>83.728850</td>
    </tr>
    <tr>
      <th>Wilson High School</th>
      <td>84.021452</td>
      <td>83.764608</td>
      <td>84.317673</td>
      <td>83.939778</td>
    </tr>
    <tr>
      <th>Wright High School</th>
      <td>83.812757</td>
      <td>84.156322</td>
      <td>84.073171</td>
      <td>83.833333</td>
    </tr>
  </tbody>
</table>
</div>



Scores by School Spending


Create a table that breaks down school performances based on average Spending Ranges (Per Student). Use 4 reasonable bins to group school spending. Include in the table each of the following:


Average Math Score
Average Reading Score
% Passing Math
% Passing Reading
Overall Passing Rate (Average of the above two)


```python
#First we calculate the max and min values of thr per student budget.
maximum_spending = School_Summary_df['Per Student Budget'].max()
minimum_spending = School_Summary_df['Per Student Budget'].min()

#Then we choose bin values to segregate our data points.
d = (700-550)/5
550+d
580+d
610+d
640+d
670+d

#Let's organize our bins into a list. 
bin_labels = ['550 - 580', '580 - 610', '610 - 640', '640 - 670']

bin_lower_bound = [550, 580, 610, 640]
bin_upper_bound = [580, 610, 640, 670]

School_Performance = pd.DataFrame(columns =[
        'Spending Range Bin',
        'Average Math Score',
        'Average Reading Score',
        '% Passing Math',
        '% Passing Reading',
        'Overall Passing Rate'
])

i = 0
for i in np.arange(len(bin_lower_bound)):
    lower_bin = (School_Summary_df['Per Student Budget']>bin_lower_bound[i])
    upper_bin = (School_Summary_df['Per Student Budget']<bin_upper_bound[i])
    school_bin = School_Summary_df.loc[lower_bin].loc[upper_bin]
    School_Performance = School_Performance.append({
        'Spending Range Bin': bin_labels[i],
        'Average Math Score': school_bin["Average Math Score"].mean(),
        'Average Reading Score': school_bin["Average Reading Score"].mean(),
        '% Passing Math': school_bin["% Passing Math"].mean(),
        '% Passing Reading': school_bin["% Passing Reading"].mean(),
        'Overall Passing Rate': school_bin["Overall Passing Rate"].mean()
        }, ignore_index=True)

(School_Performance)

```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Spending Range Bin</th>
      <th>Average Math Score</th>
      <th>Average Reading Score</th>
      <th>% Passing Math</th>
      <th>% Passing Reading</th>
      <th>Overall Passing Rate</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>550 - 580</td>
      <td>83.2700</td>
      <td>83.9900</td>
      <td>93.867718</td>
      <td>96.539641</td>
      <td>95.203679</td>
    </tr>
    <tr>
      <th>1</th>
      <td>580 - 610</td>
      <td>83.5480</td>
      <td>83.9020</td>
      <td>93.686876</td>
      <td>96.340888</td>
      <td>95.013882</td>
    </tr>
    <tr>
      <th>2</th>
      <td>610 - 640</td>
      <td>79.4740</td>
      <td>82.1200</td>
      <td>77.139934</td>
      <td>87.468080</td>
      <td>82.304007</td>
    </tr>
    <tr>
      <th>3</th>
      <td>640 - 670</td>
      <td>77.0225</td>
      <td>80.9575</td>
      <td>66.701010</td>
      <td>80.675217</td>
      <td>73.688113</td>
    </tr>
  </tbody>
</table>
</div>



Scores by School Size

Repeat the above breakdown, but this time group schools based on a reasonable approximation of school size (Small, Medium, Large).



```python
#First we calculate the max and min values of the per-student budget.
maximum_school_size = School_Summary_df['Total Students'].max()
minimum_school_size = School_Summary_df['Total Students'].min()

#How many bins do you want in your wrap? 
# 0 - 1500 = small
#1500 - 3000 = medium
#3000 - 5000 = large


# #Let's organize our bins into a list. 
size_bin_labels = ['small', 'medium', 'large']

bin_lower_bound = [0, 1500, 3000]
bin_upper_bound = [1500, 3000, 5000]

School_Performance = pd.DataFrame(columns =[
        'School Size',
        'Average Math Score',
        'Average Reading Score',
        '% Passing Math',
        '% Passing Reading',
        'Overall Passing Rate'
])

i = 0
for i in np.arange(len(bin_lower_bound)):
    lower_bin = (School_Summary_df['Total Students']>bin_lower_bound[i])
    upper_bin = (School_Summary_df['Total Students']<bin_upper_bound[i])
    school_bin = School_Summary_df.loc[lower_bin].loc[upper_bin]
    School_Performance = School_Performance.append({
        'School Size': bin_labels[i],
        'Average Math Score': school_bin["Average Math Score"].mean(),
        'Average Reading Score': school_bin["Average Reading Score"].mean(),
        '% Passing Math': school_bin["% Passing Math"].mean(),
        '% Passing Reading': school_bin["% Passing Reading"].mean(),
        'Overall Passing Rate': school_bin["Overall Passing Rate"].mean()
        }, ignore_index=True)

(School_Performance)


```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>School Size</th>
      <th>Average Math Score</th>
      <th>Average Reading Score</th>
      <th>% Passing Math</th>
      <th>% Passing Reading</th>
      <th>Overall Passing Rate</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>550 - 580</td>
      <td>83.663333</td>
      <td>83.89000</td>
      <td>93.497607</td>
      <td>96.445946</td>
      <td>94.971776</td>
    </tr>
    <tr>
      <th>1</th>
      <td>580 - 610</td>
      <td>80.903750</td>
      <td>82.82375</td>
      <td>83.556977</td>
      <td>90.588593</td>
      <td>87.072785</td>
    </tr>
    <tr>
      <th>2</th>
      <td>610 - 640</td>
      <td>77.062500</td>
      <td>80.91750</td>
      <td>66.464293</td>
      <td>81.059691</td>
      <td>73.761992</td>
    </tr>
  </tbody>
</table>
</div>



Scores by School Type

Repeat the above breakdown, but this time group schools based on school type (Charter vs. District).


```python
School_Performance = pd.DataFrame(columns =[
        'School Type',
        'Average Math Score',
        'Average Reading Score',
        '% Passing Math',
        '% Passing Reading',
        'Overall Passing Rate'
])


upper_bin = (School_Summary_df['School Type']== 'Charter')
school_bin = School_Summary_df.loc[upper_bin]
School_Performance = School_Performance.append({
    'School Type': 'Charter',
    'Average Math Score': school_bin["Average Math Score"].mean(),
    'Average Reading Score': school_bin["Average Reading Score"].mean(),
    '% Passing Math': school_bin["% Passing Math"].mean(),
    '% Passing Reading': school_bin["% Passing Reading"].mean(),
    'Overall Passing Rate': school_bin["Overall Passing Rate"].mean()
    }, ignore_index=True)

upper_bin = (School_Summary_df['School Type']== 'District')
school_bin = School_Summary_df.loc[upper_bin]
School_Performance = School_Performance.append({
    'School Type': 'District',
    'Average Math Score': school_bin["Average Math Score"].mean(),
    'Average Reading Score': school_bin["Average Reading Score"].mean(),
    '% Passing Math': school_bin["% Passing Math"].mean(),
    '% Passing Reading': school_bin["% Passing Reading"].mean(),
    'Overall Passing Rate': school_bin["Overall Passing Rate"].mean()
    }, ignore_index=True)

(School_Performance)


```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>School Type</th>
      <th>Average Math Score</th>
      <th>Average Reading Score</th>
      <th>% Passing Math</th>
      <th>% Passing Reading</th>
      <th>Overall Passing Rate</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Charter</td>
      <td>83.472500</td>
      <td>83.896250</td>
      <td>93.620830</td>
      <td>96.586489</td>
      <td>95.103660</td>
    </tr>
    <tr>
      <th>1</th>
      <td>District</td>
      <td>76.955714</td>
      <td>80.965714</td>
      <td>66.548453</td>
      <td>80.799062</td>
      <td>73.673757</td>
    </tr>
  </tbody>
</table>
</div>



Charter schools have a higher passing rate. Charter has a higher passing score in math. Charter and District both do equally well in average reading scores, but significantly more students pass in the Charter school. So why are more students in Charter schools passing even though they perform the same as District schools in that category? 

Smaller schools seem to have a higher student performance, perhaps providing more individualized attention or they require less from their students. Schools which spend more seem to have poorer performance from students. 

Students perform worse in math than reading, no matter the school, how much is spent on them, nor the grade level. 


