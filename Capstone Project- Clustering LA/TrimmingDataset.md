# Trimming the [Dataset](https://catalog.data.gov/dataset/addresses-in-the-city-of-los-angeles) before pre-processing and modelling


```python
import pandas as pd # library to process data as dataframes
```


```python
la_dataset = pd.read_csv('Addresses_in_the_City_of_Los_Angeles.csv')
la_dataset.head(10)
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
      <th>HSE_ID</th>
      <th>PIN</th>
      <th>PIND</th>
      <th>HSE_NBR</th>
      <th>HSE_FRAC_NBR</th>
      <th>HSE_DIR_CD</th>
      <th>STR_NM</th>
      <th>STR_SFX_CD</th>
      <th>STR_SFX_DIR_CD</th>
      <th>UNIT_RANGE</th>
      <th>ZIP_CD</th>
      <th>LAT</th>
      <th>LON</th>
      <th>X_COORD_NBR</th>
      <th>Y_COORD_NBR</th>
      <th>ASGN_STTS_IND</th>
      <th>ENG_DIST</th>
      <th>CNCL_DIST</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>772643</td>
      <td>150A187   366</td>
      <td>150A187-366</td>
      <td>1769</td>
      <td>NaN</td>
      <td>N</td>
      <td>IVAR</td>
      <td>AVE</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>90028</td>
      <td>34.10369</td>
      <td>-118.32831</td>
      <td>6.462278e+06</td>
      <td>1.860278e+06</td>
      <td>U</td>
      <td>C</td>
      <td>13.0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1044886</td>
      <td>111B141   217</td>
      <td>111B141-217</td>
      <td>260</td>
      <td>NaN</td>
      <td>S</td>
      <td>6TH</td>
      <td>AVE</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>90291</td>
      <td>33.99944</td>
      <td>-118.47219</td>
      <td>6.418545e+06</td>
      <td>1.822515e+06</td>
      <td>A</td>
      <td>W</td>
      <td>11.0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>1042028</td>
      <td>096B169   869</td>
      <td>096B169-869</td>
      <td>8802</td>
      <td>NaN</td>
      <td>S</td>
      <td>BELFORD</td>
      <td>AVE</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>90045</td>
      <td>33.95675</td>
      <td>-118.38381</td>
      <td>6.445274e+06</td>
      <td>1.806866e+06</td>
      <td>A</td>
      <td>W</td>
      <td>11.0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>1040000</td>
      <td>147B197   608</td>
      <td>147B197-608</td>
      <td>4610</td>
      <td>NaN</td>
      <td>W</td>
      <td>MAUBERT</td>
      <td>AVE</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>90027</td>
      <td>34.09890</td>
      <td>-118.29008</td>
      <td>6.473862e+06</td>
      <td>1.858509e+06</td>
      <td>A</td>
      <td>C</td>
      <td>13.0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>1042029</td>
      <td>096B169   869</td>
      <td>096B169-869</td>
      <td>8802</td>
      <td>1/2</td>
      <td>S</td>
      <td>BELFORD</td>
      <td>AVE</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>90045</td>
      <td>33.95675</td>
      <td>-118.38381</td>
      <td>6.445274e+06</td>
      <td>1.806866e+06</td>
      <td>A</td>
      <td>W</td>
      <td>11.0</td>
    </tr>
    <tr>
      <th>5</th>
      <td>1039775</td>
      <td>192B101   758</td>
      <td>192B101-758</td>
      <td>8320</td>
      <td>NaN</td>
      <td>N</td>
      <td>CHELSEA</td>
      <td>LANE</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>91304</td>
      <td>34.22081</td>
      <td>-118.60988</td>
      <td>6.377300e+06</td>
      <td>1.903297e+06</td>
      <td>A</td>
      <td>V</td>
      <td>12.0</td>
    </tr>
    <tr>
      <th>6</th>
      <td>1045065</td>
      <td>151-5A189 353</td>
      <td>151-5A189-353</td>
      <td>2031</td>
      <td>NaN</td>
      <td>N</td>
      <td>CHEREMOYA</td>
      <td>AVE</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>90068</td>
      <td>34.10839</td>
      <td>-118.32073</td>
      <td>6.464579e+06</td>
      <td>1.861981e+06</td>
      <td>L</td>
      <td>C</td>
      <td>4.0</td>
    </tr>
    <tr>
      <th>7</th>
      <td>1066012</td>
      <td>129B169  1343</td>
      <td>129B169-1343</td>
      <td>9039</td>
      <td>NaN</td>
      <td>W</td>
      <td>CRESTA</td>
      <td>DR</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>90035</td>
      <td>34.04616</td>
      <td>-118.38767</td>
      <td>6.444227e+06</td>
      <td>1.839407e+06</td>
      <td>A</td>
      <td>W</td>
      <td>5.0</td>
    </tr>
    <tr>
      <th>8</th>
      <td>1040871</td>
      <td>108B213   259</td>
      <td>108B213-259</td>
      <td>5500</td>
      <td>NaN</td>
      <td>S</td>
      <td>FORTUNA</td>
      <td>ST</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>90011</td>
      <td>33.99288</td>
      <td>-118.24543</td>
      <td>6.487270e+06</td>
      <td>1.819882e+06</td>
      <td>A</td>
      <td>C</td>
      <td>9.0</td>
    </tr>
    <tr>
      <th>9</th>
      <td>1040385</td>
      <td>174B121   796</td>
      <td>174B121-796</td>
      <td>5821</td>
      <td>NaN</td>
      <td>N</td>
      <td>YOLANDA</td>
      <td>AVE</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>91356</td>
      <td>34.17615</td>
      <td>-118.54091</td>
      <td>6.398062e+06</td>
      <td>1.886926e+06</td>
      <td>A</td>
      <td>V</td>
      <td>3.0</td>
    </tr>
  </tbody>
</table>
</div>




```python
la_dataset.shape
```




    (1004342, 18)




```python
la_dataset.drop(['HSE_ID','PIN','PIND','HSE_NBR','HSE_FRAC_NBR','HSE_DIR_CD','STR_SFX_DIR_CD','UNIT_RANGE',
                 'X_COORD_NBR','Y_COORD_NBR','ASGN_STTS_IND','ENG_DIST','CNCL_DIST'], axis=1, inplace=True)
