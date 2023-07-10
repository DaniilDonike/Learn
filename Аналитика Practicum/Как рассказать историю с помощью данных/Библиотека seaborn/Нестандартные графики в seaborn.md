[[Почему не хватает matplotlib]]

Вот графики, которые действительно сложно повторить без seaborn.

### violinplot() (англ. «график-скрипка»)

Как и `boxplot()`, этот график характеризует форму распределения. Необычный внешний вид получается из-за сложения двух графиков плотности распределения. Основное преимущество перед `boxplot()` — возможность изучить распределение и установить его тип.

Именно так `violinplot()` соответствует `boxplot()`:

![image](https://pictures.s3.yandex.net/resources/12_1570438507.jpg)

В seaborn такой график строят методом `violinplot()`:

Скопировать кодPYTHON

```
sns.violinplot(x='kind', y='pulse', data=sport, palette='rainbow') 
```

![image](https://pictures.s3.yandex.net/resources/Untitled-dafdb3de-4276-4b87-8506-4f78d290ee40_1570327239.png)

### stripplot() (англ. «график-полоска»)

`stripplot()` — ещё один способ отображения категориальных данных. Для каждой категории получаем диаграмму рассеяния. График рекомендуют строить в сочетании с другими, например с `violinplot()`.

В seaborn такой график строят методом `stripplot()`:

Скопировать кодPYTHON

```
sns.stripplot(x='diet', y='pulse', data=sport) 
```

![image](https://pictures.s3.yandex.net/resources/Untitled-c4347238-2b0c-4646-9382-d527f60e302b_1570327244.png)