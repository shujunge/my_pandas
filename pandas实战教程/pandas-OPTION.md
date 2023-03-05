# pandas实战教程-Options and settings

## 背景介绍
* 作为数据处理和分析的利器,pandas库提供需要函数可用于处理各式各样的数据。

## pandas库安装


```python
!pip install pandas==1.3.3 -i  https://pypi.tuna.tsinghua.edu.cn/simple # 使用清华源安装指定的版本
!pip install numpy==1.18.1 -i  https://pypi.tuna.tsinghua.edu.cn/simple # 使用清华源安装指定的版本
```

    Looking in indexes: https://pypi.tuna.tsinghua.edu.cn/simple
    Requirement already satisfied: pandas==1.3.3 in /home/xty/anaconda3/lib/python3.7/site-packages (1.3.3)
    Requirement already satisfied: python-dateutil>=2.7.3 in /home/xty/anaconda3/lib/python3.7/site-packages (from pandas==1.3.3) (2.8.1)
    Requirement already satisfied: pytz>=2017.3 in /home/xty/anaconda3/lib/python3.7/site-packages (from pandas==1.3.3) (2019.3)
    Requirement already satisfied: numpy>=1.17.3 in /home/xty/anaconda3/lib/python3.7/site-packages (from pandas==1.3.3) (1.18.1)
    Requirement already satisfied: six>=1.5 in /home/xty/anaconda3/lib/python3.7/site-packages (from python-dateutil>=2.7.3->pandas==1.3.3) (1.14.0)
    Looking in indexes: https://pypi.tuna.tsinghua.edu.cn/simple
    Requirement already satisfied: numpy==1.18.1 in /home/xty/anaconda3/lib/python3.7/site-packages (1.18.1)



```python
!python -V
```

    Python 3.7.6



```python
import pandas as pd
print("pandas版本:",pd.__version__)
import numpy as np
print("numpy版本:",np.__version__)
```

    pandas版本: 1.3.3
    numpy版本: 1.18.1


## 常用的options选项


```python
print("max_rows:", pd.options.display.max_rows)
pd.options.display.max_rows = 999
print("max_rows:", pd.options.display.max_rows)
# 等价于

# 设置显示最大行数
pd.set_option("display.max_rows", 101)
print("max_rows:", pd.get_option("display.max_rows"))
# 设置显示最大列
print("max_columns:",pd.get_option("display.max_columns"))


```

    max_rows: 60
    max_rows: 999
    max_rows: 101
    max_columns: 20


### 设置显示精度


```python
df = pd.DataFrame(np.random.randn(7, 2))
df
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
      <th>0</th>
      <th>1</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>-0.125761</td>
      <td>-0.225941</td>
    </tr>
    <tr>
      <th>1</th>
      <td>0.568543</td>
      <td>0.955912</td>
    </tr>
    <tr>
      <th>2</th>
      <td>-0.759580</td>
      <td>0.830669</td>
    </tr>
    <tr>
      <th>3</th>
      <td>0.481227</td>
      <td>-1.031987</td>
    </tr>
    <tr>
      <th>4</th>
      <td>0.555452</td>
      <td>0.483941</td>
    </tr>
    <tr>
      <th>5</th>
      <td>0.368279</td>
      <td>2.665601</td>
    </tr>
    <tr>
      <th>6</th>
      <td>3.220282</td>
      <td>0.125365</td>
    </tr>
  </tbody>
</table>
</div>




```python
pd.set_option("precision", 4)
df
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
      <th>0</th>
      <th>1</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>-0.1258</td>
      <td>-0.2259</td>
    </tr>
    <tr>
      <th>1</th>
      <td>0.5685</td>
      <td>0.9559</td>
    </tr>
    <tr>
      <th>2</th>
      <td>-0.7596</td>
      <td>0.8307</td>
    </tr>
    <tr>
      <th>3</th>
      <td>0.4812</td>
      <td>-1.0320</td>
    </tr>
    <tr>
      <th>4</th>
      <td>0.5555</td>
      <td>0.4839</td>
    </tr>
    <tr>
      <th>5</th>
      <td>0.3683</td>
      <td>2.6656</td>
    </tr>
    <tr>
      <th>6</th>
      <td>3.2203</td>
      <td>0.1254</td>
    </tr>
  </tbody>
</table>
</div>



### 设置最大行宽


```python
df = pd.DataFrame(
    np.array(
        [
            ["foo", "bar", "bim", "uncomfortably long string"],
            ["horse", "cow", "banana", "apple"],
        ]
    )
)
df
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
      <th>0</th>
      <th>1</th>
      <th>2</th>
      <th>3</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>foo</td>
      <td>bar</td>
      <td>bim</td>
      <td>uncomfortably long string</td>
    </tr>
    <tr>
      <th>1</th>
      <td>horse</td>
      <td>cow</td>
      <td>banana</td>
      <td>apple</td>
    </tr>
  </tbody>
</table>
</div>




```python
pd.set_option("max_colwidth", 8)
df
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
      <th>0</th>
      <th>1</th>
      <th>2</th>
      <th>3</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>foo</td>
      <td>bar</td>
      <td>bim</td>
      <td>unco...</td>
    </tr>
    <tr>
      <th>1</th>
      <td>horse</td>
      <td>cow</td>
      <td>banana</td>
      <td>apple</td>
    </tr>
  </tbody>
</table>
</div>




```python
pd.reset_option("max_colwidth")
```

### 对表头格式进行设置


```python
df = pd.DataFrame(
    np.array([np.random.randn(6), np.random.randint(1, 9, 6) * 0.1, np.zeros(6)]).T,
    columns=["A", "S", "C"],
    dtype="float",
)

pd.set_option("colheader_justify", "right")
df
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
      <th>A</th>
      <th>S</th>
      <th>C</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>0.3109</td>
      <td>0.1</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>-0.6989</td>
      <td>0.7</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>-0.4568</td>
      <td>0.5</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>-0.7978</td>
      <td>0.2</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>1.0188</td>
      <td>0.1</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>5</th>
      <td>0.9145</td>
      <td>0.2</td>
      <td>0.0</td>
    </tr>
  </tbody>
</table>
</div>




```python
pd.set_option("colheader_justify", "left")
df
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
    <tr style="text-align: left;">
      <th></th>
      <th>A</th>
      <th>S</th>
      <th>C</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>0.3109</td>
      <td>0.1</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>-0.6989</td>
      <td>0.7</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>-0.4568</td>
      <td>0.5</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>-0.7978</td>
      <td>0.2</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>1.0188</td>
      <td>0.1</td>
      <td>0.0</td>
    </tr>
    <tr>
      <th>5</th>
      <td>0.9145</td>
      <td>0.2</td>
      <td>0.0</td>
    </tr>
  </tbody>
</table>
</div>



## 其他格式[<sup>1</sup>](#refer-anchor)


```python
pd.options.display.latex.repr = True # 完整显示pandas的表格数据
```

## 参考文献
- [1] [pandas官方教程](https://pandas.pydata.org/pandas-docs/version/1.3.3/user_guide/options.html)
