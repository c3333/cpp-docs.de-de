---
title: Dateinamen-Suchfunktionen
ms.date: 11/04/2016
api_location:
- msvcr100.dll
- msvcr120.dll
- msvcr90.dll
- msvcrt.dll
- msvcr80.dll
- msvcr110.dll
- msvcr110_clr0400.dll
api_type:
- DLLExport
topic_type:
- apiref
helpviewer_keywords:
- file names [C++], searching for
- _find function
- wfind function
- find function
- _wfind function
ms.assetid: 2bc2f8ef-44e4-4271-b3e8-666d36fde828
ms.openlocfilehash: fb5cc0e18d150d4171e33038e27810989c0f503b
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87226241"
---
# <a name="filename-search-functions"></a>Dateinamen-Suchfunktionen

Diese Funktionen suchen nach angegebenen Dateinamen und schließen die Suche ab:

- [_findnext, _wfindnext](../c-runtime-library/reference/findnext-functions.md)

- [_findfirst, _wfindfirst](../c-runtime-library/reference/findfirst-functions.md)

- [_findclose](../c-runtime-library/reference/findclose.md)

## <a name="remarks"></a>Bemerkungen

Die `_findfirst` -Funktion stellt Informationen über das erste Vorkommen eines Dateinamens zur Verfügung, der mit der im Argument `filespec` angegebenen Datei übereinstimmt. Sie können in `filespec` beliebige Kombinationen von Platzhalterzeichen verwenden, die vom Hostbetriebssystem unterstützt werden.

Die Funktionen geben die Dateiinformationen in einer `_finddata_t`-Struktur zurück die in „io.h“ definiert ist. Verschiedene Funktionen in der Familie verwenden viele Varianten der `_finddata_t` -Struktur. Die grundlegende `_finddata_t` -Struktur umfasst die folgenden Elemente:

`unsigned attrib`<br/>
Dateiattribut.

`time_t time_create`<br/>
Erstellungszeitpunkt der Datei („-1L“ bei FAT-Dateisystemen) Die Uhrzeit wird im UTC-Format gespeichert. Verwenden Sie [localtime_s](../c-runtime-library/reference/localtime-s-localtime32-s-localtime64-s.md), um sie in die lokale Uhrzeit zu konvertieren.

`time_t time_access`<br/>
Zeitpunkt des letzten Dateizugriffs („-1L“ bei FAT-Dateisystemen) Die Uhrzeit wird im UTC-Format gespeichert. Verwenden Sie `localtime_s`, um sie in die lokale Uhrzeit zu konvertieren.

`time_t time_write`<br/>
Zeitpunkt des letzten Schreibzugriffs auf die Datei. Die Uhrzeit wird im UTC-Format gespeichert. Verwenden Sie `localtime_s`, um sie in die lokale Uhrzeit zu konvertieren.

`_fsize_t size`<br/>
Die Länge der Datei in Byte.

`char name`[ `_MAX_PATH`]: Der nullterminierte Name der zugeordneten Datei oder des zugeordneten Verzeichnisses ohne Pfad.

Die Felder `time_create` und `time_access` sind in Dateisystemen, die das Anzeigen des Zeitpunkts der Erstellung und des letzten Zugriffs nicht unterstützen, immer „-1L“. FAT-(File-Allocation-Table)-Systeme sind z.B. derartige Dateisysteme.

`_MAX_PATH` ist in „Stdlib.h“ als 260 Byte definiert.

Sie können keine Zielattribute angeben (wie etwa `_A_RDONLY`), um den Suchvorgang einzuschränken. Diese Attribute werden im Feld `attrib` der Struktur `_finddata_t` zurückgegeben und können die folgenden Werte aufweisen (die in „IO.h“ definiert sind). Die Benutzer sollten nicht darauf vertrauen, dass dies die einzigen möglichen Werte des Felds `attrib` sind.

`_A_ARCH`<br/>
Archiv. Bei jeder Änderung der Datei festgelegt und durch den **BACKUP** -Befehl zu löschen. Wert: 0x20.

`_A_HIDDEN`<br/>
Versteckte Datei. Im allgemeinen mithilfe des DIR-Befehls nicht angezeigt, sofern nicht die Option **/AH** verwendet wird. Gibt Informationen über normale Dateien und über Dateien, die dieses Attribut aufweisen, zurück. Wert: 0x02.

`_A_NORMAL`<br/>
Normal. Für die Datei sind keine weiteren Attribute festgelegt. Sie kann ohne Einschränkungen gelesen oder geschrieben werden. Wert: 0x00.

`_A_RDONLY`<br/>
Schreibgeschützt. Die Datei kann nicht zum Schreiben geöffnet werden, und eine Datei mit gleichem Namen kann nicht erstellt werden. Wert: 0x01.

`_A_SUBDIR`<br/>
Unterverzeichnis. Wert: 0x10.

`_A_SYSTEM`<br/>
Systemdatei. In der Regel mit dem Befehl **DIR** nicht angezeigt, es sei denn, die Option **/A** oder **/A:S** wird angegeben. Wert: 0x04.

`_findnext` sucht den nächsten Namen, falls vorhanden, der mit dem `filespec` -Argument übereinstimmt, das in einem vorhergegangenen Aufruf von `_findfirst`angegeben wurde. Das `fileinfo` -Argument sollte auf eine Struktur verweisen, die durch den vorhergehenden Aufruf von `_findfirst`initialisiert wurde. Wenn eine Übereinstimmung gefunden wird, wird der Inhalt der `fileinfo` -Struktur wie zuvor beschrieben geändert. Andernfalls bleibt er unverändert. `_findclose` schließt das angegebene Suchhandle und gibt alle zugeordneten Ressourcen sowohl für `_findfirst` als auch für `_findnext`frei. Das von `_findfirst` oder `_findnext` zurückgegebene Handle muss zuerst an `_findclose`übergeben werden, bevor Änderungsvorgänge, wie etwa Löschen, für die Verzeichnisse ausgeführt werden können, die in den übergebenen Pfaden vorkommen.

