---
title: _creat, _wcreat
ms.date: 4/2/2020
api_name:
- _creat
- _wcreat
- _o__creat
- _o__wcreat
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
- wcreat
- _wcreat
- _creat
- tcreat
- _tcreat
helpviewer_keywords:
- wcreat function
- _wcreat function
- files [C++], creating
- _creat function
- tcreat function
- creat function
- _tcreat function
ms.assetid: 3b3b795d-1620-40ec-bd2b-a4bbb0d20fe5
ms.openlocfilehash: 18ecf78d2cbff3647eae912a1bb1b17d5340f185
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81348335"
---
# <a name="_creat-_wcreat"></a>_creat, _wcreat

Erstellt eine neue Datei. **_creat** und **_wcreat** sind veraltet; verwenden Sie [stattdessen _sopen_s, _wsopen_s.](sopen-s-wsopen-s.md)

## <a name="syntax"></a>Syntax

```C
int _creat(
   const char *filename,
   int pmode
);
int _wcreat(
   const wchar_t *filename,
   int pmode
);
```

### <a name="parameters"></a>Parameter

*Dateiname*<br/>
Name der neuen Datei.

*Pmode*<br/>
Berechtigungseinstellung.

## <a name="return-value"></a>Rückgabewert

Diese Funktionen, sofern erfolgreich, geben einen Dateideskriptor an die erstellte Datei zurück. Andernfalls geben die Funktionen -1 zurück und setzen **errno,** wie in der folgenden Tabelle dargestellt.

|**errno-Einstellung**|BESCHREIBUNG|
|---------------------|-----------------|
|**EACCES**|*filename* gibt eine vorhandene schreibgeschützte Datei oder ein Verzeichnis anstelle einer Datei an.|
|**EMFILE**|Es sind keine Dateideskriptoren mehr verfügbar.|
|**ENOENT**|Die angegebene Datei wurde nicht gefunden.|

Wenn *filename* **NULL**ist, rufen diese Funktionen den ungültigen Parameterhandler auf, wie unter [Parametervalidierung](../../c-runtime-library/parameter-validation.md)beschrieben. Wenn die Ausführung fortgesetzt werden darf, setzen diese Funktionen **errno** auf **EINVAL** und geben -1 zurück.

Weitere Informationen zu diesen und anderen Rückgabecodes finden Sie unter [_doserrno, errno, _sys_errlist und _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Bemerkungen

Die **_creat-Funktion** erstellt eine neue Datei oder öffnet und kürzt eine vorhandene. **_wcreat** ist eine breitgefächerte Version von **_creat**; Das *Dateiname-Argument* für **_wcreat** ist eine Zeichenfolge mit großen Zeichen. **_wcreat** und **_creat** verhalten sich ansonsten gleich.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen dazu finden Sie [unter Globaler Status in der CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Zuordnung generischer Textroutinen

|Tchar.h-Routine|_UNICODE und _MBCS nicht definiert|_MBCS definiert|_UNICODE definiert|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tcreat**|**_creat**|**_creat**|**_wcreat**|

Wenn die durch *Dateiname* angegebene Datei nicht vorhanden ist, wird eine neue Datei mit der angegebenen Berechtigungseinstellung erstellt und zum Schreiben geöffnet. Wenn die Datei bereits vorhanden ist und die Berechtigungseinstellung das Schreiben zulässt, **wird die** Datei _creat auf Länge 0 abgeschnitten, wodurch der vorherige Inhalt zerstört wird, und sie zum Schreiben geöffnet. Die Berechtigungseinstellung *pmode*gilt nur für neu erstellte Dateien. Die neue Datei erhält die angegebene Berechtigungseinstellung, nachdem sie zum ersten Mal geschlossen wurde. Der ganzzahlige Ausdruck *pmode* enthält eine oder beide manifesten Konstanten **_S_IWRITE** und **_S_IREAD**, die in SYS-Stat.h definiert sind. Wenn beide Konstanten angegeben werden, werden sie mit dem bitweisen oder Operator ( **&#124;** ) verbunden. Der *Parameter pmode* wird auf einen der folgenden Werte festgelegt.

|Wert|Definition|
|-----------|----------------|
|**_S_IWRITE**|Schreiben erlaubt.|
|**_S_IREAD**|Lesen erlaubt.|
|**_S_IREAD** &#124; **_S_IWRITE**|Lesen und Schreiben erlaubt.|

Wenn keine Schreibberechtigung gewährt wird, kann die Datei nur gelesen werden. Hinweis: Alle Dateien sind stets lesbar; es ist nicht möglich, nur Schreibberechtigungen zu vergeben. Die Modi **_S_IWRITE** und **_S_IREAD** | **_S_IWRITE** sind dann gleichwertig. Dateien, die mit **_creat** geöffnet werden, werden immer im Kompatibilitätsmodus geöffnet (siehe [_sopen](sopen-wsopen.md)) mit **_SH_DENYNO**.

**_creat** wendet die aktuelle Dateiberechtigungsmaske auf *pmode* an, bevor die Berechtigungen gesetzt werden (siehe [_umask](umask.md)). **_creat** wird in erster Linie für die Kompatibilität mit früheren Bibliotheken bereitgestellt. Ein Aufruf an **_open** mit **_O_CREAT** und **_O_TRUNC** im *oflag-Parameter* entspricht **_creat** und ist für neuen Code vorzuziehen.

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|Optionaler Header|
|-------------|---------------------|---------------------|
|**_creat**|\<io.h>|\<sys/types.h>, \<sys/stat.h>, \<errno.h>|
|**_wcreat**|\<io.h> oder \<wchar.h>|\<sys/types.h>, \<sys/stat.h>, \<errno.h>|

Weitere Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Beispiel

```C
// crt_creat.c
// compile with: /W3
// This program uses _creat to create
// the file (or truncate the existing file)
// named data and open it for writing.

#include <sys/types.h>
#include <sys/stat.h>
#include <io.h>
#include <stdio.h>
#include <stdlib.h>

int main( void )
{
   int fh;

   fh = _creat( "data", _S_IREAD | _S_IWRITE ); // C4996
   // Note: _creat is deprecated; use _sopen_s instead
   if( fh == -1 )
      perror( "Couldn't create data file" );
   else
   {
      printf( "Created data file.\n" );
      _close( fh );
   }
}
```

```Output
Created data file.
```

## <a name="see-also"></a>Siehe auch

[Low-Level-E/A](../../c-runtime-library/low-level-i-o.md)<br/>
[_chmod, _wchmod](chmod-wchmod.md)<br/>
[_chsize](chsize.md)<br/>
[_close](close.md)<br/>
[_dup, _dup2](dup-dup2.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
[_sopen, _wsopen](sopen-wsopen.md)<br/>
[_umask](umask.md)<br/>
