---
title: _cscanf_s, _cscanf_s_l, _cwscanf_s, _cwscanf_s_l
ms.date: 11/04/2016
api_name:
- _cwscanf_s_l
- _cwscanf_s
- _cscanf_s
- _cscanf_s_l
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
- cscanf_s
- cscanf_s_l
- cwscanf_s
- _cwscanf_s
- _tcscanf_s
- _cscanf_s
- _cwscanf_s_l
- _cscanf_s_l
- cwscanf_s_l
- _tcscanf_s_l
- tcscanf_s
- tcscanf_s_l
helpviewer_keywords:
- cscanf_s function
- _cwscanf_s_l function
- tcscanf_s function
- console [C++], reading from
- _cscanf_s function
- data [C++], reading from the console
- cwscanf_s function
- _tcscanf_s_l function
- _cscanf_s_l function
- cscanf_s_l function
- cwscanf_s_l function
- reading data [C++], from the console
- _cwscanf_s function
- _tcscanf_s function
- tcscanf_s_l function
ms.assetid: 9ccab74d-916f-42a6-93d8-920525efdf4b
ms.openlocfilehash: a869ae4ab1b5f81c4198f620662604b79f19c2ab
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87234236"
---
# <a name="_cscanf_s-_cscanf_s_l-_cwscanf_s-_cwscanf_s_l"></a>_cscanf_s, _cscanf_s_l, _cwscanf_s, _cwscanf_s_l

Liest formatierte Daten aus der Konsole. Diese sichereren Versionen von [scanf, _scanf_l, wscanf, _wscanf_l](cscanf-cscanf-l-cwscanf-cwscanf-l.md) enthalten Sicherheitserweiterungen, wie unter [Sicherheitserweiterungen in der CRT](../../c-runtime-library/security-features-in-the-crt.md) beschrieben.

