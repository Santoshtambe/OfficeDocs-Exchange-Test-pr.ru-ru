﻿---
title: 'Включение или отключение электронной почты для пользователя почты: Exchange 2013 Help'
TOCTitle: Включение или отключение электронной почты для пользователя почты
ms:assetid: 1e2571d4-ff84-4fda-bb1d-825e96e1bd26
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Aa996598(v=EXCHG.150)
ms:contentKeyID: 50556349
ms.date: 04/30/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Включение или отключение электронной почты для пользователя почты

 

_**Применимо к:**Exchange Online, Exchange Server 2013_

_**Последнее изменение раздела:**2012-11-14_

Можно отключить электронную почты для существующего почтового пользователя в организации Exchange. После отключения электронной почты для почтового пользователя он удаляется из Exchange и адресной книги организации. Если почтовый пользователь является участником группы рассылки, он перестанет получать почту, которая отправляется группе. Кроме того, атрибуты Exchange удаляются из объекта-пользователя в Active Directory, но объект-пользователь и его атрибуты, не относящиеся к Exchange (например, контактные данные и сведения об организации), сохраняются в Active Directory.

После отключения электронной почты для почтового пользователя для него можно снова включить поддержку почты с помощью командлета **Enable-MailUser** в командной консоли. Этот командлет также можно использовать для включения поддержки почты для любого пользователя Active Directory.

<table>
<thead>
<tr class="header">
<th><img src="images/JJ126620.note(EXCHG.150).gif" title="Примечание" alt="Примечание" />Примечание.</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Почтовые пользователи (также известные как <em>пользователи с включенной поддержкой почты</em>) отличаются от пользователей с почтовым ящиком в организации. Главное различие состоит в том, что почтовые пользователи являются пользователями вне пределов организации Exchange, которые имеют внешний адрес электронной почты. У них нет почтового ящика в вашей организации. Дополнительные сведения о различиях между пользователями, которые имеют почтовые ящики в организации, и почтовыми пользователями см. в разделе <a href="recipients-exchange-2013-help.md">Получатели</a>.</td>
</tr>
</tbody>
</table>


Дополнительные сведения о задачах управления, связанных с почтовыми пользователями, см. в разделе [Управление пользователями почты](manage-mail-users-exchange-2013-help.md).

## Что нужно знать перед началом работы?

  - Предполагаемое время для завершения каждой процедуры: 2 минут.

  - Для выполнения этих процедур необходимы соответствующие разрешения. Сведения о необходимых разрешениях см. в статье Запись «Почтовые пользователи» в разделе [Разрешения получателей](recipients-permissions-exchange-2013-help.md).

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

## Отключение электронной почты для почтового пользователя

Как указывалось ранее, при отключении электронной почты для почтового пользователя атрибуты Exchange удаляются из соответствующего объекта-почтового пользователя Active Directory, но сам пользователь сохраняется. Почтовый пользователь удаляется из списка почтовых пользователей в центре администрирования Exchange, но можно просмотреть соответствующий контактный объект Active Directory и управлять им, используя средство "Пользователи и компьютеры Active Directory" или командлеты **Get-MailUser** и **Set-Set-MailUser** в командной консоли.

## Использование центра администрирования Exchange для отключения электронной почты для почтового пользователя

1.  В центре администрирования Exchange выберите **Получатели** \> **Контакты**.

2.  В списке контактов щелкните почтового пользователя, для которого необходимо отключить электронную почту.

3.  Нажмите кнопки **Дополнительно**![Значок дополнительных параметров](images/JJ150550.5381819e-3b21-4873-8714-e9b956290b28(EXCHG.150).gif "Значок дополнительных параметров") и **Отключить**.

4.  Отобразится предупреждение с запросом на подтверждение отключения выбранного почтового пользователя. Нажмите кнопку **Да**, чтобы отключить его.

Почтовый пользователь будет удален из списка контактов.

## Использование командной консоли для отключения электронной почты для почтового пользователя

В этом примере показано, как отключить электронную почту для почтового пользователя Yan Li.

    Disable-MailUser -Identity "Yan Li"

Дополнительные сведения о синтаксисе и параметрах см. в разделе [Disable-MailUser](https://technet.microsoft.com/ru-ru/library/aa998578\(v=exchg.150\)).

## Как проверить, что все получилось?

Чтобы убедиться, что электронная почта для почтового пользователя успешно отключена, выполните одно из следующих действий.

1.  В центре администрирования Exchange перейдите в раздел **Получатели** \> **Контакты** и убедитесь, что почтовый пользователь отсутствует в списке.

2.  В средстве "Пользователи и компьютеры Active Directory" щелкните правой кнопкой мыши пользователя и выберите пункт **Свойства**. Обратите внимание, что поле **Электронная почта** на вкладке **Общие** пустое. Это указывает, что для почтового пользователя не включена поддержка почты.

3.  В консоли Shell выполните следующую команду:
    
        Get-MailUser
    
    Почтовый пользователь, для которого отключена электронная почта, будет отсутствовать в результатах, поскольку данный командлет возвращает только пользователей с включенной поддержкой почты.

4.  В консоли Shell выполните следующую команду:
    
        Get-User
    
    Почтовый пользователь, для которого отключена электронная почта, отобразится в результатах, поскольку данный командлет возвращает все объекты-пользователи Active Directory.

## Использование командной консоли для включения поддержки почты для пользователей

Командлет **Enable-MailUser** используется для включения поддержки почты для существующих пользователей Active Directory. Можно включить поддержку почты для одного или (используя CSV-файл) нескольких пользователей.

## Использование командной консоли для включения поддержки почты для одного пользователя

В этом примере включается поддержка почты для пользователя Sanjay Shah. Необходимо предоставить внешний адрес электронной почты.

    Enable-MailUser -Identity "Sanjay Shah" -ExternalEmailAddress renev@tailspintoys.com

## Использование командной консоли и CSV-файла для включения поддержки почты для нескольких пользователей

При включении поддержки почты для нескольких пользователей список пользователей без этой поддержки сначала экспортируется в CSV-файл (файл данных с разделителями-запятыми), после чего в CSV-файл с помощью текстового редактора (например, блокнота) или приложения электронных таблиц (например, Microsoft Excel) добавляются внешние адреса электронной почты. Затем обновленный CSV-файл используется в командной консоли, чтобы включить поддержку почты для пользователей, перечисленных в этом файле.

1.  Выполните следующую команду, чтобы экспортировать список существующих пользователей, для которых не включена поддержка почты или у которых нет почтового ящика в организации, в файл с именем UsersToMailEnable.csv на рабочем столе администратора.
    
        Get-User | Where { $_.RecipientType -eq "User" } | Out-File "C:\Users\Administrator\Desktop\UsersToMailEnable.csv"
    
    Полученный в результате файл будет иметь примерно следующий вид.
    
        Name            RecipientType
        ----            -------------
        Guest           User
        krbtgt          User
        RMS_SERVICE     User
        David Pelton    User
        Kim Akers       User
        Janet Schorr    User
        Jeffrey Zang    User
        Spencer Low     User
        Toni Poe        User
        ...

2.  Внесите в CSV-файл следующие изменения.
    
      - Удалите из CSV-файла всех пользователей, для которых не включена поддержка почты. Например, в предыдущем примере следует удалить первые три записи, поскольку они являются системными учетными записями по умолчанию.
    
      - Удалите столбец **RecipientType** и все экземпляры `User`.
    
      - Добавьте заголовок столбца **EmailAddress**, а затем адрес электронной почты для каждого пользователя в файле. Имена и внешние адреса электронной почты всех пользователей необходимо разделить запятыми.
    
    Обновленный CSV-файл будет иметь примерно следующий вид.
    
        Name,EmailAddress
        David Pelton,davidp@contoso.com
        Kim Akers,kakers@tailspintoys.com
        Janet Schorr,janet.schorr@adatum.com
        Jeffrey Zang,jzang@tailspintoys.com
        Spencer Low,spencerl@fouthcoffee.com
        Toni Poe,tonip@contoso.com
        ...

3.  Выполните следующую команду, чтобы использовать данные в CSV-файле с целью включения поддержки почты для пользователей, перечисленных в файле.
    
        Import-CSV "C:\Users\Administrator\Desktop\UsersToMailEnable.csv" | ForEach-Object {Enable-MailUser -Identity $_.Name -ExternalEmailAddress $_.EmailAddress}
    
    В результате команды отображаются сведения о новых пользователях с включенной поддержкой почты.

## Как проверить, что все получилось?

Чтобы убедиться, что поддержка почты для пользователей Active Directory успешно включена, выполните одно из следующих действий.

  - В центре администрирования Exchange выберите **Получатели** \> **Контакты**. Новые почтовые пользователи отображаются в списке контактов. В разделе **Тип контакта** указан тип **Пользователь почты**.
    
    <table>
    <thead>
    <tr class="header">
    <th><img src="images/JJ126620.note(EXCHG.150).gif" title="Примечание" alt="Примечание" />Примечание.</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td>Чтобы отобразить новых почтовых пользователей, может понадобиться нажать кнопку <strong>Обновить</strong><img src="images/Dd353189.85f271ca-32a4-426c-842a-d2172567099d(EXCHG.150).gif" title="Значок обновления" alt="Значок обновления" />.</td>
    </tr>
    </tbody>
    </table>


  - В командной консоли выполните приведенную ниже команду, чтобы отобразить сведения о новых почтовых пользователях.
    
        Get-MailUser | Format-Table Name,RecipientTypeDetails,ExternalEmailAddress
