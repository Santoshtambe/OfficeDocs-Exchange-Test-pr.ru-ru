﻿---
title: 'Настройка кодирования при передаче содержимого: Exchange 2013 Help'
TOCTitle: Настройка кодирования при передаче содержимого
ms:assetid: c4922362-18d4-42f7-9189-9076720eb1d8
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Gg144562(v=EXCHG.150)
ms:contentKeyID: 50489122
ms.date: 04/30/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Настройка кодирования при передаче содержимого

 

_**Применимо к:**Exchange Online, Exchange Server 2013_

_**Последнее изменение раздела:**2015-03-09_

*Кодирование передачи содержимого* определяет методы кодирования для преобразования двоичных данных сообщения электронной почты в формат обычного текста US-ASCII. Это обеспечивает возможность передачи сообщения через более старые серверы обмена сообщениями SMTP, которые поддерживают только текстовые сообщения в кодировке US-ASCII. Кодирование передачи содержимого определено в спецификации RFC 2045. Метод кодирования передачи хранится в поле **Content-Transfer-Encoding** заголовка сообщения. В Microsoft Exchange Server 2013 доступны следующие методы кодирования передачи содержимого.

  - **7-битовое**   Это значение указывает на то, что данные текста сообщения уже имеют формат обычного текста US ASCII и к сообщению не применялось кодирование.

  - **Quoted-printable (QP)**   Этот метод кодирует данные в тексте сообщения, используя печатные знаки US-ASCII. Если текст исходного сообщения содержит преимущественно знаки US-ASCII, кодирование по алгоритму QP позволяет получить компактный текст, относительно пригодный для чтения. По умолчанию Exchange 2013 использует QP для кодирования двоичных данных сообщения.

  - **Base64**   Этот метод кодирования во многом основан на стандарте PEM, определенном в документе RFC 1421. Для кодирования текста сообщения в этом случае используется 64-знаковый алфавит и знаки заполнения вывода, определенные в стандарте PEM. Этот алгоритм позволяет предугадать итоговый размер сообщения и лучше всего подходит для кодирования двоичных данных и текста в кодировке, отличной от US-ASCII.

Метод кодирования передачи настраивается с помощью параметра *ByteEncoderTypeFor7BitCharsets* в командлетах **Set-OrganizationConfig** и **Set-RemoteDomain**. Параметры кодировки передаваемого содержимого, настроенные с помощью **Set-OrganizationConfig**, применяются ко всем сообщениям в организации Exchange. Параметры кодирования передаваемого содержимого, настроенные с помощью **Set-RemoteDomain**, применяются только к сообщениям, отправленным внешним получателям в удаленном домене.

В следующей таблице приведены значения, которые можно использовать для настройки метода кодирования передаваемых данных.


<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th>Параметр в <strong>Set-OrganizationConfig</strong></th>
<th>Параметр в <strong>Set-RemoteDomain</strong></th>
<th>Описание</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>0</p></td>
<td><p><code>Use7Bit</code></p></td>
<td><p>Всегда используется 7-битное кодирование для HTML и обычного текста. Это значение по умолчанию.</p></td>
</tr>
<tr class="even">
<td><p>1</p></td>
<td><p><code>UseQP</code></p></td>
<td><p>Всегда используется кодирование QP для HTML и обычного текста.</p></td>
</tr>
<tr class="odd">
<td><p>2</p></td>
<td><p><code>UseBase64</code></p></td>
<td><p>Всегда используется кодирование Base64 для HTML и обычного текста.</p></td>
</tr>
<tr class="even">
<td><p>5</p></td>
<td><p><code>UseQPHtmlDetectTextPlain</code></p></td>
<td><p>Используется кодирование QP для HTML и обычного текста, если в обычном тексте не включен перенос строк. Если перенос строк включен, для обычного текста используется 7-битное кодирование.</p></td>
</tr>
<tr class="odd">
<td><p>6</p></td>
<td><p><code>UseBase64HtmlDetectTextPlain</code></p></td>
<td><p>Используется кодирование Base64 для HTML и обычного текста, если в обычном тексте не включен перенос строк. Если в обычном тексте включен перенос строк, используется кодирование Base64 для HTML и 7-битное кодирование для обычного текста.</p></td>
</tr>
<tr class="even">
<td><p>13</p></td>
<td><p><code>UseQPHtml7BitTextPlain</code></p></td>
<td><p>Всегда используется кодирование QP для HTML. Всегда используется 7-битное кодирование для обычного текста.</p></td>
</tr>
<tr class="odd">
<td><p>14</p></td>
<td><p><code>UseBase64Html7BitTextPlain</code></p></td>
<td><p>Всегда используется кодирование Base64 для HTML. Всегда используется 7-битное кодирование для обычного текста.</p></td>
</tr>
</tbody>
</table>


Дополнительные сведения о поле заголовка **Content-Transfer-Encoding** см. в разделе «Структура сообщений электронной почты» статье [Преобразование содержимого](content-conversion-exchange-2013-help.md).

Дополнительные сведения об удаленных доменах см. в разделе [Удаленные домены](remote-domains-exchange-2013-help.md).

## Что нужно знать перед началом работы?

  - Осталось времени до завершения: 15 минут

  - Для выполнения этих процедур необходимы соответствующие разрешения. Сведения о необходимых разрешениях см. в статье запись "Служба транспорта" в разделе [Разрешения потока обработки почты](mail-flow-permissions-exchange-2013-help.md).

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


## Что необходимо сделать?

## Использование командной консоли для настройки метода кодирования передаваемого содержимого для организации

Чтобы настроить метод кодирования передаваемого содержимого для организации, выполните следующую команду:

    Set-OrganizationConfig -ByteEncoderTypeFor7BitCharsets <Integer>

Например, чтобы задать для кодировки при передаче содержимого Base64, выполните следующую команду:

    Set-OrganizationConfig -ByteEncoderTypeFor7BitCharsets 2

## Использование командной консоли для настройки метода кодирования передаваемого содержимого для удаленного домена

Чтобы настроить метод кодирования передаваемого содержимого для всех получателей в удаленном домене, выполните следующую команду:

    Set-RemoteDomain -ByteEncoderTypeFor7BitCharsets <Value>

Например, чтобы задать для кодировки при передаче содержимого Base64, выполните следующую команду:

    Set- RemoteDomain -ByteEncoderTypeFor7BitCharsets UseBase64

## Как проверить, что все получилось?

Чтобы убедиться в успешной настройке метода кодирования передаваемого содержимого, выполните следующее:

1.  Отправьте тестовое сообщение, содержащее одновременно текст US-ASCII и двоичные данные или текст в формате, отличном от US-ASCII, во внутреннюю или внешнюю тестовую учетную запись. Проверьте параметры организации с помощью внутренней учетной записи, а параметры удаленного домена — с помощью внешней учетной записи .

2.  В клиенте электронной почты просмотрите поле заголовка **Content-Transfer-Encoding** в сообщении и проверьте, совпадает ли метод кодирования передаваемого содержимого, который использовался для сообщения, с настроенным вами методом.

