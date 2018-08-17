
# Reading CSV Files
Let's practice reading csv files with this toy dataset on student scores. As you've seen a few times already, `read_csv()` is used to load data from csv files into a Pandas dataframe. We just need to specify the filepath of our data. I stored `student_scores.csv` in the same directory as this Jupyter notebook, so we just need to provide the name of the file.

Run each cell as you go through this Jupyter notebook.


```python
import pandas as pd

df = pd.read_csv('student_scores.csv')
```

`head()` is a useful function you can call on your dataframe to display the first few rows. Let's use it to see what this data looks like.


```python
df.head()
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>ID</th>
      <th>Name</th>
      <th>Attendance</th>
      <th>HW</th>
      <th>Test1</th>
      <th>Project1</th>
      <th>Test2</th>
      <th>Project2</th>
      <th>Final</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>27604</td>
      <td>Joe</td>
      <td>0.96</td>
      <td>0.97</td>
      <td>87.0</td>
      <td>98.0</td>
      <td>92.0</td>
      <td>93.0</td>
      <td>95.0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>30572</td>
      <td>Alex</td>
      <td>1.00</td>
      <td>0.84</td>
      <td>92.0</td>
      <td>89.0</td>
      <td>94.0</td>
      <td>92.0</td>
      <td>91.0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>39203</td>
      <td>Avery</td>
      <td>0.84</td>
      <td>0.74</td>
      <td>68.0</td>
      <td>70.0</td>
      <td>84.0</td>
      <td>90.0</td>
      <td>82.0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>28592</td>
      <td>Kris</td>
      <td>0.96</td>
      <td>1.00</td>
      <td>82.0</td>
      <td>94.0</td>
      <td>90.0</td>
      <td>81.0</td>
      <td>84.0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>27492</td>
      <td>Rick</td>
      <td>0.32</td>
      <td>0.85</td>
      <td>98.0</td>
      <td>100.0</td>
      <td>73.0</td>
      <td>82.0</td>
      <td>88.0</td>
    </tr>
  </tbody>
</table>
</div>



Remember, CSV stands for comma separated values - but they can actually be separated by different characters, tabs, white space, etc. If your file is separated by a colon, let's say, you can still use `read_csv()` with the `sep` parameter.


```python
df = pd.read_csv('student_scores.csv', sep=':')
df.head()
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>ID,Name,Attendance,HW,Test1,Project1,Test2,Project2,Final</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>27604,Joe,0.96,0.97,87.0,98.0,92.0,93.0,95.0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>30572,Alex,1.0,0.84,92.0,89.0,94.0,92.0,91.0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>39203,Avery,0.84,0.74,68.0,70.0,84.0,90.0,82.0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>28592,Kris,0.96,1.0,82.0,94.0,90.0,81.0,84.0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>27492,Rick,0.32,0.85,98.0,100.0,73.0,82.0,88.0</td>
    </tr>
  </tbody>
</table>
</div>



This obviously didn't work because there our CSV file is separated by commas. Because there are no colons, nothing was separated and everything was read into one column!

## Headers
Another thing you can do with `read_csv` is specify which line of the file is the header, which specifies the column labels. It's usually the first line, but sometimes we'll want to specify a later line if there is extra meta information at the top of the file. We can do that like this.


