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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: 8affd20ca7826f0d383f749567c9625d61dacd48
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81338723"
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

*nameTemplate*<br/>
Muster des Dateinamens.

## <a name="return-value"></a>Rückgabewert

Jede dieser Funktionen gibt einen Zeiger auf den geänderten NameTemplate zurück. Die Funktion gibt **NULL** zurück, wenn *nameTemplate* schlecht formatiert ist oder keine eindeutigen Namen mehr aus dem angegebenen NameTemplate erstellt werden können.

## <a name="remarks"></a>Bemerkungen

Die **_mktemp-Funktion** erstellt einen eindeutigen Dateinamen, indem das *argument nameTemplate* geändert wird. **_mktemp** verarbeitet automatisch Zeichenfolgenargumente mit mehreren Byte-Zeichen, wobei Multibyte-Zeichensequenzen entsprechend der Multibyte-Codepage erkannt werden, die derzeit vom Laufzeitsystem verwendet wird. **_wmktemp** ist eine breit gefächerte Version von **_mktemp**; Das Argument und der Rückgabewert von **_wmktemp** sind Zeichenfolgen mit großen Zeichen. **_wmktemp** und **_mktemp** verhalten sich ansonsten identisch, mit der Ausnahme, dass **_wmktemp** keine Zeichenfolgen mit mehreren Byte-Zeichen verarbeitet.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen dazu finden Sie [unter Globaler Status in der CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Zuordnung generischer Textroutinen

|Tchar.h-Routine|_UNICODE und _MBCS nicht definiert|_MBCS definiert|_UNICODE definiert|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tmktemp**|**_mktemp**|**_mktemp**|**_wmktemp**|

Das *argumentTemplate* hat die *Formularbasis*XXXXXX, wobei *basis* der Teil des neuen Dateinamens ist, den Sie angeben, und jedes X ist ein Platzhalter für ein **Zeichen, das**von _mktemp bereitgestellt wird. Jedes Platzhalterzeichen in *nameTemplate* muss ein X in Großbuchstaben sein. **_mktemp** behält die *Basis* bei und ersetzt das erste nachfolgende X durch ein alphabetisches Zeichen. **_mktemp** ersetzt die folgenden nachfolgenden X es durch einen fünfstelligen Wert; Dieser Wert ist eine eindeutige Nummer, die den aufrufenden Prozess oder in Multithreadprogrammen den aufrufenden Thread identifiziert.

Jeder erfolgreiche Aufruf **an _mktemp** ändert *nameTemplate*. Bei jedem nachfolgenden Aufruf desselben Prozesses oder Threads mit demselben *nameTemplate-Argument* **sucht _mktemp** nach Dateinamen, die mit Namen übereinstimmen, die von **_mktemp** in früheren Aufrufen zurückgegeben wurden. Wenn keine Datei für einen bestimmten Namen vorhanden ist, **gibt _mktemp** diesen Namen zurück. Wenn Dateien für alle zuvor zurückgegebenen Namen vorhanden sind, **erstellt _mktemp** einen neuen Namen, indem das alphabetische Zeichen, das im zuvor zurückgegebenen Namen verwendet wurde, durch den nächsten verfügbaren Kleinbuchstaben ersetzt wird, in der Reihenfolge von 'a' bis 'z'. Wenn die *Basis* z. B. folgende Ist::

> **fn**

und der von **_mktemp** angegebene fünfstellige Wert ist 12345, der zurückgegebene Vorname lautet:

> **fna12345**

Wenn dieser Name zum Erstellen der Datei FNA12345 verwendet wird und diese Datei immer noch vorhanden ist, lautet der nächste Name, der bei einem Aufruf desselben Prozesses oder Threads mit derselben *Basis* für *nameTemplate* zurückgegeben wird:

> **fnb12345**

Ist FNA12345 nicht vorhanden, lautet der nächste zurückgegebene Name erneut:

> **fna12345**

**_mktemp** kann maximal 26 eindeutige Dateinamen für eine beliebige Kombination von *Basis-* und *NameTemplate-Werten* erstellen. Daher ist FNZ12345 der letzte eindeutige **Dateiname,** den _mktemp für die in diesem Beispiel verwendeten *Basis-* und *NameTemplate-Werte* erstellen kann.

Bei einem Fehler wird **errno** gesetzt. Wenn *nameTemplate* ein ungültiges Format hat (z. B. weniger als 6 X), wird **errno** auf **EINVAL**gesetzt. Wenn **_mktemp** keinen eindeutigen Namen erstellen kann, da bereits alle 26 möglichen Dateinamen vorhanden sind, legt **_mktemp** nameTemplate auf eine leere Zeichenfolge fest und gibt **EEXIST**zurück.

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

## <a name="see-also"></a>Siehe auch

[Dateiverarbeitung](../../c-runtime-library/file-handling.md)<br/>
[fopen, _wfopen](fopen-wfopen.md)<br/>
[_getmbcp](getmbcp.md)<br/>
[_getpid](getpid.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
[_setmbcp](setmbcp.md)<br/>
[_tempnam, _wtempnam, tmpnam, _wtmpnam](tempnam-wtempnam-tmpnam-wtmpnam.md)<br/>
[tmpfile](tmpfile.md)<br/>
