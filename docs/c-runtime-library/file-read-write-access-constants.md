---
title: Datei-Lese-/Schreibzugriffskonstanten
ms.date: 11/04/2016
helpviewer_keywords:
- read/write access constants
- write access constants
- access constants for file read/write
- constants [C++], file attributes
- file read/write access constants
ms.assetid: 56cd1d22-39a5-4fcf-bea2-7046d249e8ee
ms.openlocfilehash: 96d146b2e2f0ed82cbdc52b11d92c049da50e2cb
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2020
ms.locfileid: "79438390"
---
# <a name="file-readwrite-access-constants"></a>Datei-Lese-/Schreibzugriffkonstanten

## <a name="syntax"></a>Syntax

```
#include <stdio.h>
```

## <a name="remarks"></a>Bemerkungen

Diese Konstanten geben den Zugriffstyp für die angeforderte Datei an („a“, „r“ oder „w“). Sowohl der [Übersetzungsmodus](../c-runtime-library/file-translation-constants.md) („b“ oder „t“) als auch der [commit-to-disk-mode](../c-runtime-library/commit-to-disk-constants.md) („c“ oder „n“) kann mit dem Zugriffstyp angegeben werden.

Die Zugriffstypen werden in der nachfolgenden Tabelle beschrieben:

|Zugriffstyp|BESCHREIBUNG|
|----------|----------------|
|**"r"**|Öffnet zum Lesen. Wenn die Datei nicht vorhanden ist oder nicht gefunden werden kann, tritt beim Aufruf zum Öffnen der Datei ein Fehler auf.|
|**"w"**|Öffnet eine leere Datei zum Schreiben. Wenn die angegebene Datei vorhanden ist, wird ihr Inhalt zerstört.|
|**„a“**|Öffnet zum Schreiben am Ende der Datei (Anfügen); erstellt die Datei zuerst, wenn sie nicht vorhanden ist. Alle Schreibvorgänge erfolgen am Ende der Datei. Der Dateizeiger kann mit `fseek` oder `rewind` neu angeordnet werden, er wird jedoch immer wieder zurück an das Ende der Datei verschoben, bevor ein Schreibvorgang durchgeführt wird. |
|**„r+“**|Öffnet sowohl zum Lesen als auch zum Schreiben. Wenn die Datei nicht vorhanden ist oder nicht gefunden werden kann, tritt beim Aufruf zum Öffnen der Datei ein Fehler auf.|
|**„w+“**|Öffnet eine leere Datei zum Lesen und Schreiben. Wenn die angegebene Datei vorhanden ist, wird ihr Inhalt zerstört.|
|**„a+“**|Wie **„a“** , erlaubt jedoch auch Lesevorgänge.|

Wenn als Typ „r+“, „w+“ oder „a+“ angegeben wird, sind sowohl Lese- als auch Schreibvorgänge zulässig (die Datei ist zum Aktualisieren geöffnet). Wenn Sie jedoch zwischen Lesen und Schreiben wechseln, muss ein sich dazwischen befindender Vorgang wie `fflush`, `fsetpos`, `fseek` oder `rewind` vorhanden sein. Die aktuelle Position kann für den Vorgang `fsetpos` oder `fseek` angegeben werden.

## <a name="see-also"></a>Weitere Informationen

[_fdopen, _wfdopen](../c-runtime-library/reference/fdopen-wfdopen.md)<br/>
[fopen, _wfopen](../c-runtime-library/reference/fopen-wfopen.md)<br/>
[freopen, _wfreopen](../c-runtime-library/reference/freopen-wfreopen.md)<br/>
[_fsopen, _wfsopen](../c-runtime-library/reference/fsopen-wfsopen.md)<br/>
[_popen, _wpopen](../c-runtime-library/reference/popen-wpopen.md)<br/>
[Global Constants (Globale Konstanten)](../c-runtime-library/global-constants.md)
