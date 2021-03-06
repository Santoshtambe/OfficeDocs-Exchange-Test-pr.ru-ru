﻿---
title: 'Политики почтовых ящиков мобильных устройств: Exchange 2013 Help'
TOCTitle: Политики почтовых ящиков мобильных устройств
ms:assetid: 9317b3bc-44a1-4e54-bc51-4f0b194b6a55
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Bb123783(v=EXCHG.150)
ms:contentKeyID: 50488661
ms.date: 04/30/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Политики почтовых ящиков мобильных устройств

 

_**Применимо к:**Exchange Server 2013_

_**Последнее изменение раздела:**2016-06-16_

В системе Майкрософт Exchange Server 2013 вы можете создать политики почтовых ящиков мобильных устройств, чтобы применять общий набор политик или параметров безопасности для ряда пользователей. После развертывания Exchange ActiveSync в организации Exchange 2013 можно создавать новые политики почтовых ящиков мобильных устройств или изменять существующие. При установке Exchange 2013 создается политика почтового ящика мобильного устройства по умолчанию. Эта политика назначается всем пользователям автоматически.

<table>
<thead>
<tr class="header">
<th><img src="images/Dd876857.important(EXCHG.150).gif" title="Важно" alt="Важно" />Важно!</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Мобильные телефоны Windows Phone 7 поддерживают только подмножество всех параметров политики почтового ящика Exchange ActiveSync. Полный список см. в разделе Синхронизация в Windows Phone 7.</td>
</tr>
</tbody>
</table>


<table>
<thead>
<tr class="header">
<th><img src="images/JJ983803.warning(EXCHG.150).gif" title="Предупреждение" alt="Предупреждение" />Предупреждение.</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Сканер отпечатков пальцев в ОС IOS7 не поддерживается в качестве пароля устройства. Если вы включите сканер отпечатков пальцев для защиты своего устройства под управлением ОС iOS7, также потребуется создать и вводить пароль, если политики почтовых ящиков вашего мобильного устройства требуют ввода пароля.</td>
</tr>
</tbody>
</table>


## Обзор политик почтовых ящиков мобильных устройств

Политики почтовых ящиков мобильных устройств можно использовать для управления множеством различных параметров. например:

  - Требование ввести пароль

  - Минимальная длина пароля

  - Требование наличия в пароле числа или специального символа

  - Период бездействия устройства перед требованием повторного ввода пароля

  - Очистка устройства после указанного количества неудачных попыток ввести пароль

Дополнительные сведения о всех настраиваемых параметрах см. в разделе "Параметры политик мобильных устройств".

## Управление политиками почтовых ящиков Exchange ActiveSync

Политики почтовых ящиков мобильных устройств можно создать в Центре администрирования Exchange (EAC) или в командной консоли Exchange. При создании политики в EAC можно настроить только некоторые из доступных параметров. Остальные параметры можно настроить с помощью командной консоли Exchange.

## Синхронизация с системой Windows Phone 7

При использовании мобильных телефонов под управлением Windows Phone 7 в организации будут возникать проблемы с их синхронизацией, если в данной организации настроены некоторые свойства политики почтовых ящиков Exchange ActiveSync. Чтобы разрешить синхронизацию мобильных телефонов Windows Phone 7 с почтовыми ящиками Exchange, установите для свойства **AllowNonProvisionableDevices** значение True или настройте следующие свойства политики почтовых ящиков Exchange ActiveSync:

  - AllowSimplePassword

  - BlockInternetSharing

  - BlockRemoteDesktop

  - DisableDesktopSync

  - DisableIrDA

  - DisableRemovableStorage

  - DeviceWipeThreshold

  - MinPasswordLength

  - IdleTimeoutFrequencyValue

  - PasswordExpiration

  - PasswordHistory

  - PasswordRequired

## Параметры политики почтовых ящиков мобильного устройства

В следующей таблице перечислены параметры, которые можно задать с помощью политик почтовых ящиков мобильных устройств.

