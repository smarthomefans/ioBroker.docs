---
translatedFrom: en
translatedWarning: Если вы хотите отредактировать этот документ, удалите поле «translationFrom», в противном случае этот документ будет снова автоматически переведен
editLink: https://github.com/ioBroker/ioBroker.docs/edit/master/docs/ru/adapterref/iobroker.smartmeter/README.md
title: ioBroker.smartmeter
hash: BkclHlQZa18om+0WsiTUS5k15xa2gQwlXdKSIEOX8AU=
---
![логотип](../../../en/adapterref/iobroker.smartmeter/admin/smartmeter.png)

![Значок Greenkeeper](https://badges.greenkeeper.io/Apollon77/ioBroker.smartmeter.svg)
![Количество установок](http://iobroker.live/badges/smartmeter-stable.svg)
![Версия NPM](http://img.shields.io/npm/v/iobroker.smartmeter.svg)
![Загрузки](https://img.shields.io/npm/dm/iobroker.smartmeter.svg)
![Трэвис-CI](http://img.shields.io/travis/Apollon77/ioBroker.smartmeter/master.svg)
![AppVeyor](https://ci.appveyor.com/api/projects/status/github/Apollon77/ioBroker.smartmeter?branch=master&svg=true)
![NPM](https://nodei.co/npm/iobroker.smartmeter.png?downloads=true)

# IoBroker.smartmeter
[![Изменение климата] (https://codeclimate.com/github/Apollon77/ioBroker.smartmeter/badges/gpa.svg)](https://codeclimate.com/github/Apollon77/ioBroker.smartmeter)

Этот адаптер для ioBroker позволяет считывать и анализировать протоколы smartmeter, которые следуют числовой логике OBIS, чтобы сделать их данные доступными.

*** Для работы адаптера требуется nodejs 4.x! ***

*** Для этого адаптера в настоящее время должен быть установлен git! ***

## В настоящее время известные проблемы
* Этот адаптер использует библиотеку Serialport. Это может означать более длительное время установки, если его нужно скомпилировать
* Кажется, что обработка памяти иногда неоптимальная и может привести к сбоям с SIGABRT или SIGSEGV во время чтения данных. iobroker Controller автоматически перезапустит Адаптер, поэтому единственный эффект здесь - 2-3 loglines :-)

## Описание параметров
ioBroker-Forum-Thread: http://forum.iobroker.net/viewtopic.php?f=23&t=5047&p=54973

### Протокол данных
Поддерживаемые протоколы:

* **Sml** SML (SmartMeterLanguage) в двоичном формате
* **D0** D0 (на основе IEC 62056-21: 2002 / IEC 61107 / EN 61107) в формате ASCII (режим двоичного протокола E в настоящее время не поддерживается)
* **Json-Efr** данные OBIS из EFR Smart Grid Hub (формат JSON)

### Обмен данными
* **Последовательный прием** получение через последовательные push-данные (Smartmeter отправляет данные без каких-либо запросов на регулярной основе). В основном используется для SML
* **Последовательная двунаправленная связь** протокол D0 в режимах A, B, C и D (режим E в настоящее время НЕ поддерживается!) С Wakeup-, Signon-, pot. ACK- и Data-сообщения для считывания данных (режим программирования / записи пока не реализован)
* **Http-Requests** чтение данных через HTTP, запрашивая определенный URL
* **Локальные файлы** чтение данных из локального файла

### Интервал запроса данных
Количество секунд ожидания следующего запроса или приостановки последовательного приема, значение 0 можно перезапустить сразу после завершения одного сообщения,

По умолчанию: 300 (= 5 минут)

### Скорость передачи последовательного устройства
скорость передачи для начального последовательного соединения, если не определены значения по умолчанию для типа транспорта (9600 для SerialResponseTransprt и 300 для SerialRequestResponseTransport)

### D0: Команда SignOn-Message
Команда для входа в сообщение, по умолчанию "?" запрашивать обязательные поля, другие значения в зависимости от устройства.
Пример: 2WR5 Heatmeter использует «#» для запроса намного большего количества данных (необязательные поля вместе со всеми обязательными)

### D0: режим перезаписи
Адаптер пытается определить режим протокола D0, как определено в спецификациях. Есть некоторые устройства, которые не соответствуют спецификациям и поэтому создают проблемы. Используя эту опцию, вы можете перезаписать определенный режим протокола.

* Режим A: нет смены скорости передачи, нет Ack-сообщения
* Режим B: переключение скорости передачи, нет Ack-сообщения
* Режим C: необходимо изменить скорость передачи и Ack-сообщение
* Режим D: без изменения скорости передачи данных, скорость передачи данных всегда 2400
* Режим E: необходимо изменить скорость передачи и Ack-сообщение, пользовательские протоколы не поддерживаются! Свяжитесь со мной, если у вас есть такой смартметр

### D0: Baudrate-Changeover-Overwrite
Адаптер пытается определить скорость передачи для сообщений данных, как определено в спецификациях протокола. Но, как и в случае с режимом, некоторые смартметры предоставляют здесь неверные данные. Таким образом, вы можете использовать это, чтобы перезаписать скорость передачи для сообщения данных по мере необходимости. Оставьте пустым, чтобы использовать переключение скорости передачи данных, как определено интеллектуальным счетчиком.

## Адаптер протестирован с ...
... по крайней мере:

* Hager eHz Energy Meter (несколько, например, eHZ-IW8E2A5L0EK2P, EHZ363W5,)
* EMH Счетчик энергии
* EFR SmartGridHub
* Siemens 2WR5 считыватель с тепловой станции
* Elster AS1440
* Iskraemeco MT174
* Iskraemeco MT175
* Itron EM214 Typ 720
* Голландский интеллектуальный счетчик, использующий протокол DSRM (в качестве протокола используйте «только данные чтения последовательного устройства» и «D0»)

Пожалуйста, пришлите мне информацию об устройствах, где вы успешно использовали библиотеку, и я добавлю ее здесь.

## Сделать
* Обновите поддержку Sml до 1.0.4 (при необходимости)
* документы для веб-страницы

## Changelog

### 2.0.0 (2019-03-22)
* BREAKING CHANGE: State names changed because * no longer supported. Is replaced by __ now because of possible collisions in state names with only one _

### 1.2.2 (2018-11-11)
* Update smartmeter library, fix HTTP-JSON-Transport

### 1.2.1 (2018-06-23)
* BREAKING CHANGE: State names changed because * no longer supported. Is replaced by _

### 1.1.3 (2018-04-13)
* Fix Admin

### 1.1.2 (26.03.2018)
* Add better support for devices with more then 16 values (OpenSML Library upgrade)

### 1.1.0 (31.01.2018)
* Allow multiple queries for D0 and Serial-Bidirectional communication
* a lot of bugfixing and Optimizations
* Switch to Serialport 6.0.4 to hopefully get more stable (less/no SIGSEGV/SIGABRT ...)

### 1.0.0 (25.08.2017)
* Update smartmeter library and fix some timing issues

### 0.5.12 (23.07.2017)
* update SML library

### 0.5.11 (21.06.2017)
* optimize D0 handling and add support for Dutch smartmeter using DSRM protocol.

### 0.5.8 (06.04.2017)
* optimize Serial handling on Windows (because pause and resume are not supported there)

### 0.5.6 (02.04.2017)
* update library

### 0.5.5 (19.03.2017)
* improved baudrate-changeover logic for D0 protocol (now hopefully finally)
* enhanced D0 protocol support for multiple values

### 0.5.0 (26.02.2017)
* maintenance update

### 0.4.2 (27.02.2017)
* one last try to fix the crashes SIGABRT/SIGSEGV

### 0.4.1 (24.02.2017)
* Fix potential hanging communication with D0 Serial

### 0.4.0 (23.02.2017)
* Optimize for D0 Message handling and baudrate changeovers

### 0.3.2 (22.02.2017)
* Optimize D0 protocol handling for mode E

### 0.3.1 (12.02.2017)
* Finalize Adapter config and added some informations

### 0.3.0 (11.02.2017)
* We now should be quiet stable

### 0.2.x
* Public release of Adapter after forum Tests
* remove all additional logging
* enhance Adapter config screenxw
* Add possibility to overwrite serial connections settings and also D0 Mode for devices that send a wrong identification
* update smartmeter-obis library for memory optimizations

### 0.1.1
* Update smartmeter-obis library to 0.2.5 to add Serial Timeout for Request/Response protocol

### 0.1.0
* Initial version for public testing

### 0.0.1
* Initial version for internal testing

## License

The MIT License (MIT)

Copyright (c) 2015-2018 Apollon77 <ingo@fischer-ka.de>

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.