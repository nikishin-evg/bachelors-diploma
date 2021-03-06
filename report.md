# Отчёт

**13.04**
Ошибка аппроксимации на тесте у этой архитектуры составляет 0.20, в то время как у классических алгоритмов (SVD, NMF, content-based kNN) оно составляет 0.36.


**10.04**
Реализовал сеть, представляющую собой объединение компоненты для предсказания рейтинга и двух автокодировщиков, приближающую строки / столбцы матрицы рейтингов. Рейтинг вычисляется следующим образом: представления, получаемые на выходе кодирущих частей, конкатенируются и подаются на вход сети, выдающей рейтинг. При этом обучается всё одновременно. Сеть оптимизирующует функционал, являющийся взвешенной суммой из трёх слагаемых: первые два отвечают за качество аппроксимации векторов пользователей и фильмов соответственно, а третий — за качество предсказания. Код довольно аккуратный, так что можно даже позапускать (fit_double_nn.py).


**03.04**
Реализовал построчный автокодировщик и автокодировщик, принимающий на вход конкатенированные векторы пользователей и предметов.


**27.03**
Релевантные статьи:
* [AutoRec](http://users.cecs.anu.edu.au/~u5098633/papers/www15.pdf) (2015). Предлагается просто скармливать автокодировщику строки или столбцы матрицы рейтингов. По сути, это как раз то, что я реализовал. С этим алгоритмом любят сравнивать во многих других недавних статьях
* [Neural Network MF](https://arxiv.org/pdf/1511.06443.pdf) (2015). Идея статьи заключается в моделировании рейтингов в виде выхода нейронной сети. Однако, кажется, нейронной сетью они называют обыковенный сумматор, так как я нигде не увидел упоминания нелинейностей. Авторы в начале упоминают, что оптимизация факторов как-то связана с artistic style'ом, но нигде не поясняют дальше. Мутно
* [Collaborative filtering with autoencoders](https://arxiv.org/pdf/1603.00806.pdf) (2016). А здесь предлагается идея использовать 2 автокодировщика для пользователей и для товаров, однако обучаются они, опять же, раздельно.
* [Collaborative filtering with LSTM](https://arxiv.org/pdf/1608.07400.pdf) (2017). Совсем свежая статья. Только месяц назад выложили код к ней. Много этого кода, кажется, можно использовать. Предлагается, в отличие от классических подходов, использовать также время выставления оценки, и, в соответствии с ним, подавать на вход сети.


**23.03**
Необязательно использовать линейную аппроксимацию (учить факторы U и V): можно попробовать использовать автокодировщик. При этом теоремы из статьи остаются справедливы.


**21.03** 
Реализовал и слегка протестировал алгоритм из [статьи](http://jmlr.org/proceedings/papers/v48/lib16.pdf)

Смущает, что с самой первой итерации градиентного спуска на тесте достигается лучшее качество для всех рангов аппроксимации. Ещё смущает, что ошибка на тренировочной выборке сильно возрастает от процедуры.
