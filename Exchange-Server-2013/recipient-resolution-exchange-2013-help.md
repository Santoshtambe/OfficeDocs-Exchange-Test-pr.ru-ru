﻿---
title: 'Разрешение получателей: Exchange 2013 Help'
TOCTitle: Разрешение получателей
ms:assetid: 09deda5a-d405-45b1-a3ff-fefd3d76cdea
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Bb430743(v=EXCHG.150)
ms:contentKeyID: 52061199
ms.date: 04/30/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Разрешение получателей

 

_**Применимо к:**Exchange Server 2013_

_**Последнее изменение раздела:**2016-03-17_

*Разрешение получателей* — это процесс расширения и разрешения всех получателей сообщения. При расширении получатели сопоставляются с соответствующими объектами службы каталогов Active Directory в организации Microsoft Exchange. При развертывании получателей все группы рассылки преобразуются в список отдельных получателей. Эти действия позволяют правильно применять к каждому получателю альтернативных получателей и ограничения для сообщений.

В организации Microsoft Exchange Server 2013 разрешение получателей выполняется классификатором в транспортной службе на серверах почтовых ящиков. Классификация каждого полученного сообщения производится после его помещения в очередь передачи. Разрешение получателей, а также преобразование содержимого и маршрутизация выполняются перед помещением сообщения в очередь доставки. Классификатор выполняет разрешение получателей перед маршрутизацией. Компонент классификатора, который отвечает за разрешение получателей, часто называется *распознавателем*.

**Содержание**

разрешение верхнего уровня;

Расширение

Развертывание и контроль расширения получателей

Диагностика разрешения получателей

## разрешение верхнего уровня;

*Разрешение верхнего уровня* — это первый этап разрешения получателей. При разрешении верхнего уровня каждый получатель входящего сообщения сопоставляется с соответствующим объектом получателя в Active Directory. Во время разрешения верхнего уровня классификатор создает список, в котором указываются получатель и первоначальные (нерасширенные) адреса электронной почты получателей, которые присутствуют в сообщении. Затем классификатор использует этот список адресов электронной почты для поиска объектов Active Directory с соответствующими атрибутами электронной почты. При обнаружении соответствия свойства соответствующих объектов Active Directory кэшируются для последующего использования. Кроме того, применяются все ограничения для отправителя сообщения.

## Адреса электронной почты получателей

Разрешение верхнего уровня начинается с обработки сообщения и первоначального (нерасширенного) списка получателей из *конверта сообщения*. Конверт сообщения содержит команды, которые используются для передачи сообщений между SMTP-серверами. Адрес электронной почты отправителя указан в команде **MAIL FROM:** . Адрес электронной почты каждого получателя указан в отдельной команде **RCPT TO:** . Отправитель и получатели конверта обычно создаются на основе отправителя и получателей, указанных в полях заголовка сообщения `To:`, `From:`, `Cc:` и `Bcc:`. Однако это не всегда так. Поля заголовка сообщения `To:`, `From:`, `Cc:` и `Bcc:` легко подделать, и они могут не соответствовать действительным адресам электронной почты отправителя и получателей, которые использовались для передачи сообщения.

## Инкапсулированные адреса электронной почты

Стандартные SMTP-адреса электронной почты соответствуют спецификациям RFC 2821 и RFC 2822, например: andrey@contoso.com. Тем не менее адрес электронной почты может не являться SMTP-адресом, инкапсулированным в допустимый SMTP-адрес. Сервер Exchange поддерживает инкапсулированные адреса, которые используют метод инкапсуляции Internet Mail Connector Encapsulated Address (IMCEA).

Для этого метода инкапсуляции требуется кодировка всех символов, которые не допускаются в SMTP-адресах электронной почты. Буквы, цифры, знак равенства (=) и дефис (-) не кодируются. Для других символов используется следующий синтаксис кодировки:

  - косая черта (/) заменяется символом подчеркивания (\_);

  - прочие символы ASCII (США) заменяются знаком «плюс» (+) и двумя цифрами их значений ASCII, записанных в шестнадцатеричной форме. Например, пробел имеет кодированное значение `+20`.

Синтаксис метода инкапсуляции IMCEA описан ниже. `IMCEA<Type>-<address>@<domain>`

Прототип \<*Type*\> указывает тип адреса, который не является SMTP-адресом, например `EX`, `X400` или `FAX`.

