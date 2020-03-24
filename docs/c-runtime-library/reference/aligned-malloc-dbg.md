---
title: _aligned_malloc_dbg
ms.date: 11/04/2016
api_name:
- _aligned_malloc_dbg
api_location:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _aligned_malloc_dbg
- aligned_malloc_dbg
helpviewer_keywords:
- aligned_malloc_dbg function
- _aligned_malloc_dbg function
ms.assetid: fb0429c3-685d-4826-9075-2515c5bdc5c6
ms.openlocfilehash: 49278c2282698478ad96cc1c7b1ad27add0a6787
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80170935"
---
# <a name="_aligned_malloc_dbg"></a>_aligned_malloc_dbg

Belegt einen Speicherblock in einer angegebenen Ausrichtungsgrenze mit zusätzlichem Speicherplatz für einen Debugheader und Überschreibungspuffer (nur Debugversion).

## <a name="syntax"></a>Syntax

```C
void * _aligned_malloc_dbg(
    size_t size,
    size_t alignment,
   const char *filename,
   int linenumber
);
```

### <a name="parameters"></a>Parameter

*size*<br/>
Größe der angeforderten Speicherzuweisung.

*Richt*<br/>
Der Zuweisungswert, muss eine ganzzahlige Potenz von 2 sein.

*filename*<br/>
Zeiger zum Namen der Quelldatei, der die Belegung angefordert hat, oder NULL.

*linenumber*<br/>
Zeilennummer in der Quelldatei, in der die Belegung angefordert wurde, oder NULL.

## <a name="return-value"></a>Rückgabewert

Ein Zeiger auf den Speicherblock, der zugeordnet wurde, oder NULL, wenn der Vorgang fehlgeschlagen ist.

## <a name="remarks"></a>Bemerkungen

**_aligned_malloc_dbg** ist eine Debugversion der [_aligned_malloc](aligned-malloc.md) -Funktion. Wenn [_DEBUG](../../c-runtime-library/debug.md) nicht definiert ist, wird jeder **_aligned_malloc_dbg** Aufrufe auf einen `_aligned_malloc`aufrufenden Wert reduziert. Sowohl `_aligned_malloc` als auch **_aligned_malloc_dbg** belegen einen Speicherblock im Basisheap, aber **_aligned_malloc_dbg** bietet mehrere Debugfunktionen: Puffer auf beiden Seiten des Benutzer Teils des Blocks zum Prüfen auf Speicher Verluste und *Dateiname*/*LineNumber* -Informationen, um den Ursprung von Zuordnungs Anforderungen zu bestimmen. Das Nachverfolgen spezifischer Zuordnungs Typen mit einem Blocktyp Parameter ist keine unterstützte Debugfunktion für ausgerichtete Zuordnungen. Ausgerichtete Zuordnungen werden als _NORMAL_BLOCK Blocktyp angezeigt.

**_aligned_malloc_dbg** ordnet den Speicherblock mit etwas mehr Speicherplatz als die angeforderte *Größe*zu. Der zusätzliche Speicherplatz wird vom Debugheapmanager verwendet, um die Debugspeicherblöck zu verknüpfen und Debugheaderinformationen und Überschreibungspuffer für die Anwendung bereitzustellen. Wenn der Block belegt wurde, wird der Benutzerteil des Blocks mit dem Wert "0xCD" gefüllt, und jeder der Überschreibungspuffer wird mit "0xFD" gefüllt.

**_aligned_malloc_dbg** legt `errno` auf `ENOMEM` fest, wenn eine Speicher Belegung fehlschlägt oder wenn der benötigte Speicherplatz (einschließlich des bereits erwähnten Mehraufwands) `_HEAP_MAXREQ`überschreitet. Informationen hierzu und über andere Fehlercodes finden Sie unter [errno, _doserrno, _sys_errlist, and _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md). Außerdem überprüft **_aligned_malloc_dbg** seine Parameter. Wenn die *Ausrichtung* keine Potenz von 2 ist oder die *Größe* 0 (null) ist, ruft diese Funktion den Handler für ungültige Parameter auf, wie unter [Parameter Validierung](../../c-runtime-library/parameter-validation.md)beschrieben. Wenn die weitere Ausführung zugelassen wird, gibt diese Funktion NULL zurück und legt `errno` auf `EINVAL`fest.

Informationen dazu, wie Speicherblöcke in der Debugversion des Basisheaps zugeordnet, initialisiert und verwaltet werden, finden Sie unter [Details zum CRT-Debugheap](/visualstudio/debugger/crt-debug-heap-details). Informationen zu den Belegungsblocktypen und ihrer Verwendung finden Sie unter [Blocktypen auf dem Debugheap](/visualstudio/debugger/crt-debug-heap-details). Informationen zu den Unterschieden zwischen dem Aufruf einer Standardheapfunktion und der Debugversion in einem Debugbuild finden Sie unter [Debugversionen von Heapreservierungsfunktionen](/visualstudio/debugger/debug-versions-of-heap-allocation-functions).

## <a name="requirements"></a>Requirements (Anforderungen)

|Routine|Erforderlicher Header|
|-------------|---------------------|
|**_aligned_malloc_dbg**|\<crtdbg.h>|

Weitere Informationen zur Kompatibilität finden Sie unter [Kompatibilität](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliotheken

Nur Debugversionen von [C-Laufzeitbibliotheken](../../c-runtime-library/crt-library-features.md).

## <a name="see-also"></a>Weitere Informationen

[Debugroutinen](../../c-runtime-library/debug-routines.md)
