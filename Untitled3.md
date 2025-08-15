```python
import pandas as pd
from bs4 import BeautifulSoup
import requests
import yfinance as yf
```


```python
GameStock = yf.Ticker("GME")
```


```python
gme_data = pd.DataFrame()

```


```python
gme_data = GameStock.history(period = 'max')
```


```python
gme_data.reset_index(inplace = True)
```


```python
gme_data.head()
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
      <th>Date</th>
      <th>Open</th>
      <th>High</th>
      <th>Low</th>
      <th>Close</th>
      <th>Volume</th>
      <th>Dividends</th>
      <th>Stock Splits</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>2002-02-13 00:00:00-05:00</td>
      <td>1.620129</td>
      <td>1.693350</td>
      <td>1.603296</td>
      <td>1.691667</td>
      <td>76216000</td>
      <td>0.0</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2002-02-14 00:00:00-05:00</td>
      <td>1.712707</td>
      <td>1.716074</td>
      <td>1.670626</td>
      <td>1.683250</td>
      <td>11021600</td>
      <td>0.0</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2002-02-15 00:00:00-05:00</td>
      <td>1.683250</td>
      <td>1.687458</td>
      <td>1.658002</td>
      <td>1.674834</td>
      <td>8389600</td>
      <td>0.0</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>2002-02-19 00:00:00-05:00</td>
      <td>1.666418</td>
      <td>1.666418</td>
      <td>1.578047</td>
      <td>1.607504</td>
      <td>7410400</td>
      <td>0.0</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>2002-02-20 00:00:00-05:00</td>
      <td>1.615921</td>
      <td>1.662210</td>
      <td>1.603296</td>
      <td>1.662210</td>
      <td>6892800</td>
      <td>0.0</td>
      <td>0.0</td>
    </tr>
  </tbody>
</table>
</div>




```python
import pandas as pd
from bs4 import BeautifulSoup
import requests
```


```python
url = "https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMDeveloperSkillsNetwork-PY0220EN-SkillsNetwork/labs/project/stock.html"
```


```python
html_data_2 = requests.get(url).text
```


```python
soup = BeautifulSoup(html_data_2,"html.parser")
```


```python
gme_revenue = pd.DataFrame(columns = ["Date","Revenue"])
```


```python
for row in soup.find("tbody").find_all('tr'):
    date = col[0].text
    Revenue = col[1].text
gme_revenue= pd.concat([gme_revenue,pd.DataFrame({"Date":[date], "Revenue":[Revenue]})], ignore_index=True) 
gme_revenue["Revenue"] = gme_revenue['Revenue'].str.replace(',|\$',"",regex=True)
gme_revenue.dropna(inplace=True)

gme_revenue = gme_revenue[gme_revenue['Revenue'] != ""]
```


```python
gme_revenue.tail()
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
      <th>Date</th>
      <th>Revenue</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Sep 01, 2015</td>
      <td>109.35</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Sep 01, 2015</td>
      <td>109.35</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Sep 01, 2015</td>
      <td>109.35</td>
    </tr>
  </tbody>
</table>
</div>




```python
graph = make_graph(gme_data , gme_revenue ,'Game Stop")
```


      Cell In[74], line 1
        graph = make.graph(gme_data , gme_revenue ,'Game Stop")
                                                   ^
    SyntaxError: unterminated string literal (detected at line 1)
    



```python

```
