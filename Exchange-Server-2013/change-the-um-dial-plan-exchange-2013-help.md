﻿---
title: 'Изменение абонентской единой системы обмена СООБЩЕНИЯМИ: Exchange 2013 Help'
TOCTitle: Изменение абонентской единой системы обмена СООБЩЕНИЯМИ
ms:assetid: 4a6b6b6f-c61c-44e8-91dd-c5d28835f441
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Ee633465(v=EXCHG.150)
ms:contentKeyID: 50487994
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Изменение абонентской единой системы обмена СООБЩЕНИЯМИ

 

_**Применимо к:**Exchange Online, Exchange Server 2013, Exchange Server 2016_

_**Последнее изменение раздела:**2012-11-05_

Вам может потребоваться переместить пользователя с включенной поддержкой единой системы обмена сообщениями в другую абонентскую группу этой системы или изменить абонентскую группу, связанную с пользователем. Например, вам может потребоваться переместить пользователя единой системы обмена сообщениями из абонентской группы "Добавочный номер" в группу "Универсальный код ресурса (URI) SIP".

Чтобы изменить абонентскую группу единой системы обмена сообщениями, вам нужно отключить для пользователя поддержку единой системы обмена сообщениями, а затем включить ее в новой абонентской группе. Это необходимо по той причине, что разные абонентские группы могут иметь разные настройки и требования, например разную длину добавочного номера или разные типы URI. Например, для абонентской группы универсального кода ресурса SIP необходимо назначить код ресурса SIP для каждого почтового ящика с включенной поддержкой единой системы обмена сообщениями, а для абонентских групп добавочного номера это не требуется. Кроме того, каждый почтовый ящик единой системы обмена сообщениями содержит ссылки на абонентскую группу единой системы обмена сообщениями и на политику почтового ящика этой системы. Политика почтовых ящиков единой системы обмена сообщениями, в свою очередь, содержит ссылки на абонентскую группу единой системы обмена сообщениями. Если вы измените основной адрес прокси-сервера для пользователя единой системы обмена сообщениями так, чтобы он указывал на другую абонентскую группу, состояние почтового ящика единой системы обмена сообщениями будет несогласованным.

Дополнительные задачи управления, связанные с пользователями, задействованными для голосовой почты, см. в разделе [Процедуры пользователя голосовой почты](voice-mail-enabled-user-procedures-exchange-2013-help.md).

## Что нужно знать перед началом работы?

  - Осталось времени до завершения: 10 минут.

  - Для выполнения этих процедур необходимы соответствующие разрешения. Сведения о необходимых разрешениях см. в статье Запись "Почтовые ящики единой системы обмена сообщениями" в разделе [Разрешения единой системы обмена сообщениями](unified-messaging-permissions-exchange-2013-help.md).

  - Перед выполнением этой процедуры убедитесь, что абонентская группа единой системы обмена сообщениями создана. Дополнительные сведения см. в разделе [Создание абонентской группы единой системы обмена сообщениями](create-a-um-dial-plan-exchange-2013-help.md).

  - Перед выполнением этой процедуры убедитесь, что политика почтовых ящиков единой системы обмена сообщениями создана. Дополнительные сведения см. в разделе [Создание политики почтовых ящиков единой системы обмена сообщениями](create-a-um-mailbox-policy-exchange-2013-help.md).

  - Перед выполнением этих действий убедитесь, что существующий получатель Exchange доступен в единой системе обмена сообщениями. Дополнительные сведения см. в разделе [Включение для пользователя поддержки голосовой почты](enable-a-user-for-voice-mail-exchange-2013-help.md).

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


## Как это сделать?

## Действие 1. Создайте абонентскую группу единой системы обмена сообщениями

<table>
<thead>
<tr class="header">
<th><img src="images/Dd876857.important(EXCHG.150).gif" title="Важно" alt="Важно" />Важно!</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>При переносе пользователей единой системы обмена сообщениями в среду Microsoft Office Communications Server 2007 R2 или Microsoft Lync Server сначала нужно создать абонентскую группу универсального кода ресурса SIP.</td>
</tr>
</tbody>
</table>


Подробные инструкции см. в разделе [Создание абонентской группы единой системы обмена сообщениями](create-a-um-dial-plan-exchange-2013-help.md).

## Действие 2. Отключите для пользователя поддержку единой системы обмена сообщениями

Подробные инструкции см. в разделе [Отключение голосовой почты для пользователя](disable-voice-mail-for-a-user-exchange-2013-help.md).

## Действие 3. Включите для пользователя поддержку единой системы обмена сообщениями в новой абонентской группе

<table>
<thead>
<tr class="header">
<th><img src="images/Dd876857.important(EXCHG.150).gif" title="Важно" alt="Важно" />Важно!</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>При перемещении пользователей в среду с Office Communications Server 2007 R2 или Lync Server во время включения их в единую систему обмена сообщениями нужно также указать код ресурса SIP для пользователя. Также необходимо выбрать политику почтовых ящиков единой системы обмена сообщениями, связанную с абонентской группой протокола SIP.</td>
</tr>
</tbody>
</table>


Подробные инструкции см. в разделе [Включение для пользователя поддержки голосовой почты](enable-a-user-for-voice-mail-exchange-2013-help.md).
