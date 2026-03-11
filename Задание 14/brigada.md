# Решение задачи 14 команды brigada
## Состав команды:
1. Ваулин Никита
2. Громов Иван
3. Кузнецов Егор

## Вариант 7: 

Решить задачу о рюкзаке с применением генетического алгоритма, с учетом следующих требований:

* Придумать условия задачи с количеством предметов не менее 8.
* Численность популяции не менее 6 особей, в скрещивании участвует 1/3 популяции.
* Для скрещивания выбираются сильнейшие особи, скрещивание – двухточечное.
* До выполнения алгоритма сформулировать стратегию применения оператора мутации и правила формирования нового поколения на основе новых особей и особей из предыдущего поколения
* Сформировать не менее 3 поколений, не считая первоначального.

# Решение
### Параметры задачи:

#### Вместимость рюкзака: V(max) = 24

#### Количество предметов: 8 (A, B, C, D, E, F, G, H)

<table border="1" cellpadding="5" cellspacing="0">
<tr>
<th>Предмет</th>
<th>A</th>
<th>B</th>
<th>C</th>
<th>D</th>
<th>E</th>
<th>F</th>
<th>G</th>
<th>H</th>
</tr>
<tr>
<td><strong>Стоимость</strong></td>
<td>7</td>
<td>9</td>
<td>11</td>
<td>8</td>
<td>10</td>
<td>12</td>
<td>6</td>
<td>4</td>
</tr>
<tr>
<td><strong>Вес</strong></td>
<td>2</td>
<td>3</td>
<td>5</td>
<td>4</td>
<td>6</td>
<td>8</td>
<td>4</td>
<td>2</td>
</tr>
</table>

# Правила генетического алгоритма

Особь считается приспособленной, если вес предметов у особи не превышает вместимости рюкзака

Особь считается более приспособленной, если при одинаковой стоимости содержимого рюкзака, вес предметов меньше

### Правило мутации:
* Вероятность мутации: 20%
* Генерируется случайное число от 1 до 10
* Если число 1 или 2 → инвертируется случайная позиция

### Правило отбора для скрещивания:
* Сортировка популяции по убыванию приспособленности F(X)
* Выбираются 2 сильнейшие особи (элита)
* Применяется двухточечное скрещивание

### Правило формирования нового поколения:
* Сохраняются 2 самые приспособленные особи (элита)
* Добавляем потомков, если потомок или потомки неприспособлены, то переходим к следующему шагу
* Случайным образом разбиваем оставшихся особей на две группы и переносим сильнейших из этих групп в новое поколение
* Если новое поколение ещё не сформировано, то добираем особей из прошлого по принципу самого приспособленного из оставшихся

# Работа алгоритма

## Сгенерируем первое поколение (Начальное)
<table border="1" cellpadding="5" cellspacing="0">
<th>Особь</th>
<th>A</th>
<th>B</th>
<th>C</th>
<th>D</th>
<th>E</th>
<th>F</th>
<th>G</th>
<th>H</th>
<th>V(X)</th>
<th>F(X)</th>
</tr>
<td><strong>A1</strong></td>
<td>1</td>
<td>0</td>
<td>0</td>
<td>0</td>
<td>1</td>
<td>1</td>
<td>1</td>
<td>1</td>
<td>22</td>
<td>39</td>
</tr>
<td><strong>A2</strong></td>
<td>1</td>
<td>0</td>
<td>1</td>
<td>1</td>
<td>0</td>
<td>0</td>
<td>0</td>
<td>1</td>
<td>13</td>
<td>30</td>
</tr>
<td><strong>A3</strong></td>
<td>0</td>
<td>1</td>
<td>1</td>
<td>0</td>
<td>1</td>
<td>0</td>
<td>0</td>
<td>0</td>
<td>14</td>
<td>30</td>
</tr>
<td><strong>A4</strong></td>
<td>0</td>
<td>1</td>
<td>0</td>
<td>0</td>
<td>1</td>
<td>0</td>
<td>1</td>
<td>0</td>
<td>13</td>
<td>25</td>
</tr>
<td><strong>A5</strong></td>
<td>1</td>
<td>0</td>
<td>1</td>
<td>0</td>
<td>1</td>
<td>1</td>
<td>0</td>
<td>1</td>
<td>23</td>
<td style="background-color: #73ee5498;"><strong >44</strong></td>
</tr>
<td><strong>A6</strong></td>
<td>0</td>
<td>1</td>
<td>1</td>
<td>1</td>
<td>0</td>
<td>1</td>
<td>0</td>
<td>0</td>
<td>20</td>
<td style="background-color: #73ee5498;"><strong>40</strong></td>
</tr>
</table>

