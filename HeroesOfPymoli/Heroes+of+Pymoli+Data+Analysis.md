

```python
# Dependencies
import pandas as pd
import json
```


```python
# Read in json files
with open('purchase_data.json') as json_data_1:
    data_1 = json.load(json_data_1)

with open('purchase_data2.json') as json_data_2:
    data_2 = json.load(json_data_2)
```


```python
# Convert json to DataFrame
#player_data_df = pd.DataFrame(data_1)
player_data_df = pd.DataFrame(data_2)
player_data_df.head()
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
      <th>Age</th>
      <th>Gender</th>
      <th>Item ID</th>
      <th>Item Name</th>
      <th>Price</th>
      <th>SN</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>20</td>
      <td>Male</td>
      <td>93</td>
      <td>Apocalyptic Battlescythe</td>
      <td>4.49</td>
      <td>Iloni35</td>
    </tr>
    <tr>
      <th>1</th>
      <td>21</td>
      <td>Male</td>
      <td>12</td>
      <td>Dawne</td>
      <td>3.36</td>
      <td>Aidaira26</td>
    </tr>
    <tr>
      <th>2</th>
      <td>17</td>
      <td>Male</td>
      <td>5</td>
      <td>Putrid Fan</td>
      <td>2.63</td>
      <td>Irim47</td>
    </tr>
    <tr>
      <th>3</th>
      <td>17</td>
      <td>Male</td>
      <td>123</td>
      <td>Twilight's Carver</td>
      <td>2.55</td>
      <td>Irith83</td>
    </tr>
    <tr>
      <th>4</th>
      <td>22</td>
      <td>Male</td>
      <td>154</td>
      <td>Feral Katana</td>
      <td>4.11</td>
      <td>Philodil43</td>
    </tr>
  </tbody>
</table>
</div>




```python
# Calculate total number of players
unique_player_data_df = player_data_df.groupby(by='SN')
total_players = unique_player_data_df.size().count()
print(total_players)
```

    74
    


```python
# Count number of unique items purchased
unique_items = player_data_df.groupby(by='Item Name').size().count()
print(unique_items)
```

    63
    


```python
# Calculate average purchase price
average_purchase_price = player_data_df['Price'].mean()
print(average_purchase_price)
```

    2.9243589743589733
    


```python
# Count total number of purchases
total_purchases = player_data_df['Price'].count()
print(total_purchases)
```

    78
    


```python
# Sum total revenue
total_revenue = player_data_df['Price'].sum()
print(total_revenue)
```

    228.0999999999999
    


```python
# Check for the categories of responses to gender
player_data_df['Gender'].unique()
```




    array(['Male', 'Female', 'Other / Non-Disclosed'], dtype=object)




```python
# Count number of unique players who self-identify as male; female; or are of non-binary gender identification  
gender_player_data_df = player_data_df.groupby(by='Gender')
total_gender = gender_player_data_df['SN'].nunique().sum()
male = gender_player_data_df['SN'].nunique()['Male']
female = gender_player_data_df['SN'].nunique()['Female']
non_gender_specific = total_gender - male - female
print(f' Total: {total_gender}\n Male: {male}\n Female: {female}\n non_specfic: {non_gender_specific}')
```

     Total: 74
     Male: 60
     Female: 13
     non_specfic: 1
    


```python
players_per_gender = gender_player_data_df['SN'].nunique()
print(players_per_gender)
```

    Gender
    Female                   13
    Male                     60
    Other / Non-Disclosed     1
    Name: SN, dtype: int64
    


```python
# Calculate percentage of respondents belonging to each gender
male_percent = (male/total_gender) * 100
female_percent = (female/total_gender) * 100
non_gender_specific_percent = (non_gender_specific/total_gender) * 100
print(f' % Male: {male_percent}\n % Female: {female_percent}\n % non_specifc: {non_gender_specific}')
```

     % Male: 81.08108108108108
     % Female: 17.56756756756757
     % non_specifc: 1
    


```python
# Purchase count by gender
gender_purchase_count = gender_player_data_df['Item Name'].count()
gender_purchase_count
```




    Gender
    Female                   13
    Male                     64
    Other / Non-Disclosed     1
    Name: Item Name, dtype: int64




```python
# Average purchase price by gender
gender_average_price = gender_player_data_df['Price'].mean()
gender_average_price
```




    Gender
    Female                   3.183077
    Male                     2.884375
    Other / Non-Disclosed    2.120000
    Name: Price, dtype: float64




```python
# Total purchase value by gender
gender_total_value = gender_player_data_df['Price'].sum()
gender_total_value
```




    Gender
    Female                    41.38
    Male                     184.60
    Other / Non-Disclosed      2.12
    Name: Price, dtype: float64




```python
# Normalized totals by gender
# The normalized totals here are the purchase total per gender, divided by the player count per gender.
gender_normalized_total = gender_total_value / players_per_gender
gender_normalized_total
```




    Gender
    Female                   3.183077
    Male                     3.076667
    Other / Non-Disclosed    2.120000
    dtype: float64




```python
# Group data by age into bins
bins = [0, 9, 14, 19, 24, 29, 34, 39, 100]
labels = ['Under 10', '10-14','15-19','20-24', '25-29', '30-34', '35-39', '40 and over']
player_data_df['Age Group'] = pd.cut(player_data_df['Age'], bins, labels=labels)
player_data_df.head()
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
      <th>Age</th>
      <th>Gender</th>
      <th>Item ID</th>
      <th>Item Name</th>
      <th>Price</th>
      <th>SN</th>
      <th>Age Group</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>20</td>
      <td>Male</td>
      <td>93</td>
      <td>Apocalyptic Battlescythe</td>
      <td>4.49</td>
      <td>Iloni35</td>
      <td>20-24</td>
    </tr>
    <tr>
      <th>1</th>
      <td>21</td>
      <td>Male</td>
      <td>12</td>
      <td>Dawne</td>
      <td>3.36</td>
      <td>Aidaira26</td>
      <td>20-24</td>
    </tr>
    <tr>
      <th>2</th>
      <td>17</td>
      <td>Male</td>
      <td>5</td>
      <td>Putrid Fan</td>
      <td>2.63</td>
      <td>Irim47</td>
      <td>15-19</td>
    </tr>
    <tr>
      <th>3</th>
      <td>17</td>
      <td>Male</td>
      <td>123</td>
      <td>Twilight's Carver</td>
      <td>2.55</td>
      <td>Irith83</td>
      <td>15-19</td>
    </tr>
    <tr>
      <th>4</th>
      <td>22</td>
      <td>Male</td>
      <td>154</td>
      <td>Feral Katana</td>
      <td>4.11</td>
      <td>Philodil43</td>
      <td>20-24</td>
    </tr>
  </tbody>
