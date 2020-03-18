---
title: Unicodestream-E/A im Text- und Binärmodus
ms.date: 11/04/2016
helpviewer_keywords:
- stream I/O routines
- I/O [CRT], unicode stream
- Unicode, stream I/O routines
- Unicode stream I/O
ms.assetid: 68be0c3e-a9e6-4fd5-b34a-1b5207f0e7d6
ms.openlocfilehash: b41818bbb625a8c875771e86e3d82b74f4291e9f
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2020
ms.locfileid: "79444506"
---
# <a name="unicode-stream-io-in-text-and-binary-modes"></a>Unicodestream-E/A im Text- und Binärmodus

Wenn eine Unicodestream-E/A-Routine (z.B. **fwprintf**, **fwscanf**, **fgetwc**, **fputwc**, **fgetws** oder **fputws**) mit einer im Textmodus (Standard) geöffneten Datei arbeitet, finden zwei Arten von Zeichenkonvertierungen statt:

- Konvertierung von Unicode zu MBCS oder von MBCS zu Unicode. Wenn eine Unicodestream-E/A-Funktion im Textmodus arbeitet, wird angenommen, dass es sich bei Quell- oder Zielstream um eine Sequenz von Multibytezeichen handelt. Daher konvertieren die Unicode-Streameingabefunktionen Multibytezeichen in Breitzeichen (wie bei einem Aufruf der **mbtowc**-Funktion). Aus demselben Grund konvertieren die Unicode-Streamausgabefunktionen Breitzeichen in Multibytezeichen (wie bei einem Aufruf der **wctomb**-Funktion).

- Übersetzung von Wagenrücklauf-Zeilenvorschub (CR-LF) Diese Übersetzung findet vor der MBCS-Unicode-Konvertierung (für Unicode-Streameingabefunktionen) und nach der Unicode-MBCS-Konvertierung (für Unicode-Streamausgabefunktionen) statt. Bei der Eingabe wird jede Kombination aus Wagenrücklauf und Zeilenvorschub in ein einzelnes Zeilenvorschubzeichen übersetzt. Bei der Ausgabe wird jedes Zeilenvorschubzeichen in eine Kombination aus Wagenrücklauf und Zeilenvorschub übersetzt.

Wenn jedoch eine Unicodestream-E/A-Funktion im binären Modus arbeitet, wir von einer Unicode-Datei ausgegangen und es erfolgt keine CR-LF-Übersetzung oder Zeichenkonvertierung während der Ein- und Ausgabe. Verwenden Sie die `_setmode( _fileno( stdin ), _O_BINARY );`-Anweisung, um `wcin` ordnungsgemäß für eine UNICODE-Textdatei zu verwenden.

## <a name="see-also"></a>Weitere Informationen

[Universelle C-Laufzeitroutinen nach Kategorie](../c-runtime-library/run-time-routines-by-category.md)<br/>
[Eingabe und Ausgabe](../c-runtime-library/input-and-output.md)<br/>
