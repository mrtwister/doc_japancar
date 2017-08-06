# 1. Получение адресов для работы с сервером

Для разных действий программе необходимо будет обращаться к разным сервисам, поэтому перед выполнением каких-либо действий следует получить адреса соответствующих сервисов.

Ссылка для получения списка сервисов для JcTrade:

[http://www.japancar.ru/jcgate/gate.php?for=jctrade&object=links&ver=japancar.ru&type=plain\_text&answer\_version=1](http://www.japancar.ru/jcgate/gate.php?for=jctrade&object=links&ver=japancar.ru&type=plain_text&answer_version=1)

ссылка для получения списка сервисов для 1C:

[http://www.japancar.ru/jcgate/gate.php?for=jctrade&object=links&ver=japancar.ru&type=plain\_text&answer\_version=1.1](http://www.japancar.ru/jcgate/gate.php?for=jctrade&object=links&ver=japancar.ru&type=plain_text&answer_version=1.1)

Ответ возвращается в виде текста, где пары имя=значение разделены переводом строки  
. Первой строкой идет слово «Ok», если при формировании списка не произошло ошибок. Все нужные адреса сервисов находятся между строками «action=begin» и «action=end»  
 Если строк «action=begin» или «action=end» нет в ответе то список считается не полным, и необходим его повторный запрос  
.

Сервисы необходимые для работы с запчастями:

| Имя сервиса | Описание |
| :---: | :---: |
| parts\_path | Все основные действия с запчастями на сервере |
| parts\_place | Сервис выдачи справочника городов |
| parts\_syn | Сервис выдачи справочника запчастей |
| update\_path | Сервис выдачи справочников для всех разделов кроме раздела «Автозапчасти» |

Пример ответа на запрос получения списка сервисов:

```
Ok
action=begin
notice_path=http://www.japancar.ru/jpoffline/base_jctrade.php?answer_version=1
notice_path_parts=http://www.japancar.ru/database/form.php?
news_path=http://www.japancar.ru/jpoffline/jo_news.php?
dispather_path=http://www.japancar.ru/jcgate/gate.php?for=jctrade&object=links&ver=japancar.ru&type=plain_text
update_path=http://www.japancar.ru/jpoffline/gate.php?
parts_place=http://www.japancar.ru/jcgate/gate.php?for=database&object=handbook&ver=1C&type=plain_text&hb=place
parts_marks=http://www.japancar.ru/jcgate/gate.php?for=database&object=handbook&ver=1C&type=plain_text&hb=marka
parts_categ=http://www.japancar.ru/jcgate/gate.php?for=database&object=handbook&ver=1C&type=plain_text&hb=cat
parts_syn=http://www.japancar.ru/jcgate/blank.php
parts_path=http://www.japancar.ru/jcgate/jctrade_dataprocess.php?answer_version=1
action=end
```



