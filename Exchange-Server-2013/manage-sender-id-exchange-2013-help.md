﻿---
title: 'Управление кодом отправителя: Exchange 2013 Help'
TOCTitle: Управление кодом отправителя
ms:assetid: 2e7b646a-8a66-4be7-a7c1-0bd43bb79a5b
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Aa997136(v=EXCHG.150)
ms:contentKeyID: 50487732
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Управление кодом отправителя

 

_**Применимо к:**Exchange Server 2013_

_**Последнее изменение раздела:**2015-04-08_

Функция идентификации отправителей обеспечивается агентом идентификации отправителей. Код отправителя позволяет проверить происхождение сообщения электронной почты благодаря сверке IP-адреса отправителя с предполагаемым владельцем домена отправителя. Фильтрация кодов отправителя выполняется для входящих сообщений, которые поступают из Интернета, но не проходят проверку подлинности. Такие сообщения обрабатываются как внешние сообщения.

## Что нужно знать перед началом работы?

  - Предполагаемое время для завершения каждой процедуры: 5 минут

  - Для выполнения этих процедур необходимы соответствующие разрешения. Сведения о необходимых разрешениях см. в статье Запись «Функции защиты от нежелательной почты» в разделе [Разрешения для защиты от нежелательной почты и вредоносных программ](anti-spam-and-anti-malware-permissions-exchange-2013-help.md).

  - Для выполнения этой процедуры можно использовать только командную консоль.

  - По умолчанию функции защиты от нежелательной почты в транспортной службе на сервере почтовых ящиков не включены. Как правило, функции защиты от нежелательной почты на сервере почтовых ящиков включают, только если организация Exchange не выполняет никакую предварительную фильтрацию нежелательной почты до приема входящих сообщений. Дополнительную информацию см. в статье [Включение функции защиты от нежелательной почты на сервере почтовых ящиков](enable-anti-spam-functionality-on-mailbox-servers-exchange-2013-help.md).

  - Сочетания клавиш для процедур, описанных в этой статье, приведены в статье [Сочетания клавиш в Центре администрирования Exchange](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).

<table>
<thead>
<tr class="header">
<th><img src="images/Bb124558.tip(EXCHG.150).gif" title="Совет" alt="Совет" />Совет.</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Возникли проблемы? Обратитесь за помощью к участникам форумов, посвященных Exchange. Посетите форумы по таким продуктам: <a href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</a>, <a href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</a> или <a href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</a>.</td>
</tr>
</tbody>
</table>


## Что необходимо сделать?

## Использование командной консоли Exchange для включения или отключения кода отправителя

Чтобы отключить идентификацию отправителей, выполните следующую команду:

    Set-SenderIDConfig -Enabled $false

Чтобы включить идентификацию отправителей, выполните следующую команду:

    Set-SenderIDConfig -Enabled $true

<table>
<thead>
<tr class="header">
<th><img src="images/JJ126620.note(EXCHG.150).gif" title="Примечание" alt="Примечание" />Примечание.</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>При отключении идентификации отправителей, соответствующий агент идентификации все еще включен. Чтобы отключить агент идентификации отправителей, выполните следующий командлет: <code>Disable-TransportAgent &quot;Sender ID Agent&quot;</code>.</td>
</tr>
</tbody>
</table>


## Как проверить, что все получилось?

Чтобы проверить успешность включения или выключения идентификации отправителей, выполните следующие действия.

1.  Выполните следующую команду:
    
        Get-SenderIDConfig | Format-List Enabled

2.  Убедитесь, что отображается значение, которое вы настроили.

## Использование командной консоли для настройки действия идентификации отправителя для поддельных сообщений

Чтобы настроить идентификацию отправителей для поддельных сообщений, выполните следующую команду:

    Set-SenderIDConfig -SpoofedDomainAction <StampStatus | Reject | Delete>

Этот пример настраивает агент идентификации отправителей для отклонения всех сообщений, IP-адреса которых не содержатся в списке авторизованных SMTP-серверов отправки в DNS-записи инфраструктуры политики отправителей (SPF) для домена отправителя.

    Set-SenderIDConfig -SpoofedDomainAction Reject

## Как проверить, что все получилось?

Чтобы проверить успешность настройки действия идентификации отправителей для поддельных сообщений, выполните следующие действия.

1.  Выполните следующую команду:
    
        Get-SenderIDConfig | Format-List SpoofedDomainAction

2.  Убедитесь, что отображается значение, которое вы настроили.

## Использование командной консоли для настройки действия идентификации отправителя для временных ошибок

Чтобы настроить идентификацию отправителей для временных ошибок, выполните следующую команду:

    Set-SenderIDConfig -TempErrorAction <StampStatus | Reject | Delete>

В этом примере агент идентификации отправителя настраивается для пометки сообщений, состояние кода отправителя которых невозможно определить вследствие временной ошибки сервера DNS. Сообщение будет обработано другими агентами защиты от нежелательной почты, после чего агент фильтрации содержимого использует пометку для определения значения вероятности нежелательной почты для этого сообщения.

    Set-SenderIDConfig -TempErrorAction StampStatus

Учтите, что значением по умолчанию для параметра *TempErrorAction* является `StampStatus`.

## Как проверить, что все получилось?

Чтобы проверить успешность настройки действия идентификации отправителей для временных ошибок, выполните следующие действия.

1.  Выполните следующую команду:
    
        Get-SenderIDConfig | Format-List TempErrorAction

2.  Убедитесь, что отображается значение, которое вы настроили.

## Использование командной консоли для настройки исключений в доменах отправителя и получателя

Чтобы заменить существующие значения, выполните следующую команду:

    Set-SenderIDConfig -BypassedRecipients <recipient1,recipient2...> -BypassedSenderDomains <domain1,domain2...>

Этот пример настраивает идентификацию отправителей на обход проверки кода отправителя для сообщений, отправленных на адресу kim@contoso.com и john@contoso.com, а также на обход проверки кода отправителя для сообщений, отправленных из домена fabrikam.com.

    Set-SenderIDConfig -BypassedRecipients kim@contoso.com,john@contoso.com -BypassedSenderDomains fabrikam.com

Чтобы добавить или удалить записи, не изменив существующие значения, выполните следующую команду:

    Set-SenderIDConfig -BypassedRecipients @{Add="<recipient1>","<recipient2>"...; Remove="<recipient1>","<recipient2>"...} -BypassedSenderDomains @{Add="<domain1>","<domain2>"...; Remove="<domain1>","<domain2>"...}

Этот пример настраивает агент идентификации отправителя с использованием следующей информации:

  - Добавить chris@contoso.com и michelle@contoso.com в список текущих получателей, обходящих проверку кода отправителя.

  - Удалить tailspintoys.com из списка существующих доменов, обходящих проверку кода отправителя.

<!-- end list -->

    Set-SenderIDConfig -BypassedRecipients @{Add="chris@contoso.com","michelle@contoso.com"} -BypassedSenderDomains @{Remove="tailspintoys.com"}

## Как проверить, что все получилось?

Чтобы проверить успешность настройки исключения доменов получателей и отправителей, выполните следующие действия.

1.  Выполните следующую команду:
    
        Get-SenderIDConfig | Format-List BypassedRecipients,BypassedSenderDomains

2.  Убедитесь, что отображаются значения, которые вы настроили.
