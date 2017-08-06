# Функция upd\_s. Изменение информации о продавце.

| Название параметра | Значение | Описание |
| :--- | :--- | :--- |
| s\_sn | набор символов длиной не более 255 символов. | код программы |
| p\_version | текст длиной не более 255 символов | версия программы |
| action | upd\_s | действие выполняемое с данными |
| s\_name | текст длиной не более 255 символов | название магазина |
| s\_email | текст длиной не более 255 символов | E-mail |
| s\_tel | текст длиной не более 255 символов | список телефонов |
| s\_web | текст длиной не более 255 символов | название сайта магазина |
| s\_fax | текст длиной не более 255 символов | список факсов |
| s\_id\_place | целое число до 11 знаков | индекс города из справочника городов |
| contact\_icq | текст длиной не более 255 символов | номер ICQ |
| contact\_skype | текст длиной не более 255 символов | имя Skype |
| contact\_company | 1/0 | признак компания / частное лицо |
| contact | текст длиной не более 512 символов | адрес магазина и дополнительная информация |

Вид POST запроса:

```
s_sn=34itlwk87er9j&p_version=3.0.25&action=upd_s&s_name=Название магазина&s_email=Адрес электронной почты (для связи с клиентами)&s_tel=(4232) 000-000&s_web=www.mysite.ru&s_fax=3450-4332-223&s_id_place=1&contact_icq=myicq&contact_skype=myskype&contact_company=1&contact= Адрес магазина  и Дополнительные сведения
```

Ответ:

```xml
<?xml version="1.0" encoding="windows-1251"?>
<jcanswer>
    <message>
        <result >SUCCESS</result>
        <code >N0008_SERVICE_SUCCESS</code>
        <action >upd_s</action>
        <group id="main"
               area="parts">
            <![CDATA[Система обработки данных]]>
        </group>
        <datetime >2010-04-15 15:04:08</datetime>
        <text >
            <![CDATA[Данные о магазине обновлены]]>
        </text>
        <debuginfo >
            <![CDATA[Array
(
    [s_sn] => 3387166128
    [id_firms] => 
    [p_version] => 3.0.25
    [action] => upd_s
    [s_name] => Название магазина
    [s_addr] => Адрес магазина
    [s_email] => Адрес электронной почты (для связи с клиентами)
    [s_tel] => (4232) 000-000
    [s_web] => www.mysite.ru 
    [s_fax] => 3450-4332-223 
    [s_id_place] => 1
    [contact_icq] => myicq 
    [contact_skype] => myskype 
    [contact_company] => 0
    [contact] => Дополнительные сведения
)
]]>
        </debuginfo>
    </message>
</jcanswer>
```



