# 2. Передача данных на сервер

Формат запроса:

* Данные передаются на сервер методом POST
* Вид передаваемых данных: param1=value1&param2=value2…&paramN=valueN
* Ограничение на размер передаваемых данных за один раз 2Мб.

Сервер генерирует ответ в формате xml

```xml
<?xml version="1.0" encoding="windows-1251" ?> 
<jcanswer>
    <message>
        <invnn>67</invnn>
        <item_id>1546470</item_id> 
        <result>SUCCESS</result> 
        <code> N0000_SERVICE_SUCCESS</code> 
        <action>EDIT</action>
        <group id="main" area="parts">
            <![CDATA[ Система обработки данных ]]>
        </group>
        <datetime>2009-07-09 14:03:02</datetime> 
        <text><![CDATA[Объявление успешно добавлено]]></text>
        <warning id="DATA_WARNING_0101">
            <![CDATA[превышено количество символов в поле Примечание". ]]>
        </warning>
        <notice id="DATA_NOTICE_0102"> 
            <![CDATA[Информационное сообщение]]>
        </notice>
        <link site="japancar.ru">
            <![CDATA[http://parts.japancar.ru/jc/view/parts_old/ytPHLjAwNA/P3fc0203165b9918da86968c57b6eb512.html]]>
        </link> 
        <link site ="qx9.ru">
            <![CDATA[http://www.qx9.ru/jc/view/parts /ytPHLjAwNA/P3fc0203165b9918da86968c57b6eb512.html]]>
        </link> 
        <techinfo> <![CDATA{TECHINFO}]]></techinfo>
        <debuginfo> <![CDATA[{SQL_TEXT}]]></debuginfo>
    </message>
</jcanswer>
```

Ответ может состоять из нескольких сообщений \(message\), по одному на каждое действие. Обязательными полями являются результат \(result\), код \(code\), текст сообщения \(text\), локализация \(group\), дата-время генерации сообщения\(datetime\) и номер объявления \(item\_id\) при добавлении. Остальные поля носят необязательный характер и призваны обеспечить ответ дополнительной полезной информацией.

Подробнее об структуре ответа сервера смотрите  "[Подробное описание полей ответа сервера](/podrobnoe-opisanie-polei-otveta-servera.md)".

Ниже приведены действия которые доступны по данному протоколу. Передаваемые в параметре "action"

| Действие | Описание действия |
| :--- | :--- |
| get\_status   | Получение информации о возможности добавления объявлений |
| get\_money | Получение информации о счете программы |
| get\_added | Получение информации о том, сколько объявлений было добавлено |
| get\_status\_money | Комбинация get\_added, get\_money, get\_status  |
| get\_ids | Получение номеров объявлений находящихся на сервере |
| upd\_s | Изменение информации о продавце |
| ins | Добавление объявлений |
| del | Удаление объявления |
| upd\_all | Изменение объявления |
| ins\_f | Добавление фотографий |

Использование get\_status, get\_money, get\_added, get\_status\_money и get\_ids не обязательно. Это информационные сервисы, предназначенные для предоставления пользователю более полной информации о состоянии счета и наличии запчастей на сервере. 

Основными функциями для работы с сервером являются upd\_s, ins, del, upd\_all, ins\_f. 



