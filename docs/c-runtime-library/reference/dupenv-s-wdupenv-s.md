---
title: _dupenv_s, _wdupenv_s
ms.date: 4/2/2020
api_name:
- _dupenv_s
- _wdupenv_s
- _o__dupenv_s
- _o__wdupenv_s
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
- api-ms-win-crt-environment-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- tdupenv_s
- _dupenv_s
- wdupenv_s
- dupenv_s
- _tdupenv_s
- _wdupenv_s
helpviewer_keywords:
- _dupenv_s function
- _tdupenv_s function
- _wdupenv_s function
- environment variables
- wdupenv_s function
- dupenv_s function
- tdupenv_s function
ms.assetid: b729ecc2-a31d-4ccf-92a7-5accedb8f8c8
ms.openlocfilehash: f65f1da3e8cef077df04d0bdb7eb2aaf75afd9fa
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81348062"
---
# <a name="_dupenv_s-_wdupenv_s"></a>_dupenv_s, _wdupenv_s

Ruft einen Wert aus der aktuellen Umgebung ab.

> [!IMPORTANT]
> Diese API kann nicht in Anwendungen verwendet werden, die in Windows-Runtime ausgeführt werden. Weitere Informationen finden Sie im Artikel [CRT functions not supported in Universal Windows Platform apps (In Apps für die universelle Windows-Plattform nicht unterstützte CRT-Funktionen)](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Syntax

```C
errno_t _dupenv_s(
   char **buffer,
   size_t *numberOfElements,
   const char *varname
);
errno_t _wdupenv_s(
   wchar_t **buffer,
   size_t *numberOfElements,
   const wchar_t *varname
);
```

### <a name="parameters"></a>Parameter

*Puffer*<br/>
Puffer zum Speichern des Variablenwerts.

*Sizeinbytes*<br/>
Größe des *Puffers*.

*Varname*<br/>
Umgebungsvariablenname.

## <a name="return-value"></a>Rückgabewert

Null bei Erfolg, ein Fehlercode, wenn ein Fehler auftritt.

Diese Funktionen überprüfen ihre Parameter; Wenn *buffer* oder *varname* **NULL**ist, wird der ungültige Parameterhandler wie unter [Parametervalidierung](../../c-runtime-library/parameter-validation.md)beschrieben aufgerufen. Wenn die Ausführung fortgesetzt werden darf, setzen die Funktionen **errno** auf **EINVAL** und geben **EINVAL**zurück.

Wenn diese Funktionen nicht genügend Arbeitsspeicher zuweisen können, legen sie *den Puffer* auf **NULL** und *numberOfElements* auf 0 fest und geben **ENOMEM**zurück.

## <a name="remarks"></a>Bemerkungen

Die **_dupenv_s-Funktion** durchsucht die Liste der Umgebungsvariablen nach *varname*. Wenn die Variable gefunden wird, **ordnet _dupenv_s** einen Puffer zu und kopiert den Wert der Variablen in den Puffer. Die Adresse und Länge des Puffers werden in *Buffer* und *numberOfElements*zurückgegeben. Durch das Zuweisen des Puffers selbst **bietet _dupenv_s** eine bequemere Alternative zu [getenv_s, _wgetenv_s](getenv-s-wgetenv-s.md).

> [!NOTE]
> Das aufrufende Programm ist dafür zuständig, den Arbeitsspeicher durch Aufruf von [free](free.md) zu leeren.

Wenn die Variable nicht gefunden wird, wird *der Puffer* auf **NULL**gesetzt, *numberOfElements* wird auf 0 gesetzt, und der Rückgabewert ist 0, da diese Situation nicht als Fehlerbedingung betrachtet wird.

Wenn Sie nicht an der Größe des Puffers interessiert sind, können Sie **NULL** für *numberOfElements*übergeben.

**_dupenv_s** wird im Windows-Betriebssystem nicht in der Groß-/Kleinschreibung berücksichtigt. **_dupenv_s** verwendet die Kopie der Umgebung, auf die die globale Variable **_environ** für den Zugriff auf die Umgebung zeigt. Siehe die Bemerkungen in [getenv_s, _wgetenv_s](getenv-s-wgetenv-s.md) für eine Diskussion **über _environ**.

Der Wert im *Puffer* ist eine Kopie des Werts der Umgebungsvariablen. Die Änderung hat keine Auswirkungen auf die Umwelt. Verwenden Sie die Funktion [_putenv_s, _wputenv_s](putenv-s-wputenv-s.md), um den Wert einer Umgebungsvariablen zu ändern.

**_wdupenv_s** ist eine breit **gefächerte**Version von _dupenv_s ; Die Argumente von **_wdupenv_s** sind Zeichenfolgen mit großen Zeichen. Die **_wenviron** globale Variable ist eine breitstellige Version von **_environ**. Weitere Informationen finden Sie in [den Getenv_s-_wgetenv_s](getenv-s-wgetenv-s.md) zu **_wenviron**.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen dazu finden Sie [unter Globaler Status in der CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Zuordnung generischer Textroutinen

|TCHAR.H-Routine|_UNICODE und _MBCS nicht definiert.|_MBCS definiert|_UNICODE definiert|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tdupenv_s**|**_dupenv_s**|**_dupenv_s**|**_wdupenv_s**|

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|
|-------------|---------------------|
|**_dupenv_s**|\<stdlib.h>|
|**_wdupenv_s**|\<stdlib.h> oder \<wchar.h>|

Zusätzliche Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Beispiel

```C
// crt_dupenv_s.c
#include  <stdlib.h>

int main( void )
{
   char *pValue;
   size_t len;
   errno_t err = _dupenv_s( &pValue, &len, "pathext" );
   if ( err ) return -1;
   printf( "pathext = %s\n", pValue );
   free( pValue );
   err = _dupenv_s( &pValue, &len, "nonexistentvariable" );
   if ( err ) return -1;
   printf( "nonexistentvariable = %s\n", pValue );
   free( pValue ); // It's OK to call free with NULL
}
```

```Output
pathext = .COM;.EXE;.BAT;.CMD;.VBS;.VBE;.JS;.JSE;.WSF;.WSH;.pl
nonexistentvariable = (null)
```

## <a name="see-also"></a>Siehe auch

[Prozess- und Umweltkontrolle](../../c-runtime-library/process-and-environment-control.md)<br/>
[Umweltkonstanten](../../c-runtime-library/environmental-constants.md)<br/>
[_dupenv_s_dbg, _wdupenv_s_dbg](dupenv-s-dbg-wdupenv-s-dbg.md)<br/>
[getenv_s, _wgetenv_s](getenv-s-wgetenv-s.md)<br/>
[_putenv_s, _wputenv_s](putenv-s-wputenv-s.md)<br/>
