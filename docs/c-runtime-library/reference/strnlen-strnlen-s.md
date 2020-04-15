---
title: strnlen, strnlen_s, wcsnlen, wcsnlen_s, _mbsnlen, _mbsnlen_l, _mbstrnlen, _mbstrnlen_l
ms.date: 4/2/2020
api_name:
- wcsnlen
- strnlen_s
- _mbstrnlen
- _mbsnlen_l
- _mbstrnlen_l
- strnlen
- wcsnlen_s
- _mbsnlen
- _o__mbsnlen
- _o__mbsnlen_l
- _o__mbstrnlen
- _o__mbstrnlen_l
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
- api-ms-win-crt-string-l1-1-0.dll
- ntoskrnl.exe
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- wcsnlen
- strnlen_s
- _mbsnlen
- _mbsnlen_l
- _tcsnlen
- _tcscnlen
- _mbstrnlen_l
- wcsnlen_s
- _mbstrnlen
- strnlen
- _tcscnlen_l
helpviewer_keywords:
- _tcscnlen function
- _mbstrnlen function
- _mbsnlen_l function
- lengths, strings
- mbstrnlen function
- mbsnlen_l function
- _mbstrnlen_l function
- _tcscnlen_l function
- wcsnlen_l function
- _tcsnlen function
- _mbsnlen function
- strnlen function
- mbsnlen function
- wcsnlen_s function
- strnlen_s function
- mbstrnlen_l function
- wcsnlen function
- string length
- strnlen_l function
ms.assetid: cc05ce1c-72ea-4ae4-a7e7-4464e56e5f80
ms.openlocfilehash: db4fa65fa47dfe11d7ab56ffc5feee06f2634e2a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364471"
---
# <a name="strnlen-strnlen_s-wcsnlen-wcsnlen_s-_mbsnlen-_mbsnlen_l-_mbstrnlen-_mbstrnlen_l"></a>strnlen, strnlen_s, wcsnlen, wcsnlen_s, _mbsnlen, _mbsnlen_l, _mbstrnlen, _mbstrnlen_l

Ruft die Länge einer Zeichenfolge durch Verwendung des aktuellen oder einen übergebenen Gebietsschemas ab. Dies sind sicherere Versionen von [strlen, wcslen, _mbslen, _mbslen_l, _mbstrlen, _mbstrlen_l](strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l.md).

