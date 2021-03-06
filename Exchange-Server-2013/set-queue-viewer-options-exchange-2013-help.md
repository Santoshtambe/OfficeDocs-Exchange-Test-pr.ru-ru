﻿---
title: 'Настройка параметров средства просмотра очереди: Exchange 2013 Help'
TOCTitle: Настройка параметров средства просмотра очереди
ms:assetid: 03a9134c-0714-4c13-b286-92bccc7ec05e
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Aa995934(v=EXCHG.150)
ms:contentKeyID: 50487364
ms.date: 04/30/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Настройка параметров средства просмотра очереди

 

_**Применимо к:**Exchange Server 2013_

_**Последнее изменение раздела:**2012-10-03_

С помощью этих параметров можно задать количество элементов, отображаемых на странице, и интервал автообновления в средстве просмотра очереди. Интервал автообновления определяет частоту обновления результатов в средстве просмотра очереди.

## Что нужно знать перед началом работы?

  - Осталось времени до завершения: 10 минут

  - Для выполнения этих процедур необходимы соответствующие разрешения. Сведения о необходимых разрешениях см. в статье Запись "Очереди" в разделе [Разрешения потока обработки почты](mail-flow-permissions-exchange-2013-help.md).

  - Сочетания клавиш для процедур, описанных в этой статье, приведены в статье [Сочетания клавиш в Центре администрирования Exchange](keyboard-shortcuts-in-the-exchange-admin-center-exchange-online-protection-help.md).

<table>
<thead>
<tr class="header">
<th><img src="images/JJ983803.warning(EXCHG.150).gif" title="Предупреждение" alt="Предупреждение" />Предупреждение.</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Возникли проблемы? Обратитесь за помощью к участникам форумов, посвященных Exchange. Посетите форумы по таким продуктам: <a href="https://go.microsoft.com/fwlink/p/?linkid=60612">Exchange Server</a>, <a href="https://go.microsoft.com/fwlink/p/?linkid=267542">Exchange Online</a> или <a href="https://go.microsoft.com/fwlink/p/?linkid=285351">Exchange Online Protection</a>.</td>
</tr>
</tbody>
</table>


## Использование инструментов Exchange для настройки параметров средства просмотра очереди

1.  Нажмите кнопку **Пуск** и последовательно выберите пункты **Все программы** \> **Microsoft Exchange Server 2013** \> **Панель элементов Exchange**.

2.  В разделе **Средства для потока почты** дважды щелкните элемент **Средство просмотра очереди**.

3.  В средстве просмотра очереди выберите **Представление** \> **Параметры**, чтобы настроить следующие параметры в диалоговом окне **Параметры средства просмотра очереди**:
    
    1.  В поле **Интервал обновления (секунды)** введите частоту, с которой средство просмотра очередей должно обновлять экран монитора.
        
        <table>
        <thead>
        <tr class="header">
        <th><img src="images/JJ126620.note(EXCHG.150).gif" title="Примечание" alt="Примечание" />Примечание.</th>
        </tr>
        </thead>
        <tbody>
        <tr class="odd">
        <td>По умолчанию применяется минимальный интервал автообновления 30 секунд. Если отключить функцию автообновления, сняв флажок <strong>Автоматически обновлять экран</strong> на странице <strong>Настройки средства просмотра очереди</strong>, то придется вручную обновлять результаты, отображаемые в средстве просмотра очереди, нажатием кнопки <strong>Обновить</strong>.</td>
        </tr>
        </tbody>
        </table>
    
    2.  В поле **Число элементов, отображаемых на каждой странице** введите максимальное число элементов, которое должно отображаться в средстве просмотра очереди. Таким числом может быть любое значение от 1 до 10 000. Если количество элементов превышает установленное значение, то элементы отображаются группами с максимальным числом элементов. Например, на следующем рисунке показана очередь из 14 сообщений, при этом средство просмотра очереди имеет настройку отображения 10 элементов на каждой странице. Количество объектов на странице отображается в правом верхнем углу. В нижней части страницы отображается общее количество элементов в очереди. Перемещаясь с помощью элементов управления, можно просмотреть дополнительные элементы в очереди.

4.  По завершении нажмите кнопку **ОК**.
    
    **Средство просмотра очереди**
    
    ![Средство просмотра очереди с количеством элементов, превышающим допустимое значение](images/Aa995934.e82196e6-002a-4e9e-823d-b244b0bd25e2(EXCHG.150).gif "Средство просмотра очереди с количеством элементов, превышающим допустимое значение")  

## Как проверить, что все получилось?

Если средство просмотра очереди использует параметры интервала обновления и числа элементов на странице, значит, все сработало.