<table>
<thead>
<tr class="header">
<th><img src="images/JJ126620.note(EXCHG.150).gif" title="Примечание" alt="Примечание" />Примечание.</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Хотя <code>SMTP</code> и <code>X500</code> являются теоретически допустимыми значениями параметра &lt;<em>Type</em>&gt;, при разрешении получателей Exchange отклоняются все адреса, закодированные с использованием метода IMCEA, которые имеют любой из этих типов.</td>
</tr>
</tbody>
</table>


Заполнитель \<*address*\> указывает на первоначальный адрес, который кодируется. Заполнитель \<*domain*\> обозначает домен SMTP, используемый для инкапсуляции адреса, не являющегося SMTP-адресом, например contoso.com.

При использовании метода инкапсуляции IMCEA адреса не инкапсулируются только в том случае, если домен совпадает с уполномоченным доменом по умолчанию в организации Exchange. Дополнительные сведения об обслуживаемых доменах см. в разделе [Обслуживаемые домены](accepted-domains-exchange-2013-help.md).

Максимальная длина SMTP-адреса электронной почты в Exchange — 571 символ. Это ограничение включает следующее:

  - 315 символов для части адреса, относящейся к имени;

  - 255 символов для имени домена;

  - символ «@», отделяющий часть адреса, относящуюся к имени, от имени домена.

Обратите внимание, что Exchange не поддерживает сообщения, которые кодируются с использованием метода инкапсуляции IMCEA, если длина части адреса, относящейся к имени, превышает 315 символов, даже если полная длина адреса не превышает 571 символа.

## Способ разрешения адресов

Адреса электронной почты отправителя и всех получателей каждого сообщения добавляются в список, который используется для опроса Active Directory. Перед добавлением в список отменяется инкапсуляция всех инкапсулированных адресов электронной почты. Опрос Active Directory может выполняться по 20 адресам электронной почты за один раз. Если при выполнении опроса Active Directory возникают временные ошибки, сообщение возвращается в очередь передачи и его доставка откладывается на время, определяемое параметром *ResolverRetryInterval* в XML-файле конфигурации `%ExchangeInstallPath%Bin\EdgeTransport.exe.config` приложения, связанного с транспортной службой Microsoft Exchange. Значение по умолчанию — 30 минут.

В представленной ниже таблице описаны объекты получателей в Active Directory. Дополнительные сведения о типах получателей в Exchange см. в разделе [Получатели](recipients-exchange-2013-help.md).

### Объекты получателей в Active Directory

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Тип получателя в Active Directory</th>
<th>Описание</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>DistributionGroup</p></td>
<td><p>Любой объект группы, поддерживающий почту. Объекты группы рассылки имеют указанные ниже типы.</p>
<ul>
<li><p><strong>MailUniversalDistributionGroup</strong>.   Объект универсальной группы рассылки.</p></li>
<li><p><strong>MailUniversalSecurityGroup</strong>.   Объект универсальной группы безопасности, которая имеет адрес электронной почты.</p></li>
<li><p><strong>MailNonUniversalGroup</strong>.   Объект локальной или глобальной группы безопасности, которая имеет адрес электронной почты.</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p>DynamicDistributionGroup</p></td>
<td><p>Объект с классом Active Directory <strong>msExchDynamicDistributionList</strong>. Подробнее см. в разделе <a href="manage-dynamic-distribution-groups-exchange-2013-help.md">Управление динамическими группами рассылки</a>.</p></td>
</tr>
<tr class="odd">
<td><p>Mailbox</p></td>
<td><p>Объект пользователя, для которого назначен адрес электронной почты и определен параметр <em>Database</em>.</p></td>
</tr>
<tr class="even">
<td><p>MailUser</p></td>
<td><p>Объект пользователя, для которого назначен адрес электронной почты и не определен параметр <em>Database</em>. Подробнее см. в разделе <a href="manage-mail-users-exchange-2013-help.md">Управление пользователями почты</a>.</p></td>
</tr>
<tr class="odd">
<td><p>MailContact</p></td>
<td><p>Объект контакта, который имеет адрес электронной почты. Обычно почтовые контакты используются для получателей за пределами организации Exchange. Почтовые контакты также используются в межлесной среде Exchange. Подробнее см. в разделе <a href="manage-mail-contacts-exchange-2013-help.md">Управление почтовыми контактами</a>.</p></td>
</tr>
<tr class="even">
<td><p>MailPublicFolder</p></td>
<td><p>Объект общей папки, который имеет адрес электронной почты.</p></td>
</tr>
<tr class="odd">
<td><p>MicrosoftExchangeRecipient</p></td>
<td><p>Объект с классом Active Directory <strong>msExchExchangeServerRecipient</strong>. Дополнительные сведения об объекте получателя Microsoft Exchange см. в разделе <a href="recipients-exchange-2013-help.md">Получатели</a>.</p></td>
</tr>
<tr class="even">
<td><p>SystemAttendantMailbox</p></td>
<td><p>Объект с классом Active Directory <strong>exchangeAdminService</strong>. В организации Exchange должен быть только один почтовый ящик системного помощника.</p></td>
</tr>
<tr class="odd">
<td><p>SystemMailbox</p></td>
<td><p>Объект пользователя, для которого назначен адрес электронной почты и который находится в контейнере системных объектов Microsoft Exchange. В организации Exchange должен быть один системный почтовый ящик для каждой базы данных почтовых ящиков.</p></td>
</tr>
</tbody>
</table>


