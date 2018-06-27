﻿---
title: 'Защита голосовой почты: Exchange 2013 Help'
TOCTitle: Защита голосовой почты
ms:assetid: a88d41d5-2e70-4193-bcd3-dec50dff412b
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Dd351041(v=EXCHG.150)
ms:contentKeyID: 52059221
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Защита голосовой почты

 

_**Применимо к:**Exchange Online, Exchange Server 2013, Exchange Server 2016_

_**Последнее изменение раздела:**2016-12-09_

Некоторые устаревшие учрежденческие автоматические телефонные станции (УАТС) и УАТС на основе протокола IP позволяют абоненту отмечать сообщение голосовой почты как личное, блокируя тем самым возможность получателю пересылать сообщение другим пользователям. В интегрированных системах голосовой почты доступ к голосовому сообщению возможен несколькими способами, что затрудняет защиту голосового сообщения, отмеченного как личное, от нежелательных слушателей.

Единую систему обмена сообщениями можно настроить для использования Active Directory службы управления правами Active Directory для защиты голосовых сообщений организации. Эта функция известна как "Защищенные сообщения голосовой почты".

Если голосовое сообщение защищено, выполняется не только блокировка возможности переадресации для получателя. Единая система обмена сообщениями также гарантирует, что только назначенный получатель или назначенные получатели сообщения смогут получить доступ к его содержимому. Доступ к защищенным голосовым сообщениям можно получить с помощью МайкрософтOutlook 2010 или более поздней версии, Outlook Web App или голосового доступа Outlook.

**Содержание**

Overview of Protected Voice Mail

Overview of Active Directory Rights Management Services

Client support and end-user features

Protected voice mail structure

Composing a Protected Voice Mail message

UM mailbox policies

Text message notifications and Protected Voice Mail

## Общие сведения о защищенной голосовой почте

В единой системе обмена сообщениями Exchange 2010 и более поздних версий доступна функция защищенной голосовой почты. Ее можно настроить в политике почтовых ящиков единой системы обмена сообщениями, а все параметры защищенной голосовой почты — в консоли управления Exchange или командной консоли Exchange 2010, а также в Центре администрирования Exchange или с помощью командлетов командной консоли Exchange 2013.

Защищенная голосовая почта реализуется путем применения системы управления правами на доступ к данным (IRM) к голосовым сообщениям. Если голосовые сообщения защищены с помощью единой системы обмена сообщениями:

  - Пользователь может отвечать на защищенные голосовые сообщения.

  - Получатели голосового сообщения не могут переадресовать его.

  - Пользователи не могут сохранять копии голосового сообщения.

  - Пользователи не могут сохранить или скопировать вложенную звуковую запись голосового сообщения.

  - Голосовое сообщение может быть открыто только назначенным пользователем или назначенными пользователями.

Голосовые сообщения автоответчика и межабонентские голосовые сообщения (голосовые сообщения, отправляемые пользователю с помощью голосового доступа к Outlook) могут быть защищены единой системой обмена сообщениями. Однако защита не будет применена к следующим типам сообщений:

  - факсимильные сообщения;

  - неголосовые сообщения. Например, сообщения электронной почты или приглашения на собрания, даже если они созданы с помощью голосового доступа к Outlook (голосовые ответы).

В начало

## Обзор служб управления правами Active Directory

Компонент AD RMS в Windows Server 2008 или в более поздних версиях позволяет обеспечить защиту файлов и делает файл доступным для просмотра только тем пользователям, которых назначил отправитель. AD RMS защищает файл путем назначения прав, которыми должен обладать пользователь для доступа к файлу. Можно настроить права для разрешения открывать, изменять, печатать, переадресовывать или предпринимать другие действия относительно данных, к которым применяются права. При помощи AD RMS можно защитить данные при их распространении вне сети организации.

