---
title: pyecharts数据可视化
category: 关于开发的那些事
updatedAt: 2024-04-09T12:19:38.089Z
createdAt: 2024-04-09T06:28:52.179Z
---

# pyecharts数据可视化
[如果需要jupyter版的请访问这个下载](http://byte2023.icu:8080/pyecharts.zip)
### 生成柱状图
```python
#生成柱状图
from pyecharts.charts import Bar
from pyecharts.faker import Faker
#假数据
bar = (Bar()
       .add_xaxis(Faker.choose())   #假数据
       .add_yaxis('test',Faker.values())  #假数据
       )
bar.render() #渲染

```    

<br>
<br>




<!-- more -->
![](https://byte2023.icu/static/img/571a3cd122e84cf0eabf7c86987bc69c.bar.webp)

<br>
<br>
<br>


### 生成饼状图
```python
#生成饼状图
from pyecharts.charts import Pie
from pyecharts.faker import Faker
x = Faker.choose()  #假数据
y = Faker.values()  #假数据
pie = (Pie()
       .add('',list(zip(x,y)))
       )
pie.render()
```
<br>
<br>


![](https://byte2023.icu/static/img/0587a643890ad76d86bd9f7703dbf231.pie.webp)

<br>
<br>
<br>


### 生成折线图
```python
from pyecharts.charts import Line
from pyecharts.faker import Faker


line = (Line()
        .add_xaxis(Faker.choose())
        .add_yaxis('',Faker.values())
        )
line.render_notebook()

```
<br>
<br>


![](https://byte2023.icu/static/img/f8e7a47b1787aa517f115dbbccac2af4.line.webp)

<br>
<br>
<br>



###  生成散点图

```python
from pyecharts.charts import Scatter
from pyecharts.faker import Faker
scatter = (Scatter()
           .add_xaxis(Faker.choose())
           .add_yaxis('123',Faker.values())
           )
scatter.render_notebook()
```


<br>
<br>


![](https://byte2023.icu/static/img/854ad7cc7d169f7662653e3421ef81a4.scatter.webp)

<br>
<br>
<br>


### 位置图

```python
from pyecharts.charts import Geo
import random
province = [
    '广东',
    '湖北',
    '湖南',
    '四川',
    '重庆',
    '黑龙江',
    '浙江',
    '山西',
    '河北',
    '安徽',
    '河南',
    '山东',
    '西藏']
data = [(i, random.randint(50, 150)) for i in province]

geo = (
    Geo()
    .add_schema(maptype="china") #maptype是地图，可以选很多
    .add("", data)
)
geo.render_notebook()

```


<br>
<br>


![](https://byte2023.icu/static/img/1f2e983fd2f23d4c088d1dbaec3a86cb.geo.webp)

<br>
<br>
<br>


### 仪表盘

```python
from pyecharts.charts import Gauge
from pyecharts.faker import Faker

gauge = (
            Gauge()
            .add("", [('转化率', Faker.values())])
            .add('',[('起飞率',Faker.values())])
            
    )
gauge.render()
```


<br>
<br>

![](https://byte2023.icu/static/img/7bc6e3bddecba9d7da909911cc2cdd85.gauge.webp)