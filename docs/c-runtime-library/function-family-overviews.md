---
title: Übersicht über die Funktions Familie
description: Eine Übersicht über die Microsoft C-Lauf Zeitfunktionen nach Familie.
ms.date: 10/05/2020
ms.assetid: b05a2755-9d11-4ea9-ab97-d00a4e872e16
ms.openlocfilehash: de5192cd03c3821afc646241d75a3e8c6c8c12e3
ms.sourcegitcommit: 8caaf5e00aeb727741a273aecafa15de293426cf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/07/2020
ms.locfileid: "91806512"
---
# <a name="function-family-overview"></a>Übersicht über die Funktions Familie

In diesem Abschnitt werden C-Lauf Zeit Bibliotheks Routinen nach Funktions Familie aufgelistet.

## <a name="crt-library-routine-families"></a>CRT-Bibliotheks Routine Familien

[_exec _wexec](exec-wexec-functions.md)\
Funktionen zum Laden und Ausführen eines neuen Prozesses.

[Dateinamen-Suchfunktionen](filename-search-functions.md)\
Funktionen zum Suchen nach angegebenen Dateinamen und zum Schließen von Such Vorgängen.

[Formatspezifikations Syntax für `printf` und `wprintf`](format-specification-syntax-printf-and-wprintf-functions.md)\
Beschreibt die Format Zeichenfolge und Argumente für `printf` und `wprintf` .

[Formatspezifikations-Feldzeichen: `scanf` und `wscanf`](format-specification-fields-scanf-and-wscanf-functions.md)\
Beschreibt die formatspezifikations Felder zum Auswerten eines Eingabedaten Stroms für die gesamte `scanf` Funktions Familie.

[`is`, `isw` Funktionen](is-isw-routines.md)\
Funktionen zum Testen von Zeichen, z. b. ob es sich um Großbuchstaben, ASCII, numerisch, Interpunktions Zeichen usw. handelt.

[`_ismbb` Funktionen](ismbb-routines.md)\
Funktionen zum Testen eines ganzzahligen Werts, der angibt, ob es sich um ein Alpha Zeichen, ein leeres Zeichen, ein Druck Zeichen usw. handelt.

[`_ismbc` Funktionen](ismbc-routines.md)\
Funktionen zum Testen eines multibytezeichens für die Darstellung eines Alpha Zeichens, eines leeren Zeichens, eines Druck Zeichens usw.

[Operator `delete` (CRT)](delete-operator-crt.md)\
Ab Visual Studio 2013 unterstützt die universelle C-Laufzeit (ucrt) nicht mehr die C++-spezifische Operator Delete-Funktion. Sie ist nun Teil der C++-Standard Bibliothek.

[Operator `new` (CRT)](new-operator-crt.md)\
Ab Visual Studio 2013 unterstützt die universelle C-Laufzeit (ucrt) nicht mehr die C++-spezifische Operator new-Funktion. Sie ist nun Teil der C++-Standard Bibliothek.

[`printf` Positions Parameter Funktionen](printf-p-positional-parameters.md)\
Positions Parameter geben nach Zahl an, welche der Argumente in einem Feld in einer Format Zeichenfolge ersetzt werden sollen.

[`scanf` typfeldzeichen](scanf-type-field-characters.md)\
Das Typzeichen bestimmt, ob das zugeordnete Argument als Zeichen, Zeichenfolge oder Zahl für eine beliebige `scanf` Funktions Familie interpretiert wird, einschließlich der sicheren Versionen wie z. b `scanf_s` ..

[`scanf` breiten Angabe](scanf-width-specification.md)\
Das Width-Feld ist eine positive ganze Dezimalzahl, die die maximale Anzahl von Zeichen steuert, die für dieses Feld gelesen werden sollen. Gilt für jede der- `scanf` Funktionen, einschließlich der sicheren Versionen wie `scanf_s` .

[_spawn, _wspawn Funktionen](spawn-wspawn-functions.md)\
Funktionen zum Erstellen und Ausführen eines neuen Prozesses.

[`strcoll` Funktionen](strcoll-functions.md)\
Die `strcoll` `wcscoll` Funktionen und vergleichen zwei Zeichen folgen gemäß der- `LC_COLLATE` Kategorieeinstellung der Gebiets Schema-Codepage.

[Funktionen für Zeichen folgen in numerische Werte](string-to-numeric-value-functions.md)\
Die `strtod` -Funktions Familie konvertiert eine NULL-terminierte Zeichenfolge in einen numerischen Wert.

[`vprintf` Funktionen](vprintf-functions.md)\
Die- `vprintf` Funktionen übernehmen einen Zeiger auf eine Argumentliste, formatiert Sie und schreiben das Ergebnis in das angegebene Ziel. Die-Funktionen unterscheiden sich in der ausgeführten Parameter Validierung, unabhängig davon, ob Sie breit-oder Einzel Byte-Zeichen folgen, das Ausgabeziel und Unterstützung für die Angabe der Reihenfolge verwenden, in der Parameter in der Format Zeichenfolge verwendet werden

## <a name="see-also"></a>Weitere Informationen

[C-Lauf Zeit Bibliotheks Referenz](c-run-time-library-reference.md)