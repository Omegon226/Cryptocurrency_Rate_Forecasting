# State of the art решения прогнозирования временных рядов для курсов криптовалют

<p align="center">
 <img src="https://github.com/Omegon226/Cryptocurrency_Rate_Forecasting/assets/69383841/11c2f5bd-4462-413f-a0a5-76533e863f7b"/>
</p>

<p align="center">
  <b>
    🚧WIP🚧
  </b>
</p>

В скором времени здесь будут выложены ipython ноутбуки с пайплайнами обработки данных, моделями и их тестированием

Здесь будут использоваться классические модели машинного обучения (ML) (KNN, ARIMA, GradientBoosting и др.), нейронные сети (DL) (свёрточные, рекурентные сети, трансформеры и др.) и модели обучения с помощью подкрепления (RL)

Модели будут создаваться и проверятся для краткосрочного прогноза (1 сек., 15 сек.), долгосрочного прогноза (5 мин., 10 мин., 15 мин.) и стратегического прогноза (1 дн., 3 дн., 1 нед.)

## Условия

Сначала опишем в каком формате будут подаваться данные в наши модели. Для классических моделей машинного обучения это будет делаться построчно (из таблицы данных будет подаваться строчка для дальнейшего прогноза). А для других моделей и возможно особых моделей классического машинного обучения данные будут подаваться как в первом варианте, так и с помощью окон данных. Это связано с ограничением некоторых моделей на размерность подаваемых входных данных (для ML моделей Sklearn нужно подавать только двухмерные данные)

У нас не будет унивариативного прогноза, только мультивариативный прогноз. В модели будут подаваться собственные значения временного ряда, а так-же доп статистика (среднее, стандартное отклонение, альфа, бета и др.). Прогнозировать мы будем собственные значения временного ряда

Здесь не будут представлены MLOps инструменты для отбора моделей и др. Не будет MLFlow, ClearML, Spark и др. Только чистый DS и R&D

Мы будем использовать только данные временных рядов для прогноза. Мы не будем анализировать новости для того, чтобы произвести прогноз, это NLP задача, которая не будет здесь рассматриваться. Так-же мы не будем определять уверенность модели в её прогнозах (мы не будем использовать задачу классификации)

Данные будут браться с CoinMarketCap или CoinGecko, или Binance, м.б. с других API (CoinMarketCap API гораздо качественней, по сравнению с CoinGecko, но его бесплатный функционал меньше). Так-же данные могут браться из сторонних датасетов

Для краткосрочного прогноза мы будем прогнозировать только одну точку, для остальных мы будем прогназировать несколько точек (3 - 30 точек вперёд в зависимости от типа прогноза)

В данной задаче мы будем прогназировать только Биткоин, т.к. он имеет самые большие исторические данные

## Протокол работы (от получения данных до тестирования модели)

1) Сначала мы получаем табличные данные о криптовалюте из выбранного API (либо из сохранённого датасета из других источников)
2) Анализ полученных данных, в основном это будут визуализации
3) В зависимости от качества данных их надо будет очистить (доп.)
4) Далее для данных нужно расчитать дополнительную статистику
5) После этого в зависимости от типа прогноза и данных их нужно заресемплить и получить множество таблиц с данными
6) В зависимости от модели требуется проскейлить данные (доп.)
7) Анализ полученных данных
8) Создание датасетов для различных типов прогнозов
9) Создание, настройка и обучение модели
10) Тестирование получившейся модели

P.s. в дальнейшем может использоваться функционал для улучшения данных, например уменьшение размерности с помощью PCA и д.р.

## Как будут отбираться модели

Модели будут отбираться на основе качества их прогноза, которое будет вычислятся с помощью классических метрик (MSE, RMSE, MAE, R2), а так-же визуализаций и на основе их скорости работы (к примеру KNN работает гораздо быстрее, чем нейронные сети), чем модель будет быстрее работать тем лучше она будет подходить для краткосрочного прогноза (но это не говорит о том, что модель будет хуже подходить для долгосрочного или стратегического прогноза)

## Статьи и источники для анализа:

- https://openreview.net/pdf?id=cGDAkQo1C0p
- https://github.com/lucidrains/iTransformer/tree/main
- https://openreview.net/pdf?id=bMUZXhuFEf
- https://openreview.net/pdf?id=cGDAkQo1C0p
- https://arxiv.org/ftp/arxiv/papers/1803/1803.03916.pdf
- https://datascience.stackexchange.com/questions/37589/can-reinforcement-learning-be-applied-for-time-series-forecasting
