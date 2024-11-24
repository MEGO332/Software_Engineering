# Тема 11. Итераторы и генераторы
Отчет по Теме #11 выполнил(а):
- Куличихин Андрей Юрьевич
- ПИЭ-22-1

| Задание | Лаб_раб | Сам_раб |
| ------ | ------ | ------ |
| Задание 1 | + | + |
| Задание 2 | + | + |
| Задание 3 | + |
| Задание 4 | + |
| Задание 5 | + |


знак "+" - задание выполнено; знак "-" - задание не выполнено;

Работу проверили:
- к.э.н., доцент Панов М.А.

## Лабораторная работа №1
### Простой итератор, но у него нет гибкой настройки, например его нельзя развернуть. Он работает просто как next(), но нет prev()
```python
numbers = [0, 1, 2, 3, 4, 5]
for item in numbers:
    print(item)
```
### Результат.
![image](https://github.com/user-attachments/assets/042eb5d0-232f-43ba-9820-fa4aedb94131)
## Лабораторная работа №2
### Класс итератор с гибкой настройкой и удобными применением
```python
class CountDown:
    def __init__(self, start):
        self.count = start + 1

    def __iter__(self):
        return self

    def __next__(self):
        self.count -= 1
        if self.count < 0:
            raise StopIteration
        return self.count

if __name__ == '__main__':
    counter = CountDown(5)
    for i in counter:
        print(i)
```
### Результат.
![image](https://github.com/user-attachments/assets/cf0de633-2adb-4c72-bfb2-6ed59caba3bb)
## Лабораторная работа №3
### Генератор списка
```python
a = [i ** 2 for i in range(1, 5)]

print('a - ', a)
for i in a:
    print(i)

print('iter(a) - ', iter(a))
for i in a:
    print(i)
```
### Результат.
![image](https://github.com/user-attachments/assets/ddc19741-54a6-4c6f-a5c4-81a17bdf83df)
## Лабораторная работа №4
### Выражения генераторы
```python
b = (i ** 2 for i in range(1, 5))
print(b)  # вывод не такой, как у генератора списков
print('first')
for i in b:
    print(i)
print('second')
# из-за особенностей выражений генераторов,
# они не будут выводиться больше одного раза
for i in b:
    print(i)
```
### Результат.
![image](https://github.com/user-attachments/assets/e2ef59cf-63c8-44c1-96bb-9b1ce51e5430)
## Лабораторная работа №5
### Такой же счетчик, как и в первом задании, только это генератор и использует yield
```python
def countdown(count):
    while count >= 0:
        yield count
        count -= 1

if __name__ == '__main__':
    counter = countdown(5)
    for i in counter:
        print(i)
```
### Результат.
![image](https://github.com/user-attachments/assets/77cc3c2b-7871-4b55-881a-89d7cb4d9ed8)
## Самостоятельная работа №1
### Вас никак не могут оставить числа Фибоначчи, очень уж они вас заинтересовали. Изучив новые возможности Python вы решили реализовать программу, которая считает числа Фибоначчи при помощи итераторов. Расчет начинается с чисел 1 и 1. Создайте функцию fib(n), генерирующую n чисел Фибоначчи с минимальными затратами ресурсов. Для реализации этой функции потребуется обратиться к инструкции yield (Она не сохраняет в оперативной памяти огромную последовательность, а дает возможность “доставать” промежуточные результаты по одному). Результатом решения задачи будет листинг кода и вывод в консоль с числом Фибоначчи от 200.
```python
def fib(n):
    a, b = 1, 1
    for _ in range(n):
        yield a
        a, b = b, a + b
fibonacci = list(fib(200))
print(fibonacci[-1])
```
### Результат.
![image](https://github.com/user-attachments/assets/ed38ad8d-3318-4f7a-9024-fa8f373965bf)
## Выводы:
Использование yield показало, как можно эффективно генерировать последовательности без перегрузки памяти, извлекая данные по мере необходимости.
## Самостоятельная работа №2
### К коду предыдущей задачи добавьте запоминание каждого числа Фибоначчи в файл “fib.txt”, при этом каждое число должно находиться на отдельной строчке. Результатом выполнения задачи будет листинг кода и скриншот получившегося файла.
```python
def fib(n):
    a, b = 1, 1
    for _ in range(n):
        yield a
        a, b = b, a + b
with open("fib.txt", "w") as file:
    for number in fib(200):
        file.write(f"{number}\n")
with open("fib.txt", "r") as file:
    print(file.read())
```
### Результат.
![image](https://github.com/user-attachments/assets/b951c173-1266-4dbc-b760-ca28e204be5b)
![image](https://github.com/user-attachments/assets/85c092f8-cf08-437d-b938-3651d6261060)
![image](https://github.com/user-attachments/assets/3ac2b9e4-686e-44a5-96a2-c6b70ef9ddeb)
## Выводы:
Научился сохранять результаты генерации в файл, что удобно для анализа и дальнейшего использования данных.
## Общие выводы по теме
Я узнал, как использовать итераторы для работы с большими последовательностями и сохранять результаты в удобной форме.
