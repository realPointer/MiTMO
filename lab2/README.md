# Лабораторная работа №3: Линейные модели. Кросс-валидация.

_Модели_: множественная линейная регрессия

_Данные_: `Boston_for_lab` (источник: <https://github.com/ania607/ML/blob/main/data/Boston_for_lab.csv>)

## Предварительный анализ данных:
![image](https://user-images.githubusercontent.com/50529632/197278511-6d44048b-8b90-4859-bc71-024affd704b9.png)

Судя по этим графикам:  
* распределение зависимой `medv` является нормальным;  
* из всех объясняющих нет нормально распределённых;  
![image](https://user-images.githubusercontent.com/50529632/197278661-7eb8936f-7153-4891-9ab3-ed5fb9571288.png)

## Оценка взаимосвязи
### Корреляционная матрица по всем наблюдениям

![image](https://user-images.githubusercontent.com/50529632/197278966-6bd0928c-0c23-4f6a-a63a-0e7d176d4a28.png)

Средняя отрицательная связь между $medv$ и $indus$, $medv$ и $crim$. Средняя положительная между $indus$ и $crim$

### Корреляционная матрица по классу налог на имущество превышает 400

![image](https://user-images.githubusercontent.com/50529632/197279156-41c024d9-300f-4ac8-8fe2-45ef6daa6fc4.png)

Слабая отрицательная между $medv$ и $indus$, средняя отрицательная $medv$ и $crim$. Слабая между $indus$ и $crim$

### Корреляционная матрица по классу налог на имущество не превышает 400

![image](https://user-images.githubusercontent.com/50529632/197279235-c394d2e9-085a-4771-b32b-d18b2a8feb1e.png)

Слабая отрицательная $medv$ и $crim$, средняя отрицательная $medv$ и $indus$. Слабая между $indus$ и $crim$

## Проверка Y на нормальность:
$medv   Statistics = 0.92, p = 0.0000$
Распределение не нормально (H0 отклоняется)

$log\\_medv   Statistics = 0.98, p = 0.0000$
Распределение не нормально (H0 отклоняется)

![image](https://user-images.githubusercontent.com/50529632/197280817-2b219c03-b72a-4777-8b58-5f4e08825bf8.png)

### Корреляционная матрица по классу налог на имущество превышает 400

![image](https://user-images.githubusercontent.com/50529632/197280842-210db7be-b399-4761-8852-20e1333e84de.png)

Слабая отрицательная $log\\_medv$ и $indus$, средняя отрицательная $log\\_medv$ и $crim$. Слабая между $indus$ и $crim$

### Корреляционная матрица по классу налог на имущество не превышает 400

![image](https://user-images.githubusercontent.com/50529632/197280866-9abab4f3-9894-4a0b-b193-6ad47cb52ecd.png)

Слабая отрицательная $log\\_medv$ и $crim$, средняя отрицательная $log\\_medv$ и $indus$. Слабая между $indus$ и $crim$

## Список возможных спецификаций моделей:
По итогам предварительного анализа данных можно предложить следующие спецификации линейных регрессионных моделей:  

1. `fit_lm_1`: $\hat{medv} = \hat{\beta_0} + \hat{\beta_1} \cdot tax\\_over\\_400 + \hat{\beta_2} \cdot indus + \hat{\beta_3} \cdot crim$
1. `fit_lm_2`: $\hat{medv} = \hat{\beta_0} + \hat{\beta_1} \cdot tax\\_over\\_400 + \hat{\beta_2} \cdot indus \cdot tax\\_over\\_400 + \hat{\beta_3} \cdot crim$
1. `fit_lm_3`: $\hat{medv} = \hat{\beta_0} + \hat{\beta_1} \cdot tax\\_over\\_400 + \hat{\beta_2} \cdot crim \cdot tax\\_over\\_400 + \hat{\beta_3} \cdot indus$
1. `fit_lm_4`: $\hat{medv} = \hat{\beta_0} + \hat{\beta_1} \cdot tax\\_over\\_400 + \hat{\beta_2} \cdot crim \cdot tax\\_over\\_400 + \hat{\beta_3} \cdot indus \cdot tax\\_over\\_400$

1. `fit_lm_1_log`: то же, что `fit_lm_1`, но для зависимой $\hat{log\\_medv}$  
1. `fit_lm_2_log`: то же, что `fit_lm_2`, но для зависимой $\hat{log\\_medv}$
1. `fit_lm_3_log`: то же, что `fit_lm_3`, но для зависимой $\hat{log\\_medv}$
1. `fit_lm_4_log`: то же, что `fit_lm_4`, но для зависимой $\hat{log\\_medv}$

Кроме того, добавим в сравнение модели зависимости `medv` и `log_medv` от всех объясняющих переменных: `fit_lm_0` и `fit_lm_0_log` соответственно. (9 и 10) 

## Оценка параметров моделей
Оценим точность моделей методом перекрёстной проверки K-VAL(10)

Наименьшая ошибка на тестовой у модели `fit_lm_3`: $MSE\\_kf10 = 62.0$

Наименьшая ошибка на тестовой у модели `fit_lm_1_log`: $MSE\\_kf10 = 0.098$

Самой точной среди моделей для $medv$ оказалась `fit_lm_3`, а среди моделей для $medv\\_log$ – `fit_lm_1_log`

## Прогноз на отложенные наблюдения

MSE модели `fit_lm_3` на отложенных наблюдениях = $376.32$

MSE модели `fit_lm_1_log` на отложенных наблюдениях = $116.05$

## Вывод

Более точная модель является `fit_lm_1_log`








