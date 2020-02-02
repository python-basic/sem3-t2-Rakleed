# Содержание
- [ИСР № 2](#инвариативная-самостоятельная-работа--2)
    - [1 задание](#21-разработка-скрипта-с-функцией-которая-строит-таблицу-истинности-для-логического-выражения-для-двух-и-трех-аргументов)
    - [2 задание](#22-разработка-программы-которая-выводит-на-экран-с-помощью-ascii-графики-таблицу-истинности-на-основе-переданных-ей-на-вход-аргументов)
    - [3 задание](#23-разработайте-скрипт-с-функцией-которая-для-ряда-фибоначчи-кол-во-элементов--22-возвращает-подмножество-значений-или-единственное-значение)
    - [4 задание](#24-разработка-программы-с-функцией-в-которой-будет-реализовано-решение-физической-задачи)
- [ВСР № 2](#вариативная-самостоятельная-работа--2)
    - [1 задание](#21-исследование-способов-проверки-программного-кода-python-на-совместимость-со-стандартом-pep8)
    - [2 задание](#22-разработака-программы-которая-для-заданного-количества-значений-возвращала-бы-список-из-уникальных-элементов-содержащихся-во-входном-наборе-значений)
    - [3 задание](#23-переписать-лямбда-функцию-генерирующую-квадраты-чисел-из-переменной-типа-list-через-генератор-списка)

# Инвариативная самостоятельная работа № 2

### [2.1. Разработка скрипта с функцией, которая строит таблицу истинности для логического выражения для двух и трех аргументов.](https://repl.it/@Rakleed/programming-indepworkinvar2-1)
```python
"""
    Автор: Моисеенко Павел, группа № 1, подгруппа № 2.

    Задание: разработайте скрипт с функцией, которая строит таблицу ис-
    тинности для логического выражения (по вариантам) для двух и трех 
    аргументов (используются различные наборы значений аргументов).

"""

values_2 = ((0, 0), (0, 1), (1, 0), (1, 1))
values_3 = ((0, 0, 0), (0, 0, 1), (0, 1, 0), (0, 1, 1), (1, 0, 0), (1, 0, 1),
            (1, 1, 0), (1, 1, 1))


def head_2():
    header = "| A | B | F |"
    under_header = "+ " + "-" * (len(header) - 4) + " +"
    print(under_header)
    print(header)
    print(under_header)


def head_3():
    header = "| A | B | C | F |"
    under_header = "+ " + "-" * (len(header) - 4) + " +"
    print(under_header)
    print(header)
    print(under_header)


def truth_table_2(val):
    result = (not val[0]) or val[0]  # ((A→B)∧A)↔A∧B = ¬A∨A
    result = int(result)
    line = "| " + str(val[0]) + " | " + str(val[1]) + " | " + str(result) + \
           " |"
    print(line)
    print('+', '-' * (len(line) - 4), '+')


def truth_table_3(val):
    result = (val[0] or val[1]) and (not val[2])
    result = int(result)
    line = "| " + str(val[0]) + " | " + str(val[1]) + " | " + str(val[2]) + \
           " | " + str(result) + " |"
    print(line)
    print('+', '-' * (len(line) - 4), '+')


def main_2():
    print("F = ((A→B)∧A)↔A∧B\n")
    head_2()
    for i in range(len(values_2)):
        truth_table_2(values_2[i])


def main_3():
    print("\n\nF = (A∨B)∧¬C\n")
    head_3()
    for i in range(len(values_3)):
        truth_table_3(values_3[i])


main_2()
main_3()
```
![Result of indepworkinvar2-1](https://github.com/python-basic/sem3-t2-Rakleed/blob/master/src/programming-indepworkinvar2-1-result.png)

### [2.2. Разработка программы, которая выводит на экран с помощью ASCII-графики таблицу истинности на основе переданных ей на вход аргументов.](https://repl.it/@Rakleed/programming-indepworkinvar2-2)
```python
"""
    Автор: Моисеенко Павел, группа № 1, подгруппа № 2.

    Задание: разработайте программу, которая выводит на экран
    с помощью ASCII-графики таблицу истинности на основе переданных ей
    на вход аргументов (логическое выражение, аргументы, результат
    вычисления выражения).

"""

values = ((0, 0), (0, 1), (1, 0), (1, 1))


def head():
    header = "| A | B | F |"
    under_header = "+ " + "-" * (len(header) - 4) + " +"
    print(under_header)
    print(header)
    print(under_header)


def truth_table(val):
    result = (not val[0] and val[1]) or (val[0] and not val[1])  # (A∨B)∧(¬A∨¬B) = (¬A∧B)∨(A∧¬B)
    result = int(result)
    line = "| " + str(val[0]) + " | " + str(val[1]) + " | " + str(result) + \
           " |"
    print(line)
    print('+', '-' * (len(line) - 4), '+')


def main():
    print("F = (A∨B)∧(¬A∨¬B)\n")
    head()
    for i in range(len(values)):
        truth_table(values[i])


main()
```
![Result of indepworkinvar2-2](https://github.com/python-basic/sem3-t2-Rakleed/blob/master/src/programming-indepworkinvar2-2-result.png)

### [2.3. Разработайте скрипт с функцией, которая для ряда Фибоначчи (кол-во элементов — 22), возвращает подмножество значений или единственное значение.](https://repl.it/@Rakleed/programming-indepworkinvar2-3)
```python
"""
    Автор: Моисеенко Павел, группа № 1, подгруппа № 2.

    Задание: разработайте скрипт с функцией, которая для ряда Фибо-
    наччи, где количество элементов, n = 22, возвращает подмножество 
    значений или единственное значение (по вариантам). Для нахождения 
    элемента требуется использовать слайсы. Формирование отчета по 
    выполнению задания и размещение его в портфолио, персональном 
    репозитории. 

"""


def sample(lst):
    lst_5 = lst[len(lst) // 4::-2]
    sum_of_5 = sum(lst_5)
    lst_10 = lst[1:len(lst) // 2 - 1:2]
    sum_of_10 = sum(lst_10)
    return sum_of_5, sum_of_10


def main():
    fib_numbers = [0, 1, 1, 2, 3, 5, 8, 13, 21, 34, 55, 89, 144, 233, 377, 
                   610, 987, 1597, 2584, 4181, 6765, 10946]
    print(sample(fib_numbers))


main()
```
![Result of indepworkinvar2-3](https://github.com/python-basic/sem3-t2-Rakleed/blob/master/src/programming-indepworkinvar2-3-result.png)

### [2.4. Разработка программы с функцией, в которой будет реализовано решение физической задачи.](https://repl.it/@Rakleed/programming-indepworkinvar2-4)
```python
"""
    Автор: Моисеенко Павел, группа № 1, подгруппа № 2.

    Задание: в правильной четырехугольной пирамиде высота равна h,
    объем равен v. Найдите боковое ребро этой пирамиды. Решение офор-
    мите в виде функции rib(h,v), которая возвращает результат l.
    Например, при h=12; v=200 функция rib(12,200) вернет l=13.

"""

import math


def rib(h, v):
    a = math.sqrt(3 * v / h)
    L = math.sqrt(h ** 2 + (a / (2 * math.sin(45*math.pi/180))) ** 2)
    return L


def main():
    h = int(input("Введите высоту h: "))
    v = int(input("Введите объём V: "))
    if (h > 0) and (v > 0):
        print("Бокоовое ребро пирамиды l = " + str(rib(h, v)))
    else:
        print("Введите числа больше 0.\n")
        main()


print("Программа вычисляет боковое ребро правильной четырёхугольной пирамиды"
      " по высоте h и объёму V.")
main()
```
![Result of indepworkinvar2-4](https://github.com/python-basic/sem3-t2-Rakleed/blob/master/src/programming-indepworkinvar2-4-result.png)

# Вариативная самостоятельная работа № 2

### 2.1. Исследование способов проверки программного кода Python на совместимость со стандартом PEP8.
[Результат.](https://github.com/python-basic/sem3-t2-Rakleed/blob/master/src/programming-indepworkvar2-1-result.pdf)

### [2.2. Разработака программы, которая для заданного количества значений возвращала бы список из уникальных элементов, содержащихся во входном наборе значений.](https://repl.it/@Rakleed/programming-indepworkvar2-2)
```python
"""
    Автор: Моисеенко Павел, группа № 1, подгруппа № 2.

    Задание: разработать программу, которая для заданного количества
    значений возвращала бы список из уникальных элементов,
    содержащихся во входном наборе значений.

"""


def set_func(values):
    var = set(values)
    return list(var)


def main():
    numbers = int(input("Введите количество значений: "))
    print("Теперь вводите числа:")
    values = list()
    while numbers != 0:
        values.append(input())
        numbers -= 1
    print('Введённые значения: ', values)
    print('Уникальные значения: ', set_func(values))


main()
```
![Result of indepworkvar2-2](https://github.com/python-basic/sem3-t2-Rakleed/blob/master/src/programming-indepworkvar2-2-result.png)

### [2.3. Переписать лямбда-функцию, генерирующую квадраты чисел из переменной типа list, через генератор списка.](https://repl.it/@Rakleed/programming-indepworkvar2-3)
```python
"""
    Автор: Моисеенко Павел, группа № 1, подгруппа № 2.

    Задание: переписать лямбда-функцию, генерирующую квадраты чисел из
    переменной типа list, через генератор списка.

"""

import random


def random_generator(numbers, maximum):
    random_list = []
    for i in range(numbers):
        random_list.append(random.randint(0, maximum))
    return random_list


def main():
    print("Программа генерирует случайный список элементов, а потом создаёт "
          "новый список из этих же чисел, возведённых в квадрат.")
    maximum = int(input("Введите верхнюю границу диапазона случайных "
                        "чисел: "))
    numbers = int(input("Введите количество случайных элементов: "))
    random_items = random_generator(numbers, maximum)
    print("Список случайно сгенерированных элементов: ", random_items)
    print("Список этих же элементов, возведённых в квадрат: ",
          list(map(lambda x: x * x, random_items)))


main()
```
![Result of indepworkvar2-3](https://github.com/python-basic/sem3-t2-Rakleed/blob/master/src/programming-indepworkvar2-3-result.png)