la_dataset.head(10)
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
      <th>STR_NM</th>
      <th>STR_SFX_CD</th>
      <th>ZIP_CD</th>
      <th>LAT</th>
      <th>LON</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>IVAR</td>
      <td>AVE</td>
      <td>90028</td>
      <td>34.10369</td>
      <td>-118.32831</td>
    </tr>
    <tr>
      <th>1</th>
      <td>6TH</td>
      <td>AVE</td>
      <td>90291</td>
      <td>33.99944</td>
      <td>-118.47219</td>
    </tr>
    <tr>
      <th>2</th>
      <td>BELFORD</td>
      <td>AVE</td>
      <td>90045</td>
      <td>33.95675</td>
      <td>-118.38381</td>
    </tr>
    <tr>
      <th>3</th>
      <td>MAUBERT</td>
      <td>AVE</td>
      <td>90027</td>
      <td>34.09890</td>
      <td>-118.29008</td>
    </tr>
    <tr>
      <th>4</th>
      <td>BELFORD</td>
      <td>AVE</td>
      <td>90045</td>
      <td>33.95675</td>
      <td>-118.38381</td>
    </tr>
    <tr>
      <th>5</th>
      <td>CHELSEA</td>
      <td>LANE</td>
      <td>91304</td>
      <td>34.22081</td>
      <td>-118.60988</td>
    </tr>
    <tr>
      <th>6</th>
      <td>CHEREMOYA</td>
      <td>AVE</td>
      <td>90068</td>
      <td>34.10839</td>
      <td>-118.32073</td>
    </tr>
    <tr>
      <th>7</th>
      <td>CRESTA</td>
      <td>DR</td>
      <td>90035</td>
      <td>34.04616</td>
      <td>-118.38767</td>
    </tr>
    <tr>
      <th>8</th>
      <td>FORTUNA</td>
      <td>ST</td>
      <td>90011</td>
      <td>33.99288</td>
      <td>-118.24543</td>
    </tr>
    <tr>
      <th>9</th>
      <td>YOLANDA</td>
      <td>AVE</td>
      <td>91356</td>
      <td>34.17615</td>
      <td>-118.54091</td>
    </tr>
  </tbody>
</table>
</div>



Find the most frequent zip codes and delete some of them **(the ones that don't start with 900)** to further trim dataset


```python
la_dataset.ZIP_CD.value_counts().head(15)
```




    90011    24839
    90026    21166
    91331    19241
    90003    19089
    90731    19086
    90019    18853
    91342    18621
    90065    17765
    90042    17248
    90044    16824
    90037    16092
    91344    15881
    91335    15690
    90032    15486
    90016    15353
    Name: ZIP_CD, dtype: int64




```python
la_dataset = la_dataset[la_dataset['ZIP_CD']<90270]
```


```python
la_dataset.shape
```




    (576727, 5)




```python
la_dataset.to_csv('Addresses_in_the_City_of_LA.csv', index=False)
```
