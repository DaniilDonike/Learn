[[Интерактивные графики]]

Средствами plotly можно построить много видов графиков: от простых линейных до сложных с географическими данными. Полный перечень графиков можно найти в [документации](https://plot.ly/python/#fundamentals) библиотеки. Пока построим знакомые линейный график и гистограмму.

Если график создают на основе данных из датафрейма, обращаются к `plotly express` — API plotly для быстрого доступа к основным методам библиотеки. Так её импортируют:

```python
import plotly.express as px 
```

Как у seaborn, в plotly есть встроенные наборы данных. Построим график по данным о выборах:

```python
data = px.data.election()
print(data.head()) 
```

```
                district  Coderre  Bergeron  Joly  total    winner     result
0     101-Bois-de-Liesse     2481      1829  3024   7334      Joly  plurality
1  102-Cap-Saint-Jacques     2525      1163  2675   6363      Joly  plurality
2   11-Sault-au-Récollet     3348      2770  2532   8650   Coderre  plurality
3           111-Mile-End     1734      4782  2514   9030  Bergeron   majority
4         112-DeLorimier     1770      5933  3044  10747  Bergeron   majority 
```

В таблице есть район голосования, количество голосов за каждого из трёх кандидатов, общее число голосов, информация о победителе и типе победы (англ. plurality — относительное большинство, majority — абсолютное). Построим графики и найдём зависимости.

## Линейный график

Отличительная особенность интерактивного линейного графика — возможность просмотреть значения прямой при наведении на неё. Чтобы построить линейный график, вызывают метод `line()` с параметрами:

- `data` — данные;
- `X` — данные по оси X;
- `Y` — данные по оси Y;
- `title` — заголовок графика.

```python
import plotly.express as px

data = px.data.election()
fig = px.line(data, x='district', y='Coderre', title='Результаты Coderre по районам')
fig.show() 
```

![image](https://pictures.s3.yandex.net/resources/newplot-c8287033-9e74-4a31-857c-6ae6c24ca92c_1570328307.png)

Подписи по оси X выглядят не очень аккуратно. Повернём их методом `update_xaxes()`. Передадим параметру `tickangle` угол поворота в градусах:

Скопировать кодPYTHON

```
fig = px.line(data, x='district', y='Coderre', title='Результаты Coderre по районам')
fig.update_xaxes(tickangle=45) # повернём подписи по оси X на 45 градусов
fig.show() 
```

![image](https://pictures.s3.yandex.net/resources/newplot_1-835a0ef3-9768-4cef-821e-ea9b243fa6bc_1570328297.png)

### Столбчатая диаграмма

Столбчатую диаграмму строят методом `bar()` с теми же параметрами, как и у линейного графика:

Скопировать кодPYTHON

```
import plotly.express as px
data = px.data.election()
fig = px.bar(data, x='district', y='Coderre', title='Результаты Coderre по районам')
fig.update_xaxes(tickangle=45)
fig.show() 
```

![image](https://pictures.s3.yandex.net/resources/newplot_3-ce89c46f-564b-4337-b83d-359b3994987a_1570328301.png)

Добавим параметр `color` и разделим данные по типу победы:

Скопировать кодPYTHON

```
fig = px.bar(data, x='district', y='Coderre', color='result', title='Результаты Coderre по районам')
fig.update_xaxes(tickangle=45)
fig.show() 
```

![image](https://pictures.s3.yandex.net/resources/newplot_4-ab8454c8-135d-4288-b28d-9cbdaea4720d_1570328304.png)