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



