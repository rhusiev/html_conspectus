# Template code
```python
from typing import Protocol

class MyProtocol(Protocol):
    def method_one(self):
        ...

    def method_two(self):
        ...


def my_function(object_with_those_methods: MyProtocol):
    pass
```

# Пояснення
Ти задаєш методи, які ти очікуєш, що будуть в об'єкті, який до тебе прийде

Приходити можуть об'єкти і з більшою кількістю методів, але ці два обов'язкові
Через успадкування від протоколу, воно не дасть закинути об'єкти без цих методів

Сам об'єкт не має бути класу `MyProtocol`

Тобто тут ми використовуємо [[Качина Типізація|Качину Типізацію]]

# Приклад
```python
from typing import Protocol

class Connectable(Protocol):
    def connect(self, key: str):
        ...


class Cloud:
    def __init__(self):
        self.key = "secret key"

    def connect(self, key: str):
        if key == self.key:
            print("Connected")
        else:
            print("Wrong key")


def connect_to_something(connectable: Connectable):
    connectable.connect("secret key")
```

У функції ми не очікуємо саме `Cloud`, а просто щось до чого можна під'єднатися з ключем