> [!IMPORTANT]
> **_mbsnlen** **, _mbsnlen_l**, **_mbstrnlen**und **_mbstrnlen_l** können nicht in Anwendungen verwendet werden, die in der Windows-Runtime ausgeführt werden. Weitere Informationen finden Sie im Artikel [CRT functions not supported in Universal Windows Platform apps (In Apps für die universelle Windows-Plattform nicht unterstützte CRT-Funktionen)](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntax

```C
size_t strnlen(
   const char *str,
   size_t numberOfElements
);
size_t strnlen_s(
   const char *str,
   size_t numberOfElements
);
size_t wcsnlen(
   const wchar_t *str,
   size_t numberOfElements
);
size_t wcsnlen_s(
   const wchar_t *str,
   size_t numberOfElements
);
size_t _mbsnlen(
   const unsigned char *str,
   size_t numberOfElements
);
size_t _mbsnlen_l(
   const unsigned char *str,
   size_t numberOfElements,
   _locale_t locale
);
size_t _mbstrnlen(
   const char *str,
   size_t numberOfElements
);
size_t _mbstrnlen_l(
   const char *str,
   size_t numberOfElements,
   _locale_t locale
);
```

### <a name="parameters"></a>Parameter

*Str*<br/>
Mit NULL endende Zeichenfolge.

*Sizeinbytes*<br/>
Die Größe des Zeichenfolgenpuffers.

*locale*<br/>
Zu verwendendes Gebietsschema.

## <a name="return-value"></a>Rückgabewert

Diese Funktionen geben die Anzahl von Zeichen in der Zeichenfolge zurück (ohne das abschließende Nullzeichen). Wenn innerhalb der ersten *numberOfElements-Bytes* der Zeichenfolge (oder Breitzeichen für **wcsnlen**) kein Null-Terminator vorhanden ist, wird *numberOfElements* zurückgegeben, um die Fehlerbedingung anzugeben. null-terminierte Zeichenfolgen haben Längen, die strikt kleiner als *numberOfElements*sind.

**_mbstrnlen** und **_mbstrnlen_l** -1 zurückgeben, wenn die Zeichenfolge ein ungültiges Multibyte-Zeichen enthält.

## <a name="remarks"></a>Bemerkungen

> [!NOTE]
> **strnlen** ist kein Ersatz für **strlen**; **strnlen** ist nur dazu gedacht, die Größe eingehender nicht vertrauenswürdiger Daten in einem Puffer bekannter Größe zu berechnen, z. B. ein Netzwerkpaket. **strnlen** berechnet die Länge, geht aber nicht am Ende des Puffers vorbei, wenn die Zeichenfolge nicht beendet ist. Verwenden Sie für andere Situationen **strlen**. (Das gleiche gilt für **wcsnlen**, **_mbsnlen**und **_mbstrnlen**.)

Jede dieser Funktionen gibt die Anzahl der Zeichen in *str*zurück, ohne das beendende Nullzeichen. **Strnlen** und **strnlen_s** interpretieren die Zeichenfolge jedoch als Zeichenfolge mit einem einzigen Byte, und daher ist der Rückgabewert immer gleich der Anzahl der Bytes, auch wenn die Zeichenfolge Multibyte-Zeichen enthält. **wcsnlen** und **wcsnlen_s** sind breitstellige Versionen von **strnlen** bzw. **strnlen_s;** Die Argumente für **wcsnlen** und **wcsnlen_s** sind Zeichenfolgen mit großen Zeichen, und die Anzahl der Zeichen sind in Breitzeicheneinheiten. Ansonsten verhalten sich **wcsnlen** und **strnlen** identisch, ebenso wie **strnlen_s** und **wcsnlen_s**.

**strnlen**, **wcsnlen**und **_mbsnlen** validieren ihre Parameter nicht. Wenn *str* **NULL**ist, tritt eine Zugriffsverletzung auf.

**strnlen_s** und **wcsnlen_s** ihre Parameter überprüfen. Wenn *str* **NULL**ist, geben die Funktionen 0 zurück.

**_mbstrnlen** überprüft auch seine Parameter. Wenn *str* **NULL**ist oder *wenn numberOfElements* größer als **INT_MAX** **ist, generiert _mbstrnlen** eine ungültige Parameterausnahme, wie unter [Parametervalidierung](../../c-runtime-library/parameter-validation.md)beschrieben. Wenn die Ausführung fortgesetzt werden darf, **setzt _mbstrnlen** **errno** auf **EINVAL** und gibt -1 zurück.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen dazu finden Sie [unter Globaler Status in der CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Zuordnung generischer Textroutinen

|TCHAR.H-Routine|_UNICODE und _MBCS nicht definiert.|_MBCS definiert|_UNICODE definiert|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tcsnlen**|**strnlen**|**strnlen**|**wcsnlen**|
|**_tcscnlen**|**strnlen**|**_mbsnlen**|**wcsnlen**|
|**_tcscnlen_l**|**strnlen**|**_mbsnlen_l**|**wcsnlen**|

**_mbsnlen** und **_mbstrnlen** die Anzahl der Multibyte-Zeichen in einer Zeichenfolge mit mehreren Byte-Zeichen zurückgeben. **_mbsnlen** erkennt Multibyte-Zeichen-Sequenzen gemäß der Multibyte-Codepage, die derzeit verwendet wird, oder nach dem Gebietsschema, das übergeben wurde. Es wird nicht auf Gültigkeit von mehreren Byte-Zeichen getestet. **_mbstrnlen** tests auf Gültigkeit von Mehreren Byte-Zeichen und erkennt Multibyte-Zeichen-Sequenzen. Wenn die Zeichenfolge, die an **_mbstrnlen** übergeben wird, ein ungültiges Multibyte-Zeichen enthält, wird **errno** auf **EILSEQ**festgelegt.

Der Ausgabewert wird durch die Einstellung der **LC_CTYPE** Kategorieeinstellung des Gebietsschemas beeinflusst. weitere Informationen finden Sie unter [setlocale, _wsetlocale.](setlocale-wsetlocale.md) Die Versionen dieser Funktionen sind identisch, mit der Ausnahme, dass die Versionen, die nicht über das **_l** Suffix verfügen, das aktuelle Gebietsschema für dieses gebietsschemaabhängige Verhalten verwenden und die Versionen mit dem **suffix _l** stattdessen den übergebenen Gebietsschemaparameter verwenden. Weitere Informationen finden Sie unter [Locale](../../c-runtime-library/locale.md).

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|
|-------------|---------------------|
|**strnlen**, **strnlen_s**|\<string.h>|
|**wcsnlen**, **wcsnlen_s**|\<string.h> oder \<wchar.h>|
|**_mbsnlen**, **_mbsnlen_l**|\<mbstring.h>|
|**_mbstrnlen**, **_mbstrnlen_l**|\<stdlib.h>|

Zusätzliche Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Beispiel

```C
// crt_strnlen.c

#include <string.h>

int main()
{
   // str1 is 82 characters long. str2 is 159 characters long

   char* str1 = "The length of a string is the number of characters\n"
               "excluding the terminating null.";
   char* str2 = "strnlen takes a maximum size. If the string is longer\n"
                "than the maximum size specified, the maximum size is\n"
                "returned rather than the actual size of the string.";
   size_t len;
   size_t maxsize = 100;

   len = strnlen(str1, maxsize);
   printf("%s\n Length: %d \n\n", str1, len);

   len = strnlen(str2, maxsize);
   printf("%s\n Length: %d \n", str2, len);
}
```

```Output
The length of a string is the number of characters
excluding the terminating null.
Length: 82

strnlen takes a maximum size. If the string is longer
than the maximum size specified, the maximum size is
returned rather than the actual size of the string.
Length: 100
```

## <a name="see-also"></a>Siehe auch

[String-Manipulation](../../c-runtime-library/string-manipulation-crt.md)<br/>
[Locale](../../c-runtime-library/locale.md)<br/>
[Interpretation von Multibyte-Zeichensequenzen](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[setlocale, _wsetlocale](setlocale-wsetlocale.md)<br/>
[strncat, _strncat_l, wcsncat, _wcsncat_l, _mbsncat, _mbsncat_l](strncat-strncat-l-wcsncat-wcsncat-l-mbsncat-mbsncat-l.md)<br/>
[strncmp, wcsncmp, _mbsncmp, _mbsncmp_l](strncmp-wcsncmp-mbsncmp-mbsncmp-l.md)<br/>
[strcoll-Funktionen](../../c-runtime-library/strcoll-functions.md)<br/>
[strncpy_s, _strncpy_s_l, wcsncpy_s, _wcsncpy_s_l, _mbsncpy_s, _mbsncpy_s_l](strncpy-s-strncpy-s-l-wcsncpy-s-wcsncpy-s-l-mbsncpy-s-mbsncpy-s-l.md)<br/>
[strrchr, wcsrchr, _mbsrchr, _mbsrchr_l](strrchr-wcsrchr-mbsrchr-mbsrchr-l.md)<br/>
[_strset, _strset_l, _wcsset, _wcsset_l, _mbsset, _mbsset_l](strset-strset-l-wcsset-wcsset-l-mbsset-mbsset-l.md)<br/>
[strspn, wcsspn, _mbsspn, _mbsspn_l](strspn-wcsspn-mbsspn-mbsspn-l.md)<br/>
