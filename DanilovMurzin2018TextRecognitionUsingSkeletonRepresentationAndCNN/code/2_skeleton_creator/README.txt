0) Написать в отчете, что были заимствованы чужие коды: библиотека скелетонизации Никиты Ломова, скрипты для запуска Ани Липкиной.
1) Понять, как строится непрерывное представление скелета (почитать можно в прилагающейся книжке).

FOR OS LINUX
2) Необходимый софт:
	утилиты qmake, make
	python2/3, либа termcolor
	Qt5

3) Как собрать проект:
	В папке PatterSpectrum:
		qmake -project
		На выходе получится файл с расширение .pro. Добавить в этот файл строчку QMAKE_CXXFLAGS += -Wextra -std=c++11
		qmake
		На выходе получится MakeFile, который потом запускается с помощью make

4) Как запускать:
	python(2 or 3) make_bones.py <параметр стрижки> <индекс_файла> <имя папки с изображениями>

индекс файла может быть любым, он остался от другого кода.
параметр стрижки --- насколько сильно стричь скелет (подробне об этом в прилагающейся книжке)

Важно: скрипт гарантированно работает с изображениями в формате png, c bmp может не всегда работать. Папка с изображениями должна лежать там же, где и make_bones.py и PatternSpectumConsole

На выходе выдает 2 файла: Geogliph_files_paths.txt --- файлы, которые лежат в переданной в аргументе папке
Geogliph_bones<индекс_файла>.txt --- описание скелета изображений:
	На каждое изображение в папке отводится строчка этого файла
	Порядок строк такой же, как и в Geogliph_files_paths.txt
	Описание строки: набор чисел, каждые 8 подряд идущих чисел описывают ребро скелета: по 4 числа на каждую вершину ребра: (x_coord, y_coord, deg, rad), deg --- степень вершины (она может быть от 1 до 3, таков алгоритм построения скелета), rad --- радиальная функция в этой точке, или же, радиус вписанной в фигуру окружности в этой точке.


