---
title: DUMPBIN-Optionen
description: Referenzhandbuch zu den Befehlszeilenoptionen für das Microsoft DUMPBIN-Hilfsprogramm.
ms.date: 02/09/2020
helpviewer_keywords:
- DUMPBIN program, options
ms.assetid: 563b696e-7599-4480-94b9-014776289ec8
ms.openlocfilehash: 54f5a22808026f4442f85d5e53a0805702e05868
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2020
ms.locfileid: "79440039"
---
# <a name="dumpbin-options"></a>DUMPBIN-Optionen

Eine Option besteht aus einem *optionsspezifizierer*, bei dem es sich entweder um einen Bindestrich (`-`) oder einen Schrägstrich (`/`) handelt, gefolgt vom Namen der Option. Optionsnamen können nicht abgekürzt werden. Einige Optionen übernehmen Argumente, die nach einem Doppelpunkt (`:`) angegeben sind. Innerhalb einer Optionsangabe sind keine Leerzeichen oder Tabstopps zulässig. Verwenden Sie eines oder mehrere Leerzeichen bzw. Tabstopps, um Optionsangaben in der Befehlszeile voneinander zu trennen. Bei Optionsnamen und Schlüsselwörtern oder Dateinamen Argumenten wird die Groß-/Kleinschreibung nicht beachtet. Die meisten Optionen gelten für alle Binärdateien, aber ein paar gilt nur für bestimmte Dateitypen. Standardmäßig sendet DUMPBIN die Informationen an die Standardausgabe. Verwenden Sie die Option [/out](out-dumpbin.md) , um die Ausgabe an eine Datei zu senden.

## <a name="options-list"></a>Options Liste

DUMPBIN hat die folgenden Optionen:

- [/ALL](all.md)

- [/ARCHIVEMEMBERS](archivemembers.md)

- [/CLRHEADER](clrheader.md)

- [/DEPENDENTS](dependents.md)

- [/DIRECTIVES](directives.md)

- [/DISASM\[: {Bytes\|nobytes}\]](disasm.md)

- [/errorreport: {None | Eingabeaufforderung | Warteschlange | Send}](errorreport-dumpbin-exe.md) (veraltet)

- [/EXPORTS](dash-exports.md)

- [/FPO](fpo.md)

- [/HEADERS](headers.md)

- [/Imports\[: Dateiname\]](imports-dumpbin.md)

- [/LINENUMBERS](linenumbers.md)

- [/LINKERMEMBER\[: {1 | 2}\]](linkermember.md)

- [/LOADCONFIG](loadconfig.md)

- [/NOPDB](nopdb.md)

- [/Out: Dateiname](out-dumpbin.md)

- [/PDATA](pdata.md)

- [/PDBPATH\[: Ausführliche\]](pdbpath.md)

- [/RANGEE: vamin\[, vamax\]](range.md)

- [/RawData\[: {None\|1\|2\|4\|8}\[, #\]\]](rawdata.md)

- [/RELOCATIONS](relocations.md)

- [/Section: Name](section-dumpbin.md)

- [/SUMMARY](summary.md)

- [/SYMBOLS](symbols.md)

- [/TLS](tls.md)

Verwenden Sie zum Auflisten der Optionen, die von DUMPBIN in der Befehlszeile unterstützt werden, das **/?** Option.

## <a name="see-also"></a>Weitere Informationen

[Zusätzliche MSVC-Buildtools](c-cpp-build-tools.md)\
[DUMPBIN-Befehlszeilen](dumpbin-command-line.md)\
[DUMPBIN-Referenz](dumpbin-reference.md)