Система AD RMS включает в себя компонент сервера и клиента, в частности:

  - Сервер, на котором установлен Windows Server 2008 R2 или его более поздние версии и который выполняет роль сервера служб управления правами Active Directory, предназначенного для обработки сертификатов и лицензий.

  - сервер базы данных;

  - клиент службы управления правами Active Directory. Последняя версия клиента AD RMS включена в состав операционных систем Windows 7 и Windows 8.

Компонент сервера состоит из нескольких веб-служб, которые выполняются на сервере Майкрософт, например Windows Server 2008 или более поздней версии. Компонент клиента может быть запущен в операционной системе клиента или сервера и включает в себя функции, позволяющие приложению зашифровывать и расшифровывать содержимое, получать шаблоны и списки отзыва, а также получать лицензии и сертификаты с сервера.

С помощью службы управления правами и клиента службы управления правами, можно дополнить стратегию безопасности организации путем защиты данных с помощью постоянных политик использования, которые остаются со сведениями, независимо от того, где он перемещается. Можно использовать службы управления правами для предотвращения конфиденциальной информации, например финансовых отчетов, технические характеристики, пользовательских данных и confidential электронной почты и голосовых сообщений — от случайного или намеренного попадания в руки. Для получения дополнительных сведений см [AD RMS Обзор](https://go.microsoft.com/fwlink/p/?linkid=199436).

В единой системе обмена сообщениями Exchange для обеспечения постоянной защиты сообщений и вложений можно использовать функции управления правами на доступ к данным (IRM).

Использование функций управления правами на доступ к данным и защищенной голосовой почты позволит организации и ее пользователям управлять правами получателей на доступ к сообщениям электронной и голосовой почты. С помощью управления правами на доступ к данным можно также разрешить или запретить получателю пересылать сообщение другим получателям, печатать сообщение или вложения, а также копировать текст сообщения или вложений.

## Требования к управлению правами на доступ к данным

Перед реализацией IRM в Exchange, необходимо развернуть и настройки инфраструктуры службы управления правами. Для получения дополнительных сведений см [Служб управления правами Active Directory](https://go.microsoft.com/fwlink/p/?linkid=199439). Чтобы реализовать IRM для поддержки защищенную голосовую почту в организации Exchange, развертывание должно соответствовать следующим требованиям.


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Сервер</th>
<th>Требования</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Кластер AD RMS</p></td>
<td><ul>
<li><p>Windows Server 2008 R2 Standard или Enterprise с пакетом обновления 1 (SP1), или Windows Server 2012 Standard или Datacenter. Дополнительные сведения о системных требованиях см. в разделе <a href="exchange-2013-system-requirements-exchange-2013-help.md">Требования к системе для установки Exchange 2013</a>.</p></li>
<li><p><strong>Точка подключения службы (SCP)</strong>   Exchange 2013 и приложения с поддержкой AD RMS используют точку подключения службы, зарегистрированную в Active Directory, для обнаружения кластеров AD RMS и URL-адресов. Служба AD RMS позволяет регистрировать точку подключения службы в программе установки AD RMS. Если при установке AD RMS используется учетная запись, которая не является участником группы безопасности &quot;Администраторы предприятия&quot;, регистрацию точки подключения службы можно выполнить после завершения установки. В лесу Active Directory существует только одна точка подключения службы AD RMS.</p></li>
<li><p><strong>Разрешения</strong>   Группа серверов Exchange или отдельные серверы Exchange должны иметь разрешения на чтение и выполнение в механизме сертификации сервера AD RMS. Путь по умолчанию на серверах AD RMS: \inetpub\wwwroot\_wmcs\certification\ServerCertification.asmx.</p></li>
<li><p><strong>Суперпользователи AD RMS</strong>   Для включения функций расшифровки транспорта и отчетов по журналу, управления правами на доступ к данным в приложении Outlook Web App и в службе поиска Exchange необходимо добавить почтовый ящик федеративной доставки (системный почтовый ящик, созданный программой установки Exchange) в группу суперпользователей в кластере AD RMS. Подробные сведения см. в разделе <a href="add-the-federation-mailbox-to-the-ad-rms-super-users-group-exchange-2013-help.md">Добавление федеративного почтового ящика в группу суперпользователей службы управления правами Active Directory</a>.</p></li>
</ul></td>
</tr>
</tbody>
</table>


## Настройка и тестирование управления правами на доступ к данным

Для настройки функций управления правами на доступ к данным необходимо использовать консоль. Чтобы настроить отдельные функции управления правами на доступ к данным, используйте командлет [Set-IRMConfiguration](https://technet.microsoft.com/ru-ru/library/dd979792\(v=exchg.150\)). Для получения дополнительных сведений о настройке функций управления правами на доступ к данным см. раздел [Сведения о процедуры управления правами](information-rights-management-procedures-exchange-2013-help.md).

После настройки сервера Exchange можно выполнить сквозное тестирование развертывания службы управления правами на доступ к данным с помощью командлета [Test-IRMConfiguration](https://technet.microsoft.com/ru-ru/library/dd979798\(v=exchg.150\)). Этот командлет проверяет конфигурацию IRM для организации; его необходимо запустить до активации функции защищенной голосовой почты. Командлет **Test-IRMConfiguration** выполняет следующие тесты:

  - Проверяет конфигурацию службы управления правами на доступ к данным в организации Exchange.

  - Проверяет сервер службы AD RMS на предмет сведений о версии и исправлениях.

  - Проверяет возможность активации сервера Exchange для службы управления правами, получая сертификат учетной записи прав и сертификат лицензиара клиента (CLC).

  - Получает шаблоны политики прав службы AD RMS с сервера службы AD RMS.

  - Проверяет способность указанного отправителя отправлять сообщения, защищенные службой IRM.

  - Получает для указанного получателя лицензию на использование суперпользователя.

  - Получает предварительную лицензию для указанного получателя.

В начало

## Поддержка клиента и возможности конечных пользователей

Программное обеспечение почтового клиента, используемого для прослушивания сообщений защищенной голосовой почты, должно поддерживать IRM и включать в себя функциональные возможности для чтения голосовых сообщений с защитой единой системы обмена сообщениями. К поддерживаемым почтовым клиентам относятся МайкрософтOutlook 2010 или более поздние версии, Outlook Web App и голосовой доступ к Outlook. Следующая таблица содержит список почтовых клиентов, а также данные об их поддержке.


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Клиент электронной почты</th>
<th>Описание</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Outlook</p></td>
<td><ul>
<li><p>Защищенные голосовые сообщения поддерживаются в Outlook 2010 и более поздних версиях.</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p>Outlook Web App</p></td>
<td><ul>
<li><p>Outlook Web App в Exchange 2010 или более поздних версиях поддерживает сообщения защищенной голосовой почты. Предыдущие версии Outlook Web App, известные как Outlook Web Access, не поддерживают такие сообщения.</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p>Голосовой доступ к Outlook</p></td>
<td><ul>
<li><p>Голосовой доступ к Outlook в Exchange 2010 и более поздних версий поддерживает защищенную голосовую почту. Голосовой доступ к Outlook, входящий в состав Exchange 2007, не поддерживает защищенную голосовую почту.</p></li>
<li><p>Почтовый ящик пользователя должен находиться на сервере почтовых ящиков Exchange 2010 или более поздней версии.</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p>Windows Mobile или Windows Phone</p></td>
<td><ul>
<li><p>Windows Mobile не поддерживает защищенную голосовую почту. Однако в Windows Phone 7 и Windows Phone 8 поддерживается защищенная голосовая почта.</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p>Exchange ActiveSync</p></td>
<td><ul>
<li><p>Защищенная голосовая почта поддерживается в Exchange 2010 с пакетом обновления 1 (SP1) и более поздних версиях.</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p>Другие почтовые клиенты</p></td>
<td><ul>
<li><p>Защищенная голосовая почта не поддерживается.</p></li>
</ul></td>
</tr>
</tbody>
</table>


В начало

## Защищенная структура голосовых сообщений

Для каждого сообщения защищенной голосовой почты фактически существует два сообщения. Первое сообщение является внешним сообщением, которое не шифруется. Оно содержит вложение с именем message.rpmsg. Вложение содержит голосовое сообщение с защитой IRM и внутренние данные управления правами. Данные управления правами включают в себя ключ содержимого и информацию о правах, указывающую пользователей, которым разрешен доступ к голосовому сообщению, и способ доступа к нему.

Защищенные голосовые сообщения отображаются во входящих сообщениях пользователя в папке **Голосовая почта**. Пользователь может прослушать голосовое сообщение при помощи встроенного проигрывателя так же, как обычное голосовое сообщение, за исключением того, что кнопка "Переслать" будет неактивна, а в верхней области сообщения будет выведено примечание с сообщением о том, что сообщение защищено и не может быть переадресовано.

В почтовых клиентах, не поддерживающих защищенную голосовую почту, будет отображен текст внешнего сообщения. Администраторы могут включать текст, когда клиентское программное обеспечение не поддерживает защищенную голосовую почту, с помощью политик почтовых ящиков единой системы обмена сообщениями. Стандартный текст, включаемый в сообщение электронной почты, можно изменить в настройках политики почтовых ящиков единой системы обмена сообщениями. Например, можно настроить политику почтовых ящиков единой системы обмена сообщениями, введя, к примеру, следующий пользовательский текст: *"Вы не можете открыть это голосовое сообщение, потому что оно защищено. Для просмотра или прослушивания этого голосового сообщения войдите на ваш почтовый ящик на сайте https://mail.contoso.com или позвоните по номеру +1 (425) 555-1234 для голосового доступа к приложению Outlook".*

В начало

## Создание защищенного сообщения голосовой почты

Существуют две ситуации, в которых можно создать защищенные голосовые сообщения.

  - **Автоответчик**.   Функция автоответчика необходима, если абонент звонит пользователю с включенной единой системой обмена сообщениями, но пользователь недоступен или переадресует абонента непосредственно к голосовой почте. В сценариях автоответчика система голосовой почты проиграет серию голосовых запросов после записи голосового сообщения звонящего.
    
    Затем звонящий может выбрать дополнительные параметры сообщения, включая возможность отметить голосовое сообщение как личное, нажав кнопку с решеткой (\#). При нажатии кнопки \# можно следовать инструкциям, предоставляемым единой системой обмена сообщениями, для пометки сообщения как личного, удалить отметку из личного голосового сообщения или отметить голосовое сообщение как сообщение с высокой степенью важности. На схеме ниже изображены параметры меню, доступные звонящим при записи личного голосового сообщения для пользователя.
    
    <table>
    <thead>
    <tr class="header">
    <th><img src="images/JJ126620.note(EXCHG.150).gif" title="Примечание" alt="Примечание" />Примечание.</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td>Для звонков на автоответчик параметры настройки защищенной голосовой почты в политике почтовых ящиков единой системы обмена сообщениями назначенного получателя сообщения используются единой системой обмена сообщениями, поскольку звонящий не прошел проверку подлинности.</td>
    </tr>
    </tbody>
    </table>
    
    **Создание защищенных сообщений голосовой почты с помощью автоответчика**
    
    ![Создание защищенных сообщений голосовой почты с помощью автоответчика](images/Dd351041.4e9f50bf-5066-4d0a-b3eb-0515a2fc4560(EXCHG.150).jpg "Создание защищенных сообщений голосовой почты с помощью автоответчика")  

  - **Голосовой доступ к Outlook**.   Голосовой доступ к Outlook позволяет пользователям с включенной единой системой обмена сообщениями получать доступ к почтовому ящику с помощью аналогового, цифрового или сотового телефона при наборе номера голосового доступа к Outlook. Пользователям, имеющим право работы с единой системой обмена сообщениями, доступны два пользовательских интерфейса: телефонный пользовательский интерфейс (TUI) и голосовой пользовательский интерфейс (VUI).
    
    Пользователи голосового доступа к Outlook могут выполнять поиск контактов в каталоге и отправлять им голосовые сообщения. При активации защищенной голосовой почты для получателей с включенной единой системой обмена сообщениями звонящие могут отмечать сообщения как личные после их записи. Также администраторы могут настроить политику почтовых ящиков единой системы голосовой почты для обеспечения защиты всех голосовых сообщений, отправляемых пользователями, прошедшими проверку подлинности, в единой системе обмена сообщениями.
    
    <table>
    <thead>
    <tr class="header">
    <th><img src="images/JJ126620.note(EXCHG.150).gif" title="Примечание" alt="Примечание" />Примечание.</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td>Если звонящий прошел проверку подлинности, применяются параметры настройки защищенной голосовой почты в политике почтовых ящиков единой системы обмена сообщениями, связанные со звонящим, вне зависимости от параметров настройки политики почтовых ящиков единой системы обмена сообщениями для назначенного получателя сообщения голосовой почты.</td>
    </tr>
    </tbody>
    </table>
    
    **Создание защищенного голосового сообщения с помощью голосового интерфейса пользователя**
    
    ![Создание защищенных сообщений голосовой почты с помощью голосового интерфейса](images/Dd351041.6b425ee4-5171-4a63-961f-bdbc6c79e1be(EXCHG.150).jpg "Создание защищенных сообщений голосовой почты с помощью голосового интерфейса")  
    
    **Создание защищенных голосовых сообщений с помощью телефонного интерфейса пользователя**
    
    ![Создание защищенной голосовой почты с помощью тонового интерфейса](images/Dd351041.dd58fd38-c4c3-437c-adc1-497deb3c8a9f(EXCHG.150).jpg "Создание защищенной голосовой почты с помощью тонового интерфейса")  

В начало

## Политики почтовых ящиков единой системы обмена сообщениями

Можно создать политику почтовых ящиков единой системы обмена сообщениями для применения общего набора параметров политики единой системы обмена сообщениями, таких как параметры политики ПИН-кодов, ограничения набора номеров и параметры защищенной голосовой почты, к коллекции почтовых ящиков с включенной функцией единой системы обмена сообщениями. Дополнительные сведения о политиках почтовых ящиков единой системы обмена сообщениями см. в разделе [Управление политикой почтовых ящиков единой системы обмена СООБЩЕНИЯМИ](manage-a-um-mailbox-policy-exchange-2013-help.md).

Можно использовать Центр администрирования Exchange или командлет **Set-UMMailboxPolicy** в командной консоли для настройки параметров защищенной голосовой почты. В следующей таблице представлены параметры, которые можно настроить для защищенной голосовой почты.

**Параметры настройки защищенной голосовой почты**


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Параметр командной консоли</th>
<th>Возможность установки в Центре администрирования Exchange</th>
<th>Описание</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><em>ProtectAuthenticatedVoiceMail</em></p></td>
<td><p>Да</p></td>
<td><p>Параметр <em>ProtectAuthenticatedVoiceMail</em> указывает возможность пользователей с включенной единой системой обмена сообщениями отправлять защищенные голосовые сообщения при доступе к почтовому ящику с помощью функции голосового доступа к Outlook. Значение по умолчанию — <code>None</code>. Это означает, что при создании голосовых сообщений не применяется защита, и звонящие не будут иметь возможность пометки голосового сообщения как личного. Если параметр имеет значение <code>Private</code>, защищены только сообщения, отмеченные как личные. При установке значения <code>All</code> защищены все голосовые сообщения вне зависимости от параметра, выбранного пользователем.</p></td>
</tr>
<tr class="even">
<td><p><em>ProtectUnauthenticatedVoiceMail</em></p></td>
<td><p>Да</p></td>
<td><p>Параметр <em>ProtectUnauthenticatedVoiceMail</em> указывает, будут ли серверы почтовых ящиков, которые отвечают на вызовы голосового доступа для пользователей, связанных с политикой почтовых ящиков единой системы обмена сообщениями, создавать защищенные сообщения голосовой почты. Эта настройка применима и в случае, если сообщение отправляется от автосекретаря единой системы обмена сообщениями пользователю с включенной единой системой обмена сообщениями. Значение по умолчанию — <code>None</code>. Это означает, что голосовые сообщения не защищены, и звонящему не будет предоставлена возможность пометки сообщения как личного. Если параметр имеет значение <code>Private</code>, защищены только сообщения, отмеченные как личные. При установке значения <code>All</code> защищены все голосовые сообщения вне зависимости от пометки сообщения как личного пользователем.</p></td>
</tr>
<tr class="odd">
<td><p><em>ProtectedVoiceMailText</em></p></td>
<td><p>Да</p></td>
<td><p>Параметр <em>ProtectedVoiceMailText</em> указывает текст, включаемый в тело внешнего сообщения для сообщения защищенной голосовой почты. Текст будет отображен во всех приложениях почтового клиента, не поддерживающих сообщения защищенной электронной почты. Обратите внимание, что при установке для данного параметра значения <code>Null</code> или отсутствии значения предоставляется стандартное сообщение единой системы обмена сообщениями.</p></td>
</tr>
<tr class="even">
<td><p><em>RequireProtectedPlayOnPhone</em></p></td>
<td><p>Да</p></td>
<td><p>Параметр <em>RequireProtectedPlayOnPhone</em> указывает на необходимость прослушивания защищенного голосового сообщения по телефону (при помощи функции воспроизведения на телефоне) для пользователей, связанных с политикой почтовых ящиков единой системы обмена сообщениями. Значением по умолчанию является значение <code>$false.</code> Если для параметра установлено значение <code>$true</code>, проигрыватель в формах защищенной голосовой почты в Outlook или Outlook Web App будет неактивен. Обратите внимание, что текст предварительного просмотра голосового сообщения доступен в любой момент. Пользователь не сможет воспроизвести звуковой файл ни в одном проигрывателе или использовать встроенный проигрыватель для прослушивания голосового сообщения.</p></td>
</tr>
<tr class="odd">
<td><p><em>AllowVoiceResponseToOtherMessageTypes</em></p></td>
<td><p>Да</p></td>
<td><p>Параметр <em>AllowVoiceResponseToOtherMessageTypes</em> указывает, могут ли абоненты, прошедшие проверку подлинности в голосовом доступе к Outlook для доступа к электронной почте, создавать голосовой ответ на сообщения электронной почты или приглашения на собрания.</p></td>
</tr>
</tbody>
</table>


Для получения дополнительных сведений об управлении параметрами настройки защищенной голосовой почты см. разделы [Защищенные процедуры голосовой почты](protected-voice-mail-procedures-exchange-2013-help.md) и [Set-UMMailboxPolicy](https://technet.microsoft.com/ru-ru/library/bb124903\(v=exchg.150\)).

В начало

## Текстовые уведомления и защищенная голосовая почта

Пользователи, настраивающие в учетной записи единой системы обмена сообщениями отправку текстовых уведомлений (также называются SMS-уведомлениями) на мобильный телефон в случае получения голосового сообщения, также получат текст транскрипции записи (предварительный просмотр голосовой почты) в составе текста сообщения. Однако для защищенных голосовых сообщений такая настройка нарушит политику безопасности, поскольку содержимое голосового сообщения должно быть защищено всегда.

При создании в единой системе обмена сообщениями текстового сообщения с уведомлением для защищенного голосового сообщения выполняется проверка на пометку данного голосового сообщения как личного. В случае присутствия такой пометки транскрипция текста не будет добавлена в текстовое сообщение, отправляемое на мобильный телефон. Вместо этого в текстовое сообщение будет включен следующий текст: "Используйте голосовой доступ к Outlook для открытия этого защищенного сообщения голосовой почты".

В начало
