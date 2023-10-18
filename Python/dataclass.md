# Template code
```python
from dataclasses import dataclass

@dataclass
class MyDataclass:
    field_one: str
    field_two: str
```

# Пояснення
Корисний, коли щось більше за просто словник, але хочеться простенького класу, який в основному просто зберігає дані та якось ними просто маніпулює

Не треба `__init__`, `__repr__` і багатьох інших дандерів. Вони автоматично генеруються

`__init__` - одразу як `__init__(field_one: str, field_two: str)`
`__repr__` - `MyDataclass(field_one=<value_one>, field_two=<value_two>)`

# Можливості
## Дефолтні значення
```python
    field_one: bool = True  # Default value = True
```

```python
from dataclasses import field
...
    field_two: list = field(default_factory=list) 
```

У другому випадку нам треба задавати так, бо якщо просто написати `field_two = []`, то воно його порахує із самого початку, і список буде однаковим для всіх об'єктів
А через те, що список змінюваний, то це призведе до проблем

`default_factory` визначає функцію, яка буде викликатися при кожному створенні. Тобто туди не просто тип вставляти можна

## Щоб не можна було задавати при створенні об'єкта
```python
    id: int = field(init=False, default_factory=random.random)
```

Тепер не вийде зробити:
```python
MyDataclass(..., id=0.2143)
```

## Виконати код після створення об'єкта, не задавати атрибут при ініті
Можна запихати код в метод `__post_init__`
Щоб атрибут не задавався при ініті, можна зробити `field(init=False)`

Наприклад:
```python
@dataclass
class Person:
    name: str
    email: str
    _searchable_str: str = field(init=False)  # An str that contains info, by which a person can be found in a database

    def __post_init__(self):
        self._searchable_str = f"{self.name}, {self.email}"
```

## Не показувати в `__repr__`
```python
...
    _searchable_string: str = field(init=False, repr=False)
...
```
`init` з попереднього
`repr` робить, аби не було в `__repr__` репрезентації

## Можливість запихання в словник(загалом хешування)
```python
@dataclass(frozen=True)
```
Тоді, правда, не можна об'єкти змінювати

## Зробити швидшим через `__slots__`
`__slots__` використовують у класах, щоб задати певний набір атрибутів, і інших не можна додавати. Виходить швидше, бо по-іншому зберігається

Щоб таким зробити датаклас треба
```python
@dataclass(slots=True)
```


# Приклад
```python
from random import choice

from dataclasses import dataclass


def generate_id() -> str:
    return "".join(random.choice("abcdefghijklmnopqrstuvwxyz") for _ in range(10))


@dataclass
class Person:
    name: str
    address: str
    active: bool = True
    email_addresses: list[str] = field(default_factory=list)
    id: str = field(init=False, default_factory=generate_id, repr=False)
    username: str = field(init=False)

    def __post_init__(self):
        self.username = f"{self.name}#{self.id}"
```