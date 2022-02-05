```python
import pandas_datareader as pdr
```


```python
fed_data1=pdr.get_data_fred(['UNRATE', 'FEDFUNDS', 'INDPRO'])
```


```python
fed_data1.describe()
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
      <th>UNRATE</th>
      <th>FEDFUNDS</th>
      <th>INDPRO</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>count</th>
      <td>59.000000</td>
      <td>59.000000</td>
      <td>58.000000</td>
    </tr>
    <tr>
      <th>mean</th>
      <td>5.081356</td>
      <td>1.096949</td>
      <td>100.140750</td>
    </tr>
    <tr>
      <th>std</th>
      <td>2.306996</td>
      <td>0.880821</td>
      <td>3.875368</td>
    </tr>
    <tr>
      <th>min</th>
      <td>3.500000</td>
      <td>0.050000</td>
      <td>84.201800</td>
    </tr>
    <tr>
      <th>25%</th>
      <td>3.800000</td>
      <td>0.090000</td>
      <td>99.283100</td>
    </tr>
    <tr>
      <th>50%</th>
      <td>4.200000</td>
      <td>1.150000</td>
      <td>101.258600</td>
    </tr>
    <tr>
      <th>75%</th>
      <td>5.600000</td>
      <td>1.870000</td>
      <td>102.366575</td>
    </tr>
    <tr>
      <th>max</th>
      <td>14.700000</td>
      <td>2.420000</td>
      <td>104.165900</td>
    </tr>
  </tbody>
</table>
</div>




```python
import statsmodels.formula.api as smf
```


```python
reg1='INDPRO~UNRATE+FEDFUNDS'
```


```python
reg1output=smf.ols(reg1,fed_data1).fit()
```


```python
print(reg1output.summary())
```

                                OLS Regression Results                            
    ==============================================================================
    Dep. Variable:                 INDPRO   R-squared:                       0.890
    Model:                            OLS   Adj. R-squared:                  0.886
    Method:                 Least Squares   F-statistic:                     221.8
    Date:                Thu, 13 Jan 2022   Prob (F-statistic):           4.68e-27
    Time:                        12:27:35   Log-Likelihood:                -96.430
    No. Observations:                  58   AIC:                             198.9
    Df Residuals:                      55   BIC:                             205.0
    Df Model:                           2                                         
    Covariance Type:            nonrobust                                         
    ==============================================================================
                     coef    std err          t      P>|t|      [0.025      0.975]
    ------------------------------------------------------------------------------
    Intercept    107.3579      0.739    145.184      0.000     105.876     108.840
    UNRATE        -1.4887      0.098    -15.225      0.000      -1.685      -1.293
    FEDFUNDS       0.3389      0.259      1.311      0.195      -0.179       0.857
    ==============================================================================
    Omnibus:                        0.711   Durbin-Watson:                   0.649
    Prob(Omnibus):                  0.701   Jarque-Bera (JB):                0.819
    Skew:                          -0.225   Prob(JB):                        0.664
    Kurtosis:                       2.631   Cond. No.                         25.8
    ==============================================================================
    
    Notes:
    [1] Standard Errors assume that the covariance matrix of the errors is correctly specified.
    


```python

```
