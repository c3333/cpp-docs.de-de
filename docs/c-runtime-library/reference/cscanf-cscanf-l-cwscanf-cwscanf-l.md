---
title: _cscanf, _cscanf_l, _cwscanf, _cwscanf_l
ms.date: 10/21/2019
api_name:
- _cscanf_l
- _cscanf
- _cwscanf
- _cwscanf_l
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
- _cwscanf
- cwscanf_l
- tcscanf_l
- _tcscanf_l
- _cscanf
- _cscanf_l
- tcscanf
- cwscanf
- _cwscanf_l
- cscanf_l
- _tcscanf
helpviewer_keywords:
- _cwscanf function
- data [C++], reading from the console
- cscanf_l function
- tcscanf function
- _cscanf_l function
- cwscanf function
- _tcscanf_l function
- _cscanf function
- _tcscanf function
- cwscanf_l function
- tcscanf_l function
- reading data [C++], from the console
- _cwscanf_l function
ms.assetid: dbfe7547-b577-4567-a1cb-893fa640e669
ms.openlocfilehash: 45dcbd93ab689c8c86ab35e53552a65f561dfd18
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87234249"
---
# <a name="_cscanf-_cscanf_l-_cwscanf-_cwscanf_l"></a>_cscanf, _cscanf_l, _cwscanf, _cwscanf_l

Liest formatierte Daten aus der Konsole. Sicherere Versionen dieser Funktionen sind verfügbar. Sie finden sie unter [_cscanf_s, _cscanf_s_l, _cwscanf_s, _cwscanf_s_l](cscanf-s-cscanf-s-l-cwscanf-s-cwscanf-s-l.md).

> [!NOTE]
> In Visual Studio 2015 `printf` wurden die-und die- `scanf` Funktions Familie als deklariert **`inline`** und in `<stdio.h>` die `<conio.h>` Header und verschoben. Wenn Sie älteren Code migrieren, kann *LNK2019* in Verbindung mit diesen Funktionen angezeigt werden. Weitere Informationen finden Sie unter [Visual C++ Änderungs Verlauf 2003-2015](../../porting/visual-cpp-change-history-2003-2015.md#stdio_and_conio).

> [!IMPORTANT]
> Diese API kann nicht in Anwendungen verwendet werden, die in Windows-Runtime ausgeführt werden. Weitere Informationen finden Sie im Artikel [CRT functions not supported in Universal Windows Platform apps (In Apps für die universelle Windows-Plattform nicht unterstützte CRT-Funktionen)](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntax

```C
int _cscanf(
   const char *format [,
   argument] ...
);
int _cscanf_l(
   const char *format,
   locale_t locale [,
   argument] ...
);
int _cwscanf(
   const wchar_t *format [,
   argument] ...
);
int _cwscanf_l(
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

## <a name="remarks"></a>Bemerkungen

Die **_cscanf** -Funktion liest Daten direkt aus der Konsole in die Speicherorte, die durch das- *Argument*angegeben werden. Die Funktion [_getche](getch-getwch.md) wird verwendet, um Zeichen zu lesen. Jeder optionale Parameter muss ein Zeiger auf eine Variable mit einem Typ sein, der einem Typspezifizierer im- *Format*entspricht. Das Format steuert die Interpretation der Eingabefelder und hat die gleiche Form und Funktion wie der *Format* -Parameter für die [scanf](scanf-scanf-l-wscanf-wscanf-l.md) -Funktion. Obwohl **_cscanf** normalerweise das Eingabezeichen wiederholt, erfolgt dies nicht, wenn der letzte aufrufungs Vorgang **_ungetch**war.

Diese Funktion überprüft ihre Parameter. Wenn Format **null**ist, wird der Handler für ungültige Parameter aufgerufen, wie in [Parameter Validation (Parameter](../../c-runtime-library/parameter-validation.md)Überprüfung) beschrieben. Wenn die weitere Ausführung zugelassen wird, wird **errno** auf **EINVAL** festgelegt, und die Funktion gibt **EOF**zurück.

Die Versionen dieser Funktionen mit dem **_l** -Suffix sind beinahe identisch, verwenden jedoch den Gebiets Schema Parameter, der anstelle des aktuellen Thread Gebiets Schemas übergeben wurde.

### <a name="generic-text-routine-mappings"></a>Zuordnung generischer Textroutinen

|TCHAR.H-Routine|_UNICODE und _MBCS nicht definiert|_MBCS definiert|_UNICODE definiert|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tcscanf**|**_cscanf**|**_cscanf**|**_cwscanf**|
|**_tcscanf_l**|**_cscanf_l**|**_cscanf_l**|**_cwscanf_l**|

## <a name="requirements"></a>Anforderungen

|-Routine zurückgegebener Wert|Erforderlicher Header|
|-------------|---------------------|
|**_cscanf** **_cscanf_l**|\<conio.h>|
|**_cwscanf** **_cwscanf_l**|\<conio.h> oder \<wchar.h>|

Weitere Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Beispiel

```C
// crt_cscanf.c
// compile with: /c /W3
/* This program prompts for a string
* and uses _cscanf to read in the response.
* Then _cscanf returns the number of items
* matched, and the program displays that number.
*/

#include <stdio.h>
#include <conio.h>

int main( void )
{
   int   result, i[3];

   _cprintf_s( "Enter three integers: ");
   result = _cscanf( "%i %i %i", &i[0], &i[1], &i[2] ); // C4996
   // Note: _cscanf is deprecated; consider using _cscanf_s instead
   _cprintf_s( "\r\nYou entered " );
   while( result-- )
      _cprintf_s( "%i ", i[result] );
   _cprintf_s( "\r\n" );
}
```

```Input
1 2 3
```

```Output
Enter three integers: 1 2 3
You entered 3 2 1
```

## <a name="see-also"></a>Siehe auch

[Konsolen-und Port-e/a](../../c-runtime-library/console-and-port-i-o.md)<br/>
[_cprintf, _cprintf_l, _cwprintf, _cwprintf_l](cprintf-cprintf-l-cwprintf-cwprintf-l.md)<br/>
[fscanf, _fscanf_l, fwscanf, _fwscanf_l](fscanf-fscanf-l-fwscanf-fwscanf-l.md)<br/>
[scanf_s, _scanf_s_l, wscanf_s, _wscanf_s_l](scanf-s-scanf-s-l-wscanf-s-wscanf-s-l.md)<br/>
[sscanf, _sscanf_l, swscanf, _swscanf_l](sscanf-sscanf-l-swscanf-swscanf-l.md)<br/>
