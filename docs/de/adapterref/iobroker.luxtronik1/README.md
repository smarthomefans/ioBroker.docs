---
translatedFrom: en
translatedWarning: Wenn Sie dieses Dokument bearbeiten möchten, löschen Sie bitte das Feld "translationsFrom". Andernfalls wird dieses Dokument automatisch erneut übersetzt
editLink: https://github.com/ioBroker/ioBroker.docs/edit/master/docs/de/adapterref/iobroker.luxtronik1/README.md
title: ioBroker.luxtronik1
hash: AbUHvOwsX7KDYdFPCF20o6DlMsHDwiIBV0DhjISrSN4=
---
![Logo](../../../en/adapterref/iobroker.luxtronik1/admin/luxtronik1.png)

![Anzahl der Installationen](http://iobroker.live/badges/luxtronik1-stable.svg)
![NPM-Version](http://img.shields.io/npm/v/iobroker.luxtronik1.svg)
![Downloads](https://img.shields.io/npm/dm/iobroker.luxtronik1.svg)
![NPM](https://nodei.co/npm/iobroker.luxtronik1.png?downloads=true)

# IoBroker.luxtronik1
Ein ioBroker-Adapter für Luxtronik 1 - Wärmepumpenregler (z. B. Alpha Innotec, Siemens ...)

Adapter installieren, Instanz erstellen.
Installieren Sie die Hardware: RS232-zu-LAN-Adapter an die serielle Schnittstelle (RS232) des Hauptpumpen der Wärmepumpe.
Technische Daten: Seriennummer: Verbindungs-PINs 2, 3 und 5 (wenn dies nicht funktioniert, Pin 2 und 3 ändern). RS232-zu-LAN-Konverter: USR TCP232 - 302.
Einstellungen serielle Schnittstelle: 57600/8 / N / 1, Modus: TCP-Server Reset Timeout: 0

Setze comfoair - IP-Adresse, Port und Polling - Intervall

Getestet an luxtronik 1 und AlphaInnotec Wärmepumpe

Liest verschiedene Werte und Werte Ihrer Wärmepumpe (Temperaturen, Fehler, Laufzeit, ...).
Steuert Luxtronik 1 durch Setzen von Werten im 'Control' - Kanal. Steuert die folgenden Werte:

- Warmwassertemperatureinstellung
- Heizungsmodus
- Heißwasser - Modus
- Heizkurve (Differenz, Endpunkt, Startpunkt, nächtliche Reduktion).

Werte im 'control' - Kanal müssen mit ack = false gesetzt werden, um eine Aktion auszulösen.

## Changelog

### 0.0.7

-   error-handling on connections added.

### 0.0.6

-   diminished risk of multiple connection, small bugfixes

### 0.0.5

-   controls hotwater-temperature, heating- & hotwater - mode and heating-curve setting.

### 0.0.4

-   error - handling optimized

### 0.0.3

-   Reads mode heating, water and heating-curve

### 0.0.2

-   First published version

### 0.0.1

-   In development stage

## License

The MIT License (MIT)

Copyright (c) 2018-2019 forelleblau marceladam@gmx.ch

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in
all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN
THE SOFTWARE.