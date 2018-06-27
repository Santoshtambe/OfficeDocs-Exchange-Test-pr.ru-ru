﻿---
title: 'Настройка квот хранилища для почтового ящика: Exchange 2013 Help'
TOCTitle: Настройка квот хранилища для почтового ящика
ms:assetid: 5f5fe292-c80e-4a0b-b3e6-e193ea5171d0
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Aa998353(v=EXCHG.150)
ms:contentKeyID: 50556384
ms.date: 04/30/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Настройка квот хранилища для почтового ящика

 

_**Применимо к:**Exchange Server 2013_

_**Последнее изменение раздела:**2015-07-07_

**Сводка.** Используйте Центр администрирования Exchange или командную консоль, чтобы установить квоты хранилища для почтовых ящиков.

Квоты хранилища позволяют контролировать размер почтовых ящиков и управлять расширением баз данных почтовых ящиков. Когда указанная квота хранилища будет исчерпана или превышена, Exchange отправит владельцу почтового ящика уведомление.

<table>
<thead>
<tr class="header">
<th><img src="images/JJ126620.note(EXCHG.150).gif" title="Примечание" alt="Примечание" />Примечание.</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Квоты хранилища применяются к размеру почтового ящика, определенному свойством <code>TotalItemSize</code> при выполнении командлета <code>Get-MailboxStatistics</code>. Дополнительные сведения см. в статье <a href="https://technet.microsoft.com/ru-ru/library/bb124612(v=exchg.150)">Get-MailboxStatistics</a>.</td>
</tr>
</tbody>
</table>


Квоты хранилища обычно настраиваются отдельно для каждой базы данных. Это значит, что квоты, настроенные для базы данных почтовых ящиков, применяются ко всем почтовым ящикам в этой базе данных. Дополнительные сведения об управлении параметрами почтовых ящиков отдельных баз данных см. в разделе [Управление базами данных почтовых ящиков в Exchange 2013](manage-mailbox-databases-in-exchange-2013-exchange-2013-help.md).

В этом разделе показано, как настроить параметры хранения для отдельного почтового ящика, чтобы не использовать параметры хранения для базы данных почтовых ящиков. Сведения о дополнительных задачах по управлению почтовыми ящиками пользователей см. в разделе [Управление почтовыми ящиками пользователей](manage-user-mailboxes-exchange-2013-help.md).

## Что нужно знать перед началом работы?

  - Предполагаемое время выполнения: 2 мин.

  - Для выполнения этих процедур необходимы соответствующие разрешения. Сведения о необходимых разрешениях см. в статье Раздел "Разрешения на подготовку получателей" в статье [Разрешения получателей](recipients-permissions-exchange-2013-help.md).

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

## Использование центра администрирования Exchange для настройки квот хранилища почтового ящика

1.  В центре администрирования Exchange перейдите к разделу **Получатели** \> **Почтовые ящики**.