### Параметры политики почтовых ящиков мобильного устройства

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th>Параметр</th>
<th>Описание</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Разрешить Bluetooth</p></td>
<td><p>Данный параметр определяет, будет ли мобильное устройство принимать подключения Bluetooth. Доступны следующие значения: &quot;Отключить&quot;, &quot;Только для громкой связи&quot; и &quot;Разрешить&quot;. Значение этого параметра по умолчанию — &quot;Разрешить&quot;. Чтобы изменить значение этого параметра, необходима корпоративная лицензия клиентского доступа Exchange.</p></td>
</tr>
<tr class="even">
<td><p>Разрешить браузер</p></td>
<td><p>Этот параметр определяет, разрешен ли на мобильном устройстве браузер Pocket Internet Explorer. Этот параметр не влияет на браузеры сторонних производителей, установленные на мобильном устройстве. По умолчанию параметр имеет значение <code>$true</code>. Чтобы изменить значение этого параметра, необходима корпоративная лицензия клиентского доступа Exchange.</p></td>
</tr>
<tr class="odd">
<td><p>Разрешить камеру</p></td>
<td><p>Этот параметр определяет, можно ли использовать камеру мобильного устройства. По умолчанию параметр имеет значение <code>$true</code>. Чтобы изменить значение этого параметра, необходима корпоративная лицензия клиентского доступа Exchange.</p></td>
</tr>
<tr class="even">
<td><p>Разрешить пользовательскую электронную почту</p></td>
<td><p>Этот параметр определяет, может ли пользователь настраивать личную учетную запись электронной почты (POP3 или IMAP4) на мобильном устройстве. По умолчанию параметр имеет значение <code>$true</code>. Этот параметр не контролирует доступ посторонних почтовых программ для мобильных устройств к электронной почте. Чтобы изменить значение этого параметра, необходима корпоративная лицензия клиентского доступа Exchange.</p></td>
</tr>
<tr class="odd">
<td><p>Разрешить синхронизацию с настольным ПК</p></td>
<td><p>Этот параметр определяет, может ли мобильное устройство синхронизироваться с настольным компьютером через кабель, порт IrDA или Bluetooth. По умолчанию параметр имеет значение <code>$true</code>. Чтобы изменить значение этого параметра, необходима корпоративная лицензия клиентского доступа Exchange.</p></td>
</tr>
<tr class="even">
<td><p>Разрешить управление внешним устройством</p></td>
<td><p>Этот параметр определяет, разрешено ли внешней программе управления устройствами управлять мобильным устройством.</p></td>
</tr>
<tr class="odd">
<td><p>Разрешить сообщения электронной почты в формате HTML</p></td>
<td><p>Этот параметр определяет, может ли электронная почта при синхронизации с мобильным устройством сохранять формат HTML. Если для этого параметра установлено значение <code>$false</code>, вся электронная почта преобразуется в обычный текст.</p></td>
</tr>
<tr class="even">
<td><p>Разрешить общий доступ к Интернету</p></td>
<td><p>Этот параметр определяет, можно ли использовать мобильное устройство в качестве модема для настольного или портативного компьютера. По умолчанию параметр имеет значение <code>$true</code>. Чтобы изменить значение этого параметра, необходима корпоративная лицензия клиентского доступа Exchange.</p></td>
</tr>
<tr class="odd">
<td><p>AllowIrDA</p></td>
<td><p>Этот параметр определяет, разрешены ли на мобильном устройстве инфракрасные соединения. Чтобы изменить значение этого параметра, необходима корпоративная лицензия клиентского доступа Exchange.</p></td>
</tr>
<tr class="even">
<td><p>Разрешить обновление Mobile OTA</p></td>
<td><p>Этот параметр определяет, можно ли отправлять параметры политики почтового ящика мобильного устройства на мобильное устройство через мобильное подключение. По умолчанию параметр имеет значение <code>$true</code>.</p></td>
</tr>
<tr class="odd">
<td><p>Разрешить неинициализируемые устройства</p></td>
<td><p>Этот параметр определяет, разрешено ли мобильным устройствам, которые могут не поддерживать применение всех параметров политики, подключаться к Exchange 2013 с помощью Exchange ActiveSync. Использование неинициализируемых мобильных устройств представляет угрозы для безопасности. Например, некоторые неинициализируемые устройства могут не применять требования организации к паролям.</p></td>
</tr>
<tr class="even">
<td><p>Разрешить POPIMAPEmail</p></td>
<td><p>Этот параметр определяет, может ли пользователь настроить на мобильном устройстве учетную запись электронной почты POP3 или IMAP4. Значение по умолчанию — <code>$true</code>. Этот параметр не управляет доступом посторонних почтовых программ.</p></td>
</tr>
<tr class="odd">
<td><p>Разрешить подключение к удаленному рабочему столу</p></td>
<td><p>Этот параметр определяет, может ли мобильное устройство инициировать подключение к удаленному рабочему столу. По умолчанию параметр имеет значение <code>$true</code>. Чтобы изменить значение этого параметра, необходима корпоративная лицензия клиентского доступа Exchange.</p></td>
</tr>
<tr class="even">
<td><p>Разрешить использовать простой пароль</p></td>
<td><p>Этот параметр включает или отключает функцию использования простого пароля, например &quot;1111&quot; или &quot;1234&quot;. Значение по умолчанию — <code>$true</code>.</p></td>
</tr>
<tr class="odd">
<td><p>Разрешить согласование алгоритма шифрования S/MIME</p></td>
<td><p>Этот параметр указывает, может ли приложение для обмена сообщениями на мобильном устройстве согласовывать алгоритм шифрования, если сертификат получателя не поддерживает указанный алгоритм.</p></td>
</tr>
<tr class="even">
<td><p>Разрешить сертификаты программного обеспечения S/MIME</p></td>
<td><p>Этот параметр определяет, разрешены ли на мобильном устройстве сертификаты программного обеспечения S/MIME.</p></td>
</tr>
<tr class="odd">
<td><p>Разрешить карты памяти</p></td>
<td><p>Этот параметр определяет, позволяет ли мобильное устройство получать доступ к сведениям, которые хранятся на карте памяти. Чтобы изменить значение этого параметра, необходима корпоративная лицензия клиентского доступа Exchange.</p></td>
</tr>
<tr class="even">
<td><p>Разрешить обмен текстовыми сообщениями</p></td>
<td><p>Этот параметр указывает, разрешен ли для мобильного устройства обмен текстовыми сообщениями. По умолчанию параметр имеет значение <code>$true</code>. Чтобы изменить значение этого параметра, необходима корпоративная лицензия клиентского доступа Exchange.</p></td>
</tr>
<tr class="odd">
<td><p>Разрешить неподписанные приложения</p></td>
<td><p>Этот параметр указывает, можно ли устанавливать на мобильное устройство неподписанные приложения. По умолчанию параметр имеет значение <code>$true</code>. Чтобы изменить значение этого параметра, необходима корпоративная лицензия клиентского доступа Exchange.</p></td>
</tr>
<tr class="even">
<td><p>Разрешить неподписанные установочные пакеты</p></td>
<td><p>Этот параметр указывает, можно ли запускать на мобильном устройстве неподписанные установочные пакеты. По умолчанию параметр имеет значение <code>$true</code>. Чтобы изменить значение этого параметра, необходима корпоративная лицензия клиентского доступа Exchange.</p></td>
</tr>
<tr class="odd">
<td><p>Разрешить Wi-Fi</p></td>
<td><p>Этот параметр указывает, разрешен ли для мобильного устройства беспроводной доступ к Интернету. По умолчанию параметр имеет значение <code>$true</code>. Чтобы изменить значение этого параметра, необходима корпоративная лицензия клиентского доступа Exchange.</p></td>
</tr>
<tr class="even">
<td><p>Требовать ввода буквенно-цифрового пароля</p></td>
<td><p>Этот параметр требует, чтобы пароль содержал не только цифры, но и другие символы. По умолчанию параметр имеет значение <code>$true</code>.</p></td>
</tr>
<tr class="odd">
<td><p>Список одобренных приложений</p></td>
<td><p>Этот параметр содержит список одобренных приложений, которые можно запускать на мобильном устройстве. Чтобы изменить значение этого параметра, необходима корпоративная лицензия клиентского доступа Exchange.</p></td>
</tr>
<tr class="even">
<td><p>Вложения разрешены</p></td>
<td><p>Этот параметр разрешает загрузку вложений на мобильное устройство. По умолчанию параметр имеет значение <code>$true</code>.</p></td>
</tr>
<tr class="odd">
<td><p>Шифрование устройства включено</p></td>
<td><p>Этот параметр включает шифрование на мобильном устройстве. Не все мобильные устройства могут поддерживать шифрование. Дополнительные сведения см. в документации на устройство и операционную систему.</p></td>
</tr>
<tr class="even">
<td><p>Интервал обновления политики устройства</p></td>
<td><p>Этот параметр указывает частоту, с которой политики почтового ящика мобильного устройства отправляется с сервера на мобильное устройство.</p></td>
</tr>
<tr class="odd">
<td><p>Служба IRM включена</p></td>
<td><p>Этот параметр указывает, включена ли служба управления правами доступа к данным (IRM) на мобильном устройстве.</p></td>
</tr>
<tr class="even">
<td><p>Максимальный размер вложения</p></td>
<td><p>Этот параметр контролирует максимальный размер вложений, которые могут быть загружены на мобильное устройство. Значение по умолчанию — &quot;Unlimited&quot;.</p></td>
</tr>
<tr class="odd">
<td><p>Фильтр максимального времени хранения календаря</p></td>
<td><p>Этот параметр задает максимальный диапазон дней календаря, который можно синхронизировать с мобильным устройством. Допустимы следующие значения:</p>
<ol>
<li><p>All</p></li>
<li><p>OneDay</p></li>
<li><p>ThreeDays</p></li>
<li><p>OneWeek</p></li>
<li><p>TwoWeeks</p></li>
<li><p>OneMonth</p></li>
</ol></td>
</tr>
<tr class="even">
<td><p>Фильтр максимального времени хранения электронной почты</p></td>
<td><p>Этот параметр задает максимальное количество дней для сообщений электронной почты, для которых выполняется синхронизация с мобильным устройством. Допустимы следующие значения:</p>
<ol>
<li><p>All</p></li>
<li><p>OneDay</p></li>
<li><p>ThreeDays</p></li>
<li><p>OneWeek</p></li>
<li><p>TwoWeeks</p></li>
<li><p>OneMonth</p></li>
</ol></td>
</tr>
<tr class="odd">
<td><p>Максимальный размер усечения текста сообщений электронной почты</p></td>
<td><p>Этот параметр задает максимальный размер сообщений электронной почты, при котором они усекаются во время синхронизации с мобильным устройством. Значение задается в килобайтах (КБ).</p></td>
</tr>
<tr class="even">
<td><p>Максимальный размер текста сообщений электронной почты в формате HTML</p></td>
<td><p>Этот параметр задает максимальный размер сообщений электронной почты в формате HTML, при котором они усекаются во время синхронизации с мобильным устройством. Значение задается в килобайтах (КБ).</p></td>
</tr>
<tr class="odd">
<td><p>Максимальное время простоя до блокировки</p></td>
<td><p>Этот параметр указывает период бездействия мобильного устройства, в течение которого для возобновления работы устройства не требуется вводить пароль. Можно задать интервал от 30 секунд до 1 часа. Значение по умолчанию равно 15 минутам.</p></td>
</tr>
<tr class="even">
<td><p>Максимальное количество неудачных попыток ввода пароля</p></td>
<td><p>Этот параметр указывает число попыток ввода правильного пароля для мобильного устройства. Можно ввести число от 4 до 16. Значение по умолчанию — 8.</p></td>
</tr>
<tr class="odd">
<td><p>Минимальное количество сложных символов в пароле</p></td>
<td><p>Этот параметр задает необходимое количество наборов символов в пароле мобильного устройства. К наборам символов относятся:</p>
<ul>
<li><p>буквы нижнего регистра;</p></li>
<li><p>буквы верхнего регистра;</p></li>
<li><p>цифры (от 0 до 9);</p></li>
<li><p>специальные символы (например, восклицательные знаки).</p></li>
</ul>
<p>Можно ввести любое число от 1 до 4. Значение по умолчанию — 1.</p>
<p>Для устройств с Windows Phone 8 этот параметр задает необходимое количество наборов символов в пароле. Например, если задано значение 3, то необходимо как минимум по одному символу из любых трех наборов символов.</p>
<p>Для устройств с Windows Phone 10 этот параметр задает следующие требования к сложности пароля:</p>
<ol>
<li><p>Только цифры.</p></li>
<li><p>Цифры и буквы нижнего регистра.</p></li>
<li><p>Цифры, а также буквы нижнего и верхнего регистров.</p></li>
<li><p>Цифры, буквы нижнего и верхнего регистров, а также специальные символы.</p></li>
</ol></td>
</tr>
<tr class="even">
<td><p>Минимальная длина пароля</p></td>
<td><p>Этот параметр указывает минимальное число знаков в пароле мобильного устройства. Можно ввести число от 1 до 16. Значение по умолчанию — 4.</p></td>
</tr>
<tr class="odd">
<td><p>Пароль включен</p></td>
<td><p>Этот параметр включает пароль мобильного устройства.</p></td>
</tr>
<tr class="even">
<td><p>Срок действия пароля</p></td>
<td><p>Этот параметр позволяет администратору настроить временной интервал, по истечении которого необходимо изменить пароль мобильного устройства.</p></td>
</tr>
<tr class="odd">
<td><p>Журнал пароля</p></td>
<td><p>Этот параметр определяет число использовавшихся паролей, хранящихся в почтовом ящике пользователя. Пользователь не может использовать сохраненный пароль повторно.</p></td>
</tr>
<tr class="even">
<td><p>Восстановление пароля включено</p></td>
<td><p>При включении этого параметра на мобильном устройстве создается пароль для восстановления, который отправляется на сервер. Если пользователь забыл пароль мобильного устройства, чтобы разблокировать мобильное устройство и разрешить пользователю создать новый пароль, можно использовать пароль для восстановления.</p></td>
</tr>
<tr class="odd">
<td><p>Требовать шифрование устройства</p></td>
<td><p>Этот параметр определяет, необходимо ли шифрование для устройства. Если параметр имеет значение <code>$true</code>, мобильное устройство должно поддерживать и применять шифрование для синхронизации с сервером.</p></td>
</tr>
<tr class="even">
<td><p>Требовать шифрование сообщений S/MIME</p></td>
<td><p>Этот параметр определяет, необходимо ли шифровать сообщения S/MIME. По умолчанию параметр имеет значение <code>$false</code>.</p></td>
</tr>
<tr class="odd">
<td><p>Требовать алгоритм шифрования S/MIME</p></td>
<td><p>Этот параметр задает алгоритм, который должен использоваться для шифрования сообщений S/MIME.</p></td>
</tr>
<tr class="even">
<td><p>Требовать при роуминге выполнение синхронизации вручную</p></td>
<td><p>Этот параметр указывает, должно ли мобильное устройство синхронизироваться вручную при роуминге. Включение автоматической синхронизации при роуминге может привести к непредвиденным расходам на мобильную связь.</p></td>
</tr>
<tr class="odd">
<td><p>Требовать подписанный алгоритм S/MIME</p></td>
<td><p>Этот параметр задает алгоритм, который должен использоваться для подписи сообщения.</p></td>
</tr>
<tr class="even">
<td><p>Требовать подписанные сообщения S/MIME</p></td>
<td><p>Этот параметр указывает, должно ли мобильное устройство отправлять подписанные сообщения S/MIME.</p></td>
</tr>
<tr class="odd">
<td><p>Требовать шифрование карты памяти</p></td>
<td><p>Этот параметр определяет, необходимо ли шифровать карту памяти. Не все операционные системы для мобильных устройств поддерживают шифрование карт памяти. Дополнительные сведения см. в документации к мобильному устройству и операционной системе.</p></td>
</tr>
<tr class="even">
<td><p>Список недопустимых приложений в ПЗУ</p></td>
<td><p>Этот параметр содержит список приложений, которые невозможно запускать в ПЗУ. Чтобы изменить значение этого параметра, необходима корпоративная лицензия клиентского доступа Exchange.</p></td>
</tr>
</tbody>
</table>

