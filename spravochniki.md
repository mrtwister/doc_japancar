# Справочники

При работе по протоколу в некоторых случаях \(например при добавлении или редактировании\) используются данные из справочников сервера. Эти справочники могут быть получены через три сервиса :

| Имя сервиса | Описание |
| :--- | :--- |
| parts\_place | Сервис выдачи справочника городов |
| parts\_syn | Сервис выдачи справочника запчастей |
| update\_path | Сервис выдачи справочников для всех разделов кроме раздела «Автозапчасти» |

### Справочник запчастей parts\_syn

Справочник выдается в текстовом формате где каждая строчка заканчивается переводом строки. В конце данных последней строкой идет слово end. Если его нет, возможно, что справочник загрузился не до конца и необходимо загрузить его заново.

Каждая строка справочника содержит три значения:

1. Первое значение – уникальный номер кода. 
2. Второе значение – Код запчасти.
3. Третье значение:
   * 1 - основной синоним 
   * 0 - не основной

Названия с одинаковыми кодами являются синонимами, т.е. по сути означают одно и то же, но названия имеют разные. Основной синоним – тот который используется для отображения на сайте.

Пример справочника запчастей:

```
"
1","АКС.115","спойлер","1"

"3","АКС.A16","дефендер","1"

"4","АКС.A18","дуга на крышу","1"

"6","АУД.177","динамик","1"

"8","АУД.A21","магнитофон","1"



……



"3719","КУЗ.001","петля капота","1"

"3830","КОН.114","кондиционер салона","1"

"3873","САЛ.745","уплотнительная резинка","1"

end
```

### Справочник городов parts\_place

Справочник выдается в текстовом формате где каждая строчка заканчивается переводом строки. В конце данных последней строкой идет слово end. Если его нет, возможно, что справочник загрузился не до конца и необходимо загрузить его заново.

Каждая строка справочника содержит два значения:

1. Код города
   .
2. Название города

Пример справочника городов:

```
"1","Владивосток"
"238","Архангельск"
"239","Барнаул"
"240","Бийск"
"241","Биробиджан"
"242","Благовещенск"
"243","Братск"
…

"365","Белгород"
"366","Каменск-Уральский"
"367","Фокино"
end
```

### Справочники для всех разделов кроме раздела "Автозапчасти"

Данный сервис позволяет выдать большое количество справочников необходимых для работы с сервером. Для работы с разделом «Автозапчасти» необходим только справочник по типам валют.

Ответ данного сервиса отличается от ответов первых двух. В данном случае выдается ответ строкой кодированной в формате base64. В этой строке содержится несколько комманд на языке SQL, которые должны быть выполнены в программе.

Целостность запроса проверяется по наличию слов @data\_start и @data\_end в тексте ответа.

Запрос справочника по типам валют:

```
http://www.japancar.ru/jpoffline/gate.php?ver_protocol=1.0.0&act=data_get&answer_type=plain&lang=RU&answer_data_type=insert&table_name=s_typecurrency&fields[]=id&fields[]=name&fields[]=name_bank&fields[]=name_ru&fields[]=name_en&unknown_value=no
```

Ответ

```
QGRhdGFfc3RhcnQKREVMRVRFIEZST00gc190eXBlY3VycmVuY3k7CklOU0VSVCBJTlRPIHNfdHlwZWN1cnJlbmN5KGlkLG5hbWUsbmFtZV9iYW5rLG5hbWVfcnUsbmFtZV9lbikgVkFMVUVTKCIxIiwiJCIsIiQiLCIkIiwiJCIpOwpJTlNFUlQgSU5UTyBzX3R5cGVjdXJyZW5jeShpZCxuYW1lLG5hbWVfYmFuayxuYW1lX3J1LG5hbWVfZW4pIFZBTFVFUygiMyIsIkVVUiIsIkVVUiIsIkVVUiIsIkVVUiIpOwpJTlNFUlQgSU5UTyBzX3R5cGVjdXJyZW5jeShpZCxuYW1lLG5hbWVfYmFuayxuYW1lX3J1LG5hbWVfZW4pIFZBTFVFUygiMiIsIkpQWSIsIkpQWSIsIkpQWSIsIkpQWSIpOwpJTlNFUlQgSU5UTyBzX3R5cGVjdXJyZW5jeShpZCxuYW1lLG5hbWVfYmFuayxuYW1lX3J1LG5hbWVfZW4pIFZBTFVFUygiNCIsItAuIiwi0C4iLCLQLiIsItAuIik7CkBkYXRhX2VuZAo=
```

Переведенный ответ из формата base64:

```
@data_start
DELETE FROM s_typecurrency;
INSERT INTO s_typecurrency(id,name,name_bank,name_ru,name_en) VALUES("1","$","$","$","$");
INSERT INTO s_typecurrency(id,name,name_bank,name_ru,name_en) VALUES("3","EUR","EUR","EUR","EUR");
INSERT INTO s_typecurrency(id,name,name_bank,name_ru,name_en) VALUES("2","JPY","JPY","JPY","JPY");
INSERT INTO s_typecurrency(id,name,name_bank,name_ru,name_en) VALUES("4","Р.","Р.","Р.","Р.");
@data_end
```