```python
df = pd.read_csv('student_scores.csv', header=2)
df.head()
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>30572</th>
      <th>Alex</th>
      <th>1.0</th>
      <th>0.84</th>
      <th>92.0</th>
      <th>89.0</th>
      <th>94.0</th>
      <th>92.0.1</th>
      <th>91.0</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>39203</td>
      <td>Avery</td>
      <td>0.84</td>
      <td>0.74</td>
      <td>68.0</td>
      <td>70.0</td>
      <td>84.0</td>
      <td>90.0</td>
      <td>82.0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>28592</td>
      <td>Kris</td>
      <td>0.96</td>
      <td>1.00</td>
      <td>82.0</td>
      <td>94.0</td>
      <td>90.0</td>
      <td>81.0</td>
      <td>84.0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>27492</td>
      <td>Rick</td>
      <td>0.32</td>
      <td>0.85</td>
      <td>98.0</td>
      <td>100.0</td>
      <td>73.0</td>
      <td>82.0</td>
      <td>88.0</td>
    </tr>
  </tbody>
</table>
</div>



Here, row 2 was used as the the header and everything above that was cut off. By default, `read_csv` uses header=0, which uses the first line for column labels.

If columns labels are not included in your file, you can use `header=None` to prevent your first line of data from being misinterpreted as column labels.


```python
df = pd.read_csv('student_scores.csv', header=None)
df.head()
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>0</th>
      <th>1</th>
      <th>2</th>
      <th>3</th>
      <th>4</th>
      <th>5</th>
      <th>6</th>
      <th>7</th>
      <th>8</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>ID</td>
      <td>Name</td>
      <td>Attendance</td>
      <td>HW</td>
      <td>Test1</td>
      <td>Project1</td>
      <td>Test2</td>
      <td>Project2</td>
      <td>Final</td>
    </tr>
    <tr>
      <th>1</th>
      <td>27604</td>
      <td>Joe</td>
      <td>0.96</td>
      <td>0.97</td>
      <td>87.0</td>
      <td>98.0</td>
      <td>92.0</td>
      <td>93.0</td>
      <td>95.0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>30572</td>
      <td>Alex</td>
      <td>1.0</td>
      <td>0.84</td>
      <td>92.0</td>
      <td>89.0</td>
      <td>94.0</td>
      <td>92.0</td>
      <td>91.0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>39203</td>
      <td>Avery</td>
      <td>0.84</td>
      <td>0.74</td>
      <td>68.0</td>
      <td>70.0</td>
      <td>84.0</td>
      <td>90.0</td>
      <td>82.0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>28592</td>
      <td>Kris</td>
      <td>0.96</td>
      <td>1.0</td>
      <td>82.0</td>
      <td>94.0</td>
      <td>90.0</td>
      <td>81.0</td>
      <td>84.0</td>
    </tr>
  </tbody>
</table>
</div>



You can also specify your own column labels like this.


```python
labels = ['id', 'name', 'attendance', 'hw', 'test1', 'project1', 'test2', 'project2', 'final']
df = pd.read_csv('student_scores.csv', names=labels)
df.head()
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>id</th>
      <th>name</th>
      <th>attendance</th>
      <th>hw</th>
      <th>test1</th>
      <th>project1</th>
      <th>test2</th>
      <th>project2</th>
      <th>final</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>ID</td>
      <td>Name</td>
      <td>Attendance</td>
      <td>HW</td>
      <td>Test1</td>
      <td>Project1</td>
      <td>Test2</td>
      <td>Project2</td>
      <td>Final</td>
    </tr>
    <tr>
      <th>1</th>
      <td>27604</td>
      <td>Joe</td>
      <td>0.96</td>
      <td>0.97</td>
      <td>87.0</td>
      <td>98.0</td>
      <td>92.0</td>
      <td>93.0</td>
      <td>95.0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>30572</td>
      <td>Alex</td>
      <td>1.0</td>
      <td>0.84</td>
      <td>92.0</td>
      <td>89.0</td>
      <td>94.0</td>
      <td>92.0</td>
      <td>91.0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>39203</td>
      <td>Avery</td>
      <td>0.84</td>
      <td>0.74</td>
      <td>68.0</td>
      <td>70.0</td>
      <td>84.0</td>
      <td>90.0</td>
      <td>82.0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>28592</td>
      <td>Kris</td>
      <td>0.96</td>
      <td>1.0</td>
      <td>82.0</td>
      <td>94.0</td>
      <td>90.0</td>
      <td>81.0</td>
      <td>84.0</td>
    </tr>
  </tbody>
</table>
</div>



If you want to tell pandas that there was a header line that you are replacing, you can specify the row of that line like this.


```python
labels = ['id', 'name', 'attendance', 'hw', 'test1', 'project1', 'test2', 'project2', 'final']
df = pd.read_csv('student_scores.csv', header=0, names=labels)
df.head()
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>id</th>
      <th>name</th>
      <th>attendance</th>
      <th>hw</th>
      <th>test1</th>
      <th>project1</th>
      <th>test2</th>
      <th>project2</th>
      <th>final</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>27604</td>
      <td>Joe</td>
      <td>0.96</td>
      <td>0.97</td>
      <td>87.0</td>
      <td>98.0</td>
      <td>92.0</td>
      <td>93.0</td>
      <td>95.0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>30572</td>
      <td>Alex</td>
      <td>1.00</td>
      <td>0.84</td>
      <td>92.0</td>
      <td>89.0</td>
      <td>94.0</td>
      <td>92.0</td>
      <td>91.0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>39203</td>
      <td>Avery</td>
      <td>0.84</td>
      <td>0.74</td>
      <td>68.0</td>
      <td>70.0</td>
      <td>84.0</td>
      <td>90.0</td>
      <td>82.0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>28592</td>
      <td>Kris</td>
      <td>0.96</td>
      <td>1.00</td>
      <td>82.0</td>
      <td>94.0</td>
      <td>90.0</td>
      <td>81.0</td>
      <td>84.0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>27492</td>
      <td>Rick</td>
      <td>0.32</td>
      <td>0.85</td>
      <td>98.0</td>
      <td>100.0</td>
      <td>73.0</td>
      <td>82.0</td>
      <td>88.0</td>
    </tr>
  </tbody>