Объект, в котором отсутствуют или повреждены критически важные свойства, классифицируется запросом Active Directory как недопустимый. Например, объект динамической группы рассылки без адреса электронной почты считается недопустимым. Сообщения, которые отправляются получателям, классифицированным как недопустимые объекты, приводят к получению отчета о недоставке.

Для каждого адреса электронной почты выполняется один первоначальный запрос всех возможных свойств получателя, таких как идентификаторы получателя, тип получателя, ограничения для сообщений, адреса электронной почты и альтернативные получатели. Применимые свойства получателя кэшируются для последующего использования. При разрешении получателей они классифицируются на основе сходства способа их разрешения и применимых свойств получателей.

Фильтр LDAP, используемый для разрешения адресов, имеет описанные ниже характеристики.

  - Для типа адресов электронной почты **EX** фильтр LDAP основывается на атрибуте получателя **legacyExchangeDN** или **proxyAddresses** службы каталогов Active Directory. Атрибут **legacyExchangeDN** службы каталогов Active Directory всегда имеет приоритет.

  - Для других типов адресов электронной почты в качестве фильтра LDAP используется атрибут получателя **proxyAddresses** службы каталогов Active Directory.

Если адрес электронной почты, использованный в сообщении, не совпадает с основным SMTP-адресом соответствующего объекта Active Directory, классификатор перезаписывает адрес электронной почты сообщения так, чтобы он соответствовал основному SMTP-адресу. Исходный адрес электронной почты сохраняется в параметре `ORCPT=` команды **RCPT TO:** в конверте сообщения.

## Ограничения для отправителя сообщения

Размер, который используется для ограничения размера сообщения для отправителя, — это значение поля **X-MS-Exchange-Organization-OriginalSize:** в заголовке сообщения. Это поле заголовка используется в Exchange для записи исходного размера сообщения при его поступлении в организацию Exchange. При проверке сообщения на соответствие ограничениям размера сообщения используется меньшее значение текущего размера сообщения или исходного размера заголовка сообщения. Размер сообщения может изменяться из-за преобразования содержимого, кодирования или обработки агентом. Если это поле заголовка отсутствует, оно создается с использованием значения текущего размера сообщения. Если сообщение имеет слишком большой размер, создается отчет о недоставке, а дальнейшая обработка сообщения прекращается.

Ограничение на количество получателей для отправителя применяется в транспортной службе только на первом сервере почтовых ящиков, который обрабатывает сообщение. Количество получателей, указанное в конверте исходного (нерасширенного) сообщения, сравнивается с максимальным количеством получателей для отправителя. Такое количество используется, чтобы избежать проблем с частичной доставкой сообщений, которые происходили в Microsoft Exchange Server 2003, когда для вложенных списков рассылки использовались удаленные серверы расширения.

Отправитель и все получатели сообщения помечаются как разрешенные путем установки расширенного свойства сообщения. Это расширенное свойство позволяет сообщению обходить разрешение верхнего уровня, если оно должно повторно пройти разрешение получателей. Так, может потребоваться повторное разрешение получателей сообщения из-за перезапуска службы транспорта Microsoft Exchange.

В начало

## Расширение

