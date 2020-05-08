---
title: _umask_s
ms.date: 4/2/2020
api_name:
- _umask_s
- _o__umask_s
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
- api-ms-win-crt-filesystem-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- unmask_s
- _umask_s
helpviewer_keywords:
- masks, file-permission-setting
- _umask_s function
- masks
- file permissions [C++]
- umask_s function
- files [C++], permission settings for
ms.assetid: 70898f61-bf2b-4d8d-8291-0ccaa6d33145
ms.openlocfilehash: 712313314c67d15987326e3e3a920cd5f1039239
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2020
ms.locfileid: "82913878"
---
# <a name="_umask_s"></a>_umask_s

Legt die Standard-Dateiberechtigungsmaske fest. Dies ist eine Version von [_umask](umask.md) mit Sicherheitserweiterungen wie in den [Sicherheitsfunktionen in CRT](../../c-runtime-library/security-features-in-the-crt.md) beschrieben.

## <a name="syntax"></a>Syntax

```C
errno_t _umask_s(
   int mode,
   int * pOldMode
);
```

### <a name="parameters"></a>Parameter

*mode*<br/>
Standard-Berechtigungseinstellung.

*poldmode*<br/>
Der vorherige Wert der Berechtigungseinstellung.

## <a name="return-value"></a>Rückgabewert

Gibt einen Fehlercode zurück, wenn der *Modus* keinen gültigen Modus angibt oder der *poldmode* -Zeiger **null**ist.

### <a name="error-conditions"></a>Fehlerbedingungen

|*mode*|*poldmode*|Rückgabewert|Inhalt von *poldmode*|
|------------|----------------|----------------------|--------------------------------|
|any|**Normal**|**Eingabe**|nicht geändert|
|ungültiger Modus|any|**Eingabe**|nicht geändert|

Wenn eine der obengenannten Bedingungen auftritt, wird der Handler für ungültige Parameter aufgerufen wie in [Parametervalidierung](../../c-runtime-library/parameter-validation.md) beschrieben. Wenn die weitere Ausführung zugelassen wird, **_umask_s** gibt _umask_s **EINVAL** zurück und legt **errno** auf **EINVAL**fest.

## <a name="remarks"></a>Hinweise

Die **_umask_s** -Funktion legt die Datei Berechtigungs Maske des aktuellen Prozesses auf den Modus fest, der durch den- *Modus*angegeben wird. Die Datei Berechtigungseinstellung ändert die Berechtigungseinstellung für neue Dateien, die durch **_creat**, **_open**oder **_sopen**erstellt wurden. Wenn ein Bit in der Maske 1 ist, wird das entsprechende Bit im angeforderten Berechtigungswert der Datei auf 0 (nicht zulässig) festgelegt. Wenn ein Bit in der Maske 0 ist, bleibt das entsprechende Bit unverändert. Die Berechtigungseinstellung für eine neue Datei wird erst festgelegt, wenn die Datei zum ersten Mal geschlossen wird.

Der ganzzahlige Ausdruck " *pmode* " enthält eine oder beide der folgenden Manifest-Konstanten, die in "sys\status" definiert sind. Micha

|*pmode*||
|-|-|
|**_S_IWRITE**|Schreiben erlaubt.|
|**_S_IREAD**|Lesen erlaubt.|
|**_S_IREAD** \| **_S_IWRITE**|Lesen und Schreiben erlaubt.|

Wenn beide Konstanten angegeben werden, werden Sie mit dem bitweisen OR-Operator ( **|** ) verknüpft. Wenn das *Mode* -Argument **_S_IREAD**ist, ist das Lesen nicht zulässig (die Datei ist schreibgeschützt). Wenn das *Mode* -Argument **_S_IWRITE**ist, ist das Schreiben nicht zulässig (die Datei ist schreibgeschützt). Wenn z.B. das Schreib-Bit in der Maske festgelegt ist, sind alle neuen Dateien schreibgeschützt. Beachten Sie, dass in MS-DOS und Windows-Betriebssystemen alle Dateien lesbar sind und es nicht möglich ist, nur Schreibberechtigungen zu vergeben. Daher hat das Festlegen des gelesenen Bits mit **_umask_s** keine Auswirkung auf den Modus der Datei.

Wenn *pmode* keine Kombination aus einer der Manifest-Konstanten ist oder einen alternativen Satz von Konstanten enthält, ignoriert die Funktion diese einfach.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen hierzu finden Sie unter [globaler Status in der CRT](../global-state.md).

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|
|-------------|---------------------|
|**_umask_s**|\<io.h> und \<sys/stat.h> und \<sys/types.h>|

Zusätzliche Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Beispiel

```C
// crt_umask_s.c
/* This program uses _umask_s to set
* the file-permission mask so that all future
* files will be created as read-only files.
* It also displays the old mask.
*/

#include <sys/stat.h>
#include <sys/types.h>
#include <io.h>
#include <stdio.h>

int main( void )
{
   int oldmask, err;

   /* Create read-only files: */
   err = _umask_s( _S_IWRITE, &oldmask );
   if (err)
   {
      printf("Error setting the umask.\n");
      exit(1);
   }
   printf( "Oldmask = 0x%.4x\n", oldmask );
}
```

```Output
Oldmask = 0x0000
```

## <a name="see-also"></a>Weitere Informationen

[Dateiverarbeitung](../../c-runtime-library/file-handling.md)<br/>
[E/a auf niedriger Ebene](../../c-runtime-library/low-level-i-o.md)<br/>
[_chmod, _wchmod](chmod-wchmod.md)<br/>
[_creat, _wcreat](creat-wcreat.md)<br/>
[_mkdir, _wmkdir](mkdir-wmkdir.md)<br/>
[_open, _wopen](open-wopen.md)<br/>
[_umask](umask.md)<br/>