</table>
</div>



## Index
Instead of using the default index (integers incrementing by 1 from 0), you can specify one or more of your columns to be the index of your dataframe.


```python
df = pd.read_csv('student_scores.csv', index_col='Name')
df.head()
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>ID</th>
      <th>Attendance</th>
      <th>HW</th>
      <th>Test1</th>
      <th>Project1</th>
      <th>Test2</th>
      <th>Project2</th>
      <th>Final</th>
    </tr>
    <tr>
      <th>Name</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Joe</th>
      <td>27604</td>
      <td>0.96</td>
      <td>0.97</td>
      <td>87.0</td>
      <td>98.0</td>
      <td>92.0</td>
      <td>93.0</td>
      <td>95.0</td>
    </tr>
    <tr>
      <th>Alex</th>
      <td>30572</td>
      <td>1.00</td>
      <td>0.84</td>
      <td>92.0</td>
      <td>89.0</td>
      <td>94.0</td>
      <td>92.0</td>
      <td>91.0</td>
    </tr>
    <tr>
      <th>Avery</th>
      <td>39203</td>
      <td>0.84</td>
      <td>0.74</td>
      <td>68.0</td>
      <td>70.0</td>
      <td>84.0</td>
      <td>90.0</td>
      <td>82.0</td>
    </tr>
    <tr>
      <th>Kris</th>
      <td>28592</td>
      <td>0.96</td>
      <td>1.00</td>
      <td>82.0</td>
      <td>94.0</td>
      <td>90.0</td>
      <td>81.0</td>
      <td>84.0</td>
    </tr>
    <tr>
      <th>Rick</th>
      <td>27492</td>
      <td>0.32</td>
      <td>0.85</td>
      <td>98.0</td>
      <td>100.0</td>
      <td>73.0</td>
      <td>82.0</td>
      <td>88.0</td>
    </tr>
  </tbody>
</table>
</div>




```python
df = pd.read_csv('student_scores.csv', index_col=['Name', 'ID'])
df.head()
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th></th>
      <th>Attendance</th>
      <th>HW</th>
      <th>Test1</th>
      <th>Project1</th>
      <th>Test2</th>
      <th>Project2</th>
      <th>Final</th>
    </tr>
    <tr>
      <th>Name</th>
      <th>ID</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Joe</th>
      <th>27604</th>
      <td>0.96</td>
      <td>0.97</td>
      <td>87.0</td>
      <td>98.0</td>
      <td>92.0</td>
      <td>93.0</td>
      <td>95.0</td>
    </tr>
    <tr>
      <th>Alex</th>
      <th>30572</th>
      <td>1.00</td>
      <td>0.84</td>
      <td>92.0</td>
      <td>89.0</td>
      <td>94.0</td>
      <td>92.0</td>
      <td>91.0</td>
    </tr>
    <tr>
      <th>Avery</th>
      <th>39203</th>
      <td>0.84</td>
      <td>0.74</td>
      <td>68.0</td>
      <td>70.0</td>
      <td>84.0</td>
      <td>90.0</td>
      <td>82.0</td>
    </tr>
    <tr>
      <th>Kris</th>
      <th>28592</th>
      <td>0.96</td>
      <td>1.00</td>
      <td>82.0</td>
      <td>94.0</td>
      <td>90.0</td>
      <td>81.0</td>
      <td>84.0</td>
    </tr>
    <tr>
      <th>Rick</th>
      <th>27492</th>
      <td>0.32</td>
      <td>0.85</td>
      <td>98.0</td>
      <td>100.0</td>
      <td>73.0</td>
      <td>82.0</td>
      <td>88.0</td>
    </tr>
  </tbody>
</table>
</div>



