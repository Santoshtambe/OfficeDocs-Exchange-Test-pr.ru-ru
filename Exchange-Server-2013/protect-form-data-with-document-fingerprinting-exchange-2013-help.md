﻿---
title: 'Защита данных форм с помощью отпечатков документов: Exchange 2013 Help'
TOCTitle: Защита данных форм с помощью отпечатков документов
ms:assetid: 110c839b-7693-42f6-aa5d-58ce64f4c357
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Dn635175(v=EXCHG.150)
ms:contentKeyID: 61203522
ms.date: 04/30/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Защита данных форм с помощью отпечатков документов

 

_**Применимо к:**Exchange Online, Exchange Server 2013_

_**Последнее изменение раздела:**2014-09-11_

Если ваша организация собирает конфиденциальные сведения с помощью форм, пользователи могут пытаться отправлять эти формы по электронной почте внешним контактам, создавая тем самым риск безопасности. Функция защиты от потери данных в Exchange позволяет защитить такие сведения путем их обнаружения с помощью [Отпечатки документов](overview-of-document-fingerprinting-in-exchange.md). Чтобы использовать отпечатки документов, просто отправьте пустую форму, например документ, в котором изложены права на интеллектуальную собственность, правительственную или другую стандартную форму, которая используется в вашей организации. Затем добавьте полученный отпечаток документа в политику защиты от потери данных или правило транспорта. Ниже приведено описание процедуры.

