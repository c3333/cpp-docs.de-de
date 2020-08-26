---
title: Übersetzungsmoduskonstanten
ms.date: 11/04/2016
f1_keywords:
- _O_BINARY
- _O_TEXT
- _O_RAW
helpviewer_keywords:
- O_BINARY constant
- O_TEXT constant
- O_RAW constant
- _O_TEXT constant
- _O_RAW constant
- translation constants
- _O_BINARY constant
- translation, constants
- translation, modes
- translation modes (file I/O)
ms.assetid: a5993bf4-7e7a-47f9-83c3-e46332b85579
ms.openlocfilehash: 0b951fc76635f67115f4a832ed316d66b6de7497
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88836698"
---
# <a name="translation-mode-constants"></a>Übersetzungsmoduskonstanten

## <a name="syntax"></a>Syntax

```
#include <fcntl.h>
```

## <a name="remarks"></a>Bemerkungen

Die Manifestkonstanten `_O_BINARY` und `_O_TEXT` geben den Übersetzungsmodus von Dateien (`_open` und `_sopen`) oder von Streams (`_setmode`) an.

Zulässige Werte sind:

|Wert|Beschreibung|
|-|-|
`_O_TEXT`  | Öffnet eine Datei im Textmodus (übersetzt). Kombinationen aus Wagenrücklauf und Zeilenvorschub (CR-LF) werden bei der Eingabe in einen einzelnen Zeilenvorschub (LF) umgewandelt. Zeilenvorschubzeichen werden bei der Ausgabe in Kombinationen aus Wagenrücklauf und Zeilenvorschub (CR-LF) übersetzt. Außerdem wird STRG+Z bei der Eingabe als EOF-Zeichen interpretiert. In den Dateien, die für das Lesen und Lesen/Schreiben geöffnet sind, überprüft `fopen` die Datei auf STRG+Z am Dateiende und entfernt nach Möglichkeit die Markierung. Dies geschieht, da ein Verwenden der Funktionen `fseek` und `ftell` zum Navigieren innerhalb einer Datei, die mit STRG + Z endet, dazu führen kann, dass sich `fseek` in der Nähe des Dateiendes nicht ordnungsgemäß verhält.
`_O_BINARY`  | Öffnet eine Datei im binären (unübersetzten) Modus. Die oben genannten Übersetzungen werden unterdrückt.
`_O_RAW`  | Wie in `_O_BINARY`. Für Kompatibilität mit C 2.0 unterstützt.

Weitere Informationen finden Sie unter [Text- und Binärmodus-Datei-E-A](../c-runtime-library/text-and-binary-mode-file-i-o.md) und [Dateiübersetzung](../c-runtime-library/file-translation-constants.md).

## <a name="see-also"></a>Weitere Informationen

[_open, _wopen](../c-runtime-library/reference/open-wopen.md)<br/>
[_pipe](../c-runtime-library/reference/pipe.md)<br/>
[_sopen, _wsopen](../c-runtime-library/reference/sopen-wsopen.md)<br/>
[_setmode](../c-runtime-library/reference/setmode.md)<br/>
[Globale Konstanten](../c-runtime-library/global-constants.md)
