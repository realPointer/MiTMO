# Лабораторная работа №1: Оценка точности модели с непрерывной зависимой переменной
**Вариант №5**

С использованием пакета rpy2

*Модели*: сглаживающие сплайны.   
*Данные*: сгенерированные.   

$X \sim U(5, 105)$   
$Y = f(X) + \epsilon$, где $f(X) = 15 + 0.02 \cdot X - 0.005 \cdot (X - 45)^2 + 0.00006 \cdot (X - 54)^3$; $\epsilon \sim N(0, 1)$.


## Задание 1
![](https://github.com/realPointer/MiTMO/blob/main/lab1/images/source.png)
![](https://github.com/realPointer/MiTMO/blob/main/lab1/images/change.png)

Лучшую модель следуют выбирать по минимуму на кривой MSE на тестовой выборке. 

Минимальные значения достигаются в этой точке
|Степень свободы | MSE_train    | MSE_test   | 
|----------------| -------------|------------|
| 6              | 0.901229     | 0.42969    |

Поэтому следует выбрать df = 6

![](https://github.com/realPointer/MiTMO/blob/main/lab1/images/spline.png)


## Задание 2
Изменение параметра $sigma$ влияет на разброс точек по вертикали при генерации данных. От этого так же растёт значение MSE на обучающей и тестовой выборке и появляется необходимость построение сплайна с меньшими степенями свободы  
### 2.1 $sigma = 0.5$
![](https://github.com/realPointer/MiTMO/blob/main/lab1/images/source_2_1.png)
![](https://github.com/realPointer/MiTMO/blob/main/lab1/images/change_2_1.png)
![](https://github.com/realPointer/MiTMO/blob/main/lab1/images/spline_2_1.png)
### 2.2 $sigma = 1$
![](https://github.com/realPointer/MiTMO/blob/main/lab1/images/source_2_2.png)
![](https://github.com/realPointer/MiTMO/blob/main/lab1/images/change_2_2.png)
![](https://github.com/realPointer/MiTMO/blob/main/lab1/images/spline_2_2.png)
### 2.3 $sigma = 1.5$
![](https://github.com/realPointer/MiTMO/blob/main/lab1/images/source_2_3.png)
![](https://github.com/realPointer/MiTMO/blob/main/lab1/images/change_2_3.png)
![](https://github.com/realPointer/MiTMO/blob/main/lab1/images/spline_2_3.png)