Все особи приспособлены

Отбираем две самые приспособленные особи для двуточечного скрещивания:

A6 и A5 самые сильные особи (элита)

Выбирем две точки для скрещивания

<table border="1" cellpadding="5" cellspacing="0">
<th>Особь</th>
<th>A</th>
<th>B</th>
<th>C</th>
<th>D</th>
<th>E</th>
<th>F</th>
<th>G</th>
<th>H</th>
<th>V(X)</th>
<th>F(X)</th>
</tr>
<td><strong>A5</strong></td>
<td>1</td>
<td>0</td>
<td style="background-color: #eedf5498;">1</td>
<td style="background-color: #eedf5498;">0</td>
<td style="background-color: #eedf5498;">1</td>
<td>1</td>
<td>0</td>
<td>1</td>
<td>23</td>
<td><strong>44</strong></td>
</tr>
<td><strong>A6</strong></td>
<td style="background-color: #eedf5498;">0</td>
<td style="background-color: #eedf5498;">1</td>
<td>1</td>
<td>1</td>
<td>0</td>
<td style="background-color: #eedf5498;">1</td>
<td style="background-color: #eedf5498;">0</td>
<td style="background-color: #eedf5498;">0</td>
<td>20</td>
<td><strong>40</strong></td>
</tr>
<table>

B1 и B2 потомки в результате двуточечного скрещивания:

<table border="1" cellpadding="5" cellspacing="0">
    <th>Особь</th>
    <th>A</th>
    <th>B</th>
    <th>C</th>
    <th>D</th>
    <th>E</th>
    <th>F</th>
    <th>G</th>
    <th>H</th>
    <th>V(X)</th>
    <th>F(X)</th>
    <tr>
        <td><strong>B1</strong></td>
        <td>1</td>
        <td>0</td>
        <td>1</td>
        <td>1</td>
        <td>0</td>
        <td >1</td>
        <td>0</td>
        <td>1</td>
        <td>21</td>
        <td><strong>42</strong></td>
    </tr>
    <tr>
        <td><strong>B2</strong></td>
        <td style="background-color: #eedf5498;">0</td>
        <td style="background-color: #eedf5498;">1</td>
        <td style="background-color: #eedf5498;">1</td>
        <td style="background-color: #eedf5498;">0</td>
        <td style="background-color: #eedf5498;">1</td>
        <td style="background-color: #eedf5498;">1</td>
        <td style="background-color: #eedf5498;">0</td>
        <td style="background-color: #eedf5498;">0</td>
        <td>22</td>
        <td><strong>42</strong></td>
    </tr>
</table>

Генерируем мутации для потомков:
* B1 - Нет(8)
* B2 - Нет(4)

Генерируем группы для турнира из оставшихся особей (A1 A2 A3 A4):

<table border="1" cellpadding="5" cellspacing="0">
    <tr>
        <td>1 группа</td>
        <td>Победитель</td>
    </tr>
    <tr>
        <td style="text-align: center;" >A1</td>
        <td rowspan="2" style="text-align: center; vertical-align: middle;">A1</td>
    </tr>
    <tr>
        <td style="text-align: center;">A2</td>
    </tr>
    <tr>
        <td>2 группа</td>
        <td>Победитель</td>
    </tr>
    <tr>
        <td style="text-align: center;">A3</td>
        <td rowspan="2" style="text-align: center; vertical-align: middle;">A3</td>
    </tr>
    <tr>
        <td style="text-align: center;">A4</td>
    </tr>
