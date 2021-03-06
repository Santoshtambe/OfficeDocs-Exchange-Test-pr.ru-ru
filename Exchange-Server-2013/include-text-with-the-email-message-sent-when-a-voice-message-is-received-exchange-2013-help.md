﻿---
title: 'Включение текста с сообщением электронной почты при получении сообщения голосовой связи: Exchange 2013 Help'
TOCTitle: Включение текста с сообщением электронной почты при получении сообщения голосовой связи
ms:assetid: b2eec29c-e5eb-4263-80d8-0b9813dd56dc
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Bb201718(v=EXCHG.150)
ms:contentKeyID: 51408065
ms.date: 05/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: MT
---

# Включение текста с сообщением электронной почты при получении сообщения голосовой связи

 

_**Применимо к:**Exchange Online, Exchange Server 2013, Exchange Server 2016_

_**Последнее изменение раздела:**2012-12-16_

В сообщение электронной почты, отправляемое при получении пользователями с включенной поддержкой единой системы обмена сообщениями сообщения голосовой почты, можно добавить дополнительный текст. По умолчанию текст, добавляемый в голосовое сообщение, сообщает только о том, что пользователь получил голосовое сообщение. Тем не менее, вы можете создать специальное сообщение, добавив текст в поле **Если пользователь получает голосовое сообщение** в политике почтовых ящиков единой системы обмена сообщениями. Например, этот текст может содержать сведения о политиках безопасности системы и описывать правильный способ обработки сообщений голосовой почты в организации. Добавленный текст будет включаться во все сообщения электронной почты, которые отправляются при получении голосовых сообщений пользователями единой системы обмена сообщениями, связанными с политикой почтовых ящиков единой системы обмена сообщениями.

<table>
<thead>
<tr class="header">
<th><img src="images/JJ126620.note(EXCHG.150).gif" title="Примечание" alt="Примечание" />Примечание.</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Максимальная длина настраиваемого текста, сопровождающего голосовое сообщение, составляет 512 символов. Сообщение может содержать простой текст в формате HTML.</td>
</tr>
</tbody>
</table>


Дополнительные сведения об управленческих задачах, связанных с политиками почтовых ящиков единой системы обмена сообщениями, см. в разделе [Процедуры политики почтовых ящиков единой системы обмена СООБЩЕНИЯМИ](um-mailbox-policy-procedures-exchange-2013-help.md).

## Что нужно знать перед началом работы

  - Предполагаемое время для завершения: менее 1 минуты.

  - Для выполнения этих процедур необходимы соответствующие разрешения. Сведения о необходимых разрешениях см. в статье Запись «Политики почтовых ящиков единой системы обмена сообщениями» в разделе [Разрешения единой системы обмена сообщениями](unified-messaging-permissions-exchange-2013-help.md).

  - Перед выполнением этих процедур убедитесь, что абонентская группа единой системы обмена сообщениями создана. Дополнительные сведения см. в разделе [Создание абонентской группы единой системы обмена сообщениями](create-a-um-dial-plan-exchange-2013-help.md).

  - Перед выполнением этих процедур убедитесь, что политика почтовых ящиков единой системы обмена сообщениями создана. Дополнительные сведения см. в разделе [Создание политики почтовых ящиков единой системы обмена сообщениями](create-a-um-mailbox-policy-exchange-2013-help.md).

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

## Использование Центра администрирования Exchange для изменения текста, включаемого в голосовое сообщение

1.  В Центре администрирования Exchange последовательно выберите пункты **Единая система обмена сообщениями** \> **Абонентские группы единой системы обмена сообщениями**. Выберите из списка абонентскую группу единой системы обмена сообщениями, которую необходимо изменить, и нажмите кнопку **Правка**![Значок редактирования](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Значок редактирования").

2.  На странице **Абонентская группа единой системы обмена сообщениями** в разделе **Политики почтовых ящиков единой системы обмена сообщениями** выберите необходимую политику почтовых ящиков этой системы, а затем нажмите кнопку **Изменить**![Значок редактирования](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Значок редактирования").

3.  На странице **Политика почтовых ящиков единой системы обмена сообщениями** \> в разделе**Текст сообщения**, в текстовом поле **Если пользователь получает голосовое сообщение** введите текст, который нужно включить в почтовое сообщение, отправляемое при получении пользователями голосового сообщения.

4.  Нажмите кнопку **Сохранить**.

## Использование командной консоли для изменения текста, включаемого в голосовое сообщение

В этом примере в голосовые сообщения, отправляемые пользователям, связанным с политикой почтовых ящиков единой системы обмена сообщениями с именем `MyUMMailboxPolicy`, добавляется текст "Не пересылайте голосовые сообщения пользователям за пределами организации".

    Set-UMMailboxPolicy -identity MyUMMailboxPolicy -VoiceMailText "Do not forward voice messages to users outside this organization."

