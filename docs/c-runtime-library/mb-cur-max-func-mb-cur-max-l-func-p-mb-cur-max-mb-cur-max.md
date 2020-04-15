---
title: ___mb_cur_max_func, ___mb_cur_max_l_func, __p___mb_cur_max, __mb_cur_max
ms.date: 4/2/2020
api_name:
- ___mb_cur_max_l_func
- __p___mb_cur_max
- ___mb_cur_max_func
- __mb_cur_max
- _o____mb_cur_max_func
api_location:
- msvcr110_clr0400.dll
- msvcr110.dll
- msvcr80.dll
- msvcr100.dll
- msvcrt.dll
- msvcr90.dll
- msvcr120.dll
- api-ms-win-crt-locale-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- ___mb_cur_max_func
- ___mb_cur_max_l_func
- __p___mb_cur_max
- __mb_cur_max
helpviewer_keywords:
- __mb_cur_max
- ___mb_cur_max_func
- ___mb_cur_max_l_func
- __p___mb_cur_max
ms.assetid: 60d36108-1ca7-45a6-8ce7-68a91f13e3a1
ms.openlocfilehash: f9b9e2d903bb05f5b1b653b4fb51c57b354d4126
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81351083"
---
# <a name="___mb_cur_max_func-___mb_cur_max_l_func-__p___mb_cur_max-__mb_cur_max"></a>___mb_cur_max_func, ___mb_cur_max_l_func, __p___mb_cur_max, __mb_cur_max

Interne CRT-Funktion. Ruft die maximale Anzahl von Bytes in einem Multibyte-Zeichen für das aktuelle oder ein angegebenes Gebietsschema ab.

## <a name="syntax"></a>Syntax

```cpp
int ___mb_cur_max_func(void);
int ___mb_cur_max_l_func(_locale_t locale);
int * __p___mb_cur_max(void);
#define __mb_cur_max (___mb_cur_max_func())
```

#### <a name="parameters"></a>Parameter

locale: Die Struktur des Gebietsschemas, aus dem das Ergebnis abgerufen werden soll. Wenn dieser Wert null ist, wird das Gebietsschema des aktuellen Threads verwendet.

## <a name="return-value"></a>Rückgabewert

Die maximale Anzahl von Bytes in einem Multibyte-Zeichen für das Gebietsschema des aktuelles Threads oder das angegebene Gebietsschema.

## <a name="remarks"></a>Bemerkungen

Dies ist eine interne Funktion, die CRT nutzt, um den aktuellen Wert des Makros [MB_CUR_MAX](../c-runtime-library/mb-cur-max.md) aus dem lokalen Threadspeicher abzurufen. Wir empfehlen, das Makro `MB_CUR_MAX` in Ihrem Code für Übertragbarkeit zu nutzen.

Das Makro `__mb_cur_max` ist ein bequemer Weg zum Aufrufen der Funktion `___mb_cur_max_func()`. Die Funktion `__p___mb_cur_max` ist für eine Kompatibilität mit Visual C++ 5.0 und früheren Versionen definiert.

Interne CRT-Funktionen sind implementierungsspezifisch und mit jedem neuen Release Änderungen unterworfen. Ihre Verwendung in einem Code wird nicht empfohlen.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen dazu finden Sie [unter Globaler Status in der CRT](global-state.md).

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|
|-------------|---------------------|
|`___mb_cur_max_func`, `___mb_cur_max_l_func`, `__p___mb_cur_max`|\<ctype.h>, \<stdlib.h>|

## <a name="see-also"></a>Siehe auch

[MB_CUR_MAX](../c-runtime-library/mb-cur-max.md)