</table>

В конечном итоге во второе поколения включаются: A5 A6 B1 B2 A1 A3

## Второе поколение

<table border="1" cellpadding="5" cellspacing="0">
<th>Особь</th>
<th>A</th>
<th>B</th>
<th>C</th>
<th>D</th>
<th>E</th>
<th>F</th>
<th>G</th>
<th>H</th>
<th>V(X)</th>
<th>F(X)</th>
    <tr>
        <td><strong>A5</strong></td>
        <td>1</td>
        <td>0</td>
        <td>1</td>
        <td>0</td>
        <td>1</td>
        <td>1</td>
        <td>0</td>
        <td>1</td>
        <td>23</td>
        <td style="background-color: #73ee5498;">44</td>
    </tr>
    <tr>
        <td><strong>A6</strong></td>
        <td>0</td>
        <td>1</td>
        <td>1</td>
        <td>1</td>
        <td>0</td>
        <td>1</td>
        <td>0</td>
        <td>0</td>
        <td>20</td>
        <td>40</td>
    </tr>
    <tr>
        <td><strong>B1</strong></td>
        <td>1</td>
        <td>0</td>
        <td>1</td>
        <td>1</td>
        <td>0</td>
        <td>1</td>
        <td>0</td>
        <td>1</td>
        <td>21</td>
        <td style="background-color: #73ee5498;">42</td>
    </tr>
    <tr>
        <td><strong>B2</strong></td>
        <td>0</td>
        <td>1</td>
        <td>1</td>
        <td>0</td>
        <td>1</td>
        <td>1</td>
        <td>0</td>
        <td>0</td>
        <td>22</td>
        <td>42</td>
    </tr>
    <tr>
        <td><strong>A1</strong></td>
        <td>1</td>
        <td>0</td>
        <td>0</td>
        <td>0</td>
        <td>1</td>
        <td>1</td>
        <td>1</td>
        <td>1</td>
        <td>22</td>
        <td>39</td>
    </tr>
    <tr>
        <td><strong>A3</strong></td>
        <td>0</td>
        <td>1</td>
        <td>1</td>
        <td>0</td>
        <td>1</td>
        <td>0</td>
        <td>0</td>
        <td>0</td>
        <td>14</td>
        <td>30</td>
    </tr>
</table>

Все особи приспособлены

Отбираем две самые приспособленные особи для двуточечного скрещивания:

A5 и B1 самые сильные особи (элита)

<table border="1" cellpadding="5" cellspacing="0">
    <tr>
        <th>Особь</th>
        <th>A</th>
        <th>B</th>
        <th>C</th>
        <th>D</th>
        <th>E</th>
        <th>F</th>
        <th>G</th>
        <th>H</th>
        <th>V(X)</th>
        <th>F(X)</th>
    </tr>
    <tr>
        <td><strong>A5</strong></td>
        <td style="background-color: #eedf5498;">1</td>
        <td style="background-color: #eedf5498;">0</td>
        <td style="background-color: #eedf5498;">1</td>
        <td>0</td>
        <td style="background-color: #eedf5498;">1</td>
        <td style="background-color: #eedf5498;">1</td>
        <td style="background-color: #eedf5498;">0</td>
        <td style="background-color: #eedf5498;">1</td>
        <td>23</td>
        <td><strong>44</strong></td>
    </tr>
    <tr>
        <td><strong>B1</strong></td>
        <td>1</td>
        <td>0</td>
        <td>1</td>
        <td style="background-color: #eedf5498;">1</td>
        <td>0</td>
        <td>1</td>
        <td>0</td>
        <td>1</td>
        <td>21</td>
        <td><strong>42</strong></td>
    </tr>
