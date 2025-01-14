---
title: Как автоматизировать AdGuard для Android
published: false
taxonomy:
  category:
    - docs
visible: false
---

Многие пользователи выбирают Android именно потому, что эта ОС позволяет настроить мобильное устройство под свои вкусы и держать всё под контролем. И это абсолютно в порядке вещей, когда пользователей AdGuard по какой-то причине не устраивает его поведение по умолчанию. Допустим, вы хотите, чтобы защита отключалась при старте определённого приложения и снова включалась при его остановке. Это задача для так называемого "таскера".

## Интерфейс AdGuard

Существует множество приложений-таскеров, например, Tasker, AutomateIt и другие. AdGuard предоставляет интерфейс, с помощью которого такие приложения могут задавать всевозможные правила автоматизации.

Благодаря этому интерфейсу любое приложение может послать специальное сообщение (также называемое "intent", или "интент"), которое содержит имя действия и какую-либо дополнительную информацию. AdGuard увидит этот интент и выполнит запрашиваемое действие.

### Вопросы безопасности

"А не слишком ли это опасно" — спросите вы — "предоставлять случайным приложениям доступ к функциям AdGuard?" И будете правы, именно поэтому вместе с интентом пересылается пароль. Этот пароль генерируется автоматически, но вы, конечно, можете поменять его самостоятельно в расширенных настройках AdGuard.

### Доступные действия

Итак, готовы немного запачкать руки? Вот список действий, которые, будучи включёнными в интент, будут понятны AdGuard:

<a name="action_start"></a>

`start` — стартует защиту, дополнительные данные не нужны;

<a name="action_stop"></a>

`stop` — останавливает защиту, дополнительные параметры не нужны;

<a name="action_pause"></a>

`pause` — ставит защиту на паузу. Отличие от `stop` в том, что появится уведомление, тап по которому возобновит защиту. Дополнительные параметры не нужны;

<a name="action_update"></a>

`update` — проверяет наличие обновлений фильтров и приложения, дополнительные данные не нужны;

---

<a name="action_dns_filtering"></a>

`dns_filtering` — включает и выключает [DNS-фильтрацию](https://kb.adguard.com/ru/general/dns-filtering-android). Требуется дополнительный флаг:

`enable:true` или `enable:false` — соответственно, включает или выключает DNS-фильтрацию.

---

<a name="action_dns_server"></a>

`dns_server` — переключается между DNS-серверами, вам нужно указать дополнительные параметры:

`server:cloudflare` — переключается на конкретный сервер по его короткому имени;

> Полный список коротких имён серверов доступен во вкладке "Secure DNS" на странице настроек DNS

`server:1.1.1.1,1.0.0.1` — переключается на любой DNS-сервер;

`server:sdns://AQIAAAAAAAAAFDE3Ni4xMDMuMTMwLjEzMDo1NDQzINErR_JS3PLCu_iZEIbq95zkSV2LFsigxDIuUso_OQhzIjIuZG5zY3J5cHQuZGVmYXVsdC5uczEuYWRndWFyZC5jb20` — переключается на любой DNS-сервер, работающий по протоколам DNS-over-HTTPS, DNS-over-SSL или DNSCrypt;

`server:system` — сбрасывает настройки DNS на "по умолчанию" (т.е. используются системные DNS серверы).

---

**Не забудьте включить пароль как доп.параметр, а также упомянуть имя пакета и класс! Это необходимо делать для каждого интента!**

Параметр: `password:*******`

Имя пакета: `com.adguard.android`

Класс: `com.adguard.android.receivers.AutomationReceiver`

### Пример интента

![](automation.png?cropResize=324,1023)
