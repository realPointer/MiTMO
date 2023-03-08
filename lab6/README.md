# Лабораторная работа №6: Кластеризация

*Данные*: load_breast_cancer

Исходные данные содержат 569 наблюдений и 30 параметров

Для рассматрения возьмём средние значения 3-ёх признаков ядра клетки:
* **Perimeter** - периметр
* **Smoothness** - гладкость
* **Area** - площадь

Задача состоит в разделении клеток на группы в зависимости от этих показателей

Перед рассмотрением данных была произведена стандартизация

Визуально данные тяжело сгруппировать на отдельные кластеры. Но можно взять, допустим, 2 группы

## Определение оптимального количества кластеров для метода локтя

Как видно на графике выше, локоть расположен в k равным 3, что свидетельствует о том, что это значение является хорошим выбором для этого набора данных

С помощью визуального анализа скорее можно сказать про 2 различные группы

Теперь видим, что каждая группа точек покрашена в цвет соответствующего кластера, а центроиды расположены внутри множества точек. Тем не менее, попробуем оценить качество кластеризации в обоих вариантах.

## Количественная оценка качества кластеризации

Посчитаем для $k=2$: средний коэффициент силуэта - $0.39280429356026775$

Средний коэффициент силуэта для $k=3 - 0.4091072731038419$

Его значение незначительно выше, чем в предыдущем случае. Но формально $k=2$ - единственное разбиение, так как раковые клетки могут быть только доброкачественные и злокачественные

## Сравнение результатов на обучающей и тестовой выборке
Посмотрим, как прогнозировать принадлежность к кластерам, построенным по обучающим данным. Сравним значения средних силуэтных коэффициентов.

Добавляем к выборке дополнительный показатель.

В обучающей выборке - 80% исходных наблюдений.

Перелом сместился ближе к 2 значению. Но значительных изменений не произошло.

Обучаем алгоритм и считаем средний силуэтный коэффициент.

Средний коэффициент силуэта - $0.46175902196471225$

Применяем модель к новым данным. Значение среднего силуэтного коэффициента  улучшилось. Средний коэффициент силуэта --  $0.527111732849388$

## Статистический анализ получившихся кластеров

Визуально  понятно разбиение кластеров, но разбиение остаётся нестрогим

## Оценка точности кластеризации с помощью Acc, сравнив оценки с фактическим разбиением на группы.

Acc для выборки с двумя показателями perimeter и smoothness = $0.8558875219683656$

Из оценки кластеризации следует, что алгоритм K-средних для 2 кластеров достиг высокой точности в своей работе, указывая правильную категоризацию большинства объектов данных.

Acc для выборки с тремя показателями (добавляется area) = $0.1335676625659051$

## Вывод
Можно сказать, что с точностью 85.6% два параметра perimeter и smoothness корректно определяют принадлежность к доброкачественной или злокачественной группе