# Вопросы на интервью

#### Как микросервисы могут общаться друг с другом?

http, polling, uqeue

#### Какие виды sql injection вы знаете?

слепые и т.д.

#### Что должно содержаться в логах?

дата, уровень, модуль

#### Чем git fetch отличается от git pull?

fetch забирает, а pull забирает и мержит

#### Как создать ветку в git?

git checkout -b branch_name

#### Как вызвать команду при сборке докер контейнера?

RUN

#### Зачем в докере делает команда CMD?

То, что в этой команде, запустится при старте контейнера

#### Где валидировать json данные, которые пришли в django?

Если у нас django rest framework, то в сериалайзере

#### Зачем нужны генераторы (yeld)?

Для вычисления следующего значения только в момент вызова, а не для просчета всех значений предварительно.

#### Задача по алгоритмам #0

```
a = [1, 3, 4]
b = [1, 4, 5]
c = [2, 7, 1]
n = 4

def check(a, b, c, n):
    # реализовать функцию check, которая получает 3 массива a, b, c и число n
    # возвращает True если есть хоть одна комбинация, где сумма чисел по одному числу каждом массиве равна n
    # в данном примере должно быть True, т.к. a[0]+b[0]+c[0]=1+1+2=4
    return True or False
```

Реализация:

```
def check(a, b, c, n):
    for i_a in a:
        for i_b in b:
            for i_c in c:
                if i_a + i_b + i_c == n:
                    return True
    return False

print(check(a, b, c, n))
```

Какая алгоритмическая сложность данной задачи? o(n^3)

Как можно ускорить алгоритм?

```
def check(a, b, c, n):
    for i_a in a:
        if i_a > n:
            continue
        for i_b in b:
            if i_a + i_b > n:
                continue
            for i_c in c:
                if i_a + i_b + i_c == n:
                    return True
    return False

print(check(a, b, c, n))
```

Как можно снизить алгоритмическую сложность?

```
def check(a, b, c, n):
    c_set = set(c)
    for i_a in a:
        for i_b in b:
            if (n - i_a - i_b) in c_set:
                return True
    return False

print(check(a, b, c, n))
```

#### Как устроен HTTP?

#### Как устроен HTTPS и в чем разница?

#### Можно ли на одном сокете держать HTTPS сервер для разных доменов?

#### Что такое CI/CD?

#### Когда должны выполнятся миграции в базе при CI/CD?

#### Что такое CAP теорема?

#### Какие буквы из CAP есть в postgresql, а какие в mongodb?

postgresql CP, mongodbAP

#### Как в django выполнить миграцию не в транзакции?

#### Что такое сигналы в django? Какой паттерн программирования они используют?

observer

#### Если в postgresql есть таблица с разными полями и по этим полям есть отдельные индексы, как будет выполняться фильтрация сразу по нескольким полям?

индексы + битовая маска

#### Интернет реализует семиуровневую модель OSI?

#### TCP/IP реализован на основе OSI? 

#### В TCP можно заменить (согласно OSI) нижестоящий IP на какой-то другой протокол?

#### Назовите и опишите три нормальных формы в базах данных.

#### С помощью какой структуры данных реализован словарь в python? Какова его алгоритмическая сложность?

HashTable + (B-Tree or OpenAddressing?). 

В лучшем случае HashTable без коллизий, тогда Search/Insertion/Deletion Θ(1). 

Когда HashTable попадает на коллизию, используется (B-Tree or OpenAddressing?), тогда Search/Insertion/Deletion Θ(log(n)).

https://www.bigocheatsheet.com/

#### Напишите декоратор, который логирует название функции, параметры, результат

```
def log_me(func):
    def wrapper(*args, **kwargs):
        value = func(*args, **kwargs)
        values = [str(a) for a in args]
        values += [f"{k}={kwargs[k]}" for k in kwargs]
        values = ', '.join(values)
        print(f"{func.__name__}({values}) = {value}")
    return wrapper


@log_me
def foo(a, b, c=2):
    return a + b + c


foo(1, b=2, c=3)
# output: foo(1, b=2, c=3) = 6

```

#### Реализуйте LinkedList на python
