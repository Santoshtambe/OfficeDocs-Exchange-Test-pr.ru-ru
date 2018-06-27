﻿---
title: 'Определение собственных шаблонов DLP и типов сведений: Exchange 2013 Help'
TOCTitle: Определение собственных шаблонов DLP и типов сведений
ms:assetid: f4622dba-3347-4758-b4a2-f01b043c908c
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/JJ674310(v=EXCHG.150)
ms:contentKeyID: 50489518
ms.date: 04/30/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Определение собственных шаблонов DLP и типов сведений

 

_**Применимо к:**Exchange Online, Exchange Server 2013_

_**Последнее изменение раздела:**2015-01-14_

Вы можете создать шаблоны политики защиты от потери данных (DLP) как XML-файлы независимо от Microsoft Exchange Server 2013, а затем импортировать их с помощью Центра администрирования Exchange или командной консоли Exchange. В этом разделе описан процесс и детали создания и настройки XML-файлов DLP для использования в решении DLP. Разрабатывать свои XML-файлы DLP не нужно, поскольку Центр администрирования Exchange обеспечивает быстрое начало работы для сканирования сообщений благодаря существующим шаблонам политики DLP и правилам транспорта.

Необходимы сведения о задачах управления, связанных с шаблонами политик DLP? См. статью [Процедуры защиты от потери данных](dlp-procedures-exchange-2013-help.md) (Exchange Server 2013) или [Процедуры защиты от потери данных](https://technet.microsoft.com/ru-ru/library/jj938003\(v=exchg.150\)) (Exchange Online).

<table>
<thead>
<tr class="header">
<th><img src="images/JJ126620.note(EXCHG.150).gif" title="Примечание" alt="Примечание" />Примечание.</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>В Exchange 2013 защита от потери данных — дополнительная возможность, для использования которой требуется корпоративная клиентская лицензия (CAL) на Exchange. Дополнительные сведения о клиентских лицензиях и лицензировании серверов см. в статье о <a href="https://go.microsoft.com/fwlink/p/?linkid=237292">лицензировании Exchange Server</a>.<br />
В Exchange Online защита от потери данных — дополнительная возможность, для использования которой требуется подписка на Exchange Online (план 2). Дополнительные сведения см. в статье о <a href="https://go.microsoft.com/fwlink/p/?linkid=286154">лицензировании Exchange Online</a>.</td>
</tr>
</tbody>
</table>


<table>
<thead>
<tr class="header">
<th><img src="images/Dd876857.important(EXCHG.150).gif" title="Важно" alt="Важно" />Важно!</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>В эту документацию не входят рекомендации по поводу бизнес-модели, сведения о пакетах файлов, инструкции по развертыванию правил конфиденциальной информации или обсуждение распространения таких правил. Более того, в этой документации не обсуждаются ни механизмы защиты, например шифрование, для разработанных пользователями правил, ни способ применения этих механизмов.</td>
</tr>
</tbody>
</table>


## Расширение типов сведений для удовлетворения потребностей пользователя

В приведенных ниже разделах описываются понятия и определение схемы XML, которые необходимо понимать, чтобы начать создавать собственные XML-файлы как для шаблонов политики DLP, так и для пакетов правил конфиденциальной информации, которые можно импортировать в Exchange 2013 и использовать как политики DLP.

DLP в Microsoft Exchange позволяет применить к конфиденциальной информации политику конкретной организации. Ключевой фактор силы решения DLP — это способность правильно определить уникальную для организации конфиденциальную или частную информацию, потребности регулирования, географию или другие аспекты бизнеса. Хотя Майкрософт в рамках продукта предоставляет шаблоны политики и типы конфиденциальной информации для начала работы, учитывая уникальные требования бизнеса, вам может понадобиться настраиваемое решение предотвращения утечки данных. В связи с этим корпорация Майкрософт предлагает способ создания и импорта ваших шаблонов политики DLP или определений конфиденциальной информации в пакетах правил классификации. Точное решение DLP зависит от настройки правильного набора правил для подсистемы обнаружения конфиденциальной информации, которая обеспечивает высокий уровень защиты, сводя к минимуму ложные срабатывания и отрицательные результаты.

## Разработка собственных шаблонов политики DLP

Вы можете написать собственный XML-файл шаблона политики DLP и импортировать его. Такой подход к расширению решения DLP, предоставленный в Exchange, позволит построить политики DLP в соответствии с вашими требованиями.

Процесс управления настраиваемыми шаблонами и связанными политиками аналогичен управлению политиками DLP, создаваемыми на основе шаблонов Майкрософт. В течение типичного жизненного цикла политики DLP вы выполняете следующие действия.

1.  Создаете собственный шаблон политики DLP, настраиваемый XML-файл. Дополнительные сведения см. в статье [Разработка файлов шаблонов политики DLP](xml-rule-schema-and-rule-structure-guide-for-dlp-policy-files.md).

2.  Импортируете настраиваемый шаблон. Дополнительные сведения см. в статье [Импорт настраиваемого шаблона политики защиты от потери данных из файла](import-a-custom-dlp-policy-template-from-a-file-exchange-2013-help.md).

3.  Создаете политику DLP на основе настраиваемого шаблона. Дополнительные сведения см. в статье [Создание политики защиты от потери данных на основе шаблона](how-to-new-dlp-data-loss-prevention-policy-template.md).

4.  Обновите настраиваемый шаблон, повторяя действия 1 и 2.

5.  Удалите настраиваемый шаблон. Дополнительные сведения см. в статье [Remove-DlpPolicyTemplate](https://technet.microsoft.com/ru-ru/library/jj215739\(v=exchg.150\)).

Дополнительные сведения об определении и понятиях схемы XML, связанных с разработкой собственных шаблонов, см. в статье [Разработка файлов шаблонов политики DLP](xml-rule-schema-and-rule-structure-guide-for-dlp-policy-files.md).

## Разработка собственных типов конфиденциальной информации и соответствующей логики в пакетах правил классификации

Свои определения конфиденциальной информации можно писать в пакете правил классификации, который является XML-файлом, и импортировать его как часть решения DLP. Подсистема обнаружения конфиденциальной информации предоставляет возможности глубокого анализа содержимого для определения частной информации, например номеров кредитных карт, номеров социального страхования и интеллектуальной собственности компании. Подсистема контролируется настраиваемым набором инструкций или правил для сканирования и анализа содержимого. Правила объединяются в пакет правил классификации, XML-документ, соответствующий определению схемы XML пакета стандартизированных правил. Вот, как можно создать собственный шаблон.

1.  Создаете собственные типы конфиденциальных сведений в виде настраиваемого XML-файла. Дополнительные сведения см. в статье [Разработка пакетов правил конфиденциальной информации](technical-description-of-xml-schema-for-dlp-rule-packages.md).

2.  Импортируйте тип конфиденциальных сведений. Дополнительные сведения см. в статье [New-ClassificationRuleCollection](https://technet.microsoft.com/ru-ru/library/jj218619\(v=exchg.150\)).

3.  Создайте настраиваемый шаблон на основе типов информации. Дополнительные сведения см. в статье [Разработка пакетов правил конфиденциальной информации](technical-description-of-xml-schema-for-dlp-rule-packages.md).

4.  Обновите настраиваемый шаблон, повторяя действия 1 и 2.

5.  Удалите настраиваемый шаблон. Дополнительные сведения см. в статье [Remove-ClassificationRuleCollection](https://technet.microsoft.com/ru-ru/library/jj218670\(v=exchg.150\)).

Дополнительные сведения о пакетах правил см. в статьях [Разработка пакетов правил конфиденциальной информации](technical-description-of-xml-schema-for-dlp-rule-packages.md) и [Соответствующие методы и приемы для пакетов правил](technical-description-of-xsd-rule-matching-for-dlp-rule-packages.md).

## Общие сведения о типах правил в пакетах правил

Правила в пакете правил настраивают процесс обнаружения четко описанных характеристик содержимого, например правила поиска номера водительского удостоверения. Доступны два типа главного правила: Сущность и сходство.

Правила *сущности* нацелены на четко описанные (и часто регулируемые) идентификаторы, например номера социального страхования США. Сущность представлена коллекцией исчисляемых шаблонов. Шаблон определяет коллекцию соответствий явному первичному идентификатору соответствий. Пример сущности — это водительские права.

Правила *сходства* нацелены на определенный тип документа, например корпоративный финансовый отчет. Сходство представлено как коллекция независимых свидетельств. Свидетельством является совокупность необходимых соответствий в пределах определенной близости. Пример сходства — это закон Сарбэйнса-Оксли США.

## Дополнительные сведения

[Защита от потери данных](technical-overview-of-dlp-data-loss-prevention-in-exchange.md)

[Импорт настраиваемого шаблона политики защиты от потери данных из файла](import-a-custom-dlp-policy-template-from-a-file-exchange-2013-help.md)

[New-ClassificationRuleCollection](https://technet.microsoft.com/ru-ru/library/jj218619\(v=exchg.150\))

[Правила обработки почтового потока и транспорта](mail-flow-rules-transport-rules-in-exchange-2013-exchange-2013-help.md)Exchange Server 2013

[Правила потока обработки почты (правила транспорта) в Exchange Online](https://technet.microsoft.com/ru-ru/library/jj919238\(v=exchg.150\))Exchange Online

[Что позволяют искать типы конфиденциальной информации в Exchange](what-the-sensitive-information-types-in-exchange-look-for-exchange-online-help.md)
