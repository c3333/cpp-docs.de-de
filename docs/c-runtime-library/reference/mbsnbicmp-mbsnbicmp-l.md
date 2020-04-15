---
title: _mbsnbicmp, _mbsnbicmp_l
ms.date: 4/2/2020
api_name:
- _mbsnbicmp_l
- _mbsnbicmp
- _o__mbsnbicmp
- _o__mbsnbicmp_l
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
- api-ms-win-crt-multibyte-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _mbsnbicmp
- mbsnbicmp
- mbsnbicmp_l
- _mbsnbicmp_l
helpviewer_keywords:
- _tcsnicmp_l function
- _strnicmp function
- mbsnbicmp_l function
- _wcsnicmp_l function
- _mbsnbicmp function
- _mbsnbicmp_l function
- _tcsnicmp function
- _strnicmp_l function
- mbsnbicmp function
- _wcsnicmp function
ms.assetid: ddb44974-8b0c-42f0-90d0-56c9350bae0c
ms.openlocfilehash: 80d2708396cdaeb86c25932c3d13129fb318719a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81340579"
---
# <a name="_mbsnbicmp-_mbsnbicmp_l"></a>_mbsnbicmp, _mbsnbicmp_l

Vergleicht **n** Bytes von zwei Zeichenfolgen mit mehreren Byte-Zeichen und ignoriert die Groß-/Kleinschreibung.

> [!IMPORTANT]
> Diese API kann nicht in Anwendungen verwendet werden, die in Windows-Runtime ausgeführt werden. Weitere Informationen finden Sie im Artikel [CRT functions not supported in Universal Windows Platform apps (In Apps für die universelle Windows-Plattform nicht unterstützte CRT-Funktionen)](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntax

```C
int _mbsnbicmp(
   const unsigned char *string1,
   const unsigned char *string2,
   size_t count
);
```

### <a name="parameters"></a>Parameter

*string1*, *string2*<br/>
Zu vergleichende mit NULL endende Zeichenfolgen.

*count*<br/>
Anzahl der zu vergleichenden Bytes.

## <a name="return-value"></a>Rückgabewert

Der Rückgabewert gibt die Beziehung zwischen den untergeordneten Zeichenfolgen an.

|Rückgabewert|BESCHREIBUNG|
|------------------|-----------------|
|< 0|*string1-Teilzeichenfolge* kleiner als *string2-Teilzeichenfolge.*|
|0|*string1-Teilzeichenfolge* identisch mit *string2-Teilzeichenfolge.*|
|> 0|*string1-Teilzeichenfolge* größer als *string2-Teilzeichenfolge.*|

Bei einem Fehler **gibt _mbsnbicmp** **_NLSCMPERROR**zurück, die in String.h und Mbstring.h definiert ist.

## <a name="remarks"></a>Bemerkungen

Die **_mbsnbicmp-Funktion** führt einen Ordinalvergleich von höchstens den ersten *Zählbytes* von *string1* und *string2*durch. Der Vergleich wird durchgeführt, indem jedes Zeichen in Kleinbuchstaben konvertiert wird. [_mbsnbcmp](mbsnbcmp-mbsnbcmp-l.md) ist eine Groß-/Kleinschreibung von **_mbsnbicmp**. Der Vergleich endet, wenn ein beendendes Nullzeichen in einer der beiden Zeichenfolgen erreicht wird, bevor *Zählzeichen* verglichen werden. Wenn die Zeichenfolgen gleich sind, wenn ein beendendes NULL-Zeichen in einer der beiden Zeichenfolgen erreicht wird, bevor *Zählzeichen* verglichen werden, ist die kürzere Zeichenfolge kleiner.

**_mbsnbicmp** ist [ähnlich wie _mbsnbcmp](mbsnbcmp-mbsnbcmp-l.md), mit der Ausnahme, dass Zeichenfolgen bis zu *Zählbytes* statt nach Zeichen verglichen werden.

Abhängig von der Großschreibung ist der Vergleich von zwei Zeichenfolgen mit Zeichen zwischen „Z“ und „a“ in der ASCII-Tabelle ('[', '\\', ']', '^', '_' und '\`') unterschiedlich. Die beiden Zeichenfolgen "ABCDE" und "ABCD" vergleichen z. B. eine Möglichkeit, wenn der Vergleich Kleinbuchstaben ist ("abcde" > "abcd") und umgekehrt ("ABCDE" < "ABCD") wenn es sich um Großbuchstaben handelt.

**_mbsnbicmp** erkennt Multibyte-Zeichen-Sequenzen entsprechend der derzeit genutzten [Multibyte-Codepage.](../../c-runtime-library/code-pages.md) Die aktuelle Gebietsschemaeinstellung nimmt dabei keinen Einfluss.

Wenn *string1* oder *string2* ein NULL-Zeiger ist, ruft **_mbsnbicmp** den ungültigen Parameterhandler auf, wie in [Parametervalidierung](../../c-runtime-library/parameter-validation.md)beschrieben. Wenn die Ausführung fortgesetzt werden darf, gibt die Funktion **_NLSCMPERROR** zurück und setzt **errno** auf **EINVAL**.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen dazu finden Sie [unter Globaler Status in der CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Zuordnung generischer Textroutinen

|Tchar.h-Routine|_UNICODE und _MBCS nicht definiert|_MBCS definiert|_UNICODE definiert|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tcsnicmp**|**_strnicmp**|**_mbsnbicmp**|**_wcsnicmp**|
|**_tcsnicmp_l**|**_strnicmp_l**|**_mbsnbicmp_l**|**_wcsnicmp_l**|

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|
|-------------|---------------------|
|**_mbsnbicmp**|\<mbstring.h>|

Weitere Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Beispiel

Weitere Informationen finden Sie im Beispiel [_mbsnbcmp _mbsnbcmp_l](mbsnbcmp-mbsnbcmp-l.md).

## <a name="see-also"></a>Siehe auch

[String-Manipulation](../../c-runtime-library/string-manipulation-crt.md)<br/>
[_mbsnbcat, _mbsnbcat_l](mbsnbcat-mbsnbcat-l.md)<br/>
[_mbsnbcmp, _mbsnbcmp_l](mbsnbcmp-mbsnbcmp-l.md)<br/>
[_stricmp, _wcsicmp, _mbsicmp, _stricmp_l, _wcsicmp_l, _mbsicmp_l](stricmp-wcsicmp-mbsicmp-stricmp-l-wcsicmp-l-mbsicmp-l.md)<br/>
