---
title: _get_wpgmptr
ms.date: 4/2/2020
api_name:
- _get_wpgmptr
- _o__get_wpgmptr
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
- api-ms-win-crt-runtime-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- get_wpgmptr
- _get_wpgmptr
helpviewer_keywords:
- _wpgmptr global variable
- get_wpgmptr function
- wpgmptr global variable
- _get_wpgmptr function
ms.assetid: a77cdd13-2303-4b7c-9a60-8debdbef2011
ms.openlocfilehash: 1e54d3dbdc837c491f5b39d33a9b8197094ac60b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81344866"
---
# <a name="_get_wpgmptr"></a>_get_wpgmptr

Ruft den aktuellen Wert der **_wpgmptr** globalen Variable ab.

## <a name="syntax"></a>Syntax

```C
errno_t _get_wpgmptr(
   wchar_t **pValue
);
```

### <a name="parameters"></a>Parameter

*pValue*<br/>
Ein Zeiger auf eine Zeichenfolge, die mit dem aktuellen Wert der **_wpgmptr-Variablen** gefüllt werden soll.

## <a name="return-value"></a>Rückgabewert

Gibt 0 (null) zurück, wenn der Vorgang erfolgreich war. Wenn ein Fehler auftritt, erscheint ein Fehlercode. Wenn *pValue* **NULL**ist, wird der ungültige Parameterhandler wie unter [Parametervalidierung](../../c-runtime-library/parameter-validation.md)beschrieben aufgerufen. Wenn die Ausführung fortgesetzt werden darf, setzt diese Funktion **errno** auf **EINVAL** und gibt **EINVAL**zurück.

## <a name="remarks"></a>Bemerkungen

Rufen Sie **_get_wpgmptr** nur auf, wenn Ihr Programm über einen breiten Einstiegspunkt verfügt, z. B. **wmain()** oder **wWinMain()**. Die **globale _wpgmptr-Variable** enthält den vollständigen Pfad zur ausführbaren Datei, die dem Prozess als Zeichenfolge mit großen Zeichen zugeordnet ist. Weitere Informationen finden Sie unter [_pgmptr, _wpgmptr](../../c-runtime-library/pgmptr-wpgmptr.md).

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen dazu finden Sie [unter Globaler Status in der CRT](../global-state.md).

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|
|-------------|---------------------|
|**_get_wpgmptr**|\<stdlib.h>|

Weitere Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Siehe auch

[_get_pgmptr](get-pgmptr.md)<br/>
