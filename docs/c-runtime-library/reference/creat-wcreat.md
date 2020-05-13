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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 379a4adbf17755341fed6a48c649afe29e150fe5
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2020
ms.locfileid: "82912113"
---
# <a name="_creat-_wcreat"></a>_creat, _wcreat

Erstellt eine neue Datei. **_creat** und **_wcreat** wurden als veraltet markiert. Verwenden Sie stattdessen [_sopen_s _wsopen_s](sopen-s-wsopen-s.md) .

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

*Einfügen*<br/>
Name der neuen Datei.

*pmode*<br/>
Berechtigungseinstellung.

## <a name="return-value"></a>Rückgabewert

Diese Funktionen, sofern erfolgreich, geben einen Dateideskriptor an die erstellte Datei zurück. Andernfalls geben die Funktionen-1 zurück und legen **errno** fest, wie in der folgenden Tabelle gezeigt.

|**errno** -Einstellung|Beschreibung|
|---------------------|-----------------|
|**EACCES**|*filename* gibt eine vorhandene schreibgeschützte Datei an oder gibt ein Verzeichnis anstelle einer Datei an.|
|**EMFILE**|Es sind keine Dateideskriptoren mehr verfügbar.|
|**ENOENT**|Die angegebene Datei wurde nicht gefunden.|

Wenn *filename* **null**ist, rufen diese Funktionen den Handler für ungültige Parameter auf, wie in [Parameter Validation (Parameter](../../c-runtime-library/parameter-validation.md)Überprüfung) beschrieben. Wenn die weitere Ausführung zugelassen wird, legen diese Funktionen **errno** auf **EINVAL** fest und geben-1 zurück.

Weitere Informationen zu diesen und anderen Rückgabecodes finden Sie unter [_doserrno, errno, _sys_errlist und _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Hinweise

Die **_creat** -Funktion erstellt eine neue Datei oder öffnet und verkürzt eine vorhandene Datei. **_wcreat** ist eine breit Zeichen Version von **_creat**. Das *filename* -Argument für **_wcreat** ist eine Zeichenfolge mit breit Zeichen. **_wcreat** und **_creat** Verhalten sich andernfalls identisch.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen hierzu finden Sie unter [globaler Status in der CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Zuordnung generischer Textroutinen

|Tchar.h-Routine|_UNICODE und _MBCS nicht definiert|_MBCS definiert|_UNICODE definiert|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tcreat**|**_creat**|**_creat**|**_wcreat**|

Wenn die durch *filename* angegebene Datei nicht vorhanden ist, wird eine neue Datei mit der angegebenen Berechtigungseinstellung erstellt und zum Schreiben geöffnet. Wenn die Datei bereits vorhanden ist und die Berechtigungseinstellung das Schreiben zulässt, **_creat** die Datei auf die Länge 0 (null) verkürzen und den vorherigen Inhalt zerstören und zum Schreiben öffnen. Die Berechtigungseinstellung *pmode*gilt nur für neu erstellte Dateien. Die neue Datei erhält die angegebene Berechtigungseinstellung, nachdem sie zum ersten Mal geschlossen wurde. Der ganzzahlige Ausdruck " *pmode* " enthält eine oder beide der Manifest-Konstanten **_S_IWRITE** und **_S_IREAD**, die in "sys\status" definiert sind. Wenn beide Konstanten angegeben werden, werden Sie mit dem bitweisen OR-Operator ( **&#124;** ) verknüpft. Der *pmode* -Parameter wird auf einen der folgenden Werte festgelegt.

|Value|Definition|
|-----------|----------------|
|**_S_IWRITE**|Schreiben erlaubt.|
|**_S_IREAD**|Lesen erlaubt.|
|**_S_IREAD** &#124; **_S_IWRITE**|Lesen und Schreiben erlaubt.|

Wenn keine Schreibberechtigung gewährt wird, kann die Datei nur gelesen werden. Hinweis: Alle Dateien sind stets lesbar; es ist nicht möglich, nur Schreibberechtigungen zu vergeben. Die Modi **_S_IWRITE** und **_S_IREAD** | **_S_IWRITE** sind dann gleichwertig. Dateien, die mit **_creat** geöffnet werden, werden immer im Kompatibilitätsmodus geöffnet (siehe [_sopen](sopen-wsopen.md)), wenn **_SH_DENYNO**.

**_creat** wendet die aktuelle Datei Berechtigungs Maske auf *pmode* an, bevor die Berechtigungen festgelegt werden (siehe [_umask](umask.md)). **_creat** wird in erster Linie für die Kompatibilität mit früheren Bibliotheken bereitgestellt. Ein Aufrufen von **_open** mit **_O_CREAT** und **_O_TRUNC** im *Oflag* -Parameter entspricht **_creat** und wird für neuen Code bevorzugt.

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

## <a name="see-also"></a>Weitere Informationen

[E/a auf niedriger Ebene](../../c-runtime-library/low-level-i-o.md)<br/>
[_chmod, _wchmod](chmod-wchmod.md)<br/>
[_chsize](chsize.md)<br/>
[_close](close.md)<br/>
[_dup, _dup2](dup-dup2.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
[_sopen, _wsopen](sopen-wsopen.md)<br/>
[_umask](umask.md)<br/>
