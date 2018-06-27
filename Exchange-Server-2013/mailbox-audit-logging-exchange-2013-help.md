﻿---
title: 'Ведение журнала аудита почтового ящика: Exchange 2013 Help'
TOCTitle: Ведение журнала аудита почтового ящика
ms:assetid: 29b67d58-eef9-4ad4-863f-562405ea8794
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Ff459237(v=EXCHG.150)
ms:contentKeyID: 50487719
ms.date: 04/30/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Ведение журнала аудита почтового ящика

 

_**Применимо к:**Exchange Server 2013_

_**Последнее изменение раздела:**2016-12-09_

Почтовые ящики могут содержать конфиденциальные сведения, важные для работы организации, а также персональные данные. Поэтому необходимо отслеживать вход в почтовые ящики организации и выполняемые в них действия. Особенно это касается доступа к почтовым ящикам пользователей, не являющихся их владельцами. Такие пользователи называются *делегированными*.

С помощью *функции ведения журнала аудита почтового ящика* можно регистрировать доступ владельцев, делегатов (в том числе администраторов с полными разрешениями на доступ к почтовому ящику) и администраторов к почтовым ящикам.

При включении функции ведения журнала аудита для почтового ящика можно указать, какие именно действия (например, доступ к почтовому ящику, перемещение или удаление сообщений) должны регистрироваться для соответствующих типов учетных записей для входа (администратор, делегированный пользователь или владелец). В записях журнала аудита также содержатся другие важные сведения, такие как IP-адрес клиента, имя узла, процесс или клиент, использованные для получения доступа к почтовому ящику. Для перемещенных сообщений также указывается имя папки назначения.

## Ведение журнала аудита почтовых ящиков

Для всех почтовых ящиков с включенной функцией ведения журнала аудита создаются журналы аудита почтовых ящиков. Записи журнала хранятся во вложенной папке "Аудиты" папки "Элементы для восстановления" отслеживаемого почтового ящика. Это обеспечивает доступ ко всем записям журнала аудита из одного места, независимо от использованного метода клиентского доступа к почтовому ящику или сервера (либо рабочей станции), использованного администратором для получения доступа к журналу аудита почтовых ящиков. При перемещении ящика на другой сервер почтовых ящиков соответственно перемещаются хранящиеся в нем журналы аудита.

