# Полносвязная нейронная сеть на Python

### Этапы написания, ошибки, выводы:
- #### Создал класс, расписал всё до этапа обратного распространения ошибки:
  - взял один батч и бегал по нему циклом *(позднее переписал под матрицы)*;
  - от входных данных до фактических предсказаний бегал одним циклом, породил кучу if-elif-else, и это определенно смущало.. *(в дальнейшем переписал блоками first-hidden-last)*;
  - данные буду хранить в одном вложенном списке объектов, многомерных тензоров, подумал я.. благо, со временем, здравый смысл взял верх;
  - поскакав по граблям, добился понятной архитектуры;
- #### Backprop потребовал от меня посидеть с блокнотом и ручкой:
  - расписал поэтапно в блокноте формулы нахождения всех градиентов;
  - во избежание ошибок расписал размерности всех матриц и тензоров с данными;
  - немножко мозгового штурма на тему 'что во что преобразуется при нахождении производных' и, вуаля, блок готов;
- #### Далее Update, ряд ошибок кода, добавление циклов по батчам и эпохам:
  - нормировал данные после ReLU;
  - исключил вероятности деления на ноль, что вылазили местами;
  - убедился, что код работает при изменении количества слоев и нейронов (не без грабель, конечно);
  - ужаснулся с того, насколько медленно моделька учится на полном наборе данных мниста;
- #### Время оптимизации и рефакторинга:
  - избавившись от лишних for и if, удалось местами сократить код в 6 раз и при этом ускорить работу едва ли не в десятки раз;
  - добавил возможность менять гиперпараметры вне класса;
  - на практике узнал, что большое количество часто используемых self. внутри класса способно значительно (на моих тестах до 40%) замедлить выполнение кода;
  - пришел к выводу, что оптимизировать еще есть что (уменьшить self., добавить Momentum, Nesterov...), но в целом, поставленная задача перед собой выполнена.