</table>

Выбирем две точки для скрещивания

С1 и С2 потомки в результате двуточечного скрещивания:

<table border="1" cellpadding="5" cellspacing="0">
    <tr>
        <th>Особь</th>
        <th>A</th>
        <th>B</th>
        <th>C</th>
        <th>D</th>
        <th>E</th>
        <th>F</th>
        <th>G</th>
        <th>H</th>
        <th>V(X)</th>
        <th>F(X)</th>
    </tr>
    <tr>
        <td><strong>C1</strong></td>
        <td>1</td>
        <td>0</td>
        <td>1</td>
        <td>0</td>
        <td>0</td>
        <td>1</td>
        <td>0</td>
        <td>1</td>
        <td>17</td>
        <td><strong>34</strong></td>
    </tr>
    <tr>
        <td><strong>C2</strong></td>
        <td style="background-color: #eedf5498;">1</td>
        <td style="background-color: #eedf5498;">0</td>
        <td style="background-color: #eedf5498;">1</td>
        <td style="background-color: #eedf5498;">1</td>
        <td style="background-color: #eedf5498;">1</td>
        <td style="background-color: #eedf5498;">1</td>
        <td style="background-color: #eedf5498;">0</td>
        <td style="background-color: #eedf5498;">1</td>
        <td>27</td>
        <td><strong>52</strong></td>
    </tr>
</table>

Потомок С2 не приспособленный

Генерируем мутации для потомков:
* С1 - Нет(7)
* С2 - Да(2) 6 ячейка

Инвертируем ячейку 6 у потомка C2

<table border="1" cellpadding="5" cellspacing="0">
    <tr>
        <th>Особь</th>
        <th>A</th>
        <th>B</th>
        <th>C</th>
        <th>D</th>
        <th>E</th>
        <th>F</th>
        <th>G</th>
        <th>H</th>
        <th>V(X)</th>
        <th>F(X)</th>
    </tr>
        <tr>
        <td><strong>C2(Мутант)</strong></td>
        <td>1</td>
        <td>0</td>
        <td>1</td>
        <td>1</td>
        <td>1</td>
        <td style="background-color: #ee54d998;">0</td>
        <td>0</td>
        <td>1</td>
        <td>19</td>
        <td><strong>40</strong></td>
    </tr>
</table>

Генерируем группы для турнира из оставшихся особей (A1 A6 B2 A3):

<table border="1" cellpadding="5" cellspacing="0">
    <tr>
        <td>1 группа</td>
        <td>Победитель</td>
    </tr>
    <tr>
        <td style="text-align: center;" >A1</td>
        <td rowspan="2" style="text-align: center; vertical-align: middle;">A6</td>
    </tr>
    <tr>
        <td style="text-align: center;">A6</td>
    </tr>
    <tr>
        <td>2 группа</td>
        <td>Победитель</td>
    </tr>
    <tr>
        <td style="text-align: center;">B2</td>
        <td rowspan="2" style="text-align: center; vertical-align: middle;">B2</td>
    </tr>
    <tr>
        <td style="text-align: center;">A3</td>
    </tr>
</table>

В конечном итоге в третье поколения включаются: A5 B2 С1 С2(Мутант) B1 A6

## Третье поколение

<table border="1" cellpadding="5" cellspacing="0">
    <tr>
