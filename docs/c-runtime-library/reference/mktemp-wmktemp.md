---
title: _mktemp, _wmktemp
ms.date: 4/2/2020
api_name:
- _wmktemp
- _mktemp
- _o__mktemp
- _o__wmktemp
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
- api-ms-win-crt-stdio-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _tmktemp
- wmktemp
- tmktemp
- _wmktemp
- _mktemp
helpviewer_keywords:
- _wmktemp function
- _mktemp function
- files [C++], temporary
- tmktemp function
- _tmktemp function
- wmktemp function
- mktemp function
- temporary files [C++]
ms.assetid: 055eb539-a8c2-4a7d-be54-f5b6d1eb5c85
ms.openlocfilehash: 536a63841c6e29fa003eb8b99c896f6d1cf5519f
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2020
ms.locfileid: "82919099"
---
# <a name="_mktemp-_wmktemp"></a>_mktemp, _wmktemp

Erstellt einen eindeutigen Dateinamen. Für diese Funktionen sind sicherere Versionen verfügbar. Informationen dazu finden Sie unter [_mktemp_s, _wmktemp_s](mktemp-s-wmktemp-s.md).

## <a name="syntax"></a>Syntax

```C
char *_mktemp(
   char *nameTemplate
);
wchar_t *_wmktemp(
   wchar_t *nameTemplate
);
template <size_t size>
char *_mktemp(
   char (&nameTemplate)[size]
); // C++ only
template <size_t size>
wchar_t *_wmktemp(
   wchar_t (&nameTemplate)[size]
); // C++ only
```

### <a name="parameters"></a>Parameter

*aufweisen*<br/>
Muster des Dateinamens.

## <a name="return-value"></a>Rückgabewert

Jede dieser Funktionen gibt einen Zeiger auf die geänderte nametemplate zurück. Die-Funktion gibt NULL zurück, wenn " *nametemplate* " **ungültig** ist oder keine weiteren eindeutigen Namen aus der angegebenen nametemplate erstellt werden können.

## <a name="remarks"></a>Hinweise

