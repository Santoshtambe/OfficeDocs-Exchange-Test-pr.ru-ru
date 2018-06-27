﻿---
title: 'Управление политиками защиты от потери данных: Exchange 2013 Help'
TOCTitle: Управление политиками защиты от потери данных
ms:assetid: ba81fabd-7f7f-4ef7-968f-ce851ada9d70
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/JJ673559(v=EXCHG.150)
ms:contentKeyID: 50489001
ms.date: 04/30/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Управление политиками защиты от потери данных

 

_**Применимо к:**Exchange Online, Exchange Server 2013_

_**Последнее изменение раздела:**2015-01-14_

Можно просматривать, изменять или удалять существующие политики предотвращения потери данных (DLP) в службе Microsoft Exchange с помощью Центра администрирования Exchange (EAC) или командной консоли Exchange.

Дополнительные задачи управления, связанные с политиками DLP, приведены в разделе [Процедуры защиты от потери данных](dlp-procedures-exchange-2013-help.md) (Exchange Server 2013) или [Процедуры защиты от потери данных](https://technet.microsoft.com/ru-ru/library/jj938003\(v=exchg.150\)) (Exchange Online).

Для получения дополнительных сведений о командной консоли Exchange см. раздел [Использование Powershell с Exchange 2013 (командная консоль Exchange)](https://technet.microsoft.com/ru-ru/library/bb123778\(v=exchg.150\)).

## Что нужно знать перед началом работы

  - Предполагаемое время для завершения каждой процедуры: 15-60 минут.

  - Для выполнения этих процедур необходимы соответствующие разрешения. Сведения о необходимых разрешениях см. в статье запись "Предотвращение потери данных (DLP)" в разделе [Политика обмена сообщениями и разрешения для соответствия требованиям](messaging-policy-and-compliance-permissions-exchange-2013-help.md).

  - Для любой политики DLP можно выбрать один из трех режимов:
    
      -  
        **Принудительное применение**   Правила в рамках политики оцениваются для всех сообщений и поддерживаемых типов файлов. Поток обработки почты может быть прерван при обнаружении данных, соответствующих условиям политики. Предпринимаются все действия, описанные в рамках политики.
    
      -  
        **Проверка политики DLP с отображением советов по политике**   Правила в рамках политики оцениваются для всех сообщений и поддерживаемых типов файлов. Поток обработки почты не будет прерван при обнаружении данных, соответствующих условиям политики. То есть сообщения не блокируются. Если советы по политике настроены, они отображаются для пользователей.
    
      -  
        **Проверка политики DLP без отображения советов по политике**   Правила в рамках политики оцениваются для всех сообщений и поддерживаемых типов файлов. Поток обработки почты не будет прерван при обнаружении данных, соответствующих условиям политики. То есть сообщения не блокируются. Если советы по политике политики настроены, они не отображаются для пользователей.

  - У отдельного правила внутри политики DLP могут быть собственные параметры режимов. Если режим политики отличается от режима правила внутри этой политики, параметр правила имеет более высокий приоритет и вычисляется в соответствии со своим режимом.

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

## Просмотр сведений о существующей политике DLP

Возможно, понадобится просмотреть правила и действия существующей политики DLP, уже установленной для вашей организации. Это может помочь, если наблюдаются случаи неожиданных потоков почты, или если ваша организация изменила способ контроля конфиденциальных сведений.

## Просмотр сведений в рамках существующей политики DLP с помощью Центра администрирования Exchange (EAC)

1.  В Центре администрирования Exchange откройте раздел **Управление соответствием требованиям** \> **Предотвращение потери данных**.

2.  Дважды щелкните одну из политик в списке политик либо выделите один элемент и нажмите кнопку **Изменить**![Значок редактирования](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Значок редактирования").

3.  На странице **Изменение политики DLP** нажмите кнопку **Правила**.

<table>
<thead>
<tr class="header">
<th><img src="images/Bb124558.tip(EXCHG.150).gif" title="Совет" alt="Совет" />Совет.</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Можно создать политику DLP и оставить ее неактивированной или выключенной. В этом режиме политика не является принудительной. Можно изменять любые предикаты, действия или значения, связанные с ее правилами, перед ее проверкой или перед тем, как сделать политику принудительной.</td>
</tr>
</tbody>
</table>


## Просмотр сведений в рамках существующей политики DLP с помощью командной консоли

В этом примере возвращаются сведения о фиктивной политике DLP с именем Employee Numbers. Команда передается конвейерным образом командлету **Format-List** для отображения подробных сведений о конфигурации указанной политики DLP.

    Get-DlpPolicy "Employee Numbers" | Format-List

Дополнительные сведения о синтаксисе и параметрах см. в разделе [Get-DlpPolicy](https://technet.microsoft.com/ru-ru/library/jj215752\(v=exchg.150\)).

## Изменение политики DLP

Существующую политику DLP можно изменить, изменив либо имя политики, либо правила, определяющие ее эффекты. Пример изменения правила может включать добавление пользовательского текста заявления об отказе в текст сообщения и защиту службы управления правами для сообщений, отправленных в рамках определенного домена, в которых выявлены конфиденциальные сведения. В случае использования шаблонов политик DLP необходимо учитывать, что это — лишь одна из функций службы Exchange 2013, с помощью которой можно конструировать и применять надежную политику и систему соответствия для среды сообщений.

## Изменение существующей политики DLP с помощью Центра администрирования Exchange (EAC)

1.  В Центре администрирования Exchange откройте раздел **Управление соответствием требованиям** \> **Предотвращение потери данных**.

2.  Дважды щелкните одну из политик на основе шаблона в списке политик либо выделите один элемент и нажмите кнопку **Изменить**![Значок редактирования](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Значок редактирования").

3.  На странице **Изменение политики DLP** нажмите кнопку **Правила**.

4.  Чтобы изменить существующее правило, выберите его и нажмите кнопку **Изменить**![Значок редактирования](images/Bb124582.6f53ccb2-1f13-4c02-bea0-30690e6ea71d(EXCHG.150).gif "Значок редактирования").

5.  Чтобы добавить новое пустое правило, которое можно полностью настроить, щелкните пиктограмму **Создать**![Значок добавления](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Значок добавления").

6.  Чтобы добавить правило об уведомлении отправителя, блокировании сообщений или разрешении переопределений, щелкните стрелку рядом с пиктограммой **Создать**![Значок добавления](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Значок добавления").

7.  Чтобы удалить правило, выберите его и нажмите кнопку **Удалить**![Значок удаления](images/Dd979797.14f639f6-61e8-4418-bbfb-0db14de9d2f5(EXCHG.150).gif "Значок удаления").

8.  Нажмите кнопку **Сохранить**, чтобы закончить изменение политики и сохранить изменения.

## Изменение существующей политики DLP с помощью командной консоли

С помощью командной консоли Exchange можно указать действие и уровень уведомления политики. В этом примере настраивается режим для фиктивной политики DLP с именем Employee Numbers таким образом, что действия не являются принудительными, а сообщения уведомления не отображаются.

    Set-DlpPolicy "Employee Numbers" -Mode Audit

Дополнительные сведения о синтаксисе и параметрах см. в разделе [Set-DlpPolicy](https://technet.microsoft.com/ru-ru/library/jj215778\(v=exchg.150\)).

## Удаление политики DLP

Можно удалить политику DLP без возможности восстановления с помощью Центра администрирования Exchange (EAC). После удаления политики она больше не является принудительной, и никакие правила и действия не сохраняются.

Также можно установить для политики операционное состояние или режим **Проверка политики DLP без подсказок политики**. Таким образом политика более не будет принудительной в среде сообщений, но будут сохранены подробные параметры конфигурации самой политики. Это может быть полезным, если существует возможность, что в будущем понадобится опять сделать политику принудительной.

## Удаление существующей политики DLP с помощью Центра администрирования Exchange (EAC)

1.  В Центре администрирования Exchange откройте раздел **Управление соответствием требованиям** \> **Предотвращение потери данных**.

2.  Выберите политику, которую необходимо удалить, в списке политик, а затем нажмите кнопку **Удалить**![Значок удаления](images/Dd979797.14f639f6-61e8-4418-bbfb-0db14de9d2f5(EXCHG.150).gif "Значок удаления").

## Удаление существующей политики DLP с помощью командной консоли

В этом примере удаляется фиктивная политика DLP с именем Employee Numbers.

    Remove-DlpPolicy "Employee Numbers"

Дополнительные сведения о синтаксисе и параметрах см. в разделе [Remove-DlpPolicy](https://technet.microsoft.com/ru-ru/library/jj215677\(v=exchg.150\)).

## Дополнительные сведения

[Защита от потери данных](technical-overview-of-dlp-data-loss-prevention-in-exchange.md)

[Советы политик](technical-overview-of-policy-tips-in-exchange-online-and-exchange-2013.md)
