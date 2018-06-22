﻿---
title: 'Предварительные условия для гибридного развертывания: Exchange 2013 Help'
TOCTitle: Предварительные условия для гибридного развертывания
ms:assetid: e7454db0-fed4-4662-8890-9501126b1ba2
ms:mtpsurl: https://technet.microsoft.com/ru-ru/library/Hh534377(v=EXCHG.150)
ms:contentKeyID: 50489601
ms.date: 02/22/2018
mtps_version: v=EXCHG.150
ms.translationtype: HT
---

# Предварительные условия для гибридного развертывания

 

_<strong>Применимо к:</strong>Exchange Online, Exchange Server 2013, Exchange Server 2016_

_<strong>Последнее изменение раздела:</strong>2017-07-25_

**Сводка**. Что необходимо среде Exchange для настройки гибридного развертывания.

Перед созданием и настройкой гибридного развертывания с помощью мастера гибридной конфигурации необходимо, чтобы ваша существующая локальная организация Exchange соответствовала определенным требованиям. В противном случае вы не сможете выполнить шаги в мастере гибридной конфигурации и настроить гибридное развертывание между локальной организацией Exchange и организацией Exchange Online.

## Необходимые условия для гибридного развертывания

Ниже приведены необходимые условия для настройки гибридного развертывания:

  - **Локальная организация Exchange**. Гибридные развертывания можно настроить для локальной организации на базе Exchange 2007 или более поздней версии.
    
    Версия Exchange, установленная в локальной организации, определяет версию, доступную для установки при гибридном развертывании. Как правило, необходимо настроить самую новую версию для гибридного развертывания, поддерживаемую в вашей организации. Например, если в локальной организации есть Exchange 2007, необходимо настроить гибридное развертывание с использованием Exchange 2013. Полные сведения о совместимости Exchange Server и Office 365 для предприятий в случае гибридного развертывания можно найти в приведенной ниже таблице.
    
    
    <table>
    <colgroup>
    <col style="width: 25%" />
    <col style="width: 25%" />
    <col style="width: 25%" />
    <col style="width: 25%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th>Локальная среда</th>
    <th>гибридное развертывание на основе Exchange 2016</th>
    <th>гибридное развертывание на основе Exchange 2013</th>
    <th>гибридное развертывание на основе Exchange 2010</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><p>Exchange 2016</p></td>
    <td><p>Поддерживается</p></td>
    <td><p>Не поддерживается</p></td>
    <td><p>Не поддерживается</p></td>
    </tr>
    <tr class="even">
    <td><p>Exchange 2013</p></td>
    <td><p>Поддерживается</p></td>
    <td><p>Поддерживается</p></td>
    <td><p>Не поддерживается</p></td>
    </tr>
    <tr class="odd">
    <td><p>Exchange 2010</p></td>
    <td><p>Поддерживается</p></td>
    <td><p>Поддерживается</p></td>
    <td><p>Поддерживается</p></td>
    </tr>
    <tr class="even">
    <td><p>Exchange 2007</p></td>
    <td><p>Не поддерживается</p></td>
    <td><p>Поддерживается</p></td>
    <td><p>Поддерживается</p></td>
    </tr>
    </tbody>
    </table>


  - **Локальные выпуски Exchange**. Для гибридных развертываний требуется установка последнего накопительного пакета обновления для версии Exchange, установленной в вашей локальной организации. Если вы не можете установить последний накопительный пакет обновления, выпуск, предшествующий последнему, также поддерживается. Более ранние накопительные пакеты обновления не поддерживаются.
    
    Например, предположим, что вы установили Exchange 2013 с накопительным пакет обновления 8 в вашей локальной организации, а самый новый доступный выпуск — Exchange 2013 с накопительным пакетом обновления 10. Чтобы оставаться в пределах поддерживаемой гибридной конфигурации, вам необходимо обновить серверы Exchange 2013 по крайней мере до накопительного пакета обновления 9. Тем не менее мы настоятельно рекомендуем обновиться до накопительного пакета обновления 10.
    
    Накопительные пакеты обновления выходят с периодичностью раз в квартал, поэтому обновление серверов до последнего накопительного пакета обновления можно проводить с достаточной гибкостью, если вам периодически требуется дополнительное время, чтобы завершить обновления.

  - **Роли локального сервера** Роли сервера, которые вам необходимо установить в локальной организации, зависят от установленной версии Exchange.
    
      - **Exchange 2010** По крайней мере один сервер с установленными ролями почтового сервера, транспортного сервера-концентратора и сервера клиентского доступа. Несмотря на то что роли почтового сервера, транспортного сервера-концентратора и сервера клиентского доступа можно установить на различных серверах, мы настоятельно рекомендуем устанавливать все роли на каждом сервере для большей надежности и повышенной производительности.
    
      - **Exchange 2013** По крайней мере один сервер с установленными ролями почтового сервера и сервера клиентского доступа. Несмотря на то что роли почтового сервера и сервера клиентского доступа можно установить на различных серверах, мы настоятельно рекомендуем устанавливать обе роли на каждом сервере для большей надежности и повышенной производительности.
    
      - **Exchange 2016 и более новые версии**. По меньшей мере один сервер с установленной ролью почтового сервера.
    
    Гибридное развертывание также поддерживает серверы Exchange с активной ролью пограничного транспортного сервера. Пограничные транспортные серверы также необходимо обновить до последнего накопительного пакета обновления, доступного для установленной версии Exchange. Мы настоятельно рекомендуем развертывать пограничные транспортные серверы в сети периметра. Почтовые серверы и серверы клиентского доступа невозможно развертывать в сети периметра.

  - **Office 365**. Гибридное развертывание поддерживается во всех планах Office 365 с поддержкой Синхронизация Azure Active Directory. Все планы Office 365 корпоративный, Office 365 для государственных организаций, Office 365 для образовательных учреждений и Office 365 для среднего бизнеса поддерживают гибридные развертывания. Планы Office 365 бизнес и Office 365 для дома не поддерживают гибридные развертывания.
    
    Дополнительные сведения см. в статье [Регистрация в Office 365](https://go.microsoft.com/fwlink/p/?linkid=203981).

  - **Личные домены**   Зарегистрируйте любой личный домен, который необходимо использовать при гибридном развертывании Office 365. Это можно сделать на портале администрирования Office 365, а также с помощью дополнительной настройки служб федерации Active Directory (AD FS) в локальной организации.
    
    Дополнительные сведения см. в статье [Добавление домена в Office 365](https://go.microsoft.com/fwlink/p/?linkid=229238).

  - **Синхронизация Active Directory**. Разверните средство Azure Active Directory Connect, чтобы обеспечить синхронизацию Active Directory с локальной организацией.
    
    Дополнительные сведения см. в статье [Параметры входа в Azure AD Connect](http://go.microsoft.com/fwlink/p/?linkid=723514).

  - **Автообнаружение DNS-записей**   Настройте автообнаружение общедоступных DNS-записей для существующих доменов SMTP, чтобы они указывали на локальный сервер клиентского доступа Exchange 2013.

  - **Организация Office 365 в Центре администрирования Exchange**. Узел организации Office 365 по умолчанию включен в локальный Центр администрирования Exchange. Но прежде чем вы сможете использовать мастер гибридной конфигурации, Центр администрирования Exchange необходимо подключить к организации Office 365, используя учетные данные администратора Office 365. Это позволит вам управлять как локальными организациями, так и организациями Exchange Online с помощью одной консоли управления.
    
    Дополнительные сведения см. в статье [Управление в гибридных средах Exchange](hybrid-management-in-exchange-hybrid-deployments-exchange-2013-help.md).

  - 
    
    **Сертификаты**. Установите службы Exchange и назначьте для них допустимый цифровой сертификат, приобретенный в доверенном общедоступном центре сертификации (CA). Хотя самозаверяющие сертификаты нужно использовать для локального доверия федерации с Microsoft Federation Gateway, их невозможно применять для служб Exchange при гибридном развертывании. Для экземпляра служб IIS на серверах Exchange Server, настроенных при гибридном развертывании, должен быть допустимый цифровой сертификат от доверенного центра сертификации (CA). Кроме того, внешний URL-адрес веб-служб Exchange и конечная точка автообнаружения, указанная в общедоступной DNS, должны быть указаны в альтернативном имени субъекта (SAN) сертификата. В случае сертификатов, установленных на серверах Exchange Server, которые настроены для почтового транспорта в гибридной среде, должен применяться один и тот же сертификат (т. е. они выдаются одним и тем же центром сертификации, у них один субъект).
    
    Дополнительные сведения см. в разделе [Требования к сертификатам для гибридных развертываний](certificate-requirements-for-hybrid-deployments-exchange-2013-help.md).

  - **EdgeSync**. Если в локальной организации развернуты пограничные транспортные серверы и нужно настроить их для безопасного почтового транспорта в гибридной среде, перед использованием мастера гибридной конфигурации необходимо настроить EdgeSync. Кроме того, EdgeSync необходимо запускать при каждом применении нового накопительного пакета обновления к пограничному транспортному серверу.
    
    > [!IMPORTANT]
    > Хотя EdgeSync является необходимым условием в развертываниях с пограничными транспортными серверами, понадобится дополнительная ручная настройка конфигурации транспорта при настройке пограничных транспортных серверов для гибридной безопасной транспортировки почты.
    
    Дополнительные сведения см. в статье [Пограничные транспортные серверы в гибридных развертываниях](edge-transport-servers-with-hybrid-deployments-exchange-2013-help.md).

  - **Почтовые ящики, поддерживающие единую систему обмена сообщениями (UM)**. Если у вас есть почтовые ящики, поддерживающие единую систему обмена сообщениями, и вы хотите перенести их в Office 365, помимо гибридного развертывания Exchange, нужно будет выполнить указанные ниже действия. Ниже приведены требования **для** переноса почтовых ящиков, поддерживающих единую систему обмена сообщениями, в Office 365.
    
      - Lync Server 2010, Lync Server 2013 или Skype для бизнеса Server 2015 или более поздней версии, интегрированный с локальной системой телефонии **или**
    
      - Skype для бизнеса Online, интегрированный с локальной системой телефонии **или**
    
      - Обычная локальная УАТС или IP-УАТС.
    
      - Названия политик почтовых ящиков UM в Exchange Online и в локальной организации должны совпадать.
        
        > [!NOTE]  
		> С одной политикой почтовых ящиков UM в Exchange Online можно сопоставить несколько локальных политик почтовых ящиков UM. Для этого необходимо использовать командную консоль Exchange, чтобы вручную сопоставить локальные политики почтовых ящиков UM с политиками Exchange Online.
        
    
    Дополнительные сведения см. в статьях [Интеграция телефонной системы с единой системой обмена сообщениями](https://technet.microsoft.com/ru-ru/library/jj673558\(v=exchg.150\)), [Рекомендации по телефонии в Exchange 2013](https://technet.microsoft.com/ru-ru/library/ee364753\(v=exchg.150\)) и [Настройка голосовой почты облачной УАТС](https://go.microsoft.com/fwlink/p/?linkid=826207).

## Протоколы, порты и конечные точки гибридного развертывания

Для корректной работы функций и компонентов гибридного развертывания определенные протоколы входящей почты, порты и конечные точки подключения должны быть доступны в Office 365. Перед настройкой гибридного развертывания убедитесь, что локальная сеть и конфигурация безопасности поддерживают функции и компоненты, указанные в приведенной ниже таблице. Кроме протоколов входящих сообщений, портов и конечных точек, компьютерам в сети также должны быть доступны IP-адреса, порты и URL-адреса, указанные в статье [URL-адреса и диапазоны IP-адресов Office 365](https://go.microsoft.com/fwlink/?linkid=823100).


<table>
<colgroup>
<col style="width: 12%" />
<col style="width: 12%" />
<col style="width: 12%" />
<col style="width: 12%" />
<col style="width: 12%" />
<col style="width: 12%" />
<col style="width: 12%" />
<col style="width: 12%" />
</colgroup>
<thead>
<tr class="header">
<th>Транспортный протокол</th>
<th>Протокол более высокого уровня</th>
<th>Возможность или компонент</th>
<th>Локальная конечная точка</th>
<th>Локальный путь</th>
<th>Поставщик проверки подлинности</th>
<th>Метод авторизации</th>
<th>Поддерживается предварительная проверка подлинности?</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>TCP 25 (SMTP)</p></td>
<td><p>SMTP/TLS</p></td>
<td><p>Поток почты между Office 365 и локальной средой</p></td>
<td><p>Почтовый или пограничный сервер Exchange 2016</p>
<p>Сервер клиентского доступа или пограничный сервер Exchange 2013</p>
<p>Сервер-концентратор или пограничный сервер Exchange 2010</p></td>
<td><p>Недоступно</p></td>
<td><p>Недоступно</p></td>
<td><p>На основе сертификатов</p></td>
<td><p>Нет</p></td>
</tr>
<tr class="even">
<td><p>TCP 443 (HTTPS)</p></td>
<td><p>Автообнаружение</p></td>
<td><p>Автообнаружение</p></td>
<td><p>Почтовый сервер Exchange 2016</p>
<p>Сервер клиентского доступа Exchange 2013/2010</p></td>
<td><p>/autodiscover/autodiscover.svc/wssecurity</p>
<p>/autodiscover/autodiscover.svc</p></td>
<td><p>Система проверки подлинности Azure AD</p></td>
<td><p>Проверка подлинности WS-Security</p></td>
<td><p>Нет</p></td>
</tr>
<tr class="odd">
<td><p>TCP 443 (HTTPS)</p></td>
<td><p>EWS</p></td>
<td><p>Сведения о занятости, подсказки, отслеживание сообщений</p></td>
<td><p>Почтовый сервер Exchange 2016</p>
<p>Сервер клиентского доступа Exchange 2013/2010</p></td>
<td><p>/ews/exchange.asmx/wssecurity</p></td>
<td><p>Система проверки подлинности Azure AD</p></td>
<td><p>Проверка подлинности WS-Security</p></td>
<td><p>Нет</p></td>
</tr>
<tr class="even">
<td><p>TCP 443 (HTTPS)</p></td>
<td><p>EWS</p></td>
<td><p>Поиск по нескольким почтовым ящикам</p></td>
<td><p>Почтовый сервер Exchange 2016</p>
<p>Сервер клиентского доступа Exchange 2013/2010</p></td>
<td><p>/ews/exchange.asmx/wssecurity</p>
<p>/autodiscover/autodiscover.svc/wssecurity</p>
<p>/autodiscover/autodiscover.svc</p></td>
<td><p>Сервер проверки подлинности</p></td>
<td><p>Проверка подлинности WS-Security</p></td>
<td><p>Нет</p></td>
</tr>
<tr class="odd">
<td><p>TCP 443 (HTTPS)</p></td>
<td><p>EWS</p></td>
<td><p>Перенос почтовых ящиков</p></td>
<td><p>Почтовый сервер Exchange 2016</p>
<p>Сервер клиентского доступа Exchange 2013/2010</p></td>
<td><p>/ews/mrsproxy.svc</p></td>
<td><p>NTLM</p></td>
<td><p>Базовый</p></td>
<td><p>Да</p></td>
</tr>
<tr class="even">
<td><p>TCP 443 (HTTPS)</p></td>
<td><p>Автообнаружение</p>
<p>EWS</p></td>
<td><p>OAuth</p></td>
<td><p>Почтовый сервер Exchange 2016</p>
<p>Сервер клиентского доступа Exchange 2013/2010</p></td>
<td><p>/ews/exchange.asmx/wssecurity</p>
<p>/autodiscover/autodiscover.svc/wssecurity</p>
<p>/autodiscover/autodiscover.svc</p></td>
<td><p>Сервер проверки подлинности</p></td>
<td><p>Проверка подлинности WS-Security</p></td>
<td><p>Нет</p></td>
</tr>
<tr class="odd">
<td><p>TCP 443 (HTTPS)</p></td>
<td><p>Недоступно</p></td>
<td><p>AD FS (входит в состав Windows)</p></td>
<td><p>Windows 2008/2012 Server</p></td>
<td><p>/adfs/*</p></td>
<td><p>Система проверки подлинности Azure AD</p></td>
<td><p>Зависит от конфигурации.</p></td>
<td><p>Двухфакторная</p></td>
</tr>
<tr class="even">
<td><p>TCP 443 (HTTPS)</p></td>
<td><p>Недоступно</p></td>
<td><p>Azure Active Directory Connect с AD FS</p></td>
<td><p>Windows 2012 R2 Server</p></td>
<td><p>/adfs/*</p></td>
<td><p>Система проверки подлинности Azure AD</p></td>
<td><p>Зависит от конфигурации.</p></td>
<td><p>Двухфакторная</p></td>
</tr>
</tbody>
</table>


## Рекомендуемые средства и службы

Кроме описанных ранее необходимых условий, при настройке гибридных развертываний с помощью мастера гибридной конфигурации удобно использовать другие средства и службы:

  - **Помощник по развертыванию Exchange Server**. Это бесплатное веб-средство помогает развернуть Exchange в локальной организации, настроить гибридное развертывание между локальной организацией и Office 365 или выполнить полную миграцию в Office 365. Средство предлагает ответить на несколько вопросов и затем, в зависимости от ваших ответов, создает специальный контрольный список с инструкциями для развертывания или настройки Exchange Server. Помощник по развертыванию предоставляет именно те сведения, которые вам необходимы для настройки гибридного развертывания.
    
    Дополнительные сведения см. в статье [Помощник по развертыванию Exchange Server](https://technet.microsoft.com/exdeploy2013).
    
     

  - **Анализатор удаленных подключений**   Средство анализатора удаленных подключений (Майкрософт) проверяет внешнее подключение локальной организации Exchange и подтверждает готовность к настройке гибридного развертывания. Перед настройкой гибридного развертывания с помощью мастера гибридной конфигурации мы настоятельно рекомендуем вам проверить свою локальную организацию с помощью анализатора удаленных подключений.
    
    Дополнительные сведения см. на странице [анализатора удаленного подключения (Майкрософт)](https://testconnectivity.microsoft.com/).
    
     

  - **Единый вход**. Единый вход позволяет пользователям с помощью одного имени пользователя и пароля получать доступ как к локальной организации, так и к организации Exchange Online. Эта функция пользователям дает возможность применять знакомый способ входа, а администраторам — с легкостью управлять политиками учетных записей для почтовых ящиков из организации Exchange Online с помощью средств управления в локальной среде Active Directory.
    
    При развертывании единого входа у вас есть несколько вариантов: синхронизация паролей и службы федерации Active Directory. Оба варианта обеспечивает Azure Active Directory Connect. Синхронизация паролей позволяет легко реализовать единый вход практически для любой организации независимо от ее размера. По этой причине, а также потому что работа пользователей в гибридной среде значительно эффективнее при включенной функции единого входа, мы настоятельно рекомендуем реализовать ее. Службы федерации Active Directory требуются для очень крупных организаций, например организаций с несколькими лесами Active Directory, которые необходимо присоединить к гибридной среде.
    
    Дополнительные сведения об этом читайте в статье [Единый вход в гибридных развертываниях](single-sign-on-with-hybrid-deployments-exchange-2013-help.md).