По умолчанию записи журнала аудита хранятся в почтовом ящике 90 дней, после чего удаляются. Время хранения можно изменить, используя параметр *AuditLogAgeLimit* в командлете [Set-Mailbox](https://technet.microsoft.com/ru-ru/library/bb123981\(v=exchg.150\)). Если почтовый ящик хранится на месте или хранится для судебного разбирательства, записи журнала аудита сохраняются до истечения периода хранения журналов аудита для этого почтового ящика. Чтобы сохранить журналы аудита на более длительный срок, следует увеличить период хранения, изменив значение параметра *AuditLogAgeLimit*. Вы также можете экспортировать записи журнала аудита до истечения периода хранения. Дополнительные сведения см. в следующих разделах:

  - [Экспорт журналов аудита почтовых ящиков](export-mailbox-audit-logs-exchange-2013-help.md)

  - [Поиск в журнале аудита почтовых ящиков](create-a-mailbox-audit-log-search-exchange-2013-help.md)

## Включение ведения журнала аудита почтовых ящиков

Ведение журнала аудита включено для каждого почтового ящика. С помощью командлета **Set-Mailbox** можно включить или отключить ведение журнала аудита почтовых ящиков. Дополнительные сведения см. в разделе [Включение и отключение ведения журнала аудита для почтового ящика](enable-or-disable-mailbox-audit-logging-for-a-mailbox-exchange-2013-help.md).

При включении ведения журнала аудита почтового ящика операции доступа к почтовому ящику, а также некоторые действия администраторов и делегатов записываются по умолчанию. Для записи действий владельца почтового ящика необходимо указать, какие именно действия должны записываться.

## Действия, записываемые в журнале аудита почтовых ящиков

В следующей таблице перечислены действия, записываемые в журнале аудита почтового ящика, включая соответствующие типы учетных записей для входа.


<table>
<colgroup>
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
<col style="width: 20%" />
</colgroup>
<thead>
<tr class="header">
<th>Действие</th>
<th>Описание</th>
<th>Администратор</th>
<th>Делегат</th>
<th>Владелец</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Copy</p></td>
<td><p>Сообщение скопировано в другую папку.</p></td>
<td><p>Да</p></td>
<td><p>Нет</p></td>
<td><p>Нет</p></td>
</tr>
<tr class="even">
<td><p>Create</p></td>
<td><p>В папке &quot;Календарь&quot;, &quot;Контакты&quot;, &quot;Заметки&quot; или &quot;Задачи&quot; почтового ящика создан элемент, например новое приглашение на собрание. Учтите, что создание сообщений и папок при этом не регистрируется.</p></td>
<td><p>Да*</p></td>
<td><p>Да*</p></td>
<td><p>Да</p></td>
</tr>
<tr class="odd">
<td><p>FolderBind</p></td>
<td><p>Папка почтового ящика была открыта.</p></td>
<td><p>Да*</p></td>
<td><p>Да**</p></td>
<td><p>Нет</p></td>
</tr>
<tr class="even">
<td><p>HardDelete</p></td>
<td><p>Элемент удален из папки &quot;Элементы для восстановления&quot; без возможности восстановления.</p></td>
<td><p>Да*</p></td>
<td><p>Да*</p></td>
<td><p>Да</p></td>
</tr>
<tr class="odd">
<td><p>MessageBind</p></td>
<td><p>Сообщение открыто или просматривается в области просмотра.</p></td>
<td><p>Да</p></td>
<td><p>Нет</p></td>
<td><p>Нет</p></td>
</tr>
<tr class="even">
<td><p>Move</p></td>
<td><p>Сообщение перемещено в другую папку.</p></td>
<td><p>Да*</p></td>
<td><p>Да</p></td>
<td><p>Да</p></td>
</tr>
<tr class="odd">
<td><p>MoveToDeletedItems</p></td>
<td><p>Сообщение перемещено в папку &quot;Удаленные&quot;.</p></td>
<td><p>Да*</p></td>
<td><p>Да</p></td>
<td><p>Да</p></td>
</tr>
<tr class="even">
<td><p>SendAs</p></td>
<td><p>Сообщение отправлено с использованием разрешений &quot;Отправить как&quot;.</p></td>
<td><p>Да*</p></td>
<td><p>Да*</p></td>
<td><p>Неприменимо</p></td>
</tr>
<tr class="odd">
<td><p>SendOnBehalf</p></td>
<td><p>Сообщение отправлено с использованием разрешений &quot;Отправить от имени&quot;.</p></td>
<td><p>Да*</p></td>
<td><p>Да</p></td>
<td><p>Не применимо</p></td>
</tr>
<tr class="even">
<td><p>SoftDelete</p></td>
<td><p>Сообщение удалено из папки &quot;Удаленные&quot;.</p></td>
<td><p>Да*</p></td>
<td><p>Да*</p></td>
<td><p>Да</p></td>
</tr>
<tr class="odd">
<td><p>Update</p></td>
<td><p>Параметры элемента обновлены.</p></td>
<td><p>Да*</p></td>
<td><p>Да*</p></td>
<td><p>Да</p></td>
</tr>
</tbody>
</table>


\*Записывается по умолчанию, если для почтового ящика включена функция ведения журнала аудита.

\*\*Записи о действиях делегатов по привязке папок консолидируются. За 24 часа в журнале создается одна запись для доступа к отдельной папке.

Для отключения записи определенных действий, выполняемых в почтовом ящике, необходимо изменить параметры ведения журнала аудита почтового ящика. Существующие записи в журнале аудита удаляются после истечения заданного срока хранения.

## Поиск записей журнала аудита почтовых ящиков

Для поиска записей в журнале аудита можно использовать следующие способы.

  - **Синхронный поиск в отдельном почтовом ящике.** С помощью командлета [Search-MailboxAuditLog](https://technet.microsoft.com/ru-ru/library/ff522360\(v=exchg.150\)) можно выполнять синхронный поиск записей в журнале аудита для отдельного почтового ящика. Результаты поиска командлета отображаются в окне командной консоли Exchange. Дополнительные сведения см. в разделе [Поиск почтового ящика в журнале аудита почтовых ящиков](search-the-mailbox-audit-log-for-a-mailbox-exchange-2013-help.md).

  - **Асинхронный поиск в одном или нескольких почтовых ящиках.** Вы можете создать поиск журнала аудита почтового ящика для асинхронного поиска в журналах аудита одного или нескольких почтовых ящиках, а затем отправить результаты поиска по указанному адресу электронной почты. Результаты поиска отправляются в виде вложения XML. Для выполнения поиска используйте командлет [New-MailboxAuditLogSearch](https://technet.microsoft.com/ru-ru/library/ff522362\(v=exchg.150\)). Дополнительные сведения см. в разделе [Поиск в журнале аудита почтовых ящиков](create-a-mailbox-audit-log-search-exchange-2013-help.md).

  - **Использование отчетов аудита в Центре администрирования Exchange (EAC).** Вкладку **Аудит** можно использовать для выполнения отчетов доступа к почтовому ящику пользователями, не являющимися его владельцами, или экспорта записей из журнала аудита почтового ящика. Подробнее см. в
    
      - [Запуск отчета об обращениях к почтовым ящикам от пользователей, не являющихся их владельцами](run-a-non-owner-mailbox-access-report-exchange-online-help.md)
    
      - [Экспорт журналов аудита почтовых ящиков](export-mailbox-audit-logs-exchange-2013-help.md)

## Записи журнала аудита почтовых ящиков

В следующей таблице описываются поля, заполняемые в журнале аудита почтовых ящиков.


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Поле</th>
<th>Заполняется</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>Operation</strong></p></td>
<td><p>Одно из следующих действий:</p>
<ul>
<li><p>Copy</p></li>
<li><p>Create</p></li>
<li><p>FolderBind</p></li>
<li><p>HardDelete</p></li>
<li><p>MessageBind</p></li>
<li><p>Move</p></li>
<li><p>MoveToDeletedItems</p></li>
<li><p>SendAs</p></li>
<li><p>SendOnBehalf</p></li>
<li><p>SoftDelete</p></li>
<li><p>Update</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p><strong>OperationResult</strong></p></td>
<td><p>Один из следующих результатов:</p>
<ul>
<li><p>Failed</p></li>
<li><p>PartiallySucceeded</p></li>
<li><p>Succeeded</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p><strong>LogonType</strong></p></td>
<td><p>Тип учетной записи для входа пользователя, выполняющего действие. Типы учетных записей для входа:</p>
<ul>
<li><p>Владелец</p></li>
<li><p>Делегат</p></li>
<li><p>Администратор</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p><strong>DestFolderId</strong></p></td>
<td><p>Идентификатор GUID папки назначения для операций перемещения.</p></td>
</tr>
<tr class="odd">
<td><p><strong>DestFolderPathName</strong></p></td>
<td><p>Путь к папке назначения для операций перемещения.</p></td>
</tr>
<tr class="even">
<td><p><strong>FolderId</strong></p></td>
<td><p>Идентификатор GUID папки.</p></td>
</tr>
<tr class="odd">
<td><p><strong>FolderPathName</strong></p></td>
<td><p>Путь к папке.</p></td>
</tr>
<tr class="even">
<td><p><strong>ClientInfoString</strong></p></td>
<td><p>Сведения для идентификации клиента или компонента Exchange, выполняющего эту операцию.</p></td>
</tr>
<tr class="odd">
<td><p><strong>ClientIPAddress</strong></p></td>
<td><p>IP-адрес клиентского компьютера.</p></td>
</tr>
<tr class="even">
<td><p><strong>ClientMachineName</strong></p></td>
<td><p>Имя клиентского компьютера.</p></td>
</tr>
<tr class="odd">
<td><p><strong>ClientProcessName</strong></p></td>
<td><p>Имя процесса клиентского приложения.</p></td>
</tr>
<tr class="even">
<td><p><strong>ClientVersion</strong></p></td>
<td><p>Версия клиентского приложения.</p></td>
</tr>
<tr class="odd">
<td><p><strong>InternalLogonType</strong></p></td>
<td><p>Тип учетной записи для входа пользователя, выполняющего действие. Типы учетных записей для входа:</p>
<ul>
<li><p>Владелец</p></li>
<li><p>Делегат</p></li>
<li><p>Администратор</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p><strong>MailboxOwnerUPN</strong></p></td>
<td><p>Имя участника-пользователя (UPN) владельца почтового ящика.</p></td>
</tr>
<tr class="odd">
<td><p><strong>MailboxOwnerSid</strong></p></td>
<td><p>Идентификатор безопасности владельца почтового ящика (SID).</p></td>
</tr>
<tr class="even">
<td><p><strong>DestMailboxOwnerUPN</strong></p></td>
<td><p>Имя участника-пользователя владельца почтового ящика назначения, выполняющего действия в нескольких почтовых ящиках.</p></td>
</tr>
<tr class="odd">
<td><p><strong>DestMailboxOwnerSid</strong></p></td>
<td><p>Идентификатор безопасности владельца почтового ящика назначения, выполняющего действия в нескольких почтовых ящиках.</p></td>
</tr>
<tr class="even">
<td><p><strong>DestMailboxOwnerGuid</strong></p></td>
<td><p>Идентификатор GUID владельца почтового ящика назначения.</p></td>
</tr>
<tr class="odd">
<td><p><strong>CrossMailboxOperation</strong></p></td>
<td><p>Запись сведений об операции, выполненной в нескольких почтовых ящиках (например, копирование или перемещение сообщений в другие почтовые ящики).</p></td>
</tr>
<tr class="even">
<td><p><strong>LogonUserDisplayName</strong></p></td>
<td><p>Отображаемое имя пользователя, выполнившего вход.</p></td>
</tr>
<tr class="odd">
<td><p><strong>DelegateUserDisplayName</strong></p></td>
<td><p>Отображаемое имя пользователя-делегата.</p></td>
</tr>
<tr class="even">
<td><p><strong>LogonUserSid</strong></p></td>
<td><p>Идентификатор безопасности пользователя, выполнившего вход.</p></td>
</tr>
<tr class="odd">
<td><p><strong>SourceItems</strong></p></td>
<td><p>Идентификатор ItemID элементов почтового ящика, в котором выполнено записанное действие (например, перемещение или удаление). Для действий, выполненных для нескольких элементов, данное поле отображается как совокупность элементов.</p></td>
</tr>
<tr class="even">
<td><p><strong>SourceFolders</strong></p></td>
<td><p>Идентификатор GUID исходной папки.</p></td>
</tr>
<tr class="odd">
<td><p><strong>ItemId</strong></p></td>
<td><p>Идентификатор элемента.</p></td>
</tr>
<tr class="even">
<td><p><strong>ItemSubject</strong></p></td>
<td><p>Тема элемента.</p></td>
</tr>
<tr class="odd">
<td><p><strong>MailboxGuid</strong></p></td>
<td><p>Идентификатор GUID почтового ящика</p></td>
</tr>
<tr class="even">
<td><p><strong>MailboxResolvedOwnerName</strong></p></td>
<td><p>Формат разрешенного имени пользователя почтового ящика выглядит следующим образом: <em>ДОМЕН</em>\<em>SamAccountName</em>.</p></td>
</tr>
<tr class="odd">
<td><p><strong>LastAccessed</strong></p></td>
<td><p>Время выполнения действия.</p></td>
</tr>
<tr class="even">
<td><p><strong>Identity</strong></p></td>
<td><p>Идентификатор записи журнала аудита.</p></td>
</tr>
</tbody>
</table>


## Дополнительные сведения

  - **Доступ администраторов к почтовым ящикам.** Считается, что администраторы получают доступ к почтовым ящикам только в следующих случаях.
    
      - [Обнаружение электронных данных на месте](in-place-ediscovery-exchange-2013-help.md) используется для поиска в почтовых ящиках.
    
      - Использование командлета [New-MailboxExportRequest](https://technet.microsoft.com/ru-ru/library/ff607299\(v=exchg.150\)) для экспорта почтового ящика.
    
      - [Средство MAPI Editor для Microsoft Exchange Server](https://go.microsoft.com/fwlink/p/?linkid=204086) используется для доступа к почтовому ящику.

  - **Пропуск записи в журнал аудита почтового ящика**. Доступ к почтовым ящикам с помощью авторизованных автоматических процессов, например учетных записей, используемых инструментами сторонних производителей или учетных записей для отслеживания исполнения законодательства, может привести к образованию большого количества записей в журнале аудита почтовых ящиков, что может создать затруднения для организации. Регистрацию сведений о таких учетных записях в журнале аудита можно отключить. Дополнительные сведения см. в разделе [Обход сервера-посредника пользователя для учетной записи аудита почтовых ящиков ведения журнала](bypass-a-user-account-from-mailbox-audit-logging-exchange-2013-help.md).

  - **Запись действий владельца почтового ящика в журнал**. В почтовых ящиках, используемых для поиска на обнаружение, в которых могут содержаться более конфиденциальные сведения, можно включить запись действий (например, удаление сообщений) их владельцев в журнале аудита.

Ведение журнала аудита почтовых ящиков
