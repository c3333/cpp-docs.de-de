---
title: _CrtSetDumpClient
ms.date: 11/04/2016
api_name:
- _CrtSetDumpClient
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
- _CrtSetDumpClient
- CrtSetDumpClient
helpviewer_keywords:
- _CrtSetDumpClient function
- CrtSetDumpClient function
ms.assetid: f3dd06d0-c331-4a12-b68d-25378d112033
ms.openlocfilehash: fd2b037ce10f708ab133f31a20636438b0d04b93
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87234262"
---
# <a name="_crtsetdumpclient"></a>_CrtSetDumpClient

Installiert eine Anwendungs definierte Funktion zum Sichern von **_CLIENT_BLOCK** -Typspeicher Blöcken (nur Debugversion).

## <a name="syntax"></a>Syntax

```C
_CRT_DUMP_CLIENT _CrtSetDumpClient( _CRT_DUMP_CLIENT dumpClient );
```

### <a name="parameters"></a>Parameter

*dumpclient*<br/>
Die neue clientdefinierte Speicherabbildfunktion, die mit dem Debug-Speicherabbildprozess der C-Laufzeit verknüpft werden soll.

## <a name="return-value"></a>Rückgabewert

Gibt die zuvor definierte Client-Blockdumpfunktion zurück.

## <a name="remarks"></a>Bemerkungen

Die **_CrtSetDumpClient** -Funktion ermöglicht es der Anwendung, eine eigene Funktion anzuhostecken, um in **_CLIENT_BLOCK** Speicherblöcken gespeicherte Objekte in den Debug-Speicher Abbild Prozess der C-Laufzeit zu sichern. Daher wird jedes Mal, wenn eine debugdumpfunktion wie [_CrtMemDumpAllObjectsSince](crtmemdumpallobjectssince.md) oder [_CrtDumpMemoryLeaks](crtdumpmemoryleaks.md) einen **_CLIENT_BLOCK** Speicher Block absichert, die dumpfunktion der Anwendung ebenfalls aufgerufen. **_CrtSetDumpClient** bietet einer Anwendung eine einfache Methode zum Erkennen von Speicher Verlusten und zum Überprüfen oder melden des Inhalts von Daten, die in **_CLIENT_BLOCK** Blöcken gespeichert sind. Wenn [_DEBUG](../../c-runtime-library/debug.md) nicht definiert ist, werden Aufrufe von **_CrtSetDumpClient** während der Vorverarbeitung entfernt.

Die **_CrtSetDumpClient** -Funktion installiert die neue Anwendungs definierte dumpfunktion, die in *dumpclient* angegeben ist, und gibt die zuvor definierte dumpfunktion zurück. Beispiel einer Client-Blockdumpfunktion:

```C
void DumpClientFunction( void *userPortion, size_t blockSize );
```

Das *usertteil* -Argument ist ein Zeiger auf den Anfang des Benutzerdaten Teils des Speicherblocks, und *BLOCKSIZE* gibt die Größe des belegten Speicherblocks in Bytes an. Die Client-blockdumpfunktion muss zurückgeben **`void`** . Der Zeiger auf die clientdumpfunktion, die an **_CrtSetDumpClient** übermittelt wird, ist vom Typ **_CRT_DUMP_CLIENT**, wie in CRTDBG. h definiert:

```C
typedef void (__cdecl *_CRT_DUMP_CLIENT)( void *, size_t );
```

Weitere Informationen zu Funktionen, die auf **_CLIENT_BLOCK** Typen von Speicherblöcken angewendet werden, finden Sie unter Hookfunktionen für [Client Blöcke](/visualstudio/debugger/client-block-hook-functions). Die [_CrtReportBlockType](crtreportblocktype.md)-Funktion kann zum Zurückgeben von Informationen zu Blocktypen und -untertypen verwendet werden.

## <a name="requirements"></a>Anforderungen

|-Routine zurückgegebener Wert|Erforderlicher Header|
|-------------|---------------------|
|**_CrtSetDumpClient**|\<crtdbg.h>|

Weitere Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliotheken

Nur Debugversionen der [C-Laufzeitbibliotheken](../../c-runtime-library/crt-library-features.md).

## <a name="see-also"></a>Siehe auch

[Debugroutinen](../../c-runtime-library/debug-routines.md)<br/>
[_CrtReportBlockType](crtreportblocktype.md)<br/>
[_CrtGetDumpClient](crtgetdumpclient.md)<br/>
