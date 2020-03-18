---
title: _mbsnbicmp, _mbsnbicmp_l
ms.date: 11/04/2016
api_name:
- _mbsnbicmp_l
- _mbsnbicmp
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
ms.openlocfilehash: c7a4d5def115101c9f3fbd6c53d649ab5b122f1c
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2020
ms.locfileid: "79442835"
---
# <a name="_mbsnbicmp-_mbsnbicmp_l"></a>_mbsnbicmp, _mbsnbicmp_l

Vergleicht **n** Bytes von zwei Multibyte-Zeichen folgen und ignoriert die Groß-/Kleinschreibung.

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

*Zeichenfolge1*, *Zeichenfolge2*<br/>
Zu vergleichende mit NULL endende Zeichenfolgen.

*count*<br/>
Anzahl der zu vergleichenden Bytes.

## <a name="return-value"></a>Rückgabewert

Der Rückgabewert gibt die Beziehung zwischen den untergeordneten Zeichenfolgen an.

|Rückgabewert|BESCHREIBUNG|
|------------------|-----------------|
|< 0|*Zeichenfolge1* Teil Zeichenfolge kleiner als *Zeichenfolge2* Teil Zeichenfolge.|
|0|*Zeichenfolge1* Teil Zeichenfolge, die mit *Zeichenfolge2* Teil Zeichenfolge identisch ist.|
|> 0|*Zeichenfolge1* Teil Zeichenfolge größer als *Zeichenfolge2* Teil Zeichenfolge.|

Bei einem Fehler gibt **_mbsnbicmp** **_NLSCMPERROR**zurück, das in String. h und mbstring. h definiert ist.

## <a name="remarks"></a>Bemerkungen

Die **_mbsnbicmp** -Funktion führt einen Ordinalvergleich von höchstens der ersten *Anzahl* von Bytes von *Zeichenfolge1* und *Zeichenfolge2*aus. Der Vergleich wird durchgeführt, indem jedes Zeichen in Kleinbuchstaben konvertiert wird. [_mbsnbcmp](mbsnbcmp-mbsnbcmp-l.md) ist eine Version von **_mbsnbicmp**, die Groß-/Kleinschreibung beachtet. Der Vergleich endet, wenn ein abschließendes NULL-Zeichen in einer der beiden Zeichen folgen erreicht wird, bevor *count* -Zeichen verglichen werden. Wenn die Zeichen folgen gleich sind, wenn ein abschließende Null-Zeichen in einer der beiden Zeichen folgen erreicht wird, bevor *count* -Zeichen verglichen werden, ist die kürzere Zeichenfolge geringer.

**_mbsnbicmp** ähnelt [_mbsnbcmp](mbsnbcmp-mbsnbcmp-l.md), mit dem Unterschied, dass die Zeichen folgen nicht mit Zeichen, sondern mit der *Anzahl* von Bytes verglichen werden.

Abhängig von der Großschreibung ist der Vergleich von zwei Zeichenfolgen mit Zeichen zwischen „Z“ und „a“ in der ASCII-Tabelle ('[', '\\', ']', '^', '_' und '\`') unterschiedlich. Beispielsweise vergleichen die beiden Zeichen folgen "abcde" und "abcd ^" eine Richtung, wenn der Vergleich klein geschrieben ist ("abcde" > "abcd ^") und die andere Methode ("abcde" < "abcd ^"), wenn es sich um einen Großbuchstaben handelt.

**_mbsnbicmp** erkennt multibytezeichensequenzen gemäß der derzeit verwendeten [Multibytezeichen-Codepage](../../c-runtime-library/code-pages.md) . Die aktuelle Gebietsschemaeinstellung nimmt dabei keinen Einfluss.

Wenn entweder *Zeichenfolge1* oder *Zeichenfolge2* ein NULL-Zeiger ist, ruft **_mbsnbicmp** den Handler für ungültige Parameter auf, wie unter [Parameter Validierung](../../c-runtime-library/parameter-validation.md)beschrieben. Wenn die weitere Ausführung zugelassen wird, gibt die Funktion **_NLSCMPERROR** zurück und legt **errno** auf **EINVAL**fest.

### <a name="generic-text-routine-mappings"></a>Zuordnung generischer Textroutinen

|Tchar.h-Routine|_UNICODE und _MBCS nicht definiert|_MBCS definiert|_UNICODE definiert|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tcsnicmp**|**_strnicmp**|**_mbsnbicmp**|**_wcsnicmp**|
|**_tcsnicmp_l**|**_strnicmp_l**|**_mbsnbicmp_l**|**_wcsnicmp_l**|

## <a name="requirements"></a>Requirements (Anforderungen)

|Routine|Erforderlicher Header|
|-------------|---------------------|
|**_mbsnbicmp**|\<mbstring.h>|

Weitere Informationen zur Kompatibilität finden Sie unter [Kompatibilität](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Beispiel

Weitere Informationen finden Sie im Beispiel [_mbsnbcmp _mbsnbcmp_l](mbsnbcmp-mbsnbcmp-l.md).

## <a name="see-also"></a>Weitere Informationen

[Zeichenfolgenbearbeitung](../../c-runtime-library/string-manipulation-crt.md)<br/>
[_mbsnbcat, _mbsnbcat_l](mbsnbcat-mbsnbcat-l.md)<br/>
[_mbsnbcmp, _mbsnbcmp_l](mbsnbcmp-mbsnbcmp-l.md)<br/>
[_stricmp, _wcsicmp, _mbsicmp, _stricmp_l, _wcsicmp_l, _mbsicmp_l](stricmp-wcsicmp-mbsicmp-stricmp-l-wcsicmp-l-mbsicmp-l.md)<br/>
