﻿---
title: 'Разрешения соединителя получения: Exchange 2013 Help'
TOCTitle: Разрешения соединителя получения
ms:assetid: 31af7139-6823-411b-81b3-e42edd83ee6c
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/JJ673053(v=EXCHG.150)
ms:contentKeyID: 50487760
ms.date: 04/30/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Разрешения соединителя получения

 

_**Применимо к:**Exchange Server 2013_

_**Последнее изменение раздела:**2015-04-07_

В следующей таблице перечислены типы разрешений и описание каждого из них.


<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Разрешение соединителя получения</th>
<th>Описание</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>ms-Exch-SMTP-Submit</p></td>
<td><p>Это разрешение должно быть предоставлено сеансу, иначе он не сможет передавать сообщения данному получающему соединителю. Если сеанс не имеет этого разрешения, команды MAIL FROM и AUTH завершатся сбоем.</p></td>
</tr>
<tr class="even">
<td><p>ms-Exch-SMTP-Accept-Any-Recipient</p></td>
<td><p>Это разрешение позволяет сеансу ретранслировать сообщения через соединитель. Если это разрешение отсутствует, соединитель будет принимать только сообщения, адресованные получателям в обслуживаемых доменах.</p></td>
</tr>
<tr class="odd">
<td><p>ms-Exch-SMTP-Accept-Any-Sender</p></td>
<td><p>Это разрешение позволяет сеансу обходить проверку на подмену адреса отправителя.</p></td>
</tr>
<tr class="even">
<td><p>ms-Exch-SMTP-Accept-Authoritative-Domain-Sender</p></td>
<td><p>Это разрешение позволяет отправителям с адресами электронной почты в удостоверяющих доменах устанавливать сеанс с получающим соединителем.</p></td>
</tr>
<tr class="odd">
<td><p>ms-Exch-SMTP-Accept-Authentication-Flag</p></td>
<td><p>Это разрешение позволяет серверам Exchange 2003 отправлять сообщения от внутренних отправителей. При этом Exchange 2010 распознает эти сообщения как внутренние. Отправитель может объявить сообщение &quot;доверенным&quot;. Сообщения, входящие в систему Exchange через анонимную доставку, будут ретранслироваться в организации Exchange с этим флагом как ненадежные.</p></td>
</tr>
<tr class="even">
<td><p>ms-Exch-Accept-Headers-Routing</p></td>
<td><p>Это разрешение позволяет сеансу передавать сообщение со всеми неизмененными заголовками. Если это разрешение отсутствует, сервер удалит все полученные заголовки.</p></td>
</tr>
<tr class="odd">
<td><p>ms-Exch-Accept-Headers-Organization</p></td>
<td><p>Это разрешение позволяет сеансу передавать сообщение с неизмененными заголовками организаций. Все заголовки организации начинаются с фразы <strong>X-MS-Exchange-Organization-</strong>. Если это разрешение отсутствует, получающий сервер удалит все заголовки организации.</p></td>
</tr>
<tr class="even">
<td><p>ms-Exch-Accept-Headers-Forest</p></td>
<td><p>Это разрешение позволяет сеансу передавать сообщение со всеми неизмененными заголовками леса. Все заголовки леса начинаются с фразы <strong>X-MS-Exchange-Forest-</strong>. Если это разрешение отсутствует, получающий сервер удалит все заголовки леса.</p></td>
</tr>
<tr class="odd">
<td><p>ms-Exch-Accept-Exch50</p></td>
<td><p>Это разрешение позволяет сеансу передавать сообщения, содержащие команды XEXCH50. Эта команда необходима для взаимодействия с Exchange 2003. Команда XEXCH50 предоставляет такие данные о сообщении, как уровень вероятности нежелательной почты (SCL).</p></td>
</tr>
<tr class="even">
<td><p>ms-Exch-Bypass-Message-Size-Limit</p></td>
<td><p>Это разрешение позволяет сеансу передавать сообщения, выходящие за ограничение размера сообщения, настроенного для соединителя.</p></td>
</tr>
<tr class="odd">
<td><p>Ms-Exch-Bypass-Anti-Spam</p></td>
<td><p>Это разрешение позволяет сеансу обходить фильтр нежелательной почты.</p></td>
</tr>
</tbody>
</table>