Die **_mktemp** -Funktion erstellt einen eindeutigen Dateinamen, indem das *nametemplate* -Argument geändert wird. **_mktemp** automatisch Multibytezeichen-Zeichen folgen Argumente behandelt, wobei Multibytezeichen-Zeichen folgen entsprechend der Multibytezeichen-Codepage erkannt werden, die zurzeit vom Laufzeitsystem verwendet wird. **_wmktemp** ist eine breit Zeichen Version von **_mktemp**. Das Argument und der Rückgabewert von **_wmktemp** sind Zeichen folgen mit breit Zeichen. **_wmktemp** und **_mktemp** Verhalten sich andernfalls identisch, mit dem Unterschied, dass **_wmktemp** keine Multibyte-Zeichen folgen verarbeitet.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen hierzu finden Sie unter [globaler Status in der CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Zuordnung generischer Textroutinen

|Tchar.h-Routine|_UNICODE und _MBCS nicht definiert|_MBCS definiert|_UNICODE definiert|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tmktemp**|**_mktemp**|**_mktemp**|**_wmktemp**|

Das *nametemplate* -Argument hat die Form *Base*xxxxxx, wobei *Base* der von Ihnen angegebene Teil des neuen Datei namens und jedes X ein Platzhalter für ein Zeichen ist, das von **_mktemp**angegeben wird. Jedes Platzhalter Zeichen in *nametemplate* muss ein Großbuchstabe X sein. **_mktemp** behält die *Basis* bei und ersetzt das erste nachfolgende x durch ein alphabetisches Zeichen. **_mktemp** ersetzt die folgenden nachfolgenden X-Werte durch einen fünfstelligen Wert. Dieser Wert ist eine eindeutige Zahl, die den aufrufenden Prozess identifiziert, bzw. in Multithreadprogrammen den aufrufenden Thread.

Bei jedem erfolgreichen Aufrufe von **_mktemp** wird " *nametemplate" geändert*. Bei jedem nachfolgenden Aufruf desselben Prozesses oder Threads mit demselben *nametemplate* -Argument prüft **_mktemp** nach Dateinamen, die mit den Namen übereinstimmen, die von **_mktemp** in vorherigen Aufrufen zurückgegeben wurden. Wenn für einen bestimmten Namen keine Datei vorhanden ist, gibt **_mktemp** diesen Namen zurück. Wenn Dateien für alle zuvor zurückgegebenen Namen vorhanden sind, erstellt **_mktemp** einen neuen Namen, indem das in dem zuvor zurückgegebenen Namen verwendete alphabetische Zeichen durch den nächsten verfügbaren Kleinbuchstaben (in der angegebenen Reihenfolge) von "a" bis "z" ersetzt wird. Wenn die *Basis* beispielsweise:

> **fn**

der von **_mktemp** bereitgestellte fünfstellige Wert ist 12345, der erste zurückgegebene Name lautet:

> **FNA12345**

Wenn dieser Name verwendet wird, um die Datei zu erstellen FNA12345 und diese Datei immer noch vorhanden ist, lautet der nächste Name, der bei einem Rückruf desselben Prozesses oder Threads mit der gleichen *Basis* für " *nametemplate* " zurückgegeben wird, wie folgt:

> **fnb12345**

Ist FNA12345 nicht vorhanden, lautet der nächste zurückgegebene Name erneut:

> **FNA12345**

**_mktemp** können maximal 26 eindeutige Dateinamen für eine bestimmte Kombination von *Basis* -und *nametemplate* -Werten erstellen. Daher ist FNZ12345 der letzte eindeutige Dateiname **_mktemp** der für die *Basis* -und *nametemplate* -Werte erstellt werden kann, die in diesem Beispiel verwendet werden.

Bei einem Fehler wird **errno** festgelegt. Wenn *nametemplate* ein ungültiges Format aufweist (z. b. weniger als 6 X), wird **errno** auf **EINVAL**festgelegt. Wenn **_mktemp** keinen eindeutigen Namen erstellen kann, weil alle 26 möglichen Dateinamen bereits vorhanden sind, wird "nametemplate" **_mktemp** auf eine leere Zeichenfolge festgelegt und " **EEXIST**" zurückgegeben.

In C++ haben diese Funktionen Vorlagenüberladungen, mit denen die neueren, sicheren Entsprechungen dieser Funktionen aufgerufen werden. Weitere Informationen finden Sie unter [Sichere Vorlagenüberladungen](../../c-runtime-library/secure-template-overloads.md).

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|
|-------------|---------------------|
|**_mktemp**|\<io.h>|
|**_wmktemp**|\<io.h> oder \<wchar.h>|

Weitere Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Beispiel

```C
// crt_mktemp.c
// compile with: /W3
/* The program uses _mktemp to create
* unique filenames. It opens each filename
* to ensure that the next name is unique.
*/

#include <io.h>
#include <string.h>
#include <stdio.h>
#include <errno.h>

char *template = "fnXXXXXX";
char *result;
char names[27][9];

int main( void )
{
   int i;
   FILE *fp;

   for( i = 0; i < 27; i++ )
   {
      strcpy_s( names[i], sizeof( names[i] ), template );
      /* Attempt to find a unique filename: */
      result = _mktemp( names[i] );  // C4996
      // Note: _mktemp is deprecated; consider using _mktemp_s instead
      if( result == NULL )
      {
         printf( "Problem creating the template\n" );
         if (errno == EINVAL)
         {
             printf( "Bad parameter\n");
         }
         else if (errno == EEXIST)
         {
             printf( "Out of unique filenames\n");
         }
      }
      else
      {
         fopen_s( &fp, result, "w" );
         if( fp != NULL )
            printf( "Unique filename is %s\n", result );
         else
            printf( "Cannot open %s\n", result );
         fclose( fp );
      }
   }
}
```

```Output
Unique filename is fna03912
Unique filename is fnb03912
Unique filename is fnc03912
Unique filename is fnd03912
Unique filename is fne03912
Unique filename is fnf03912
Unique filename is fng03912
Unique filename is fnh03912
Unique filename is fni03912
Unique filename is fnj03912
Unique filename is fnk03912
Unique filename is fnl03912
Unique filename is fnm03912
Unique filename is fnn03912
Unique filename is fno03912
Unique filename is fnp03912
Unique filename is fnq03912
Unique filename is fnr03912
Unique filename is fns03912
Unique filename is fnt03912
Unique filename is fnu03912
Unique filename is fnv03912
Unique filename is fnw03912
Unique filename is fnx03912
Unique filename is fny03912
Unique filename is fnz03912
Problem creating the template.
Out of unique filenames.
```

## <a name="see-also"></a>Weitere Informationen

[Dateiverarbeitung](../../c-runtime-library/file-handling.md)<br/>
[fopen, _wfopen](fopen-wfopen.md)<br/>
[_getmbcp](getmbcp.md)<br/>
[_getpid](getpid.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
[_setmbcp](setmbcp.md)<br/>
[_tempnam, _wtempnam, tmpnam, _wtmpnam](tempnam-wtempnam-tmpnam-wtmpnam.md)<br/>
[tmpfile](tmpfile.md)<br/>