Расширение выполняется после разрешения верхнего уровня. При этом вложенные уровни получателей полностью развертываются в отдельных получателей. Для расширения всех получателей может потребоваться выполнить процесс расширения несколько раз. Не всех получателей можно расширить. Тем не менее все получатели должны пройти через этот процесс. При расширении также применяются ограничения для сообщений, установленные для получателя, для всех видов получателей.

В следующем списке перечислены виды получателей, для которых требуется расширение.

  - **Группы рассылки и динамические группы рассылки**.   Группы рассылки расширяются на основе свойства **memberOf** службы каталогов Active Directory. Динамические группы рассылки расширяются с помощью определения запроса Active Directory. Если для группы установлен параметр *ExpansionServer*, она не расширяется на текущем сервере. Группа рассылки маршрутизируется на указанный сервер для расширения.
    
    <table>
    <thead>
    <tr class="header">
    <th><img src="images/JJ126620.note(EXCHG.150).gif" title="Примечание" alt="Примечание" />Примечание.</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td>Если в организации выбирается специальный транспортный сервер в качестве сервера расширения, использование группы рассылки зависит от доступности этого сервера расширения. Если сервер расширения недоступен, никакие сообщения, отправленные этой группе рассылки, не могут быть доставлены. При планировании использования отдельных серверов расширений для групп рассылки следует предусмотреть внедрение на этих серверах решений, обеспечивающих высокий уровень доступности, чтобы снизить вероятность прерывания работы службы.</td>
    </tr>
    </tbody>
    </table>


  - **Альтернативные получатели**.   Для почтовых ящиков и общих папок с поддержкой почты, может быть установлен параметр *ForwardingAddress*. Параметр *ForwardingAddress* перенаправляет все сообщения указанному альтернативному получателю. Такой получатель называется *получателем переадресованного* сообщения. Если в параметре *ForwardingAddress* указан альтернативный адрес доставки, а для параметра *DeliverToMailboxAndForward* установлено значение `$true`, сообщение доставляется исходному получателю и альтернативному получателю. Такой получатель называется *получателем доставленного и переадресованного* сообщения.

  - **Цепочки контактов**.   *Цепочка контактов* — это почтовый пользователь или контакт, у которого в качестве значения параметра *ExternalEmailAddress* установлен адрес электронной почты другого получателя в организации Exchange.

## Обнаружение зацикливания получателей

При расширении групп рассылки, альтернативных получателей и цепочек контактов классификатор проверяет наличие *зацикливания получателей*. Зацикливание получателей — это проблема настройки получателей, которая приводит к доставке сообщения одним и тем же получателям в бесконечном цикле. Ниже описаны различные типы зацикливания получателей.

  - **Безвредное зацикливание получателей**.   При безвредном зацикливании получателей доставка сообщения выполняется успешно. В списке ниже описаны два сценария безвредного зацикливания получателей.
    
      - Две группы рассылки являются членами друг друга.
    
      - Почтовые ящики или общие папки, поддерживающие почту, настроены на доставку и переадресацию почты друг в друга. Это происходит, когда параметр *DeliverToMailboxAndForward* обоих получателей имеет значение `$true`, а для параметра *ForwardingAddress* установлены адреса друг друга.
    
    При обнаружении безвредного зацикливания получателей сообщение доставляется получателю, но дополнительные попытки доставки сообщения тому же получателю не предпринимаются.

  - **Ошибочное зацикливание получателей**.   При ошибочном зацикливании получателей сообщение не может быть успешно доставлено. Примером такого зацикливания является случай, когда в качестве значения параметра *ForwardingAddress* каждого почтового ящика или общей папки с поддержкой почты, установлен другой почтовый ящик или общая папка. Когда классификатор обнаруживает ошибочное зацикливание получателей, расширение для текущего получателя прекращается, а для получателя создается отчет о недоставке.

Обнаружение зацикливания получателей не предотвращает повторную доставку сообщений. Например, сообщения будут повторно доставляться в группу рассылки C, если выполняются следующие условия:

  - группы рассылки B и C являются членами группы рассылки A;

  - группа рассылки C также является членом группы рассылки B.

## Перенаправление отчета о доставке для групп рассылки

При расширении группы рассылки проверяется тип сообщения, чтобы определить, является ли оно отчетом о доставке. Если сообщение является отчетом о доставке, проверяются параметры перенаправления для группы рассылки, чтобы определить, требуется ли перенаправление отчета о доставке. Можно запрещать отправку отчетов о доставке, так как такие отчеты могут содержать сведения о группе рассылки и ее членах, которые нежелательно разглашать.

