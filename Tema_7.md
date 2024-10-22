# Тема 7. Работа с файлами(ввод, вывод).
Отчет по Теме #7 выполнил:
- Куличихин Андрей Юрьевич
- ПИЭ-22-1

| Задание | Лаб_раб | Сам_раб |
| ------ | ------ | ------ |
| Задание 1 | + | + |
| Задание 2 | + | + |
| Задание 3 | + | + |
| Задание 4 | + | + |
| Задание 5 | + | + |
| Задание 6 | + |   |
| Задание 7 | + |   |
| Задание 8 | + |   |
| Задание 9 | + |   |
| Задание 10 | + |   |

знак "+" - задание выполнено; знак "-" - задание не выполнено;

Работу проверили:
- к.э.н., доцент Панов М.А.

## Лабораторная работа №1
### Составьте текстовый файл и положите его в одну директорию с программой на Python. Текстовый файл должен состоять минимум из двух строк.
### Результат.

## Лабораторная работа №2
### Напишите программу, которая выведет только первую строку из вашего файла, при этом используйте конструкцию open()/close().
```python
f = open('input.txt','r', encoding='utf-8')
print(f.readline())
f.close()
```
### Результат.

## Лабораторная работа №3
### Напишите программу, которая выведет все строки из вашего файла в массиве, при этом используйте конструкцию open()/close().
```python
f = open('input.txt','r', encoding='utf-8')
print(f.readline())
f.close()
```
### Результат.

## Лабораторная работа №4
### Напишите программу, которая выведет все строки из вашего файла в массиве, при этом используйте конструкцию with open().
```python
with open('input.txt', encoding='utf-8') as f: 
    print(f.readlines())
```
### Результат.

## Лабораторная работа №5
### Напишите программу, которая выведет каждую строку из вашего файла отдельно, при этом используйте конструкцию with open().
```python
with open('input.txt', encoding='utf-8') as f:
    for line in f:
        print(line)
```
### Результат.

## Лабораторная работа №6
### Напишите программу, которая будет добавлять новую строку в ваш файл, а потом выведет полученный файл в консоль. Вывод можно осуществлять любым способом. Обязательно проверьте сам файл, чтобы изменения в нем тоже отображались.
```python
with open('input.txt', 'a+', encoding='utf-8') as f:
    f.write('\nIm additional line')

with open('input.txt', 'r') as f:
    result = f.readlines()
    print(result)
```
### Результат.

## Лабораторная работа №7
### Напишите программу, которая перепишет всю информацию, которая была у вас в файле до этого, например напишет любые данные из произвольно вами составленного списка. Также не забудьте проверить что измененная вами информация сохранилась в файле.
```python
lines = ['one', 'two', 'three'] 
with open('input.txt', 'w', encoding='utf-8') as f:
    for line in lines:
        f.write('\nCycle run ' + line)
    print('Done!')
```
### Результат.

## Лабораторная работа №8
### Выберите любую папку на своем компьютере, имеющую вложенные директории. Выведите на печать в терминал ее содержимое, как и всех подкаталогов при помощи функции print_docs(directory).
```python
import os

def print_docs(directory):
    all_files = os.walk(directory)
    for catalog in all_files:
        print(f'Папка {catalog[0]} содержит: ')
    print(f'Директории: {",".join([folder for folder in catalog[1]])}') 
    print(f'Файлы: {", ".join([file for file in catalog[2]])}') 
    print('-' * 40)
print_docs('C:\Python_proj\Tema_6')
```
### Результат.

## Лабораторная работа №9
### Документ «input.txt» содержит следующий текст:
### Приветствие
### Спасибо
### Извините
### Пожалуйста
### До свидания
### Ты готов?
### Как дела?
### С днем рождения!
### Удача!
### Я тебя люблю.
### Требуется реализовать функцию, которая выводит слово, имеющее максимальную длину (или список слов, если таковых несколько). Проверьте работоспособность программы на своем наборе данных.
```python
def longest_words(file):
    with open(file, encoding='utf-8') as f:
        words = f.read().split()
        max_length = len(max(words, key=len)) 
        for word in words:
            if len(word) == max_length:
                sought_words = word
        if len(sought_words) == 1: 
            return sought_words[0] 
        return sought_words
print(longest_words('input.txt'))
```
### Результат.

## Лабораторная работа №10
### Требуется создать csv-файл «rows_300.csv» со следующими столбцами:
### • № - номер по порядку (от 1 до 300);
### • Секунда – текущая секунда на вашем ПК;
### • Микросекунда – текущая миллисекунда на часах.
### Для наглядности на каждой итерации цикла искусственно приостанавливайте скрипт на 0,01 секунды.
```python
import csv
import datetime
import time

with open('rows_300.csv','w', encoding='utf-8', newline='') as f: 
    writer = csv.writer(f)
    writer.writerow(['№', 'Секунда','Микросекунда'])
    for line in range(1, 301):
        writer.writerow([line, datetime.datetime.now().second, datetime.datetime.now().microsecond])
    time.sleep(0.01)
```
### Результат.

