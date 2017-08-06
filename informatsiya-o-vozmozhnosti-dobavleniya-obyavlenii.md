# 2.6. Функция get\_status. Информация о возможности добавления объявлений.

| Название параметра | Значение | Описание |
| :--- | :--- | :--- |
| s\_sn | набор символов длиной не более 255 символов. | код программы |
| action | get\_status | действие выполняемое с данными |
| base\_tables\[\] | parts | раздел по которому должна быть получена информация |
| counts\[\] | целое число до 11 знаков | количество объявлений которые предполагается добавить |

Вид POST запроса:

```
action=get_status&s_sn=34itlwk87er9j&base_tables[]=parts&counts[]=40
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
        <datetime >2010-04-15 17:11:10</datetime>
        <text ><![CDATA[Данные о возможности проведения операции получены]]></text>
        <techinfo ><![CDATA[{"summary":{"parts":{"free":{"count":40,"atom_cost":0,"cost":0},"cash":{"count":0,"atom_cost":0,"cost":0}}},"result":1,"posible":"yes","cost":0,"currency_id":4}]]></techinfo>
    </message>
</jcanswer>
```

В теге techinfo ссдержится запрашиваемая информация в формате JSON.   
Описание объекта возвращаемого в качестве результата:

* int **result**
  * 0 если нельзя 
  * 1 если операцию проводить можно
  * -1 если ошибка
* string **possible** – детализированный ответ
  * yes – да, можно
  * no\_account - нет счета
  * not\_enough\_money - не достаточно денег
  * accaunt\_blocked - счет заблокирован
  * error\_serviceunreach - сервис не доступен
  * error\_servicedown - сервис не доступен
  * error\_incorrectdata – неправильные данные
  * error\_internal – ошибка сервиса
  * error\_uncatched – неопределенная ошибка, ошибка на сервере билинга
  * error\_unknown – неопределенная ошибка.
* double **cost** – общая стоимость
* int **currency\_id** – в биллинге всегда рубли, приходит «4»
* array **summary** – трехмерный массив содержащий информацию:
  * free - сколько добавлено бесплатно
  * cash сколько добавлено за деньги
    Для раздела указывается:
    * string **pay\_type**  - тип «оплаты» объявлений {free, cash }
    * int **count** – количество объявлений
    * double **cost** – общая стоимость этих объявлений
    * double **atom\_cost** – стоимость одного такого объявления \(не используется\)



