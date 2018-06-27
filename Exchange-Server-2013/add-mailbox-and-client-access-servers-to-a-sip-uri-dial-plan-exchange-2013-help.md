﻿---
title: 'Добавьте серверы клиентского доступа и почтовых ящиков для абонентской группы SIP URI: Exchange 2013 Help'
TOCTitle: Добавьте серверы клиентского доступа и почтовых ящиков для абонентской группы SIP URI
ms:assetid: 17fed308-ff0d-4e61-b9f9-e6680b6eccaa
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Aa996399(v=EXCHG.150)
ms:contentKeyID: 52061205
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Добавьте серверы клиентского доступа и почтовых ящиков для абонентской группы SIP URI

 

_**Применимо к:**Exchange Server 2013, Exchange Server 2016_

_**Последнее изменение раздела:**2013-04-16_

В абонентские группы с универсальным кодом ресурса SIP можно добавлять серверы клиентского доступа и почтовых ящиков. Серверы клиентского доступа и почтовых ящиков не могут быть связаны с абонентскими группами добавочных номеров или E.164, но будут отвечать на все входящие вызовы.

Для правильной работы исходящих вызовов в развертывании Microsoft Lync Server необходимо вручную добавить серверы клиентского доступа и почтовых ящиков во все абонентские группы с универсальным кодом ресурса SIP, созданные для Lync Server.

Дополнительные задачи управления, связанные с абонентскими группами единой системы обмена сообщениями, см. в разделе [Процедуры плана телефонным единой системы обмена СООБЩЕНИЯМИ](um-dial-plan-procedures-exchange-2013-help.md).

## Что нужно знать перед началом работы

  - Предполагаемое время для завершения: менее 1 минуты.

  - Для выполнения этих процедур необходимы соответствующие разрешения. Сведения о необходимых разрешениях см. в статье запись "Абонентская группа единой системы обмена сообщениями" в разделе [Разрешения единой системы обмена сообщениями](unified-messaging-permissions-exchange-2013-help.md).

  - Перед выполнением этих процедур убедитесь, что абонентская группа SIP URI создана. Дополнительные сведения см. в разделе [Создание абонентской группы единой системы обмена сообщениями](create-a-um-dial-plan-exchange-2013-help.md).

  - Сочетания клавиш для процедур, описанных в этой статье, приведены в статье [Сочетания клавиш в Центре администрирования Exchange](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).

<table>
<thead>
<tr class="header">
<th><img src="images/Bb124558.tip(EXCHG.150).gif" title="Совет" alt="Совет" />Совет.</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Возникли проблемы? Обратитесь за помощью к участникам форумов, посвященных Exchange. Посетите форумы по таким продуктам: <a href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</a>, <a href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</a> или <a href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</a>..</td>
</tr>
</tbody>
</table>


## Что необходимо сделать?

## Добавление сервера почтовых ящиков в абонентскую группу с универсальным кодом ресурса SIP с помощью Центра администрирования Exchange

1.  В Центре администрирования Exchange перейдите к разделу **Серверы** \> **Серверы**.

2.  Выберите из списка сервер почтовых ящиков, который необходимо изменить, и нажмите кнопку **Правка**![Значок редактирования](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Значок редактирования").

3.  На странице **Exchange Server** нажмите кнопку **Единая система обмена сообщениями**.

4.  В разделе **Параметры службы единой системы обмена сообщениями** \> **Сопоставленные абонентские группы** щелкните **Добавить**![Значок добавления](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Значок добавления").

5.  В окне **Выбор абонентской группы единой системы обмена сообщениями** выберите абонентскую группу с универсальным кодом ресурса SIP, щелкните **Добавить**, **OK** и **Сохранить**.

## Добавление сервера почтовых ящиков в абонентскую группу с универсальным кодом ресурса SIP с помощью командной консоли

В этом примере сервер почтовых ящиков с именем `MyMailboxServer` добавляется в абонентскую группу с универсальным кодом ресурса SIP с именем `MySIPDialPlan` и ему запрещается принимать новые вызовы. Также показано переключение из режима запуска в двойной режим, который позволяет серверу почтовых ящиков принимать запросы по протоколам TCP и TLS.

    Set-UMService -Identity MyMailboxServer -DialPlans MySIPDialPlan -Status Disabled -UMStartupMode Dual

В этом примере сервер почтовых ящиков с именем `MyMailboxServer` добавляется в две абонентские группы SIP с именами `MySIPDialPlan` и `MySIPDialPlan2`, а также выполняются следующие настройки.

  - Разрешаются адреса IPv4 и IPv6.

  - Устанавливает максимальное количество входящих вызовов как 50.

  - Настраивается служба доступа SIP для Lync Server.

<!-- end list -->

    Set-UMService -Identity MyMailboxServer -DialPlans MySIPDialPlan, MySIPDialPlan2 -IPAddressFamily Any -MaxCallsAllowed 50 -SipAccessService northamerica.lyncpoolna.contoso.com

## Добавление сервера клиентского доступа в абонентскую группу с универсальным кодом ресурса SIP с помощью Центра администрирования Exchange

1.  В Центре администрирования Exchange перейдите к разделу **Серверы** \> **Серверы**.

2.  Выберите из списка сервер клиентского доступа, который необходимо изменить, и нажмите кнопку **Правка**![Значок редактирования](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Значок редактирования").

3.  На странице **Exchange Server** нажмите кнопку **Единая система обмена сообщениями**.

4.  В разделе **Параметры маршрутизатора вызовов единой системы обмена сообщениями** \> **Сопоставленные абонентские группы** щелкните **Добавить**![Значок добавления](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Значок добавления").

5.  В окне **Выбор абонентской группы единой системы обмена сообщениями** выберите абонентскую группу с универсальным кодом ресурса SIP, щелкните **Добавить**, **OK** и **Сохранить**.

## Добавление сервера клиентского доступа в абонентскую группу с универсальным кодом ресурса SIP с помощью командной консоли

В этом примере сервер клиентского доступа с именем `MyClientAccessServer` добавляется в абонентскую группу с универсальным кодом ресурса SIP с именем `MySIPDialPlan`. Также показано переключение из режима запуска в двойной режим, который позволяет серверу клиентского доступа принимать запросы по протоколам TCP и TLS.

    Set-UMCallRouterSettings -DialPlans MySIPDialPlan -Server MyClientAccessServer -UMStartupMode Dual

В этом примере сервер клиентского доступа с именем `MyClientAccessServer` добавляется в две абонентские группы SIP с именами `MySIPDialPlan` и `MySIPDialPlan2`; кроме того, серверу разрешается использовать адреса IPv4 и IPv6.

    Set-UMCallRouterSettings -DialPlans MySIPDialPlan, MySIPDialPlan2 -IPAddressFamily Any -Server MyClientAccessServer
