﻿---
title: 'Внешние соединители: Exchange 2013 Help'
TOCTitle: Внешние соединители
ms:assetid: 21c6a7a9-f4d2-4359-9ac9-930701b63a4e
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Aa996779(v=EXCHG.150)
ms:contentKeyID: 50487604
ms.date: 04/30/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Внешние соединители

 

_**Применимо к:**Exchange Server 2013_

_**Последнее изменение раздела:**2012-09-25_

Внешний соединитель доставляет сообщения на сервер или во внешнюю систему, не использующую протокол SMTP в качестве основного механизма транспорта. В качестве примера можно привести сервер шлюза для факсов. Внешний соединитель использует локальный или общий транзитный каталог для отправки исходящих сообщений с помощью передачи файлов во внешнюю систему. Внешние соединители создаются в службе транспорта сервера почтовых ящиков Microsoft Exchange Server 2013.

Серверы внешних шлюзов могут отправлять сообщения в организацию Exchange 2013 с помощью каталогов раскладки или преобразования, существующих в службе транспорта сервера почтовых ящиков. Правильно отформатированные файлы сообщений электронной почты, скопированные в каждый каталог, передаются для доставки в почтовый ящик Exchange.

<table>
<thead>
<tr class="header">
<th><img src="images/Bb124558.tip(EXCHG.150).gif" title="Совет" alt="Совет" />Совет.</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>В большинстве случаев, где нужно доставить исходящие сообщения в систему, отличную от SMTP, рекомендуется использовать соединители агента доставки, поскольку они позволяют управлять очередью сообщений, не требуют записывания сообщений в файловую систему и имеют другие преимущества. Более подробные сведения можно найти в разделе <a href="delivery-agents-and-delivery-agent-connectors-exchange-2013-help.md">Агенты доставки и соединители агентов доставки</a>.</td>
</tr>
</tbody>
</table>


## Дополнительные сведения

[Создание внешнего соединителя для доставки сообщений факс отличного от SMTP-шлюза](create-a-foreign-connector-to-deliver-messages-to-a-non-smtp-fax-gateway-exchange-2013-help.md)

[Агенты доставки и соединители агентов доставки](delivery-agents-and-delivery-agent-connectors-exchange-2013-help.md)

[New-ForeignConnector](https://technet.microsoft.com/ru-ru/library/aa996310\(v=exchg.150\))

[Set-ForeignConnector](https://technet.microsoft.com/ru-ru/library/bb123789\(v=exchg.150\))