В представленном ниже списке описаны параметры перенаправления отчета о доставке для групп рассылки и динамических групп рассылки.

  - **ReportToManagerEnabled**.    Этот параметр включает отправку отчетов о доставке диспетчеру группы рассылки. Допустимы следующие значения: `$true` и `$false`. По умолчанию параметр имеет значение `$false`. Для групп рассылки диспетчер определяется параметром *ManagedBy* командлета **Set-Group**. Для динамических групп рассылки диспетчер определяется параметром *ManagedBy* командлета **Set-DynamicDistributionGroup**.

  - **ReportToOriginatorEnabled**.   Этот параметр включает отправку отчетов о доставке отправителю сообщений электронной почты в данную группу рассылки. Допустимы следующие значения: `$true` и `$false`. По умолчанию параметр имеет значение `$true`.
    
    <table>
    <thead>
    <tr class="header">
    <th><img src="images/JJ126620.note(EXCHG.150).gif" title="Примечание" alt="Примечание" />Примечание.</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td>Параметры <em>ReportToManagerEnabled</em> и <em>ReportToOriginatorEnabled</em> не могут одновременно иметь значение <code>$true</code>. Если значение одного параметра равно <code>$true</code>, то для другого параметра необходимо установить значение <code>$false</code>. Оба параметра могут иметь значение <code>$false</code>. При этом никакие сообщения отчетов о доставке не отправляются.</td>
    </tr>
    </tbody>
    </table>


В списке ниже перечислены доступные отчеты о доставке.

  - **Отчет о доставке**.   Данный отчет подтверждает, что сообщение было доставлено получателю, для которого оно предназначалось.

  - **Уведомление о доставке**.   В этом отчете описывается результат попытки доставки сообщения. Дополнительные сведения об уведомлениях о доставке см. в разделе [Уведомления о доставке и отчеты о недоставке в Exchange 2013](dsns-and-ndrs-in-exchange-2013-exchange-2013-help.md).

  - **Уведомление о состоянии сообщения**.   В этом отчете описывается состояние сообщения после успешной доставки получателю. Примерами таких сообщений являются уведомление о прочтении и уведомление о непрочтении. Уведомления о доставке почты определены в RFC 2298 и контролируются полем **Disposition-Notification-To:** в заголовке сообщения. Параметры уведомления о доставке почты, использующие поле заголовка `Disposition-Notification-To:`, совместимы с многими различными серверами обмена сообщениями. Параметры уведомления о доставке почты также можно определить с помощью свойств Microsoft Outlook и Exchange.

  - **Отчет о недоставке**.   Этот отчет сообщает отправителю сообщения о том, что оно не было доставлено указанным получателям.

  - **Уведомление о непрочтении**.   Этот отчет указывает на то, что сообщение было удалено, перед тем как оно было прочитано.

  - **Нет на месте (OOF)**.   Этот отчет указывает на то, что получатель не ответит на сообщения электронной почты. Аббревиатура OOF относится к первоначальной системе обмена сообщениями Microsoft, в которой соответствующее уведомление называлось «Out of facility» (Вне помещения).

  - **Уведомление о прочтении**.   Этот отчет указывает на то, что сообщение было прочитано.

  - **Отчет об отзыве**.   Этот отчет содержит сведения о состоянии запроса на отзыв для данного получателя. Запрос на отзыв — это попытка отправителя отозвать отправленное сообщение с помощью Outlook.

При отправке отчета о доставке в группу рассылки указанные ниже параметры приводят к его удалению.

  - Не задано перенаправление отчета, или отчет перенаправляется отправителю сообщения.

  - Отчет перенаправляется диспетчеру группы рассылки, а сообщение отчета о доставке не является отчетом о недоставке.

Отчет о доставке, отправленный в группу рассылки, может быть доставлен диспетчеру группы рассылки. Это происходит, когда настроено перенаправление отчета диспетчеру группы рассылки и сообщение является отчетом о недоставке.

При отправке сообщения, которое не является отчетом о доставке, в группу рассылки оно доставляется участникам группы рассылки. Параметры запроса отчетов описаны в приведенном ниже списке.

  - Если установлено перенаправление отчетов отправителю сообщения, параметры запроса отчетов не изменяются.

  - Если перенаправление отчетов не установлено, все параметры запроса отчетов подавляются. В конверт сообщения для каждого получателя добавляется параметр `NOTIFY=NEVER` для команды **RCPT TO:** .

  - Если установлено перенаправление отчетов диспетчеру группы рассылки, все параметры запроса отчетов подавляются, кроме отчетов о недоставке, которые отправляются диспетчеру группы рассылки.

