# Лабораторная работа №5: Машины опорных векторов

_Модели_: PCR, Случайный лес, kNN

_Данные_: `winequality-white_for_lab` (источник: https://github.com/ania607/ML/blob/main/data/winequality-white_for_lab.csv)

## Загрузка данных

Загружаем данные и откладываем 15% наблюдений для прогноза.

## Предварительный анализ данных

Выводы по описательным статистикам: значения объясняющих переменных положительные, масштабы измерения отличаются. Убираем `quality` из-за нулевой дисперсии

## Стандартизация и переход к главным компонентам

Предварительно преобразуем пространство исходных показателей с помощью метода главных компонент

## Прогноз на отложенные наблюдения по лучшей модели

Настройки параметров моделей позволяет повысить точность модели kNN с 0.718 до 0.794, для случайного леса это лишь увеличение на 0.002

Итоговые значения моделей

|     |      Модель      |  Acc  |
| :-: | :--------------: | :---: |
|  0  |    pca_logit     | 0.660 |
|  1  | random_forest_GS | 0.837 |
|  2  |    sc_pca_knn    | 0.794 |

Модели 1 и 2 показывают неплохие значения по показателю $Acc$, при этом самой точной оказывается модель случайного леса. Сделаем прогноз на отложенные наблюдения.

|              | precision | recall | f1-score | support |
| :----------: | :-------: | :----: | :------: | :-----: |
|      0       |   0.75    |  0.71  |   0.73   |   241   |
|      1       |   0.86    |  0.88  |   0.87   |   494   |
|   accuracy   |           |        |   0.83   |   735   |
|  macro avg   |   0.81    |  0.80  |   0.80   |   735   |
| weighted avg |   0.83    |  0.83  |   0.83   |   735   |