> [!VIDEO https://www.microsoft.com/ru-ru/videoplayer/embed/576c1b06-d34f-4f34-b031-20374a77316f]

## Создание отпечатка документа с помощью Центра администрирования Exchange

![Выделенный путь к созданию отпечатка документа в Центре администрирования Exchange](images/Dn635175.e8562ea7-40ba-4feb-adde-2e81f029fcda(EXCHG.150).png "Выделенный путь к созданию отпечатка документа в Центре администрирования Exchange")

1.  В Центре администрирования Exchange перейдите в раздел **Управление соответствием требованиям** \> **Защита от потери данных**.

2.  Щелкните **Управление отпечатками документов**.

3.  На странице отпечатков документов нажмите кнопку **Создать**![Значок добавления](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Значок добавления"), чтобы создать отпечаток документа.

4.  Присвойте ему **Имя** и **Описание**. (Выбранное имя отобразится в списке типов конфиденциальных сведений.)

5.  Чтобы отправить форму, нажмите кнопку **Добавить**![Значок добавления](images/JJ218640.c1e75329-d6d7-4073-a27d-498590bbb558(EXCHG.150).gif "Значок добавления").

6.  Выберите форму и нажмите кнопку **Открыть**. (Убедитесь, что отправляемый файл содержит текст, не защищен паролем и имеет один из типов файлов, поддерживаемых в правилах транспорта. Список поддерживаемых типов файлов см. в статье [Проверка вложений с помощью правил обработки почтового потока](https://technet.microsoft.com/ru-ru/library/jj919236\(v=exchg.150\)). В противном случае при создании отпечатка отобразится ошибка.) Повторите эту процедуру для всех дополнительных файлов, которые необходимо добавить в список документов для данного отпечатка документа. При желании вы также можете добавить или удалить файлы из этого отпечатка документа.

7.  Нажмите кнопку **Сохранить**.

Теперь отпечаток документа входит в ваш список типов конфиденциальных сведений, и вы можете добавить его в политику защиты от потери данных или правило транспорта с помощью условия **Если сообщение содержит...конфиденциальную информацию**.

![Выделенное условие "Применить это правило, если..."](images/Dn635175.9355a513-a790-48eb-a61b-575ba2ecdfa6(EXCHG.150).png "Выделенное условие \"Применить это правило, если...\"")

Дополнительные сведения о добавлении правил в политику защиты от потери данных см. в пункте "Изменение политики защиты от потери данных" раздела [Управление политиками защиты от потери данных](manage-dlp-policies-exchange-2013-help.md). Дополнительные сведения об изменении правил транспорта см. в статье [Интеграция правил конфиденциальной информации с правилами транспорта](integrating-sensitive-information-rules-with-transport-rules-exchange-2013-help.md). Сведения о создании новой политики см. в статье [Создание политики защиты от потери данных на основе шаблона](how-to-new-dlp-data-loss-prevention-policy-template.md).

## Создание пакета правил классификации на основе отпечатков документов с помощью командной консоли

<table>
<thead>
<tr class="header">
<th><img src="images/Bb124558.tip(EXCHG.150).gif" title="Совет" alt="Совет" />Совет.</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Хотя вы можете создавать и изменять пакеты правил классификации в командной консоли, создавать отпечатки документов в Центре администрирования Exchange немного проще. Эту процедуру рекомендуется сначала выполнить в Центре администрирования Exchange, а затем — в командной консоли.</td>
</tr>
</tbody>
</table>


Функция защиты от потери данных использует пакеты правил классификации для обнаружения конфиденциального содержимого в сообщениях. Чтобы создать пакет правил классификации на основе отпечатка документа, используйте командлеты **New-Fingerprint** и **New-DataClassification**. Поскольку результаты выполнения командлета **New-Fingerprint** не хранятся за пределами правила классификации данных, командлеты **New-Fingerprint** и **New-DataClassification** или **Set-DataClassification** всегда выполняются во время одного сеанса PowerShell. В примере ниже создается новый отпечаток документа на основе файла C:\\My Documents\\Contoso Employee Template.docx. Новый отпечаток хранится в качестве переменной, поэтому его можно использовать с командлетом **New-DataClassification** во время одного сеанса PowerShell.

    $Employee_Template = Get-Content "C:\My Documents\Contoso Employee Template.docx" -Encoding byte
    $Employee_Fingerprint = New-Fingerprint -FileData $Employee_Template -Description "Contoso Employee Template"

Давайте создадим новое правило классификации данных с именем "Contoso Employee Confidential", использующее отпечаток документа из файла C:\\My Documents\\Contoso Customer Information Form.docx.

    $Employee_Template = Get-Content "C:\My Documents\Contoso Customer Information Form.docx" -Encoding byte
    $Customer_Fingerprint = New-Fingerprint -FileData $Customer_Form -Description "Contoso Customer Information Form"
    New-DataClassification -Name "Contoso Customer Confidential" -Fingerprints $Customer_Fingerprint -Description "Message contains Contoso customer information." 

Вы можете использовать командлет **Get-DataClassification** для поиска всех пакетов правил классификации данных, используемых функцией защиты от потери данных, а в этом примере в список пакетов правил классификации данных входит пакет "Contoso Customer Confidential".

Наконец, добавьте пакет правил классификации данных "Contoso Customer Confidential" в политику защиты от потери данных.

    New-TransportRule -Name "Notify :External Recipient Contoso confidential" -NotifySender NotifyOnly -Mode Enforce -SentToScope NotInOrganization -MessageContainsDataClassification @{Name=" Contoso Customer Confidential"}

На данном этапе агент защиты от потери данных будет обнаруживать документы, соответствующие отпечатку документа Contoso Customer Form.docx.

Сведения о синтаксисе и параметрах см. в разделах [New-Fingerprint](https://technet.microsoft.com/ru-ru/library/dn584142\(v=exchg.150\)), [New-DataClassification](https://technet.microsoft.com/ru-ru/library/dn584139\(v=exchg.150\)), [Set-DataClassification](https://technet.microsoft.com/ru-ru/library/dn584141\(v=exchg.150\)) и [Get-DataClassification](https://technet.microsoft.com/ru-ru/library/jj215720\(v=exchg.150\)).

## Дополнительные сведения

[Отпечатки документов](overview-of-document-fingerprinting-in-exchange.md)

[Управление политиками защиты от потери данных](manage-dlp-policies-exchange-2013-help.md)

[Интеграция правил конфиденциальной информации с правилами транспорта](integrating-sensitive-information-rules-with-transport-rules-exchange-2013-help.md)