<th>Особь</th>
<th>A</th>
<th>B</th>
<th>C</th>
<th>D</th>
<th>E</th>
<th>F</th>
<th>G</th>
<th>H</th>
<th>V(X)</th>
<th>F(X)</th>
    </tr>
    <tr>
        <td><strong>A5</strong></td>
        <td>1</td>
        <td>0</td>
        <td>1</td>
        <td>0</td>
        <td>1</td>
        <td>1</td>
        <td>0</td>
        <td>1</td>
        <td>23</td>
        <td style="background-color: #73ee5498;">44</td>
    </tr>
    <tr>
        <td><strong>B2</strong></td>
        <td>0</td>
        <td>1</td>
        <td>1</td>
        <td>0</td>
        <td>1</td>
        <td>1</td>
        <td>0</td>
        <td>0</td>
        <td>22</td>
        <td>42</td>
    </tr>
    <tr>
        <td><strong>C1</strong></td>
        <td>1</td>
        <td>0</td>
        <td>1</td>
        <td>0</td>
        <td>0</td>
        <td>1</td>
        <td>0</td>
        <td>1</td>
        <td>17</td>
        <td>34</td>
    </tr>
    <tr>
        <td><strong>C2(Мутант)</strong></td>
        <td>1</td>
        <td>0</td>
        <td>1</td>
        <td>1</td>
        <td>1</td>
        <td>0</td>
        <td>0</td>
        <td>1</td>
        <td>19</td>
        <td>40</td>
    </tr>
    <tr>
        <td><strong>B1</strong></td>
        <td>1</td>
        <td>0</td>
        <td>1</td>
        <td>1</td>
        <td>0</td>
        <td>1</td>
        <td>0</td>
        <td>1</td>
        <td>21</td>
        <td style="background-color: #73ee5498;" >42</td>
    </tr>
    <tr>
        <td><strong>A6</strong></td>
        <td>0</td>
        <td>1</td>
        <td>1</td>
        <td>1</td>
        <td>0</td>
        <td>1</td>
        <td>0</td>
        <td>0</td>
        <td>20</td>
        <td>40</td>
    </tr>
</table>

Все особи приспособлены

Отбираем две самые приспособленные особи для двуточечного скрещивания:

A5 и B1 самые сильные особи (элита)

<table border="1" cellpadding="5" cellspacing="0">
    <tr>
        <th>Особь</th>
        <th>A</th>
        <th>B</th>
        <th>C</th>
        <th>D</th>
        <th>E</th>
        <th>F</th>
        <th>G</th>
        <th>H</th>
        <th>V(X)</th>
        <th>F(X)</th>
    </tr>
    <tr>
        <td><strong>A5</strong></td>
        <td>1</td>
        <td>0</td>
        <td>1</td>
        <td>0</td>
        <td style="background-color: #eedf5498;">1</td>
        <td style="background-color: #eedf5498;">1</td>
        <td>0</td>
        <td>1</td>
        <td>23</td>
        <td><strong>44</strong></td>
    </tr>
    <tr>
        <td><strong>B1</strong></td>
        <td style="background-color: #eedf5498;">1</td>
        <td style="background-color: #eedf5498;">0</td>
        <td style="background-color: #eedf5498;">1</td>
        <td style="background-color: #eedf5498;">1</td>
        <td>0</td>
        <td >1</td>
        <td style="background-color: #eedf5498;">0</td>
        <td style="background-color: #eedf5498;">1</td>
        <td>21</td>
        <td><strong>42</strong></td>
    </tr>
</table>

Выбирем две точки для скрещивания

D1 и D2 потомки в результате двуточечного скрещивания:

<table border="1" cellpadding="5" cellspacing="0">
    <tr>
        <th>Особь</th>
        <th>A</th>
        <th>B</th>
        <th>C</th>
        <th>D</th>
        <th>E</th>
        <th>F</th>
        <th>G</th>
        <th>H</th>
        <th>V(X)</th>
        <th>F(X)</th>
    </tr>
    <tr>
        <td><strong>D1</strong></td>
        <td>1</td>
        <td>0</td>
        <td>1</td>
        <td>0</td>
        <td>0</td>
        <td>1</td>
        <td>0</td>
        <td>1</td>
        <td>17</td>
        <td><strong>34</strong></td>
    </tr>
    <tr>
        <td><strong>D2</strong></td>
        <td style="background-color: #eedf5498;">1</td>
        <td style="background-color: #eedf5498;">0</td>
        <td style="background-color: #eedf5498;">1</td>
        <td style="background-color: #eedf5498;">1</td>
        <td style="background-color: #eedf5498;">1</td>
        <td style="background-color: #eedf5498;">1</td>
        <td style="background-color: #eedf5498;">0</td>
        <td style="background-color: #eedf5498;">1</td>
        <td>27</td>
        <td><strong>52</strong></td>
    </tr>
