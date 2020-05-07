---
title: _isctype, iswctype, _isctype_l, _iswctype_l
ms.date: 4/2/2020
api_name:
- _isctype_l
- iswctype
- _iswctype_l
- _isctype
- _o__isctype
- _o__isctype_l
- _o__iswctype_l
- _o_iswctype
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
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- iswctype
- _isctype
- _isctype_l
- _iswctype
- isctype
- iswctype_l
- isctype_l
- _iswctype_l
helpviewer_keywords:
- isctype_l function
- iswctype_l function
- iswctype function
- _isctype function
- _isctype_l function
- _iswctype_l function
- isctype function
- _iswctype function
ms.assetid: cf7509b7-12fc-4d95-8140-ad2eb98173d3
ms.openlocfilehash: 2261eab574a8bc206a02f9e505beff88cf4c7fcf
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2020
ms.locfileid: "82918949"
---
# <a name="_isctype-iswctype-_isctype_l-_iswctype_l"></a>_isctype, iswctype, _isctype_l, _iswctype_l

Testet *c* für die CType-Eigenschaft, die vom *DESC* -Argument angegeben wird. Für jeden gültigen *Wert von "* Debug" gibt es eine entsprechende breit Zeichen-Klassifizierungs Routine.

## <a name="syntax"></a>Syntax

```C
int _isctype(
   int c,
   _ctype_t desc
);
int _isctype_l(
   int c,
   _ctype_t desc,
   _locale_t locale
);
int iswctype(
   wint_t c,
   wctype_t desc
);
int _iswctype_l(
   wint_t c,
   wctype_t desc,
   _locale_t locale
);
```

### <a name="parameters"></a>Parameter

*scher*<br/>
Zu testende ganze Zahl.

*DESC*<br/>
Eigenschaft, für die der Test durchgeführt werden soll. Diese wird normalerweise mithilfe von ctype oder [wctype](wctype.md) abgerufen.

*locale*<br/>
Das für alle gebietsschemaabhängigen Tests zu verwendende Gebietsschema.

## <a name="return-value"></a>Rückgabewert

**_isctype** und **iswctype** geben einen Wert ungleich 0 (null) zurück, wenn *c* die vom *DESC* im aktuellen Gebiets Schema angegebene Eigenschaft oder 0 (null) aufweist. Die Versionen dieser Funktionen mit dem **_l** -Suffix sind beinahe identisch, verwenden jedoch das übergebene Gebiets Schema anstelle des aktuellen Gebiets Schemas für Ihr vom Gebiets Schema abhängiges Verhalten. Weitere Informationen finden Sie unter [Locale](../../c-runtime-library/locale.md).

Das Verhalten von **_isctype** und **_isctype_l** ist nicht definiert, wenn *c* nicht EOF ist oder im Bereich von 0 bis 0xFF (einschließlich) liegt. Wenn eine Debug-CRT-Bibliothek verwendet wird und *c* keiner dieser Werte ist, wird von den Funktionen eine-Assertion erhoben.

### <a name="generic-text-routine-mappings"></a>Zuordnung generischer Textroutinen

|Tchar.h-Routine|_UNICODE und _MBCS nicht definiert|_MBCS definiert|_UNICODE definiert|
|---------------------|--------------------------------------|--------------------|-----------------------|
|–|**_isctype**|–|**_iswctype**|
|–|**_isctype_l**|–|**_iswctype_l**|

## <a name="remarks"></a>Hinweise

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen hierzu finden Sie unter [globaler Status in der CRT](../global-state.md).

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|
|-------------|---------------------|
|**_isctype**|\<ctype.h>|
|**iswctype**|\<ctype.h> oder \<wchar.h>|
|**_isctype_l**|\<ctype.h>|
|**_iswctype_l**|\<ctype.h> oder \<wchar.h>|

Weitere Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliotheken

Alle Versionen [C-Laufzeitbibliotheken](../../c-runtime-library/crt-library-features.md).

## <a name="see-also"></a>Weitere Informationen

[Zeichen Klassifizierung](../../c-runtime-library/character-classification.md)<br/>
[Locale](../../c-runtime-library/locale.md)<br/>
[is-, ISW-Routinen](../../c-runtime-library/is-isw-routines.md)<br/>
