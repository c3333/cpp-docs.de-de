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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 39184eff5db511dfb920782c3e29bf2b0cc9340e
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2020
ms.locfileid: "82915179"
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

*ert*<br/>
Puffer zum Speichern des Variablenwerts.

*numberOfElements*<br/>
Größe des *Puffers*.

*varname*<br/>
Umgebungsvariablenname.

## <a name="return-value"></a>Rückgabewert

Null bei Erfolg, ein Fehlercode, wenn ein Fehler auftritt.

Diese Funktionen überprüfen Ihre Parameter. Wenn *buffer* oder *varname* **null**ist, wird der Handler für ungültige Parameter aufgerufen, wie in [Parameter Validation (Parameter](../../c-runtime-library/parameter-validation.md)Überprüfung) beschrieben. Wenn die weitere Ausführung zugelassen wird, legen die Funktionen " **errno** " auf " **EINVAL** " fest und geben " **EINVAL**" zurück.

Wenn diese Funktionen nicht genügend Arbeitsspeicher zuordnen können, legen Sie den *Puffer* auf **null** und die *Anzahl* der Werte auf 0 fest und geben **ENOMEM**zurück.

## <a name="remarks"></a>Hinweise

Die **_dupenv_s** -Funktion durchsucht die Liste der Umgebungsvariablen nach *varname*. Wenn die Variable gefunden wird, ordnet **_dupenv_s** einen Puffer zu und kopiert den Wert der Variablen in den Puffer. Die Adresse und die Länge des Puffers werden in *buffer* und *nummerioements*zurückgegeben. Wenn Sie den Puffer selbst zuweisen, bietet **_dupenv_s** eine komfortablere Alternative zu [Getenv_s, _wgetenv_s](getenv-s-wgetenv-s.md).

> [!NOTE]
> Das aufrufende Programm ist dafür zuständig, den Arbeitsspeicher durch Aufruf von [free](free.md) zu leeren.

Wenn die Variable nicht gefunden wird, wird *buffer* auf **null**festgelegt, der Wert für " *" ist auf* "0" festgelegt, und der Rückgabewert ist 0, da diese Situation nicht als Fehlerbedingung angesehen wird.

Wenn Sie nicht an der Größe des Puffers interessiert sind, können Sie **null** für " *numofelements*" übergeben.

beim Windows-Betriebssystem wird **_dupenv_s** die Groß-/Kleinschreibung nicht beachtet. **_dupenv_s** verwendet die Kopie der Umgebung, auf die die globale Variable verweist, um auf die Umgebung zuzugreifen **_environ** . Eine Erläuterung der **_environ**finden Sie in den Hinweisen in [getenv_s _wgetenv_s](getenv-s-wgetenv-s.md) .

Der Wert in *buffer* ist eine Kopie des Werts der Umgebungsvariablen. eine Änderung der Umgebung hat keine Auswirkungen auf die Umgebung. Verwenden Sie die Funktion [_putenv_s, _wputenv_s](putenv-s-wputenv-s.md), um den Wert einer Umgebungsvariablen zu ändern.

**_wdupenv_s** ist eine breit Zeichen Version von **_dupenv_s**. die Argumente von **_wdupenv_s** sind Zeichen folgen mit breit Zeichen. Die **_wenviron** globale Variable ist eine breit Zeichen Version von **_environ**. Weitere Informationen zu **_wenviron**finden Sie in den Hinweisen in [getenv_s _wgetenv_s](getenv-s-wgetenv-s.md) .

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen hierzu finden Sie unter [globaler Status in der CRT](../global-state.md).

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

## <a name="see-also"></a>Weitere Informationen

[Prozess-und Umgebungs Steuerung](../../c-runtime-library/process-and-environment-control.md)<br/>
[Umgebungs Konstanten](../../c-runtime-library/environmental-constants.md)<br/>
[_dupenv_s_dbg, _wdupenv_s_dbg](dupenv-s-dbg-wdupenv-s-dbg.md)<br/>
[getenv_s, _wgetenv_s](getenv-s-wgetenv-s.md)<br/>
[_putenv_s, _wputenv_s](putenv-s-wputenv-s.md)<br/>