## Самостоятельная работа №1
### Найдите в интернете любую статью (объем статьи не менее 200 слов), скопируйте ее содержимое в файл и напишите программу, которая считает количество слов в текстовом файле и определит самое часто встречающееся слово. Результатом выполнения задачи будет: скриншот файла со статьей, листинг кода, и вывод в консоль, в котором будет указана вся необходимая информация.
```python
from collections import Counter
import re
def word_count(filename):
    with open(filename, 'r', encoding='utf-8') as file:
        text = file.read().lower()
        words = re.findall(r'\b\w+\b', text)
        word_frequency = Counter(words)
        most_common_word = word_frequency.most_common(1)[0]
        return len(words), most_common_word
word_count, most_common = word_count('stat.txt')
print(f"Всего слов: {word_count}")
print(f"Самое частое слово: {most_common[0]} ({most_common[1]} раз)")
```
### Результат.

## Выводы

## Самостоятельная работа №2
### У вас появилась потребность в ведении книги расходов, посмотрев все существующие варианты вы пришли к выводу что вас ничего не устраивает и нужно все делать самому. Напишите программу для учета расходов. Программа должна позволять вводить информацию о расходах, сохранять ее в файл и выводить существующие данные в консоль. Ввод информации происходит через консоль. Результатом выполнения задачи будет: скриншот файла с учетом расходов, листинг кода, и вывод в консоль, с демонстрацией работоспособности программы.
```python
def add_expense(filename, expense, amount):
    with open(filename, 'a', encoding='utf-8') as file:
        file.write(f"{expense}: {amount}\n")
def show_expenses(filename):
    with open(filename, 'r', encoding='utf-8') as file:
        for line in file:
            print(line.strip())
filename = 'rash.txt'
while True:
    action = input("Введите 'добавить', чтобы добавить расход, или 'показать', чтобы вывести все расходы (или 'выход', чтобы завершить): ")
    if action == 'добавить':
        expense = input("Введите название расхода: ")
        amount = input("Введите сумму расхода: ")
        add_expense(filename, expense, amount)
    elif action == 'показать':
        show_expenses(filename)
    elif action == 'выход':
        break
```
### Результат.

## Выводы

## Самостоятельная работа №3
### Имеется файл input.txt с текстом на латинице. Напишите программу, которая выводит следующую статистику по тексту: количество букв латинского алфавита; число слов; число строк.
### • Текст в файле:
### Beautiful is better than ugly.
### Explicit is better than implicit.
### Simple is better than complex.
### Complex is better than complicated.
### • Ожидаемый результат:
### Input file contains:
### 108 letters
### 20 words
### 4 lines
```python
def text_statistics(filename):
    with open(filename, 'r', encoding='utf-8') as file:
        text = file.read()
        letters = sum(c.isalpha() for c in text)
        words = len(text.split())
        lines = len(text.splitlines())
        return letters, words, lines
letters, words, lines = text_statistics('analiz.txt')
print(f"Файл содержит:\n{letters} букв\n{words} слов\n{lines} строк")
```
### Результат.

## Выводы

## Самостоятельная работа №4
### Напишите программу, которая получает на вход предложение, выводит его в терминал, заменяя все запрещенные слова звездочками * (количество звездочек равно количеству букв в слове). Запрещенные слова, разделенные символом пробела, хранятся в текстовом файле input.txt. Все слова в этом файле записаны в нижнем регистре. Программа должна заменить запрещенные слова, где бы они ни встречались, даже в середине другого слова. Замена производится независимо от регистра: если файл input.txt содержит запрещенное слово exam, то слова exam, Exam, ExaM, EXAM и exAm должны быть заменены на ****.
### • Запрещенные слова:
### hello email python the exam wor is
### • Предложение для проверки:
### Hello, world! Python IS the programming language of thE future. My
### EMAIL is....
### PYTHON is awesome!!!!
### • Ожидаемый результат:
### *****, ***ld! ****** ** *** programming language of *** future. My
### ***** **....
### ****** ** awesome!!!!
```python
import re
def censor_text(text, banned_words):
    for word in banned_words:
        text = re.sub(rf'(?i){word}', '*' * len(word), text)
    return text
with open('cens.txt', 'r', encoding='utf-8') as f:
    banned_words = f.read().split()
text = input("Введите предложение: ")
censored_text = censor_text(text, banned_words)
print(censored_text)
```
### Результат.

## Выводы

## Самостоятельная работа №5
### Программа для чтения и сортировки строк по длине.
```python
def sort_lines_by_length(filename):
    with open(filename, 'r') as file:
        lines = file.readlines()
        sorted_lines = sorted(lines, key=len)
        return sorted_lines
sorted_lines = sort_lines_by_length('sort.txt')
for line in sorted_lines:
    print(line.strip())
```
### Результат.

## Выводы

## Общие выводы по теме
