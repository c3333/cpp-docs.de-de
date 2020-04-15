---
title: isgraph, iswgraph, _isgraph_l, _iswgraph_l
ms.date: 4/2/2020
api_name:
- isgraph
- iswgraph
- _iswgraph_l
- _isgraph_l
- _o_isgraph
- _o_iswgraph
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
- api-ms-win-crt-string-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _isgraph_l
- _iswgraph_l
- Isgraph
- _istgraph_l
- _istgraph
- iswgraph
helpviewer_keywords:
- isgraph function
- _istgraph_l function
- istgraph function
- _isgraph_l function
- iswgraph function
- _iswgraph_l function
- _istgraph function
- _ismbcgraph_l function
ms.assetid: 531a5f34-4302-4d0a-8a4f-b7ea150ad941
ms.openlocfilehash: b10038a783f05512f12f25a231dd553a1863c143
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81343827"
---
# <a name="isgraph-iswgraph-_isgraph_l-_iswgraph_l"></a>isgraph, iswgraph, _isgraph_l, _iswgraph_l

Bestimmt, ob eine ganze Zahl ein Grafikzeichen darstellt.

## <a name="syntax"></a>Syntax

```C
int isgraph(
   int c
);
int iswgraph(
   wint_t c
);
int _isgraph_l(
   int c,
   _locale_t locale
);
int _iswgraph_l(
   wint_t c,
   _locale_t locale
);
```

### <a name="parameters"></a>Parameter

*C*<br/>
Zu testende ganze Zahl.

## <a name="return-value"></a>Rückgabewert

Jede dieser Routinen gibt einen Wert ungleich Null zurück, wenn *c* eine bestimmte Darstellung eines anderen druckbaren Zeichens als eines Leerzeichens ist. **isgraph** gibt einen Wert ungleich Null zurück, wenn *c* ein druckbares Zeichen ist, das nicht ein Leerzeichen ist. **iswgraph** gibt einen Wert ungleich Null zurück, wenn *c* ein druckbares breites Zeichen ist, das nicht ein großer Zeichenraum ist. Jede dieser Routinen gibt 0 zurück, wenn *c* die Testbedingung nicht erfüllt.

Die Versionen dieser Funktionen mit dem **suffix _l** verwenden das Gebietsschema, das übergeben wird, anstelle des aktuellen Gebietsschemas für ihr gebietsschemaabhängiges Verhalten. Weitere Informationen finden Sie unter [Locale](../../c-runtime-library/locale.md).

Das Verhalten von **isgraph** und **_isgraph_l** ist nicht definiert, wenn *c* nicht EOF ist oder im Bereich 0 bis 0xFF, einschließlich. Wenn eine Debug-CRT-Bibliothek verwendet wird und *c* nicht einer dieser Werte ist, werden die Funktionen eine Assertion aus.

### <a name="generic-text-routine-mappings"></a>Zuordnung generischer Textroutinen

|TCHAR.H-Routine|_UNICODE und _MBCS nicht definiert.|_MBCS definiert|_UNICODE definiert|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_istgraph**|**isgraph**|[_ismbcgraph](ismbcgraph-functions.md)|**iswgraph**|
|**_istgraph_l**|**_isgraph_l**|[_ismbcgraph_l](ismbcgraph-functions.md)|**_iswgraph_l**|

## <a name="remarks"></a>Bemerkungen

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen dazu finden Sie [unter Globaler Status in der CRT](../global-state.md).

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|
|-------------|---------------------|
|**isgraph**|\<ctype.h>|
|**iswgraph**|\<ctype.h> oder \<wchar.h>|
|**_isgraph_l**|\<ctype.h>|
|**_iswgraph_l**|\<ctype.h> oder \<wchar.h>|

Zusätzliche Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Siehe auch

[Zeichenklassifizierung](../../c-runtime-library/character-classification.md)<br/>
[Locale](../../c-runtime-library/locale.md)<br/>
[is, isw Routines](../../c-runtime-library/is-isw-routines.md)<br/>
