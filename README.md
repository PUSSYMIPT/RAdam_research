# RAdam_research

В этом репозитории хранится исходный код для запуска и аналитики результатов проекта. 

## Эксперимент

Мы посмотрели на распределение градиентов между последним и предпоследним слоем ResNet-18 на датасете CIFAR-10 c разными оптимизаторами.

![test accuracy](img/test_accuracy.png)
 Для каждого веса была проведена бутстрэпная оценка дисперсии на каждой итерации для величины

<img src="img/alr_formula.png" alt="drawing" width="300"/>

Так же был применен критерий согласия Шапиро-Уилка и сделана попрака FWER методом Холма. В результате было получено несколько графиков — один для каждого параметра.

## Анализ результатов

Для каждого из десяти нейронов посмотрим на распределение градиентов для всех весов имеющих отношение к ним:

<img src="img/grad_dist_all.png" alt="drawing" width="1000"/>

Как видно, в целом, распределение для каждого нейрона похоже на смесь нормальных.

Теперь для каждого веса посмотрим на рапсределение градиентов для него и проверим гипотезу о нормальности. После поправки FWER получим:

<img src="img/fwer.png" alt="drawing" width="500"/>

Посмотрим на тот для которого гипотеза отверглась (первый график), и на тот, для которого гипотеза не отверглась (второй график). Теоретическую оценку возьмем в предположении нормальности градиентов.

<img src="img/bad_distribution.png" alt="drawing" width="700"/>

<img src="img/good_distribution.png" alt="drawing" width="700"/>

Как видно для первого графика на первых итерациях отклонение достаточно значимо.
