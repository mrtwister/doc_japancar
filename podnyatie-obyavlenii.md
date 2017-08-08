# Функция raise\_up. Поднятие объявлений.

| Название параметра | Значение | Описание |
| :--- | :--- | :--- |
| s\_sn | набор символов длиной не более 255 символов. | код программы |
| action | raise\_up | действие выполняемое с данными |
| base\_tables\[\] | auto, moto, water, power, powerparts, waterparts, auto2parts, motoparts, sound, tyre, tuning, parts | раздел по которому должна быть получена информация |
| counts | целое число | массив количества объявлений которые нужно поднять в каждом из указанных разделов.  |
| raise\_all | all | Опционально, если указать "all", то поднятие будет применено не только к архивным, а ко всем объявлениям. |
| parts\_category | код категории запчасти из справочника категорий | опционально, если в параметре base\_tables содержится раздел "parts", то запчасти будут подняты только с кодом категории указанным parts\_category. На поднятие объявлений в других разделах parts\_category не влияет |
| id\[\] | массив идентификаторов объявлений | опционально, если в параметре base\_tables содержится раздел "parts", то запчасти будут подняты только с указанными идентификаторами |

Вид POST запроса:

```
s_sn=45234523453&action=raise_up&base_tables[]=moto&base_tables[]=tyre&counts[]=150& counts[]=50&raise_all=all
```

Для поднятия по идентификаторам:

```
s_sn=45234523453&action=raise_up&base_tables[]=moto&base_tables[]=parts&counts[]=150& counts[]=2&raise_all=all&id[]=3494&id=49349
```

Ответ:

```xml
<?xml version="1.0" encoding="windows-1251"?>
<jcanswer>
    <message>
        <result >SUCCESS</result>
        <code >N0050_SERVICE_SUCCESS</code>
        <action >raise_up</action>

    <group id="main" area="moto"><![CDATA[Система обработки данных]]></group>
        <datetime >2013-07-11 06:55:58</datetime>
        <text ><![CDATA[Объявления успешно подняты]]></text>
        <techinfo >
            <count>1</count>
            <affected>1</affected>
            <found>2</found>
        </techinfo>
        <debuginfo ><![CDATA[]]></debuginfo>
    </message>
    <message>
        <result >SUCCESS</result>
        <code >N0050_SERVICE_SUCCESS</code>
        <action >raise_up</action>
        <group id="main" area="auto"><![CDATA[Система обработки данных]]></group>
        <datetime >2013-07-11 06:55:58</datetime>
        <text ><![CDATA[Объявления успешно подняты]]></text>
        <notice id="N0073_SCRIPT_NOTICE" ><![CDATA[]]></notice>
        <techinfo >
            <count>0</count>
            <affected>0</affected>
            <found>0</found>
        </techinfo>
        <debuginfo ><![CDATA[]]></debuginfo>
    </message>
</jcanswer>
```

Функция поэтапно осуществляет поднятие по дате объявлений, находящихся в архиве \(добавлены более двух месяцев назад\) по разделам учитывая установленное ограничение на количество объявлений. При этом проверяется возможность проведения операции через биллинг, так как услуга платная. Если для раздела указано количество больше чем фактически есть объявлений, то будет использоваться количество фактически существующих объявлений. Если фактически объявлений больше, то подняты будут самые старые обновленные данные в указанном количестве.

