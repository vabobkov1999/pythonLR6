# Лабораторная работа №6

Классификаторы на основе нейронных сетей прямого распространения
----------------------------------------------------------------


| 🔢  | Ход работы   | ℹ️ |
| ------------- | ------------- |------------- |
| 1️⃣  |  Установить библиотеку keras, tensorflow. | ✅ |
| 2️⃣ | Скачать датасет с симпсонами варианту (для каждого класса отдельная директория).  |✅  |
| 3️⃣ | Создать архитектуру нейронной сети прямого распространения с двумя полносвязными скрытыми слоями и сверточной нейронной сети с двумя сверточными и двумя полносвязными слоями и скомпилировать модели (model.summary()). |✅  |



Цель работы
------------
С помощью python3.8 разработать нейронные сети с прямой связью (обычную и свёрточную нейронные сети) для классификации картинок. Создать архетектуру нейронной сети и обучить её. Классифицировать картинки в соответствии с вариантом.

Выполнение работы
-----------------

#### Feedforward Neural Network

Нейронная сеть прямого распространения - это искусственная нейронная сеть, в которой соединения между узлами не образуют цикла. Мы подаём на вход "сырые" картинки, а на выходе получаем какую-то вероятность принадлежности какому-то классу. FFNN(Feedforward Neural Network) данные сразу передаются в нейронную сеть.

<p align="center">
  <img src="https://vitalflux.com/wp-content/uploads/2020/10/feed_forward_neural_network-1.gif" />
</p>

Путь train_path по которым будет учиться нейронка. test_path путь к файлам которые мы будем классифицировать. result_path куда сохраняются файлы которые нейронка обработала.
plot_path куда сохранить график
Массив дата будет содержать информацию о картинках т.е матрицу RGB  (Матрица размерности = ширина х высоту х (3(тк 3 цвета))
Массив лейблс название картинок

С помощью метода listdir смотрим какие папки находятся на пути
Далее сортировка по имени с помощью метода sort()

цикл по изображениям  просмотр папок
запоминания пути, создание пути для тренировки
создать путь для каждой картинки
преобразование изображение в размер 32х32
flatten одномерный массив

train_test_split метод делит данные на тренировучную и тестувую выборку
random_state=seed принцип деления данных по закономерности
LabelBinarizer метод который к каждому классу дает вектор, если классов 5 то вектор длинны 5

Sequential создание нейронки
add добавляю слои
Dense спрятанный слой
activation="sigmoid функция активации
EPOCHS = 20 инициализация эпох
model.summary() архитектура нейронки

оценка нейросети

 строим графики потерь и точности
 метод history
 test_labels = os.listdir(test_path) запоминание названий картинок
 запоминаем путь считываем его

 predictions = model.predict(image) вектор вероятности

Метод lb.classes запоминает и что-то там уникальные индефикаторы>

выводим название класса и вероятность принадлежности на картинку.



#### Convolutional Neural Network

Свёрточная нейронная сеть - это такая же нейронная сеть, но прежде чем подать данные их предварительно обрабатывают для получения вектора фитч. CNN(Convolutional Neural Network)-предварительная обработка данных.

<p align="center">
  <img src="https://miro.medium.com/max/1000/1*BIpRgx5FsEMhr1k2EqBKFg.gif" />
</p>

При обработки изображений CNN выполняются следующие операции:
* Классификация - это первый этап обработки изображения на, котором происходит разделение объектов на определённое количество классов по определённым признакам, при этом задано конечное множество объектов, для которых уже определен класс. Для остальных необходимо построить алгоритм, способный классифицировать их. Так же для классификации используются полносвязные слои.

<p align="center">
  <img src="https://btechmag.com/wp-content/uploads/2020/11/UNSupervised-Learning.gif" />
</p>

* Детекция – задача, в рамках которой необходимо выделить несколько объектов на изображении посредством нахождения координат их ограничивающих рамок и классификации этих ограничивающих рамок из множества заранее известных классов.

<p align="center">
  <img src="http://download.smartlife.global/files/face-recog-4.gif" />
</p>

* Сегментация - поиск групп пикселей, каждая из которых обладает определенными признаками.
Сверточные слои обычно рисуются в виде набора плоскостей или объемов. Каждая плоскость на таком рисунке или каждый срез в этом объеме — это, по сути, один нейрон, который реализует операцию свертки. По сути, это матричный фильтр,
который трансформирует исходное изображение в какое-то другое, и это можно делать много раз.

<p align="center">
  <img src="https://s3-us-west-2.amazonaws.com/static.pyimagesearch.com/opencv-mask-rcnn/mask_rcnn_example03.gif" />
</p>

* Слои субдискретизации (Subsampling или Pooling) просто уменьшают размер изображения: было 200х200 ps, после Subsampling стало 32х32 ps. По сути, усреднение.

<p align="center">
  <img src="https://miro.medium.com/max/1400/1*kOThnLR8Fge_AJcHrkR3dg.gif" />
</p>


### Результат выполнения программы

#### Нейронная сеть прямого распространения



![Gitlab logo](https://bmstu.codes/MorozoFF/lr-6-opc/-/raw/master/FFNN_model.png)


Оценка полноты, точности и аккуратности


![Gitlab logo](https://bmstu.codes/MorozoFF/lr-6-opc/-/raw/master/FFNN_accuracy.png)

График потерь и точности для каждой модели


![Gitlab logo](https://bmstu.codes/MorozoFF/lr-6-opc/-/raw/master/loss-accuracy-ffnn__epoch_20_.png)

![Gitlab logo](https://bmstu.codes/MorozoFF/lr-6-opc/-/raw/master/loss-accuracy-ffnn.png)



#### Свёрточная нейронная сеть




![Gitlab logo](https://bmstu.codes/MorozoFF/lr-6-opc/-/raw/master/CNN_model.png)


Оценка полноты, точности и аккуратности


![Gitlab logo](https://bmstu.codes/MorozoFF/lr-6-opc/-/raw/master/CNN_accuracy.png)


График потерь и точности для каждой модели


![Gitlab logo](https://bmstu.codes/MorozoFF/lr-6-opc/-/raw/master/loss-accuracy-сnn.png)

![Gitlab logo](https://bmstu.codes/MorozoFF/lr-6-opc/-/raw/master/loss-accuracy-сnn__epoch_25_.png)

Данные полученные в результате выполнения ЛР с нестандартными картинками [Ссылка на Google диск с данными](https://drive.google.com/drive/folders/1bCQIDeO7y4lV-IXUu9NI_t2EC_Bhh_hF?usp=sharing)

Так же напоминаю для тех кому интересно выполнить задание самому или протестировать данную программу, то прошу перейти [сюда](https://drive.google.com/drive/folders/1b_molbj8z6JhHV6r178AeI1XpQezehsm?usp=sharing "Практикум по машинному обучению")