Die `_find` -Funktionen können verschachtelt werden. Wenn ein Aufruf von `_findfirst` oder `_findnext` beispielsweise feststellt, dass sich die Datei in einem Unterverzeichnis befindet, kann eine neue Suche mit einem weiteren Aufruf von `_findfirst` oder `_findnext`eingeleitet werden.

`_wfindfirst` und `_wfindnext` sind Breitzeichenversionen von `_findfirst` und `_findnext`. Das Strukturargument der Breitzeichenversionen weist den Datentyp `_wfinddata_t` auf, der in „IO.h“ und in „Wchar.h“ definiert ist. Die Felder dieses Datentyps sind identisch mit denen des `_finddata_t` Datentyps, mit dem Unterschied, dass im `_wfinddata_t` Feld Name vom Typ und nicht **`wchar_t`** vom Typ ist **`char`** . Andernfalls verhalten sich `_wfindfirst` und `_wfindnext` identisch mit `_findfirst` und `_findnext`.

`_findfirst` und `_findnext` verwenden den 64-Bit-Uhrzeittyp. Wenn Sie stattdessen den alten 32-Bit-Uhrzeittyp verwenden müssen, können Sie `_USE_32BIT_TIME_T`definieren. Die Versionen dieser Funktionen, die das `32` -Suffix im Namen aufweisen, verwenden den 32-Bit-Uhrzeittyp, und die mit dem `64` -Suffix verwenden den 64-Bit-Uhrzeittyp.

Die Funktionen `_findfirst32i64`, `_findnext32i64`, `_wfindfirst32i64`und `_wfindnext32i64` verhalten sich ebenfalls identisch wie die Versionen dieser Funktionen mit dem 32-Bit-Uhrzeittyp, mit dem Unterschied, dass sie 64-Bit-Dateilängen verwenden und zurückgeben. Die Funktionen `_findfirst64i32`, `_findnext64i32`, `_wfindfirst64i32`und `_wfindnext64i32` verwenden den 64-Bit-Uhrzeittyp, aber Dateilängen von 32 Bit. Diese Funktionen verwenden entsprechende Varianten des `_finddata_t` -Typs, bei denen die Felder verschiedene Typen für die Uhrzeit und die Dateigröße aufweisen.

`_finddata_t` ist tatsächlich ein Makro, das zu `_finddata64i32_t` ausgewertet wird (oder `_finddata32_t` , wenn `_USE_32BIT_TIME_T` definiert ist). In der folgenden Tabelle sind die Varianten von `_finddata_t`zusammengefasst:

|Struktur|Uhrzeittyp|Dateigrößentyp|
|---------------|---------------|--------------------|
|`_finddata_t`, `_wfinddata_t`|`__time64_t`|`_fsize_t`|
|`_finddata32_t`, `_wfinddata32_t`|`__time32_t`|`_fsize_t`|
|`__finddata64_t`, `__wfinddata64_t`|`__time64_t`|**`__int64`**|
|`_finddata32i64_t`, `_wfinddata32i64_t`|`__time32_t`|**`__int64`**|
|`_finddata64i32_t`, `_wfinddata64i32_t`|`__time64_t`|`_fsize_t`|

`_fsize_t`ist eine **`typedef`** für **`unsigned long`** (32 Bits).

## <a name="example"></a>Beispiel

```c
// crt_find.c
// This program uses the 32-bit _find functions to print
// a list of all files (and their attributes) with a .C extension
// in the current directory.

#include <stdio.h>
#include <stdlib.h>
#include <io.h>
#include <time.h>

int main( void )
{
   struct _finddata_t c_file;
   intptr_t hFile;

   // Find first .c file in current directory
   if( (hFile = _findfirst( "*.c", &c_file )) == -1L )
      printf( "No *.c files in current directory!\n" );
   else
   {
      printf( "Listing of .c files\n\n" );
      printf( "RDO HID SYS ARC  FILE         DATE %25c SIZE\n", ' ' );
      printf( "--- --- --- ---  ----         ---- %25c ----\n", ' ' );
      do {
         char buffer[30];
         printf( ( c_file.attrib & _A_RDONLY ) ? " Y  " : " N  " );
         printf( ( c_file.attrib & _A_HIDDEN ) ? " Y  " : " N  " );
         printf( ( c_file.attrib & _A_SYSTEM ) ? " Y  " : " N  " );
         printf( ( c_file.attrib & _A_ARCH )   ? " Y  " : " N  " );
         ctime_s( buffer, _countof(buffer), &c_file.time_write );
         printf( " %-12s %.24s  %9ld\n",
            c_file.name, buffer, c_file.size );
      } while( _findnext( hFile, &c_file ) == 0 );
      _findclose( hFile );
   }
}
```

```Output
Listing of .c files

RDO HID SYS ARC  FILE         DATE                           SIZE
--- --- --- ---  ----         ----                           ----
N   N   N   Y   blah.c       Wed Feb 13 09:21:42 2002       1715
N   N   N   Y   test.c       Wed Feb 06 14:30:44 2002        312
```

## <a name="see-also"></a>Siehe auch

[System Aufrufe](../c-runtime-library/system-calls.md)