There are many other things you can do with this function alone, such as parsing dates, filling null values, skipping rows, etc. A lot of these can be done in different steps after `read_csv()`. We're going to modify our data in other ways, but you can always look up how to do some steps with this function [here](https://pandas.pydata.org/pandas-docs/stable/generated/pandas.read_csv.html).

## Quiz #1
Use `read_csv()` to read in `cancer_data.csv` and use an appropriate column as the index. Then, use `.head()` on your dataframe to see if you've done this correctly. *Hint: First call `read_csv()` **without parameters** and then `head()` to see what the data looks like.*


```python
df_cancer =pd.read_csv('cancer_data.csv')
df_cancer.head()
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>id</th>
      <th>diagnosis</th>
      <th>radius_mean</th>
      <th>texture_mean</th>
      <th>perimeter_mean</th>
      <th>area_mean</th>
      <th>smoothness_mean</th>
      <th>compactness_mean</th>
      <th>concavity_mean</th>
      <th>concave_points_mean</th>
      <th>...</th>
      <th>radius_max</th>
      <th>texture_max</th>
      <th>perimeter_max</th>
      <th>area_max</th>
      <th>smoothness_max</th>
      <th>compactness_max</th>
      <th>concavity_max</th>
      <th>concave_points_max</th>
      <th>symmetry_max</th>
      <th>fractal_dimension_max</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>842302</td>
      <td>M</td>
      <td>17.99</td>
      <td>NaN</td>
      <td>122.80</td>
      <td>1001.0</td>
      <td>0.11840</td>
      <td>0.27760</td>
      <td>0.3001</td>
      <td>0.14710</td>
      <td>...</td>
      <td>25.38</td>
      <td>NaN</td>
      <td>184.60</td>
      <td>2019.0</td>
      <td>0.1622</td>
      <td>0.6656</td>
      <td>0.7119</td>
      <td>0.2654</td>
      <td>0.4601</td>
      <td>0.11890</td>
    </tr>
    <tr>
      <th>1</th>
      <td>842517</td>
      <td>M</td>
      <td>20.57</td>
      <td>17.77</td>
      <td>132.90</td>
      <td>1326.0</td>
      <td>0.08474</td>
      <td>0.07864</td>
      <td>0.0869</td>
      <td>0.07017</td>
      <td>...</td>
      <td>24.99</td>
      <td>23.41</td>
      <td>158.80</td>
      <td>1956.0</td>
      <td>0.1238</td>
      <td>0.1866</td>
      <td>0.2416</td>
      <td>0.1860</td>
      <td>0.2750</td>
      <td>0.08902</td>
    </tr>
    <tr>
      <th>2</th>
      <td>84300903</td>
      <td>M</td>
      <td>19.69</td>
      <td>21.25</td>
      <td>130.00</td>
      <td>1203.0</td>
      <td>0.10960</td>
      <td>0.15990</td>
      <td>0.1974</td>
      <td>0.12790</td>
      <td>...</td>
      <td>23.57</td>
      <td>25.53</td>
      <td>152.50</td>
      <td>1709.0</td>
      <td>0.1444</td>
      <td>0.4245</td>
      <td>0.4504</td>
      <td>0.2430</td>
      <td>0.3613</td>
      <td>0.08758</td>
    </tr>
    <tr>
      <th>3</th>
      <td>84348301</td>
      <td>M</td>
      <td>11.42</td>
      <td>20.38</td>
      <td>77.58</td>
      <td>386.1</td>
      <td>NaN</td>
      <td>0.28390</td>
      <td>0.2414</td>
      <td>0.10520</td>
      <td>...</td>
      <td>14.91</td>
      <td>26.50</td>
      <td>98.87</td>
      <td>567.7</td>
      <td>NaN</td>
      <td>0.8663</td>
      <td>0.6869</td>
      <td>0.2575</td>
      <td>0.6638</td>
      <td>0.17300</td>
    </tr>
    <tr>
      <th>4</th>
      <td>84358402</td>
      <td>M</td>
      <td>20.29</td>
      <td>14.34</td>
      <td>135.10</td>
      <td>1297.0</td>
      <td>0.10030</td>
      <td>0.13280</td>
      <td>0.1980</td>
      <td>0.10430</td>
      <td>...</td>
      <td>22.54</td>
      <td>16.67</td>
      <td>152.20</td>
      <td>1575.0</td>
      <td>0.1374</td>
      <td>0.2050</td>
      <td>0.4000</td>
      <td>0.1625</td>
      <td>0.2364</td>
      <td>0.07678</td>
    </tr>
  </tbody>
</table>
<p>5 rows × 32 columns</p>
</div>



## Quiz #2
Use `read_csv()` to read in `powerplant_data.csv` with more descriptive column names based on the description of features on this [website](http://archive.ics.uci.edu/ml/datasets/combined+cycle+power+plant). Then, use `.head()` on your dataframe to see if you've done this correctly. *Hint: Like in the previous quiz, first call `read_csv()` without parameters and then `head()` to see what the data looks like.*


```python
df_powerplant =pd.read_csv('powerplant_data.csv')
df_powerplant.head()
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>AT</th>
      <th>V</th>
      <th>AP</th>
      <th>RH</th>
      <th>PE</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>8.34</td>
      <td>40.77</td>
      <td>1010.84</td>
      <td>90.01</td>
      <td>480.48</td>
    </tr>
    <tr>
      <th>1</th>
      <td>23.64</td>
      <td>58.49</td>
      <td>1011.40</td>
      <td>74.20</td>
      <td>445.75</td>
    </tr>
    <tr>
      <th>2</th>
      <td>29.74</td>
      <td>56.90</td>
      <td>1007.15</td>
      <td>41.91</td>
      <td>438.76</td>
    </tr>
    <tr>
      <th>3</th>
      <td>19.07</td>
      <td>49.69</td>
      <td>1007.22</td>
      <td>76.79</td>
      <td>453.09</td>
    </tr>
    <tr>
      <th>4</th>
      <td>11.80</td>
      <td>40.66</td>
      <td>1017.13</td>
      <td>97.20</td>
      <td>464.43</td>
    </tr>
  </tbody>
