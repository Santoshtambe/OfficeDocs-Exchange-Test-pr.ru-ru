﻿---
title: 'Включить или отключить поиск в каталоге: Exchange 2013 Help'
TOCTitle: Включить или отключить поиск в каталоге
ms:assetid: c0768815-8578-4385-8d4c-7d1e40304cec
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Ee423557(v=EXCHG.150)
ms:contentKeyID: 52059248
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Включить или отключить поиск в каталоге

 

_**Применимо к:**Exchange Online, Exchange Server 2013, Exchange Server 2016_

_**Последнее изменение раздела:**2016-05-10_

Можно включить поиск в каталоге, чтобы абоненты, совершающие вызовы автосекретарю единой системы обмена сообщениями, могли выполнять поиск имен в каталоге с помощью клавиатуры телефона, но не могли выполнять поиск в каталоге с помощью голосового ввода. Этот параметр по умолчанию включен. Если этот параметр отключен, абоненты не смогут найти определенного человека в каталоге с помощью тонального набора или голосовых команд.

Дополнительные задачи управления, связанные с автосекретарями единой системы обмена сообщениями, см. в разделе [Процедуры автосекретаря единой системы обмена сообщениями](um-auto-attendant-procedures-exchange-2013-help.md).

<table>
<thead>
<tr class="header">
<th><img src="images/JJ126620.note(EXCHG.150).gif" title="Примечание" alt="Примечание" />Примечание.</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Outlook голосового доступа к пользователи не могут использовать автоматического распознавания речи (ASR) или голосовой ввод для нахождения пользователей в каталоге, их можно использовать только DTMF и тонального.</td>
</tr>
</tbody>
</table>


## Что нужно знать перед началом работы?

  - Предполагаемое время для завершения: менее 1 минуты.

  - Для выполнения этих процедур необходимы соответствующие разрешения. Сведения о необходимых разрешениях см. в статье Запись «Автосекретари единой системы обмена сообщениями» в разделе [Разрешения единой системы обмена сообщениями](unified-messaging-permissions-exchange-2013-help.md).

  - Перед выполнением этих процедур убедитесь, что абонентская группа единой системы обмена сообщениями создана. Дополнительные сведения см. в разделе [Создание абонентской группы единой системы обмена сообщениями](create-a-um-dial-plan-exchange-2013-help.md).

  - Перед выполнением этих процедур убедитесь, что автосекретарь единой системы обмена сообщениями создан. Дополнительные сведения см. в разделе [Создание автосекретаря единой системы обмена сообщениями](create-a-um-auto-attendant-exchange-2013-help.md).

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

## Включение и выключение поиска в каталоге с помощью Центра администрирования Exchange

1.  В Центре администрирования Exchange последовательно выберите пункты **Единая система обмена сообщениями** \> **Абонентские группы единой системы обмена сообщениями**. Выберите из списка абонентскую группу единой системы обмена сообщениями, которую необходимо изменить, и нажмите кнопку **Правка**![Значок редактирования](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Значок редактирования").

2.  На странице **Абонентская группа единой системы обмена сообщениями** в разделе **Автосекретари единой системы обмена сообщениями** выберите автосекретарь единой системы обмена сообщениями, для которого нужно включить или выключить поиск в каталоге, а затем нажмите кнопку **Правка**![Значок редактирования](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Значок редактирования").

3.  Чтобы включить для абонентов функцию поиска пользователей, на странице **Автосекретарь единой системы обмена сообщениями** \> **Адресная книга и доступ оператора** в разделе **Параметры для поиска в адресной книге** установите флажок рядом с пунктом **Разрешить абонентам искать пользователей по имени или псевдониму**. Чтобы выключить для абонентов возможность поиска пользователей, снимите этот флажок.

4.  Нажмите кнопку **Сохранить**.

## Включение и выключение поиска в каталоге с помощью командной консоли

В этом примере показано, как отключить поиск в каталоге в автосекретаре единой системы обмена сообщениями с именем `MyUMAutoAttendant`.

    Set-UMAutoAttendant -Identity MyUMAutoAttendant -NameLookupEnabled $false

