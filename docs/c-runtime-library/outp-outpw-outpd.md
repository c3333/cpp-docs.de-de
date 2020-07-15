---
title: outp, outpw, _outp _outpw, _outpd
description: Beschreibt die veralteten und entfernten outp-, outpw-, _outp-, _outpw-und _outpd-Funktionen der Microsoft C-Lauf Zeit Bibliothek (CRT).
ms.date: 12/09/2019
api_name:
- _outpd
- _outp
- _outpw
- outp
- outpw
api_location:
- msvcrt.dll
- msvcr100.dll
- msvcr120.dll
- msvcr90.dll
- msvcr110_clr0400.dll
- msvcr110.dll
- msvcr80.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _outpw
- _outpd
- _outp
- outp
- outpw
- outpd
helpviewer_keywords:
- outpw function
- words
- _outpd function
- outpd function
- outp function
- ports, writing bytes at
- bytes, writing to ports
- words, writing to ports
- double words
- double words, writing to ports
- _outpw function
- _outp function
ms.assetid: c200fe22-41f6-46fd-b0be-ebb805b35181
ms.openlocfilehash: 0d28511cdf7487226635c0317b7c0ba21ab1d1be
ms.sourcegitcommit: 31a443c9998cf5cfbaff00fcf815b133f55b2426
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/14/2020
ms.locfileid: "86373475"
---
# <a name="outp-outpw-_outp-_outpw-_outpd"></a>outp, outpw, _outp _outpw, _outpd

Gibt an einem Port ein Byte ( `outp` , `_outp` ), ein Wort ( `outpw` , `_outpw` ) oder ein doppeltes Wort ( `_outpd` ) aus.

> [!IMPORTANT]
> Diese Funktionen sind veraltet. Ab Visual Studio 2015 sind Sie in CRT nicht verfügbar. \
> Diese API kann nicht in Anwendungen verwendet werden, die in Windows-Runtime ausgeführt werden. Weitere Informationen finden Sie im Artikel [CRT functions not supported in Universal Windows Platform apps (In Apps für die universelle Windows-Plattform nicht unterstützte CRT-Funktionen)](../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntax

```cpp
int _outp(
   unsigned short port,
   int databyte
);
unsigned short _outpw(
   unsigned short port,
   unsigned short dataword
);
unsigned long _outpd(
   unsigned short port,
   unsigned long dataword
);
```

### <a name="parameters"></a>Parameter

*Port*\
Portnummer

*Databyte, dataword*\
Ausgabewerte

## <a name="return-value"></a>Rückgabewert

Die Funktionen geben die Datenausgabe zurück. Es gibt keine Fehlerrückgabe.

## <a name="remarks"></a>Hinweise

Die Funktionen `_outp`, `_outpw`und `_outpd` schreiben in den angegebenen Ausgabeport jeweils ein Byte, ein Wort und ein Doppelwort. Das *Port* -Argument kann eine beliebige ganze Zahl ohne Vorzeichen im Bereich 0-65.535; sein. *Databyte* kann eine beliebige ganze Zahl im Bereich 0-255 sein. und *dataword* kann jeder Wert im Bereich einer ganzen Zahl, eine kurze ganze Zahl ohne Vorzeichen und eine ganze Zahl ohne Vorzeichen sein.

Da diese Funktionen direkt in einen e/a-Port schreiben, können Sie nicht im Windows-Code im Benutzermodus verwendet werden. Informationen zur Verwendung von I/O-Ports im Windows-Betriebssystem finden Sie unter [serielle Kommunikation](https://docs.microsoft.com/previous-versions/ff802693(v=msdn.10)).

Die `outp` -und- `outpw` Namen sind älter, als veraltet markierte Namen für die `_outp` -und- `_outpw` Funktionen. Weitere Informationen finden Sie unter [POSIX-Funktionsnamen](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md#posix-function-names).

## <a name="requirements"></a>Anforderungen

|-Routine zurückgegebener Wert|Erforderlicher Header|
|-------------|---------------------|
|`_outp`|\<conio.h>|
|`_outpw`|\<conio.h>|
|`_outpd`|\<conio.h>|

Weitere Informationen zur Kompatibilität finden Sie unter [Compatibility](../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliotheken

Alle Versionen [C-Laufzeitbibliotheken](../c-runtime-library/crt-library-features.md).

## <a name="see-also"></a>Weitere Informationen

[Konsolen-und Port-e/a](../c-runtime-library/console-and-port-i-o.md)\
[INP, inpw, _inp _inpw, _inpd](../c-runtime-library/inp-inpw-inpd.md)
