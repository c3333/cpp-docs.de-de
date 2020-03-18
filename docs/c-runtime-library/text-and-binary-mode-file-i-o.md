---
title: Text- und Binärmodusdatei-E/A
ms.date: 04/11/2018
helpviewer_keywords:
- files [C++], open functions
- I/O [CRT], text files
- functions [CRT], file access
- binary access, binary mode file I/O
- translation, modes
- I/O [CRT], binary
- text files, I/O
- I/O [CRT], translation modes
- translation modes (file I/O)
- binary access
ms.assetid: 3196e321-8b87-4609-b302-cd6f3c516051
ms.openlocfilehash: 75d302e625747d6e02e1d904c21542530d70d02f
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2020
ms.locfileid: "79444628"
---
# <a name="text-and-binary-mode-file-io"></a>Text- und Binärmodusdatei-E/A

E/A-Dateivorgänge erfolgen abhängig vom Modus, in dem die Datei geöffnet wird, in zwei Übersetzungsmodi: im *Text-* oder im *Binärmodus*. Datendateien werden in der Regel im Textmodus verarbeitet. Zur Steuerung des Dateiübersetzungsmodus können Sie Folgendes tun:

- Behalten Sie die aktuelle Standardeinstellung bei, und geben Sie den alternativen Modus nur an, wenn Sie ausgewählte Dateien öffnen.

- Verwenden Sie die Funktion [_set_fmode](../c-runtime-library/reference/set-fmode.md), um den Standardmodus für neu geöffnete Dateien zu ändern. Verwenden Sie [_get_fmode](../c-runtime-library/reference/get-fmode.md), um nach dem aktuellen Standardmodus zu suchen. Als ursprüngliche Standardeinstellung ist der Textmodus ( **_O_TEXT**) festgelegt.

- Ändern Sie direkt den Standardübersetzungsmodus, indem Sie die globale Variable [_fmode](../c-runtime-library/fmode.md) in Ihrem Programm festlegen. Die Funktion **_set_fmode** legt den Wert dieser Variable fest, er kann jedoch auch direkt festgelegt werden.

Wenn Sie eine „file-open“-Funktion (z.B. [_open](../c-runtime-library/reference/open-wopen.md), [fopen](../c-runtime-library/reference/fopen-wfopen.md), [fopen_s](../c-runtime-library/reference/fopen-s-wfopen-s.md), [freopen](../c-runtime-library/reference/freopen-wfreopen.md), [freopen_s](../c-runtime-library/reference/freopen-s-wfreopen-s.md), [_fsopen](../c-runtime-library/reference/fsopen-wfsopen.md) oder [_sopen_s](../c-runtime-library/reference/sopen-s-wsopen-s.md)) aufrufen, können Sie die aktuelle Standardeinstellung von **_fmode** überschreiben, indem Sie das entsprechende Argument in der Funktion [_set_fmode](../c-runtime-library/reference/set-fmode.md) angeben. Die Streams **stdin**, **stdout** und **stderr** werden standardmäßig immer im Textmodus geöffnet. Sie können diesen Standardwert auch überschreiben, wenn Sie eine dieser Dateien öffnen. Verwenden Sie [_setmode](../c-runtime-library/reference/setmode.md), um den Übersetzungsmodus mit dem Dateideskriptor zu ändern, nachdem die Datei geöffnet wurde.

## <a name="see-also"></a>Weitere Informationen

[Eingabe und Ausgabe](../c-runtime-library/input-and-output.md)<br/>
[Universelle C-Laufzeitroutinen nach Kategorie](../c-runtime-library/run-time-routines-by-category.md)<br/>
