﻿---
title: 'Отключить вызовы от пользователей, которые не включены единой системы обмена СООБЩЕНИЯМИ: Exchange 2013 Help'
TOCTitle: Отключить вызовы от пользователей, которые не включены единой системы обмена СООБЩЕНИЯМИ
ms:assetid: 272ff4ab-b4d9-4647-98e2-7c171f9dfc3f
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/JJ673516(v=EXCHG.150)
ms:contentKeyID: 50487653
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Отключить вызовы от пользователей, которые не включены единой системы обмена СООБЩЕНИЯМИ

 

_**Применимо к:**Exchange Online, Exchange Server 2013, Exchange Server 2016_

_**Последнее изменение раздела:**2012-11-05_

Пользователь может включить или отключить прием вызовов от пользователей, для которых не включена поддержка единой системы обмена сообщениями. По умолчанию единая система обмена сообщениями позволяет перенаправлять через автосекретарь входящие вызовы от абонентов, не прошедших проверку подлинности, пользователям системы. Благодаря этому пользователи, не относящиеся к организации, могут звонить пользователям единой системы обмена сообщениями.

Если этот параметр отключен для пользователя единой системы обмена сообщениями, почтовый ящик этого пользователя можно найти с помощью поиска в каталоге. Однако при попытке перенаправления внешнего вызова этому пользователю система выдает сообщение: "Извините, не удается перенаправить вызов этому пользователю". После этого вызов будет перенаправлен оператору, если он настроен для автосекретаря. Если для автосекретаря не настроен ни один оператор, вызов будет перенаправлен оператору абонентской группы (если он настроен). Если добавочный номер оператора не настроен ни для автосекретаря с поддержкой речевых функций, ни для резервного автосекретаря с функцией двухтонального многочастотного набора DTMF, ни для абонентской группы, система выдает сообщение: "Извините. Оператор и служба тонального набора недоступны".

Дополнительные задачи управления, связанные с пользователями, задействованными для голосовой почты, см. в разделе [Процедуры пользователя голосовой почты](voice-mail-enabled-user-procedures-exchange-2013-help.md).

## Что нужно знать перед началом работы?

  - Предполагаемое время для завершения: менее 1 минуты.

  - Для выполнения этих процедур необходимы соответствующие разрешения. Сведения о необходимых разрешениях см. в статье Запись «Почтовые ящики единой системы обмена сообщениями» в разделе [Разрешения единой системы обмена сообщениями](unified-messaging-permissions-exchange-2013-help.md).

  - Перед выполнением этой процедуры убедитесь, что абонентская группа единой системы обмена сообщениями создана. Дополнительные сведения см. в разделе [Создание абонентской группы единой системы обмена сообщениями](create-a-um-dial-plan-exchange-2013-help.md).

  - Перед выполнением этой процедуры убедитесь, что политика почтовых ящиков единой системы обмена сообщениями создана. Дополнительные сведения см. в разделе [Создание политики почтовых ящиков единой системы обмена сообщениями](create-a-um-mailbox-policy-exchange-2013-help.md).

  - Перед выполнением этой процедуры убедитесь, что для почтового ящика пользователя включена поддержка единой системы обмена сообщениями. Дополнительные сведения см. в разделе [Включение для пользователя поддержки голосовой почты](enable-a-user-for-voice-mail-exchange-2013-help.md).

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


## Использование командной консоли для отключения звонков от пользователей, для которых не включена поддержка единой системы обмена сообщениями

В этом примере показано отключение приема голосовых вызовов для пользователя Тони Смита (Tony Smith) от абонентов, для которых не включена поддержка единой системы обмена сообщениями.

    Set UMMailbox -Identity tony@contoso.com -AllowUMCallsFromNonUsers None

