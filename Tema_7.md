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
![image](https://github.com/user-attachments/assets/aed4791c-c095-48f6-ba49-067fd26ae5c6)
## Лабораторная работа №2
### Напишите программу, которая выведет только первую строку из вашего файла, при этом используйте конструкцию open()/close().
```python
f = open('input.txt','r', encoding='utf-8')
print(f.readline())
f.close()
```
### Результат.
![image](https://github.com/user-attachments/assets/afa97640-3175-44c6-a325-1e64aebbb5a3)
## Лабораторная работа №3
### Напишите программу, которая выведет все строки из вашего файла в массиве, при этом используйте конструкцию open()/close().
```python
f = open('input.txt','r', encoding='utf-8')
print(f.readline())
f.close()
```
### Результат.
![image](https://github.com/user-attachments/assets/c157d58c-c009-4ede-b3c7-d6e760e4e86f)
## Лабораторная работа №4
### Напишите программу, которая выведет все строки из вашего файла в массиве, при этом используйте конструкцию with open().
```python
with open('input.txt', encoding='utf-8') as f: 
    print(f.readlines())
```
### Результат.
![image](https://github.com/user-attachments/assets/2bbbfea1-4aeb-49cb-8145-91ec2c5c1dd1)
## Лабораторная работа №5
### Напишите программу, которая выведет каждую строку из вашего файла отдельно, при этом используйте конструкцию with open().
```python
with open('input.txt', encoding='utf-8') as f:
    for line in f:
        print(line)
```
### Результат.
![image](https://github.com/user-attachments/assets/d2dbd53d-1500-4e31-981e-b5b99141a59e)
## Лабораторная работа №6
### Напишите программу, которая будет добавлять новую строку в ваш файл, а потом выведет полученный файл в консоль. Вывод можно осуществлять любым способом. Обязательно проверьте сам файл, чтобы изменения в нем тоже отображались.
```python
with open('input.txt', 'a+', encoding='utf-8') as f:
    f.write('\nIm additional line')

with open('input.txt', 'r', encoding='utf-8') as f:
    result = f.readlines()
    print(result)
```
### Результат.
![image](https://github.com/user-attachments/assets/de677409-ed5b-4d64-9087-bdd1431f6249)
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
![image](https://github.com/user-attachments/assets/b0183e08-aeed-45e1-b891-b7265f92bbfd)
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
![image](https://github.com/user-attachments/assets/a5b078f4-00e5-4c32-ad02-c21a3fe71322)
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
![image](https://github.com/user-attachments/assets/b4dd92d2-90aa-46bd-8a45-fa9abf598773)
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
![image](https://github.com/user-attachments/assets/2df7e1a0-a624-438b-bad4-85afb6389722)
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
![image](https://github.com/user-attachments/assets/55461946-5ffe-4aab-ad6b-af76ade441cb)
![image](https://github.com/user-attachments/assets/2c1856be-1c93-4af1-900e-9a9f43281dde)
## Выводы
Я научился считывать текст из файла и подсчитывать количество слов. Также я узнал, как находить самое часто встречающееся слово.
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
![image](https://github.com/user-attachments/assets/17711800-6b39-4f6c-84d4-514423df475b)
![image](https://github.com/user-attachments/assets/038f5c8a-c57e-4499-83c5-95fb514e39f5)
## Выводы
Я понял, как создать систему учёта расходов, которая позволяет вводить данные через консоль и сохранять их в файл.
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
![image](https://github.com/user-attachments/assets/7f3aba12-087b-4b74-9fb4-07067405db0f)
## Выводы
Я научился анализировать текстовые данные, подсчитывая количество букв, слов и строк в файле.
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
![image](https://github.com/user-attachments/assets/f1724a61-359b-4240-8f38-2799b6f79114)
## Выводы
Я узнал, как заменять запрещённые слова в тексте на символы (например, звёздочки), что может быть полезно для создания фильтров в текстовых приложениях.
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
![image](https://github.com/user-attachments/assets/037b6a61-088b-47a1-a8f0-fd9a22ca09c9)
![image](https://github.com/user-attachments/assets/f9fb839d-dd81-48f3-9a1f-e61c69a56424)
## Выводы
Я научился подсчитывать количество слов в каждой строке текста и записывать результаты в новый файл. Это помогает структурировать данные и анализировать текст более детально.
## Общие выводы по теме
В ходе выполнения этих задач я освоил основные методы работы с текстовыми файлами в Python. Я научился считывать, обрабатывать и записывать текстовые данные, а также выполнять различные анализы и манипуляции с текстом.
