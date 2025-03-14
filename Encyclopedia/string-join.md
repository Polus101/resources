# Метод строки join

### Синтаксис:

```python
str.join(iter)
```
Данный метод строки создает(возвращает) одну большую строку из контейнера объектов строкового типа данных, соединяя их через некоторый разделитель.
- *str* - параметр, строковый тип данных, который являет собой разделитель для будущей строки;
- *join* - непосредственно метод;
- *iter* - параметр, итерируемый контейнер с объектами в виде строкового типа данных.

### Зачем нужен и где применяется:

Во многих ситуациях применение метода .join() облегчает работу, а иногда даже ускоряет работу программы. К примеру, когда необходимо сложить или сгруппировать строки в одном выводе.

#### Пример кода без .join():
```python
line = "Продукты к покупке: "
products = ["яблоки", "бананы", "колбаса", "сыр", "молоко"]

for product in products:
  line += f"\n- {product}"
  
print(line)
```

#### Пример кода с .join():
```python
line = "Продукты к покупке: "
products = ["яблоки", "бананы", "колбаса", "сыр", "молоко"]

line = line + "\n- ".join(products)

print(line)
```

В обоих случаях вывод составит:
```
Продукты к покупке: 
- яблоки
- бананы
- колбаса
- сыр
- молоко
```

