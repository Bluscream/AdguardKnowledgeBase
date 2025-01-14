---
title: "Проблемы, специфичные для macOS 11 Big Sur"
taxonomy:
  category:
    - docs
visible: true
---

- [Существующие проблемы (Big Sur 11.2)](#current)
  - [Совместимость с локальными прокси](#local-proxies)
    - [Настройка вышестоящего прокси Shadowsocks](#shadowsocks)
    - [Настройка вышестоящего прокси Surge](#surge)
  - [Совместимость с Cisco AnyConnect](#cisco)
  - [Совместимость с Flutter](#flutter)
  - [VPN-приложения со старым API](#legacy-api)
- [Уже исправленные проблемы](#fixed)
  - [Совместимость с Little Snitch](#little-snitch)
- [Альтернативы использованию Network Extension](#alternatives)
  - [Использование режима «Автоматический прокси»](#automatic-proxy)
  - [Переключение на Kernel Extension в Big Sur](#kernel-extension)

Новейшая версия macOS, **BigSur**, вышла в конце 2020 года. В ней появляется новый API, Network Extensions, пришедший на замену старому API Kernel Extensions. И он уже обуславливает некоторые проблемы в работе многих приложений, AdGuard не оказался исключением. В этой статье собраны известные проблемы и возможные способы их решения.

<a id="current"></a>

## Известные проблемы (Big Sur 11.2)

Эти проблемы ещё не исправлены разработчиками Apple, либо исправлены только частично.

<a id="local-proxies"></a>

### Совместимость с локальными прокси

> Важно: в Big Sur 11.1 (и новее) AdGuard может фильтровать локальные прокси без проблем (в большинстве случаев). Если вы всё же столкнулись с какими-либо трудностями, или если вы используете Big Sur 11.0, уберите локальный прокси из системных настроек и настройте вышестоящий прокси в AdGuard, следуя инструкции ниже.

> После выхода обновления Big Sur 11.3 вернулись прежние проблемы с локальными прокси. Apple, скорее всего, уже работает над исправлением данного бага, и мы также рассматриваем возможности обойти эту проблему. Необходимые правки уже внесены в [Nightly-версию](http://agrd.io/mac_nightly) AdGuard для Mac.

Чтобы настроить вышестоящий прокси в AdGuard для Mac на Big Sur, вам необходимо перейти в _Меню AdGuard -> Дополнительно -> Расширенные настройки..._. Кликните по области _Значение_ настройки `upstream.proxy`, чтобы настроить прокси.

<img src="https://cdn.adguard.com/public/Adguard/kb/BigSur/problems/proxy_ru.png" style="max-width: 650px;">

Введите строку вида `scheme://user:password@host:port`, где

- `scheme` имеет значение `http`, `https`, `socks4` или `socks5`, в зависимости от типа прокси.

> Если вы используете тип прокси `socks5`, установите значение настройки `upstream.proxy.socks5udp` как `true`, чтобы указать AdGuard направлять UDP-трафик через прокси-сервер.

- `user` и `password` — имя пользователя и пароль от вашего прокси соответственно (если требуются). Игнорируйте эти параметры, если один из них (или оба) не применимы к данному прокси.
- `host` — IP-адрес вашего прокси-сервера.
- `port` — желаемый номер порта, который будет использоваться прокси-сервером.

> Пример: стркоа `socks5://localhost:6322` настроит локальный прокси типа SOCKS5, который слушает порт 6322 и не требует имени пользователя и пароля.

Нажмите _Применить_, чтобы заставить AdGuard пересылать весь трафик через настроенный прокси-сервер.

Если у вас возникли трудности в процессе настройки вышестоящего прокси, свяжитесь с нашей службой поддержки: support@adguard.com.

<a id="shadowsocks"></a>

#### Пример 1: Настройка вышестоящего прокси Shadowsocks

Здесь на примере [Shadowsocks](https://shadowsocks.org/en/index.html) проиллюстрирована настройка вышестоящего прокси в AdGuard.

Прежде всего, вам потребуется настроить работу серверной части вашего прокси. Вероятнее всего, для этого вы будете использовать JSON-файл наподобие этого (значения полей `server` и `password` здесь выбраны случайным образом):

```
{
    "server":"111.222.333.444",
    "server_port":8388,
    "local_port":1080,
    "password":"barfoo!",
    "timeout":600,
    "method":"chacha20-ietf-poly1305"
}
```

> Подробнее почитать о том, как начать работать с Shadowsocks, можно на их [веб-сайте](https://shadowsocks.org/en/config/quick-guide.html).

Затем надо установить клиент Shadowsocks на ваш Mac. Убедитесь, что вы выбрали "Manual Mode" или "Auto Mode" в настройках! Конфигурация с "Global Mode" работать не будет! В версиях Big Sur ниже 11.1 также не будет работать режим "Auto Mode".

<img src="https://cdn.adguard.com/public/Adguard/kb/BigSur/problems/shadowsocks.png" style="max-width: 350px;">

Теперь надо перейти в _Меню AdGuard -> Дополнительно -> Расширенные настройки..._ и вписать в поле _Значение_ настройки `upstream.proxy` строку `socks5://localhost:1080`. Обратите внимание, что здесь необходимо использовать значение "local_port" из JSON-файла, упомянутого выше.

Поскольку Shadowsocks использует SOCKS5, вам также понадобится изменить значение настройки `upstream.proxy.socks5udp` в Расширенных настройках AdGuard на `true`, если вы хотите, чтобы AdGuard также направлял через прокси-сервер UDP-трафик вашего Mac.

<a id="surge"></a>

#### Пример 2: Настройка вышестоящего прокси Surge

В версиях Big Sur 11.1 и выше не существует известных конфликтов между AdGuard и Surge. Если вы используете более старую версию Big Sur, убедитесь, что отключён **System Proxy** в правом нижнем углу. В противном случа Surge не будет работать вместе с AdGuard. С другой стороны, **Enhanced Mode** включать можно на любой версии системы, он не вызовет конфликтов.

<img src="https://cdn.adguard.com/public/Adguard/kb/BigSur/problems/surge.png" style="max-width: 800px;">

Теперь переходим в _Меню AdGuard -> Дополнительно -> Расширенные настройки..._ и вписываем в поле _Значение_ настройки `upstream.proxy` строку `socks5://localhost:6153` или `http://localhost:6152`, в зависимости от типа прокси, который вы хотите использовать. Обратите внимание, что нужно использовать значение **port**, указанное в разделе **Events** вкладки **Activity** в вашем клиенте Surge.

Если вы выбрали протокол SOCKS5, вам также понадобится изменить значение настройки `upstream.proxy.socks5udp` в Расширенных настройках AdGuard на `true`, чтобы AdGuard мог пропускать UDP-трафик через прокси-сервер.

<a id="cisco"></a>

### Совместимость с Cisco AnyConnect

AdGuard не будет работать вместе с Cisco AnyConnect, если находится в режиме фильтрации _Network Extension_. Вам нужно переключить AdGuard в режим _Автоматический прокси_. Чтобы сделать это, [следуйте инструкции](#automatic-proxy).

<a id="flutter"></a>

### Совместимость с Flutter

Если вы используете Flutter на Big Sur параллельно с AdGuard в режиме "Network Extension" (или с любым другим приложением типа "Transparent Proxy"), вы столкнётесь с проблемами: проекты не будут открываться и приложение окажется, по сути, сломанным. Мы уже сообщили Apple об этом баге. Тем временем, вы можете использовать одно из этих временных решений:

1. Используйте AdGuard в режиме [Автоматический прокси](#automatic-proxy) mode

2. Отключите SIP и переключите AdGuard в режим Kernel Extension по инструкции [отсюда](#kernel-extension).

<a id="legacy-api"></a>

### VPN-приложения со старым API

Несмотря на то, что AdGuard отображается в системных настройках, как VPN, конфликтов с другими приложениями на основе VPN возникнуть не должно. Однако, если вы используете VPN-приложение, скачанное не из AppStore, существует шанс, что оно использует сторое VPN API, и в таком случае необходимо исключить его из фильтрации:

1. Откройте меню AdGuard.
2. Выберите _Настройки..._.
3. Переключитесь на вкладку _Сеть_.
4. Кликните по кнопке _Приложения..._.
5. Найдите приложение, которое вы хотите добавить в исключения, и уберите галочку напротив него.

<img src="https://cdn.adguard.com/public/Adguard/kb/BigSur/problems/legacy-api_ru.png" style="max-width: 650px;">

<a id="fixed"></a>

## Уже решённые проблемы

Эти проблемы уже решены разработчиками Apple, но могут встречаться на более старых версиях macOS Big Sur.

<a id="little-snitch"></a>

### Совместимость с Little Snitch 5

На момент написания статьи режим фильтрации Network Extension в AdGuard не совместим с [Little Snitch 5](https://obdev.at/products/littlesnitch/index.html). Когда они оба запущены, существует вероятность столкнуться с проблемами в поведении различных приложений, даже если они исключениы из фильтрации в AdGuard. Эта проблема вызвана багом в Big Sur, о котором мы уже проинформировали Apple. Это позволяет надеяться, что в ближайших обновлениях он будет исправлен.

Необходимо заметить, что эту проблему нельзя решить отключением мониторинга соединений в Little Snitch, поскольку это не выгружает его расширение из системы. Мы рекомендуем использовать режим фильтрации [**Автоматический прокси**](#automatic-proxy), если вы запускаете AdGuard на одном устройстве с Little Snitch под Big Sur, во всяком случае до тех пор, пока Apple не исправит данную проблему совместимости.

<a id="alternatives"></a>

## Альтернативы использованию Network Extension

Невозможно предвидеть все потенциальные проблемы, которые могут возникнуть в Big Sur, ведь существует бесчисленное количество комбинаций железа, софта и настроек. Так что если вы всё же столкнётесь с какими-либо сложностями, пожалуйста, напишите нам в поддержку — но также вы можете попробовать одно из альтернативных решений.

<a id="automatic-proxy"></a>

### Использование в режиме "Автоматический прокси"

Если вы столкнулись в какими-либо проблемами в Big Sur, которые нельзя решить способами, описанными выше, вы можете попробовать переключить AdGuard в режим _Автоматический прокси_.

1. Откройте меню AdGuard.
2. Выберите _Настройки..._.
3. Переключитесь на вкладку _Сеть_.
4. Кликните по кнопке _Выбрать режим..._.
5. Выберите _Automatic proxy_.

<img src="https://cdn.adguard.com/public/Adguard/kb/BigSur/problems/automatic-proxy_ru.png" style="max-width: 650px;">

AdGuard автоматически добавит **.pac**-файл в сетевые настройки вашего Mac, и теперь система будет распознавать AdGuard как прокси и попытается направлять через него весь трафик.

> Примите во внимание, что некоторые приложения могут игнорировать это настройку, и в таком случае их трафик не будет фильтроваться.

<a id="kernel-extension"></a>

### Переключение на Kernel Extension в Big Sur

По умолчанию, на Big Sur AdGuard использует фреймворк Network Extension, так как используемый ранее фреймворк Kernel Extension отключён в новой версии системы. Это может вызывать проблемы совместимости, но чтобы включить Kernel Extension обратно, вам сначала потребуется отключить системную настройку безопасности System Integrity Protection (SIP). Для отключения SIP следуйте этой инструкции:

1. Кликните по _Символу Apple_ в строке меню.
2. Кликните _Перезагрузить…_
3. Зажмите _Command-R_, чтобы запустить систему в Режиме Восстановления.
4. Кликните по кнопке _Utilities_.
5. Выберите _Terminal_.
6. Вбейте в появившемся окне `csrutil disable`.
7. Нажмите на клавиатуре клавишу _Return_ или _Enter_.
8. Кликните по _Символу Apple_ в строке меню.
9. Кликните _Перезагрузить…_

Теперь, когда SIP отключён, выполните следущие шаги для включения Kernel Extension:

<img src="https://cdn.adguard.com/public/Adguard/kb/BigSur/problems/kernel_ru.png" style="max-width: 650px;">

1. Откройте меню AdGuard.
2. Выберите _Настройки..._.
3. Переключитесь на вкладку _Сеть_.
4. Кликните по кнопке _Выбрать режим..._.
5. Выберите _Kernel Extension_.

> Однако, мы рекомендуем использовать этот метод только в том случае, если все остальные не дали результата, поскольку он может привести к непредвиденным последствиям.
