---
title: Unicodestream-E/A im Text- und Binärmodus
description: Eine Beschreibung der Zeichen Konvertierungen mit Unicode-Datenstrom-e/A.
ms.topic: conceptual
ms.date: 11/04/2016
helpviewer_keywords:
- stream I/O routines
- I/O [CRT], unicode stream
- Unicode, stream I/O routines
- Unicode stream I/O
ms.assetid: 68be0c3e-a9e6-4fd5-b34a-1b5207f0e7d6
ms.openlocfilehash: 9c4ef7da54463021f9487849df0235ae289e38fa
ms.sourcegitcommit: 9451db8480992017c46f9d2df23fb17b503bbe74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/30/2020
ms.locfileid: "91590237"
---
# <a name="unicode-stream-io-in-text-and-binary-modes"></a>Unicodestream-E/A im Text- und Binärmodus

Wenn eine Unicodestream-E/A-Routine (z.B. **fwprintf**, **fwscanf**, **fgetwc**, **fputwc**, **fgetws** oder **fputws**) mit einer im Textmodus (Standard) geöffneten Datei arbeitet, finden zwei Arten von Zeichenkonvertierungen statt:

- Konvertierung von Unicode zu MBCS oder von MBCS zu Unicode. Wenn eine Unicodestream-E/A-Funktion im Textmodus arbeitet, wird angenommen, dass es sich bei Quell- oder Zielstream um eine Sequenz von Multibytezeichen handelt. Daher konvertieren die Unicode-Streameingabefunktionen Multibytezeichen in Breitzeichen (wie bei einem Aufruf der **mbtowc**-Funktion). Aus demselben Grund konvertieren die Unicode-Streamausgabefunktionen Breitzeichen in Multibytezeichen (wie bei einem Aufruf der **wctomb**-Funktion).

- Übersetzung von Wagenrücklauf-Zeilenvorschub (CR-LF) Diese Übersetzung findet vor der MBCS-Unicode-Konvertierung (für Unicode-Streameingabefunktionen) und nach der Unicode-MBCS-Konvertierung (für Unicode-Streamausgabefunktionen) statt. Bei der Eingabe wird jede Kombination aus Wagenrücklauf und Zeilenvorschub in ein einzelnes Zeilenvorschubzeichen übersetzt. Bei der Ausgabe wird jedes Zeilenvorschubzeichen in eine Kombination aus Wagenrücklauf und Zeilenvorschub übersetzt.

Wenn jedoch eine Unicodestream-E/A-Funktion im binären Modus arbeitet, wir von einer Unicode-Datei ausgegangen und es erfolgt keine CR-LF-Übersetzung oder Zeichenkonvertierung während der Ein- und Ausgabe. Verwenden Sie die `_setmode( _fileno( stdin ), _O_BINARY );`-Anweisung, um `wcin` ordnungsgemäß für eine UNICODE-Textdatei zu verwenden.

## <a name="see-also"></a>Weitere Informationen

[Universelle C-Laufzeitroutinen nach Kategorie](../c-runtime-library/run-time-routines-by-category.md)<br/>
[Eingabe und Ausgabe](../c-runtime-library/input-and-output.md)<br/>