</table>
</div>



# Writing CSV Files
Awesome! Now, we'll save your second dataframe with power plant data into a csv file for the next section.


```python
df_powerplant.to_csv('powerplant_data_edited.csv')
```

Let's see if that worked the way we wanted.


```python
df = pd.read_csv('powerplant_data_edited.csv')
df.head()
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Unnamed: 0</th>
      <th>AT</th>
      <th>V</th>
      <th>AP</th>
      <th>RH</th>
      <th>PE</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>0</td>
      <td>8.34</td>
      <td>40.77</td>
      <td>1010.84</td>
      <td>90.01</td>
      <td>480.48</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1</td>
      <td>23.64</td>
      <td>58.49</td>
      <td>1011.40</td>
      <td>74.20</td>
      <td>445.75</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2</td>
      <td>29.74</td>
      <td>56.90</td>
      <td>1007.15</td>
      <td>41.91</td>
      <td>438.76</td>
    </tr>
    <tr>
      <th>3</th>
      <td>3</td>
      <td>19.07</td>
      <td>49.69</td>
      <td>1007.22</td>
      <td>76.79</td>
      <td>453.09</td>
    </tr>
    <tr>
      <th>4</th>
      <td>4</td>
      <td>11.80</td>
      <td>40.66</td>
      <td>1017.13</td>
      <td>97.20</td>
      <td>464.43</td>
    </tr>
  </tbody>
</table>
</div>



What's this `Unnamed:0`? `to_csv()` will store our index unless we tell it not to. To make it ignore the index, we have to provide the parameter `index=False`


```python
df_powerplant.to_csv('powerplant_data_edited.csv', index=False)
```


```python
df = pd.read_csv('powerplant_data_edited.csv')
df.head()
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>AT</th>
      <th>V</th>
      <th>AP</th>
      <th>RH</th>
      <th>PE</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>8.34</td>
      <td>40.77</td>
      <td>1010.84</td>
      <td>90.01</td>
      <td>480.48</td>
    </tr>
    <tr>
      <th>1</th>
      <td>23.64</td>
      <td>58.49</td>
      <td>1011.40</td>
      <td>74.20</td>
      <td>445.75</td>
    </tr>
    <tr>
      <th>2</th>
      <td>29.74</td>
      <td>56.90</td>
      <td>1007.15</td>
      <td>41.91</td>
      <td>438.76</td>
    </tr>
    <tr>
      <th>3</th>
      <td>19.07</td>
      <td>49.69</td>
      <td>1007.22</td>
      <td>76.79</td>
      <td>453.09</td>
    </tr>
    <tr>
      <th>4</th>
      <td>11.80</td>
      <td>40.66</td>
      <td>1017.13</td>
      <td>97.20</td>
      <td>464.43</td>
    </tr>
  </tbody>
</table>
</div>