## Ограничения для получателей сообщения

При расширении также применяются ограничения для получателей сообщения. Такие ограничения могут быть настроены отдельно для каждого получателя или на уровне организации — для всех транспортных серверов-концентраторов в организации Exchange. В представленной ниже таблице описаны ограничения для получателей сообщения.

### Ограничения для получателей сообщения

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Источник</th>
<th>Параметр</th>
<th>Описание</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>Set-DistributionGroup</strong></p>
<p><strong>Set-DynamicDistributionGroup</strong></p>
<p><strong>Set-Mailbox</strong></p>
<p><strong>Set-MailContact</strong></p>
<p><strong>Set-MailPublicFolder</strong></p>
<p><strong>Set-MailUser</strong></p>
<p><strong>Set-TransportConfig</strong></p></td>
<td><p><em>MaxReceiveSize</em></p></td>
<td><p>В качестве параметра <em>MaxReceiveSize</em>, используемого для ограничения размера сообщений получателей, выступает значение поля <strong>X-MS-Exchange-Organization-OriginalSize:</strong> в заголовке сообщения. Это поле заголовка используется в Exchange для записи исходного размера сообщения при его поступлении в организацию Exchange. При проверке сообщения на соответствие ограничениям размера сообщения используется меньшее значение текущего размера сообщения или исходного размера заголовка сообщения. Размер сообщения может изменяться из-за преобразования содержимого, кодирования или обработки агентом. Если это поле заголовка отсутствует, оно создается с использованием значения текущего размера сообщения. Если сообщение имеет слишком большой размер, создается отчет о недоставке, а дальнейшая обработка сообщения прекращается.</p></td>
</tr>
<tr class="even">
<td><p><strong>Set-DistributionGroup</strong></p>
<p><strong>Set-DynamicDistributionGroup</strong></p>
<p><strong>Set-Mailbox</strong></p>
<p><strong>Set-MailContact</strong></p>
<p><strong>Set-MailPublicFolder</strong></p>
<p><strong>Set-MailUser</strong></p></td>
<td><p><em>RequireSenderAuthenticationEnabled</em></p></td>
<td><p>Параметр <em>RequireSenderAuthenticationEnabled</em> разрешает доставку получателю сообщений только от отправителей, прошедших проверку подлинности. Если для этого параметра установлено значение <code>$true</code>, сообщения от отправителей, не прошедших проверку подлинности, отклоняются. Все отправители сообщений в системный почтовый ящик и почтовый ящик системного помощника должны проходить проверку подлинности.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Set-DistributionGroup</strong></p>
<p><strong>Set-DynamicDistributionGroup</strong></p>
<p><strong>Set-Mailbox</strong></p>
<p><strong>Set-MailContact</strong></p>
<p><strong>Set-MailPublicFolder</strong></p>
<p><strong>Set-MailUser</strong></p></td>
<td><p><em>AcceptMessagesOnlyFromSendersOrMembers</em></p>
<p><em>RejectMessagesFromSendersOrMembers</em></p></td>
<td><p>Параметр <em>AcceptMessagesOnlyFromSendersOrMembers</em> указывает отправителей или группы рассылки, которым разрешается отправлять сообщения данному получателю. Обратите внимание, что этот параметр совмещает функции устаревших параметров <em>AcceptMessagesOnlyFrom</em> и <em>AcceptMessagesOnlyFromDLMembers</em>.</p>
<p>Параметр <em>RejectMessagesFromSendersOrMembers</em> указывает отправителей или группы рассылки, которым не разрешается отправлять сообщения данному получателю. Обратите внимание, что этот параметр совмещает функции устаревших параметров <em>RejectMessagesFrom</em> и <em>RejectMessagesFromDLMembers</em>.</p>
<p>Классификатор проверяет разрешения для получателей в два этапа. На первом этапе определяется, указан ли отправитель в параметре <em>AcceptOnlyMessagesFromSendersOrMembers</em> или <em>RejectMessagesFromSendersOrMembers</em>. Если отправитель не указан ни в одном из этих параметров, группы рассылки, заданные в этих параметрах, полностью расширяются. Полное расширение групп рассылки может занять некоторое время. Рекомендуется использовать как можно меньшую глубину вложенности групп рассылки для этих параметров.</p></td>
</tr>
</tbody>
</table>


