﻿---
title: 'Удаление связи организации: Exchange 2013 Help'
TOCTitle: Удаление связи организации
ms:assetid: ff211394-f58b-4da7-bb3a-df6abcb5950e
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/JJ657513(v=EXCHG.150)
ms:contentKeyID: 50489536
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Удаление связи организации

 

_**Применимо к:**Exchange Server 2013_

_**Последнее изменение раздела:**2015-01-04_

Связи организации позволяют пользователям вашей организации Exchange обмениваться данными календаря о доступности с пользователями организации Office 365 или других локальных организаций Exchange. Можно удалить связь организации, чтобы запретить общий доступ к календарю пользователям из других организаций.

Чтобы получить возможность предоставлять общий доступ к календарям пользователям другой организации, нужно настроить отношение проверки подлинности с системой проверки подлинности Azure Active Directory (также известное как "федерация") и выполнить минимальные требования к программному обеспечению. Дополнительные сведения о федеративном общем доступе см. в разделе [Общий доступ](sharing-exchange-2013-help.md).

## Что нужно знать перед началом работы

  - Предполагаемое время для завершения: 5 минут.

  - Для выполнения этих процедур необходимы соответствующие разрешения. Сведения о необходимых разрешениях см. в статье Подраздел "Разрешения календаря и доступа" в разделе [Разрешения получателей](recipients-permissions-exchange-2013-help.md).

  - Сочетания клавиш для процедур, описанных в этой статье, приведены в статье [Сочетания клавиш в Центре администрирования Exchange](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).

## Что необходимо сделать?

## Использование Центра администрирования Exchange для удаления организационного отношения

1.  На сервере Exchange 2013 в локальной организации последовательно выберите пункты **Организация** \> **Общий доступ**.

2.  В разделе **Организационный совместный доступ** выберите организационное отношение и нажмите кнопку **Удалить**![Значок удаления](images/Dd979797.14f639f6-61e8-4418-bbfb-0db14de9d2f5(EXCHG.150).gif "Значок удаления"), чтобы удалить организационное отношение.

3.  В окне предупреждения, которое появится, нажмите кнопку **Да**.

## Использование командной консоли Exchange для удаления организационного отношения

В этом примере из организации Exchange удаляется организационное отношение «Contoso»

    Remove-OrganizationRelationship -Identity "Contoso"

Дополнительные сведения о синтаксисе и параметрах см. в разделе [Remove-OrganizationRelationship](https://technet.microsoft.com/ru-ru/library/ee332362\(v=exchg.150\)).

## Как проверить, что все получилось?

Чтобы убедиться в успешности удаления организационного отношения, выполните одно из следующих действий:

  - В Центре администрирования Exchange перейдите в раздел **Организация** \> **Общий доступ** и убедитесь, что организационное отношение не отображается в списке раздела **Организационный совместный доступ**.

  - Выполните следующую команду операционной системы, чтобы убедиться в удалении информации организационного отношения.
    
        Get-OrganizationRelationship | Format-List

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

