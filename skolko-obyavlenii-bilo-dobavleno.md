# 2.6. Функция get\_added. Сколько объявлений было добавлено.

| Название параметра | Значение | Описание |
| :--- | :--- | :--- |
| s\_sn | набор символов длиной не более 255 символов. | код программы |
| action | get\_added | действие выполняемое с данными |
| added\_section\[\] | parts | раздел по которому должна быть получена информация |

Вид POST запроса:

```
action=get_added&s_sn=34itlwk87er9j&added_section[]=parts
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
        <datetime >2010-04-15 17:00:53</datetime>
        <text ><![CDATA[Данные о добавленных объявлениях получены]]></text>
        <techinfo ><![CDATA[{"added_count":73}]]></techinfo>
    </message>
</jcanswer>
```

в теге techinfo ссдержится запрашиваемая информация в формате JSON.

* added\_count – количество добавленых объявлений с начала текущего месяца.    



