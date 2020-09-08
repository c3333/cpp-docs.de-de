---
title: conj, conjf, conjl
description: API-Referenz für "Configuration Manager", "Configuration Manager" und "config" , die die komplexe konjugierte Zahl einer komplexen Zahl abrufen.
ms.date: 9/2/2020
api_name:
- conj
- conjf
- conjl
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
- api-ms-win-crt-math-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- conj
- conjf
- conjl
- complex/conj
- complex/conjf
- complex/conjl
helpviewer_keywords:
- conj function
- conjf function
- conjl function
ms.assetid: 792fccfa-19c6-4890-99f9-a3b89effccd6
ms.openlocfilehash: b779eb2d92893b204a73b2fa4f5c89928933ffeb
ms.sourcegitcommit: 4ed2d68634eb2fb77e18110a2d26bc0008be369c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/08/2020
ms.locfileid: "89556352"
---
# <a name="conj-conjf-conjl"></a>conj, conjf, conjl

Gibt die konjugiert komplexe Zahl einer komplexen Zahl zurück.

## <a name="syntax"></a>Syntax

```C
_Dcomplex conj(
   _Dcomplex z
);
_Fcomplex conj(
   _Fcomplex z
);  // C++ only
_Lcomplex conj(
   _Lcomplex z
);  // C++ only
_Fcomplex conjf(
   _Fcomplex z
);
_Lcomplex conjl(
   _Lcomplex z
);
#define conj(X) // Requires C11 or higher
```

### <a name="parameters"></a>Parameter

*z*\
Eine komplexe Zahl.

## <a name="return-value"></a>Rückgabewert

Die komplexe konjugierte Zahl von *z*.  Das Ergebnis hat denselben Real-und Imaginärteil wie *z*, aber mit dem umgekehrten Vorzeichen.

## <a name="remarks"></a>Hinweise

Da **C++ das** überladen zulässt, können Sie über Ladungen von "Configuration Manager" aufzurufen, die **_Fcomplex** -und **_Lcomplex** -Werte verwenden und zurückgeben. Wenn Sie in einem C-Programm das- \<tgmath.h> Makro **verwenden,** um diese Funktion aufzurufen, nimmt "C" immer einen **_Dcomplex** Wert an und gibt diesen zurück.

Wenn Sie das- \<tgmath.h> `conj()` Makro verwenden, bestimmt der Typ des Arguments, welche Version der Funktion ausgewählt ist. Weitere Informationen finden Sie unter [Type-Generic Math](../../c-runtime-library/tgmath.md) .

## <a name="requirements"></a>Anforderungen

|-Routine zurückgegebener Wert|C-Header|C++-Header|
|-------------|--------------|------------------|
|Configuration **Manager, Configuration**Manager **conjf** **conjl**|\<complex.h>|\<ccomplex>|
|**Maj** -Makro | \<tgmath.h> ||

Weitere Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Weitere Informationen

[Alphabetische Funktionsreferenz](crt-alphabetical-function-reference.md)<br/>
[norm, normf, norml](norm-normf-norml1.md)<br/>
[creal, crealf, creall](creal-crealf-creall.md)<br/>
[cproj, cprojf, cprojl](cproj-cprojf-cprojl.md)<br/>
[cimag, cimagf, cimagl](cimag-cimagf-cimagl.md)<br/>
[carg, cargf, cargl](carg-cargf-cargl.md)<br/>
[cabs, cabsf, cabsl](cabs-cabsf-cabsl.md)<br/>
