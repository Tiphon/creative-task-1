# Pillow
Pillow- Билблитека в python, c помощью которой можно обрабатывать изображения
## что умеет эта библиотека:
1.  открывать изображения
2.  редактирорвать изображения
3.  обрезать картинку
4.  выводить форматы изображений(jpeg, png...)  
## Версии библитотеки и совместимость с разными версиями питона:

|Python          | 3.12    | 3.11   | 3.10   | 3.9   | 3.8   | 3.7   | 3.6   | 3.5   |
|----------------|---------|--------|--------|-------|-------|-------|-------|-------|
|Pillow >= 10.1  | да      | да     | да     | да    | да    |       |       |       |
| Pillow 10.0    |         | да     | да     | да    | да    |       |       |       |
|Pillow 9.3-9.5  |         | да     | да     | да    | да    | да    |       |       |
|Pillow 9.0-9.2  |         |        | да     | да    | да    | да    |       |       |
|Pillow 8.3.2-8.4|         |        | да     | да    | да    | да    | да    |       |
|Pillow 8.0-8.3.1|         |        |        | да    | да    | да    | да    |       |
|Pillow 7.0-7.2  |         |        |        |       | да    | да    | да    | да    |

# __дата создания: 2009 год__
## Поворот картинки
импортировать библиотеку можно с помощью 
```python
from PIL import Image
```
для примера берём картинку

![alt text](https://github.com/user-attachments/assets/516bdb06-c260-48d2-bebf-ebf2730cb4e6)

```python
from PIL import Image
image = Image.open("python.jpeg")
rotated_image = image.rotate(45)
rotated_image.save("rotated.jpeg")
```

![alt text](https://github.com/user-attachments/assets/552c0e55-4b77-482a-ad3d-4607d404a659)

c помощью функции `image.rotate` мы можем повернуть картинку на указанное кол-во градусов, в этом случае на 45градусов

## Вывод формата картинки
Для примера берём ту же картинку `python.jpeg` корорую мы поворачивали, и используем функцию `.format`
```python
from PIL import Image
image = Image.open("python.jpeg")
print(image.format)
```
и мы получим вывод формата, в этом случае это формат `JPEG`

## Копия изображения 
С помощью  функции `.save` можно сохранить новую копию изображения. Пример:

```python
from PIL import Image
image = Image.open("python.jpeg")
image.save("python2.jpeg")
```
у нас получилась копия файла.
## Обрезать изображение
с помощью функции `crop()` можно обрезать изображение по координатам пикселей
```python
from PIL import Image
image = Image.open("python.jpeg")
coordinates = (100, 0, image.width, image.height) # вводим координаты, которые хотим обрезать
cut = image.crop(coordinates) # обрезаем
cut.save("cut.jpeg")
```
результат:

![alt text](https://github.com/user-attachments/assets/c6c467bc-8b93-4dfa-ad81-336f9f1007a7)

## Изменение размера изображения
есть 2 способа изменения размера картинки:1
1.  `resize` : изменение размера картинки __без сохранения пропорций__
2.  `thumbnail` : изменение размера картинки с __сохранением пропорций__

рассмотрим способ `thumbnail`
```python
image = Image.open("python.jpeg")
print(image.size)  #выводим размер изображения, тут он 225 на 225 пикселей
image.thumbnail((200, 200))   #указываем желаемое количество пискелей
print(image.size)  #выводим уменьшенный размер изображения, тут он 200 на 200 пикселей
```

## Наложение изображений друг на друга
для этого используется функция `Image.blend()`
для работы нудны 3 аргумента:
1.  1-ая картинка
2.  2-ая картинка
3.  коэфицент прозрачности

пример:
берём 2 картинки:
уже известную

![alt text](https://github.com/user-attachments/assets/516bdb06-c260-48d2-bebf-ebf2730cb4e6)

и новую

![alt text](https://github.com/user-attachments/assets/3f34b4b5-fb5b-4b5f-9265-30a84650f58b)

```python
from PIL import Image
image1 = Image.open("python.jpeg")
print(image.size) # проверка размера изображеня для подгона её размера
image2 = Image.open("code.jpeg")
print(image2.size) # проверка размера изображеня для подгона её размера
image2.thumbnail((225, 225)) # подгоняем 2 картинку под размер первой
result = Image.blend(image1, image2, 0.5)  # Получится картинка, сложенная из двух
result.save("result.jpeg")
```

результат: 

![alt text](https://github.com/user-attachments/assets/a74e39f6-3ebf-4224-ab7c-f9419236f73d)


### конец
# :+1:
