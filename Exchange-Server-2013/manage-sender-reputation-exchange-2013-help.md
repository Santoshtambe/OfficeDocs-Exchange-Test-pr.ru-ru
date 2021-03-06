﻿---
title: 'Управление репутацией отправителя: Exchange 2013 Help'
TOCTitle: Управление репутацией отправителя
ms:assetid: f2716bd9-e3ac-46d9-9264-4e3dabfa0f38
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Bb125186(v=EXCHG.150)
ms:contentKeyID: 50489497
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Управление репутацией отправителя

 

_**Применимо к:**Exchange Server 2013_

_**Последнее изменение раздела:**2015-04-08_

Функция репутации отправителя обеспечивается агентом анализа протокола. Репутация отправителя блокирует сообщения в зависимости от различных характеристик отправителя. Репутация отправителя основана на имеющихся сведениях об отправителе и определяет, какое действие будет предпринято (если это требуется) в отношении данного входящего сообщения.

## Что нужно знать перед началом работы?

  - Предполагаемое время для завершения каждой процедуры: 5 минут

  - Для выполнения этих процедур необходимы соответствующие разрешения. Сведения о необходимых разрешениях см. в статье Запись «Функции защиты от нежелательной почты» в разделе [Разрешения для защиты от нежелательной почты и вредоносных программ](anti-spam-and-anti-malware-permissions-exchange-2013-help.md).

  - Для выполнения этой процедуры можно использовать только командную консоль.

  - По умолчанию функции защиты от нежелательной почты в транспортной службе на сервере почтовых ящиков не включены. Как правило, функции защиты от нежелательной почты на сервере почтовых ящиков включают, только если организация Exchange не выполняет никакую предварительную фильтрацию нежелательной почты до приема входящих сообщений. Дополнительную информацию см. в статье [Включение функции защиты от нежелательной почты на сервере почтовых ящиков](enable-anti-spam-functionality-on-mailbox-servers-exchange-2013-help.md).

  - Функция репутации отправителя основана на использовании агента анализа протокола. При отключении функции репутации отправителя агент анализа протокола все еще включен.

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


## Что нужно сделать

## Включение или отключение функции репутации отправителя с помощью командной консоли Exchange

В этом примере показано, как отключить функцию репутации отправителя.

    Set-SenderReputationConfig -Enabled $false

В этом примере показано, как включить функцию репутации отправителя.

    Set-SenderReputationConfig -Enabled $true

## Как проверить, что все получилось?

Чтобы убедиться, что функция репутации отправителя успешно включена или отключена, выполните следующие действия.

1.  Убедитесь, что агент анализа протокола установлен и включен, выполнив следующую команду:
    
        Get-TransportAgent

2.  Проверьте настроенные значения репутации отправителя, выполнив следующую команду:
    
        Get-SenderReputationConfig | Format-List Enabled,*MailEnabled

## Включение или отключение функции репутации отправителя для внутренних или внешних сообщений с помощью командной консоли Exchange

По умолчанию репутация отправителя включена для внешних сообщений и отключена для внутренних. Сообщение считается внешним, если оно пришло с непроверенного подключения за пределами организации Exchange. Сообщение считается внутренним, если оно пришло с проверенного подключения, а домен отправителя настроен как доверенный домен организации Exchange.

Чтобы отключить репутацию отправителя, выполните следующую команду:

    Set-SenderReputationConfig -ExternalMailEnabled $false

Чтобы включить репутацию отправителя, выполните следующую команду:

    Set-SenderReputationConfig -ExternalMailEnabled $true

Чтобы отключить репутацию отправителя для внутренних сообщений, выполните следующую команду:

    Set-SenderReputationConfig -InternalMailEnabled $false

Чтобы включить репутацию отправителя для внутренних сообщений, выполните следующую команду:

    Set-SenderReputationConfig -InternalMailEnabled $true

## Как проверить, что все получилось?

Чтобы убедиться, что функция репутации отправителя для внутренних и внешних сообщений успешно включена или отключена, выполните следующие действия.

1.  Выполните следующую команду:
    
        Get-SenderReputationConfig | Format-List Enabled,*MailEnabled

2.  Убедитесь, что отображаемые значения совпадают с настроенными значениями.

## Настройка свойств репутации отправителя с помощью командной консоли Exchange

Чтобы настроить свойства репутации отправителя, выполните следующую команду:

    Set-SenderReputationConfig -SrlBlockThreshold <Value> -SenderBlockingPeriod <Hours>

В этом примере устанавливается значение 6 для порога блокировки уровня репутации отправителя (SRL), и выполняется настройка репутации отправителя для добавления нежелательных отправителей в список заблокированных IP-адресов на 36 часов:

    Set-SenderReputationConfig -SrlBlockThreshold 6 -SenderBlockingPeriod 36

## Как проверить, что все получилось?

Чтобы убедиться, что свойства репутации отправителя успешно настроены, выполните следующие действия.

1.  Выполните следующую команду:
    
        Get-SenderReputationConfig

2.  Убедитесь, что отображаемые значения совпадают с настроенными значениями.

## Настройка исходящего доступа для обнаружения открытых прокси-серверов с помощью командной консоли Exchange

Чтобы позволить репутации отправителя обойти все брандмауэры между Интернетом и сервером Exchange, на котором запущен агент анализа протокола, может потребоваться выполнение дополнительных действий. В следующей таблице приведен список исходящих портов, необходимых для репутации отправителя.


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Протоколы</th>
<th>Порты</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>SOCKS4, SOCKS5</p></td>
<td><p>1081, 1080</p></td>
</tr>
<tr class="even">
<td><p>Wingate, Telnet, Cisco</p></td>
<td><p>23</p></td>
</tr>
<tr class="odd">
<td><p>HTTP CONNECT, HTTP POST</p></td>
<td><p>6588, 3128, 80</p></td>
</tr>
</tbody>
</table>


Чтобы настроить исходящий доступ для обнаружения открытых прокси-серверов, выполните следующую команду:

    Set-SenderReputationConfig -ProxyServerName <String> -ProxyServerPort <Port> -ProxyServerType <String>

В этом примере настраивается репутация отправителя для использования открытого прокси-сервера SERVER01, который использует протокол HTTP CONNECT через порт 80.

    Set-SenderReputationConfig - ProxyServerName SERVER01 -ProxyServerPort 80 -ProxyServerType HttpConnect

## Как проверить, что все получилось?

Чтобы убедиться, что исходящий доступ для определения открытых прокси-серверов успешно настроен, выполните следующие действия.

1.  Выполните следующую команду:
    
        Get-SenderReputationConfig | Format-List ProxyServer*

2.  Убедитесь, что отображаются значения, которые вы настроили.

