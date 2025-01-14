---
title: "Настройки низкого уровня"
taxonomy:
  category:
    - docs
visible: true
---

В разделе "Расширенные настройки" в меню AdGuard для Android есть пункт "Настройки низкого уровня". Если выбрать его, вы увидите длинный список различных настроек, назначение многих из которых может быть непонятным для рядового пользователя.

**ВНИМАНИЕ!** Изменение любых из этих настроек без понимания того, что делает та или иная настройка, может привести к нежелательным последствиям! Обратитесь за помощью к нашей службе поддержки, если вы сомневаетесь по поводу какой-либо настройки.

Ниже мы постараемся описать, для чего нужны некоторые из самых важных и наиболее часто используемых настроек низкого уровня.

### pref.net.exclusions

Если нажать на эту кнопку, вы увидите список, каждая строка в котором является названием пакета какого-то приложения. Смысл этого списка в том, чтобы дать пользователю возможность исключить какое-либо приложение из фильтрации на более глубоком уровне, нежели это можно сделать в Брандмауэре. Трафик приложений из списка pref.net.exclusions вообще не проходит через AdGuard, так что он не может быть изменен по определению.

Чтобы добавить приложение в этот список, просто введите новой строкой название пакета этого приложения. Для приложений из Google Play определить название очень просто - достаточно открыть страницу приложения и посмотреть на адресную строку. Часть после "**id=**" - именно то, что вам нужно. Например, для приложения YouTube ссылка целиком будет выглядеть как

**https://play.google.com/store/apps/details?id=com.google.android.youtube**,

где **com.google.android.youtube** - название пакета.

### Настройки фильтрации HTTPS

Мы объединили сразу несколько настроек под этим названием: **pref.https.apps.exclusions**, **pref.https.domains.blacklist** и **pref.https.domains.whitelist**. По сути, это те же самые настройки, которые можно найти в разделе настроек _HTTPs фильтрация_. Всю необходимую информацию относительно этого раздела можно найти в статье нашего блога:

<https://blog.adguard.com/en/adguard-android/adguard-for-android-25-official.html>

### pref.vpn.ipv6.bypass

Сегодня всё больше и больше SMS и MMS пересылаются через сеть, и в случаях, когда это происходит, всё чаще используется нестандартная сеть IPv6 . Когда мы пытаемся фильтровать такой трафик, инногда мы нарушаем отправку и даже получение MMS. Если вы подозреваете, что это как раз ваш случай, мы рекомендуем вам установить флажок напротив опции **pref.vpn.ipv6.bypass**, или добавить приложение, отвечающее за отправку MMS, в **pref.net.exclusions**.

### Все опции:

**pref.vpn.ipv4.force.default**

Если включено - VPN будет настроен на фильтрацию 0.0.0.0/0.

**pref.vpn.ipv4.force.complex**

Если включено - AdGuard принудительно будет фильтровать все соединения, кроме добавленных в исключения.

**pref.vpn.ipv4.address**

Адрес интерфейса IPv4 TUN.

**pref.vpn.ipv6.address**

Адрес интерфейса IPv6 TUN.

**pref.vpn.ipv6.force**

Если включено - AdGuard добавит IPv6-адрес в VPN, даже если нет активной сети IPv6.

**pref.vpn.ipv4.bypass**

Если включено - AdGuard не будет фильтровать трафик IPv4.

**pref.vpn.ipv6.bypass**

Если включено - AdGuard не будет фильтровать трафик IPv6.

**pref.vpn.ipv6.disable**

Если включено - AdGuard принудительно отключит маршруты IPv6 (VPN).

**pref.vpn.tun.mtu**

Устанавливает максимальное значение передачи данных MTU через VPN.

**pref.ipv4.routes.excluded**

Список маршрутов IPv4, исключенных из VPN и авто-прокси.

**pref.ipv6.routes.excluded**

Список маршрутов IPv6, исключенных из VPN и авто-прокси.

**pref.excluded.uids**

UID'ы исключенных пакетов.

**pref.vpn.capture**

Включает запись всего трафика проходящего через стек TCP/IP.

**pref.har.capture**

Включает запись файла HAR.

**pref.vpn.disable.pause**

Отключает автоматическую паузу VPN в случае отсутствия сети, режима модема или энергосбережения.

**pref.vpn.disable.reconfigure**

Отключает автоматическую перенастройку VPN.

**pref.proxy.disable.reconfigure**

Отключает автоматическую перенастройку Proxy.

**pref.proxy.block.ipv6**

Блокировка всех интернет-соединений через IPv6 (Proxy).

**pref.filtered.ports**

Список портов перенаправления.

**pref.boot.startup.delay**

Начальная задержка запуска защиты (в секундах) после загрузки устройства.

**pref.enforce.paused.notification**

Принудительное уведомление о приостановленной защите, даже если для значка уведомления установлено значение Выключено (для версий Android ниже Oreo).

**pref.root.clear.youtube**

AdGuard будет очищать данные приложения Youtube каждый раз при загрузке (необходимы права ROOT).

**pref.root.set.oom_adj**

AdGuard установит минимальный oom_score_adj для собственного процесса (необходимы права ROOT).

**pref.enforce.https.filtering**

Список приложений, для которых AdGuard применяет фильтрацию HTTPS, даже если они нацелены на платформу Android 7+.

**pref.removed.html.log**

AdGuard будет отображать информацию об удаленных элементах HTML в журнале фильтрации.

**pref.samsungpay.autopause.enable**

AdGuard приостановит защиту, пока приложение Samsung Pay находится на переднем плане (только в режиме VPN).

**pref.dns.bootstrap**

DNS-сервер начальной загрузки для DoH и DoT серверов.

**pref.dns.fallback**

Резервный DNS-сервер.

**pref.dns.blocking.type**

Тип блокировки для фильтрации DNS.

**pref.notify.on.unknown.ca**

Показывать уведомления о неизвестных CA.