Ограничения не распространяются на некоторые типы сообщений, отправляемых прошедшими проверку отправителями. Такие виды сообщений описаны ниже.

  - **Все сообщения, отправленные получателем Microsoft Exchange**.   К таким сообщениям относятся уведомления о доставке, отчеты журнала, сообщения о квоте, а также другие сообщения, создаваемые системой и отправляемые внутренним отправителям сообщений. Дополнительные сведения о получателе Microsoft см. в разделе [Получатели](recipients-exchange-2013-help.md).

  - **Все сообщения, отправленные с внешнего адреса администратора почты**.   К таким сообщениям относятся уведомления о доставке и другие сообщения, создаваемые системой и отправляемые внешним отправителям сообщений. Дополнительные сведения о внешнем адресе администратора почты см. в разделе [Настройка внешнего адреса администратора почты](configure-the-external-postmaster-address-exchange-2013-help.md).

Некоторые типы сообщений блокируются при отправке из организации Exchange во внешние домены. Это определяется следующими параметрами командлета **Set-RemoteDomain**:

  - *AllowedOOFType*

  - *AutoForwardEnabled*

  - *AutoReplyEnabled*

  - *DeliveryReportEnabled*

  - *NDREnabled*

Дополнительные сведения см. в разделе [Удаленные домены](remote-domains-exchange-2013-help.md).

В начало

## Развертывание и контроль расширения получателей

Так как при разрешении получателей расширяется и разрешается полный список получателей сообщения, в некоторых случаях необходимо создать несколько копий одного сообщения. Это происходит в описанных ниже ситуациях.

  - **Для получателей сообщений установлены различные параметры сообщений**.   Свойства сообщения, такие как отправка уведомлений о прочтении, могут быть включены для одних получателей и заблокированы для других. Создание новой версии сообщения, свойства которой немного отличаются от свойств исходного сообщения, называется *развертыванием*.

  - **Ограничение количества получателей конверта для одного сообщения**.   При расширении получателей для крупных групп рассылки могут создаваться тысячи отдельных получателей. В Exchange вместо создания одной копии сообщения с тысячами получателей конверта создается несколько копий одного сообщения с ограниченным количеством получателей конверта.

## Развертывание

Развертывание происходит при разрешении получателей, если выполняются указанные ниже условия.

  - Обновляется отправитель сообщения, указанный в команде **MAIL FROM:** конверта сообщения (например, если параметр *ReportToManagerEnabled* для группы рассылки имеет значение `$true`).

  - Требуется запретить сообщения автоответа, такие как уведомления о доставке, сообщения об отсутствии на работе и отчеты об отзыве.

  - Расширяются альтернативные получатели.

  - Поле заголовка **Resent-From:** необходимо добавить в заголовок сообщения. Поля заголовков Resent — это информационные поля заголовков, по которым можно определить, было ли сообщение переадресовано пользователем. Поля Resent применяются для того, чтобы сообщение выглядело так, как если бы оно было отправлено непосредственно исходным отправителем. Просмотрев заголовок сообщения, получатель может узнать, кто переадресовал сообщение. Поля заголовков Resent определяются в разделе 3.6.6 документа RFC 2822.

  - Требуется передать журнал расширения группы рассылки.

## Контроль расширения получателей

Если количество получателей после расширения слишком большое, классификатор разделяет сообщение на несколько копий. Это выполняется для снижения использования системных ресурсов при расширении сообщения. Максимальное количество получателей конверта для сообщения определяется параметром *ExpansionSizeLimit* в файле конфигурации приложения `%ExchangeInstallPath%Bin\EdgeTransport.exe.config`. Значение по умолчанию — 1000.

<table>
<thead>
<tr class="header">
<th><img src="images/Dd876857.Caution(EXCHG.150).gif" title="Внимание!" alt="Внимание!" />Внимание!</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Не рекомендуется изменять значение параметра <em>ExpansionSizeLimit</em> для транспортного сервера Exchange в рабочей среде.</td>
</tr>
</tbody>
</table>


В начало

## Диагностика разрешения получателей

