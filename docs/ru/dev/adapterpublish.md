---
title: Разработка - Издательские адаптеры
lastChanged: 14.09.2018
editLink: https://github.com/ioBroker/ioBroker.docs/edit/master/docs/ru/dev/adapterpublish.md
translatedFrom: de
translatedWarning: Если вы хотите отредактировать этот документ, удалите поле «translationFrom», в противном случае этот документ будет снова автоматически переведен
hash: dwTMQkRGPU/TgOfkndd1Y2lo5lmjAaxCsDaLBue6p3k=
---
# Опубликовать адаптер
Прежде чем рассмотреть возможность публикации адаптера, его следует предложить для тестирования в [Тестовая тема форума](https://forum.iobroker.net/viewforum.php?f=36). Если тесты пройдены успешно и адаптер стабилен, его следует сначала включить в последний репозиторий. <br/><br/> Если адаптер стабильно работает с определенным номером версии, его можно перенести в стабильный репозиторий. Для этого требуется собственная оценка разработчика во взаимодействии с отзывами пользователей.

## Требования к последнему репозиторию
1. GitHub-хранилище адаптера должно иметь большую букву B в ioBroker, пока она мала в package.json

должен быть написан, потому что ``npm`` не допускает прописные буквы.

2. Заголовок в io-package.json не должен содержать слова ``ioBroker`` und nicht das Wort ``Adapter``.

3. ``title`` Attribut in der io-package.json (common) ist der Kurzname des Adapters auf Englisch. Während ``titleLang``

содержит переводы атрибута ``title``. (расширение Lang обозначает языки)

4. Адаптер должен содержать инструкции в виде файла README.md. Это должно быть по крайней мере на английском языке

быть доступным Кроме того, приветствуются другие языки. Это §§LLLL_0§§ может служить предложением.

5. Адаптер требует лицензии. Как в io-package.json, так и в отдельном

[файл](https://github.com/foxriver76/ioBroker.denon/blob/master/LICENSE) в хранилище Github.

   Пример использования io-package.json:

```json
{
  "common": {
      "license": "MIT"
  }
}
```

6. Каталог ``www`` Verzeichnis sowie das ``widget`` следует удалять, когда он не используется.

7. В io-package.json атрибут ``type`` должен быть создан в общем. Для этого следует из этого

§§LLLL_0§§ указана наиболее подходящая категория.

8. Состояния, созданные адаптером, должны быть действительными для их

[рулет](https://github.com/ioBroker/ioBroker/blob/master/doc/STATE_ROLES.md#state-roles) ``role`` имеют общее.
Следует избегать использования роли `state`.

9. Адаптер должен использовать оба теста, указанные в шаблоне. Это можно сделать с помощью учетной записи Github в Appveyor.

(Тесты Windows) и Travis CI (тесты Linux и Mac OS) связаны, и соответствующий репозиторий для тестирования регистрируется. Эти два инструмента непрерывной интеграции доказали свою пригодность для проекта ioBroker и бесплатны для общедоступных репозиториев Github. <br/><br/> Область тестирования может быть расширена разработчиком.

10. В io-package.json должна быть хотя бы одна общая спецификация для атрибута `authors`. также

атрибут `author` должен быть заполнен в package.json. При желании несколько авторов могут быть сохранены для npm, используя атрибут `contributors` в package.json.

11. Адаптер должен быть доступен в виде пакета npm. Больше информации можно

§§LLLL_0§§ найдены.

12. Организация ioBroker должна быть добавлена в npm. Это необходимо для обеспечения долгосрочного обслуживания упаковки

даже если разработчик не может ждать пакета из-за времени или других причин. Дополнительную информацию можно найти [здесь](https://github.com/ioBroker/ioBroker.repositories#add-owner-to-packet).

## Требования к стабильному репозиторию
1. Адаптер был успешно добавлен в последний репозиторий
2. Для адаптера есть [Тестовая тема форума](https://forum.iobroker.net/viewforum.php?f=36), в котором уже

Обратная связь с пользователем была дана.

3. Должна быть реализована функция обнаружения. Это функция в

[Discovery Adapter](https://github.com/ioBroker/ioBroker.discovery) для автоматического определения, может ли пользователь использовать экземпляр адаптера. Для этого необходимо поместить запрос на извлечение данных в хранилище [Адаптеры Discovery](https://github.com/ioBroker/ioBroker.discovery).

## Добавьте адаптер в официальный репозиторий
1. §§LLLL_0§§ следует посетить

и запрос на извлечение со следующим содержимым, в зависимости от хранилища.

2. Пожалуйста, расположите адаптер в алфавитном порядке между существующими адаптерами.

3. После включения в стабильный репозиторий должен быть объявлен номер версии. Это в разработке

адаптера.

4. Адаптер должен установить атрибут списка `docs` в io-package.json, где руководство

можно найти на соответствующем языке. Ключом является язык и в качестве значения путь к файлу уценки.
Требуются инструкции на английском языке (в случае крайней необходимости можно сослаться на стандарт README). Также желательно немецкое руководство, потому что большинство пользователей говорят по-немецки, но это не обязательно.
Подробное руководство, разработчик может сэкономить много времени на форуме. Пример можно найти [здесь](https://github.com/foxriver76/ioBroker.denon/blob/master/docs/de/README.md).

   пример:

```json
{
  "common": {
     "docs": {
         "de": "docs/de/README.md"
     }
  }
}
```

### Последний
Файл `sources-dist.json` необходимо отредактировать:

пример:

```json
  "admin": {
    "meta": "https://raw.githubusercontent.com/ioBroker/ioBroker.admin/master/io-package.json",
    "icon": "https://raw.githubusercontent.com/ioBroker/ioBroker.admin/master/admin/admin.png",
    "published": "2017-04-10T17:10:21.690Z",
    "type": "general"
  }
```

Дата `published` представляет дату первой публикации и не должна изменяться.

### Стабильный
Файл `sources-dist-stable.json` необходимо отредактировать:

пример:

```json
  "admin": {
    "meta": "https://raw.githubusercontent.com/ioBroker/ioBroker.admin/master/io-package.json",
    "icon": "https://raw.githubusercontent.com/ioBroker/ioBroker.admin/master/admin/admin.png",
    "version": "2.0.7",
    "published": "2017-04-10T17:10:21.690Z",
    "type": "general"
  }
```

Дата `published` представляет дату первой публикации и не должна изменяться.

## Администрирование версий адаптера
Текущий номер версии адаптера указывается как в io-package.json, так и в package.json. Две детали должны совпадать. Номер версии разделен на три части двумя точками.

```json
"version": "1.7.6"
```

Первая часть (слева направо) представляет собой `Major Part`, вторая часть - часть `minor`, а последняя - часть `micro`. Номера версий следует увеличить в соответствии со следующим списком:

- **микро** исправлены только ошибки
- **несовершеннолетний** функции были добавлены, но версия совместима с предыдущими версиями
- **Major** Большие изменения, благодаря которым обратная совместимость со старой версией больше не предоставляется.

Атрибут `news` также должен поддерживаться в io-package.json. Это позволяет пользователям устанавливать любую версию из списка (при условии, что она была выпущена на npm) через интерфейс администратора.
Здесь следует указать номер версии и изменения. Изменения могут быть задокументированы для любого поддерживаемого языка, по крайней мере, на английском языке.

пример:

```json
"news": {
    "1.7.6": {
        "en": "Configuration dialog was corrected",
        "de": "Konfigurationsdialog wurde korrigiert",
        "ru": "Диалог конфигурации был исправлен",
        "pt": "A caixa de diálogo de configuração foi corrigida",
        "nl": "Configuratiedialoog is gecorrigeerd",
        "fr": "La boîte de dialogue de configuration a été corrigée",
        "it": "La finestra di configurazione è stata corretta",
        "es": "Se corrigió el diálogo de configuración",
        "pl": "Okno dialogowe konfiguracji zostało poprawione"
    },
    "1.7.5": {
        "en": "The roles were tuned",
        "de": "Die Rollen waren abgestimmt",
        "ru": "Роли были настроены",
        "pt": "Os papéis foram afinados",
        "nl": "De rollen zijn afgestemd",
        "fr": "Les rôles ont été réglés",
        "it": "I ruoli erano sintonizzati",
        "es": "Los roles fueron sintonizados",
        "pl": "Role zostały dostrojone"
    }
}
```

## Категории адаптеров
- **сигнализация** - системы безопасности
- **климат-контроль** - кондиционеры, воздушные фильтры, обогреватели и многое другое
- **связь** - предоставление данных для других адаптеров, например. Б. ОТДЫХОМ
- **Дата и время** - z. Например календарь
- **энергия** - текущий мониторинг, солнечные системы, инверторы и многое другое.
- **измерение** - дополнительные измерительные системы (например, вода, газ, нефть)
- **сад** - з. Как газонокосилки, спринклерные системы
- **общие** - общие адаптеры, такие как Admin, Web, Discovery
- **геопозиция** - геолокация объектов или лиц
- **Аппаратное обеспечение** - Различные многофункциональные устройства, такие как Arduino, ESP, Bluetooth, ...
- **бытовая** - кухонная техника, пылесосы и пр.
- **инфраструктура** - сеть, NAS, принтеры, телефоны
- **iot-systems** - Другие системы умного дома (аппаратное и программное обеспечение)
- **освещение** - освещение
- **логика** - правила, скрипты, парсеры и т. д.
- **обмен сообщениями** - Адаптер для отправки и получения сообщений, например. Например, по электронной почте, телеграмме, ...
- **misc-data** - экспорт и импорт данных, конвертер валют и др.
- **мультимедиа** - телевизор, AVR, колонки, голосовые помощники и т. д.
- **сеть** - пинг, обнаружение сети, UPnP, ...
- **протоколы** - протоколы связи, например. B. MQTT
- **хранилище** - регистрация, хранение данных z. Например, реляционные базы данных, ...
- **утилита** - поддержка таких адаптеров. Например, резервное копирование
- **визуализация** - адаптер для визуализации, например, vis и т. д.
- **visualization-icons** - иконки для визуализаций
- **визуализация-виджеты** - виджеты iobroker.vis
- **погода** - информация о погоде, качество воздуха, информация об окружающей среде

?> ***Это подстановочный знак*** . <br><br> Помогите с ioBroker и расширьте эту статью. Пожалуйста, обратите внимание на [Руководство по стилю ioBroker](community/styleguidedoc), чтобы изменения могли быть легко приняты.