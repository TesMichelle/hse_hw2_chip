### Google collab


https://colab.research.google.com/drive/1VqetexCIkeLH0YkyGspld6YWgILMpuHa?usp=sharing

### fastqc

ENCFF000BCE - replicate 1
![Alt text](/imgs/BCE.png?raw=true "Optional Title")

ENCFF000BCI - replicate 2
![Alt text](/imgs/BCI.png?raw=true "Optional Title")

ENCFF000BAU - control
![Alt text](/imgs/BAU.png?raw=true "Optional Title")

Видим хорошие показатели качества прочтений для replicate 1 и control. Для
replicate 2 наблюдается очень сильный разброс в качестве прочтений, поэтому для
replicate 2 была проведена обработка с помощью `trimmomatic`.

![Alt text](/imgs/BCI_filtered.png?raw=true "Optional Title")

После фильтрации прочтений качество заметно улучшилось.

### Выравнивание

|  Образец    | Всего ридов | Уникально выр.  | НЕ-уникально выр. | Не выравнилось |
|:-----------:|:------------|:----------------|:------------------|:-------------- |
| ENCFF000BCE | 23311976    | 1012890 (4.34%) | 2897175 (12.43%)  | 19401911       |
| ENCFF000BCI | 39589029    | 1635458 (4.13%) | 5590864 (14.12%)  | 32362707       |
| ENCFF000BAU | 84569628    | 3493144 (4.13%) | 9185116 (10.86%)  | 71891368       |

Так как выравнивание производилось всего на одну хромосому (14-ю), то выравнились не все прочтения
из образцов, а лишь те что могли попасть на данную хромосому. Доля 14-й хромосомы составляет около 3.5% всего генома человека. Процент уникальных выравниваний соответствует этому числу.  

### Диаграммы Венна

ENCFF000BCE - replicate 1
![Alt text](/imgs/BCE_.png?raw=true "Optional Title")
![Alt text](/imgs/_BCE.png?raw=true "Optional Title")

ENCFF000BCI - replicate 2
![Alt text](/imgs/BCI_.png?raw=true "Optional Title")
![Alt text](/imgs/_BCI.png?raw=true "Optional Title")

Найденных пиков меньше чем в фале для сравнения, так как мы производили поиск только на одной хромосоме.
Наблюдаем, что в пересечении пиков заметно меньше, чем в файле для сравнения.
Более того при поиске пересечений между полученными пиками и файлом для сравнения
мы получаем число большее чем при поиске пересечений между файлом для сравнения и полученными пиками.
Это говорит о том, что в среднем на один попавший в пересечение пик из файла сравнения приходятся несколько полученных пиков. Это может происходить из-за особенностей выбора параметров при поиске пиков, например, пороговых значений.

### Bonus
![Alt text](/imgs/result_1.png?raw=true "Optional Title")
![Alt text](/imgs/result_2.png?raw=true "Optional Title")

Из распределений мы наблюдаем отрицательную корреляцию присутствия H3K27me3 в сайте начала транскрипции. Можно предположить, что данная гистонная модификация негативно влияет на экспрессию генов, рядом с которыми она находится (это подтверждается в [википедии](https://en.wikipedia.org/wiki/H3K27me3 "Необязательная подсказка")).
