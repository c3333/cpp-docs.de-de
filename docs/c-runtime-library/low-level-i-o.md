---
title: E/A auf niedriger Ebene
ms.date: 11/04/2016
helpviewer_keywords:
- I/O [CRT], low-level
- I/O [CRT], functions
- low-level I/O routines
- file handles [C++]
- file handles [C++], I/O functions
ms.assetid: 53e11bdd-6720-481c-8b2b-3a3a569ed534
ms.openlocfilehash: acf07682e9045800bb04aa4c9d6abc5ae4376280
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2020
ms.locfileid: "79443099"
---
# <a name="low-level-io"></a>E/A auf niedriger Ebene

Diese Funktionen rufen direkt das Betriebssystem für einen Vorgang auf, der sich auf einer niedrigeren Ebene befindet als der durch Stream-E/A bereitgestellte Vorgang. Eingabe- und Ausgabeaufrufe auf niedriger Ebene puffern oder formatieren keine Daten.

Routinen auf niedriger Ebene können mit den folgenden vordefinierten Dateideskriptoren auf Standardstreams zugreifen, die beim Programmstart geöffnet werden.

|STREAM|Dateideskriptor|
|------------|---------------------|
|**stdin**|0|
|**stdout**|1|
|**stderr**|2|

E/A-Routinen auf niedriger Ebene legen die globale Variable [errno](../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) fest, wenn ein Fehler auftritt. Sie müssen nur dann STDIO.H bei der Verwendung von Funktionen auf niedriger Ebene einschließen, wenn das Programm eine in STDIO.H definierte Konstante erfordert, z.B. den Indikator für das Dateiende (**EOF**).

## <a name="low-level-io-functions"></a>E/A-Funktionen auf niedriger Ebene

|Funktion|Zweck|
|--------------|---------|
|[_close](../c-runtime-library/reference/close.md)|Datei schließen|
|[_commit](../c-runtime-library/reference/commit.md)|Datei auf Datenträger leeren|
|[_creat, _wcreat](../c-runtime-library/reference/creat-wcreat.md)|Datei erstellen|
|[_dup](../c-runtime-library/reference/dup-dup2.md)|Nächsten verfügbaren Dateideskriptor für eine angegebene Datei zurückgeben|
|[_dup2](../c-runtime-library/reference/dup-dup2.md)|Zweiten Deskriptor erstellen, für die angegebenen Datei erstellen|
|[_eof](../c-runtime-library/reference/eof.md)|Dateiende prüfen|
|[_lseek, _lseeki64](../c-runtime-library/reference/lseek-lseeki64.md)|Position des Dateizeigers auf einen angegebenen Speicherort ändern|
|[_open, _wopen](../c-runtime-library/reference/open-wopen.md)|Datei öffnen|
|[_read](../c-runtime-library/reference/read.md)|Daten von Datei lesen|
|[_sopen, _wsopen](../c-runtime-library/reference/sopen-wsopen.md), [_sopen_s, _wsopen_s](../c-runtime-library/reference/sopen-s-wsopen-s.md)|Datei für die Dateifreigabe öffnen|
|[_tell, _telli64](../c-runtime-library/reference/tell-telli64.md)|Aktuelle Dateizeigerposition abrufen|
|[_umask](../c-runtime-library/reference/umask.md), [_umask_s](../c-runtime-library/reference/umask-s.md)|Dateiberechtigungsmaske festlegen|
|[_write](../c-runtime-library/reference/write.md)|Daten in Datei schreiben|

**_dup** und **_dup2** werden im Allgemeinen verwendet, um verschiedenen Dateien die vordefinierten Dateideskriptoren zuzuordnen.

## <a name="see-also"></a>Weitere Informationen

[Eingabe und Ausgabe](../c-runtime-library/input-and-output.md)<br/>
[Universelle C-Laufzeitroutinen nach Kategorie](../c-runtime-library/run-time-routines-by-category.md)<br/>
[Systemaufrufe](../c-runtime-library/system-calls.md)<br/>
