---
title: _mktemp_s, _wmktemp_s
ms.date: 4/2/2020
api_name:
- _mktemp_s
- _wmktemp_s
- _o__mktemp_s
- _o__wmktemp_s
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
- wmktemp_s
- mktemp_s
- _mktemp_s
- _wmktemp_s
helpviewer_keywords:
- _tmktemp_s function
- mktemp_s function
- _wmktemp_s function
- _mktemp_s function
- files [C++], temporary
- tmktemp_s function
- wmktemp_s function
- temporary files [C++]
ms.assetid: 92a7e269-7f3d-4c71-bad6-14bc827a451d
ms.openlocfilehash: 061c5647b2c5a5e79b017cf93989f62ad19cfc0a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81338758"
---
# <a name="_mktemp_s-_wmktemp_s"></a>_mktemp_s, _wmktemp_s

Erstellt einen eindeutigen Dateinamen. Dabei handelt es sich um Versionen von [_mktemp, _wmktem](mktemp-wmktemp.md) mit den unter [Sicherheitsfunktionen in der CRT](../../c-runtime-library/security-features-in-the-crt.md) beschriebenen Erweiterungen.

## <a name="syntax"></a>Syntax

```C
errno_t _mktemp_s(
   char *nameTemplate,
   size_t sizeInChars
);
errno_t _wmktemp_s(
   wchar_t *nameTemplate,
   size_t sizeInChars
);
template <size_t size>
errno_t _mktemp_s(
   char (&nameTemplate)[size]
); // C++ only
template <size_t size>
errno_t _wmktemp_s(
   wchar_t (&nameTemplate)[size]
); // C++ only
```

### <a name="parameters"></a>Parameter

*nameTemplate*<br/>
Muster des Dateinamens.

*sizeInChars*<br/>
Größe des Puffers in Einzelbyte-Zeichen in **_mktemp_s**; breite Zeichen in **_wmktemp_s**, einschließlich des Null-Terminators.

## <a name="return-value"></a>Rückgabewert

Beide Funktionen geben bei Erfolg null und bei Fehlern einen Fehlercode zurück.

### <a name="error-conditions"></a>Fehlerbedingungen

|*nameTemplate*|*sizeInChars*|Rückgabewert|Neuer Wert in *nameTemplate*|
|----------------|-------------------|----------------------|-------------------------------|
|**Null**|any|**Einval**|**Null**|
|Falsches Format (siehe Abschnitt "Hinweise" für das richtige Format)|any|**Einval**|Leere Zeichenfolge|
|any|<= Anzahl von X|**Einval**|Leere Zeichenfolge|

Wenn eine der oben genannten Fehlerbedingungen auftritt, wird ein Handler für ungültige Parameter aufgerufen (siehe [Parametervalidierung](../../c-runtime-library/parameter-validation.md)). Wenn die Ausführung fortgesetzt werden darf, wird **errno** auf **EINVAL** gesetzt und die Funktionen geben **EINVAL**zurück.

## <a name="remarks"></a>Bemerkungen

Die **funktion _mktemp_s** erstellt einen eindeutigen Dateinamen, indem das argument *nameTemplate* geändert wird, sodass der *nameTemplate-Zeiger* nach dem Aufruf auf eine Zeichenfolge verweist, die den neuen Dateinamen enthält. **_mktemp_s** verarbeitet automatisch Zeichenfolgenargumente mit mehreren Byte-Zeichen, wobei Multibyte-Zeichensequenzen entsprechend der Multibyte-Codepage erkannt werden, die derzeit vom Laufzeitsystem verwendet wird. **_wmktemp_s** ist eine breit **gefächerte**Version von _mktemp_s ; das Argument von **_wmktemp_s** ist eine Zeichenfolge mit großen Zeichen. **_wmktemp_s** und **_mktemp_s** verhalten sich ansonsten identisch, mit der Ausnahme, dass **_wmktemp_s** keine Zeichenfolgen mit mehreren Byte-Zeichen verarbeitet.

