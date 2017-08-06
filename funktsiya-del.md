# Функция del. Удаление объявления.

| Название параметра | Значение | Описание |
| :--- | :--- | :--- |
| s\_sn | набор символов длиной не более 255 символов. | код программы |
| p\_version | текст длиной не более 255 символов | версия программы |
| action | del | действие выполняемое с данными |
| count | целое число от 1 до 500 | количество передаваемых запчастей в данном запросе |
| id\[n\] | набор символов длиной не более 255 символов. | уникальный номер запчасти в программе |

Вид POST запроса:

```
s_sn=34itlwk87er9j&p_version=3.0.25&action=del&count=8&id[0]=000000003&id[1]=000000004...&id[7]=000000010
```

Ответ:

```xml
<?xml version="1.0" encoding="windows-1251"?>
<jcanswer>
	<message>
		<result >SUCCESS</result>
		<code >N0000_SERVICE_SUCCESS</code>
		<action >del</action>
		<group id="main" area="parts"><![CDATA[Система обработки данных]]></group>
		<datetime >2010-04-15 16:23:35</datetime>
		<text ><![CDATA[Объявления успешно удалены]]></text>
		<notice id="N0500_RESULT_NOTICE" ><![CDATA[Удалено 7 объявлений запчастей]]></notice>
		<debuginfo ><![CDATA[ … ]]></debuginfo>
	</message>
</jcanswer>
```