</table>

Потомок D2 не приспособленный

Генерируем мутации для потомков:
* D1 - Да(2) 2 ячейка
* D2 - Да(1) 6 ячейка

Инвертируем ячейку 2 у потомка D1 и ячейку 6 у потомка D2

<table border="1" cellpadding="5" cellspacing="0">
    <tr>
        <th>Особь</th>
        <th>A</th>
        <th>B</th>
        <th>C</th>
        <th>D</th>
        <th>E</th>
        <th>F</th>
        <th>G</th>
        <th>H</th>
        <th>V(X)</th>
        <th>F(X)</th>
    </tr>
    <tr>
        <td><strong>D1(Мутант)</strong></td>
        <td>1</td>
        <td style="background-color: #ee54d998;">1</td>
        <td>1</td>
        <td>0</td>
        <td>0</td>
        <td>1</td>
        <td>0</td>
        <td>1</td>
        <td>20</td>
        <td><strong>43</strong></td>
    </tr>
    <tr>
        <td><strong>D2(Мутант)</strong></td>
        <td >1</td>
        <td >0</td>
        <td >1</td>
        <td >1</td>
        <td >1</td>
        <td style="background-color: #ee54d998;">0</td>
        <td >0</td>
        <td >1</td>
        <td>19</td>
        <td><strong>40</strong></td>
    </tr>
</table>

Генерируем группы для турнира из оставшихся особей (A6 С1 B2 C2(Мутант)):

<table border="1" cellpadding="5" cellspacing="0">
    <tr>
        <td>1 группа</td>
        <td>Победитель</td>
    </tr>
    <tr>
        <td style="text-align: center;" >A6</td>
        <td rowspan="2" style="text-align: center; vertical-align: middle;">A6</td>
    </tr>
    <tr>
        <td style="text-align: center;">C1</td>
    </tr>
    <tr>
        <td>2 группа</td>
        <td>Победитель</td>
    </tr>
    <tr>
        <td style="text-align: center;">B2</td>
        <td rowspan="2" style="text-align: center; vertical-align: middle;">B2</td>
    </tr>
    <tr>
        <td style="text-align: center;">C2(Мутант)</td>
    </tr>
</table>

В конечном итоге в третье поколения включаются: A5 B1 D2(Мутант) D1(Мутант) B2 A6

## Четвёртое поколение
<table border="1" cellpadding="5" cellspacing="0">
    <tr>
        <th>Особь</th>
