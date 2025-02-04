---
title: "Как работает блокировка рекламы"
taxonomy:
  category:
    - docs
visible: true
---

- [Введение](#introduction)
- [Общие принципы](#general)
- [Фильтры](#filter-lists)
- [Типы правил фильтрации](#types-filtering)
  - [Базовые правила](#basic)
  - [Косметические правила](#cosmetic)
  - [HTML-правила](#html)

<a name="introduction"></a>

## Введение

В семействе блокировщиков AdGuard есть много продуктов для разных платформ, у каждого из них свои уникальные особенности. Но что их объединяет — они все блокируют рекламу и трекинг. Эта статья описывает, как устроена блокировка рекламы изнутри.

> В этой статье мы не касаемся DNS-фильтрации. Это альтернативный способ блокировать рекламу, со своими преимуществами и недостатками. Переходите по этой ссылке, чтобы [узнать больше про DNS-фильтрацию](https://kb.adguard.com/ru/general/dns-filtering).

<a name="general"></a>

## Общие принципы

В основе любого блокировщика лежат фильтры. Фильтры — это буквально списки правил, написанные в соответствии с определённым синтаксисом. Блокировщики понимают этот сложный синтаксис. Они интерпретируют правила и на их основе совершают те или иные действия с веб-трафиком: блокируют элементы, изменяют вид веб-страниц и т.д.

<img src="https://cdn.adguard.com/public/Adguard/Blog/manifestv3/adblockingworks_ru.png" style="max-width: 750px; border: 1px solid #efefef;">

<a name="filter-lists"></a>

## Фильтры

Чтобы понимать, как работает блокировка рекламы, вначале надо разобраться в основополагающих принципах работы фильтров.

Правила фильтрации, из которых состоят фильтры, не создаются сами собой. Они являются результатом кропотливой работы разработчиков фильтров, как профессионалов, так и волонтёров. Разработчики используют консоль браузеров и другие инструменты (такие, как Журнал фильтрации AdGuard), чтобы определять, какое правило нужно для блокировки конкретной рекламы или трекера. Это очень упрощённое описание процесса: в особо трудных случаях могут потребоваться сразу несколько правил, множество итераций и использование сложного синтаксиса, чтобы заблокировать элемент.

Даже когда правило попадает в фильтр, оно не остаётся там навсегда. Реклама и способ её подачи могут поменяться, и правила фильтрации должны меняться вслед за ними. Иногда правила устаревают и больше не нужны, иногда появляется новая реклама и требуются новые правила, а иногда уже существующее правила требуется доработать. Поэтому фильтры требуют постоянной поддержки, и часто эту поддержку осуществляет всего один человек. Но даже в случае с целой командой разработчиков фильтров невозможно представить, чтобы они постоянно мониторили все сайты в интернете. Поэтому многие блокировщики имеют встроенный функционал, чтобы дать пользователям простой способ сообщать о пропущенной рекламе и любых других проблемах с фильтрами, с которыми они сталкиваются.

<img src="https://cdn.adguard.com/public/Adguard/Blog/manifestv3/filtersupdates_ru.png" style="max-width: 750px; border: 1px solid #efefef;">

Пользователи AdGuard [могут отправлять такие отчёты при помощи специальной веб-утилиты](https://reports.adguard.com/new_issue.html). Благодаря жалобам пользователей разработчики могут сфокусироваться на исправлении и дополнении фильтров, а не на поиске пропущенной рекламы по всей сети.

Фильтры могут гораздо больше, чем просто блокировать рекламные элементы. Существуют фильтры для блокировки трекеров, виджетов социальных сетей, раздражающих элементов (вроде уведомлений о cookie) и т.д. Разные пользователи могут выбирать разные комбинации фильтров, чтобы подстроить фильтрацию под свои нужды. Существуют специальные сайты, такие, как [filterlists.com](https://filterlists.com/), где собраны огромные базы всевозможных фильтров.

> Мы разрабатываем и поддерживаем [свой собственный набор фильтров](https://kb.adguard.com/ru/general/adguard-ad-filters), которые можно использовать как внутри AdGuard, так и с другими блокировщиками.

<a name="types-filtering"></a>

## Типы правил фильтрации

Существует множество видов правил фильтрации, служащих различным целям. В зависимости от используемого вами блокировщика и в особенности от вашей операционной системы, те или иные виды правил могут не поддерживаться.

<a name="basic"></a>

### Базовые правила

Чтобы вы увидели рекламу на веб-странице или в приложении, её сначала необходимо загрузить с сервера. Для этого браузер или приложение должны отправить веб-запрос. Самый простой способ предотвратить загрузку рекламы — заблокировать этот запрос, так что он никогда не попадёт на сервер, а значит и реклама не загрузится.

Практически все продукты из семейства AdGuard могут блокировать веб-запросы в соответствии с активными правилами фильтрации. Этот метод является одним из самых эффективных в плане блокировки рекламы, но у него есть и недостатки. Самый очевидный из всех — на месте заблокированной рекламы может остаться пустое место.

<a name="cosmetic"></a>

### Косметические правила

Каждая веб-страница имеет так называемый DOM ("document object model" или "объектная модель документа"), по сути — HTML-документ, содержащий структуру страницы и всех её элементов. Реклама на странице тоже является элементом и, следовательно, отображается в DOM. Блокировщики могут убирать часть DOM, а правила фильтрации помогают им понять, какие именно куски DOM соответствуют рекламе и требуют удаления, а какие не стоит трогать.

Этот метод позволяет, например, избежать остатков рекламы, вроде пустых кусков страницы, но также и выполнять другие, более сложные задачи.

<a name="html"></a>

### HTML-правила

В большинстве случаев вышеупомянутых базовых и косметических правил достаточно, чтобы скрыть или заблокировать всю рекламу. Но иногда требуется изменить сам HTML-код страницы ещё до того, как она будет загружена. Для этого существуют правила фильтрации HTML-контента. Такие правила указывают блокировщику на элементы HTML, которые нужно вырезать из кода ещё до загрузки страницы браузером.

Это весьма сложный тип правил, и он требует от блокировщика наличия определённых прав, поэтому поддерживается не на всех платформах. HTML-правила работают в приложениях AdGuard для Windows, Mac и Android, а также в браузерном расширении AdGuard для Firefox.

> Есть и другие типы правил фильтрации, но для их понимания необходим ещё более высокий уровент технической подготовки. Если вам интересно, [вы можете ознакомиться с подробным описанием правил фильтрации](https://kb.adguard.com/ru/general/how-to-create-your-own-ad-filters) в статье по ссылке.