2.  В списке почтовых ящиков пользователей щелкните ящик, для которого требуется изменить квоты хранилища, а затем выберите команду **Изменить**![Значок редактирования](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Значок редактирования").

3.  На странице свойств почтового ящика выберите **Использование почтового ящика**, а затем **Дополнительные параметры**.

4.  Выберите **Настроить параметры для этого почтового ящика** и укажите необходимые значения в следующих полях. Диапазон значений для каждого из параметров квоты хранилища составляет от 0 до 2047 гигабайт (ГБ).
    
      - **Выводить предупреждение при (ГБ)**. В этом поле отображается максимальный размер хранилища, в случае превышения которого выводится предупреждение. Если размер почтового ящика достигает указанного значения или превышает его, Exchange отправляет пользователю предупреждение.
        
        <table>
        <thead>
        <tr class="header">
        <th><img src="images/Dd876857.important(EXCHG.150).gif" title="Важно" alt="Важно" />Важно!</th>
        </tr>
        </thead>
        <tbody>
        <tr class="odd">
        <td>Сообщение, связанное с квотой <strong>Выводить предупреждение</strong>, не отправляется пользователю, если значение этого параметра не превышает 50 % значения, указанного в квоте <strong>Запретить отправку</strong>. Например, если вы установили квоту <strong>Запретить отправку</strong> в размере 8 МБ, квота <strong>Предупреждать о проблеме</strong> должна быть не меньше 4 МБ. В противном случае сообщение, связанное с квотой <strong>Выводить предупреждение</strong>, отправляться не будет.</td>
        </tr>
        </tbody>
        </table>
    
      - **Запретить отправку при (ГБ)**. В этом поле указано ограничение *запрета на отправку* для почтового ящика. Если размер почтового ящика достигнет указанного значения или превысит его, пользователь не сможет отправлять новые сообщения — появится сообщение об ошибке.
    
      - **Запретить отправку и получение при (ГБ)**. В этом поле указано ограничение *запрета на отправку и получение* для почтового ящика. Если размер почтового ящика достигнет указанного значения или превысит его, пользователь не сможет ни отправлять, ни получать новые сообщения. Сообщения, отправленные в почтовый ящик, будут возвращены отправителю с соответствующим сообщением об ошибке.

5.  Нажмите кнопку **Сохранить**, чтобы сохранить изменения.

## Использование командной консоли Exchange для настройки квот хранилища почтового ящика

В этом примере показано, как задать квоты для предупреждения, запрета на отправку, запрета на отправку и получение для почтового ящика пользователя Joe Healy, равные 24,5 ГБ, 24,75 ГБ и 25 ГБ соответственно.

<table>
<thead>
<tr class="header">
<th><img src="images/JJ126620.note(EXCHG.150).gif" title="Примечание" alt="Примечание" />Примечание.</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Чтобы использовать настраиваемые параметры для почтового ящика вместо значений по умолчанию для базы данных почтовых ящиков, необходимо присвоить параметру <em>UseDatabaseQuotaDefaults</em> значение <code>$false</code>.</td>
</tr>
</tbody>
</table>


    Set-Mailbox -Identity "Joe Healy" -IssueWarningQuota 24.5gb -ProhibitSendQuota 24.75gb -ProhibitSendReceiveQuota 25gb -UseDatabaseQuotaDefaults $false

В этом примере показано, как задать квоты для предупреждения, запрета на отправку, запрета на отправку и получение для почтового ящика пользователя Ayla Kol, равные 900 МБ, 950 МБ и 1 ГБ соответственно, а также настроить почтовый ящик на использование настраиваемых параметров.

    Set-Mailbox -Identity "Ayla Kol" -IssueWarningQuota 900mb -ProhibitSendQuota 950mb -ProhibitSendReceiveQuota 1gb -UseDatabaseQuotaDefaults $false

Дополнительные сведения о синтаксисе и параметрах см. в разделе [Set-Mailbox](https://technet.microsoft.com/ru-ru/library/bb123981\(v=exchg.150\)).

## Как проверить, что все получилось?

Чтобы проверить, успешно ли заданы квоты хранилища для почтового ящика, выполните одно из следующих действий.

1.  В центре администрирования Exchange перейдите к разделу **Получатели** \> **Почтовые ящики**.

2.  В списке почтовых ящиков пользователей щелкните ящик, для которого требуется проверить квоты хранилища, а затем выберите команду **Изменить**![Значок редактирования](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Значок редактирования").

3.  На странице свойств почтового ящика последовательно щелкните **Использование почтового ящика** и **Дополнительные параметры**.

4.  Убедитесь, что выбран пункт **Настроить параметры для данного почтового ящика**.

5.  Проверьте параметры квоты хранилища.

Или

Выполните в командной консоли следующую команду.

    Get-Mailbox <identity> | fl IssueWarningQuota,ProhibitSendQuota,ProhibitSendReceiveQuota,UseDatabaseQuotaDefaults