> [!IMPORTANT]
> Diese API kann nicht in Anwendungen verwendet werden, die in Windows-Runtime ausgeführt werden. Weitere Informationen finden Sie im Artikel [CRT functions not supported in Universal Windows Platform apps (In Apps für die universelle Windows-Plattform nicht unterstützte CRT-Funktionen)](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntax

```C
int _cscanf_s(
   const char *format [,
   argument] ...
);
int _cscanf_s_l(
   const char *format,
   locale_t locale [,
   argument] ...
);
int _cwscanf_s(
   const wchar_t *format [,
   argument] ...
);
int _cwscanf_s_l(
   const wchar_t *format,
   locale_t locale [,
   argument] ...
);
```

### <a name="parameters"></a>Parameter

*format*<br/>
Formatsteuerzeichenfolge.

*argument*<br/>
Optionale Parameter.

*locale*<br/>
Das zu verwendende Gebietsschema.

## <a name="return-value"></a>Rückgabewert

Die Anzahl der Felder, die erfolgreich konvertiert und zugewiesen wurden. Der Rückgabewert enthält keine nicht zugewiesenen gelesenen Felder. Der Rückgabewert ist **EOF** für den Versuch, am Dateiende zu lesen. Dies kann vorkommen, wenn Tastatureingaben auf der Befehlszeilenebene des Betriebssystems umgeleitet wurden. Ein Rückgabewert von 0 bedeutet, dass keine Felder zugewiesen wurden.

Diese Funktionen überprüfen ihre Parameter. Wenn *Format* ein NULL-Zeiger ist, rufen diese Funktionen den Handler für ungültige Parameter auf, wie in [Parameter Validation (Parameter](../../c-runtime-library/parameter-validation.md)Überprüfung) beschrieben. Wenn die weitere Ausführung zugelassen wird, geben diese Funktionen " **EOF** " und " **errno** " auf " **EINVAL**" zurück.

## <a name="remarks"></a>Bemerkungen

Die **_cscanf_s** -Funktion liest Daten direkt aus der Konsole in die Speicherorte, die durch das- *Argument*angegeben werden. Die Funktion [_getche](getch-getwch.md) wird verwendet, um Zeichen zu lesen. Jeder optionale Parameter muss ein Zeiger auf eine Variable mit einem Typ sein, der einem Typspezifizierer im- *Format*entspricht. Das Format steuert die Interpretation der Eingabefelder und hat die gleiche Form und Funktion wie der *Format* -Parameter für die [scanf_s](scanf-scanf-l-wscanf-wscanf-l.md) Funktion. Obwohl **_cscanf_s** normalerweise das Eingabezeichen wiederholt, erfolgt dies nicht, wenn der letzte aufrufungs Vorgang **_ungetch**war.

Wie andere sichere Versionen von Funktionen in der **scanf** -Familie erfordern **_cscanf_s** und **_cswscanf_s** Größen Argumente für die tyfeldzeichen **c**, **c**, **s**, **s**und **[**. Weitere Informationen finden Sie unter [scanf Width Specification (scanf-Breitenangabe)](../../c-runtime-library/scanf-width-specification.md).

> [!NOTE]
> Der Size-Parameter ist vom Typ **`unsigned`** und nicht vom **size_t**.

Die Versionen dieser Funktionen mit dem **_l** -Suffix sind beinahe identisch, verwenden jedoch den Gebiets Schema Parameter, der anstelle des aktuellen Thread Gebiets Schemas übergeben wurde.

### <a name="generic-text-routine-mappings"></a>Zuordnung generischer Textroutinen

|TCHAR.H-Routine|_UNICODE und _MBCS nicht definiert|_MBCS definiert|_UNICODE definiert|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tcscanf_s**|**_cscanf_s**|**_cscanf_s**|**_cwscanf_s**|
|**_tcscanf_s_l**|**_cscanf_s_l**|**_cscanf_s_l**|**_cwscanf_s_l**|

## <a name="requirements"></a>Anforderungen

|-Routine zurückgegebener Wert|Erforderlicher Header|
|-------------|---------------------|
|**_cscanf_s** **_cscanf_s_l**|\<conio.h>|
|**_cwscanf_s** **_cwscanf_s_l**|\<conio.h> oder \<wchar.h>|

Weitere Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliotheken

Alle Versionen [C-Laufzeitbibliotheken](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Beispiel

```C
// crt_cscanf_s.c
// compile with: /c
/* This program prompts for a string
* and uses _cscanf_s to read in the response.
* Then _cscanf_s returns the number of items
* matched, and the program displays that number.
*/

#include <stdio.h>
#include <conio.h>

int main( void )
{
   int result, n[3];
   int i;

   result = _cscanf_s( "%i %i %i", &n[0], &n[1], &n[2] );
   _cprintf_s( "\r\nYou entered " );
   for( i=0; i<result; i++ )
      _cprintf_s( "%i ", n[i] );
   _cprintf_s( "\r\n" );
}
```

```Input
1 2 3
```

```Output
You entered 1 2 3
```

## <a name="see-also"></a>Siehe auch

[Konsolen-und Port-e/a](../../c-runtime-library/console-and-port-i-o.md)<br/>
[_cprintf, _cprintf_l, _cwprintf, _cwprintf_l](cprintf-cprintf-l-cwprintf-cwprintf-l.md)<br/>
[fscanf_s, _fscanf_s_l, fwscanf_s, _fwscanf_s_l](fscanf-s-fscanf-s-l-fwscanf-s-fwscanf-s-l.md)<br/>
[scanf_s, _scanf_s_l, wscanf_s, _wscanf_s_l](scanf-s-scanf-s-l-wscanf-s-wscanf-s-l.md)<br/>
[sscanf_s, _sscanf_s_l, swscanf_s, _swscanf_s_l](sscanf-s-sscanf-s-l-swscanf-s-swscanf-s-l.md)<br/>