</table>
</div>




```python
# Group data by age
player_age_group_data_df = player_data_df.groupby(by='Age Group')
players_per_age_group = player_age_group_data_df['SN'].nunique()
print(players_per_age_group)
```

    Age Group
    Under 10        5
    10-14           3
    15-19          11
    20-24          34
    25-29           8
    30-34           6
    35-39           6
    40 and over     1
    Name: SN, dtype: int64
    


```python
# Purchase count by age group
purchase_count_by_age_group = player_age_group_data_df['Item Name'].count()
purchase_count_by_age_group
```




    Age Group
    Under 10        5
    10-14           3
    15-19          11
    20-24          36
    25-29           9
    30-34           7
    35-39           6
    40 and over     1
    Name: Item Name, dtype: int64




```python
# Average purchase price by age group
average_purchase_price_by_age_group = player_age_group_data_df['Price'].mean()
average_purchase_price_by_age_group
```




    Age Group
    Under 10       2.764000
    10-14          2.986667
    15-19          2.764545
    20-24          3.024722
    25-29          2.901111
    30-34          1.984286
    35-39          3.561667
    40 and over    4.650000
    Name: Price, dtype: float64




```python
# Total purchase value by age group
total_purchase_value_by_age_group = player_age_group_data_df['Price'].sum()
total_purchase_value_by_age_group
```




    Age Group
    Under 10        13.82
    10-14            8.96
    15-19           30.41
    20-24          108.89
    25-29           26.11
    30-34           13.89
    35-39           21.37
    40 and over      4.65
    Name: Price, dtype: float64




```python
# Normalized totals by age
# The normalized totals here are the purchase total per age group, divided by the player count per age group.
age_group_normalized_total = total_purchase_value_by_age_group / players_per_age_group
age_group_normalized_total
```




    Age Group
    Under 10       2.764000
    10-14          2.986667
    15-19          2.764545
    20-24          3.202647
    25-29          3.263750
    30-34          2.315000
    35-39          3.561667
    40 and over    4.650000
    dtype: float64




```python
unique_player_total_value = unique_player_data_df['Price'].sum()
unique_player_total_value = unique_player_total_value.sort_values(ascending=False)
top_spenders = unique_player_total_value.nlargest(5)
print(top_spenders)
```

    SN
    Sundaky74     7.41
    Aidaira26     5.13
    Eusty71       4.81
    Chanirra64    4.78
    Alarap40      4.71
    Name: Price, dtype: float64
    


```python
player_data_df.loc[player_data_df['SN']=='Sundaky74']
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
      <th>Age</th>
      <th>Gender</th>
      <th>Item ID</th>
      <th>Item Name</th>
      <th>Price</th>
      <th>SN</th>
      <th>Age Group</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>27</th>
      <td>25</td>
      <td>Male</td>
      <td>117</td>
      <td>Heartstriker, Legacy of the Light</td>
      <td>4.71</td>
      <td>Sundaky74</td>
      <td>25-29</td>
    </tr>
    <tr>
      <th>71</th>
      <td>25</td>
      <td>Male</td>
      <td>60</td>
      <td>Wolf</td>
      <td>2.70</td>
      <td>Sundaky74</td>
      <td>25-29</td>
    </tr>
  </tbody>
</table>
</div>




```python
# Most popular items
most_popular_items = player_data_df.groupby(by='Item ID')
most_popular_items.count().sort_values('Item Name',ascending=False).head(5)
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
      <th>Age</th>
      <th>Gender</th>
      <th>Item Name</th>
      <th>Price</th>
      <th>SN</th>
      <th>Age Group</th>
    </tr>
    <tr>
      <th>Item ID</th>
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
      <th>94</th>
      <td>3</td>
      <td>3</td>
      <td>3</td>
      <td>3</td>
      <td>3</td>
      <td>3</td>
    </tr>
    <tr>
      <th>90</th>
      <td>2</td>
      <td>2</td>
      <td>2</td>
      <td>2</td>
      <td>2</td>
      <td>2</td>
    </tr>
    <tr>
      <th>111</th>
      <td>2</td>
      <td>2</td>
      <td>2</td>
      <td>2</td>
      <td>2</td>
      <td>2</td>
    </tr>
    <tr>
      <th>64</th>
      <td>2</td>
      <td>2</td>
      <td>2</td>
      <td>2</td>
      <td>2</td>
      <td>2</td>
    </tr>
    <tr>
      <th>154</th>
      <td>2</td>
      <td>2</td>
      <td>2</td>
      <td>2</td>
      <td>2</td>
      <td>2</td>
    </tr>
  </tbody>
</table>
</div>




```python

```
