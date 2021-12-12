---
title: 'Ошибка "Вероятная угроза безопасности"'
taxonomy:
  category:
    - docs
visible: true
---

<img src="https://cdn.adguard.com/public/Adguard/kb/ru/certificate/cert_error_ru.png" style="border: 1px solid #efefef; padding: 2px; max-width: 700px;" />

Ошибка "Вероятная угроза безопасности" чаще всего встречается в браузерах на основе Firefox, таких как Mozilla Firefox, PaleMoon, Waterfox и другие.

Начиная с версии 68, Firefox доверяет сертификатам из системного хранилища при выполнении определённых условий. Но иногда по какой-либо причине (не зависящей от AdGuard) механизм доверия сертификатам из системного хранилища перестаёт работать, что и приводит к возникновению этой ошибки. Чтобы исправить её, необходимо скачать локальный сертификат AdGuard и затем добавить его в собственное хранилище сертификатов вручную. Для этого выполните следующие шаги:

> Данная инструкция описывает порядок действий в браузере Firefox, названия кнопок и разделов могут немного отличаться в других браузерах на его основе.

1. Запустите AdGuard.

2. Перейдите на страницу [http://local.adguard.org/cert](http://local.adguard.org/cert) и кликните по кнопке _Скачать_. Браузер начнёт загрузку файла **cert.cer**.

> Также вы можете перейти на страницу скачаивания сертификата напрямую из раздела приложения _Настройки - Сеть - Фильтрация HTTPS_.

<img src="https://cdn.adguard.com/public/Adguard/kb/ru/certificate/cert_win_ru.png" style="border: 1px solid #efefef; padding: 2px; max-width: 500px;" />

3. Откройте ваш браузер и затем откройте в нём _Настройки_.

4. Перейдите во вкладку _Приватность и защита_.

5. Прокрутите страницу вниз до раздела _Сертификаты_ и кликните по кнопке _Просмотр сертификатов..._.

<img src="https://cdn.adguard.com/public/Adguard/kb/ru/certificate/cert_settings_ru.png" style="border: 1px solid #efefef; padding: 2px; max-width: 700px;" />

6. Выберите вкладку _Центры сертификации_.

7. Нажмите кнопку _Импортировать..._.

<img src="https://cdn.adguard.com/public/Adguard/kb/ru/certificate/cert_import_ru.png" style="border: 1px solid #efefef; padding: 2px; max-width: 500px;" />

8. Найдите загруженный файл **cert.cer** и нажмите _Открыть_.

9. Нажмите кнопку _OK_.

Вы успешно установили сертификат AdGuard. Перезапустите браузер и ошибка должна исчезнуть.