Die Debugbibliotheksversionen dieser Funktionen füllen zunächst den Puffer mit 0xFE. Um dieses Verhalten zu deaktivieren, verwenden Sie [_CrtSetDebugFillThreshold](crtsetdebugfillthreshold.md).

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen dazu finden Sie [unter Globaler Status in der CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Zuordnung generischer Textroutinen

|Tchar.h-Routine|_UNICODE und _MBCS nicht definiert|_MBCS definiert|_UNICODE definiert|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tmktemp_s**|**_mktemp_s**|**_mktemp_s**|**_wmktemp_s**|

Das *argumentTemplate* hat das Formular **baseXXXXXX**, wobei *base* der Teil des neuen Dateinamens ist, den Sie angeben, und jedes X ist ein Platzhalter für ein **Zeichen, das**von _mktemp_s bereitgestellt wird. Jedes Platzhalterzeichen in *nameTemplate* muss ein X in Großbuchstaben sein. **_mktemp_s** behält die *Basis* bei und ersetzt das erste nachfolgende X durch ein alphabetisches Zeichen. **_mktemp_s** ersetzt die folgenden nachfolgenden X es durch einen fünfstelligen Wert; Dieser Wert ist eine eindeutige Nummer, die den aufrufenden Prozess oder in Multithreadprogrammen den aufrufenden Thread identifiziert.

Jeder erfolgreiche Aufruf **an _mktemp_s** ändert *nameTemplate*. Bei jedem nachfolgenden Aufruf desselben Prozesses oder Threads mit demselben *nameTemplate-Argument* **sucht _mktemp_s** nach Dateinamen, die mit Namen übereinstimmen, die von **_mktemp_s** in früheren Aufrufen zurückgegeben wurden. Wenn keine Datei für einen bestimmten Namen vorhanden ist, **gibt _mktemp_s** diesen Namen zurück. Wenn Dateien für alle zuvor zurückgegebenen Namen vorhanden sind, **erstellt _mktemp_s** einen neuen Namen, indem das alphabetische Zeichen, das im zuvor zurückgegebenen Namen verwendet wurde, durch den nächsten verfügbaren Kleinbuchstaben ersetzt wird, in der Reihenfolge von 'a' bis 'z'. Wenn die *Basis* z. B. folgende Ist::

> **fn**

und der von **_mktemp_s** angegebene fünfstellige Wert ist 12345, der zurückgegebene Vorname lautet:

> **fna12345**

Wenn dieser Name zum Erstellen der Datei FNA12345 verwendet wird und diese Datei immer noch vorhanden ist, lautet der nächste Name, der bei einem Aufruf desselben Prozesses oder Threads mit derselben *Basis* für *nameTemplate* zurückgegeben wird:

> **fnb12345**

Ist FNA12345 nicht vorhanden, lautet der nächste zurückgegebene Name erneut:

> **fna12345**

**_mktemp_s** kann maximal 26 eindeutige Dateinamen für eine beliebige Kombination von *Basis-* und *NameTemplate-Werten* erstellen. Daher ist FNZ12345 der letzte eindeutige Dateiname, den **_mktemp_s** für die in diesem Beispiel verwendeten *Basis-* und *NameTemplate-Werte* erstellen kann.

In C++ wird die Verwendung dieser Funktionen durch Vorlagenüberladungen vereinfacht; die Überladungen können automatisch Rückschlüsse auf die Pufferlänge ziehen (wodurch kein Größenargument mehr angegeben werden muss), und sie können automatisch die älteren, nicht sicheren Funktionen durch ihre neueren, sicheren Entsprechungen ersetzen. Weitere Informationen finden Sie unter [Sichere Vorlagenüberladungen](../../c-runtime-library/secure-template-overloads.md).

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|
|-------------|---------------------|
|**_mktemp_s**|\<io.h>|
|**_wmktemp_s**|\<io.h> oder \<wchar.h>|

Weitere Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Beispiel

```cpp
// crt_mktemp_s.cpp
/* The program uses _mktemp to create
* five unique filenames. It opens each filename
* to ensure that the next name is unique.
*/

#include <io.h>
#include <string.h>
#include <stdio.h>

char *fnTemplate = "fnXXXXXX";
char names[5][9];

int main()
{
   int i, err, sizeInChars;
   FILE *fp;

   for( i = 0; i < 5; i++ )
   {
      strcpy_s( names[i], sizeof(names[i]), fnTemplate );
      /* Get the size of the string and add one for the null terminator.*/
      sizeInChars = strnlen(names[i], 9) + 1;
      /* Attempt to find a unique filename: */
      err = _mktemp_s( names[i], sizeInChars );
      if( err != 0 )
         printf( "Problem creating the template" );
      else
      {
         if( fopen_s( &fp, names[i], "w" ) == 0 )
            printf( "Unique filename is %s\n", names[i] );
         else
            printf( "Cannot open %s\n", names[i] );
         fclose( fp );
      }
   }

   return 0;
}
```

### <a name="sample-output"></a>Beispielausgabe

```Output
Unique filename is fna03188
Unique filename is fnb03188
Unique filename is fnc03188
Unique filename is fnd03188
Unique filename is fne03188
```

## <a name="see-also"></a>Siehe auch

[Dateiverarbeitung](../../c-runtime-library/file-handling.md)<br/>
[fopen, _wfopen](fopen-wfopen.md)<br/>
[_getmbcp](getmbcp.md)<br/>
[_getpid](getpid.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
[_setmbcp](setmbcp.md)<br/>
[_tempnam, _wtempnam, tmpnam, _wtmpnam](tempnam-wtempnam-tmpnam-wtmpnam.md)<br/>
[tmpfile_s](tmpfile-s.md)<br/>