<th>A</th>
<th>B</th>
<th>C</th>
<th>D</th>
<th>E</th>
<th>F</th>
<th>G</th>
<th>H</th>
<th>V(X)</th>
<th>F(X)</th>
    </tr>
    <tr>
        <td><strong>A5</strong></td>
        <td>1</td>
        <td>0</td>
        <td>1</td>
        <td>0</td>
        <td>1</td>
        <td>1</td>
        <td>0</td>
        <td>1</td>
        <td>23</td>
        <td style="background-color: #73ee5498;">44</td>
    </tr>
    <tr>
        <td><strong>B1</strong></td>
        <td>1</td>
        <td>0</td>
        <td>1</td>
        <td>1</td>
        <td>0</td>
        <td>1</td>
        <td>0</td>
        <td>1</td>
        <td>21</td>
        <td>42</td>
    </tr>
    <tr>
        <td><strong>D2(Мутант)</strong></td>
        <td>1</td>
        <td>0</td>
        <td>1</td>
        <td>1</td>
        <td>1</td>
        <td>0</td>
        <td>0</td>
        <td>1</td>
        <td>19</td>
        <td>40</td>
    </tr>
    <tr>
        <td><strong>D1(Мутант)</strong></td>
        <td>1</td>
        <td>1</td>
        <td>1</td>
        <td>0</td>
        <td>0</td>
        <td>1</td>
        <td>0</td>
        <td>1</td>
        <td>20</td>
        <td style="background-color: #73ee5498;">43</td>
    </tr>
    <tr>
        <td><strong>B2</strong></td>
        <td>0</td>
        <td>1</td>
        <td>1</td>
        <td>0</td>
        <td>1</td>
        <td>1</td>
        <td>0</td>
        <td>0</td>
        <td>22</td>
        <td>42</td>
    </tr>
    <tr>
        <td><strong>A6</strong></td>
        <td>0</td>
        <td>1</td>
        <td>1</td>
        <td>1</td>
        <td>0</td>
        <td>1</td>
        <td>0</td>
        <td>0</td>
        <td>20</td>
        <td>40</td>
    </tr>
</table>

Все особи приспособлены

Отбираем две самые приспособленные особи для двуточечного скрещивания:

A5 и D1(Мутант) самые сильные особи (элита)

<table border="1" cellpadding="5" cellspacing="0">
    <tr>
        <th>Особь</th>
        <th>A</th>
        <th>B</th>
        <th>C</th>
        <th>D</th>
        <th>E</th>
        <th>F</th>
        <th>G</th>
        <th>H</th>
        <th>V(X)</th>
        <th>F(X)</th>
    </tr>
    <tr>
        <td><strong>A5</strong></td>
        <td>1</td>
        <td style="background-color: #eedf5498;">0</td>
        <td style="background-color: #eedf5498;">1</td>
        <td>0</td>
        <td>1</td>
        <td>1</td>
        <td>0</td>
        <td>1</td>
        <td>23</td>
        <td><strong>44</strong></td>
    </tr>
    <tr>
        <td><strong>D1(Мутант)</strong></td>
        <td style="background-color: #eedf5498;">1</td>
        <td>1</td>
        <td>1</td>
        <td style="background-color: #eedf5498;">0</td>
        <td style="background-color: #eedf5498;">0</td>
        <td style="background-color: #eedf5498;">1</td>
        <td style="background-color: #eedf5498;">0</td>
        <td style="background-color: #eedf5498;">1</td>
        <td>20</td>
        <td><strong>43</strong></td>
    </tr>
</table>

Выбирем две точки для скрещивания

E1 и E2 потомки в результате двуточечного скрещивания:

<table border="1" cellpadding="5" cellspacing="0">
    <tr>
        <th>Особь</th>
        <th>A</th>
        <th>B</th>
        <th>C</th>
        <th>D</th>
        <th>E</th>
        <th>F</th>
        <th>G</th>
        <th>H</th>
        <th>V(X)</th>
        <th>F(X)</th>
    </tr>
    <tr>
        <td><strong>E1</strong></td>
        <td>1</td>
        <td>1</td>
        <td>1</td>
        <td>0</td>
        <td>1</td>
        <td>1</td>
        <td>0</td>
        <td>1</td>
        <td>26</td>
        <td><strong>53</strong></td>
    </tr>
    <tr>
        <td><strong>E2</strong></td>
        <td style="background-color: #eedf5498;">1</td>
        <td style="background-color: #eedf5498;">0</td>
        <td style="background-color: #eedf5498;">1</td>
        <td style="background-color: #eedf5498;">0</td>
        <td style="background-color: #eedf5498;">0</td>
        <td style="background-color: #eedf5498;">1</td>
        <td style="background-color: #eedf5498;">0</td>
        <td style="background-color: #eedf5498;"> 1</td>
        <td>17</td>
        <td><strong>34</strong></td>
    </tr>
</table>

