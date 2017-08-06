# 2.6. Функция get\_money. Получение информации о счете программы.

| Название параметра | Значение | Описание |
| :--- | :--- | :--- |
| s\_sn | набор символов длиной не более 255 символов. | код программы |
| action | ins | действие выполняемое с данными |

Вид POST запроса:

```
action=get_money&s_sn=34itlwk87er9j
```

Ответ: 

```xml
<?xml version="1.0" encoding="windows-1251"?>
<jcanswer>
	<message>
		<result >SUCCESS</result>
		<code >N0407_BILLING_SUCCESS</code>
		<action >account</action>
		<group id="billing" area="none"><![CDATA[Обработка данных биллинга]]></group>
		<datetime >2010-04-15 16:37:29</datetime>
		<text ><![CDATA[Данные о лицевом счете]]></text>
		<techinfo ><![CDATA[{"money":9965.6,"currency_id":4}]]></techinfo>
	</message>
</jcanswer>

```



