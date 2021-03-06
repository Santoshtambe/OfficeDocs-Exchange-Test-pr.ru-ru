﻿---
title: 'Настройка дополнительного способа поиска пользователями голосового доступа к Outlook: Exchange 2013 Help'
TOCTitle: Настройка дополнительного способа поиска пользователями голосового доступа к Outlook
ms:assetid: 5cd4e0a0-d023-45a1-aa3c-b8dea6ec6d72
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Aa998311(v=EXCHG.150)
ms:contentKeyID: 52059183
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Настройка дополнительного способа поиска пользователями голосового доступа к Outlook

 

_**Применимо к:**Exchange Online, Exchange Server 2013, Exchange Server 2016_

_**Последнее изменение раздела:**2013-02-22_

При создании абонентской группы можно настроить основной и дополнительный *способы звонка по имени*, которые абоненты могут использовать для поиска имен. Абоненты используют данные способы дозвона по имени для поиска пользователей и связи с ними при звонке на номер голосового доступа к Outlook или при вызове автосекретаря единой системы обмена сообщениями, связанного с абонентской группой. Абоненты могут использовать тональный набор для поиска пользователя с включенной поддержкой единой системы обмена сообщениями.

<table>
<thead>
<tr class="header">
<th><img src="images/JJ126620.note(EXCHG.150).gif" title="Примечание" alt="Примечание" />Примечание.</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Если для дополнительного способа поиска имен выбрать значение <strong>Нет</strong>, абонентам будет доступен только основной способ поиска имен пользователей. Если вы настроили как основной, так и дополнительный способы поиска имен, абонентам будут предлагаться оба этих способа.</td>
</tr>
</tbody>
</table>


Дополнительные задачи управления, связанные с абонентскими группами единой системы обмена сообщениями, см. в разделе [Процедуры плана телефонным единой системы обмена СООБЩЕНИЯМИ](um-dial-plan-procedures-exchange-2013-help.md).

## Что нужно знать перед началом работы

  - Предполагаемое время для завершения: менее 1 минуты.

  - Для выполнения этих процедур необходимы соответствующие разрешения. Сведения о необходимых разрешениях см. в статье запись "Абонентская группа единой системы обмена сообщениями" в разделе [Разрешения единой системы обмена сообщениями](unified-messaging-permissions-exchange-2013-help.md).

  - Перед выполнением этих процедур убедитесь, что абонентская группа единой системы обмена сообщениями создана. Дополнительные сведения см. в разделе [Создание абонентской группы единой системы обмена сообщениями](create-a-um-dial-plan-exchange-2013-help.md).

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

## Использование Центра администрирования Exchange для изменения дополнительного способа дозвона по имени

1.  В Центре администрирования Exchange последовательно выберите пункты **Единая система обмена сообщениями** \> **Абонентские группы единой системы обмена сообщениями**.

2.  Выберите из списка абонентскую группу единой системы обмена сообщениями, которую необходимо изменить, и нажмите кнопку **Правка**![Значок редактирования](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Значок редактирования").

3.  На странице **Абонентская группа единой системы обмена сообщениями** нажмите кнопку **Настроить**.

4.  На странице **Параметры** в разделе **Дополнительный способ поиска имен** выберите в раскрывающемся списке нужный вариант:
    
      - **Фамилия Имя** (по умолчанию)
    
      - **Имя Фамилия**
    
      - **SMTP-адрес**
    
      - **Нет**

5.  Нажмите кнопку **Сохранить**.

## Использование командной консоли для изменения дополнительного способа дозвона по имени

В этом примере для дополнительного способа дозвона по имени задается значение `FirstLast`. Это позволяет абонентам, звонящим по номеру голосового доступа Outlook или автосекретарю единой системы обмена сообщениями, связанному с абонентской группой, выполнять поиск пользователей единой системы обмена сообщениями по имени и фамилии.

    Set-UMDialPlan -Identity MyUMDialPlan -DialByNameSecondary FirstLast

В этом примере для дополнительного способа дозвона по имени задается значение `LastFirst`. Это позволяет абонентам, звонящим по номеру голосового доступа Outlook или автосекретарю единой системы обмена сообщениями, связанному с абонентской группой, выполнять поиск пользователей единой системы обмена сообщениями по имени и фамилии.

    Set-UMDialPlan -Identity MyUMDialPlan -DialByNameSecondary LastFirst 

В этом примере для дополнительного способа дозвона по имени задается значение `SMTP address`. Это позволяет абонентам, звонящим по номеру голосового доступа Outlook или автосекретарю единой системы обмена сообщениями, связанному с абонентской группой, выполнять поиск пользователей единой системы обмена сообщениями по их SMTP-адресу.

    Set-UMDialPlan -Identity MyUMDialPlan -DialByNameSecondary SMTPAddress 

В этом примере для дополнительного и основного способов дозвона по имени задаются значения `None` и `SMTP address` соответственно. Это позволяет абонентам, звонящим по коду голосового доступа Outlook или автосекретарю единой системы обмена сообщениями, связанному с абонентской группой, выполнять поиск пользователей системы только по их SMTP-адресу.

    Set-UMDialPlan -Identity MyUMDialPlan -DialByNamePrimary SMTPAddress -DialByNameSecondary None

