# Функции get\_price\_info и get\_price. Узнать цену запчасти.

Описание функции:

Сервис "узнать цену запчасти" работает в два этапа:

1. Функция \(get\_price\_info\) определяет возможность проведения операции и есть ли данные по запрашиваемым параметрам.
2. Функция \(get\_price\) списывает деньги за услугу и выдает подробную информацию о ценах.

### Первый этап. Функция  get\_price\_info

| Название параметра | Значение | Описание |
| :--- | :--- | :--- |
| s\_sn | набор символов длиной не более 255 символов. | код программы |
| action | get\_price\_info | действие выполняемое с данными |
| marka | строка | опционально, марка машины |
| model | строка | опционально, модель машины |
| modelN | строка | опционально, номер оптики |
| kuzovN | строка | опционально, номер кузова |
| engineN | строка | опционально, номер двигателя |
| producer\_code | строка | опционально, код производителя |
| producer | строка | опционально, производитель |
| F\_R | R,F | опционально, перед/зад |
| U\_D | U,D | опционально, верх/низ |
| R\_L | L,R | опционально, лев/прав |
| N\_O | O,N | опционально, новая, б/у |
| name | строка | опционально, название запчасти |
| oem | строка | опционально, ОЕМ код запчасти |
| place | код города из справчника parts\_place | опционально, идентификатор города |

Вид POST запроса:

```
s_sn=3274171001&action=get_price_info&name=efi&marka=toyota&model=ipsum
```

Ответ: \(пример приведен для программ 1С, для программ JcTrade ответ будет таки же, за исключением тега techinfo. Информация в нем будет представлена в формате JSON\)

```xml
<?xml version="1.0" encoding="windows-1251"?>
<jcanswer>
<message>
    <result >SUCCESS</result>
    <code >N0407_BILLING_SUCCESS</code>
    <action >detail</action>
    <group id="billing" area="none"><![CDATA[Обработка данных биллинга]]></group>
    <datetime >2013-07-11 06:38:13</datetime>
    <text ><![CDATA[Данные о возможности проведения операции получены]]></text>
    <techinfo >
        <summary>
            <get_price_info>
                <free>
                    <count>0</count>
                    <atom_cost>0</atom_cost>
                    <cost>0</cost>
                </free>
                <poket>
                    <count>0</count>
                    <atom_cost>0</atom_cost>
                    <cost>0</cost>
                </poket>
                <cash>
                    <count>1</count>
                    <atom_cost>1</atom_cost>
                    <cost>1</cost>
                </cash>
                <active>1</active>
            </get_price_info>
        </summary>
        <result>1</result>
        <posible>yes</posible>
        <cost>1</cost>
        <currency_id>4</currency_id>
    </techinfo>
</message>
<message>
    <result >SUCCESS</result>
    <code >N0407_BILLING_SUCCESS</code>
    <action >account</action>
    <group id="billing" area="none"><![CDATA[Обработка данных биллинга]]></group>
    <datetime >2013-07-11 06:38:13</datetime>
    <text ><![CDATA[Данные о лицевом счете и добавленных объявлениях]]></text>
    <techinfo>
        <money>395143</money>
        <currency_id>4</currency_id>
        <added_count>0</added_count>
    </techinfo>
</message>
<message>
    <result >SUCCESS</result>
    <code >N0080_SERVICE_SUCCESS</code>
    <action >get_price_info</action>
    <group id="main" area="parts"><![CDATA[Система обработки данных]]></group>
    <datetime >2013-07-11 06:38:14</datetime>
    <text ><![CDATA[Запрос на среднюю цену успешно обработан]]></text>
    <techinfo>
        <has_value>1</has_value>
        <request_id>41</request_id>
        <notice_count>119</notice_count>
    </techinfo>
    <debuginfo></debuginfo>
</message>
</jcanswer>
```

Результат функции:  
в первом теге message содержится информация о стоимости услуги, возможности ее проведения, во втором теге message указывается информация о состоянии счета программы, в третьем теге  message результат запроса  функции get\_price\_info. В теге techinfo приходят следующие параметры:

| Название параметра | Значение | Описание |
| :--- | :--- | :--- |
| has\_value | 0,1 | флаг показывающий есть ли результат |
| request\_id | Целое число | идентификатор, по которому можнообратится для получения данных методом get\_price |
| notice\_count | Целое число | количество объявлений участвовавших в формировании цены |

### Второй этап. Функция get\_price Получение результата.

| Название параметра | Значение | Описание |
| :--- | :--- | :--- |
| s\_sn | набор символов длиной не более 255 символов. | код программы |
| action | get\_price | действие выполняемое с данными |
| request\_id | Целое число | Значение, полученное на первом этапе функцией get\_price\_info |

Вид POST запроса:

```
s_sn=45234523453&action=get_price&request_id=1565
```

Ответ: \(пример приведен для программ 1С, для программ JcTrade ответ будет таки же, за исключением тега details. Информация в нем будет представлена в формате JSON\)

```xml
<?xml version="1.0" encoding="windows-1251"?>
<jcanswer>
    <message>
        <result >SUCCESS</result>
        <code >N0081_SERVICE_SUCCESS</code>
        <action >get_price</action>
        <group id="main" area="parts"><![CDATA[Система обработки данных]]></group>
        <datetime >2013-07-11 06:40:54</datetime>
        <text ><![CDATA[Средняя цена получена]]></text>
        <techinfo >
            <notice_count>28</notice_count>
            <price_min>100</price_min>
            <price_max>5670</price_max>
            <price_average>3293</price_average>
            <details>
                <item num="0">14</item>
                <item num="100">1</item>
                <item num="1500">1</item>
                <item num="1600">1</item>
                <item num="2000">2</item>
                <item num="3000">3</item>
                <item num="3200">1</item>
                <item num="4846">1</item>
                <item num="4850">1</item>
                <item num="5670">3</item>
            </details>
        </techinfo>
        <debuginfo ><![CDATA[]]></debuginfo>
    </message>
</jcanswer>
```

В результате поле techinfo содержит следующие параметры:

| Название параметра | Значение | Описание |
| :--- | :--- | :--- |
| notice\_count | набор символов длиной не более 255 символов. | количество объявлений принимавших участие в построении цены |
| price\_min | Целое число | минимальная цена |
| price\_max | Целое число | максимальная цена |
| price\_average | Целое число | средняя цена |
| details | атрибут num - цена, значение в теге item - количество запчастей с указаной ценой. | массив полученных цен, сгруппированных по цене, массив отсортирован по возрастанию. Ограничение на количество элементов в массиве: 200 \(если различных цен больше то в результат не войдут маленькие цены\) |



