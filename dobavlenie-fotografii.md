# Функция ins\_f. Добавление фотографий.

| Название параметра | Значение | Описание |
| :--- | :--- | :--- |
| s\_sn | набор символов длиной не более 255 символов. | код программы |
| p\_version | текст длиной не более 255 символов | версия программы |
| action | ins\_f | действие выполняемое с данными |
| id | набор символов длиной не более 255 символов. | уникальный номер запчасти в программе |
| N\_O | O,N | Новая/Контрактная |
| photo\[\] | строка base64 | Фотография, закодированная в формат base64. Таких параметров в теле запроса может быть неограниченное количество. Сервер при получении этих параметров будет рассматривать их как массив. Ограничение накладывается на общий объем данных в запросе – не более 2 МБ. Если есть прямая ссылка на картинку, можно вместо строки указать ссылку на картинку и она будет добавлена точно так же. |

Вид POST запроса:

```
s_sn=34itlwk87er9j&p_version=3.0.25&action=ins_f&id=000000002&N_O=O&photo[]=/9j/4AAQSkZJRgABAQAAAQABAAD/2wBDAAMCAgMCAgMDAwMEAwMEBQgFBQQEBQoHBwYIDAoMDAsK
CwsNDhIQDQ4RDgsLEBYQERMUFRUVDA8XGBYUGBIUFRT/2wBDAQMEBAUEBQkFBQkUDQsNFBQUFBQU
FBQUFBQUFBQUFBQUFBQUFBQUFBQUFBQUFBQUFBQUFBQUFBQUFBQUFBQUFBT/wAARCAJYAyADASIA
AhEBAxEB/8QAHwAAAQUBAQEBAQEAAAAAAAAAAAECAwQFBgcICQoL/8QAtRAAAgEDAwIEAwUFBAQA
AAF9AQIDAAQRBRIhMUEGE1FhByJxFDKBkaEII0KxwRVS0fAkM2JyggkKFhcYGRolJicoKSo0NTY3
ODk6Q0RFRkdISUpTVFVWV1hZWmNkZWZnaGlqc3R1dnd4eXqDhIWGh4iJipKTlJWWl5iZmqKjpKWm
p6ip 
... 
&photo[]=/9j/4AAQSkZJRgABAQAAAQABAAD/2wBDAAMCAgMCAgMDAwMEAwMEBQgFBQQEBQoHBwYIDAoMDAsK
CwsNDhIQDQ4RDgsLEBYQERMUFRUVDA8XGBYUGBIUFRT/2wBDAQMEBAUEBQkFBQkUDQsNFBQUFBQU
FBQUFBQUFBQUFBQUFBQUFBQUFBQUFBQUFBQUFBQUFBQUFBQUFBQUFBQUFBT/wAARCAJYAyADASIA
AhEBAxEB/8QAHwAAAQUBAQEBAQEAAAAAAAAAAAECAwQFBgcICQoL/8QAtRAAAgEDAwIEAwUFBAQA
AAF9AQIDAAQRBRIhMUEGE1FhByJxFDKBkaEII0KxwRVS0fAkM2JyggkKFhcYGRolJicoKSo0NTY3
ODk6Q0RFRkdISUpTVFVWV1hZWmNkZWZnaGlqc3R1dnd4eXqDhIWGh4iJipKTlJWWl5iZmqKjpKWm
p6ip ...
```

Ответ:

```xml
<?xml version="1.0" encoding="windows-1251"?>
<jcanswer>
    <message>
        <result >SUCCESS</result>
        <code >N0000_SERVICE_SUCCESS</code>
        <action >ins_f</action>
        <group id="main" area="parts"><![CDATA[Система обработки данных]]></group>
        <datetime >2010-04-15 16:29:23</datetime>
        <text ><![CDATA[Фотография добавлена]]></text>
        <notice id="N0500_RESULT_NOTICE" ><![CDATA[Добавлено 2 фотографий]]></notice>
        <debuginfo ><![CDATA[ … ]]></debuginfo>
    </message>
</jcanswer>
```



