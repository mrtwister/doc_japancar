# Функция get\_status\_money. Комбинация get\_added, get\_money, get\_status.

| Название параметра | Значение | Описание |
| :--- | :--- | :--- |
| action | get\_status\_money | действие выполняемое с данными |

Все остальные параметры идентичны параметрам из статьи [Информация о возможности добавления объявлений.](/informatsiya-o-vozmozhnosti-dobavleniya-obyavlenii.md)

Вид POST запроса:

```
action=get_status_money&s_sn=34itlwk87er9j&base_tables[]=parts&counts[]=40
```

Ответ:

```xml
<?xml version="1.0" encoding="windows-1251"?>
<jcanswer>
	<message>
		<result >SUCCESS</result>
		<code >N0407_BILLING_SUCCESS</code>
		<action >detail</action>
		<group id="billing" area="none"><![CDATA[Обработка данных биллинга]]></group>
		<datetime >2010-04-15 17:48:39</datetime>
		<text ><![CDATA[Данные о возможности проведения операции получены]]></text>
		<techinfo ><![CDATA[{"summary":{"parts":{"free":{"count":40,"atom_cost":0,"cost":0},"cash":{"count":0,"atom_cost":0,"cost":0}}},"result":1,"posible":"yes","cost":0,"currency_id":4}]]></techinfo>
	</message>
	<message>
		<result >SUCCESS</result>
		<code >N0407_BILLING_SUCCESS</code>
		<action >account</action>
		<group id="billing" area="none"><![CDATA[Обработка данных биллинга]]></group>
		<datetime >2010-04-15 17:48:39</datetime>
		<text ><![CDATA[Данные о лицевом счете и добавленных объявлениях]]></text>
		<techinfo ><![CDATA[{"added_count":0,"money":9965.6,"currency_id":4}]]></techinfo>
	</message>
</jcanswer>
```

В данном ответе передаются сразу два тега message. В одном из тегов содержится информация о возможности добавления объявлений. Формат аналогичен ответу из [Информация о возможности добавления объявлений.](/informatsiya-o-vozmozhnosti-dobavleniya-obyavlenii.md). 

В другом тэге содержится информация о счете программы, формат аналогичен ответу из [Получение информации о счете программы](/poluchenie-informatsii-o-schete-programmi.md)