Потомок E1 не приспособленный

Генерируем мутации для потомков:
* E1 - Нет (3)
* E2 - Нет (3)

Генерируем группы для турнира из оставшихся особей (B2 A6 B1 D2(Мутант)):

<table border="1" cellpadding="5" cellspacing="0">
    <tr>
        <td>1 группа</td>
        <td>Победитель</td>
    </tr>
    <tr>
        <td style="text-align: center;" >B2</td>
        <td rowspan="2" style="text-align: center; vertical-align: middle;">B2</td>
    </tr>
    <tr>
        <td style="text-align: center;">A6</td>
    </tr>
    <tr>
        <td>2 группа</td>
        <td>Победитель</td>
    </tr>
    <tr>
        <td style="text-align: center;">B1</td>
        <td rowspan="2" style="text-align: center; vertical-align: middle;">B1</td>
    </tr>
    <tr>
        <td style="text-align: center;">D2(Мутант)</td>
    </tr>
</table>

Из оставшихся A6 и D2(Мутант) - выбираем D2(Мутант) поскольку меньше вес

В конечном итоге в третье поколения включаются: A5 D1(Мутант) E2 B1 B2 D2(Мутант)

## Пятое поколение

<table border="1" cellpadding="5" cellspacing="0">
    <tr >
<th>Особь</th>
<th>A</th>
<th>B</th>
<th>C</th>
<th>D</th>
<th>E</th>
<th>F</th>
<th>G</th>
<th>H</th>
<th>V(X)</th>
<th>F(X)</th>
    </tr>
    <tr>
        <td><strong>A5</strong></td>
        <td>1</td>
        <td>0</td>
        <td>1</td>
        <td>0</td>
        <td>1</td>
        <td>1</td>
        <td>0</td>
        <td>1</td>
        <td>23</td>
        <td style="background-color: #73ee5498;">44</td>
    </tr>
    <tr>
        <td><strong>D1(Мутант)</strong></td>
        <td>1</td>
        <td>1</td>
        <td>1</td>
        <td>0</td>
        <td>0</td>
        <td>1</td>
        <td>0</td>
        <td>1</td>
        <td>20</td>
        <td>43</td>
    </tr>
    <tr>
        <td><strong>E2</strong></td>
        <td>1</td>
        <td>0</td>
        <td>1</td>
        <td>0</td>
        <td>0</td>
        <td>1</td>
        <td>0</td>
        <td>1</td>
        <td>17</td>
        <td>34</td>
    </tr>
    <tr>
        <td><strong>B1</strong></td>
        <td>1</td>
        <td>0</td>
        <td>1</td>
        <td>1</td>
        <td>0</td>
        <td>1</td>
        <td>0</td>
        <td>1</td>
        <td>21</td>
        <td>42</td>
    </tr>
    <tr>
        <td><strong>B2</strong></td>
        <td>0</td>
        <td>1</td>
        <td>1</td>
        <td>0</td>
        <td>1</td>
        <td>1</td>
        <td>0</td>
        <td>0</td>
        <td>22</td>
        <td>42</td>
    </tr>
    <tr>
        <td><strong>D2(Мутант)</strong></td>
        <td>1</td>
        <td>0</td>
        <td>1</td>
        <td>1</td>
        <td>1</td>
        <td>0</td>
        <td>0</td>
        <td>1</td>
        <td>19</td>
        <td>40</td>
    </tr>
</table>

## Ответ:
### На момент 5 поколения:
* Максимальная стоимость предметов в рюкзаке  - 44
* Набор предметов особи - (A C E F H)
* Вес предметов в рюкзаке - 23
* Свободное место в рюкзаке - 1

### Точное решение:
* Максимальная стоимость предметов в рюкзаке  - 51
* Набор предметов особи - (A B C D F H)
* Вес предметов в рюкзаке - 24
* Свободное место в рюкзаке - 0

### Разница от точного решения составляет - 7