Отчеты и диагностические сведения для разрешения получателей предоставляются счетчиками производительности и журналом отслеживания сообщений. Эти источники позволяют определять и диагностировать проблемы с разрешением получателей.

## Счетчики производительности разрешения получателей

В представленной ниже таблице описаны счетчики производительности для разрешения получателей.

### Счетчики производительности разрешения получателей

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Имя счетчика</th>
<th>Отображаемое имя</th>
<th>Описание</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>AmbiguousRecipientsTotal</p></td>
<td><p>Неоднозначных получателей</p></td>
<td><p>Общее количество неоднозначных получателей, обнаруженных при разрешении получателей. Неоднозначные получатели — это различные получатели с совпадающими атрибутами Active Directory <strong>legacyExchangeDN</strong> или <strong>proxyAddresses</strong>.</p></td>
</tr>
<tr class="even">
<td><p>AmbiguousSendersTotal</p></td>
<td><p>Неоднозначных отправителей</p></td>
<td><p>Общее количество неоднозначных отправителей, обнаруженных при разрешении получателей. Неоднозначные отправители — это различные отправители с совпадающими атрибутами Active Directory <strong>legacyExchangeDN</strong> или <strong>proxyAddresses</strong>.</p></td>
</tr>
<tr class="odd">
<td><p>FailedRecipientsTotal</p></td>
<td><p>Неудачных получателей</p></td>
<td><p>Общее количество получателей, которых не удалось разрешить, обнаруженных при разрешении получателей.</p></td>
</tr>
<tr class="even">
<td><p>LoopRecipientsTotal</p></td>
<td><p>Зацикленных получателей</p></td>
<td><p>Общее количество получателей, которых не удалось разрешить из-за зацикливания получателей.</p></td>
</tr>
<tr class="odd">
<td><p>MessagesChippedTotal</p></td>
<td><p>Усеченных сообщений</p></td>
<td><p>Общее количество копий одного сообщения, созданных при разрешении получателей для контроля числа получателей конверта одного сообщения. В Exchange этот процесс называется <em>усечением</em>.</p></td>
</tr>
<tr class="even">
<td><p>MessagesCreatedTotal</p></td>
<td><p>Создано сообщений</p></td>
<td><p>Количество сообщений, созданных при разрешении получателей.</p></td>
</tr>
<tr class="odd">
<td><p>MessagesRetriedTotal</p></td>
<td><p>Повторных попыток доставки сообщений</p></td>
<td><p>Количество сообщений, для которых была запланирована повторная попытка при разрешении получателей.</p></td>
</tr>
<tr class="even">
<td><p>UnresolvedOrgRecipientsTotal</p></td>
<td><p>Получателей с нераспознанной организацией</p></td>
<td><p>Количество неразрешенных получателей из уполномоченного домена, обнаруженных при разрешении получателей.</p></td>
</tr>
<tr class="odd">
<td><p>UnresolvedOrgSendersTotal</p></td>
<td><p>Отправителей с нераспознанной организацией</p></td>
<td><p>Количество неразрешенных отправителей из уполномоченного домена, обнаруженных при разрешении получателей.</p></td>
</tr>
</tbody>
</table>


## События разрешения получателей в журнале отслеживания сообщений

В представленной ниже таблице описаны события разрешения получателей, которые регистрируются в журнале отслеживания сообщений.

### События разрешения получателей в журнале отслеживания сообщений

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Событие отслеживания сообщений</th>
<th>Описание</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>EXPAND</p></td>
<td><p>Это событие указывает на то, что группа рассылки была расширена.</p></td>
</tr>
<tr class="even">
<td><p>REDIRECT</p></td>
<td><p>Это событие указывает на то, что сообщение, отправленное в почтовый ящик или общую папку с поддержкой почты, было перенаправлено альтернативному получателю, заданному параметром <em>ForwardingAddress</em>.</p></td>
</tr>
<tr class="odd">
<td><p>RESOLVE</p></td>
<td><p>Это событие показывает, что адрес электронной почты получателя был изменен на основной SMTP-адрес соответствующего объекта получателя Active Directory.</p></td>
</tr>
<tr class="even">
<td><p>TRANSFER</p></td>
<td><p>Это событие указывает на то, что произошло развертывание или усечение сообщения.</p></td>
</tr>
</tbody>
</table>


Дополнительные сведения об отслеживании сообщений см. в разделе [Отслеживание сообщений](message-tracking-exchange-2013-help.md).

