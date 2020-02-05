# MongoDB

## Типы

* **String**: строковый тип данных, как в приведенном выше примере (для строк используется кодировка UTF-8)
* **Array** (массив): тип данных для хранения массивов элементов
* **Binary data** (двоичные данные): тип для хранения данных в бинарном формате
* **Boolean**: булевый тип данных, хранящий логические значения TRUE или FALSE, например, {"married": FALSE}
* **Date**: хранит дату в формате времени Unix
* **Double**: числовой тип данных для хранения чисел с плавающей точкой
* **Integer**: используется для хранения целочисленных значений, например, {"age": 29}
* **JavaScript**: тип данных для хранения кода javascript
* **Min key/Max key**: используются для сравнения значений с наименьшим/наибольшим элементов BSON
* **Null**: тип данных для хранения значения Null
* **Object**: строковый тип данных, как в приведенном выше примере
* **ObjectID**: тип данных для хранения id документа
* **Regular expression**: применяется для хранения регулярных выражений
* **Symbol**: тип данных, идентичный строковому. Используется преимущественно для тех языков, в которых есть специальные символы.
* **Timestamp**: применяется для хранения времени
---


1. Используем
```MongoDB
use users_test
```
2. Добавление данных

    * insertOne(): добавляет один документ
    * insertMany(): добавляет несколько документов
    * insert(): может добавлять как один, так и несколько документов

```MongoDB
db.users_test.insertOne({"name": "Tom", "age": 28, languages: ["english", "spanish"]})
db.users_test.insertOne({"_id": 123457, "name": "Tom", "age": 28, languages: ["english", "spanish"]})
db.users_test.find().pretty()
```

Результат

```js
{
        "_id" : ObjectId("5e3ad868b6a7205fe1741891"),
        "name" : "Tom",
        "age" : 28,
        "languages" : [
                "english",
                "spanish"
        ]
}
{
        "_id" : 123457,
        "name" : "Tom",
        "age" : 28,
        "languages" : [
                "english",
                "spanish"
        ]
}
```

```MongoDB
db.users_test.insertMany([{"name": "Bob", "age": 26, languages: ["english", "frensh"]}, 
{"name": "Alice", "age": 31, languages:["german", "english"]}])
db.users_test.find()
```

Результат

```js
{ "_id" : ObjectId("5e3ad868b6a7205fe1741891"), "name" : "Tom", "age" : 28, "languages" : [ "english", "spanish" ] }
{ "_id" : 123457, "name" : "Tom", "age" : 28, "languages" : [ "english", "spanish" ] }
{ "_id" : ObjectId("5e3ad907b6a7205fe1741892"), "name" : "Bob", "age" : 26, "languages" : [ "english", "frensh" ] }
{ "_id" : ObjectId("5e3ad907b6a7205fe1741893"), "name" : "Alice", "age" : 31, "languages" : [ "german", "english" ] }
```

```MongoDB
document=({"name": "Bill", "age": 32, languages: ["english", "french"]})
db.users_test.insert(document)
db.users_test.find()
```

Результат

```js
{ "_id" : ObjectId("5e3ad868b6a7205fe1741891"), "name" : "Tom", "age" : 28, "languages" : [ "english", "spanish" ] }
{ "_id" : 123457, "name" : "Tom", "age" : 28, "languages" : [ "english", "spanish" ] }
{ "_id" : ObjectId("5e3ad907b6a7205fe1741892"), "name" : "Bob", "age" : 26, "languages" : [ "english", "frensh" ] }
{ "_id" : ObjectId("5e3ad907b6a7205fe1741893"), "name" : "Alice", "age" : 31, "languages" : [ "german", "english" ] }
{ "_id" : ObjectId("5e3ad9bcb6a7205fe1741895"), "name" : "Bill", "age" : 32, "languages" : [ "english", "french" ] }
```

Удаляем БД
```MongoDB
db.users_test.drop()
```

3. Выборка

Для старта необходимо создать бд.
```MongoDB
load("D:/Projects/MongoDB/MOCK_DATA.js")
```
