#Первое подключение к серверу

Для того что бы можно было работать по протоколу передачи данных необходимо выполнить два условия: 

1. Идентификатор программы должен появиться на сервере до того как началась передача данных.
2. Идентификатор программы должен быть привязан к личному кабинету пользователя.

\(На текущий момент, можно просто привязать ключ\(строку со случайными символами\) в личном кабинете. Прим. редактора\)

Что бы выполнить первое условие достаточно один раз отправить информацию о магазине действием [Изменение информации о продавце.](/funktsiya-upds.md) После этого идентификатор программы будет храниться на сервере.

Для выполнения второго условия, пользователь должен в своем личном кабинете привязать программу к своему счету. При проверке счета с идентификатором не привязанным к личному кабинету в ответ придет следующее сообщение:

```
<?xml version="1.0" encoding="windows-1251"?>
<jcanswer>
<message>
<result >SUCCESS</result>
<code >N0000_SERVICE_SUCCESS</code>
<action >detail</action>
<group id="billing" area="none"><![CDATA[Обработка данных биллинга]]></group>
<datetime >2010-04-16 13:05:09</datetime>
<text ><![CDATA[Программа не зарегистрирована]]></text>
<fulltext ><![CDATA[Необходимо зарегистрировать счет программы для получения бесплатного пакета и возможности пополнять счет и добавлять объявления платно. Для того чтобы зарегистрировать счет пройдите по ссылке]]></fulltext>
<link site="japancar.ru" ><![CDATA[http://user.japancar.ru/?code=user&mode=progreg&programm=jctrade&programm_id=34itlwk87er9j]]></link>
<link site="japancar.ru" ><![CDATA[http://information.japancar.ru/?code=info&mode=progreghelp]]></link>
<techinfo ><![CDATA[{"result":0,"posible":"no_account","cost":0,"currency":0,"summary":[]}]]></techinfo>
<debuginfo ><![CDATA[ ]]></debuginfo>
</message>
</jcanswer>

```

Первый тег link всегда содержит ссылку на регистрацию программы в личном кабинете, а второй всегда содержит ссылку на страницу с описанием процесса регистрации программ в личном кабинете.После сохранения данных о программе на сервере и регистрации программы в личном кабинете можно пользоваться функциями добавления, изменения, удаления объявлений и тп функциями.



